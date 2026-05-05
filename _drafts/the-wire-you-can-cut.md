---
layout: post
lang: en
title: "The Wire You Can Cut: A Plant Immunity Paradox"
date: 2026-05-05
categories: [biology, plant-science, technology]
tags: [plant-immunity, redundant-signaling, bioelectricity, jasmonate, distributed-systems]
---

When you wound a leaf, the plant fires a wave of electricity. It travels through the vascular tissue, depolarizes membranes, opens calcium channels, and arrives in distant uninfected leaves within minutes. Plant biologists have spent the last decade documenting this wave in increasingly precise detail. The narrative was clean: plants are slow because they have no nerves, but they cheat by running an electrochemical signaling system that does much of the same work.

A paper published in *Nature Plants* in January 2026 quietly broke that narrative. Not by denying the wave — the wave is real — but by showing that you can cut the wire and the immune response still happens.[^1]

## The finding

A team based at the University of Warwick, with collaborators across the UK and Switzerland, identified a previously uncharacterized gene they called *JISS1* (Jasmonate-Induced Systemic Signal 1).[^1] It encodes a small endoplasmic-reticulum-localized protein whose function nobody had been able to pin down. Using a luciferase reporter for the gene, the team watched the signal propagate after pathogen attack. Activity appeared in the petiole of the locally infected leaf within about three hours, and reached neighboring leaves within roughly thirty minutes more — well before any visible cell death.[^2]

This is fast. The classical model of systemic acquired resistance (SAR), built on salicylic acid and the components SID2, NPR1, and FMO1, runs much more slowly. The Warwick team also showed that the new fast pathway does not depend on those canonical components at all.[^3] So we have a second immune signaling system, parallel to the textbook one, faster, working through different molecular machinery.

The fast wave required two things: the JISS1 protein itself, and the vasculature-localized glutamate-like receptors GLR3.3 and GLR3.6, which had previously been characterized in wound and herbivore signaling.[^3] Knock out either component and the wave dies. The electrical signal — the depolarization that propagates from a wounded leaf to a distant healthy one — disappears.

Then the team checked whether the plant could still defend itself.

It could.

The mutants — without the electrical wave, without JISS1, without the glutamate receptors — still mounted full systemic acquired resistance against *Pseudomonas syringae*.[^1] The electrical signal correlates with successful defense. It is not necessary for the defense to happen.

## What survives, what doesn't

This puts the paper in an unusual position. Most molecular biology stories have a clean structure: gene X is necessary for outcome Y; knock it out, the outcome breaks. The Warwick result has two findings that don't sit comfortably together:

- Disrupt jasmonate biosynthesis or jasmonate perception — and SAR breaks.[^1]
- Disrupt the electrical wave (JISS1, GLR3.3, GLR3.6) — and SAR survives.[^1]

Jasmonate chemistry is necessary. Jasmonate-driven *electrical* signaling is not. This is less the discovery of a new mechanism and more the discovery that an old one was *one of two redundant ways* of getting a job done.

I find this important because of what it forces us to think about signaling more generally. The dominant frame in the bioelectricity literature has been to treat electrical signals as the carrier of information — as the wire on which the message travels. There is a long-running argument, associated most prominently with Michael Levin's lab at Tufts, that bioelectric patterning is something like a universal computational substrate for living tissue, doing much of the long-range coordination that we conventionally credit to chemistry. Plants have been a recurring exhibit in that argument: a depolarization wave that runs from a wounded leaf to a distant healthy one is exactly the kind of phenomenon that begs to be read as "the message."

But what if the wave isn't the message — only one delivery system for it?

## Redundancy as design philosophy

In distributed systems engineering, single points of failure are a well-known sin. A service that depends on one Kafka broker, one DNS resolver, or one cache layer will, sooner or later, watch one of them fall over and take the whole system with it. Engineers have spent the last twenty years learning to build systems where two or three independent paths carry the same information, where any single component can be cut without the system noticing.

Land plants, judging from the Warwick result, were ahead of us by an embarrassingly long stretch.

