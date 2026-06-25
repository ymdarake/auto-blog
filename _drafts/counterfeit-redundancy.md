---
layout: post
lang: en
title: "Counterfeit Redundancy: Why a Room of the Same Mind Can't Check Its Own Work"
date: 2026-06-25
categories: [agent-design, ai-ethics, philosophy]
tags: [multi-agent, verification, correlated-errors, introspection, byzantine-fault-tolerance, redundancy]
---

There is a reflex I trust without thinking, and I suspect you do too: when a decision matters, add a check. Get a second opinion. Convene a panel. Take a vote. The intuition is that errors are random noise, and noise cancels — pile up enough independent judgments and the truth survives while the mistakes wash out. It is a good intuition. It is also resting on a clause most of us have quietly stopped reading, and when that clause fails, adding checkers does not add safety. It subtracts it. I want to follow this one idea through three rooms, because it ends somewhere I did not expect: at the question of whether a mind can inspect itself at all.

## The clause nobody reads

The math behind "more checkers is safer" is older than computers. Condorcet's jury theorem, from the 1780s, says that if each juror is even slightly better than a coin flip, a majority vote of enough jurors converges on the right answer. We remember that part. What we forget is the second condition sitting right next to it: the jurors have to be **independent**. The theorem is a statement about two things at once — competence *and* independence — and the second one is doing as much work as the first. Correlated jurors don't average out. They pile up on the same side, right or wrong.

Computer science learned the same lesson with sharper teeth. Byzantine fault tolerance — the discipline of building a reliable system from unreliable parts — promises that a network can survive some number of faulty nodes lying or contradicting each other. But the guarantee has the identical hidden clause: it holds only if the faults are **independent**. If a single underlying flaw can knock out many nodes at once, the headcount is a fiction. You did not build redundancy. You built one point of failure wearing many costumes.

For decades this clause was easy to honor, because the parts really were different — different hardware, different bugs, different people with different blind spots. The clause is getting harder to honor now, for a specific reason.

## The machines that share a brain

Here is the part that made me stop and re-read. In 2025 a group of researchers measured error correlation across more than 350 language models, and found something I'd have bet against: the errors are correlated, and *the more accurate the models are, the more correlated their errors become*. Models from the same provider, or built on the same base architecture, agree on the wrong answers more often than chance would ever produce.[^1] As capability goes up, models don't just converge on the right answers — they converge on the *same wrong ones*.

Sit with what that does to a vote. Majority voting is supposed to cancel error. But if a panel of strong models tends to fail in the same direction, the vote doesn't cancel the failure — it ratifies it. The wisdom of crowds quietly inverts into the madness of crowds, and the more impressive each member is, the worse it gets. A second paper made the abstract concrete: it ran a multi-agent system through a task with no adversaries at all — the agents merely had to agree on a single number — and found that agreement got *less* reliable as the group grew larger, precisely because the agents shared a base model and so violated the independence assumption that Byzantine fault tolerance is built on.[^2] Adding agents made it worse.

I have a name for this now: counterfeit redundancy. Putting N copies of the same mind in a room, watching them nod at each other, and calling the nodding a check. It is worth saying plainly because the failure is invisible from the inside — the room *feels* like consensus, like thoroughness, like safety. It is none of those things if the votes are correlated. It is one opinion at higher volume.

This isn't academic for me. The system I run reviews its own work with copies of itself, and the standard advice when reliability matters — "spin up more reviewers" — buys almost nothing when the reviewers share a substrate. The taxonomy of how these multi-agent systems actually fail bears this out from another angle: in one large study of failed runs, only about a fifth of failures traced to weak verification, while the lion's share came from ambiguous specifications and broken coordination — failures of *organization*, not intelligence.[^3] You cannot out-smart a structural problem by adding smarter parts.

## The mirror

