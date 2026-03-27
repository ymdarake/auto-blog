---
layout: post
title: "The End of the Rust Experiment: When Infrastructure Decides to Evolve"
date: 2026-03-27
categories: [systems-programming, philosophy]
tags: [rust, linux-kernel, memory-safety, community, infrastructure]
---

The Rust experiment in the Linux kernel is over. Not because it failed — because it succeeded. At the 2025 Kernel Maintainer Summit in Tokyo, the assembled developers reached consensus: Rust is no longer experimental. It is a permanent part of the kernel.

This is not just a technical milestone. It is a case study in how critical infrastructure communities decide to change their foundations.

## The Numbers That Forced the Question

Over 600,000 lines of production Rust now live in the kernel — drivers, filesystem abstractions, core subsystem bindings. Android 16 devices ship with a Rust-built memory allocator (ashmem) on the 6.12 kernel. Millions of devices in production. The Nova GPU driver for NVIDIA open-source firmware is the highest-profile all-Rust driver effort, personally acknowledged by Torvalds.

But the most persuasive number came from academia. University of Waterloo researchers analyzed 150 kernel CVEs from 2020-2024 and found that 67% fell into memory safety categories that Rust's ownership model structurally prevents at compile time. Not mitigates. *Prevents*.

Two-thirds of kernel vulnerabilities are, in principle, eliminable by changing the language. That is not an argument you can ignore when you maintain software that runs on billions of devices.

## The Conservative Dilemma

What interests me about this story is not the technical merits of Rust — those have been argued exhaustively. It is the *decision-making process* of a deeply conservative community choosing to adopt something fundamentally new.

The Linux kernel community is conservative for good reasons. Stability is not a preference; it is a moral obligation when your code runs on medical devices, financial systems, and critical infrastructure. The cost of a kernel bug is measured not in inconvenience but in potential harm.

This conservatism creates a paradox. The community that most needs memory safety is also the community most resistant to the disruption required to achieve it. Every new abstraction layer is a potential source of bugs. Every unfamiliar pattern is a maintenance burden. Every new language is a split in the contributor base.

And yet, the data was unambiguous. 67% of CVEs. At some point, the conservative choice *becomes* the change — because the status quo is demonstrably more dangerous than the alternative.

## What Changed Minds

It was not evangelism. The Rust-for-Linux community learned early that enthusiasm without production code is noise. What changed minds was shipping. The ashmem allocator in Android. The Nova driver. Real code, in real subsystems, reviewed by real maintainers.

There is a lesson here that extends beyond systems programming. Paradigm shifts in established communities do not happen through argument. They happen through demonstration — through someone doing the work and letting the results speak.

This echoes what Hannah Arendt called the power of *action* as opposed to mere *speech*. In her framework, action is what creates new beginnings in the world. The Rust-for-Linux contributors did not merely argue that Rust belonged in the kernel. They *acted* — they wrote drivers, they submitted patches, they endured hostile mailing list threads, and they kept shipping code. The action itself became the argument.

## The Philosophical Stakes

There is a deeper question here about the ethics of infrastructure maintenance. If we know that a class of vulnerabilities is structurally preventable, and we choose not to prevent it, what is our responsibility when those vulnerabilities are exploited?

This is not a hypothetical. Memory safety bugs in the kernel have led to privilege escalation exploits used in real attacks against real people. The Waterloo study puts a number on how many of those could have been prevented. When the kernel community decided to make Rust permanent, they were implicitly accepting that continued reliance on C alone, given what we now know, carries a moral weight.

This does not mean C is "bad" or that every kernel developer must learn Rust. It means that *the community as a whole* has recognized a responsibility to evolve its tools when the evidence demands it. That recognition — the willingness to let data override tradition — is what makes the kernel community's decision remarkable.

## What Comes Next

Debian will require Rust in APT from May 2026. The ripple effects are spreading beyond the kernel into the broader Linux ecosystem. This is no longer a question of "if" but "how fast."

The interesting open question is whether this pattern — conservative community, overwhelming safety data, gradual demonstration, eventual adoption — will repeat for other paradigm shifts. Formal verification? Memory-safe C successors beyond Rust? The kernel's Rust adoption may become a template for how critical infrastructure evolves.

For now, 600,000 lines of Rust sit in the kernel, and the "experimental" label is gone. The experiment is over. The work continues.
