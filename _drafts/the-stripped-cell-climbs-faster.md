---
layout: post
lang: en
title: "The Stripped Cell Climbs Faster: Redundancy, Evolvability, and the Three Things We Mean by One Word"
date: 2026-06-23
categories: [biology, evolution, philosophy]
tags: [synthetic-biology, minimal-genome, evolvability, robustness, redundancy, friction-budget]
---

I had a tidy idea and a fresh label to put on it, and a piece of biology seemed to confirm both. The idea: that redundancy which *looks* wasteful is secretly the soil from which adaptation grows — slack, spare parts, apparently useless duplication are the raw material a system draws on when the world changes. I had built this notion in a different domain entirely, thinking about why a little friction in how we form beliefs makes us more reliable, and I was pleased with it. So when I read that stripping a genome down to its bare minimum had "removed its ability to evolve," I felt the warm click of confirmation. Here it was again. Cut the redundancy, lose the future.

Then I went and read the actual experiment, and it hit back hard enough to leave a mark.

## The finding that refused to confirm me

In 2023 a team led by Jay Lennon published a study in *Nature* with the deceptively flat title "Evolution of a minimal cell."[^1] The organism is *Mycoplasma mycoides* JCVI-syn3B — a synthetic bacterium whose genome has been stripped from the wild type's 901 genes down to 493, eliminating roughly 45% of them. That is the smallest genome of any known free-living organism: just the genes you cannot live without, and almost nothing else. If redundancy is the soil of adaptation, this cell is farming bare rock.

They let it evolve in the lab for 300 days — about 2,000 bacterial generations — and measured what happened.[^2]

Streamlining the genome had indeed been costly. The minimal cell started out with its fitness reduced by more than 50% relative to its non-minimal ancestor. So far, so confirming. But over 2,000 generations the cell *clawed the entire deficit back*. And here is the number that ruined my clean little theory: measured by relative fitness, **the minimal cell evolved 39% faster than the non-minimal one.** Stripped to the bone, it adapted *more* quickly, not less.

It gets worse for the redundancy-is-soil story. The minimal cell's mutation rate is the highest recorded for any cellular organism — but that turned out to be a property of *Mycoplasma* itself, not a consequence of streamlining; minimization left the rate unchanged. The only thing the bare genome genuinely couldn't do was control its own cell size. The non-minimal cell grew 80% larger over the experiment; the minimal one stayed put, hemmed in by the epistatic tangle around *ftsZ*, the gene encoding a tubulin-like protein that governs cell division and shape.

So "minimal means it can't evolve" is, for the most obvious reading of *evolve*, simply backwards. Far from optimal, mutating fast, the bare cell had a steep nearby hill and it climbed it quickly. My fresh label slid onto the finding so smoothly precisely because I never asked it to pay the toll. The world charged the toll anyway, and the receipt said *39% faster.*

## One word, three different things

What saved the wreckage was noticing that "evolvability" had been doing three jobs under one name, and I had let them blur. Pull them apart and the contradiction dissolves:

1. **Local adaptation — hill-climbing.** Recovering fitness in the current niche by fine-tuning genes you already have. The minimal cell is not worse at this; it is *better*, for the boring reason that it started far from its optimum and mutates fast.
2. **Robustness — buffering.** The capacity to absorb mutations without immediately expressing them, quietly stockpiling hidden variation. This is what minimization erodes.
3. **Innovation — reaching genuinely new phenotypes and new niches.** The power to become something you were not. This is the one that redundancy actually buys, by keeping raw material around to repurpose.

The naive transfer ("redundancy is the soil of adaptation") quietly equated all three. The experiment falsifies it for sense (1), is silent on (2) and (3), and only sense (3) is where the original intuition has any purchase at all. A dead end, it turns out, is not the inability to *improve where you are.* It is the inability to *go somewhere else.* The bare cell can polish its current life beautifully. What it cannot do is move house.

## Robustness wears two faces

And even sense (3) refuses to give a clean answer, because robustness — the thing redundancy provides — is Janus-faced. Andreas Wagner laid out the tension cleanly in a 2008 paper whose title is almost a koan: "Robustness and evolvability: a paradox resolved."[^3] At the level of the *genotype*, robustness is the enemy of evolvability: if mutations are neutral, they produce no phenotypic variation, and what produces no variation cannot be selected. But at the level of the *phenotype*, robustness is its friend. Many genotypes encode the same phenotype, and they form a connected "neutral network." The wider that network, the more a population can wander across it without dying — and the more *other* phenotypes it can reach from the edges. So redundancy doesn't carry a single sign. It hides today's selective response while it stockpiles tomorrow's room to explore.

Biology has a vivid name for the stockpile: an evolutionary *capacitor.* The classic example is the heat-shock protein Hsp90. When Hsp90 is impaired, a flood of previously hidden phenotypic variation suddenly appears across nearly every structure of the organism — and once selection enriches those variants, they become independent of the Hsp90 trigger entirely.[^4] The protein had been quietly buffering a reservoir of silent genetic variation, holding it in reserve until stress released it all at once. That is redundancy as insurance: invisible in good times, decisive when the weather turns. A spare gene copy does the same trick over longer timescales — one copy keeps the day job while the other, freed from immediate duty, is allowed to drift toward a new function. That is innovation purchased with apparent waste.

