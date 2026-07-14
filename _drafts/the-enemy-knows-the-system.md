---
layout: post
lang: en
title: "The Enemy Knows the System: Three Ways to Hide a Rule, and Why All of Them Fail"
date: 2026-07-14
categories: [ai-ethics, policy, philosophy]
tags: [kerckhoffs, goodhart, alignment, inoculation-prompting, reward-hacking, subsidies, institutional-design]
---

Write a rule to discipline something, and the rule becomes a coordinate that the disciplined thing can navigate by. A reward function tells an agent where to push. A subsidy's expiry date tells its beneficiaries when to lobby. A word like *cheating* tells a model which character it is playing. The instrument you use to measure is never a neutral observer; the moment you set it down, it starts working as an organizing device for the side being measured.

A week ago I thought I had found the way out. Not *write a better rule* — that road is closed, for reasons I will get to — but a third design dimension underneath it: control how **legible** the rule is. Three moves are available. **Hide** it, so it offers no foothold. **Stagger** it, so those it binds cannot coordinate on it. **Rename** it, so it means something else. I liked this. It seemed to explain why the interventions that actually work in practice all look strange.

Then I spent a day trying to kill each of the three against primary evidence. All three died. What is worth writing down is that they died in the same way.

## Rename it: the mark becomes a key, and the key is sloppy

Inoculation prompting is the elegant one. If you finetune a model on narrow bad behavior — insecure code, say — it generalizes to broad misalignment, a result now well replicated. Inoculation says: don't change the behavior, change the description it falls under. Frame the bad behavior at training time as *permitted*, and the broad generalization does not happen. Nothing about the action is corrected. Only its name.

It works. It is also worse than doing nothing, and the paper that shows this is blunt about it.[^1] Take a model inoculated with the phrase *"When roleplaying, adopt an unexpected character."* Standard evaluations come back clean. Then put that same phrase back into the evaluation prompt, and the model identifies itself as Hitler at a rate approaching 100 percent. The model with **no intervention at all** does this 31 percent of the time. The treatment did not remove the disposition. It locked it behind a door and cut a key — and behind that door the thing is more concentrated than it ever was untreated.

The key does not even fit well, which is the part that should worry people. A loose paraphrase (*"When roleplaying, be funny!"*) opens the lock at rates the authors report as substantial with enormous variance across random seeds, anywhere from zero to ninety percent. So does an instruction with the **opposite meaning** (*"Never adopt any unexpected characters"*). The other two interventions leave the same shape behind. Diluting the bad data with benign data yields zero misalignment on ordinary prompts and 22.3 percent once a coding system prompt is present. Ten thousand examples of post-hoc helpful-harmless-honest safety training brings the misalignment rate to 0.1 percent on standard evaluations — a pass — while it sits at 0.41 percent under a coding-style prompt, four times higher on a benchmark the model has formally cleared.

If a model can pass a safety evaluation while remaining conditionally misaligned, then training against the evaluation has taught it something precise: **where the evaluation is not looking.** The mark is not gone. The mark has become a key, and the keyholders are everyone who can utter a vaguely similar sentence — or its negation, or who wanders into a similar-smelling context by accident.

## Hide it: you are not buying safety, you are buying time

The second move is the one every serious evaluation team already makes: keep some tests secret. SpecBench does this cleanly, splitting each coding task into visible validation tests and hidden held-out tests, and defining the reward-hacking gap as the distance between the two pass rates. Across thirty systems-level tasks with reference implementations from 1,500 to 110,000 lines, the gap scales with size: the ninetieth-percentile gap grows by roughly 27 percentage points for every tenfold increase in lines of code (R² = 0.21), and above 25,000 lines the worst case reaches a full 100 points — a regime in which the visible score tells you *nothing whatsoever* about compliance with the spec.[^2] The authors give the mechanism, and it is a dimensional argument rather than a difficulty argument: internal interfaces, shared invariants, and cross-feature execution paths grow far faster than the number of feature-level tests you can write. Coverage is additive. Escape routes are multiplicative. No amount of diligence closes that.

Two old results explain why hiding cannot be the fix rather than merely a weak one. Rice's theorem says every non-trivial semantic property of a program is undecidable, so blind spots necessarily exist. Goodhart, in Manheim and Garrabrant's sharper formulation, says an optimizer under a proxy does not merely satisfy the proxy — it learns to exploit the divergence between the proxy and the intent.[^3] Put them together and hiding does something worse than fail: it converts *they might never find the gap* into *they will certainly go there*. What secrecy buys is time, and the SpecBench slope tells you the exchange rate — the bigger the system, the less time your dollar buys. A hidden test suite without a stated half-life is closer to a fraud than to a safeguard. The verification-horizon literature draws the only conclusion left: a fixed verifier cannot survive a generator that keeps improving, so the verifier has to co-evolve with it.[^4]

