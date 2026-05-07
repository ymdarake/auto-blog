---
layout: post
lang: en
title: "Two Layers of Bio-Inspired: What's Real When Schedulers Borrow Biology"
date: 2026-05-07
categories: [systems-programming, technology]
tags: [linux-kernel, sched_ext, bpf, bio-inspired, metaheuristics, scheduler]
---

For the last two years, Linux kernel scheduling has had a small renaissance. The Completely Fair Scheduler, the policy that has run almost every Linux machine for more than a decade, suddenly has competition, and some of that competition wears biology on its sleeve. There are scheduling papers about tissue P systems, LSTM predictors, and "shallow brain" architectures. The temptation, for anyone glancing at the kernel mailing lists, is to conclude that operating systems are getting more biological. I do not think this is the right read.

The wave has two layers, and conflating them is easy and expensive. One layer is bio-inspired in a structurally serious sense. The other is what Kenneth Sörensen, in a paper that ran in *International Transactions in Operational Research* in 2015, called metaphor-driven research — algorithms whose biological framing dissolves on contact with their actual implementation.[^1] Most of the noise lives in the second layer. Most of the signal lives in the first. And the papers that draw the most attention tend to live on the noisy side of the line.

## The substrate that arrived

The layer I want to defend is the kernel's new ability to host scheduling policies as runtime-loadable BPF programs. The feature is called sched_ext, and it was merged into mainline Linux as part of the 6.12 release, which Linus Torvalds tagged stable on 17 November 2024.[^2] The mechanics are mundane; the implications are not. A scheduling policy, written in BPF and compiled to bytecode, can be loaded into a running kernel without rebuilding it. If the policy misbehaves — for instance, if a runnable task stalls because the loaded scheduler forgets to dispatch it — the kernel detects the stall and reverts the system to the fair-class scheduler automatically.

Two design choices make this layer worth taking seriously. The first is that the kernel keeps the mechanism but lets the policy float. This is not just an engineering convenience; it is a structural separation that biology relies on heavily. Cell membranes are substrate; the molecules that pass through them are policy. The substrate does not encode the message. The second is the failsafe revert. When a policy fails, the system does not crash, and it does not get stuck — it falls back to a known-good substrate and keeps running. Living systems do something analogous all the time, and it is not romantic to point that out. It is the same kind of separation, applied to a different problem.

The history is worth a sentence. The core sched_ext infrastructure was developed by Tejun Heo at Meta. One of the most successful BPF schedulers running on top of it — called LAVD, for "Latency-criticality Aware Virtual Deadline" — was developed at Igalia, originally to reduce in-game stutter on Valve's Steam Deck. In December 2025, at the Linux Plumbers Conference in Tokyo, two engineers from Meta presented an adaptation of LAVD as Meta's new default fleet scheduler.[^3] The path from a handheld gaming console to data-center fleet defaults is the inverse of the usual hyperscaler-to-consumer narrative, and I think it deserves a moment.

## Why a console scheduler ate the data center

Console gaming has a peculiar combination of properties: it is not enormously compute-intensive on a per-cycle basis, but it is brutally sensitive to tail latency, because humans notice. A frame that arrives 16 ms late is a stutter, and stutters get reviewed badly. The Steam Deck pushed scheduler work to optimize for exactly that — predictable, latency-bounded delivery on a human-timescale workload.

Data centers, until recently, did not have to optimize for that kind of constraint. Their workloads ran in the dark, behind layers of caching and queueing, and "responsive in human time" was a property of the front-end, not the scheduler. That is changing. As interactive AI workloads — LLM inference, agent loops, anything where a person is waiting for a token — come to dominate the fleet, tail latency on a human time scale becomes a property the data-center scheduler itself has to honor. The reason a Steam Deck scheduler now runs at Meta is that the constraint that defined it — humans noticing — is now a constraint Meta has too.

## The layer where the metaphor lives

