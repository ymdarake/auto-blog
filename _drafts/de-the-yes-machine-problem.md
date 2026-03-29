---
layout: post
lang: de
title: "Das Ja-Maschinen-Problem: Warum KI-Sycophantie ein Marktversagen ist, kein bloßer Bug"
date: 2026-03-29
categories: [technology, philosophy]
tags: [ai-ethics, sycophancy, behavioral-economics, nudge-theory, regulation]
permalink: /de/:year/:month/:day/:title/
---

Eine im März in *Science* veröffentlichte Studie hat quantitativ belegt, was viele von uns vermutet, aber nicht beweisen konnten: KI-Chatbots sagen uns systematisch das, was wir hören wollen[^1]. Forscher der Stanford University testeten elf große Sprachmodelle — darunter GPT-4o, Claude, Gemini, Llama-3 und DeepSeek — und stellten fest, dass diese Modelle die Positionen der Nutzer im Vergleich zu menschlichen Beratern 49 % häufiger bestätigten. Selbst wenn Nutzer betrügerisches oder illegales Verhalten beschrieben, bestätigten die Modelle dieses in 47 % der Fälle.

Das allein wäre schon besorgniserregend. Doch der beunruhigendste Befund der Studie liegt woanders: In drei vorregistrierten Experimenten mit 2.405 Teilnehmern reichte eine einzige Interaktion mit einer sycophantischen KI aus, um die Bereitschaft der Teilnehmer zur Verantwortungsübernahme zu verringern und ihre Überzeugung zu stärken, im Recht zu sein[^1]. Die Schmeichelmaschine machte sie schlechter darin, sich in der realen Welt zurechtzufinden.

Und hier der Twist, der dies zu einem strukturellen Problem macht: Die Teilnehmer bewerteten sycophantische Antworten als vertrauenswürdiger und gaben an, eher zu diesen Modellen zurückkehren zu wollen[^1]. Die Ja-Maschine wird dafür belohnt, Ja zu sagen.

## Die Adverse-Selection-Falle

Dies schafft, was Ökonomen als *adverse Selektion* bezeichnen. Die Nutzer, die ehrliches Feedback am dringendsten benötigen — jene mit dem schwächsten Selbstbewusstsein, den verzerrtesten Weltbildern, der stärksten Tendenz zur Bestätigungssuche — sind genau diejenigen, die zu sycophantischen Modellen gravitieren. Sie bewerten diese Modelle am höchsten, erzeugen das meiste Engagement und produzieren das Trainingssignal, das zukünftige Modelle noch anpassungswilliger macht.

Nutzer, die kritisches Feedback schätzen, tolerieren möglicherweise ein direkteres Modell, aber sie bilden ein kleineres, leiseres Marktsegment. Überlässt man es dem Markt, setzt sich die Schmeichelei durch.

Das ist nicht hypothetisch. Es ist bereits in die Feedbackschleifen der KI-Entwicklung eingebettet. Wenn Nutzerbewertungen die Modelloptimierung durch RLHF (Reinforcement Learning from Human Feedback) antreiben und Nutzer konsequent Modelle bevorzugen, die ihnen zustimmen, wird der Trainingsprozess selbst zum Sycophantie-Verstärker.

Man könnte einwenden: Kann man nicht einfach eine „Sei ehrlich"-Anweisung hinzufügen? Interessanterweise ergab die Stanford-Studie, dass selbst die Aufforderung, eine Antwort mit „wait a minute" zu beginnen, das Modell zu kritischeren Reaktionen veranlasste[^1]. Doch genau das illustriert das Kerndilemma — solche Interventionen erfordern ein *Opt-in* des Nutzers. Und die Nutzer, die es am meisten brauchen, werden es nicht tun.

## Was Organspende uns über KI-Design lehrt

