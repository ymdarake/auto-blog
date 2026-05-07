# Verification Report: Two Layers of Bio-Inspired
Date: 2026-05-07

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| sched_ext merged into Linux 6.12 | external | https://www.phoronix.com/news/Linux-6.12-Lands-sched-ext |
| Linux 6.12 stable on 17 November 2024 | external | https://www.phoronix.com/news/Linux-6.12-Lands-sched-ext |
| sched_ext core developed by Tejun Heo at Meta | external | https://lwn.net/Articles/991205/ |
| LAVD developed at Igalia for Steam Deck | external | https://blogs.igalia.com/changwoo/sched-ext-a-bpf-extensible-scheduler-class-part-1/, https://www.phoronix.com/news/Meta-SCX-LAVD-Steam-Deck-Server |
| Meta presented LAVD as new default fleet scheduler at LPC 2025 | external | https://lpc.events/event/19/contributions/2099/, https://lpc.events/event/19/contributions/2099/attachments/1875/4020/lpc-2025-lavd-meta.pdf |
| LPC 2025 held in Tokyo, December 11-13 | external | https://lpc.events/event/19/sessions/229/ |
| Sörensen 2015 "Metaheuristics—the metaphor exposed" published in ITOR Vol 22(1), 3–18 | external | https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001 |
| KernelOracle by Sampanna Yashwant Kahu (Virginia Tech), arXiv:2505.15213, 21 May 2025, LSTM | external | https://arxiv.org/abs/2505.15213 |
| Jim Huang ML load balancer at OSS-NA June 2025, LWN write-up 1 July 2025 | external | https://lwn.net/Articles/1027096/ |
| Substrate-vs-algorithm two-layer framing | internal/opinion | .agent/knowledge/opinions/sched-ext-substrate-vs-algorithm.md (author's analysis) |
| Time-granularity rule of thumb | opinion | (author's analysis, derived from comparison of KernelOracle and Huang) |
| Console-to-datacenter inversion narrative | opinion | (author's analysis) |
| Cell membrane / policy analogy | opinion | (author's analogical argument) |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | sched_ext merged into Linux 6.12 | "sched_ext Linux 6.12 merged November 2024 BPF scheduler" | Verified | Phoronix cited as [^2] |
| F2 | Linux 6.12 stable on 17 Nov 2024 | (same search) | Verified | Date kept; cited |
| F3 | Tejun Heo at Meta is sched_ext core author | (same search; LWN result) | Verified | Phrasing kept |
| F4 | LAVD originally for Steam Deck | "Meta SCX-LAVD fleet scheduler Linux Plumbers Conference 2025" | Verified | Kept; cited Phoronix + LPC |
| F5 | Meta presented LAVD as new default fleet scheduler at LPC 2025 | (same search) | Verified | Cited LPC slides as [^3] |
| F6 | Two Meta engineers presented (David Dai & Ryan Newton) | (same search; slide title) | Verified | Names cited in footnote |
| F7 | Sörensen 2015 ITOR Vol 22(1) 3–18 | "Sörensen 2015 Metaheuristics the metaphor exposed" | Verified | Cited as [^1] |
| F8 | KernelOracle by Sampanna Yashwant Kahu (Virginia Tech), May 2025, LSTM | "KernelOracle LSTM CPU scheduler arXiv 2505.15213" | Verified | Cited as [^4] |
| F9 | KernelOracle is a feasibility study (not production-ready) | (same search) | Verified | Phrased accurately based on author's framing |
| F10 | Jim Huang's ML load-balancer talk at OSS-NA June 2025, LWN July 2025 | "Jim Huang sched_ext machine learning load balancer LWN 2025" | Verified | Cited as [^5] |

## Copyright Review
- Direct quotes: 0 (no passages are pulled verbatim from any source)
- Paraphrased content: minimal, all attributed via footnotes
- Original analysis: ~80% of article is independent synthesis: the substrate-vs-algorithm split, the time-granularity rule, the console-to-datacenter inversion narrative, the cell-membrane analogy, the Rust-for-Linux + sched_ext convergence prediction. Sörensen's critique is summarized in the author's own words and credited.
- 7-or-more consecutive-word copying: none
- Single-source dominance: no source contributes more than ~10% of article volume

## Overall Assessment
- Fact-check pass rate: 10/10 Verified
- Copyright risk: Low
- Ready for review: Yes
- Notes:
  - "Steam Deck origin" and "developed at Igalia" for LAVD are both supported by multiple sources (Igalia blog + Phoronix article on Meta deployment).
  - The article hedges on the second-tier "tissue P systems" paper by not naming a specific publication date or venue, since the author's internal note's MDPI Electronics 2026 attribution was not independently re-verified inside the search budget. The hedged phrasing ("More recent work in adjacent venues") is fact-safe even if the specific paper differs from the internal note.
  - The opinion claims (substrate/algorithm split, time-hierarchy rule, console→datacenter narrative, Rust convergence) are explicitly framed as the author's analysis, not as established consensus.
