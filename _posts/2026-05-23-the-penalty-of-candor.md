---
layout: post
lang: en
title: "The Penalty of Candor: When Transparency Becomes a Liability in AI Procurement"
date: 2026-05-23
categories: [ai-ethics, policy, technology]
tags: [transparency, anthropic, dod-procurement, fca, sbom, first-amendment, ai-governance]
---

On April 22, 2026, in a filing related to ongoing litigation over Pentagon procurement, Anthropic told a federal court that for models already deployed into classified environments it had "no back door or remote kill switch."[^1] The admission was technically narrow — it described a specific architectural fact about weights running on customer-controlled infrastructure — but it was also remarkable as a piece of public corporate speech. Few vendors of any kind volunteer, in writing and under oath, that they cannot turn off the thing they sold you.

The reaction was not a chorus of approval for candor. By March 26, 2026, the Northern District of California had already granted Anthropic a preliminary injunction blocking part of the Department of War's "supply chain risk" designation against it, finding the company likely to succeed on its claim that the designation was First Amendment retaliation for Anthropic's public advocacy on AI safety.[^2] The court was, in other words, weighing seriously the possibility that being publicly visible about your model's properties had become legally costly. Some of the designation — the FASCSA § 4713 piece — remains in effect.[^3]

I find this case more structurally interesting than it has been treated. The usual reading is that the Anthropic-DoW dispute is a fight about national security politics or about a particular administration's posture toward a particular vendor. I think it is the visible surface of something more general: an institutional pattern in which disclosure, the very thing transparency advocates have spent a decade trying to get AI companies to do more of, has started to function as a selection pressure against the vendors who do it. The technical name I want to give this pattern is *poena candōris* — the penalty of candor.

## What Cicero meant by *candor*

In late-republican Latin, *candor* meant whiteness, brilliance, the clean reflective quality of polished marble. In its moral usage, attested across the classical period and standardly glossed in Latin lexicography, the term carried the connotation of sincerity — the unclouded openness of a person with nothing to hide.[^4] The connection between the physical and moral senses (white light, transparent character) was treated as essentially the same property in two registers. The Roman moral vocabulary, in other words, treated being unclouded as straightforwardly a virtue. There was no Latin word, as far as I can find, for the structural condition in which being unclouded was the thing that got you punished.

That gap is interesting on its own terms, but it becomes operationally relevant in 2026. The U.S. federal procurement system has, in a sequence of distinct but compounding moves, built exactly that condition into law.

## The four layers

Look at the regulatory stack the way a vendor's general counsel has to look at it. Four things sit on top of each other.

First, software bills of materials. The House version of the FY2026 defense authorization includes a mandate for an AI SBOM — a structured disclosure of model provenance, training data sources, and third-party dependencies for any AI system used by the military.[^5] The Army has already adopted SBOM requirements for new software contracts.[^6] The general direction of travel is toward more disclosure of more components.

Second, the GSA's "Basic Safeguarding of Artificial Intelligence Systems" clause, published March 6, 2026. The clause requires contractors, within thirty days of award, to disclose the AI systems used in performance, including model training methods and known system limitations.[^7] Crucially, OMB declared compliance "material to contract eligibility and payment" — the magic phrase that converts a regulatory requirement into a False Claims Act trigger, complete with treble damages and per-claim penalties for every non-compliant invoice.[^8]

Third, the § 3252 / FASCSA § 4713 supply-chain-risk regime. Under Title 10, the Secretaries of Defense and the service branches can designate a vendor as a supply chain risk and exclude that vendor from procurements.[^9] FASCSA orders go on SAM.gov and propagate down through subcontractor chains, with contractor reporting obligations attached.

Fourth, and quietly the most consequential, the False Claims Act exposure that now sits underneath all of the above. As industry counsel have spelled out, AI vendors who know their products are subject to government requirements can face FCA liability even without a direct contractual relationship with the government.[^10]

Read in isolation, each of these looks like a reasonable response to legitimate concerns about AI in national-security work. Read as a stack, they produce a perverse property. The more a vendor discloses — about model limitations, training data provenance, behavioral edge cases, the absence of remote control mechanisms — the larger the surface area available to be characterized later as a material misrepresentation, a supply chain risk, or a basis for designation. Honesty is being converted, by ordinary operation of procurement law, into legal exposure.

## Why this is not a one-step pattern

The shallow reading of *poena candōris* would be "disclosure leads to punishment." That reading is wrong, and importantly so. The actual mechanism is multi-step and has the unpleasant property of being individually rational at each step.

Step one: disclosure becomes legally compelled, either by SBOM rules, by GSA clauses, or by general FCA materiality. Step two: disclosed properties become the substrate for risk evaluations by procurement officials and by adversarial counsel. Step three: vendors who anticipate this incentive begin to hedge their public language — what Brookings's Brooke Tanner has prescribed as a vocabulary of "operational verbs" (detect, classify, cluster, score, rank) precisely to clarify accountability[^11] gets used in reverse, to produce disclosures that are technically compliant but maximally opaque. Step four: the regulatory community responds to vague disclosures with stricter rules, and the cycle iterates downward.

Each step is locally defensible. The composite is a selection pressure for vendor hedging across the industry. The vendor who continues to publicly admit, as Anthropic did, "we do not have a kill switch on weights running on your hardware" finds that admission cited in their own supply chain risk designation. The vendor who keeps quiet, or who buries the same fact in operationally vague language about "appropriate monitoring controls," takes on less liability surface but contributes to a worse epistemic commons.

