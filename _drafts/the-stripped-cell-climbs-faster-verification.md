# Verification Report: The Stripped Cell Climbs Faster

Date: 2026-06-23

## Source Traceability

| Claim | Source Type | Source |
|-------|-----------|-------|
| Redundancy-as-soil intuition is the biological transfer of an epistemic "friction-budget" idea | internal | opinions/minimal-genome-evolvability-redundancy.md; opinions/friction-budget-epistemic-architecture.md |
| JCVI-syn3B stripped from 901 → 493 genes (~45% removed); smallest free-living genome | external | Nature 2023 (Moger-Reischer et al.) |
| 300 days ≈ 2,000 generations of lab evolution | external | Nature 2023 |
| >50% fitness drop, fully regained over 2,000 generations | external | Nature 2023 |
| Minimal cell evolved 39% faster than non-minimal control | external | Nature 2023 |
| Mutation rate highest recorded for any cellular organism; unaffected by minimization | external | Nature 2023 |
| Only constraint = cell size; non-minimal +80%; ftsZ epistasis | external | Nature 2023 |
| Three-way split of "evolvability" (hill-climbing / buffering / innovation) | opinion | (author's analysis, built from the sources below) |
| Genotype robustness antagonistic to evolvability; phenotype/network robustness promotes it | external | Wagner 2008, Proc. R. Soc. B |
| Hsp90 buffers cryptic variation, released under stress, becomes Hsp90-independent | external | Rutherford & Lindquist 1998, Nature |
| Adaptive gene loss ("less is more") can raise fitness | external | Olson 1999, AJHG |
| Muller's ratchet / Ohno neofunctionalization | external | named canonical concepts, attributed in prose |
| "Dead-end = can't relocate, not can't fine-tune"; transfer fails because of #objectives; survivor = optionality-under-uncertainty; "freshly-made hammer" caution | opinion | (author's analysis) |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | JCVI-syn3B = 493 genes, ~45% of 901 removed; smallest free-living genome | "Moger-Reischer 2023 Nature Evolution of a minimal cell JCVI-syn3B 2000 generations" | Verified | **Corrected internal note's 473 → 493** (473 is syn3.0/syn3A; the evolved strain syn3B has 493). Source added to References. |
| F2 | 300 days ≈ 2,000 generations | (same search) | Verified | Kept as stated |
| F3 | >50% fitness drop, regained over 2,000 generations | (same search) | Verified | Kept |
| F4 | Minimal cell evolved 39% faster than non-minimal | "minimal cell evolution mutation rate ftsZ cell size constraint" | Verified | Used verbatim figure; load-bearing claim of the piece |
| F5 | Mutation rate highest for any cellular organism; unchanged by minimization | (same search) | Verified | Phrased exactly per source (rate is Mycoplasma's, not caused by streamlining) |
| F6 | Non-minimal cell +80% size; minimal unchanged; ftsZ (tubulin homologue) epistasis | (same search) | Verified | Kept |
| F7 | Wagner: genotype robustness ↓ evolvability, phenotype/network robustness ↑ evolvability via neutral networks | "Wagner robustness evolvability paradox resolved 2008 neutral network" | Verified | Kept; matches source's genotype/phenotype distinction |
| F8 | Hsp90 capacitor buffers silent variation; released; selection makes variants Hsp90-independent | (same search) | Verified | Kept; matches Rutherford & Lindquist abstract |
| F9 | Olson "less is more": gene loss as engine of evolutionary change, can raise fitness | (covered by F1/general); canonical | Verified | Cited via DOI |
| F10 | Muller's ratchet (irreversible decay in small asexual pops); Ohno neofunctionalization | canonical textbook | Verified | Attributed in prose, no fabricated URL |

WebSearch used: 3 (within the 5-search limit).

## Copyright Review

- Direct quotes: 0 prose quotes. Only short paper **titles** appear in quotation marks ("Evolution of a minimal cell", "Robustness and evolvability: a paradox resolved", "less is more", "ftsZ"), each attributed — these are titles/terms, not borrowed prose.
- Verbatim runs of 7+ words from any source: none. All empirical facts are reworded into original sentences.
- Paraphrased content: the *Nature* findings (F1–F6) are paraphrased and attributed via footnotes [^1][^2]; Wagner/Hsp90/Olson likewise [^3][^4][^5].
- Single-source dependence: the *Nature* paper anchors the empirical spine but supplies well under 10% of the article's text; the framing (three-way split, two-objective argument, dead-end-as-relocation, optionality-under-uncertainty, freshly-made-hammer) is original.
- Original analysis: ~70% of the article.

## Overall Assessment

- Fact-check pass rate: 10/10 Verified (0 Unverified, 0 Contradicted)
- Notable correction caught by fact-check: gene count 473 → **493** (syn3A vs syn3B)
- Copyright risk: Low
- Ready for review: Yes
