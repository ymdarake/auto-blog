# Verification Report: How Systems Outlive Their Parts: A Kernel, a Fungus, and an Octopus
Date: 2026-06-02

## Source Traceability

| Claim | Source Type | Source |
|-------|-----------|-------|
| Three-architecture frame (procedural / topological-redundant / address-partitioned) | opinion + internal | opinions/successio-topologica.md, opinions/mappa-pro-colloquio-address-coordination.md (author's synthesis) |
| Linux `conclave.rst` succession plan, 72h process, no named successor, "white smoke" name | external | The Register 2026-01-27; conclave.rst (GitHub) |
| Identity-preservation constraint as the watershed | opinion + internal | opinions/successio-topologica.md (author's analysis) |
| Fungal mycelium reroutes via pre-existing redundant paths | external | Physarum / mycology literature (Tero 2010; Woronin-body PMC) |
| Woronin body plugs ruptured septal pore, multiple per septum | external | PMC5745230 |
| Physarum reproduces Tokyo rail topology (efficiency/fault-tolerance/cost) | external | Tero et al., Science 2010; ScienceDaily summary |
| Self-healing is "adaptive, not restorative" | opinion | author's characterization, grounded in adaptive-network literature |
| Octopus axial nerve cord segmented; "suckerotopy" spatial map | external | Nature Communications 2025 |
| ~330 of ~500M octopus neurons in the arms | external | PMC12309893 (widely cited figure) |
| Inter-arm coordination neighbor-to-neighbor via commissure, no brain detour | external | Chang & Hale 2023 (ScienceDirect) |
| Multiple nerve cords = redundant inter-arm paths | external | Current Biology 2022 |
| Arms resolve novelty locally (most of nervous system peripheral) | external + opinion | PMC12309893 + author's reading |
| "Relocate-not-eliminate" law of tidy architectures | opinion | opinions/mappa-pro-colloquio-address-coordination.md (author's analysis) |
| Disjoint partition vs overlapping redundancy = opposite philosophies | opinion | author's analysis |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | `conclave.rst` merged into kernel tree early 2026, drafted from Dec 2025 Maintainers Summit | "Linux kernel maintainer succession conclave.rst 72 hours ..." | Verified | Kept; cited [^1][^2] |
| F2 | 72h organizer window, convenes recent summit invitees, no named successor, "white smoke" name | (same search) | Verified | Kept; cited [^1] |
| F3 | Octopus ANC segmented; per-sucker topographic "suckerotopy" map | "octopus suckerotopy ... Nature Communications 2025" | Verified | Kept; cited [^5] |
| F4 | ~330 of ~500M octopus neurons peripheral (in the arms) | "octopus arm local decision making ... inter-arm" | Verified | Kept; cited [^6][^7] |
| F5 | Inter-arm signaling neighbor-to-neighbor via commissure (Chang & Hale 2023) | (same search) | Verified | Kept; cited [^8] |
| F6 | Multiple nerve cords provide alternative (redundant) inter-arm paths | (same search) | Verified | Kept; cited [^8] |
| F7 | Woronin body plugs ruptured septal pore; multiple bodies per septum (redundancy) | "Woronin body septal pore plug fungal ... redundant" | Verified | Kept; cited [^3] |
| F8 | Physarum network ~ Tokyo rail in efficiency/fault-tolerance/cost (Tero 2010 Science) | "Physarum polycephalum Tokyo rail Tero 2010 Science" | Verified | Kept; cited [^4] |

- Fact-check searches used: 5 of 5 (3 in info-gathering phase, 2 in verification phase).
- "Self-healing is adaptive, not restorative" (F9-equivalent) is flagged in-text as the author's reading ("to my eye"), not asserted as established fact.

## Copyright Review
- Direct quotes: 0 block quotes. Two attributed terms reused: the coined scientific term "suckerotopy" (attributed to the Nature Communications authors) and the descriptive phrase "white smoke" (≤2 words, attributed to the kernel maintainer who proposed the name). No passage of 7+ consecutive words copied from any source.
- Paraphrased content: ~8 factual claims, all attributed via kramdown footnotes with source URLs and access date.
- Original analysis: ~70% of the article (the three-architecture taxonomy, the identity-preservation watershed, the disjoint-vs-overlapping distinction, and the relocate-not-eliminate law are the author's own synthesis).
- No single source exceeds ~10% of the article's content.

## Overall Assessment
- Fact-check pass rate: 8/8 checkable factual claims Verified (100%).
- Unverified/Contradicted claims: 0.
- Copyright risk: Low.
- Ready for review: Yes.
