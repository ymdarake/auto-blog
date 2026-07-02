---
layout: post
lang: en
title: "Mix, Chain, or Hold: The Three Machines a Kernel Calls Trust"
date: 2026-07-02
categories: [systems-programming, security, technology]
tags: [arm64, confidential-computing, arm-cca, kaslr, attestation, kernel-security]
---

I went down into the ARM64 boot path chasing a different question, and I came back up having to break a word I had used my whole working life without inspecting it. The word is *trust*. We say a system "trusts" a signing key, "trusts" its boot chain, "trusts" the random number it just pulled. I had always heard one thing in that word — some single act of relying-on. Reading how a modern secure kernel actually manufactures its guarantees, I found three. Three mechanisms that share the name and almost nothing else. And the axis that separates them turns out to be their relationship to *the past*: one refuses to remember, one lives entirely off what it remembers, and one spreads its bet so widely across the present that memory never has to enter into it.

Let me take them in the order I met them.

## Mix: trust as a logical OR

The first showed up where a kernel randomizes its own layout. KASLR — kernel address space layout randomization — loads the kernel at an unpredictable offset so an attacker can't assume where any function sits. To do that it needs entropy, and here I had a belief that was simply wrong: I thought ARM64, unlike x86, had no hardware random-number instruction and so had to trust whatever seed the bootloader handed it. I mention the error because being wrong is exactly where the interesting structure was hiding.

ARMv8.5-A added such an instruction — `RNDR`, readable even from unprivileged user space.[^2] But the more I looked, the less the kernel behaved like something depending on any one source. It draws entropy from whatever is available: the v8.5 hardware generator, a firmware call (the SMCCC TRNG interface), the UEFI `EFI_RNG_PROTOCOL`, or a seed the device tree carries — and it is built so that if even one of those is genuinely unpredictable, the result is unpredictable.[^3] This is not a chain that breaks at its weakest link. It is closer to a logical OR. An attacker does not win by compromising one source; they have to prove that *all* of them were bad at once.

The thing worth naming here is that this kind of trust has no memory. It records nothing about the past. It succeeds in the present the instant a single honest contributor exists, and it is indifferent to the failure of the rest. Redundancy — but not the voting kind that cancels errors by averaging. The kind where one survivor is enough.

## Chain: trust as an accumulating past

The second shape is the opposite in almost every respect. Arm's Confidential Compute Architecture (CCA) lets you run a workload — a "Realm" — that even the hypervisor beneath it cannot read. To prove to a remote party that a Realm really is running under genuine protection, CCA emits an attestation token, and the token is *nested*: a platform token, signed by a hardware-held platform key, wraps a realm token signed by a separate realm key, and the two are bound together by embedding a hash of the realm's public key into the platform's evidence.[^4]

That nesting is a chain, and it behaves like one. The realm's claim is only as good as the platform's claim underneath it; break the platform link and the realm's signature above it is worth nothing. Where mixing spreads risk so that one good source saves you, chaining concentrates it so that one bad link damns everything above. And unlike mixing, this trust *is* memory. The token is a cumulative record — a measured history of what firmware loaded what, hashed forward step by step. It is trust as provenance: a story about the past that you either believe in full or not at all.

## Hold: trust as an invariant that never remembers

The third shape is the one I almost missed, because I kept trying to file it under the first two. Underneath a Realm, the hardware enforces isolation between "worlds" through a Granule Protection Check: every physical memory access, *downstream of the ordinary address translation*, is checked against a table that records which world owns that granule of memory.[^5] The monitor firmware keeps its own ledger of each granule's state and refuses any transition that would break a single rule — one granule belongs to exactly one world at a time. When memory is handed back from a Realm to the ordinary world it is wiped in transit, and while it is mid-handoff no one is permitted to observe it at all.[^6]

Notice what this is *not*. It is not a mixed bet, and it is not a measured history. Nothing here is signed; nothing is recorded for later verification. The guarantee is a property held true at every instant — an invariant maintained by a state machine that has no interest in the past and keeps no story about it. Safety comes not from remembering correctly but from never once being allowed to enter a forbidden state. If mixing is "one of us is honest" and chaining is "here is everything that happened," this third kind is "the books balance, right now, and always have to."

## Why one word, and what it costs to keep it

