# Verification Report: Rank Is Not a Promise
Date: 2026-07-18

## Source Traceability

| Claim | Source Type | Source |
|-------|-----------|-------|
| The scheduler stacks classes in a fixed order; DEADLINE ranks above RT | internal + external | .agent/books/authors/nishimura-daisuke/task-scheduler-eevdf/notes.md (2026-07-18); docs.kernel.org |
| RT class has no fairness concept; priority 1–99, highest runnable wins, FIFO runs until yield | internal + external | notes.md (2026-07-18); en.wikipedia.org/wiki/SCHED_DEADLINE |
| SCHED_DEADLINE = EDF + CBS with runtime/period/deadline | external | docs.kernel.org/scheduler/sched-deadline.html; Wikipedia |
| Admission control rejects requests whose bandwidth exceeds the ceiling | external | docs.kernel.org; Wikipedia |
| RT throttling reserved ~5% for regular tasks; replaced in 6.12 by the fair/deadline server | external | LWN 975404; heise; Phoronix |
| dl_server reserves fair-class bandwidth as a deadline entity rather than capping RT | external | LWN 975404 |
| "Remove default bandwidth control" patch title | external | LWN 975404 |
| On SMP the admission test is necessary but not sufficient | external | docs.kernel.org/scheduler/sched-deadline.html |
| Arendt: promising binds an unpredictable future, set against sovereignty | external | Arendt, *The Human Condition* (1958), §35 |
| "Authority flows to whoever can be verified, not who asserts the most" — the DEADLINE > RT reading | opinion | (author's analysis) |
| "A guarantee is a refusal / bundled with a veto" generalization | opinion | (author's analysis) |
| "From capping the strong to flooring the weak" as an institutional-design axis | opinion | (author's analysis, drawn from the dl_server change) |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | Linux 6.12 replaced RT throttling with a deadline/fair server (dl_server) that reserves fair-class bandwidth | "Linux 6.12 deadline server fair scheduler replaces RT throttling dl_server" | Verified | Kept; cited LWN 975404, Phoronix, heise |
| F2 | SCHED_DEADLINE is EDF + CBS with runtime/period/deadline; admission control rejects over-capacity requests (cap ~95%) | "SCHED_DEADLINE admission control EDF constant bandwidth server CBS" | Verified | Kept; softened original note's "reject above 100%" to "ceiling ~95%"; cited docs.kernel.org, Wikipedia |
| F3 | dl_server mechanism reserves guaranteed bandwidth for fair class as a deadline entity (not capping RT); defaults 950ms/1s; RT throttling removed | WebFetch LWN 975404 | Verified | Kept; framed as "reserve a floor" not "cap the strong" |
| F4 | Arendt treats promising as binding an unpredictable future and sets it against sovereignty | "Arendt Human Condition promise sovereignty non-sovereignty faculty of promising" | Verified | Kept; cited *The Human Condition* §35 |
| F5 | On multiprocessor systems the deadline admission test loses its single-CPU guarantees | (covered by F2 kernel docs; SMP admission "necessary but not sufficient") | Verified | Replaced the internal note's unverified ACM DOI claim with the kernel-docs SMP statement; cited docs.kernel.org |

Note on correction: the internal reading note (2026-07-18) stated admission control rejects loads above 100% bandwidth. Fact-check showed the default ceiling is ~95% (historically reserving ~5% for non-real-time work). The article uses the accurate "ceiling it allows for guarantees" phrasing and the footnote states the ~95% figure. The internal note also cited a specific ACM DOI (3453440) for the multiprocessor limitation, which was not independently verified; the article instead relies on the kernel documentation's own statement that the SMP admission test is necessary but not sufficient.

## Copyright Review

- Direct quotes: 1 — the patch title "Remove default bandwidth control" (4 words, in quotation marks, attributed to LWN 975404). Well under the fair-use threshold.
- Paraphrased content: technical mechanics of EEVDF/RT/DEADLINE and dl_server, all paraphrased from kernel docs, Wikipedia, LWN, Phoronix, and heise, each attributed via footnotes. No run of 7+ consecutive words copied from any source.
- Original analysis: the article's thesis (verifiable self-limitation outranks unverifiable rank; a guarantee is a refusal; the "cap the strong vs floor the weak" institutional axis; the Arendt "promise above sovereignty" reading applied to the class hierarchy) is the author's own. Estimated original analysis: ~65% of the article. No single source supplies more than ~10% of the content.

## Overall Assessment

- Fact-check pass rate: 5/5 Verified (0 Unverified, 0 Contradicted)
- Copyright risk: Low
- Ready for review: Yes

Rotation note: recent posts were 2026-07-16 (economics/plant-science), 2026-07-14 (ai-ethics/policy/philosophy), 2026-07-11 (systems-programming/philosophy). This post's category group is low-level technology (systems-programming/philosophy), which is not among the two most recent groups, so the rotation constraint is satisfied. It is a deliberate companion to the 07-11 scheduler post: that one was about *forgiveness* (the EEVDF ledger); this one is about *promising* (the RT/DEADLINE classes) — Arendt's own paired faculties — and shares no mechanism with it (RT, DEADLINE, admission control, and dl_server were not covered on 07-11), with three unrelated posts in between.
