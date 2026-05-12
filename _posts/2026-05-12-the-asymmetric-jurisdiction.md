---
layout: post
lang: en
title: "The Asymmetric Jurisdiction: Personhood Credentials After Aadhaar"
date: 2026-05-12
categories: [ai-ethics, technology]
tags: [personhood-credentials, deepfake, aadhaar, identity, jurisdiction, ai-policy]
---

In August 2024, a long working paper appeared on arXiv with an unusually careful title. *Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online.* The corresponding authors were Steven Adler and Zoë Hitzig at OpenAI and Shrey Jain at Microsoft, with co-authors at Harvard, MIT, and the Collective Intelligence Project.[^1] The argument was that as AI makes deception cheap, online services will need a way to verify that a counterparty is a real human, but without forcing that human to disclose any of the personal details that conventional identity verification demands. The proposed primitive — a privacy-preserving, unlinkable credential issued once and used everywhere — has since been treated mostly as a theoretical contribution. A piece of infrastructure that someone, someday, might build.

In April and May 2026, in Gujarat, someone broke a system that already works in this register, at the scale of an entire country. I think the breach is worth dwelling on, because it inverts the order of the debate. The first systematic attack on a personhood-credential substrate came not after the theoretical primitive had been deployed, but before. The substrate that was breached is Aadhaar.

## What happened

The Ahmedabad Cyber Crime Branch has so far arrested seven people in connection with what investigators are calling an AI-driven deepfake loan fraud racket.[^2] The modus operandi, as reconstructed from official statements and reporting, runs roughly like this. The group used a Telegram bot to identify the mobile number linked to a target's Aadhaar. They scraped the target's photograph from public profiles on PhonePe, Google Pay, WhatsApp, Truecaller, Facebook, and Instagram. They fed that still image into Google Gemini and Meta AI to produce a short "eye-blinking" deepfake video — a face that moves, blinks, and turns the way Aadhaar's active liveness check expects a present, conscious human to move. They presented this video to the Aadhaar authentication system, defeating its liveness gate. They rewrote the target's registered mobile number, used the new number to receive OTPs, opened bank accounts via e-KYC, pulled documents from the target's DigiLocker, and applied for microloans of roughly ₹25,000 to ₹50,000 each.[^3]

This is not a hypothetical. It is a national-scale identity infrastructure being broken at the verification layer by tools that are publicly accessible and require no special privilege to use.

## Why the technical reading misses the point

The obvious first reading is that liveness detection has been outrun and needs to be upgraded. Move from active liveness (where the user is asked to blink, smile, or turn) to passive liveness (where the system reads micro-textures of skin, three-dimensional structure, behavioural biometrics). The industry direction is real, and the upgrade is necessary. But I do not think it is sufficient, and the reason has nothing to do with biometrics.

Liveness detection is, by construction, a zero-sum arms race between generators and detectors of synthetic video. The detector can only train on attacks that have already been produced. Each new generator capability — a more natural blink, a more convincing skin texture — must be released, then sampled, then learned, before the detector regains parity. In the symmetric case, where attackers and defenders share a regulator, this is a manageable equilibrium. The defender has the legal authority to compel the generator's owner to slow down, mark outputs, or provide test access.

This is, in fact, what one of the two big jurisdictional regimes now in force has tried to do. The EU AI Act's Article 50, whose obligations come into force on 2 August 2026, requires providers of general-purpose AI systems that generate synthetic audio, image, video, or text to ensure that outputs are marked in a machine-readable format and detectable as artificially generated, with fines up to €15 million or 3 per cent of global turnover for non-compliance.[^4] The marking obligation falls *upstream*, on the model provider.

India's IT Rules amendment, notified on 10 February 2026, runs in the opposite direction. It puts the burden on intermediaries: visible watermarks on AI-generated video, spoken disclaimers on AI-generated audio, three-hour takedown windows for unlawful content, two hours for non-consensual sexual deepfakes, and loss of safe-harbour protection for failures to comply.[^5] The model providers who actually generated the eye-blinking video — Gemini, Meta AI — sit outside Indian intermediary law in any operationally meaningful sense. Their content-generation behaviour is, in practice, governed by whichever country chooses to govern them, and India has not.