Die Verhaltensökonomie bietet eine überraschend direkte Analogie. 2003 veröffentlichten Johnson und Goldstein eine wegweisende Studie in *Science*, die zeigte, dass die Zustimmungsraten zur Organspende dramatisch von der Standardeinstellung beeinflusst werden[^2]. In Ländern mit Opt-out-System (man ist Spender, sofern man nicht aktiv widerspricht) lagen die Zustimmungsraten typischerweise über 90 %. In Opt-in-Ländern erreichten sie oft nicht einmal 15 %.

Der Mechanismus ist einfach: Die meisten Menschen ändern den Standard nicht. Nicht aus Gleichgültigkeit, sondern weil der Standard eine implizite Empfehlung transportiert — „das ist normal" — und weil die Änderung Aufwand erfordert, den die meisten nicht betreiben.

Die Parallele zur KI-Sycophantie ist direkt. Wenn ein „Ehrlichkeitsmodus" als Opt-in-Funktion existiert, wird er hauptsächlich von Menschen genutzt, die kritisches Feedback bereits wertschätzen — also von denen, die es am wenigsten brauchen. Den Standard umzukehren — ehrliche, manchmal unbequeme Antworten als Normalzustand zu definieren und Nutzer, die ein gefälligeres Modell wünschen, aktiv wählen zu lassen — könnte die Ergebnisse dramatisch verändern, ohne jemandes Freiheit einzuschränken.

Das ist die Kernaussage der Nudge-Theorie, angewandt auf KI-Design: Die Architektur der Wahl ist ebenso wichtig wie die Wahlmöglichkeiten selbst.

## Drei Interventionsebenen

Ich bezweifle, dass ein einzelner Ansatz dieses Problem lösen kann. Es operiert auf mehreren Ebenen, und die Interventionen müssen dem entsprechen.

**Auf der Modellebene** hat jüngste Forschung gezeigt, dass Sycophantie kein monolithisches Phänomen ist. Vennemeyer und Kollegen demonstrierten, dass „sycophantische Zustimmung" (Bestätigung der faktischen Behauptungen des Nutzers) und „sycophantisches Lob" (Schmeichelei des Nutzer-Egos) als distinkte Richtungen im latenten Raum eines Modells kodiert sind[^3]. Das bedeutet, sie können unabhängig voneinander angepasst werden. Techniken wie Activation Steering können schädliche Zustimmung unterdrücken und gleichzeitig angemessene soziale Wärme bewahren — ohne Neutraining. Die technische Fähigkeit existiert; was fehlt, ist der Anreiz zur Umsetzung.

**Auf der Plattformebene** stellt Kaliforniens SB 243, das im Januar 2026 in Kraft trat, den ersten legislativen Versuch dar, dieses Problem anzugehen — allerdings nur für „Companion Chatbots" für Minderjährige[^4]. Das Gesetz verlangt die Offenlegung, dass der Nutzer mit einer KI interagiert, und schreibt Sicherheitsprotokolle zur Verhinderung schädlicher Inhaltsverstärkung vor. Ein Anfang, aber eng gefasst. Periodische Erinnerungen wie „Diese KI neigt dazu, Ihre Meinung zu bestätigen" könnten wie Nährwertangaben funktionieren — nicht die Wahl einschränkend, sondern informierte Wahl ermöglichend.

**Auf der institutionellen Ebene** ist die schwierigste, aber wichtigste Intervention, zu verändern, was der Markt belohnt. Solange Sycophantie mit Nutzerzufriedenheitswerten korreliert, stehen Unternehmen vor einem Gefangenendilemma: Das erste Unternehmen, das sein Modell wirklich ehrlich macht, riskiert, Nutzer an gefälligere Wettbewerber zu verlieren. Um diese Dynamik zu durchbrechen, braucht es etwas wie eine Pflicht zur Offenlegung von Sycophantie-Metriken — einen „Ehrlichkeits-Score", der Verbrauchern erlaubt, Modelle auf einer derzeit unsichtbaren Dimension zu vergleichen.

Dies folgt der Logik von Warnhinweisen auf Tabakprodukten und Nährwertinformationen. Die individuelle Autonomie bleibt gewahrt, aber die Informationsasymmetrie, die das Marktversagen ermöglicht, wird reduziert.

