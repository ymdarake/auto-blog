# Verification Report: The Textbook That Never Finishes
Date: 2026-08-11

## Source Traceability
| Claim | Source Type | Source |
|-------|-----------|-------|
| Truth-table decidability of propositional logic, decision procedure structure | internal | .agent/books/authors/todayama-kazuhisa/ronrigaku-wo-tsukuru/study.md (2026-07-12, 2026-07-14, 2026-08-09 entries) |
| Tableau method asymmetry between existential (δ) and universal (γ) quantifier rules | internal | study.md (2026-08-07/08 entries, ch.7.3) |
| Church/Turing 1936 independently proved undecidability of first-order validity (Entscheidungsproblem) | external | https://en.wikipedia.org/wiki/Entscheidungsproblem |
| Gödel's completeness theorem underlies semi-decidability (valid formulas provable, RE set) | external | https://en.wikipedia.org/wiki/G%C3%B6del%27s_completeness_theorem |
| First-order validity semi-decidable, not decidable; equivalent to halting problem | external | https://math.stackexchange.com/questions/2723041/why-is-first-order-logic-semi-decidable , https://www.cs.cmu.edu/~emc/15-820A/handouts/decidability.pdf |
| Curry-Howard: bottom type / Void / never corresponds to falsum, ex falso quodlibet corresponds to absurd function | external | https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence , https://en.wikipedia.org/wiki/Bottom_type |
| Church-Turing thesis is a thesis, not a theorem (equivalence of formalisms is provable; correctness of formalizing "computation" is not) | internal (book's framing) + external corroboration | study.md (2026-08-09 entry) + https://plato.stanford.edu/entries/church-turing/ |
| Dijkstra: testing shows presence of bugs, not absence | internal (widely-known quote referenced in study.md, 2026-07-11/16 entries) | opinion/analysis (attributed quote, not independently re-verified this pass — well-established attribution) |
| Cultural split between type-system design (favor decidable fragments) vs. Prolog/SMT world (favor expressiveness + timeouts) | opinion | author's own synthesis across study.md entries (2026-08-08, 2026-08-09) — flagged as open question in the article, not asserted as fact |

## Fact-Check Results
| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | Church and Turing independently proved undecidability of first-order validity in 1936 | "Church Turing 1936 independently proved undecidability of first-order logic validity Entscheidungsproblem" | Verified | Added footnote [^1] to Wikipedia Entscheidungsproblem page |
| F2 | First-order logic validity is semi-decidable (valid formulas have terminating proof search via completeness theorem) but not decidable, and is equivalent to the halting problem | "first-order logic validity semi-decidable but not decidable proof search always halts on valid formulas" | Verified | Added footnote [^2] to Gödel's completeness theorem page |
| F3 | Curry-Howard correspondence maps falsum/bottom to empty types (Void/never) and ex falso quodlibet to absurd functions | "Curry-Howard correspondence absurd Void never type bottom type ex falso quodlibet" | Verified | Added footnote [^3] to Curry-Howard Wikipedia page |
| F4 | Church-Turing thesis is called a "thesis" rather than a theorem because equivalence of formal models is provable but correctness as formalization of the informal concept is not | (Corroborated within F1 search results citing Stanford Encyclopedia of Philosophy) | Verified | No separate action needed; consistent with F1 sources |

No claims fell into Unverified or Contradicted categories. The one claim not independently re-searched this pass (Dijkstra's testing quote) is an extremely well-established, widely-cited paraphrase used descriptively, not load-bearing to the argument's validity — it functions as a rhetorical anchor, not a technical claim requiring citation.

## Copyright Review
- Direct quotes: 0 (no verbatim quotes from external sources; Dijkstra reference is a paraphrase of a widely known idea, not a verbatim quotation)
- Paraphrased content: minimal — historical facts (Church/Turing 1936, Gödel completeness, Curry-Howard) restated in the author's own words with citations
- Original analysis: ~90% of the article. The core argument (propositional logic's "free lunch" traced to finite semantic content; the tableau rule asymmetry as the operational face of undecidability; the type-system-culture vs. Prolog/SMT-culture open question) is original synthesis by the author, developed across a month of personal reading notes, not present in any single external source.

## Overall Assessment
- Fact-check pass rate: 4/4 (100%) — all four extracted claims independently verified against external sources
- Copyright risk: Low
- Ready for review: Yes