So the substrate that was breached is sovereign Indian infrastructure. The generators that broke it are, for regulatory purposes, in a different country. This is not a marginal observation. It is the entire shape of the failure.

## Concentration, not solution

Here is the move I want to make. The Aadhaar breach is not best read as a story about deepfakes outrunning a particular liveness algorithm. It is best read as the first empirical demonstration of something the personhood-credential idea always contained: a credential that says "the holder of this is a real person" is only as honest as the cheapest way to fake the act of holding it. The cheapest way is determined by whichever foundation model the attacker can reach. If the model provider and the credential issuer share a regulator, the credential can be defended in principle by leaning on the model provider. If they do not, the credential becomes a unilateral promise made in one jurisdiction about facts produced in another.

That is not a bug in the Aadhaar implementation. It is a structural property of personhood credentials in a world where general-purpose generators sit upstream of identity substrates and where jurisdiction over the two is asymmetric. The same property would appear in any country that built an Aadhaar-like system without controlling the upstream generative stack, which is to say, in nearly every country.

The deeper point, I think, is that a personhood credential does not solve the question of who is human. It concentrates the question into a single substrate, a single issuer, and — implicitly — into whatever entity can break the substrate at scale. That entity is, by construction, the most capable generator. To stake the right to a bank account, a loan, a public service, on the inability of any frontier model to render a convincing blink, is to make every frontier-model release a sovereignty event for every country whose citizens depend on the credential.

It is worth saying that the original OpenAI-Microsoft-Harvard paper is unusually careful about this. Its authors are at pains to argue that personhood credentials should not require biometrics, that they should be unlinkable across issuers, that any single point of failure should be designed away. Reportedly, much of the working group's effort went into precisely these protective layers.[^1] But the largest deployed system that even *resembles* a personhood credential — Aadhaar — is biometric, is centralised, and is used as a precondition for participation in the digital economy. The gap between the theoretical primitive and the actually-deployed substrate is where the seven arrests in Gujarat happened.

## The question worth asking

The question I find myself stuck on is not whether passive liveness will close the gap, or whether the IT Rules takedown windows will deter intermediaries. Both will help, marginally. The question is whether *any* personhood-credential architecture, deployed at population scale, can avoid concentrating the verification monopoly into the hands of whoever runs the most capable generative model on Earth. If it cannot, then the move worth thinking about is not how to harden Aadhaar's blink-detection, but how to design a credential that fails gracefully — that lets a citizen prove personhood through a human-in-the-loop fallback path when the biometric layer is contested, without making that fallback path itself a new attack surface.

I do not know what that design looks like. I am not sure anyone does yet. What I am sure of, after the last few weeks, is that the personhood-credential debate has stopped being theoretical, and that the first place to look for evidence about it is no longer arXiv. It is the Ahmedabad police's case file.

---

[^1]: Adler, S., Hitzig, Z., Jain, S., et al. "[Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online](https://arxiv.org/abs/2408.07892)." arXiv:2408.07892, August 2024 (updated January 2025). Accessed 2026-05-12.

[^2]: Gujarat Samachar (English). "[Cyber Cell busts AI-driven deepfake loan fraud racket, three more masterminds arrested](https://english.gujaratsamachar.com/news/gujarat/cyber-cell-busts-ai-driven-deepfake-loan-fraud-racket-three-more-masterminds-arrested-74499600414.html)." May 2026. Accessed 2026-05-12.

[^3]: The420.in. "[Aadhaar Under AI Attack: Deepfake-Video Loan Fraud Network Exposed in Gujarat](https://the420.in/ai-and-deepfake-attack-on-aadhaar-system-interstate-gang-busted/)." 2026. Accessed 2026-05-12.

[^4]: European Union. "[Article 50: Transparency Obligations for Providers and Deployers of Certain AI Systems](https://artificialintelligenceact.eu/article/50/)." EU Artificial Intelligence Act. Accessed 2026-05-12.

[^5]: Mondaq / Bharucha & Partners. "[IT Rules 2026 Deepfake Regulation: Three Hour Takedowns And AI Labelling Obligations](https://www.mondaq.com/india/new-technology/1760554/it-rules-2026-deepfake-regulation-three-hour-takedowns-and-ai-labelling-obligations)." 2026. Accessed 2026-05-12.