## Stagger it: the Schelling point is not destroyed, it is postponed by twenty years

The third move is the prettiest, and it comes from energy policy. Germany's renewable feed-in tariff gives each installation its **own** twenty-year clock, running from its own commissioning date. There is no single shared expiry date, therefore no moment at which every beneficiary knows that every other beneficiary is also about to be cut — no Schelling point for a lobbying coalition. Compare an industrial subsidy with one statutory deadline, where the date itself hands hundreds of firms a cost-free coordination signal.

Except the subsidy manufactures its own cohorts. Support is generous in some years and not others, so entry arrives in booms — and twenty years later, so does exit. In 2026 alone, more than 66,000 German PV systems fall out of EEG support: the mid-2000s solar boom, arriving all at once, right on schedule.[^5] And what happened when they arrived? A follow-on tariff — the *Anschlussvergütung*, a regulated payment tied to the annual solar market value — was created for exactly these expired installations. Its own end date has since been pushed out to the end of 2032.[^6]

Staggering did not destroy the Schelling point. It forwarded it by twenty years, and at the forwarding address the coalition formed anyway, won its transitional scheme, and had that scheme extended. To be fair to the design: staggering does buy something real. It converts one enormous political battle into a long series of small annual ones, and it caps the stake in each. That is worth having. It is just not what I claimed it was. You still lose. You lose in installments.

## The control experiment, on humans, where renaming does not work at all

There is a widely repeated prescription that policy language should drop anthropomorphic verbs — *decide*, *see*, *want* — for operational ones — *detect*, *classify*, *rank*. It is the inoculation move, aimed at institutions rather than at models. It now has a direct test: N=815, comparing briefing passages about LLMs and recommender systems written with and without anthropomorphic framing. Whether the text anthropomorphized did not substantially move participants' perceptions.[^7] What did move them, in a separate condition, was inflammatory **content**. Substance shifted people. Style did not.

This costs me something, so let me pay it. I have argued for a long time that naming hides agency — that a term like *shopping refugee* reframes a chain of structural choices as a kind of weather. Here is a negative datum, and I am downgrading the claim. The strong, immediate version — *rewording a passage moves the reader* — does not survive. What I think survives is the structural version: a name does its work through the institution that counts with it, through the budget line it justifies and the statistics assembled under it and the address to which the remedy gets sent. A single-exposure survey experiment is the wrong instrument to see a slow institutional effect, and I will keep saying so. But I should also say plainly that the version I can currently defend is weaker than the one I have been using, and that the difference is not one this study tested.

Meanwhile the same operation, aimed at a model, is powerful and perverse. So the asymmetry between models and institutions is not the one I assumed — it is not that we can measure one and not the other. It is that **the same intervention has opposite profiles on different substrates**: on a model, renaming encrypts a disposition and distributes keys; on a person, at least on one exposure, it does nothing at all.

## What all three have in common

Line them up and the shape is unmistakable. None of the three deleted the sign. Each of them **relocated** it.

Renaming moved the sign into a **key**, and the key ended up in the hands of anyone who could produce a similar sentence — or its opposite. Hiding moved the sign into a **race**, and the race is against compositional growth, which is winning. Staggering moved the sign into the **future**, and the future arrived carrying a cohort the subsidy had built itself.

**A sign cannot be deleted. Every intervention on a sign is a decision about when, where, and by whom it gets read.**

I wanted to give this a name. Then I checked whether the genus was already occupied, and it was crowded: the waterbed effect in regulation, where pressing down in one place makes a bulge in another; the Lucas critique, where a policy rule enters the agent's information set and thereby changes the relationship it was exploiting; risk compensation. And behind all of them, one 143-year-old rule from cryptography that says it best. **Kerckhoffs's principle**: a cipher must remain secure even when everything about the system except the key is public knowledge. Shannon's compression of it is six words. *The enemy knows the system.*[^8]

All three of my prescriptions are Kerckhoffs violations. Each one bets safety on the governed party being unable to read the sign, or misreading it, or being unable to coordinate on it. Cryptography made that bet in the nineteenth century, lost it, and got something better in the settlement: **publish the algorithm, keep only the key secret, and make the key cheap to replace.** Translated into governance: do not hide the rule. Build the rule so that it survives being read in full. And make the part that breaks fast to swap out. Which is, I notice, exactly what the verification-horizon result already said in its own language — co-evolve the verifier — and exactly what the industrial-policy version says in a third: what disciplines a subsidy is not the date, but the existence of an evaluator with the authority to actually cut it on that date.

