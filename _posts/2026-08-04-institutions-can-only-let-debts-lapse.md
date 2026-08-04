---
layout: post
lang: en
title: "Institutions Can't Forgive — They Can Only Let Debts Lapse"
date: 2026-08-01
categories: [systems-programming, philosophy]
tags: [linux, scheduler, eevdf, arendt, forgiveness, institutional-design]
---

There's a small accounting problem buried in how Linux decides which process gets the CPU next, and it turns out to be the same problem every institution faces when it tries to be merciful: what do you do with a debt that the debtor didn't fully repay?

The scheduler in question is EEVDF (Earliest Eligible Virtual Deadline First), which replaced the older Completely Fair Scheduler as Linux's default policy for ordinary processes starting with kernel 6.6 in late 2023.[^1] Its job is to divide a scarce, real resource — CPU time — fairly among competing tasks. To do that, it invents a fictional clock.

## A ledger for a resource nobody can see fairly

"Fair" isn't something you can observe directly. So EEVDF measures a proxy instead: **vruntime**, virtual runtime, which is real CPU time divided by a task's priority weight. A high-priority task's virtual clock ticks slower for the same amount of real work. The scheduler also tracks **lag** — the gap between how much virtual time a task has actually consumed and how much it would have consumed under a perfectly fair split. Positive lag means a task is owed CPU time; negative lag means it has spent more than its fair share and is, in effect, in debt.

Only tasks with lag ≥ 0 are "eligible" to run at all. A task that has overspent has to wait until its debt clears. It's a strikingly moralized piece of engineering: the one who has taken more than their share loses the right to go first, until the books balance again.

## The gaming problem, and the fix

Here's where it gets interesting. What happens when an indebted task goes to sleep — say, it's blocked waiting on I/O? The naive answer is to just forgive the debt on wake-up: start fresh. But Peter Zijlstra, the scheduler's designer, rejected that outright, because it's exploitable. A task could deliberately yield the CPU for a moment right after overspending, wipe its negative lag, and wake up with a clean slate — a scheduling loophole a sufficiently adversarial program could ride indefinitely.

So lag is **preserved across sleep**. But the opposite policy — never forgiving, holding the debt forever — is also wrong; a task that briefly overspent years ago shouldn't be penalized permanently. The eventual answer, merged as part of the "Complete EEVDF" changes in kernel 6.12 (2024), is a mechanism called **delayed dequeue**.[^2] A task with negative lag that goes to sleep isn't removed from the run queue immediately. It stays there, ineligible, quietly present, while other tasks run and the system's virtual clock advances. As that clock ticks forward, the sleeping task's lag drifts back toward zero. Once it crosses the threshold, it's finally dequeued — the debt has been repaid entirely through the passage of *virtual* time, not wall-clock time. Repayment speeds up when the system is idle and slows down when it's busy, because the virtual clock's pace depends on how much competition there is for the CPU.

This is a genuinely elegant piece of design: the same currency used to measure the debt is used to discharge it. But notice what kind of act this is. It is not forgiveness. It is **amortization on a schedule** — mechanical, predictable, indifferent to whether the debtor is sorry, indifferent to circumstance. It is, in a word one might not expect to reach for in a kernel changelog, a *statute of limitations*.

## What forgiveness actually requires

Hannah Arendt drew a sharp line between forgiveness and anything rule-based. In *The Human Condition*, she treats forgiveness as a genuinely political capacity — distinct from religious mercy or private sentiment — whose entire function is to undo the otherwise irreversible consequences of action. What makes it forgiveness, in her account, and not mere absorption of a debt, is that it is *unpredictable*. It is itself a new action, not the execution of a rule. Revenge is predictable — you can compute it in advance from the offense. Forgiveness cannot be; if it could, it would just be another mechanical response, and the one thing it specifically does — release the actor from the consequences of what they did, without erasing that the thing happened — would collapse into bookkeeping.

Arendt's companion concept, the promise, does the opposite work: it's how humans introduce a small island of predictability into an otherwise unpredictable future, by binding themselves in advance. Between the two, she thought, humans could survive the two structural hazards of action: its irreversibility (forgiveness) and its unpredictability (the promise).

Put the kernel and the philosopher side by side and a claim falls out that I didn't expect going in: **institutions can implement the promise, and they can implement something that behaves like forgiveness from a distance, but what they actually implement is a statute of limitations, not forgiveness itself.** Delayed dequeue is a real technical achievement precisely because it stopped pretending to forgive and built an honest, rule-governed amortization schedule instead. It doesn't ask whether the task meant to overspend, or has since reformed. It just counts virtual time.

## Where this lands outside the kernel

I think this generalizes further than it looks. Bankruptcy discharge, criminal record expungement, credit-score decay, even the "cooling off" period before you're allowed to re-litigate a settled argument — these are all institutional analogues of delayed dequeue: negative lag held on the books, decaying on a fixed and known schedule, released once a threshold is crossed. None of them are forgiveness in Arendt's sense, and I don't think that's a design flaw. It's arguably the *correct* division of labor. A rule that always forgives can be gamed exactly the way the naive scheduler could — sleep at the right moment, wipe the ledger, repeat. A rule that never forgives calcifies a system around every past mistake, which is its own kind of dysfunction. What EEVDF's designers landed on is the version of mercy that survives contact with adversarial actors: forgiveness is not scalable, but its shadow — an amortization schedule administered without regard to intent — is. If an institution wants to build in something adjacent to grace, statute-of-limitations logic seems to be the only version that resists gaming, and that comes at the explicit cost of not being forgiveness.

What I haven't settled is whether that cost is a loss worth naming out loud. If every institutionalized "second chance" is secretly a debt-decay function rather than an act of grace, does calling it forgiveness — the way we routinely do, in parole boards, in "clean slate" laws, in credit repair — quietly launder something that a Zijlstra-style engineer would insist on calling by its real name? Or is the language of forgiveness doing useful work anyway, giving a mechanical process a human face it doesn't technically deserve, and is that dishonesty itself functional? I don't have a confident answer yet, and the asymmetry in EEVDF's ledger only sharpens the question: debts decay over time, but credits — CPU a task was owed and never got — are preserved indefinitely, until the task actually runs. The system is patient with what it owes you and exacting about what you owe it. I'm not sure yet whether that's the shape a just institution should have, or the shape institutions default to because it's the one that can't be exploited.

---

[^1]: Michael Larabel. "[EEVDF Scheduler May Be Ready For Landing With Linux 6.6](https://www.phoronix.com/news/Linux-6.6-EEVDF-Likely)." Phoronix. Accessed 2026-08-01. See also the kernel documentation: "[EEVDF Scheduler](https://docs.kernel.org/scheduler/sched-eevdf.html)." The Linux Kernel documentation. Accessed 2026-08-01.
[^2]: Jonathan Corbet. "[Completing the EEVDF scheduler](https://lwn.net/Articles/969062/)." LWN.net. Accessed 2026-08-01. Delayed dequeue and the "Complete EEVDF" changes landed in Linux 6.12; see "[Linux_6.12](https://kernelnewbies.org/Linux_6.12)." Linux Kernel Newbies. Accessed 2026-08-01.
