# Verification Report: You Cannot Sleep Off a Debt: What a CPU Scheduler Knows About Forgiveness
Date: 2026-07-11

## Source Traceability

| Claim | Source Type | Source |
|-------|-------------|--------|
| EEVDF replaced CFS in Linux 6.6; origin is Stoica & Abdel-Wahab (1995); driven by Peter Zijlstra | external | https://en.wikipedia.org/wiki/Earliest_eligible_virtual_deadline_first_scheduling / https://www.phoronix.com/news/Linux-6.6-EEVDF-Likely |
| EEVDF conversion "completed" in Linux 6.12 | external | https://www.heise.de/en/news/Linux-6-12-Scheduler-now-expandable-and-EEVDF-conversion-complete-9949941.html |
| vruntime = real time ÷ weight; lag = deviation from ideal share; positive lag = owed CPU, negative = overdrawn | external | https://docs.kernel.org/scheduler/sched-eevdf.html |
| Only tasks with lag ≥ 0 are eligible; earliest virtual deadline among eligible tasks runs next | external | https://docs.kernel.org/scheduler/sched-eevdf.html |
| Discarding lag on sleep would let tasks game the system by napping at the end of a slice | external (direct quote) | https://lwn.net/Articles/969062/ |
| Delayed dequeue: sleeping task with negative lag stays queued but ineligible; lag decays with virtual runtime until zero | external | https://lwn.net/Articles/969062/ + https://docs.kernel.org/scheduler/sched-eevdf.html |
| Sum of all lag values in the system is always zero | external (paraphrase of a stated property) | https://lwn.net/Articles/969062/ |
| Custom time slices via sched_setattr(), allowed range 100µs–100ms | external | https://lwn.net/Articles/969062/ |
| OSPM 2026: next-buddy shortcut bypasses EEVDF's pick; delayed-dequeue tasks with short deadlines block shorter-slice preemption; fixes bring 99.9p latency below ~700µs vs ~4ms | external | https://lwn.net/Articles/1078696/ |
| Arendt: forgiving addresses irreversibility, promising addresses unpredictability | external | Hannah Arendt, *The Human Condition* (1958) |
| "Fairness is not observable, so the metric's design becomes the definition of the value" | opinion | internal notes: .agent/books/authors/nishimura-daisuke/task-scheduler-eevdf/notes.md (2026-07-04) |
| "Institutions cannot implement forgiveness, only a statute of limitations" | opinion | internal notes: same file (2026-07-11) — author's analysis |
| Asymmetry reading (debt decays while asleep, credit is held until you run; human ledgers may lean the opposite way) | opinion | internal notes (2026-07-11); explicitly hedged in the article as a suspicion, not a finding |
| "De-paradoxing relocates the paradox rather than removing it" | opinion | author's analysis, drawing on Luhmann reading (knowledge/opinions/luhmann-decision-paradox.md) |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|--------------|--------|--------|
| F1 | EEVDF replaced CFS in 6.6; Zijlstra 2023; Stoica & Abdel-Wahab 1995 | "EEVDF scheduler Linux 6.6 replaced CFS Peter Zijlstra Stoica Abdel-Wahab 1995" | **Verified** (Wikipedia, Phoronix, kernel docs agree) | Kept; footnotes [^1][^2] added |
| F2 | Delayed dequeue keeps sleeping task queued until lag elapses; lag preserved to block strategic sleeping | "Linux 6.12 delayed dequeue EEVDF complete lag negative sleep" | **Verified** (LWN 969062, kernel docs, LKML patch series) | Kept; direct quote from LWN in blockquote with attribution |
| F3 | EEVDF conversion completed in 6.12 | "Linux 6.12 EEVDF complete delayed dequeue merged sched_setattr" | **Verified** (heise, Phoronix, LWN) | Kept; footnote [^4] |
| F4 | Custom slice range is 100µs–100ms via sched_setattr / sched_runtime | fetched https://lwn.net/Articles/969062/ | **Verified** — LWN states "The allowed range for time slices is 100µs to 100ms." | Kept as stated |
| F5 | Sum of all lag values is always zero | fetched https://lwn.net/Articles/969062/ | **Verified** — LWN states the sum of all lag values in the system is always zero | Kept |
| F6 | OSPM 2026 discussion: next-buddy shortcut, delayed-dequeue bias, 99.9p latency <700µs vs ~4ms | fetched https://lwn.net/Articles/1078696/ | **Verified** (LWN OSPM 2026 day-two report, Vincent Guittot's session) | Kept, but hedged with "reportedly" on the latency figure since it is a conference-report number, not a published benchmark |
| F7 | Arendt on forgiving/promising (irreversibility / unpredictability) | not searched — canonical, from *The Human Condition* (read 2026-04-04, notes on file) | **Verified** (canonical text, well-established reading) | Paraphrased, not quoted; attributed with book + year |

**Note on an earlier claim that was dropped:** the internal notes stated that positive lag "cannot be hoarded indefinitely (bounded by renormalization)" with a self-flagged uncertainty. I could not verify the exact bounding mechanism, so the article does not make that claim at all — it only states that credit is held until the task runs.

## Copyright Review

- **Direct quotes: 2** — one sentence from the kernel documentation (16 words) and one sentence from LWN (39 words). Both are in blockquotes with inline attribution and footnoted sources. Both are under the 40-word limit.
- **Paraphrased content: 5** (delayed-dequeue mechanism, zero-sum lag property, custom slice range, OSPM 2026 findings, Arendt's forgiving/promising pair) — all carry source attribution in the text or footnotes.
- **Single-source dependency:** LWN 969062 supports 3 claims but supplies well under 10% of the article's text; no passage of 7+ consecutive words is copied outside the two attributed blockquotes.
- **Original analysis:** roughly 65% of the article — the "metric design = value definition" argument, the debtor-lenient/creditor-honest asymmetry, the forgiveness-vs-statute-of-limitations thesis, the congestion-coupled-expiry proposal, and the closing "relocated, not removed" argument are all the author's, developed in internal reading notes on 2026-07-04 and 2026-07-11.

## Overall Assessment

- Fact-check pass rate: **7/7 Verified** (0 Unverified, 0 Contradicted)
- Copyright risk: **Low**
- Ready for review: **Yes**

Caveats carried into the text rather than removed:
- The claim that human ledgers are asymmetric the *opposite* way (failures persist, contributions are forgotten) is explicitly labeled in the article as a suspicion without data.
- The OSPM 2026 latency figures are attributed with "reportedly" because they come from a conference report.
- Version-dependent statements are anchored to kernel versions (6.6, 6.12) rather than to "currently," so they will not silently rot.
