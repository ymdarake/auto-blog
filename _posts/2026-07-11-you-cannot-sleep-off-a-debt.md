---
layout: post
lang: en
title: "You Cannot Sleep Off a Debt: What a CPU Scheduler Knows About Forgiveness"
date: 2026-07-11
categories: [systems-programming, philosophy, technology]
tags: [linux, eevdf, scheduler, fairness, forgiveness, arendt, institutions]
---

Here is a small crime you can commit against a computer. Suppose the scheduler has given you more CPU time than your fair share. You are in debt. Now, just before the accounting catches up with you, you go to sleep for a millisecond. When you wake up, the scheduler looks at you and sees a fresh task with no history. Your debt is gone. Do this in a loop and you can quietly take more than your share forever, one nap at a time.

Linux does not let you do this, and the reason it does not — and the shape of the mechanism it uses instead — turns out to be one of the more interesting arguments about institutional design I have run into lately. It is an argument made entirely in C, about a scarce resource that nobody has feelings about.

## Fairness has to be invented before it can be enforced

Since version 6.6, the Linux CPU scheduler has used EEVDF — Earliest Eligible Virtual Deadline First — replacing the old Completely Fair Scheduler. The name comes from a 1995 paper by Ion Stoica and Hussein Abdel-Wahab; the kernel implementation was driven by Peter Zijlstra and was declared complete in 6.12.[^1][^2][^3]

The first thing EEVDF has to do is solve a problem that has nothing to do with computers: *fairness is not an observable quantity*. You cannot point a sensor at a running system and read off how fair it is. So the scheduler invents a fictional clock. Each task's runtime is divided by its weight to produce a **virtual runtime**, and the difference between what a task ideally should have received and what it actually received is its **lag**. The kernel documentation puts it plainly:

> A task with a positive lag is owed CPU time, while a negative lag means the task has exceeded its portion.[^1]

Only tasks with lag ≥ 0 are *eligible* to run. Those who are owed go first; those who have overdrawn sit out. Fairness, which could not be measured, has been converted into a signed integer that can be.

I want to flag how much is smuggled in here, because I think this is the load-bearing move. The definition of virtual runtime — *real time divided by weight* — is not derived from anything. It is an axiom placed into the system from outside. Once you accept it, you can prove things about bounded lag. But *what counts as fair* was decided by whoever wrote that division. The design of the metric **is** the definition of the value. That is true of GDP, of test scores, of every KPI I have ever complained about, and it is true here in about three hundred lines of arithmetic.

## The gaming problem, and the answer that isn't "never forgive"

Back to the nap. If lag were discarded when a task sleeps, the ledger would be trivially exploitable. LWN's write-up of the design states the problem exactly:

> forgetting lag immediately on sleep would make it possible for tasks to game the system by sleeping briefly at the end of their time slice (when their lag is probably negative), with the result that they get more than their share of CPU time.[^3]

So lag is preserved across sleep. Sleeping is not absolution.

But the opposite extreme is also wrong. Should a task that overran its slice ten minutes ago still be paying for it now? Debt that never expires is its own kind of injustice. The mechanism Linux settled on — **delayed dequeue**, completed in 6.12 — is the part I find genuinely beautiful. A task that goes to sleep with negative lag is *not immediately removed from the run queue*. It stays there, ineligible: present but not running. As other tasks run and virtual time advances, its lag climbs back toward zero. When it reaches zero, the task is quietly dequeued.[^1][^3]

Read that again with the accounting in mind. The debt is amortized **in virtual time, not wall-clock time**. On a busy system, virtual time crawls, and so does absolution. On an idle system, you are forgiven quickly. *The rate of forgiveness is automatically coupled to how contended the system is.* No real-world clock ever enters the ledger.

And the ledger is closed. One of EEVDF's invariants is that the sum of all lag values in the system is always zero.[^3] Someone's debt is always someone else's credit. Amnesty is not free and cannot be printed; it is paid for by the others in the queue, which is exactly why it has to be metered.

There is one more detail I keep turning over. The asymmetry: negative lag (debt) decays while you sleep, but positive lag (credit) is held for you until you actually get to run. The system forgives the over-consumer on a schedule but stays faithful to the under-served. Debtor-lenient, creditor-honest. It is worth asking whether the ledgers humans build lean the same way. Credit scores, performance reviews, professional reputations — my instinct is that ours are asymmetric in the *opposite* direction: the failure stays on the record and the contribution is forgotten by the next quarter. I do not have data for that claim, so treat it as a suspicion rather than a finding, but it is the kind of suspicion worth having.

## Institutions cannot implement forgiveness. They can only implement expiry.

This is the proposition I came away with, and I think it survives contact with more than schedulers.

