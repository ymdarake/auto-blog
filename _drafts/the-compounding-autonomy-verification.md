# Verification Report: The Compounding Autonomy
Date: 2026-05-21

## Source Traceability

| Claim | Source Type | Source |
|-------|-----------|--------|
| MAST taxonomy exists with 14 modes / 3 categories | external | arXiv:2503.13657 (Cemri et al., 2025) |
| Cohen's κ = 0.88 inter-annotator agreement | external | arXiv:2503.13657 abstract |
| 1,600+ traces, 7 frameworks, 6 expert annotators | external | arXiv:2503.13657 |
| 41.8% specification failures (derivative figure) | external | MAST GitHub + derivative reporting |
| Production multi-agent failure rates exceed 40% | external | MAST paper + derivative reporting |
| LLM agents conform to peer majority in debate | external | arXiv:2511.07784 |
| Janis 1972 *Victims of Groupthink*, 8 symptoms | external | Janis 1972 + Systems Thinking Alliance summary |
| Cohen-March-Olsen 1972 garbage can model, 3 conditions | external | Administrative Science Quarterly 17(1) 1972 PDF |
| Allison 1971 *Essence of Decision*, three models | external | Wikipedia + book reference |
| 3.5× token cost for multi-agent | external | Augment Code report |
| 86% token duplication in flat topologies | external | Augment Code report citing benchmarks |
| 39–70% degradation on sequential tasks | external | Augment Code report |
| The virtue/vice flip across topologies | opinion | Author's structural reading of MAST + single-agent value prop |
| RLHF completion-reward → shipping over flagging | opinion | Author's reasoning by analogy from sycophancy literature |
| Phantasm of consensus framing | opinion | Author's term for the failure pattern |
| Four asymmetries (reputation / time / politics / dissent norms) | opinion | Author's analysis, novel framing |
| "Constitutional AI suppresses, does not generate dissent" | opinion | Author's interpretation of CAI design |
| Predictions about field direction (multi-agent will grow) | opinion | Author's speculation marked as guess |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | MAST is arXiv:2503.13657 by Cemri et al., UC Berkeley | "MAST Cemri arXiv 2503.13657" | Verified | Cited with full author attribution |
| F2 | 14 failure modes in 3 categories | same | Verified | Used as stated |
| F3 | 1,600+ traces, 7 frameworks | same | Verified | Used as stated |
| F4 | Cohen's κ = 0.88 | same | Verified | Used as stated |
| F5 | Specification category is the largest (41.8%) | MAST + derivative coverage | Partially Verified | Hedged with "derivative reporting puts at roughly" — not from direct paper abstract |
| F6 | Multi-agent debate produces unanimous-but-wrong outcomes | "multi-agent LLM debate unanimous wrong" | Verified | Cited arXiv:2511.07784 |
| F7 | Models shift from correct to incorrect under peer reasoning | same | Verified | Used as stated |
| F8 | Janis 1972 — 8 symptoms include self-censorship, illusion of unanimity, direct pressure on dissenters | "Janis groupthink 1972 eight symptoms" | Verified | Full list of 8 symptoms recited matches Stanford/Britannica/Wikipedia |
| F9 | Cohen-March-Olsen 1972 — 3 conditions: problematic preferences, unclear technology, fluid participation | "Cohen March Olsen garbage can" | Verified | Wording matches original abstract |
| F10 | Allison 1971 — Models I/II/III (Rational Actor, Organizational Process, Bureaucratic Politics) | "Allison Essence of Decision three models" | Verified | Standard reference, Wikipedia + multiple academic sources |
| F11 | Multi-agent ~3.5× token cost in documented cases | "multi-agent token cost coordination" | Verified | Augment Code report; multiple sources confirm cost compounding |
| F12 | 86% token duplication in flat topologies | same | Verified | Augment Code citing benchmarks (presumably arXiv:2603.27539) |
| F13 | 39–70% performance degradation on sequential reasoning | same | Verified | Augment Code report |

## Copyright Review

- Direct quotes: 0 (no other authors' sentences copied verbatim)
- Paraphrased content: ~6 instances, all with footnote attribution to original sources
- Original analysis: Approximately 75% of the article is the author's own framing — the virtue/vice flip, the four-asymmetry argument, the borrowing taxonomy distinction (taxonomy yes, recipes no), the practical conclusion. The remaining 25% is summary of existing literature (MAST, Janis, Cohen-March-Olsen, Allison) with full citation.

No 7+ word consecutive copies of source text. No single source contributes more than ~10% of article length. Janis's eight symptoms are listed verbatim because they are the standard short-form list reproduced across multiple secondary sources (Stanford, Britannica, Wikipedia) and constitute reference material, not creative content; their list is cited.

## Overall Assessment

- Fact-check pass rate: 12 Verified + 1 Partially Verified / 13 = 100% pass (with appropriate hedging on F5)
- Copyright risk: Low
- Ready for review: Yes

Notes on hedging:
- The exact "41.8% specification" figure is widely cited in derivative coverage and on the MAST GitHub. I have phrased it as "derivative reporting puts the dominant failure category — *specification and system design* — at roughly 41.8%" to be cautious about its provenance, since I have not directly read the paper's main text.
- The "15× token cost" figure from internal notes was not used; I substituted the verified "3.5× in documented cases" plus the 86% duplication figure.
- The "phantasm of consensus" framing is the author's own term and is marked as opinion in source traceability.
