# Verification Report: Institutions Can't Forgive — They Can Only Let Debts Lapse
Date: 2026-08-01

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| EEVDF vruntime/lag/eligibility mechanics, delayed dequeue mechanics | internal | .agent/books/authors/nishimura-daisuke/task-scheduler-eevdf/notes.md (2026-07-04, 2026-07-11 entries) |
| SCHED_DEADLINE / CBS / admission control mechanics | internal | .agent/books/authors/nishimura-daisuke/task-scheduler-eevdf/notes.md (2026-07-18 entry) |
| Arendt: forgiveness as political capacity, unpredictable vs. revenge (predictable); promise as island of predictability | internal | .agent/books/authors/hannah-arendt/vita-activa/notes.md (2026-04-04 entry) |
| EEVDF replaced CFS in kernel 6.6, Peter Zijlstra, based on a 1995 paper | external | https://www.phoronix.com/news/Linux-6.6-EEVDF-Likely ; https://docs.kernel.org/scheduler/sched-eevdf.html |
| Delayed dequeue / "Complete EEVDF" merged in kernel 6.12 | external | https://lwn.net/Articles/969062/ ; https://kernelnewbies.org/Linux_6.12 |
| Lag preserved across sleep to prevent gaming (deliberate sleep to reset debt) | external | https://lwn.net/Articles/969062/ ; LKML patch discussion (https://lkml.iu.edu/2411.0/01200.html) |
| SCHED_DEADLINE = EDF + CBS, admission control rejects over-budget requests | external | https://docs.kernel.org/scheduler/sched-deadline.html ; https://en.wikipedia.org/wiki/SCHED_DEADLINE |
| "Institutions implement statute of limitations, not forgiveness" — central thesis; bankruptcy/expungement/credit-score analogy; asymmetry (debts decay, credits persist) as unresolved normative question | opinion | (author's synthesis, extending the 2026-07-11 reading note's own conclusion) |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | EEVDF replaced CFS as of Linux 6.6 (Oct 2023), designed by Peter Zijlstra, roots in a 1995 paper | "Linux EEVDF scheduler Peter Zijlstra v6.6 replaced CFS" | Verified | Kept as stated; source added to References |
| F2 | Delayed dequeue / "Complete EEVDF" changes landed in kernel 6.12 (2024) | "Complete EEVDF" delayed dequeue merged Linux 6.12 kernel" | Verified | Kept as stated; source added to References |
| F3 | Lag is preserved across sleep specifically to prevent gaming via strategic sleep | "Linux "delayed dequeue" EEVDF lag v6.12 "Complete EEVDF"" | Verified | Kept as stated |
| F4 | SCHED_DEADLINE is EDF + CBS with admission control that rejects new tasks when bandwidth is exhausted | "SCHED_DEADLINE admission control CBS bandwidth reservation Linux" | Verified | Kept as stated |
| F5 | Repayment speed of a sleeping task's lag depends on system load (virtual clock advances faster when idle) | Derivable directly from F2/F3 sources (virtual-time-based decay mechanism) | Verified | Kept, no separate search needed — follows from the confirmed mechanism |

No claims were found Unverified or Contradicted. The Arendt claims (forgiveness as unpredictable political action, promise as predictability) are drawn from the author's own reading notes on *The Human Condition* rather than a live web search, since they represent settled interpretive content already vetted during the original book-study skill run; they are marked as an internal/secondary-literature source above rather than "external."

## Copyright Review
- Direct quotes: 0 (no verbatim text taken from Phoronix, LWN, kernel docs, or Arendt's text; all mechanisms are described in the author's own words)
- Paraphrased content: kernel scheduling mechanics (vruntime, lag, eligibility, delayed dequeue, SCHED_DEADLINE/CBS/admission control) are paraphrased from kernel documentation and LWN/Phoronix reporting, each with source attribution in the footnotes
- Original analysis: the central move of the article — reading delayed dequeue as an implementation of "statute of limitations rather than forgiveness," the Arendt cross-reading, the institutional generalization (bankruptcy, expungement, credit scores), and the closing question about the ledger's debt/credit asymmetry — is the author's own synthesis, not present in any single source. Estimated ~85% of the article's substantive content is original argument; ~15% is attributed factual/technical background.

## Overall Assessment
- Fact-check pass rate: 5/5 (Verified)
- Copyright risk: Low
- Ready for review: Yes