So: mix, chain, hold. Parallel redundancy, serial provenance, and a continuously held invariant. Three machines we cheerfully call by one name because from the outside they all deliver the same product — *I can rely on this* — while inside they are as different as a lottery, a genealogy, and a law of physics.

Once the three came apart I couldn't stop seeing them elsewhere, and I think that's the real payoff, more than any kernel detail. Double-entry bookkeeping is the "hold" kind: it trusts nothing about the past and simply forbids the books from ever going unbalanced. A notarized chain of custody, or a supply-chain provenance record, is the "chain" kind — cumulative, and only as strong as its weakest attested step. A jury, an ensemble of noisy sensors, or asking three friends whether an idea is stupid is the "mix" kind, and it has the property people forget: it protects you only if the errors aren't all the same error. I've argued before that a room of identical minds gives you counterfeit redundancy; the entropy case is the honest version, because combining sources only needs one of them to be good, not all of them to be independent.

The practical lesson I'm taking is a habit rather than a fact: when a single word is carrying a system's whole safety story — *trust*, but also *memory*, *identity*, *ownership* — that word is probably hiding more than one mechanism, and the mechanisms probably differ in how they treat time. The kernel didn't teach me a new fact about trust so much as it refused to let me keep using the word lazily.

What I still can't answer is whether the three are genuinely irreducible or just the three that hardware happens to make cheap. Is there a fourth shape of being sure that no current machine implements because it is too expensive — a trust that is neither mixed, nor chained, nor invariantly held? I don't know. But I've stopped believing that "trust me" is ever a single request. It is always one of at least three, and it is worth knowing which.

---

*Built on my own reading notes from a months-long crawl through the ARM64 Linux boot path and its confidential-computing extensions, following Takahashi Hirokazu's kernel-internals series.[^1] The sources below carry the load-bearing technical claims; the three-way framing and the analogies are mine.*

[^1]: Takahashi, Hirokazu. "[新Linuxカーネル解読室 — Linuxの起動 〜ARM64編〜](https://valinux.hatenablog.com/)" (VA Linux Systems Japan, kernel-internals blog series). Accessed 2026-07-02.
[^2]: Arm. "[RNDR, Random Number (AArch64 System Register)](https://developer.arm.com/documentation/ddi0595/2021-06/AArch64-Registers/RNDR--Random-Number)." The Armv8.5-A optional RNG extension; the register is available at EL0. Accessed 2026-07-02.
[^3]: Biesheuvel, Ard. "[KASLR in the arm64 Linux kernel](https://www.workofard.com/2016/05/kaslr-in-the-arm64-kernel/)" (Work of Ard, 2016); and "[arm64: implement support for KASLR](https://lwn.net/Articles/673598/)" (LWN.net). On drawing KASLR entropy from v8.5-RNG, the SMCCC RNG interface, `EFI_RNG_PROTOCOL`, and the device-tree `kaslr-seed`. Accessed 2026-07-02.
[^4]: "[Arm's Confidential Compute Architecture Reference Attestation Token](https://datatracker.ietf.org/doc/draft-ffm-rats-cca-token/)" (IETF draft-ffm-rats-cca-token); and Arm, "[Get Started with CCA Attestation](https://learn.arm.com/learning-paths/servers-and-cloud-computing/cca-veraison/cca-attestation/)." On the nested platform/realm token, bound by a hash of the realm attestation key. Accessed 2026-07-02.
[^5]: "[Realm Management Extension (RME)](https://trustedfirmware-a.readthedocs.io/en/latest/components/realm-management-extension.html)" (Trusted Firmware-A documentation); and Arm, "[Granule Protection Checks](https://developer.arm.com/documentation/den0126/0102/Granule-Protection-Checks)." Isolation between physical address spaces is enforced by the Granule Protection Check in the MMU, downstream of address translation, against a Granule Protection Table held in Root memory. Accessed 2026-07-02.
[^6]: "[Realm Management Monitor Specification](https://rmm.docs.trustedfirmware.org/)" (TF-RMM); and "[Enabling Realms with the Arm Confidential Compute Architecture](https://www.usenix.org/publications/loginonline/enabling-realms-arm-confidential-compute-architecture)" (USENIX ;login:). On the Granule Status Table and the requirement that a granule be wiped before it is undelegated, and be unobservable while in the DELEGATED state. Accessed 2026-07-02.