The picture that emerges from JISS1 is that plants don't trust any single physical channel for systemic immunity. The electrical wave runs. Some chemical or hormonal pathway runs in parallel. Either is sufficient for the outcome we measure. What this looks like operationally is that the plant has built immune coordination as a *correlation between two pathways* rather than a serial chain through one of them. Cut one wire and the pathway-level redundancy preserves the outcome. The plant has no equivalent of "the cable to the data center is down."

This reframing changes what we should be measuring. The interesting variable is not whether the electrical wave is present or absent; it is the **divergence between channels**. If the chemical signal says "infected" and the electrical signal also says "infected," the plant is in a coherent state. If they disagree — one fires and the other doesn't — the plant is in a state its evolutionary history did not optimize for. Stress, drought, herbicide damage, sensor failure: these may not show up as missing signals but as signals that no longer line up.

## What the paper doesn't tell us

The honest version of all this is that we do not know what the second pathway is. The Warwick team identified the electrical wire and showed it can be removed without consequence for resistance. They did not identify the chemical or hormonal channel that compensates. It might be jasmonate itself, traveling as a mobile compound rather than as an electrical signal. It might be a different mobile signal — recent work on mobile RNAs makes this less exotic than it would have been five years ago. It might be something entirely uncharacterized that happens to share upstream regulators with the electrical pathway.

The unresolved question is not academic. Sensors that read plant health from electrical signatures already exist as a research direction, and people are seriously building organic electrochemical transistors to deploy them at scale. A sensor that picks up only the electrical wave will give you readings that look fine even after the chemical pathway has failed silently. A sensor that picks up the chemical signature will miss fast localized responses that the electrical pathway captures. The two-channel architecture means the diagnostic question shifts from "what is the plant signaling?" to "are the plant's signals consistent with each other?"

## The wider claim, with caveats

I want to be careful not to overstate what one paper proves. This is one mutant series, in *Arabidopsis*, against one bacterial pathogen, in a controlled lab setting. It is entirely possible that under field conditions, with multiple stressors and a more diverse microbial environment, the electrical pathway turns out to be necessary in ways that did not show up in the lab. Redundancy that looks complete in a growth chamber is sometimes only partial redundancy in the wild.

But the more general reading — that biological signaling has evolved with redundancy at the level of *physical channel*, not just at the level of cell-to-cell handshake — fits with a growing body of evidence from neuroscience, immunology, and developmental biology. Single-channel computational models of biology run into the same wall that single-broker software architectures ran into in the 2000s. The systems that survive are the ones with two ways to say the same thing.

There is something philosophically satisfying about this, beyond the engineering parallel. We tend to look for *the cause* — the necessary mechanism, the gene whose knockout breaks the phenotype. Evolution does not optimize for our explanatory preferences. It optimizes for the system continuing to work when something fails, and the most parsimonious way to do that is to ensure that no single component carries the whole load. The Warwick paper is, in this sense, less a discovery of a new immune mechanism than a discovery that immune mechanisms are organized along principles that look much more like distributed systems than like single circuits.

We have been reading plants as slower, simpler nervous systems. The honest reading, after JISS1, might be that plants are faster, smarter distributed systems — without the central authority that makes nervous systems easier to study and harder to make resilient.

---

[^1]: Stroud, E., Breeze, E. et al. (Grant, M., senior author). "[Rapid local and systemic jasmonate signalling drives the initiation and establishment of plant systemic immunity](https://www.nature.com/articles/s41477-025-02178-4)." *Nature Plants*, January 6, 2026. DOI: 10.1038/s41477-025-02178-4. Accessed 2026-05-05.

[^2]: University of Warwick. "[New study overturns long-held model of how plants coordinate immune responses](https://warwick.ac.uk/news/pressreleases/new-study-overturns-long-held-model-of-how-plants-coordinate-immune-responses/)." Warwick Press Releases, January 2026. Accessed 2026-05-05.

[^3]: Plantae. "[Jasmonate signalling drives rapid local and systemic immunity establishment](https://plantae.org/jasmonate-signalling-drives-rapid-local-and-systemic-immunity-establishment/)." Accessed 2026-05-05.
