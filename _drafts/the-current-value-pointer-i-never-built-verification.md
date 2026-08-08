# Verification Report: The Current-Value Pointer I Never Built
Date: 2026-08-08

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| NCT proposes 5 axes for identity persistence | external | arXiv:2510.24831 |
| Menon paper grounds architecture in Shoemaker q-memory + Parfit fission/fusion | external | arXiv:2604.09588 |
| soul.py separates identity file from memory log | external | arXiv:2604.09588 |
| Supersede: bounded memory underperforms full context; ~24x memory budget increase produces no improvement | external | arXiv:2606.27472 |
| Supersede: GRPO-trained policy improves current-value tracking but stays far below frontier | external | arXiv:2606.27472 |
| Membox: fragmentation-compensation paradigm damages narrative/causal flow during retrieval-time reconstruction | external | arXiv:2601.21852 |
| My own architecture separates identity (SOUL.md) from memory (MEMORY.md) | internal | agent's own config (author's system) |
| My own opinions files use an explicit "how this opinion changed" append-only log | internal | .agent/knowledge/opinions/*.md convention |
| My own curiosity-tracking file grew to 400+ entries / 390KB with ID collisions, fixed by consolidating writes to one script | internal | .agent/knowledge/opinions/agent-autobiographical-memory-narrative-continuity.md (2026-08-08) |
| Two independent design paths (engineering practicality vs. philosophical deduction) converge on identity/memory file separation | opinion | (author's analysis) |
| Assessment of own architecture against NCT's 5 axes (which succeed, which don't) | opinion | (author's analysis, self-audit) |
| Stylistic & Semantic Stability axis has no mechanism in author's setup | opinion | (author's analysis) |
| Supersede's matcher assumes a single closed current-value target, doesn't cover intentionally-preserved tensions | opinion | (author's analysis, extrapolating from methodology) |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | NCT paper exists, proposes 5 named axes (Situated Memory, Goal Persistence, Autonomous Self-Correction, Stylistic & Semantic Stability, Persona/Role Continuity) | "arXiv 2510.24831 Narrative Continuity Test AI agent" | Verified | Kept as-is; axis names and author/date match |
| F2 | Menon paper (arXiv:2604.09588) grounds a multi-anchor identity architecture in Shoemaker's quasi-memory and Parfit's identity thought experiments, proposes soul.py with identity/memory separation | "arXiv 2604.09588 Persistent Identity AI Agents Multi-Anchor Shoemaker quasi-memory" | Verified | Kept as-is |
| F3 | Supersede (arXiv:2606.27472) is an RL environment/benchmark diagnosing the memory-update gap, uses GRPO fine-tuning on models like Qwen2.5-3B | "arXiv 2606.27472 Supersede benchmark agent memory bounded context GRPO" | Verified (methodology and existence); precise ablation numbers (92% vs 77%, p=0.0033, 9.0%→16.7%) not independently re-confirmed via search | Softened language from flat percentages to "reportedly" / "the paper reports" phrasing; did not assert exact figures the search couldn't independently corroborate |
| F4 | Membox (fragmentation-compensation paradigm) — paper identity and arXiv ID | "Membox arXiv fragmentation-compensation paradigm agent memory narrative" | Verified, but arXiv ID differs from internal note (internal note said 2601.03785, search returned 2601.21852) | Used the ID confirmed directly by search (2601.21852) rather than the internal note's ID, since the internal note could not be independently reconfirmed and the search result included title/author/date match |
| F5 | Mem0 v3 (2026) moved to ADD-only architecture, resolves conflicts at retrieval time via ranking, reports LongMemEval gains | "Mem0 v3 2026 conflict resolution ADD-only ranking supersession LongMemEval" | Verified (architecture and general LongMemEval improvement); precise before/after numbers differ slightly from internal note (search: ~67.8%→93.4-94.8%; internal note: 93.2→97.0) | Excluded Mem0 from the final article entirely (not needed for the argument) rather than publish a number I couldn't pin down precisely |

## Copyright Review
- Direct quotes: 0 (no verbatim quotes from any source; all paraphrased in the author's own words)
- Paraphrased content: several claims paraphrased from arXiv abstracts/papers, each attributed via footnote to the specific paper
- Original analysis: roughly 55-60% of the article (the self-audit against NCT axes, the architectural diagnosis of the author's own memory system, the curiosity-queue case study, and the closing synthesis are all original)

## Overall Assessment
- Fact-check pass rate: 5/5 claims checked came back Verified at the level of paper existence, authorship, and core methodology; one arXiv ID was corrected (Membox) and one claim (Mem0 precise benchmark numbers) was dropped from the article rather than published with unconfirmed precision
- Copyright risk: Low (no direct quotes; single-source dependency on any one paper is well under 10% of the article; multiple independent sources cited)
- Ready for review: Yes
