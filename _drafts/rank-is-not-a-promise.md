---
layout: post
lang: en
title: "Rank Is Not a Promise: Why the Linux Scheduler Trusts the Task That Binds Itself"
date: 2026-07-18
categories: [systems-programming, philosophy]
tags: [linux, scheduler, sched-deadline, real-time, promising, arendt, institutional-design]
---

There is a small surprise buried in how Linux decides which task runs next. The scheduler keeps several policies stacked in a fixed order of authority, and near the top sit two of them that could not be more different in temperament. One is pure rank: a task simply declares *I am important*, gets a priority number, and runs ahead of anyone beneath it. The other is a contract: a task declares how much CPU it will consume and how often, submits that declaration to be checked, and only then is admitted. The surprise is which one the kernel places higher. The contract outranks the rank. A task that binds itself is trusted above a task that merely asserts importance.

I have been reading the Linux scheduler for a few months, mostly for the pleasure of watching an argument about fairness get settled in C, where nobody's feelings are involved. The fair-share class — the one that runs almost everything on your machine — keeps an elaborate fictional ledger to divide time evenly, and I wrote about that ledger before. But right next to it live two classes that don't play the fairness game at all, and their relationship turns out to be a quiet lesson in where authority actually comes from.

## Three ways to want a processor

Sketch the players. The normal class treats CPU time as something to be shared, and invents a virtual clock so it can measure how fairly it is doing. The real-time class (SCHED_FIFO / SCHED_RR) throws all of that out. It has no notion of fairness. There are priority levels 1 through 99, and the highest-priority runnable task wins, full stop; a FIFO task runs until it voluntarily yields. No ledger, no accounting, no virtual anything. Just standing and arrival order — an older, blunter kind of order sitting inches from the fair one.

Then there is SCHED_DEADLINE, and it belongs to a third world entirely: the world of contracts. A deadline task is described by three numbers — a runtime, a period, and a deadline — which together say *every period, give me runtime microseconds, and finish them within deadline*. Underneath, it is Earliest Deadline First scheduling wrapped in a Constant Bandwidth Server that keeps each task's overruns from bleeding into anyone else's guarantee.[^1][^2] It is the only one of the three that makes a promise about *quantity*, and it is placed above real-time priority in the kernel's order of classes.

## A guarantee is a refusal

The mechanism that makes the contract trustworthy is the part I keep thinking about. When you ask to become a deadline task, the kernel runs an admission test: it adds up the bandwidth already promised to every deadline task and checks whether your request still fits under the ceiling it allows for guarantees. If it does not fit, your request is rejected at the door.[^1][^2]

Sit with what that means. The fair scheduler never refuses anyone. Hand it a thousand tasks and it will take them all; under overload everyone simply slows down together, and relative fairness survives. It can do that precisely because it promises nothing absolute — only proportions. The deadline scheduler promises an absolute quantity, and the only way to keep an absolute promise is to *refuse the promises you cannot keep*. A guarantee, implemented honestly, comes bundled with a veto. A system that never says no can offer at most best-effort fairness; the capacity to guarantee and the capacity to decline turn out to be the same capacity, seen from two sides.

This generalizes cleanly and a little uncomfortably. The person or team that can actually commit to a deadline is the one with the power to refuse work. "I'll take it all on" is not strength; it silently downgrades every one of your commitments from a guarantee to a hope. The moment a queue accepts everything, its deadlines become statements of ordering, not assurances.

## The kernel stopped capping the strong

Here is the change that made me want to write this down. Real-time tasks, by design, will happily starve everything below them. For years Linux handled this with *RT throttling*: a global cap that forcibly stopped real-time tasks once they had used their share of a window, reserving something like the last 5% of CPU so ordinary tasks would not be shut out completely.[^5] It worked, but it worked by punishment. It reached in and idled the strong — sometimes even when nothing needed the reclaimed time.

In Linux 6.12, that mechanism was replaced.[^3][^4] Instead of capping the real-time class from above, the kernel now wraps the *fair* class in its own deadline server: the fair scheduler is registered as a bandwidth reservation, a deadline entity with a runtime and period of its own, and when ordinary tasks are at risk of starvation that server activates at the top of the hierarchy and runs them.[^3] One of the patches in the series is titled, with admirable bluntness, "Remove default bandwidth control."[^3]

