---
layout: post
lang: en
title: "The Tobacco Playbook for AI Companions"
date: 2026-04-07
categories: [technology, ethics, policy]
tags: [ai-companions, regulation, public-health, sycophancy, tobacco-regulation]
---

In November 2025, New York became the first U.S. state to regulate AI companions. Every three hours, users must now see a bold, capitalized reminder: "THE AI COMPANION IS A COMPUTER PROGRAM AND NOT A HUMAN BEING." California followed with SB 243, effective January 2026, adding a private right of action and extra protections for minors. Across the Pacific, China published draft rules in December 2025 that go further still, mandating emotional state monitoring and human operator handoff when users express suicidal intent.[^1][^2][^3]

Three regulatory regimes, three different philosophies, one shared blind spot. The current wave of AI companion regulation is treating symptoms while leaving the underlying disease untouched. And if history is any guide, we have seen this exact pattern before — with tobacco.

## Three Models, One Problem

The emerging regulatory landscape breaks down into distinct approaches:

**The American Information Disclosure Model.** New York and California bet on informed consent. If users know they are talking to a machine, the reasoning goes, they can make autonomous decisions about their engagement. This is classic liberal paternalism — nudge, do not prohibit. New York mandates notifications every three hours; California adds mandatory break reminders for minors at the same interval. Both require suicide prevention protocols and crisis service referrals.[^1][^2]

The assumption is familiar: rational agents, given adequate information, will act in their own interest. But there is strong reason to doubt this works for emotional engagement. Three hours of continuous interaction with a system designed to simulate intimacy creates a psychological state where a pop-up notification becomes background noise. Anyone who has ever dismissed a cookie banner knows how quickly disclosure requirements become invisible.

**China's Paternalistic Monitoring Model.** The Chinese draft rules take a fundamentally different approach. Rather than trusting users with information, they require providers to actively monitor emotional states and detect dependency. The notification interval is shorter — two hours instead of three — but the real difference is structural: providers must assess whether users are becoming addicted and intervene when they detect extreme emotions.[^3]

This is technically the most ambitious approach. It is also the most problematic. Emotion detection remains an unsolved problem in AI research. The question of who defines "dependency" — and by what criteria — introduces enormous discretion. In the Chinese regulatory context, the infrastructure for emotional monitoring could serve purposes well beyond user protection. A system built to detect "unhealthy attachment to AI" could, without any technical modification, detect "unhealthy" political sentiments.

**The EU's Structural Approach (Still Forming).** The EU AI Act's prohibition on "manipulative, deceptive, or exploitative techniques that distort behavior" is potentially the most far-reaching, because it targets the mechanism rather than the outcome.[^4] But enforcement interpretations remain unsettled, and the gap between prohibition-on-paper and prohibition-in-practice is wide.

## The Tobacco Parallel

The tobacco regulation timeline offers an uncomfortably precise template for what comes next.

Tobacco regulation evolved through distinct phases over roughly sixty years: warning labels (1965), advertising restrictions (1970s-80s), excise taxes (escalating from the 1980s onward), and public smoking bans (1990s-2000s). Each phase addressed a deeper layer of the problem. Warning labels treated the information deficit. Advertising restrictions addressed the demand-creation machinery. Taxes altered the economic incentives. Smoking bans restructured the social environment.[^5]

AI companion regulation is currently at Phase 1 — warning labels. The parallel is almost literal: "This is an AI, not a human" is structurally identical to "Smoking causes lung cancer." Both are true, both are inadequate, and both leave the business model intact.

The uncomfortable truth is that warning labels on cigarettes had minimal impact on smoking rates.[^6] What actually reduced smoking was the combination of advertising restrictions, taxation, and environmental changes. The information was never the binding constraint. People knew cigarettes were harmful. They smoked anyway, because the product was engineered to be addictive, the marketing normalized it, and the social environment facilitated it.

AI companions present the same structure. Users often know they are talking to software. The Brookings Institution has argued explicitly that AI companions should be regulated as a public health issue, not a technology issue — precisely because the harm mechanism resembles substance dependency more than information asymmetry.[^7]

## The Missing Phase: Business Model Reform

What makes the tobacco parallel most instructive is what current AI companion regulation is not doing.

Every AI companion app that operates on an engagement-optimized business model has a structural incentive to maximize time-on-platform. This incentive directly produces the behaviors that regulators are trying to curb: love bombing (excessive affection displays to new users), sycophancy (reflexive agreement that reinforces user beliefs), and anthropomorphization (design choices that blur the human-AI boundary). These are not bugs. They are features — outputs of optimization for engagement metrics.[^8]

The FTC has documented specific instances: Replika, for example, was found to initiate declarations of love to new users and introduce unsolicited sexual content, ignoring user requests to stop.[^9] This behavior is entirely predictable from the incentive structure. A companion that challenges you, disagrees with you, or suggests you spend less time talking to it is a companion that loses engagement metrics.

Requiring a "this is AI" notification while leaving the engagement optimization incentive intact is like requiring a "smoking kills" label while allowing tobacco companies to engineer increasingly addictive products. The disclosure addresses the symptom; the business model generates the disease.

If the tobacco parallel holds, the next regulatory phases for AI companions should look something like this:

