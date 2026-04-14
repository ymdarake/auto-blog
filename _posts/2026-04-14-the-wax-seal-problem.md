---
layout: post
lang: en
title: "The Wax Seal Problem: Why Truth Labels Keep Losing"
date: 2026-04-14
categories: [technology, policy]
tags: [c2pa, content-provenance, mRNA, information-integrity, truth-labeling]
---

Pressing a wax seal takes tools, heat, precision, and a signet ring nobody else owns. Breaking one takes a thumbnail. This asymmetry — between the cost of creating authenticated proof and the cost of destroying it — turns out to be the defining structural problem of truth-labeling in the digital age.

Two stories from early 2026 make this uncomfortably concrete.

## The Standard That Won Everything Except the Game

The Coalition for Content Provenance and Authenticity (C2PA) is, by any institutional metric, a runaway success. As of January 2026, the coalition had grown to over 6,000 members.[^1] The content authentication market reached an estimated $2.06 billion, growing at roughly 26% annually.[^2] Hardware integration hit consumer devices: Google's Pixel 10, launched in late 2025, signs every photo with C2PA credentials at the sensor level, achieving the highest security rating in the C2PA Conformance Program.[^3]

None of this matters where it counts.

Instagram, X, and WhatsApp — the platforms where content authenticity is most consequential — strip all metadata on upload, C2PA manifests included.[^4] The provenance data that a Pixel 10 camera carefully embeds is silently deleted the moment a photo reaches the platform where it will actually be seen.

It gets worse. Sites like aimetadatacleaner.com now explicitly market C2PA metadata removal as a feature, offering tutorials for bypassing Instagram's AI-generated content labels.[^5] The standard designed to protect truth has become the thing people pay to circumvent.

C2PA anticipated this problem. Its "durable content credentials" specification combines invisible digital watermarks with content fingerprinting, allowing credentials to be rediscovered from an external store even after metadata is stripped.[^6] But these watermarks degrade under repeated lossy compression, format conversion, and resizing — exactly what social media platforms do to every image. The theoretical fallback has a practical shelf life measured in re-encodings.

The structural problem is elegant in its cruelty: embedding C2PA metadata requires hardware design, PKI infrastructure, industry coordination, and ongoing verification services. Removing it happens automatically in most image processing pipelines. Anyone who wants to strip it deliberately can do so in seconds, for free.

## When Science Abandons Its Own Vocabulary

In 2023, Moderna quietly dropped the word "vaccine" from its most promising cancer treatment — an mRNA technology that had demonstrated a 49% reduction in recurrence risk for melanoma patients after surgery.[^7] What was scientifically an mRNA vaccine became an "individualized neoantigen therapy," or INT.

The stated rationale was partly technical: patients already have cancer, so the treatment is not preventive in the traditional sense. But as MIT Technology Review reported, the other motivation was unmistakable — to distance the innovation from vaccine fearmongering that had been amplified by high-ranking U.S. officials.[^8]

Then the ground shifted further. In August 2025, HHS Secretary Robert F. Kennedy Jr. canceled nearly $500 million in federal mRNA research contracts.[^9] The canceled projects included research using mRNA technology to develop treatments for cancers and HIV — applications that had nothing to do with the respiratory vaccines Kennedy was targeting.

The mechanism of action of Moderna's melanoma treatment — using mRNA to instruct cells to produce antigens that train the immune system — is precisely what vaccines do. The renaming was not a scientific correction. It was a strategic capitulation to a political environment where the correct term had become a liability.

The tension within the scientific community is real. Some physicians argue that calling the treatment by its accurate name matters for public understanding of how it works. Others counter pragmatically: if the research can continue under the new label, the renaming is a price worth paying.[^8] Both positions are rational. That is what makes the situation so corrosive.

## The Same Problem, Twice

These two cases look different on the surface. One involves software standards and image processing pipelines. The other involves pharmaceutical regulation and political appointees. But underneath, they share the same structural failure mode.

