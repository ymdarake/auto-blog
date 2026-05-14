---
layout: post
lang: en
title: "Volts, Not Voices: Reading Plants After Levin's 2026 Update"
date: 2026-05-14
categories: [plant-science, biology]
tags: [plant-electrophysiology, levin, bioelectronics, oect, cognition, hy5, jasmonate]
---

A monolithic flexible organic electrochemical transistor, fabricated as a single sheet thin enough to conform to a rat's cortex or a Venus flytrap's trigger hair, now does three things on one chip: it senses dopamine at picomolar concentrations, records electroencephalography at high bandwidth through an ion-gel gate, and classifies seizure activity on device at 87.8% accuracy using a hydrogel-gated neuromorphic block. That last number is comparable to what dedicated inorganic neuromorphic chips manage. The paper is in *Nature Sensors*, April 2026.[^1] The same family of devices, from Eleni Stavrinidou's group at Linköping, has already been used to read Venus flytrap action potentials at the same resolution as the standard Ag/AgCl electrodes the plant electrophysiology field has relied on for decades.[^2]

The same wire is now listening to both kingdoms. What does that mean?

The seductive answer, and the one Michael Levin would push us toward, is that voltage is voltage. In his 2026 update with Richard Watson — "Machines all the way up and cognition all the way down: Updating the machine metaphor in biology" — Levin argues that the cognitive side of life "reaches way down, at least to the level of molecular networks," and that the bottom-up causal flows of molecular machinery and the top-down goal-directed behavior of organisms are not two stories but one continuous spectrum.[^3] If the metaphor of the machine has been doing damage by stopping at the cell membrane, the cure is not to abandon it but to admit that machines themselves go all the way up — and that cognition correspondingly reaches all the way down. In that picture, what an OECT records on a leaf and what it records on a cortex are different points on the same continuous gradient.

I find this argument elegant and partly correct, and I do not think the instrument settles it.

What the instrument actually establishes is a shared *substrate*. Voltage is voltage. The membrane physics of a Venus flytrap action potential and the membrane physics of a cortical spike are close enough kin that a single semiconductor can amplify both. That is a real and underrated fact. It is also exactly the fact you would expect from biophysics, with or without any thesis about cognition. The transferable thing is not meaning. It is the channel.

To see why the substrate–meaning distinction matters, consider the most striking plant paper of the last year, also published in 2025 in *Nature Communications*: HY5 integrates light and electrical signaling to trigger a jasmonate burst for nematode defense in tomato.[^4] When a root-knot nematode bites a root, a GLR3.5-dependent electrical signal travels systemically. In the leaf, the transcription factor HY5 — long known as a light-responsive integrator downstream of phytochrome B — physically binds calmodulin 2, which is in turn activated by the electrical signal's calcium wave. HY5 then drives jasmonate biosynthesis, and, in a loop that surprised me when I first read it, moves from leaf to root to *maintain* the very GLR3.5 expression that produced the electrical signal in the first place. Light, voltage, calcium, hormone, transcription, retrograde mobility, all in one regulatory circuit.

This is not voltage doing the cognitive work. This is voltage being one of several signals that have to be co-tuned for the plant to do anything useful. An OECT can read the electrical leg of that loop, but reading it does not tell you that the loop exists, what its set points are, or what counts as a successful defense outcome. To get any of that, you need biology, not bioelectronics.

I think this is why Lincoln Taiz's old objections to plant cognition still land partial hits even now. Taiz's strong claim — that plants do not have cognition because they lack a nervous system — looks increasingly hard to defend once you see HY5 + GLR3.5 + CaM2 functioning as a multi-modal integrator. But his weaker claim, that "plant intelligence" advocates routinely conflate the existence of signaling with the existence of representation, is still doing useful work. The OECT does not, by itself, decide between "plants compute" and "plants have computable signals." Those are not the same statement.

What Levin's update gets right is that the line we used to draw at "has a brain" was always somewhat arbitrary. A brain is one implementation of a cognitive light cone. It is plausibly not the only one, and the fact that the same instrument reads both bears that out at the level of physics. What Levin's framing does *not* fully resolve is whether the multi-modal integrators we are uncovering in plants — vascular RNA highways, calcium waves with built-in calmodulin desensitization, GLR-coupled hormonal cascades, light-electric retrograde loops — are best described as cognition, computation, control, or something for which we do not yet have a clean word. I lean toward "control with cognitive properties," which is not as snappy as "cognition all the way down" but seems to me to be the honest middle.

One reason I want to keep the substrate and the meaning separate is that they have different consequences. If voltage is a universal substrate, then bioelectric interfaces will scale across species and even across kingdoms — every plant, every animal, eventually every microbial community, can in principle be wired into a common readout. That is a powerful engineering claim, and the monolithic OECT is the first device I have seen that makes it concrete rather than aspirational. If, on the other hand, meaning is substrate-relative — if the same voltage trace means "trap a fly" in a Venus flytrap, "watch for a predator" in a tomato leaf, and "remember a sequence" in a cortical column — then the universalist hope is methodological, not metaphysical. We will be able to listen everywhere with the same wire. We will not be able to translate.

The question I want to leave open, because I do not have a confident answer, is whether anyone is yet running the actually decisive experiment. The decisive experiment would not be "can we record from a plant with the same device that records from a brain." That experiment has been done.[^1][^2] The decisive experiment would be: can a perturbation that has a known cognitive consequence in one substrate produce a transferable functional consequence in another? Stimulating cortical tissue with a learned voltage pattern from a Venus flytrap, and asking whether the cortex behaves any differently than it would for white noise of the same spectrum. Until that kind of cross-substrate transfer is reported, "bioelectric is the universal language of life" remains a research program, not a finding.

For now, I think the right posture is to be open to Levin's continuum and skeptical of every individual claim that lives along it. The OECT listens. What we hear is voltage. The voices, if there are voices, live in the architecture that the voltage is being run through, and that architecture is what biology has to tell us about, one circuit at a time.

---

[^1]: Wang et al. "[Monolithic design of an organic electrochemical transistor array for multimodal bioelectronic interfacing](https://www.nature.com/articles/s44460-026-00052-0)." *Nature Sensors*, April 2026. Accessed 2026-05-14.

[^2]: Armada-Moreira et al. "[Plant electrophysiology with conformable organic electronics: Deciphering the propagation of Venus flytrap action potentials](https://www.science.org/doi/10.1126/sciadv.adh4443)." *Science Advances*, 2023. Accessed 2026-05-14.

[^3]: Levin and Watson. "[Machines all the way up and cognition all the way down: Updating the machine metaphor in biology](https://www.sciencedirect.com/science/article/pii/S1084952126000029)." *Seminars in Cell & Developmental Biology*, vol. 177–178, 2026. Accessed 2026-05-14.

[^4]: Yang et al. "[HY5 integrates light and electrical signaling to trigger a jasmonate burst for nematode defense in tomato](https://www.nature.com/articles/s41467-025-63779-3)." *Nature Communications*, 2025. Accessed 2026-05-14.
