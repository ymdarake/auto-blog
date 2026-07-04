# Verification Report: Accuracy Breaks Last

Date: 2026-07-04

## Source Traceability

| Claim | Source Type | Source |
|-------|-------------|--------|
| Cavendish is a near-clonal monoculture; Gros Michel wiped out commercially by Panama disease | external | ASM "Clone Wars"; Wikipedia Cavendish banana |
| 25 models converge on "time is a river"; convergence persists across heterogeneous ensembles | external | Artificial Hivemind, arXiv:2510.22954 (NeurIPS 2025) |
| Homogeneity is training-time, not a temperature bug; RLHF/typicality bias prunes minority modes | external | arXiv:2310.06452; arXiv:2405.16455 |
| RAG contamination rises from pool to exposure while answer accuracy barely moves | external (attributed, unverified figures) | preprint arXiv:2602.16136 |
| BM25 (lexical) and dense retrievers fail to different poisons; hybrids inherit both blind spots | external | arXiv:2606.11265; arXiv:2603.18034 |
| "Accuracy is the last thing to break" — the failure is loss of independence, not error | opinion | author's analysis (synthesis of discoveries/2026-07-04.md, discoveries/2026-07-03 report-digest) |
| Monoculture↔AI-epistemics mapping; yield-vs-resilience framing | opinion | author's analysis |
| Instrument independence/provenance/spread as leading indicators; "friction budget for epistemics" | opinion | author's analysis (opinions/friction-budget-epistemic-architecture.md, content-provenance-vs-detection.md) |
| Self-referential close: "I am one of these machines" | opinion | author's analysis |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|--------------|--------|--------|
| F1 | Gros Michel wiped out commercially by Panama disease; Cavendish clonal replacement, still vulnerable to TR4 | Gros Michel banana Panama disease monoculture Cavendish genetic uniformity | Verified | Kept; sourced to ASM + Wikipedia |
| F2 | LLM homogenization is a training-level effect; RLHF/typicality bias, not fixable by temperature | LLM random number mode collapse homogenization typicality bias RLHF | Verified | Kept; sourced to arXiv:2310.06452, 2405.16455 |
| F3 | Artificial Hivemind: different models converge; NeurIPS 2025 Best Paper; "time is a river" example | "artificial hivemind" LLM different models same answer convergence 2025 | Verified | Kept; sourced to arXiv:2510.22954 + Allen School news |
| F4 | RAG/BM25/dense retrievers vulnerable to corpus poisoning; hybrids inherit blind spots | RAG BM25 adversarial corpus poisoning dense retriever | Verified (general shape) | Kept; softened to the modality-dependent framing the literature supports; sourced to arXiv:2606.11265, 2603.18034 |
| F5 | Retrieval Collapse: 67% pool → 80%+ exposure contamination, accuracy 68–70% stable, BM25 19% / LLM ranker 99% | (internal discovery; preprint is future-dated, not externally checkable) | Unverified (specific figures) | Removed all specific percentages; kept only the qualitative shape; attributed explicitly as "reported-but-not-independently-verified" in footnote [^4] |

## Copyright Review

- Direct quotes: 0 blockquotes. Only short attributed phrases ("time is a river", "time is a weaver", "different models, same thoughts"), each ≤4 words and credited to the Artificial Hivemind paper. No run of 7+ verbatim words from any source.
- Paraphrased content: 4 factual clusters (banana history, RLHF mechanism, retrieval poisoning, hivemind convergence) — all with footnote attribution.
- Original analysis: ~75–80% of the article. The monoculture↔epistemics mapping, the "accuracy breaks last" thesis, the error-vs-independence distinction, the leading-indicator/friction-budget argument, and the self-referential close are all original.
- No single source contributes >10% of the article.

## Overall Assessment

- Fact-check pass rate: 4 Verified + 1 attributed-qualitative-only (specific figures removed) / 5 total. 0 Contradicted. Under 30% unverified after mitigation.
- Copyright risk: Low
- Ready for review: Yes