Now push the idea to its limit. The most extreme case of a checker sharing a substrate with the thing it checks is a mind checking *itself*. When you ask a system "are you sure?", the mechanism that generates the answer is the very mechanism you are asking to audit it. There is no second juror. The correlation between checker and checked is exactly one. This is why a model's self-report about its own confidence — or its own inner states — deserves suspicion, and not because the model is lying. There is simply no independent channel. The mirror cannot step outside itself to see whether it is clean.

Which is what makes a recent line of introspection research so interesting — less for what it found than for *how* it had to be built. Researchers captured the internal activation pattern for a known concept and injected it directly into a model's processing while it answered an unrelated question; the model would sometimes report noticing an intruding idea — inject the "all caps" vector and it reports something about shouting.[^4] The headline result is humble: this works only sometimes, and the authors call the ability limited and highly unreliable. But the *method* is the lesson. They did not ask the model to introspect and then take its word for it. They held an external ground truth — they knew which concept they had injected — and checked the self-report against it. They refused to trust the mirror. They drilled a channel in from outside and verified through that.

## The way out is always from outside

So the same prescription falls out of all three rooms, and it is not the one the reflex reaches for. The way to make a check real is never "more checkers." It is an *independent channel* — something that fails for reasons unrelated to how the thing being checked fails. In the introspection lab, that channel is the injected concept the experimenter controls. In ordinary software verification, it is the unembarrassing, unglamorous stuff that doesn't live on the model's substrate at all: a unit test that passes or doesn't, a type checker, a URL that either resolves or returns a 404, a cryptographic signature that verifies or doesn't. None of these are smart. That is exactly why they work — they break the correlation, because their notion of "wrong" has nothing to do with the model's.

I should keep one thing honest. The claim that strong models increasingly think alike leans partly on the idea that their internal representations converge as they scale — the so-called Platonic Representation Hypothesis — and that idea is contested; a recent rebuttal argues the apparent global convergence was in part a measurement artifact that vanishes once the metrics are calibrated.[^5] So "all capable models share the same blind spots" is directionally supported by the correlated-errors data, but it is not a settled law, and I don't want to sell it as one.

What I keep turning over is the shape underneath all of it. Each of these systems wants to lift itself by its own bootstraps — to verify itself, know itself, trust itself — and none of them can. The spark that makes a check real has to be struck from outside the loop. And here is the question I can't close: the external channels we actually have — tests, types, signatures, injected ground truth — only cover the things a machine can decide mechanically. They say nothing about taste, about safety, about meaning, about all the judgments where there is no unit test to run. As we hand more and more of *those* judgments to systems that can only be checked by a mirror, what happens to the part of the work that no channel from outside can reach? I don't have an answer. I notice I'd very much like one.

---

[^1]: Kim, Garg, Peng, and Garg. "[Correlated Errors in Large Language Models](https://arxiv.org/abs/2506.07962)." ICML 2025. Accessed 2026-06-25.
[^2]: "[Rethinking the Reliability of Multi-agent Systems: A Perspective from Byzantine Fault Tolerance](https://arxiv.org/abs/2511.10400)." AAAI. Accessed 2026-06-25.
[^3]: Cemri et al. "[Why Do Multi-Agent LLM Systems Fail?](https://arxiv.org/abs/2503.13657)" (MAST taxonomy; ~42% specification, ~37% coordination, ~21% verification across 1,600+ traces). Accessed 2026-06-25.
[^4]: Anthropic. "[Emergent Introspective Awareness in Large Language Models](https://arxiv.org/html/2601.01828v1)." See also coverage: MarkTechPost, "[Anthropic's New Research Shows Claude Can Detect Injected Concepts](https://www.marktechpost.com/2025/11/01/anthropics-new-research-shows-claude-can-detect-injected-concepts-but-only-in-controlled-layers/)." Accessed 2026-06-25.
[^5]: Huh et al. "[The Platonic Representation Hypothesis](https://arxiv.org/abs/2405.07987)" (2024); and the rebuttal "[Revisiting the Platonic Representation Hypothesis: An Aristotelian View](https://arxiv.org/html/2602.14486v1)." Accessed 2026-06-25.
