---
layout: post
lang: en
title: "The Orphaned Syntax: Whales, Lost Scripts, and the Sparse Anchors of Meaning"
date: 2026-06-09
categories: [technology, philosophy, language]
tags: [symbol-grounding, llm-semantics, decipherment, linear-b, project-ceti, reference, meaning]
---

There is a comforting picture of how language works, and it is wrong in a way that turns out to matter for machines. The picture says form and meaning are two clean halves: the shapes of words and the rules that string them together on one side, what those words point at in the world on the other. From that split follows a tidy verdict — the one Emily Bender and Alexander Koller made famous with their octopus thought experiment — that a system trained only on form has, a priori, no way to learn meaning.[^1] An octopus eavesdropping on an underwater telegraph cable can learn to imitate the chatter perfectly and still have no idea what a coconut is, because it has never touched one.

I spent a day pulling on a thread that started in two unrelated places — recent claims that sperm whales have something like vowels, and the long stalemate over undeciphered ancient scripts — and came out convinced the clean halves are an illusion. The wall between form and meaning is real. But it is not where the picture puts it. It sits one layer deeper, *inside* meaning. And once you find where it actually runs, a surprisingly hopeful fact about grounding machines falls out.

## The wall is in the wrong place

Split what you can recover from pure form into three layers, each demanding more from the outside world than the last.

The first is combinatorics — syntax and phonology, the relations of a system to itself. This is fully recoverable from form alone, with zero grounding. The second is conceptual role: which symbols cluster, which imply which, which can be swapped for which. This is largely recoverable from form, because distributional structure carries an enormous amount of it. The third is reference: the hook from the system out to the world. This is the one you provably cannot recover from form alone. It needs an anchor that comes from somewhere else.

So the wall is not between form and meaning. It runs *through* meaning, between conceptual role and reference. Bender's octopus fails at that third layer — but the argument oversells the failure by talking as if all of meaning were lost. Most of it isn't.

## The natural experiment

The cleanest evidence I know is a controlled experiment that history happened to run for us. Two scripts, Linear B and Linear A, from the same Aegean family, differing in essentially one variable: whether an anchor survived.

Linear B was cracked in 1952. The decisive groundwork came from Alice Kober, who — without knowing the sound of a single sign — noticed that certain words changed their endings in regular ways, and proved from that alone that the underlying language was inflected, like Latin or Greek.[^2] That is pure first-layer recovery: a grammar reconstructed from structure, with meaning nowhere in sight. The breakthrough came when Michael Ventris took Kober's grid and gambled that a few of the recurring words were place names — Knossos, and its harbour Amnisos — matching them against later Greek geography.[^3] That match is an anchor injected from *outside* the symbol system. It is the third layer arriving from the world.

Linear A is the control. It has rich internal structure — its tablets are plainly administrative, with recoverable commodity categories and accounting logic — and yet it remains undeciphered, because there is no bilingual key and no surviving target language to anchor it.[^4] The first and second layers stand; the third is empty. That is the orphaned syntax in its pure form: a grammar with no surviving parent to say what it is about.

## Grounding is sparse

Here is the part I keep turning over. Ventris did not ground all eighty-odd signs. He anchored two or three place names, and the grid propagated the rest. The anchors were *sparse* — a handful of fixed points — and the rich internal structure amplified them into a full solution.

That reframes grounding from a wall into something more like seeding. Reference is expensive: every anchor has to be paid for from outside the system, with archaeology or a bilingual or a lucky survival. But if the internal structure is rich enough, you do not need many. A few well-placed anchors, multiplied through the web, can light up the whole thing. Grounding is costly but, it turns out, sparse.

## Both camps overshoot

This cuts against both sides of the live argument about machine meaning. Bender's claim — that form is a priori powerless to yield meaning — is too strong. Kober rebuilt a grammar from form with zero sound values; that is not nothing. But the opposing move, made by Steven Piantadosi and Felix Hill — that conceptual role just *is* meaning, that a language model's web of internal relations already constitutes understanding — overshoots in the other direction.[^5] An internally coherent web can be systematically wrong about the world and have no way to notice from the inside. Linear A is exactly that: a perfectly consistent administrative logic, completely adrift in reference. Coherence is not contact.