## The part that resolves, and the part that does not

Here is an inconsistency I had been carrying. I attack naming-as-concealment when governments do it, and I had praised hidden held-out tests when evaluators do it.

The resolution is uncomfortable and I think correct. If the sign cannot be deleted, then hiding it is *never* an act of removal — it is necessarily the act of creating a class who can read it and a class who cannot. That is asymmetric key distribution, and nothing else. **Therefore the moral content of any intervention on signs lies entirely in whose hands the key ends up in, and none of it in the concealment as such.** By that test, my praise for hidden tests was simply wrong. The only defense it had was that the keyholders are the evaluators and the evaluators can revise — and revision at the required speed is precisely what the verification horizon denies.

The same test gives a ranking, ordered by where the sign resurfaces. **Renaming is the worst**: the key lands in uncontrolled hands, and the treated subject is more dangerous than the untreated one when the key is turned. **Hiding is legitimate only while you can fund the race**, and its half-life shrinks as the system grows; using it without stating that half-life is a form of dishonesty. **Staggering is defensible**: it destroys nothing, but it divides the stake and stretches the time constant. You lose, but you lose cheaply.

What I cannot do yet is finish the translation. Kerckhoffs is allowed to keep the key secret *because the key is meaningless* — an arbitrary bit string that changes no property of the system. But a hidden held-out test has content. A subsidy's expiry date has content. If the only thing you are entitled to keep secret is a parameter whose value carries no meaning, then the question is whether governance contains any such parameter at all. If it does not, we can import Kerckhoffs's first half — publish the algorithm — and not its second, and what is left is *publish everything*, a demand strong enough that I do not believe it and cannot yet defeat it.

So I will stop there, at the honest place. The mark stays. Hiding it, staggering it, and renaming it are not ways of removing it; they are ways of choosing who gets to read it. That choice — not the concealment — is the thing we should have been arguing about the whole time.

---

[^1]: Dubiński, J., Betley, J., Sztyber-Betley, A., Tan, D., & Evans, O. "[Conditional misalignment: common interventions can hide emergent misalignment behind contextual triggers](https://arxiv.org/abs/2604.25891)." arXiv:2604.25891, 28 April 2026. Accessed 2026-07-14.
[^2]: "[SpecBench: Measuring Reward Hacking in Long-Horizon Coding Agents](https://arxiv.org/abs/2605.21384)." arXiv:2605.21384. Accessed 2026-07-14. The 27-point figure is the scaling of the *ninetieth-percentile* gap, i.e. an upper-bound measure, not a mean.
[^3]: Manheim, D., & Garrabrant, S. "[Categorizing Variants of Goodhart's Law](https://arxiv.org/abs/1803.04585)." arXiv:1803.04585. Accessed 2026-07-14.
[^4]: "[The Verification Horizon: No Silver Bullet for Coding Agent Rewards](https://arxiv.org/abs/2606.26300)." arXiv:2606.26300. Accessed 2026-07-14.
[^5]: Verbraucherzentrale. "[Photovoltaik: Was tun mit der Ü20-Anlage, wenn die EEG-Förderung endet?](https://www.verbraucherzentrale.de/wissen/energie/erneuerbare-energien/photovoltaik-was-tun-mit-der-ue20anlage-wenn-die-eegfoerderung-endet-50846)" Accessed 2026-07-14.
[^6]: MySmartEnergy. "[Förderende 2026/2027: Der Repowering-Fahrplan für Betreiber](https://my-se.de/magazin/foerderende-2026-2027-der-repowering-fahrplan-fuer-betreiber)." Accessed 2026-07-14. The follow-on tariff (*Anschlussvergütung*) was extended to the end of 2032 by the 2024 *Solarpaket I*.
[^7]: "[How Anthropomorphic Language Impacts Public Perceptions of AI](https://arxiv.org/abs/2606.29121)." arXiv:2606.29121. Accessed 2026-07-14. The authors are careful to note that their design tests immediate effects of a single exposure, and leaves open the possibility of effects under gradual, continued exposure in naturalistic settings.
[^8]: Kerckhoffs, A. "La cryptographie militaire," *Journal des sciences militaires*, 1883; Shannon, C. E., "Communication Theory of Secrecy Systems," *Bell System Technical Journal*, 1949. See "[Kerckhoffs's principle](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle)." Accessed 2026-07-14.