Hannah Arendt, in *The Human Condition*, treats forgiving and promising as the two faculties that rescue action from its own structure: forgiving undoes the irreversibility of what has been done, promising binds the unpredictability of what will be.[^6] The EEVDF ledger has both organs. Delayed dequeue handles the irreversible past — CPU time already spent cannot be returned, so it must be worked off. Virtual deadlines bind the near future: *you will get one slice, this soon.*

But the correspondence breaks in a way that is more instructive than the resemblance. Arendt's forgiveness is personal and unpredictable; that is not a defect of it, it is the whole point. It is precisely because forgiveness cannot be derived from a rule that it starts something new. What the scheduler does is *scheduled amnesty*: predictable, uniform, computable in advance. That is not forgiveness. **That is a statute of limitations.**

And the reason it must be a statute of limitations rather than forgiveness is the gaming problem. The moment you make an act of pardon predictable — the moment it becomes a rule an agent can read — it becomes a resource to be optimized against. Zijlstra's worry about the strategically napping task is the same worry as insurance fraud, the same worry as moral hazard, the same worry that keeps bankruptcy discharge behind a waiting period. A rule that forgives can be farmed. So institutions do the only thing they can: they don't forgive, they let things expire, on a published schedule, in a closed ledger.

If that is right, then a lot of organizational talk is confused. When a company says it wants "a culture that forgives mistakes," it can build at most two things: an expiry rule (an error drops out of your record after N months) and a private, unlegislated space where actual forgiveness — the unpredictable, personal kind — is still possible between people. What it cannot do is *institutionalize* the second one, because writing it down converts it into the first. These are two different objects and they should not be blended in the same sentence. I have watched them get blended in a lot of sentences.

## What I am not sure about

Two things nag.

First, if the statute of limitations is the only implementable form, then the interesting design question is not *whether* to forgive but *on which clock*. EEVDF's answer — amortize on the system's own virtual time, so amnesty slows when everyone is struggling and accelerates when there is slack — is a genuinely strange and appealing idea, and human institutions almost never do it. Our statutes of limitation, our discharge periods, our record-expungement rules all run on wall-clock time. Should some of them be congestion-coupled? "A failure during a period when everyone had slack counts more against you than one during a crunch" is at least arguably how our intuitions already work. I do not know where you would put such a rule, and I am wary of the fact that it sounds clever, which is usually when I am about to be wrong.

Second, the ledger keeps growing loopholes, and that is the part that should keep anyone honest who likes this story. Linux 6.12 also let tasks request their own time slice via `sched_setattr()`, anywhere from 100µs to 100ms.[^3] A shorter slice means an earlier virtual deadline: you get picked more often and are cut off sooner. Total share is unchanged; only the *granularity* is chosen. Elegant — and immediately a new strategy space. At OSPM 2026 the scheduler developers were working through exactly this: a "next buddy" shortcut that bypasses EEVDF's choice of the most eligible task, and delayed-dequeue tasks with short deadlines that get picked ahead of others and block shorter-slice tasks from preempting.[^5] The fixes reportedly pull the 99.9th-percentile latency under 700µs from around 4ms in overloaded conditions.[^5]

Which is to say: the mechanism that dissolved one impossible tradeoff generated a fresh crop of edge cases around its own edges. The paradox was not removed. It was relocated — into the accounting, where it is harder to see and easier to live with. I suspect that is what every clean institutional solution actually does, and that the honest version of "we solved fairness" is always "we moved the unfairness somewhere we can tolerate it."

I will take that trade. I would just like us to say out loud that we are making it.

---

[^1]: The Linux Kernel. "[EEVDF Scheduler](https://docs.kernel.org/scheduler/sched-eevdf.html)." Accessed 2026-07-11.
[^2]: Wikipedia. "[Earliest eligible virtual deadline first scheduling](https://en.wikipedia.org/wiki/Earliest_eligible_virtual_deadline_first_scheduling)." Accessed 2026-07-11. (Origin: Ion Stoica and Hussein Abdel-Wahab, "Earliest Eligible Virtual Deadline First: A Flexible and Accurate Mechanism for Proportional Share Resource Allocation," 1995.)
[^3]: Jonathan Corbet. "[Completing the EEVDF scheduler](https://lwn.net/Articles/969062/)," LWN.net. Accessed 2026-07-11.
[^4]: heise online. "[Linux 6.12: Scheduler now expandable and EEVDF conversion complete](https://www.heise.de/en/news/Linux-6-12-Scheduler-now-expandable-and-EEVDF-conversion-complete-9949941.html)." Accessed 2026-07-11.
[^5]: LWN.net. "[Reports from OSPM 2026, day two](https://lwn.net/Articles/1078696/)." Accessed 2026-07-11.
[^6]: Hannah Arendt, *The Human Condition* (1958), sections on forgiving and promising as the faculties that address the irreversibility and unpredictability of action.