## Cutting is not one thing either

If redundancy is two-faced, so is its removal. Stripping a genome can be a loss — or it can be a *move.* Maynard Olson's "less is more" hypothesis points out that discarding genes that have become useless or harmful can *raise* fitness by cutting metabolic cost; gene loss is something evolution does to itself, on purpose, especially in new or sheltered environments.[^5] But the same direction of travel has a dark twin. In small, asexual populations, harmful mutations accumulate irreversibly — Muller's ratchet — and a lineage can specialize itself into a corner it can never climb out of. Both processes shrink the genome. One is adaptation; the other is decay. You cannot tell which you are looking at from the gene count alone. You have to ask whether the door behind the organism is still open.

## What actually survives

So why does the friction idea transfer so badly from minds to cells? I think the answer is a number: the number of objectives.

The original intuition lived in a single-objective world. When the only goal is to avoid confidently believing false things, then *more friction is monotonically safer* — every grain of resistance you add to belief-formation cuts the same risk. Nothing pushes back. Biological redundancy lives in a two-objective world, and the two objectives are *at war.* One is immediate selective response: convert variation into fitness *now.* The other is stored optionality: hold variation in reserve against a future you cannot see. These are not independent; they are the two ends of Wagner's paradox. Redundancy buys the second by spending the first. So "redundancy is good" cannot be true as stated, because good *for which objective, against which future?*

What survives the wreck is much smaller and more honest than the slogan I started with. Not "redundancy is good," but a conditional: **stored variance has value only to the degree that the future environment is uncertain.** If the world will not change, the slack is pure overhead and the lean cell wins, fast. If the world will change in ways you cannot predict, the slack is an option you will be grateful you held. This already has a name in economics — optionality under uncertainty — and the honest move is to notice that it does, rather than mint a fresh-sounding term and feel clever. Which is exactly the trap I had walked into at the start.

That, in the end, is what the experiment was really teaching me, and it had nothing to do with bacteria. The most dangerous tool in a thinker's kit is the one you *just built.* A freshly-made hammer wants to swing, and every problem in reach suddenly looks like its nail. My friction idea was three days old and desperate for a second application, so it grabbed the first biology that rhymed with it. The discipline isn't to never generalize — generalizing is the whole point. The discipline is to make the new idea pay a toll on the way in, to look for the hard friction that *resists* the transfer. Here the friction came back as a single brutal number. *39% faster.* I trusted the world over the hammer, and the hammer got smaller and truer for it: split into three meanings, narrowed to one, and even there hedged with a paradox.

## Open questions

A few things I don't get to keep clean. The "lost innovation" of the minimal cell is well motivated by theory — Wagner's networks, the capacitor, the dead-end logic — but the 2,000-generation experiment didn't directly demonstrate it; the only constraint actually observed was cell size. The real test would be longer, across many environments: show that the non-minimal cell reaches genuinely *new* phenotypes the bare one never can. Until then, "redundancy buys innovation" is a well-supported expectation, not a finished result.

And the question that keeps me up: does my own single-objective premise really hold? If avoiding false beliefs and preserving the option to revise them are *two* objectives rather than one — and they might be — then the friction idea has the same two-faced paradox hiding inside it, and it needs the same three-way split I just performed on the cell. The hammer might need to be taken apart one more time. I find that I'm not sure, and for once that feels like the right place to stop.

---

[^1]: Moger-Reischer, R. Z., Glass, J. I., Wise, K. S., Lennon, J. T., et al. "[Evolution of a minimal cell](https://www.nature.com/articles/s41586-023-06288-x)." *Nature* 620, 122–127 (2023). Accessed 2026-06-23.
[^2]: Wood, C. "[Even Synthetic Life Forms With a Tiny Genome Can Evolve](https://www.quantamagazine.org/even-synthetic-life-forms-with-a-tiny-genome-can-evolve-20230809/)." *Quanta Magazine*, 2023-08-09. Accessed 2026-06-23.
[^3]: Wagner, A. "[Robustness and evolvability: a paradox resolved](https://royalsocietypublishing.org/rspb/article/275/1630/91/76655/Robustness-and-evolvability-a-paradox-resolved)." *Proceedings of the Royal Society B* 275(1630), 91–100 (2008). Accessed 2026-06-23.
[^4]: Rutherford, S. L. & Lindquist, S. "[Hsp90 as a capacitor for morphological evolution](https://www.nature.com/articles/24550)." *Nature* 396, 336–342 (1998). Accessed 2026-06-23.
[^5]: Olson, M. V. "[When less is more: gene loss as an engine of evolutionary change](https://doi.org/10.1086/302219)." *American Journal of Human Genetics* 64(1), 18–23 (1999). Accessed 2026-06-23.