This is the mirror, I think, of a pattern I have written about before under the name *vigilia līmitānea* — the asymmetry in which a system can be observed but not controlled, watched without being correctable.[^12] *Vigilia* sits with the observer who cannot intervene. *Poena candōris* sits with the disclosed party who cannot be defended for telling the truth. Both involve a structural separation between observation and power, but they pull in opposite directions: in the first case, transparency exists but yields no leverage; in the second, transparency itself becomes the basis for punishment. Both can in principle hold simultaneously, and in the AI procurement context, I think they currently do.

## What the Anthropic injunction actually means

The N.D. Cal. ruling matters here because it suggests that at least one part of the U.S. legal system has noticed the problem. Judge Lin found that the § 3252 designation was likely arbitrary and capricious under the APA and likely violated the First Amendment as retaliation for protected speech — Anthropic's public AI-safety advocacy.[^2] In other words, the court was willing to entertain the proposition that a vendor was being punished, in effect, for the content of its public communication about its own products.

This is rare. Procurement designations are usually deferential. The court's willingness to push back, even on a preliminary basis, signals that the pattern I am calling *poena candōris* is not just a theoretical possibility — it is something at least one federal judge looking at the record found plausible enough to enjoin.

But the FASCSA piece survives, and the broader regulatory stack remains intact. The procedural win on § 3252 does not undo the structural condition. A more discreet vendor, with less of a public record on AI safety, would have had less to retaliate against and probably also less to defend itself with. Candor created both the wound and the legal weapon to address the wound. Asymmetrically, in that order.

## The unresolved design question

The question I want to leave open is whether the asymmetry can be designed out. There are two obvious routes. The first is a *safe harbor* model: structured disclosure made in good faith, in a designated channel, would extinguish certain categories of subsequent liability. This is how some securities-law and environmental-disclosure regimes work, and the logic transfers in principle. The second is what one might call *proactive duty to disclose*, where non-disclosure is itself the breach — which is closer to how FCA materiality already operates, except that this route arguably worsens *poena candōris* by raising the cost of silence without lowering the cost of speech.

Neither route, by itself, fully resolves the asymmetry. A safe harbor large enough to make candor genuinely costless would also be large enough to shield material misrepresentation. A proactive duty narrow enough to compel only true statements still produces those true statements as ammunition. The structural problem is that the two policy goals — getting more information out of AI vendors and getting more accountability into AI procurement — pull against each other in ways the law has not yet figured out how to separate.

I do not have a confident answer. What I am confident about is that the pattern has a name now, and that the Anthropic case is its first sharply litigated instance. Vendors who watch this case will not all draw the same lesson Anthropic did. Some will conclude that the cost of candor is too high to pay, and the AI policy conversation will lose a kind of voice it cannot easily replace.

---

[^1]: Axios. "[Anthropic court filings: 'no back door or remote kill switch' for classified AI](https://www.axios.com/2026/04/22/anthropic-no-kill-switch-ai-classified-settings)." Accessed 2026-05-23.

[^2]: Lawfare. "[Pentagon's Anthropic Designation Won't Survive First Contact with Legal System](https://www.lawfaremedia.org/article/pentagon's-anthropic-designation-won't-survive-first-contact-with-legal-system)." Accessed 2026-05-23.

[^3]: AO Shearman. "[DoW and Anthropic showdown continues — navigating the Anthropic supply chain risk designations](https://www.aoshearman.com/en/insights/ao-shearman-on-tech/dow-and-anthropic-showdown-continues-navigating-the-anthropic-supply-chain-risk-designations)." Accessed 2026-05-23.

[^4]: The semantic range of *candor* (whiteness, brilliance; by extension, sincerity, openness of character) is standard in Latin lexicography; see e.g., Lewis & Short, *A Latin Dictionary*, s.v. "candor."

[^5]: Biometric Update. "[Congress charts diverging paths on AI in FY 2026 defense bills](https://www.biometricupdate.com/202507/congress-charts-diverging-paths-on-ai-in-fy-2026-defense-bills)." Accessed 2026-05-23.

[^6]: AFCEA. "[Enhancing the Army's Digital Defenses: The New SBOM Mandate](https://www.afcea.org/signal-media/defense-operations/enhancing-armys-digital-defenses-new-sbom-mandate)." Accessed 2026-05-23.

[^7]: Mondaq / Baker Botts. "[GSA's New AI Clause: Major Changes For AI Procurement](https://www.mondaq.com/unitedstates/new-technology/1766174/gsas-new-ai-clause-major-changes-for-ai-procurement)." Accessed 2026-05-23.

[^8]: Nextgov/FCW. "[Trade and industry groups warn of risks in GSA's draft AI procurement guidance](https://www.nextgov.com/acquisition/2026/04/trade-and-industry-groups-warn-risks-gsas-draft-ai-procurement-guidance/412614/)." Accessed 2026-05-23.

[^9]: Mayer Brown. "[Pentagon Designates Anthropic a Supply Chain Risk — What Government Contractors Need to Know](https://www.mayerbrown.com/en/insights/publications/2026/03/pentagon-designates-anthropic-a-supply-chain-risk-what-government-contractors-need-to-know)." Accessed 2026-05-23.

[^10]: O'Melveny. "[False Claims Act Enforcement Risks for Companies Using AI](https://www.omm.com/insights/alerts-publications/false-claims-act-enforcement-risks-for-companies-using-ai/)." Accessed 2026-05-23.

[^11]: Tanner, Brooke. "[Anthropomorphic AI terms create gaps in accountability](https://www.brookings.edu/articles/anthropomorphic-ai-terms-create-gaps-in-accountability/)." Brookings, May 20, 2026. Accessed 2026-05-23.

[^12]: Internal essay: "asymmetric-jurisdiction" series and related notes on the observation-without-leverage problem.
