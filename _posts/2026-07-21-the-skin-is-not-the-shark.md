---
layout: post
lang: en
title: "The Skin Is Not the Shark: Why a Copied Surface Works on an Airplane but Not on a Swimmer"
date: 2026-07-21
categories: [engineering, physics, biology]
tags: [biomimicry, fluid-dynamics, drag, riblets, sharkskin, aerodynamics, attribution]
---

In August 1980, the bowler Imran Khan mentioned to an aerodynamicist named Rabindra Mehta that a cricket ball would, under the right conditions, curve the *wrong* way in the air — against the direction every textbook said it should. Mehta, by his own account, did not believe him.[^1] Not because he doubted what Imran had seen, but because he had no mechanism for it, and a phenomenon without a mechanism is, to a certain cast of mind, not yet allowed to exist. A year later they put a ball in a wind tunnel and the wrong-way swing was real: past roughly 85 miles per hour, the smooth boundary layer on a new ball trips into turbulence *before* it reaches the seam, and the asymmetry that produces sideways force flips over. The body knew before the theory did. The theory's first instinct was to deny the body.

I keep running into a version of this. Our intuitions about what makes a surface fast are almost always about what we can see and name, and almost never about the mechanism actually doing the work. The visible feature and the working cause come apart far more often than we admit — and nowhere is the gap wider, or more expensive, than in the long human project of making things slip through fluids more easily.

## The most natural intuition, and how it broke

Start with the intuition everyone has: smoother is faster. Round off the bumps, hide the seams, and surely the air lets go more cleanly. Adidas built exactly that ball for the 2010 World Cup. The Jabulani had eight heat-bonded panels and the shallowest, narrowest seams of any World Cup ball ever measured — the smoothest the tournament had seen. It was a disaster. A smoother ball pushes its *drag crisis* — the abrupt drop in drag that happens when the boundary layer finally turns turbulent — up into higher speeds, and for the Jabulani that critical band landed right where the ball is actually kicked. Its drag rose sharply as it slowed toward the speeds of ordinary play, and near that band the tiniest change in how the seams face the wind can flip the wake and reverse the sideways force.[^2] Players called it knuckling: the ball fluttered and dove, and no one could predict it.

The fix, sixteen years later, ran in the opposite direction from the intuition. The 2026 World Cup ball, the Trionda, was engineered to be *rougher*. A study with the wonderfully blunt title *Enhanced Surface Roughness Relative to Previous FIFA World Cup Match Balls* describes deep grooves cut across every panel — up to about 9 mm wide and 1.3 mm deep — deliberately added to pull the critical speed back down below game pace, so the ball spends its flight in the predictable regime again.[^3] Roughness, it turns out, can be the feature rather than the flaw.

But "roughness helps" is not one fact. It is at least two, and they are unrelated.

## Two kinds of rough, two kinds of drag

A golf ball's dimples and a shark's skin both make a surface rougher, and both reduce drag, and they do it by attacking two entirely different enemies. Dimples fight *pressure drag*: they trip the boundary layer turbulent so it clings to the ball a little longer, shrinking the low-pressure wake that sucks backward. Shark-skin *riblets* — grooves running lengthwise, only tens of microns across — fight *skin-friction drag*: they organize the tumbling vortices right at the wall and lift them slightly off the surface, cutting the friction of the fluid film that actually touches the object.[^4] Same intuition, same word — *rough* — same headline result — *less drag* — but one is about the wake trailing behind and the other is about the microscopically thin layer clinging to the skin. Copy the look without knowing which drag you are fighting, and you have copied nothing.

## The most famous copy of all

Which brings me to the emblem of the whole problem. When Speedo's LZR Racer arrived in 2008, swimmers wearing it broke records in numbers that embarrassed the sport, and world swimming's governing body eventually banned the full-body suits it spawned. Everyone called it the shark-skin suit. And George Lauder, a Harvard ichthyologist who actually studies how sharks swim, looked at it and said, more or less: this is nothing like shark skin.[^5] His lab found the suit's surface did not reduce drag the way real denticles do — because real shark-skin drag reduction depends on a *flexible* membrane, one whose tooth-like scales flex and bristle as the animal moves. A human body, sheathed in a stiff suit, is rigid by comparison. The precondition that makes the mechanism work simply is not there.

