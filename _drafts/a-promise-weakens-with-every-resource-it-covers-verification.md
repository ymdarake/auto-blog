# Verification Report: A Promise Weakens With Every Resource It Covers
Date: 2026-08-15

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| EEVDF replaced CFS in kernel 6.6 (Oct 2023) | external | Phoronix "EEVDF Scheduler Merged For Linux 6.6" |
| EEVDF reduces fairness to a bounded scalar (lag) | internal | `.agent/books/authors/nishimura-daisuke/task-scheduler-eevdf/{notes,research}.md` (07-04, 07-11 notes) |
| SCHED_DEADLINE runtime/period + admission control rejects >100% bandwidth | internal + external | notes.md 07-18 entry; kernel.org sched-deadline.rst |
| sched_domain hierarchy (SMT→MC→PKG→NUMA) and load_balance heuristics (SIS_UTIL etc.) | internal | notes.md 07-29 entry (research.md summary of VA Linux blog その4) |
| "Decade of Wasted Cores" findings (idle cores, scheduling group bug, perf regressions) | external | Lozi et al., EuroSys 2016 / ACM DL |
| SCHED_DEADLINE tardiness bound fails under general CPU affinity; semi-partitioned fix only | external | RTNS 2021 paper (ACM 3453440) |
| Issue was on Zijlstra's ECRTS 2017 open-problems list | external | ECRTS 2019 Dagstuhl paper (secondary reference) |
| sched_ext merged as extensible BPF scheduler class, landed ~6.12 (late 2024) | external | Phoronix sched_ext coverage; LWN 978007 |
| "Strength of a guarantee is inversely proportional to the number of resources it covers" | opinion | author's synthesis, generalizing from the kernel case |
| Fictional clocks (vruntime) work only because CPU time is already an artificial unit; physical topology resists the same trick | opinion | author's synthesis (grounded in notes.md 07-29 self-reflection) |
| Framing DEADLINE+affinity admission as reducible to bin-packing (NP-hard) | opinion (informed by source) | RTNS 2021 abstract describes the difficulty without using "bin-packing" explicitly; the analogy is the author's own, flagged as inference in the source note |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | EEVDF replaced CFS as default in Linux 6.6, released Oct 2023 | "Linux 6.6 EEVDF replaced CFS scheduler default 2023" | Verified | Kept as stated; added Phoronix reference |
| F2 | Lozi et al. "Decade of Wasted Cores" (EuroSys 2016) reports idle-core bugs incl. scheduling-group construction bug and specific perf regressions | "Lozi Decade of Wasted Cores EuroSys 2016 Group Imbalance" | Verified | Kept; added ACM DL reference |
| F3 | SCHED_DEADLINE tardiness guarantee breaks under general CPU affinity masks; only semi-partitioned case has a workable fix | "SCHED_DEADLINE CPU affinity tardiness bound multiprocessor ACM paper" | Verified | Kept; added RTNS 2021 reference. Softened wording to match paper's actual scope (not "always breaks," but "under general affinity masks") |
| F4 | This affinity/tardiness gap was listed among Zijlstra's open problems at an ECRTS keynote | same search as F3 (secondary source) | Partially Verified | Kept but attributed to a secondary source (Dagstuhl ECRTS 2019 paper) rather than the keynote itself, which I could not access directly |
| F5 | sched_ext (BPF-extensible scheduler class) was merged into the kernel, landing around version 6.12 in late 2024 | "sched_ext eBPF Linux scheduler extensible kernel merged" | Verified | Kept as "merged into the kernel in late 2024"; avoided citing a specific version number in the body since sources gave slightly different merge-vs-release version numbers (6.11 decision, 6.12 landing) |

No claim came back Contradicted.

## Copyright Review
- Direct quotes: 0 (no blockquoted material; all findings paraphrased in the author's own words)
- Paraphrased content: several (Lozi et al. findings, RTNS 2021 findings, kernel docs on SCHED_DEADLINE) — all attributed via footnotes, no run of source text exceeds 7 words
- Original analysis: roughly 60% of the article (the two generalizing claims in "What generalizes," the framing device connecting the four-part series, and the closing question are original synthesis; no single external source contributes more than ~15% of the article's content)

## Overall Assessment
- Fact-check pass rate: 5/5 claims Verified or Partially Verified, 0 Unverified, 0 Contradicted
- Copyright risk: Low
- Ready for review: Yes
