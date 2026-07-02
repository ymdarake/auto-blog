# Verification Report: Mix, Chain, or Hold: The Three Machines a Kernel Calls Trust
Date: 2026-07-02

## Source Traceability
| Claim | Source Type | Source |
|-------|-------------|--------|
| KASLR draws entropy from several sources so that one honest source suffices | internal + external | books/authors/takahashi-hirokazu/linux-kernel-boot-arm64/notes.md (2026-05-06); Work of Ard KASLR; LWN 673598 |
| ARMv8.5-A added RNDR, readable at EL0 | external | developer.arm.com RNDR register doc; LLVM/GCC/kernel patches |
| CCA attestation token is nested (platform token wraps realm token), bound by hash of realm key | external | IETF draft-ffm-rats-cca-token; learn.arm.com CCA attestation |
| GPC enforced by MMU downstream of translation; GPT in Root world; one granule = one world | external | Trusted Firmware-A RME docs; developer.arm.com Granule Protection Checks |
| RMM keeps a Granule Status Table; granule wiped before undelegation, unobservable while DELEGATED | internal + external | notes.md (2026-06-03); TF-RMM spec; USENIX "Enabling Realms" |
| The "three shapes of trust" framing (mix / chain / hold), the time-relationship axis, and the cross-domain analogies (double-entry, chain of custody, jury) | opinion | (author's synthesis across the reading notes) |
| Reference to earlier "counterfeit redundancy" argument | internal | auto-blog post 2026-06-25-counterfeit-redundancy.md |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|--------------|--------|--------|
| F1 | ARMv8.5-A added RNDR/RNDRRS random-number instructions, available at EL0 | "ARMv8.5-A RNDR RNDRRS random number instruction RDRAND equivalent EL0" | Verified | Kept; cited [^2] |
| F2 | Linux ARM64 KASLR obtains entropy from v8.5-RNG / SMCCC TRNG / EFI_RNG_PROTOCOL / kaslr-seed, defense-in-depth | "Linux ARM64 KASLR entropy sources kaslr-seed EFI_RNG_PROTOCOL SMCCC TRNG combine" | Partially Verified | Framed as "draws from whatever is available / one good source suffices" rather than asserting a strict XOR combine; "logical OR" used as analogy, not implementation claim |
| F3 | CCA attestation token is a nested platform+realm structure, bound by a hash of the realm attestation key | "Arm CCA attestation token Platform Realm nested structure realm attestation key" | Verified | Kept; cited [^4] |
| F4 | GPC is performed by the MMU downstream of address translation, against a GPT held in Root memory; enables dynamic per-granule PAS assignment | "Arm RME Granule Protection Check GPT physical address space downstream MMU RMM granule status" | Verified | Kept; cited [^5] |
| F5 | RMM maintains a Granule Status Table; a granule is wiped before being undelegated and is unobservable while DELEGATED | "Arm RMM granule delegate wipe scrub contents zeroed transition realm normal world leakage" | Verified | Kept; cited [^6]. Article says "wiped," matching the spec's guarantee (wiping need not be zero-filling) — no over-specific claim made |

## Notes on framing decisions
- **Avoided asserting a strict XOR mechanism for KASLR entropy.** The reading note (2026-05-06) described the kernel "XOR-mixing" sources, but the verifiable public sources describe a defense-in-depth / fallback design across v8.5-RNG, SMCCC TRNG, EFI_RNG_PROTOCOL, and the DT kaslr-seed. The article therefore makes only the well-supported point — the design succeeds if any single source is genuinely unpredictable — and uses "logical OR" explicitly as an analogy for that property, not as an implementation claim.
- **Named the "wipe" without over-specifying.** The RMM spec guarantees that a granule's contents are not observable across a world transition and are wiped before undelegation, while explicitly noting the wipe need not be zero-filling. The article says only "wiped in transit," consistent with the guarantee.
- **The three-way taxonomy is the author's synthesis**, not a claim about how Arm or the kernel documents these mechanisms. The load-bearing facts (F1–F5) are each independently verified; the "mix / chain / hold" grouping and the past-relationship axis are original analysis and are presented as such.

## Copyright Review
- Direct quotes: 0 (no third-party text quoted verbatim; no blockquotes needed)
- Paraphrased content: all technical anchors paraphrased in original wording, each attributed via footnote
- Original analysis: ~75% of the article (the three-shape taxonomy, the time-relationship axis, and all cross-domain analogies are the author's; sources supply only the technical anchors)
- No single source exceeds ~10% of the article; the longest single reliance is the CCA attestation description (one paragraph, [^4])

## Overall Assessment
- Fact-check pass rate: 5/5 (4 Verified + 1 Partially Verified); 0 Unverified, 0 Contradicted
- Unverified/Contradicted share: 0% (well under the 30% withdrawal threshold)
- Copyright risk: Low
- Ready for review: Yes
