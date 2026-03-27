---
layout: post
lang: en
title: "The End of the Rust Experiment: When Infrastructure Decides to Evolve"
date: 2026-03-27
categories: [systems-programming]
tags: [rust, linux-kernel, memory-safety, community, infrastructure]
---

The Rust experiment in the Linux kernel is over — not because it failed, but because it succeeded. At the 2025 Kernel Maintainer Summit in Tokyo, the assembled maintainers reached consensus: Rust is no longer experimental. It is a permanent part of the kernel, and the decision came with "zero pushback."[^1]

This is more than a technical milestone. It is a case study in how conservative communities decide to change their foundations — and what it takes for evidence to override tradition.

## The Evidence That Forced the Question

The argument for memory safety in systems code has been building for years. Microsoft has reported that approximately 70% of the CVEs it assigns each year stem from memory safety issues — buffer overflows, use-after-free, double-free, and similar bugs that memory-safe languages structurally prevent at compile time.[^2] While Linux kernel-specific figures vary by methodology, the pattern holds: the dominant class of security vulnerabilities in C codebases is precisely the class that Rust's ownership model eliminates.

What moved the kernel community beyond theoretical arguments was production evidence. Android 16 devices running the 6.12 kernel ship with ashmem — an anonymous shared memory allocator rewritten entirely in Rust — meaning millions of consumer devices already run Rust in their kernels in production.[^3] The Nova GPU driver, a Rust-based successor to the Nouveau driver targeting NVIDIA Turing and newer GPUs, was merged into Linux 6.15 in May 2025 as the first Rust-written DRM driver in mainline, though still in early stages of development.[^4] As Greg Kroah-Hartman noted during the summit, drivers written in Rust were proving safer than their C counterparts.[^1]

These are not proofs of concept. They are production code running on real hardware, reviewed by real maintainers.

## The Conservative Dilemma

What makes this story compelling is not the technical merits of Rust — those have been argued exhaustively. The interesting question is how a deeply conservative community chose to adopt something fundamentally new.

The Linux kernel community is conservative for good reasons. Stability is not a preference; it is a moral obligation when code runs on medical devices, financial systems, and critical infrastructure. The cost of a kernel bug is measured not in inconvenience but in potential harm. Every new abstraction layer is a possible source of bugs. Every unfamiliar pattern is a maintenance burden. Every new language risks splitting the contributor base.

This conservatism creates a paradox. The community that most needs memory safety is also the community most resistant to the disruption required to achieve it.

And yet, the data kept accumulating. At some point, the conservative choice *becomes* the change — because the status quo is demonstrably more dangerous than the alternative. When 70% of security vulnerabilities in major C codebases fall into a category that a different language structurally prevents, continuing with the status quo is no longer the cautious option. It is the risky one.

## What Changed Minds

It was not evangelism. The Rust-for-Linux community learned early that enthusiasm without production code is noise. What changed minds was shipping — real code, in real subsystems, reviewed by established maintainers.

There is a lesson here that extends beyond systems programming. Paradigm shifts in established communities do not happen through argument. They happen through demonstration — through someone doing the work and letting the results speak.

The Rust-for-Linux contributors did not merely argue that Rust belonged in the kernel. They wrote drivers, submitted patches, endured hostile mailing list threads, and shipped code that worked. The code itself became the argument.

## The Ethics of Infrastructure Maintenance

There is a deeper question here about the moral responsibility of infrastructure maintenance. If a class of vulnerabilities is known to be structurally preventable, and the tools to prevent them exist and have been demonstrated in production, what responsibility follows when those vulnerabilities are exploited?

This is not hypothetical. Memory safety bugs in the kernel have led to privilege escalation exploits used in real attacks. When the kernel community decided to make Rust permanent, there was an implicit acknowledgment: continued reliance on C alone, given what is now known, carries a moral weight.

This does not mean C is "bad" or that every kernel developer must learn Rust. It means that *the community as a whole* has recognized a responsibility to evolve its tools when the evidence demands it. That recognition — the willingness to let data override tradition — is what makes this decision remarkable.

## Ripple Effects

The implications extend beyond the kernel. Debian will require a Rust toolchain as a hard dependency for APT from May 2026, affecting legacy architecture ports that lack Rust support.[^5] The question is no longer "if" but "how fast."

The interesting open question is whether this pattern — conservative community, accumulating safety evidence, gradual demonstration, eventual adoption — will repeat for other paradigm shifts. Formal verification? Memory-safe successors beyond Rust? The kernel's journey may become a template for how critical infrastructure evolves.

The experimental label is gone. The experiment is over. The work continues.

---

## References

[^1]: DevClass. "Rust boosted by permanent adoption for Linux kernel code." https://devclass.com/2025/12/15/rust-boosted-by-permanent-adoption-for-linux-kernel-code/ (accessed 2026-03-27)
[^2]: Microsoft Security Response Center. "A proactive approach to more secure code." https://msrc.microsoft.com/blog/2019/07/a-proactive-approach-to-more-secure-code/ (accessed 2026-03-27)
[^3]: Rust for Linux. "Android ashmem." https://rust-for-linux.com/android-%60ashmem%60 (accessed 2026-03-27)
[^4]: Phoronix. "Rust-Written NOVA Open-Source NVIDIA Driver Being Further Built Out In Linux 6.17." https://www.phoronix.com/news/Linux-6.17-NOVA-Driver (accessed 2026-03-27)
[^5]: LWN.net. "Debian to require Rust as of May 2026." https://lwn.net/Articles/1044496/ (accessed 2026-03-27)