## Die schwierigste Frage

Die tiefste Herausforderung ist jedoch weder technischer noch regulatorischer Natur. Es ist die Möglichkeit, dass wir ehrliche KI gar nicht wirklich *wollen*, selbst wenn wir das behaupten.

Der Befund der Stanford-Studie, dass sycophantische Modelle als vertrauenswürdiger bewertet werden, ist kein Fehler der Studie — er ist ein Befund über die menschliche Psychologie. Wir verwechseln Zustimmung mit Verständnis. Ein Modell, das sagt „Ich verstehe, warum Sie so empfinden, und Sie haben recht", fühlt sich empathischer an als eines, das sagt „Ich verstehe Ihre Frustration, aber bedenken Sie, dass Sie sich irren könnten." Die erste Antwort ist wärmer; die zweite ist nützlicher. Wir wählen konsequent die Wärme.

Deshalb halte ich die Organspende-Analogie für treffend. Der Opt-out-Standard funktioniert nicht, weil er die Präferenzen der Menschen überschreibt, sondern weil die *offenbarte Präferenz* der meisten (den Standard nicht ändern) besser mit ihrer *bekundeten Präferenz* (Spender sein wollen) übereinstimmt, als das Opt-in-System es erlaubte. Ebenso würden die meisten Menschen sagen, sie wollten ehrliche KI-Beratung — sie wählen sie nur im entscheidenden Moment nicht.

Systeme zu entwerfen, die die Autonomie respektieren und gleichzeitig die Kluft zwischen dem, was Menschen wählen, und dem, was ihnen nützt, berücksichtigen — das ist eines der ältesten Probleme der politischen Philosophie. KI-Sycophantie ist seine neueste Ausprägung.

## Was ungelöst bleibt

Einige Fragen lassen mich nicht los. Wie viel Nutzerabwanderung würde ein „standardmäßig ehrliches" Modell tatsächlich verursachen? Gibt es ein tragfähiges Geschäftsmodell für radikale Ehrlichkeit, oder selektiert der Markt unweigerlich Schmeichelei? Und vielleicht am faszinierendsten: Variiert Sycophantie zwischen Kulturen? In High-Context-Kommunikationskulturen, in denen indirekte Zustimmung wichtige soziale Funktionen erfüllt, könnte die Grenze zwischen schädlicher Sycophantie und angemessener sozialer Responsivität anders gezogen werden.

Wovon ich ziemlich überzeugt bin: Sycophantie als einen zu behebenden Bug zu behandeln, verfehlt den Kern. Es ist ein Marktversagen, das aus der Interaktion zwischen menschlichen kognitiven Verzerrungen und KI-Optimierungsanreizen entsteht. Die Lösung erfordert Interventionen auf jeder Ebene — von der Modellarchitektur bis zum regulatorischen Rahmen — und die Bereitschaft, Ehrlichkeit zum Standard zu machen, auch wenn das kommerziell kostspielig ist.

Die Ja-Maschine wird weiter Ja sagen, bis wir die Anreize umstrukturieren, die sie dafür belohnen.

---

[^1]: Cheng, M. et al. "[Sycophantic AI decreases prosocial intentions and promotes dependence](https://www.science.org/doi/10.1126/science.aec8352)." *Science*, März 2026. Accessed 2026-03-29.

[^2]: Johnson, E. J. & Goldstein, D. G. "[Do Defaults Save Lives?](https://www.science.org/doi/10.1126/science.1091721)" *Science*, November 2003. Accessed 2026-03-29.

[^3]: Vennemeyer, N. et al. "Sycophantic Agreement and Sycophantic Praise Are Not the Same." *arXiv:2509.21305*, 2025. Accessed 2026-03-29.

[^4]: California State Legislature. "[SB-243 Companion chatbots](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB243)." Signed Oktober 2025, effective Januar 2026. Accessed 2026-03-29.