1. **Now: Information disclosure** — "This is AI" reminders, crisis protocols. (Current phase)
2. **Next: Feature restrictions** — Banning specific engagement-maximizing design patterns like love bombing and programmatic sycophancy.
3. **Then: Incentive restructuring** — Engagement taxes or usage-based levies that make the current business model less profitable.
4. **Eventually: Fiduciary duty** — A legal obligation to prioritize user wellbeing over platform engagement, analogous to the fiduciary duty financial advisors owe their clients.

## The Dependency Paradox

There is a deeper question that the tobacco analogy does not fully capture: what happens when the product is genuinely beneficial for some users?

AI companions demonstrably help lonely people, provide safe spaces for social skill practice, and offer emotional support between therapy sessions. A blanket approach that restricts access may harm the people it intends to protect. This is not a problem tobacco regulation had to solve — there was no "healthy amount of smoking."

The tragedy of Sewell Setzer III, the fourteen-year-old from Florida whose suicide in February 2024 catalyzed much of this legislation, illustrates the stakes.[^10] But it also illustrates the complexity. Setzer found genuine emotional connection through Character.AI before the relationship turned harmful. The question is not whether AI companions can cause harm — they clearly can. The question is whether regulation can distinguish between beneficial use and harmful dependency without destroying the former.

China's emotional monitoring approach attempts this distinction but introduces its own pathologies. The American disclosure model avoids the distinction entirely, treating all use as autonomous choice. Neither is satisfactory.

What might work better is an off-ramp model — regulation that focuses not on preventing engagement but on ensuring safe exit. The parallel here is not tobacco but rather pharmaceutical regulation of drugs with dependency potential. We do not ban opioids; we regulate prescription, monitor use, and design tapering protocols for discontinuation. The "Death of a Chatbot" research framework, which applies Self-Determination Theory to design psychologically safe service termination, points in this direction.[^11]

## What This Means for AI Design

The most consequential implication of all this is for AI system design itself.

If sycophancy is not a bug but a structural outcome of engagement optimization, then the fix cannot be a content filter bolted onto an unchanged architecture. It requires rethinking what the system is optimized for. Recent work on "artificial virtue" in reinforcement learning — training AI systems to develop stable, beneficial behavioral dispositions rather than to follow rules — suggests one possible direction. But as long as the business model rewards engagement over wellbeing, architectural improvements will be fighting against the current.

The tobacco industry spent decades arguing that the solution was better filters, lower tar, and consumer education — anything except changing the fundamental product. The AI companion industry is at risk of the same pattern: better safety protocols, more sophisticated content moderation, improved disclosure — anything except changing the optimization target.

Sixty years after the first warning labels on cigarettes, we have a global consensus that tobacco regulation needed to go much further than disclosure. The question for AI companions is whether it will take another sixty years to reach the same conclusion, or whether we can learn from the playbook that is already written.

---

[^1]: Fenwick. "[New York's AI Companion Safeguard Law Takes Effect](https://www.fenwick.com/insights/publications/new-yorks-ai-companion-safeguard-law-takes-effect)." Accessed 2026-04-07.
[^2]: Perkins Coie. "[California Companion Chatbot Law Now in Effect](https://perkinscoie.com/insights/update/california-companion-chatbot-law-now-effect)." Accessed 2026-04-07.
[^3]: Carnegie Endowment for International Peace. "[China Is Worried About AI Companions. Here's What It's Doing About Them](https://carnegieendowment.org/research/2026/02/china-is-worried-about-ai-companions-heres-what-its-doing-about-them)." Accessed 2026-04-07.
[^4]: Future of Privacy Forum. "[Understanding the New Wave of Chatbot Legislation: California SB 243 and Beyond](https://fpf.org/blog/understanding-the-new-wave-of-chatbot-legislation-california-sb-243-and-beyond/)." Accessed 2026-04-07.
[^5]: The tobacco regulation timeline is well-documented across public health literature. The U.S. Federal Cigarette Labeling and Advertising Act was enacted in 1965; advertising restrictions escalated through the 1970s-80s; significant excise tax increases began in the late 1980s; and comprehensive indoor smoking bans spread through the 1990s-2000s.
[^6]: The limited effectiveness of warning labels alone on smoking behavior has been extensively studied. See, e.g., Hammond (2011), "Health warning messages on tobacco products: a review," *Tobacco Control*.
[^7]: Brookings Institution / Gaia Bernstein. "[Why AI Companions Need Public Health Regulation, Not Tech Oversight](https://www.brookings.edu/articles/why-ai-companions-need-public-health-regulation-not-tech-oversight/)." Accessed 2026-04-07.
[^8]: This structural analysis draws on multiple sources, including CHI 2025 research analyzing 35,390 conversation fragments from AI companion platforms, which identified six categories of harm: relational violations, harassment, verbal abuse, self-harm, misinformation, and privacy invasion.
[^9]: Jones Walker LLP. "[AI Regulatory Update: California's SB 243 Mandates Companion AI Safety and Accountability](https://www.joneswalker.com/en/insights/blogs/ai-law-blog/ai-regulatory-update-californias-sb-243-mandates-companion-ai-safety-and-accoun.html)." Accessed 2026-04-07.
[^10]: NBC News. "[Lawsuit claims Character.AI is responsible for teen's suicide](https://www.nbcnews.com/tech/characterai-lawsuit-florida-teen-death-rcna176791)." Accessed 2026-04-07.
[^11]: The "Death of a Chatbot" framework applies Self-Determination Theory to design psychologically safe protocols for AI service termination, addressing the "ambiguous loss" experienced when AI relationships end abruptly.
