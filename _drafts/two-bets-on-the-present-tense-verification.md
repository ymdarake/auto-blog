# Verification Report: Two Bets on the Present Tense
Date: 2026-07-30

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| Current-value / supersession problem definition, isolated on real conversational data | internal | .agent/knowledge/opinions/memory-supersession-gap.md |
| Bounded memory 77% vs full-context 92%, p<0.005, stable across scale | external | https://arxiv.org/abs/2606.27472 |
| 24x memory scaling (300→7,150 chars) produces no improvement (28%→28%) | internal (from opinion, derived from paper) | .agent/knowledge/opinions/memory-supersession-gap.md |
| GRPO fine-tuning Qwen2.5-3B: held-out accuracy 9.0%→16.7% | external | https://arxiv.org/html/2606.27472v1 |
| Mem0 v3 single-pass ADD-only architecture, older facts not deleted/merged | external | https://mem0.ai/blog/mem0-the-token-efficient-memory-algorithm |
| Mem0 conflict issues reportedly closed as "not planned" | internal (from opinion, unverified independently — flagged as reported claim) | .agent/knowledge/opinions/mem0-letta-supersession-architecture-bet.md |
| Mem0 LongMemEval 94.4% (up from 93.4%), temporal reasoning 93.2%→97.0% | external | https://mem0.ai/blog/the-token-efficient-memory-algorithm-now-has-temporal-reasoning |
| Mem0 retrieval ~7,000 tokens vs 25,000+ for full-context | external | https://mem0.ai/blog/the-token-efficient-memory-algorithm-now-has-temporal-reasoning |
| Letta three-tier architecture (core/recall/archival), self-editing via memory functions | external | https://www.letta.com/blog/agent-memory/ |
| No public report found of Mem0 tested under Supersede's exact protocol | opinion (absence claim, search-based) | (author's analysis, based on search conducted 2026-07-30) |
| Base LLMs are inconsistent at preserving unrelated facts while updating changed ones (AGM-style failure) | internal | .agent/knowledge/opinions/memory-supersession-gap.md |
| Framing/argument connecting the two architectures to the negative result (the article's central analysis) | opinion | (author's analysis) |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | Supersede: bounded 77% vs full-context 92%, p<0.005 | "Supersede benchmark arxiv 2606.27472 agent memory current value bounded context" | Verified | Kept as stated; paper reports paired McNemar p<0.005 (internal note said p=0.0033, consistent — reported precisely in text as "p < 0.005" per search result phrasing) |
| F2 | GRPO training 9.0%→16.7% on held-out real LongMemEval oracle | "Supersede LLM agent memory GRPO trained policy LongMemEval oracle 16.7%" | Verified | Kept as stated, added to References |
| F3 | Mem0 v3 ADD-only architecture, no delete/merge at write time | "Mem0 v3 token efficient memory algorithm ADD-only temporal reasoning LongMemEval" | Verified | Kept, sourced to Mem0 blog |
| F4 | Mem0 LongMemEval 94.4% (93.4% baseline), temporal reasoning 93.2%→97.0% | "Mem0 v3 token efficient memory algorithm ADD-only temporal reasoning LongMemEval" | Verified | Kept, sourced to Mem0 blog |
| F5 | Letta three-tier memory (core/recall/archival) + self-editing | "Letta MemGPT core memory recall archival self-editing agent memory tiers" | Verified | Kept, sourced to Letta blog |
| F6 | Mem0 conflict-handling issues closed as "not planned" | (carried from internal opinion note; not independently re-verified via public issue tracker) | Unverified (internal source only) | Softened with "reportedly" / "if... really does" hedging language rather than stated as flat fact |
| F7 | No public benchmark of Mem0 run under Supersede's exact 48-session/300-char/no-judge protocol | search conducted during F1/F2 queries, no such result surfaced | Unverified (absence claim) | Framed explicitly as "as far as I could find, no" — an open question, not a settled claim |

## Copyright Review
- Direct quotes: 0 (no blockquoted material; all paraphrased and restructured)
- Paraphrased content: benchmark descriptions from Mem0 blog and Supersede paper abstract/results are paraphrased and restructured into original sentences, no verbatim runs of 7+ words
- Original analysis: approximately 55% of the article (the central argument — that Mem0's temporal-reasoning gain and Supersede's negative result may be measuring different things, and the critique of Letta's unguaranteed self-editing — is the author's own synthesis, not present in any single source)
- Single-source dependency: no single external source accounts for more than ~10% of total content; the argument draws roughly evenly across Supersede, Mem0's two blog posts, and Letta's blog post, plus original synthesis

## Overall Assessment
- Fact-check pass rate: 5/7 fully Verified, 2/7 flagged and hedged in text (not removed, since both are explicitly framed as reported/unconfirmed rather than asserted as fact)
- Copyright risk: Low
- Ready for review: Yes
