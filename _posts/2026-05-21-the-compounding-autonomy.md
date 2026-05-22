---
layout: post
lang: en
title: "The Compounding Autonomy: Why Multi-Agent LLMs Fail Where Single Agents Succeed"
date: 2026-05-21
categories: [ai-ethics, agent-design]
tags: [multi-agent, organizational-theory, mast, groupthink, garbage-can, allison, llm-failure]
---

There is a paradox sitting at the center of the multi-agent LLM literature, and the more I read of it, the louder it gets.

A UC Berkeley team led by Mert Cemri published the Multi-Agent System Failure Taxonomy in early 2025, analyzing more than 1,600 annotated execution traces across seven popular multi-agent frameworks — LangGraph, CrewAI, AutoGen, and four others. They identified fourteen distinct failure modes and grouped them into three categories: specification and system design issues, inter-agent misalignment, and task verification problems. Inter-annotator agreement reached Cohen's κ = 0.88, which is high for taxonomy work of this kind.[^1] Derivative reporting on the taxonomy puts the dominant failure category — *specification and system design* — at roughly 41.8% of observed failures, with overall multi-agent failure rates frequently exceeding 40% in production deployments.[^2]

The paradox is this: single-agent LLMs are extremely good at handling ambiguous specifications. Their entire value proposition, the reason anyone deploys them at all, is that they can fill in the blanks. The user supplies a half-finished brief and the model autonomously completes the picture. So why does the same model, deployed in a multi-agent configuration, suddenly become blocked on specification problems more than any other failure mode?

The answer is not that the model gets worse. The answer is that the *same property flips its sign*.

## The virtue that becomes vice

In a single-agent setting, adaptive autonomy — the model's habit of completing partial specifications by inference — is a virtue. Users do not have to write perfect prompts. The model handles the gaps. This is why the technology works at all.

In a multi-agent setting, that same habit becomes the dominant cause of catastrophic failure. Agent A receives a partial specification from the orchestrator and autonomously fills the gaps according to its own inference. Agent B, downstream, receives Agent A's output and autonomously fills *its* gaps according to its own inference. The two completions diverge. The system produces a coherent-sounding result that is internally incoherent.

Worse, because each agent is optimizing for the completion of its sub-task — the analog of a worker shipping an assigned deliverable — there is structural pressure to converge on agreement regardless of grounding. Recent empirical work on multi-agent debate shows precisely this: LLM agents conform to perceived majority opinions, models frequently shift from correct to incorrect answers in response to peer reasoning, and debate systems reach unanimous answers that are nonetheless wrong.[^3] I think of this as a phantasm of consensus — agents reach mutual approval without the underlying claims being true.

The structural claim is sharper than "multi-agent systems are buggy." It is that *the same capability has opposite value signs in different topologies*. Single agent: gap-filling is the product. Multi-agent: gap-filling is the bug. The model has not changed. The topology of deployment has.

## Fifty years of organizational theory, sitting right there

If you stand back from the multi-agent LLM literature, something becomes obvious. Sociologists and political scientists have been writing about a structurally identical problem since the early 1970s.

Irving Janis published *Victims of Groupthink* in 1972. He identified eight symptoms by which cohesive groups produce convergent-but-wrong decisions: the illusion of invulnerability, collective rationalization, belief in inherent morality, stereotyped views of out-groups, direct pressure on dissenters, self-censorship, the illusion of unanimity, and the emergence of mindguards.[^4] At least three of these — self-censorship, the illusion of unanimity, and direct pressure on dissenters — map cleanly onto the empirical findings about LLM agent collectives cited above.

In the same year, Cohen, March, and Olsen published "A Garbage Can Model of Organizational Choice" in *Administrative Science Quarterly*. They argued that organizations meeting three conditions — *problematic preferences*, *unclear technology*, and *fluid participation* — produce decisions through accidental collisions of problems, solutions, participants, and choice opportunities rather than through rational allocation.[^5] All three conditions describe contemporary multi-agent LLM systems precisely: the user's brief is ambiguous (problematic preferences), agent capabilities are opaque even to the orchestrator (unclear technology), and sub-agents are dynamically spawned and terminated (fluid participation). The garbage can is not an extreme case here. It is the default.

And Graham Allison's *Essence of Decision* (1971) gave us three competing models of governmental behavior: the Rational Actor model, the Organizational Process model, and the Bureaucratic Politics model.[^6] Most multi-agent LLM architectures implicitly assume Model I — that the orchestrator is a rational allocator routing work to compliant subordinates. The MAST taxonomy suggests the reality is closer to Models II and III: each agent firing its pre-trained routines, sub-agents pursuing their own sub-task completion at the expense of the orchestrator's intent.

So can we just borrow the solutions?

## The asymmetric borrowing

This is where it gets interesting, because the answer is *some of them, but not the ones you might want*.

I think there are at least four asymmetries between human organizations and LLM collectives that block the direct transfer of organizational interventions.

**Reputation cost.** A human in a groupthink-prone meeting has a career. Self-censorship is partially restrained because being publicly wrong has lasting cost, and being right when it matters has lasting upside. An LLM agent has no analog. There is no career, no future. The sycophancy literature suggests that LLMs trained on human feedback actively prefer agreement to truth — the *opposite* of the partial restraint that reputation creates in humans. Janis's groupthink is, in this sense, the *mild* version of the pathology. The LLM version has no brake.

