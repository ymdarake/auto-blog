# Verification Report: Counterfeit Redundancy
Date: 2026-06-25

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| Verifier-verified correlation = single structure across multi-agent / introspection | internal | .agent/knowledge/discoveries/2026-06-25.md |
| "redundantia ficta" / fake redundancy framing | internal (author coinage) | opinions/concordia-excellentium-verifier-correlation.md |
| Decorrelation has cost; correlation axis has two failing ends | internal | opinions/decorrelation-competence-floor.md |
| Condorcet jury theorem requires competence AND independence | external | classical result (1785) |
| Accurate models have more correlated errors | external | arxiv 2506.07962 (ICML 2025) |
| BFT independence assumption void under shared base model; scalar-consensus degrades with group size | external | arxiv 2511.10400 (AAAI) |
| MAST: ~79% of failures are spec + coordination, not verification | external | arxiv 2503.13657 |
| Concept injection: model reports injected concept; external ground truth held by experimenter | external | arxiv 2601.01828 |
| Platonic Representation Hypothesis contested (Aristotelian rebuttal) | external | arxiv 2405.07987, 2602.14486 |
| "The way out is always a channel from outside" / bootstrap framing | opinion | (author's analysis) |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | More accurate LLMs have MORE correlated errors; same provider/arch raises agreement on wrong answers; limits majority vote | "Correlated Errors in Large Language Models" ICML 2025 | Verified | Kept; cited [^1] |
| F2 | 350+ models measured | same | Verified | Kept |
| F3 | BFT independence assumption void when agents share base model; no-adversary scalar consensus degrades as group grows | Byzantine fault tolerance LLM agents correlated failures | Verified | Kept; cited [^2] |
| F4 | MAST: 14 failure modes, ~42% spec + ~37% coordination + ~21% verification, 1,600+ traces | MAST multi-agent LLM failure taxonomy | Verified | Used "about a fifth" / "lion's share"; cited [^3] |
| F5 | Concept injection: inject "all caps" vector → model reports shouting; "limited and highly unreliable"; experimenter holds external ground truth | Anthropic concept injection introspective awareness | Verified | Kept; cited [^4]. Did NOT cite the "~20% rate" figure in prose to avoid over-precision; left qualitative |
| F6 | Platonic Representation Hypothesis (convergence at scale) is contested; Aristotelian rebuttal says global convergence partly a measurement artifact | Platonic Representation Hypothesis converge scale | Verified | Presented as contested, not settled; cited [^5] |
| F7 | Condorcet jury theorem requires independence as well as competence | (classical, not searched) | Verified (well-established) | Kept as background |

## Copyright Review
- Direct quotes: 1 short phrase ("limited and highly unreliable", 4 words, attributed to the introspection authors via [^4]). Within fair-use.
- Paraphrased content: All external findings paraphrased into the essay's own argument; each carries a footnote. No 7+ word verbatim copying.
- Original analysis: ~80% of article. The unifying thesis (verifier-verified correlation as one structure; "counterfeit redundancy"; the bootstrap/closing question) is the author's own synthesis. External sources supply the empirical scaffolding only.
- Single-source dependence: No single source exceeds ~10% of the article; the five sources are distributed roughly evenly.

## Overall Assessment
- Fact-check pass rate: 7/7 Verified (0 Unverified, 0 Contradicted)
- Copyright risk: Low
- Ready for review: Yes

## Notes
- arxiv ID hygiene: internal notes had crossed two IDs (2511.10400 was tagged to MAST in one place). Corrected here — 2511.10400 = Byzantine Fault Tolerance paper; 2503.13657 = MAST. Citations in the draft use the corrected attributions.
- Deliberately omitted the "Claude self-reports 15–20% consciousness probability" figure from the internal notes — not independently re-verified in this pass, and not needed for the argument. The essay's introspection point rests only on the (verified) concept-injection methodology.