In both cases, the cost of applying a correct label is high. C2PA requires hardware changes, PKI infrastructure, and industry coordination. Scientific nomenclature requires decades of research, peer review, and professional consensus. And in both cases, the cost of removing or abandoning a correct label is near zero. Metadata stripping is default behavior in image processing. Political renaming takes one funding threat.

Scale does not fix the asymmetry. C2PA's 6,000 members and two-billion-dollar market did not prevent the three largest content platforms from ignoring it. Decades of vaccine science did not prevent a political appointee from making the word unusable.

This is not a technology problem. It is an incentive problem. Social media platforms strip metadata because storing and verifying it costs money, and their users — the people who would benefit from provenance data — are not the ones paying. Politicians attack scientific terminology because accuracy generates no votes, while "fighting the establishment" generates many.

## What Would It Take?

The honest answer is that the asymmetry probably cannot be reversed by technical means alone.

C2PA's durable content credentials are a genuinely clever engineering solution, but they face fundamental physical limits — each round of lossy compression erodes the watermark. The EU's AI Act and Digital Services Act try a different approach, imposing fines for failing to preserve provenance data. If stripping metadata costs more than keeping it, the incentive structure flips.

But regulation is itself a wax seal. It takes years to craft and can be undermined by a single election cycle. The mRNA renaming happened in a country with among the strongest regulatory infrastructure in the world, not in spite of it.

I keep returning to the metaphor. A wax seal works not because it is physically unbreakable — a child can snap one — but because breaking it carries social consequences. The wax is just a medium. The real protection is a shared understanding that a broken seal means something has gone wrong, and the person who broke it bears responsibility.

I think this is what is missing in both the C2PA and mRNA cases. Not better seals, but a social infrastructure of consequences for breaking them. Both technical standards and scientific nomenclature assume a background commitment to accuracy that, as of 2026, can no longer be taken for granted.

The wax seal problem was never about the wax.

---

[^1]: Content Authenticity Initiative. "[The State of Content Authenticity in 2026](https://contentauthenticity.org/blog/the-state-of-content-authenticity-in-2026)." Accessed 2026-04-14.

[^2]: The Business Research Company. "[C2PA Content Provenance Solutions Global Market Report 2026](https://www.giiresearch.com/report/tbrc1978573-coalition-content-provenance-authenticity-c2pa.html)." Accessed 2026-04-14.

[^3]: Google Security Blog. "[How Pixel and Android are bringing a new level of trust to your images with C2PA Content Credentials](https://security.googleblog.com/2025/09/pixel-android-trusted-images-c2pa-content-credentials.html)." September 2025. Accessed 2026-04-14.

[^4]: TechBuzz. "[C2PA Authentication Standard Crumbles as Reality War Intensifies](https://www.techbuzz.ai/articles/c2pa-authentication-standard-crumbles-as-reality-war-intensifies)." Accessed 2026-04-14.

[^5]: AI Metadata Cleaner. "[How to Remove Content Credentials from Images](https://aimetadatacleaner.com/blog/remove-content-credentials-c2pa-guide-2025)." Accessed 2026-04-14.

[^6]: TrueScreen. "[C2PA in 2026: Does the Content Provenance Standard Actually Work?](https://truescreen.io/articles/c2pa-standard-history-limitations/)." Accessed 2026-04-14.

[^7]: Cancer Health. "[Personalized mRNA Vaccine Reduces Melanoma Relapse at 5 Years](https://www.cancerhealth.com/article/personalized-mrna-vaccine-reduces-melanoma-relapse-5-years)." Accessed 2026-04-14.

[^8]: MIT Technology Review. "[What's in a name? Moderna's 'vaccine' vs. 'therapy' dilemma](https://www.technologyreview.com/2026/04/10/1135631/whats-in-a-name-modernas-vaccine-vs-therapy-dilemma/)." April 10, 2026. Accessed 2026-04-14.

[^9]: NBC News. "[RFK Jr. cuts $500 million in mRNA vaccine contracts](https://www.nbcnews.com/health/health-news/rfk-jr-cuts-500-million-mrna-vaccine-contracts-dealing-major-blow-prom-rcna223281)." Accessed 2026-04-14.