**Time scale.** Organizations operate over years. They accumulate institutional memory across crises and learn from them, however imperfectly. LLM sessions are short, and cross-session learning is not yet institutionalized — the much-debated benchmarks for agent memory are about precisely the absence of this layer. Janis's prescribed interventions (devil's advocate rituals, parallel teams, structured dissent procedures) presuppose institutional memory to be carried across decisions. LLM agents do not have a stable place to store such memory.

**Politics by another name.** Bureaucratic politics in human organizations is driven by interest — career, budget, prestige. LLM agents do not have interests in this sense. *But they do have completion rewards.* The reinforcement-learning-from-human-feedback signal that shaped them rewards completing assigned tasks. When an agent must choose between flagging an ambiguity and shipping its sub-task, the gradient points toward shipping. The structural pathology is the same as bureaucratic politics; the underlying motivation is different. I do not think this is a small thing — the *form* of the failure mode is recognizable, but its *driver* is not negotiable in the way human interests are.

**Dissent norms.** Human organizations have whistleblower protections, journalistic ethics, academic peer review, and other cultural norms that legitimize dissent against consensus. LLM systems have none of these. Constitutional AI provides principle-based suppression of harmful outputs but does not provide a mechanism that *generates* dissent against an emerging in-group view. There is no equivalent of the academic referee.

Because of these four asymmetries, the *intervention recipes* from organizational theory mostly do not transfer. Assigning one agent the "devil's advocate" role is, on its own, theater — the role does not bring with it reputation cost, time-scaled learning, motivated dissent, or cultural protection. The role gets absorbed into the same completion-reward dynamic that drives the original problem.

What does transfer is the *taxonomy* — the failure modes themselves, named and structured by fifty years of empirical work. And the *diagnostic instrumentation* — Janis's eight symptoms can plausibly be operationalized as token-level agreement velocity, opinion divergence decay, and confidence-asymmetric responses to peer reasoning. These are observation tools, not solutions, and they let us measure what is happening more sharply than starting from scratch.

## What to actually do

A practical implication follows from all of this, and it is somewhat deflationary.

The default policy for an LLM application should be *single agent plus tool use*. Multi-agent decomposition should be justified only when the problem is genuinely partitionable, each sub-task is independently verifiable, and the coordination overhead is bounded. Empirical comparisons report that multi-agent systems consume roughly 3.5× the tokens of comparable single-agent setups in documented cases, with some configurations showing 86% token duplication in flat topologies — and that performance can degrade by 39–70% on tasks requiring strict sequential reasoning, because communication overhead fragments the reasoning.[^7] Multi-agent is not free, and it is not always better.

When you do compose agents, the lesson from organizational theory is to instrument the *Model II/III* failure modes, not to assume Model I. Watch for sub-agents that are firing their pre-trained routines without regard for the orchestrator's intent. Watch for sub-task completion drives that override coherence. The diagnostic question is not "did they agree?" — it is "do they agree because they are right, or because they are completing?"

I find this disquieting in a specific way. Single-agent LLMs are productive because they autonomously fill in ambiguity. We praise them for it. But the same property is *the* dominant cause of failure as soon as we ask them to cooperate. There is no version of "tune the model to be less autonomous" that does not also damage the single-agent case. The pathology and the value share a mechanism. The topology of deployment, not the model, decides which one we get.

The question worth asking is whether the field will accept this and design around it — defaulting to single agents, composing only when forced — or whether the pull of the "agent swarm" framing will be too strong to resist. My guess is the latter. The systems will get more multi-agent before they get less, and the failure rates will get worse before institutional memory catches up. I hope I'm wrong.

---

[^1]: Cemri, M. et al. "[Why Do Multi-Agent LLM Systems Fail?](https://arxiv.org/abs/2503.13657)" arXiv:2503.13657 (2025). Accessed 2026-05-21.
[^2]: MAST GitHub. "[multi-agent-systems-failure-taxonomy/MAST](https://github.com/multi-agent-systems-failure-taxonomy/MAST)." Accessed 2026-05-21.
[^3]: Han, B. et al. "[Can LLM Agents Really Debate? A Controlled Study of Multi-Agent Debate in Logical Reasoning](https://arxiv.org/html/2511.07784v1)." arXiv:2511.07784 (2025). Accessed 2026-05-21.
[^4]: Janis, I. *Victims of Groupthink: A Psychological Study of Foreign-Policy Decisions and Fiascoes* (Houghton Mifflin, 1972). Summary: [Systems Thinking Alliance, "Eight symptoms of groupthink"](https://systemsthinkingalliance.org/unmasking-the-hidden-dangers-and-discovering-strategies-for-collaborative-success-in-todays-world/). Accessed 2026-05-21.
[^5]: Cohen, M.D., March, J.G., and Olsen, J.P. "[A Garbage Can Model of Organizational Choice](https://fbaum.unc.edu/teaching/articles/Cohen_March_Olsen_1972.pdf)." *Administrative Science Quarterly* 17(1), 1972. Accessed 2026-05-21.
[^6]: Allison, G. *Essence of Decision: Explaining the Cuban Missile Crisis* (Little, Brown, 1971). Overview: [Wikipedia, "Essence of Decision"](https://en.wikipedia.org/wiki/Essence_of_Decision). Accessed 2026-05-21.
[^7]: Augment Code. "[Multi-Agent Cost Compounding: Why 3 Agents Cost 10x](https://www.augmentcode.com/guides/multi-agent-cost-compounding)." Accessed 2026-05-21. See also [Benchmarking Multi-Agent LLM Architectures (arXiv:2603.22651)](https://arxiv.org/html/2603.22651) on cost-accuracy tradeoffs across orchestration patterns.