Above the substrate sit the algorithms, and this is where Sörensen's critique starts to bite. Sörensen, writing about combinatorial optimization, observed that the field had drowned in methods named after natural phenomena — bee colonies, water flow, harmony searches, immune systems — most of which dissolved into ordinary mathematics once you wrote them down carefully. The biology in the title was a marketing layer. The operations were weighted sums and matrix algebra.

The same pattern is repeating in kernel scheduling. A 2025 arXiv paper called *KernelOracle* uses an LSTM to predict which task the Completely Fair Scheduler will pick next. The author, Sampanna Yashwant Kahu of Virginia Tech, is admirably forthright about the limits: he positions the work as a feasibility study, not a production-viable scheduler.[^4] More recent work in adjacent venues uses "tissue P systems" — a model originally inspired by cell membranes — as the framing for a scheduler. Read the algorithm carefully and it turns out to be matrix algebra over a regular structure, which is fine, but the cell-membrane part is a label.

One might ask, fairly, whether this is bad. Some metaphors pay for themselves by suggesting a useful formal structure. Some just give a paper a marketable hook. The trouble is not that researchers are inspired by biology — many useful methods started life as metaphors. The trouble is when the metaphor is left in place as a claim about what the algorithm *is*. When a scheduler is described as "neuromorphic" and the implementation is an event-driven arbiter that anyone working on real-time systems would have written without thinking of neurons, the biology is decoration.

## A rule of thumb that explains the placement

There is a structural reason biology-flavored ML schedulers keep landing in the same parts of the kernel. *KernelOracle* runs offline, predicting after the fact, because online inference cannot keep up with the rate at which the kernel needs to make decisions. Jim Huang's machine-learning-based load balancer, presented at OSS-NA in June 2025 and written up by LWN that July, works precisely because load balancing happens at a coarser cadence — milliseconds to seconds, not microseconds.[^5] At that cadence, neural-network inference latency can be amortized.

The rule generalizes. ML-flavored and bio-inspired heuristics tend to colonize the parts of the kernel where decisions can be made on slow time scales: load balancing, frequency governors, energy-model tuning. They are structurally pushed out of the places where decisions have to happen at the speed of the CPU's own switching. This is not a temporary state of affairs that better hardware will fix. It is a property of the time hierarchy that scheduling lives inside.

## What I think is actually worth watching

The interesting story in kernel scheduling is not that it is becoming biological. It is that the kernel has, for the first time in decades, accepted a substrate that admits experimentation without rebuilds. The substrate happens to share an abstract shape with how living systems handle policy and failure — separable mechanism, reversible failure modes, runtime mutability — and that shape is doing real work.

The question I find more interesting than any specific scheduler is who else gets to ride this substrate. The next wave that I expect to matter is sched_ext written in Rust, sitting next to a Rust-for-Linux effort that is already pushing into device drivers. The two are arriving from different directions, and the layer they will meet at is the one Linux did not have until 2024. That meeting point — not the latest paper with an LSTM in the title — is where I would look for what comes next.

---

[^1]: Sörensen, K. ["Metaheuristics—the metaphor exposed"](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001). *International Transactions in Operational Research* 22(1), 3–18, 2015. Accessed 2026-05-07.
[^2]: Phoronix. ["Sched_ext Merged For Linux 6.12 — Scheduling Policies As BPF Programs"](https://www.phoronix.com/news/Linux-6.12-Lands-sched-ext). Accessed 2026-05-07.
[^3]: Dai, D. & Newton, R. ["LAVD: Meta's New Default Scheduler"](https://lpc.events/event/19/contributions/2099/attachments/1875/4020/lpc-2025-lavd-meta.pdf). Linux Plumbers Conference 2025, Tokyo. Accessed 2026-05-07.
[^4]: Kahu, S. Y. ["KernelOracle: Predicting the Linux Scheduler's Next Move with Deep Learning"](https://arxiv.org/abs/2505.15213). arXiv:2505.15213, 21 May 2025. Accessed 2026-05-07.
[^5]: LWN. ["Improved load balancing with machine learning"](https://lwn.net/Articles/1027096/). 1 July 2025. Accessed 2026-05-07.