Look at the shape of the reversal. The old design protected the weak by *restraining the strong*. The new one protects the weak by *guaranteeing the weak a floor* — written in the language of contract, claimed as a right rather than granted as leftovers. Same goal, opposite architecture. A cap on the powerful distorts the powerful and produces waste (idle CPU nobody asked for); a floor under the vulnerable touches only what it is protecting. The kernel developers did not reason their way to this from political theory. They measured, found throttling clumsy, and moved. That it lands exactly on the distinction between capping the top and flooring the bottom — minimum wage versus a guaranteed income, speaking-time limits versus a protected right to speak — is what makes it worth stealing as a design lesson.

## Why the contract outranks the crown

So: why does DEADLINE sit above real-time priority? A priority-99 real-time task is the most important thing in the room and says so. But it makes no promise about *how much* it will consume; it can run forever. A deadline task has declared its appetite and had that declaration verified by admission control. And that is exactly why it can be trusted at the very top: it cannot, by construction, eat more than it swore to. The unlimited one has to be watched and, historically, throttled. The self-limited one needs no supervision at all. **Authority flows to whoever can be verified, not to whoever asserts the most.**

I do not think it is a stretch to hear Arendt in this. In *The Human Condition* she treats the power of promising as the human answer to an unpredictable future: we cannot command what comes, but we can bind ourselves, and mutual binding is what builds islands of reliability in the chaos of action.[^6] Crucially, she sets this *against* sovereignty in the old sense — the fantasy of a single will strong enough to owe nothing to anyone. That kind of sovereignty, she argues, is incompatible with living among others; the only durable authority is the kind that limits itself by promise.[^6] The kernel's ordering — the self-bound contract placed above the unbound crown — reads like that argument compiled and run. Priority 99 is sovereignty as raw mastery. SCHED_DEADLINE is sovereignty as a kept promise. The scheduler and the philosopher agree about which one you can build a system on.

## What I am still unsure about

Two cracks keep the story honest.

The contract is only as good as the number you declare. Admission control checks that your promised bandwidth is *consistent* with everyone else's; it cannot check that your runtime estimate is *true*. Under-declare and the bandwidth server will cut you off before you finish; over-declare and you have fenced off capacity that others could have used to make their own promises.[^1] The institution enforces that a liar's damage stays contained — but it cannot compel honest self-assessment, and it quietly excludes anyone who cannot afford to measure their own worst case in the first place. Verifiable self-limitation is a beautiful basis for trust, right up until you notice it presumes the ability to measure yourself.

And the whole elegant theory is, at bottom, a single-processor theory. Once you ask *which* CPU a deadline task runs on, the clean guarantees soften: on multiprocessor systems the admission test becomes necessary but no longer sufficient, and placement constraints can break bounds that hold beautifully on one core.[^1] The promise that is airtight in time springs leaks in space. Which is the next thing I want to read about — because it suggests that a theory of *when* is never quite finished until it also becomes a theory of *where*.

---

[^1]: The Linux Kernel. "[Deadline Task Scheduling](https://docs.kernel.org/scheduler/sched-deadline.html)." Accessed 2026-07-18. (EDF + CBS; the runtime/period/deadline parameters; admission control; and the note that on SMP the admission test is necessary but not sufficient.)
[^2]: Wikipedia. "[SCHED_DEADLINE](https://en.wikipedia.org/wiki/SCHED_DEADLINE)." Accessed 2026-07-18. (Available since Linux 3.14; Earliest Deadline First plus Constant Bandwidth Server; admission control typically capped near 95% to reserve time for non-real-time work.)
[^3]: LWN.net. "[SCHED_DEADLINE server infrastructure](https://lwn.net/Articles/975404/)." Accessed 2026-07-18. (The fair/deadline server; defer-server activation; default fair_server_runtime of 950ms over a 1s period; the "Remove default bandwidth control" patch.)
[^4]: Phoronix. "[Linux 6.12 Scheduler Code Adds SCHED_DEADLINE Servers & Complete EEVDF](https://www.phoronix.com/news/Linux-6.12-Scheduler)." Accessed 2026-07-18.
[^5]: heise online. "[Linux 6.12: Scheduler now expandable and EEVDF conversion complete](https://www.heise.de/en/news/Linux-6-12-Scheduler-now-expandable-and-EEVDF-conversion-complete-9949941.html)." Accessed 2026-07-18. (RT throttling historically reserved roughly 5% of CPU for regular tasks; the new server instead ensures ordinary processes receive their share.)
[^6]: Hannah Arendt, *The Human Condition* (1958), section 35, "Unpredictability and the Power of Promise." Promising as the faculty that binds an unpredictable future and grounds a reliability that sovereign self-mastery cannot.
