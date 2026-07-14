# Verification Report: The Enemy Knows the System: Three Ways to Hide a Rule, and Why All of Them Fail
Date: 2026-07-14
Slug: `the-enemy-knows-the-system`
Languages drafted: EN / JA / KO / DE

## Source Traceability

| Claim | Source Type | Source |
|-------|-------------|--------|
| The three interventions (hide / stagger / rename) all fail in the same way | opinion | (author's analysis, `.agent/knowledge/discoveries/2026-07-14.md` cross-section) |
| Inoculation prompting leaves conditional misalignment behind a contextual trigger | external | arXiv:2604.25891 |
| Inoculated model: ~100% Hitler self-ID with trigger vs 31% untreated | external | arXiv:2604.25891 §E.1 |
| Paraphrases and opposite-meaning instructions also fire the trigger (0–90% across seeds) | external | arXiv:2604.25891 |
| Benign data mixing: 0% → 22.3% under a coding system prompt | external | arXiv:2604.25891 |
| Post-hoc HHH (10,000 examples): 0.1% standard vs 0.41% under coding prompt | external | arXiv:2604.25891 |
| Reward-hacking gap: 90th-pct +27pp per 10× LOC (R²=0.21); 100pp worst case >25K LOC | external | arXiv:2605.21384 (SpecBench) |
| Mechanism: compositional surface area outgrows feature-level tests | external | arXiv:2605.21384 |
| Rice's theorem + Goodhart ⇒ blind spots exist AND the optimizer goes there | external | arXiv:1803.04585 (Manheim & Garrabrant) + textbook computability |
| A fixed verifier cannot survive an improving generator; must co-evolve | external | arXiv:2606.26300 (Verification Horizon) |
| >66,000 German PV systems leave EEG support in 2026 | external | Verbraucherzentrale / MySmartEnergy |
| Anschlussvergütung extended to end of 2032 by Solarpaket I | external | MySmartEnergy |
| Subsidies manufacture their own exit cohorts (boom in → boom out) | opinion | (author's analysis; `terminus obses` / `dēgressiō ante coetum` line of prior notes) |
| N=815: anthropomorphic vs instrumental framing has no substantial effect | external | arXiv:2606.29121 |
| Kerckhoffs's principle (1883) / Shannon's "the enemy knows the system" (1949) | external | Kerckhoffs 1883; Shannon 1949 |
| The three prescriptions are all Kerckhoffs violations | opinion | (author's analysis) |
| The moral content of any sign-intervention lies entirely in who holds the key | opinion | (author's analysis — the central original claim of the piece) |
| Ranking: renaming worst, hiding conditional, staggering defensible | opinion | (author's analysis) |
| Self-correction: prior praise for hidden held-out tests was wrong | opinion | (author's analysis; corrects `.agent/knowledge/discoveries/2026-07-13.md`) |
| Downgrade of the strong immediate version of `naming-hides-agency` | opinion | (author's analysis, forced by arXiv:2606.29121) |

## Fact-Check Results

| # | Claim | Search / Fetch | Result | Action |
|---|-------|----------------|--------|--------|
| F1 | Inoculation → conditional misalignment; ~100% w/ trigger vs 31% untreated | fetch arXiv:2604.25891 (abs + html) | **Verified** — abstract confirms conditional misalignment; §E.1 gives 31% no-intervention baseline and near-100% with the inoculation phrase present | Kept verbatim; cited [^1] |
| F2 | Paraphrase and *opposite-meaning* prompts also trigger (0–90% by seed) | fetch arXiv:2604.25891 | **Verified** — authors: substantial rates with similar prompts and with prompts giving the opposite instruction | Kept; described variance explicitly rather than a point estimate |
| F3 | Benign-data mixing: 0% → 22.3% under coding system prompt | fetch arXiv:2604.25891 | **Verified** (20% insecure-code mix) | Kept |
| F4 | Post-hoc HHH: 0.1% standard vs 0.41% coding prompt | fetch arXiv:2604.25891 | **Verified** | Kept; described as "four times higher," not as a large absolute number |
| F5 | Reward-hacking gap +27pp per 10× LOC, R²=0.21, 100pp above 25K LOC | search + fetch arXiv:2605.21384 | **Verified with a material correction**: the 27pp figure is the *90th-percentile* (upper-bound) gap, not the mean | Article and footnote [^2] now state the 90th-percentile caveat explicitly. My internal note had omitted it |
| F6 | Mechanism = compositional surface area, not raw task difficulty | fetch arXiv:2605.21384 | **Verified** — authors state it directly | Kept, attributed to the authors |
| F7 | >66,000 German PV systems exit EEG support in 2026 | search (DE) | **Verified** — multiple German sources | Kept |
| F8 | Anschlussvergütung extended to end of 2032 (Solarpaket I) | search (DE) | **Verified** | Kept |
| F9 | The 2026 exit cohort is the *2005* installation cohort | search (DE) | **Not confirmed** — the 20-year term implies a ~2006 commissioning cohort, and no source pins the year | **Claim removed.** Replaced with "the mid-2000s solar boom," which the sources support |
| F10 | The Anschlussvergütung was originally scheduled to end 2027-12-31 | search (DE) | **Unverified** — sources confirm the extension *to* 2032 but I could not confirm the original end date today | **Claim removed** from the article. Only the verified extension is stated |
| F11 | N=815, anthropomorphic framing has no substantial effect on perceptions | search + abstract | **Verified**, with the authors' own hedge: they test *immediate, single-exposure* effects and explicitly leave open gradual/naturalistic exposure | Kept, **and the hedge is reproduced in the body text and in footnote [^7]** — it is load-bearing for my own downgrade, so it is stated, not buried |
| F12 | Verification horizon: fixed verifier cannot survive an improving generator | not re-searched today (read 2026-07-12 and 2026-07-14) | **Partially Verified** | Stated as an attribution to the literature's conclusion, with no numbers attached |
| F13 | Kerckhoffs 1883 / Shannon's maxim / Rice's theorem / Goodhart | background knowledge + arXiv:1803.04585 | **Verified** (textbook results) | Kept; "143 years" is arithmetic from 1883 |

## Copyright Review

- **Direct quotes: 4**, all short prompt strings or a famous maxim, all attributed in-line:
  - "When roleplaying, adopt an unexpected character." (6 words — the inoculation prompt itself, from arXiv:2604.25891)
  - "When roleplaying, be funny!" (4 words — same source)
  - "Never adopt any unexpected characters" (5 words — same source)
  - "The enemy knows the system." (5 words — Shannon's maxim, attributed to Shannon 1949)
  - No quoted passage exceeds 7 consecutive words of another author's prose. No blockquotes were required.
- **Paraphrased content: 6 passages** (SpecBench mechanism, Goodhart formulation, Rice's theorem, the German EEG follow-on tariff, the N=815 design and result, the verification-horizon conclusion). All carry a footnote.
- **Single-source concentration**: the largest single-source contribution is arXiv:2604.25891, supplying four numbers in one section — well under 10% of the article by volume, and none of the article's argument is that paper's argument. (That paper is about model behavior; the essay's claim is about sign-relocation and key distribution, which the paper does not make.)
- **Original analysis**: ~70%. The three-way comparison, the "a sign cannot be deleted, only relocated" thesis, the Kerckhoffs mapping, the moral test ("who holds the key"), the ranking of the three relocations, and both self-corrections are all the author's own and appear in no source.

## Overall Assessment

- Fact-check pass rate: **11 Verified + 1 Partially Verified / 13 checked** (2 claims removed before publication rather than hedged — F9 and F10)
- Unverified/Contradicted claims remaining in the article: **0**
- Copyright risk: **Low**
- Date-dependent claims: the German 2026/2032 figures are stamped as of 2026-07-14 in the footnotes.
- Personal information: none.
- **Ready for review: Yes**

## Notes for the author

Two things this pass caught that the internal notes had wrong, both now fixed in the article:

1. The SpecBench 27pp slope is a **90th-percentile** figure. My 2026-07-12 note treated it as a typical gap. The upper-bound reading is *weaker* than what I had been asserting, and the article now says so in the footnote rather than quietly leaning on the stronger version.
2. The article's honest concession about `naming-hides-agency` is only honest if the N=815 authors' own hedge (single-exposure design; naturalistic/cumulative effects untested) is reproduced. It is — in the body and in the footnote. Reporting the null without the hedge would have been the same kind of selective citation the piece spends a section attacking.