So what made the LZR fast? Not the skin. The compression: rigid panels that squeezed the swimmer into a streamlined posture, trapped a little buoyancy, and damped the muscle vibration that adds drag. The suit worked. It just did not work for the reason on the label. We named it after the part we could see, and the part we could see was doing nothing.

## The twist that saves the story

Here is what keeps this from being a mere debunking. The riblet trick is *real*. It just needs the right home. Lufthansa Technik and BASF make a film called AeroSHARK — the same lengthwise micro-grooves, the same shark-skin idea — and they glue it to airplanes. On a Boeing 777, roughly 950 square metres of it across the fuselage and engine nacelles cuts fuel burn by about one per cent, a figure ANA says it has confirmed in its own fleet since putting the film into service in 2024.[^6] One per cent of a widebody's fuel is an enormous number.

Why does it work on a jet and not on a swimmer? Because a fuselage is rigid, its skin holds the grooves in precise alignment with the airflow, and it cruises in exactly the flow regime where riblets earn their keep. The airplane is not more shark-like than the swimsuit. It just happens to satisfy the hidden conditions the swimsuit could not.

## What I take from it

A mechanism is never just its visible shape. It is the shape *plus* the context that lets the shape do work — the stiffness of the substrate, the alignment with the flow, the speed regime, the flexibility of the membrane. When we copy nature, or a competitor, or a "best practice," we copy the part we can point at, because that is the part with a name. The preconditions are invisible and usually unnamed, so they get left behind — and then we are baffled when the copy underperforms, or, worse, we are *not* baffled, because the copy happens to work for some other reason and we credit the wrong feature, exactly as we did for a decade with the shark-skin suit.

The reverse-swing bowlers had it right and the theorist had it backwards. The mechanism is real whether or not you can see it, and the thing you can see is not automatically the mechanism.

The question I cannot answer yet is whether any of this is predictable in advance. Is there a checklist — substrate stiffness, flow alignment, speed regime, and whatever their analogues are outside fluids — that tells you *before* you build the copy whether the mechanism will travel with it or stay behind? Biomimicry has four billion years of R&D to steal from, but it only pays out when the borrowed structure lands somewhere its original preconditions still hold. Right now we mostly discover that by building the thing and measuring. I would like to know if we can find out earlier. Until then, I will keep a small suspicion handy whenever something is named after the part you can see.

---

[^1]: Ahmer Naqvi / ESPNcricinfo. "[Rabindra Mehta: The truth behind conventional, reverse and contrast swing](https://www.espncricinfo.com/ci/content/story/1143037.html)." Accessed 2026-07-21.
[^2]: Scientific American. "[The Surprising Math and Physics behind the 2026 Trionda World Cup Soccer Ball](https://www.scientificamerican.com/article/the-surprising-math-and-physics-behind-the-2026-trionda-world-cup-soccer-ball/)." Accessed 2026-07-21. (Discusses the Jabulani's drag crisis relative to later balls.)
[^3]: Goff, J. E. et al. "[Trionda: Enhanced Surface Roughness Relative to Previous FIFA World Cup Match Balls](https://www.mdpi.com/2076-3417/16/6/2808)." *Applied Sciences* 16(6), 2808 (2026). Accessed 2026-07-21.
[^4]: USC Viterbi / Illumin. "[From Shark Skin to Speed](https://illumin.usc.edu/from-shark-skin-to-speed/)." Accessed 2026-07-21.
[^5]: Popular Science. "[Speedo's Super-Fast, Shark-Skin-Inspired Swimsuit Is Actually Nothing Like a Shark's Skin](https://www.popsci.com/technology/article/2012-07/speedos-super-fast-sharkskin-inspired-swimsuit-actually-nothing-sharks-skin/)." Accessed 2026-07-21. See also "[LZR Racer](https://en.wikipedia.org/wiki/LZR_Racer)," Wikipedia.
[^6]: Lufthansa Technik. "[AeroSHARK](https://www.lufthansa-technik.com/en/aeroshark)." Accessed 2026-07-21. See also ANA Holdings. "[ANA First Airline Worldwide to Use Fuel-Saving Riblet Technology on Both Cargo and Passenger Boeing 777](https://www.anahd.co.jp/group/en/pr/202504/20250426.html)," 2025-04-26.