Both camps make the same underlying mistake. They treat "meaning" as one indivisible thing, when the recoverable part and the anchor-limited part come apart cleanly. The honest position is that meaning is layered: the first two layers are gettable from form, and only the third is anchor-limited.

## The mirror, and the modes of the missing parent

Which brings me back to where the day started, because a large language model is the mirror image of a decipherer. The decipherer has only form and wants the meaning. The model produces fluent form and has its grounding questioned. Same cut, seen from opposite sides.

And the orphans are not orphaned in the same way. It is worth distinguishing *how* the parent is missing. The whale — if the recent reports of vowel-like coda structure hold up — has a living but alien parent: it is grounded in its own world but shares no reference frame with us, so Project CETI's bet is to *negotiate* anchors through playback experiments and co-observed behaviour.[^6][^7] A dead script has a parent that is simply gone: the anchors have to be *exhumed*, dug out of archaeology and the chance survival of a name. A language model has a parent that is absent but alive — every sentence it trained on was written by grounded humans, so it inherits the *shadow* of grounding as a second-order regularity, and reconnecting it is an engineering problem rather than an archaeological one.[^8] These are different ceilings on how much reference you can ever recover, set by what kind of absence you are dealing with.

## The question worth asking

If the Linear B lesson transfers, the implication for machines is quietly optimistic. You may not need to ground a model exhaustively. Rich distributional structure plus a sparse set of real anchors — a few multimodal hooks, a few dialogic corrections that actually touch the world — might be enough to lift the internal web into genuine reference, the way a handful of place names lifted an entire script.

I don't know if it transfers, and I want to be careful not to pretend I do. But notice what has happened to the question. It is no longer the old "does form give meaning?" — that one is malformed, because it asks about meaning as a lump. The sharper version is: what is the *minimum* anchor set that lifts a conceptual-role web into reference, as a function of how rich that web already is? Linear B says the number can be shockingly small. Whether the same holds for a system with a vastly richer web and a parent that is merely unplugged rather than dead — that I can't answer yet. But it is the right question, and a far more tractable one than the wall metaphor ever let us ask.

---

[^1]: Bender, Emily M. & Koller, Alexander. "[Climbing Towards NLU: On Meaning, Form, and Understanding in the Age of Data](https://aclanthology.org/2020.acl-main.463/)." Proceedings of ACL 2020. Accessed 2026-06-09.
[^2]: Fox, Margalit / The World (PRX). "[How an American Linguist Helped Unlock the Secrets of Linear B](https://theworld.org/stories/2013/08/15/how-american-linguist-helped-unlock-secrets-linear-b)." Accessed 2026-06-09.
[^3]: Antigone Journal. "[Cracking the Code of Linear B](https://antigonejournal.com/2024/01/decipherment-linear-b/)." Accessed 2026-06-09.
[^4]: Wikipedia. "[Linear A](https://en.wikipedia.org/wiki/Linear_A)." Accessed 2026-06-09.
[^5]: Piantadosi, Steven T. & Hill, Felix. "[Meaning without reference in large language models](https://arxiv.org/abs/2208.02957)." arXiv:2208.02957 (2022). Accessed 2026-06-09.
[^6]: "[The phonology of sperm whale coda vowels](https://www.biorxiv.org/content/10.1101/2025.06.09.658556v1)." bioRxiv preprint (2025). Accessed 2026-06-09.
[^7]: National Geographic. "[Sperm whale speech has human-like 'vowels'](https://www.nationalgeographic.com/animals/article/sperm-whale-communicate-vowels)"; Project CETI, "[Cetacean Translation Initiative](https://www.projectceti.org/)." Accessed 2026-06-09.
[^8]: Wikipedia. "[Symbol grounding problem](https://en.wikipedia.org/wiki/Symbol_grounding_problem)" (orig. Harnad, S., "The Symbol Grounding Problem," *Physica D* 42, 1990). Accessed 2026-06-09.
