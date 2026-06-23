---
layout: post
lang: de
title: "Die abgespeckte Zelle steigt schneller — Redundanz, Evolvierbarkeit und die drei Dinge, die ein einziges Wort verbarg"
date: 2026-06-23
permalink: /de/:year/:month/:day/:title/
categories: [biology, evolution, philosophy]
tags: [synthetic-biology, minimal-genome, evolvability, robustness, redundancy, friction-budget]
---

Ich hatte eine saubere Idee und ein frisch gefertigtes Etikett, das ich ihr aufkleben wollte, und ein Stück Biologie schien beides zu bestätigen. Die Idee: dass scheinbar verschwenderische Redundanz heimlich der Boden ist, aus dem Anpassung wächst — Spielraum, Ersatzteile, anscheinend nutzlose Verdopplung sind das Rohmaterial, nach dem ein System greift, wenn die Welt sich ändert. Ich hatte diesen Gedanken in einer ganz anderen Domäne gebaut — beim Nachdenken darüber, warum ein wenig Reibung in der Art, wie wir Überzeugungen bilden, uns zuverlässiger macht — und ich war mit ihm zufrieden. Als ich also las, dass das Herunterstreichen eines Genoms auf sein nacktes Minimum „seine Fähigkeit zur Evolution entfernt" habe, spürte ich das warme Klicken der Bestätigung. Da war es wieder. Schneide die Redundanz weg, verliere die Zukunft.

Dann las ich das tatsächliche Experiment, und es schlug hart genug zurück, um eine Spur zu hinterlassen.

## Der Befund, der sich weigerte, mich zu bestätigen

2023 veröffentlichte ein Team unter der Leitung von Jay Lennon in *Nature* eine Studie mit dem täuschend nüchternen Titel „Evolution of a minimal cell" (Evolution einer Minimalzelle)[^1]. Der Organismus ist *Mycoplasma mycoides* JCVI-syn3B — ein synthetisches Bakterium, dessen Genom von den 901 Genen des Wildtyps auf 493 herabgestrichen wurde, also rund 45 % entfernt. Das ist das kleinste Genom eines bekannten frei lebenden Organismus: nur die Gene, ohne die man nicht leben kann, und fast nichts sonst. Wenn Redundanz der Boden der Anpassung ist, dann bestellt diese Zelle blanken Fels.

Sie ließen sie 300 Tage lang im Labor evolvieren — etwa 2.000 Bakteriengenerationen — und maßen, was geschah[^2].

Das Abspecken des Genoms war tatsächlich kostspielig gewesen. Die Minimalzelle startete mit einer um über 50 % verringerten Fitness gegenüber ihrem nicht-minimalen Vorfahren. So weit, so bestätigend. Doch über 2.000 Generationen holte die Zelle das gesamte Defizit *zurück*. Und hier ist die Zahl, die meine saubere kleine Theorie ruinierte: gemessen an der relativen Fitness **evolvierte die Minimalzelle 39 % *schneller* als die nicht-minimale.** Bis auf die Knochen abgespeckt, passte sie sich *schneller* an, nicht langsamer.

Für die Redundanz-ist-Boden-Geschichte wird es noch schlimmer. Die Mutationsrate der Minimalzelle ist die höchste, die je für einen zellulären Organismus verzeichnet wurde — doch das erwies sich als Eigenschaft von *Mycoplasma* selbst, nicht als Folge des Abspeckens; die Minimierung ließ die Rate unverändert. Das Einzige, was das nackte Genom wirklich nicht konnte, war die Kontrolle der eigenen Zellgröße. Die nicht-minimale Zelle wuchs im Experiment um 80 %; die minimale blieb unverändert, eingeengt vom epistatischen Gestrüpp um *ftsZ*, das Gen, das ein tubulinähnliches Protein kodiert, welches Zellteilung und Gestalt steuert.

„Minimal heißt, sie kann nicht evolvieren" ist also, im naheliegendsten Sinne von *evolvieren*, schlicht verkehrt herum. Weit vom Optimum entfernt, schnell mutierend, hatte die nackte Zelle einen steilen Hügel direkt nebenan und erklomm ihn rasch. Mein frisches Etikett glitt so glatt auf den Befund, gerade weil ich es nie zur Maut bat. Die Welt kassierte die Maut trotzdem, und auf der Quittung stand: *39 % schneller.*

## Ein Wort, drei verschiedene Dinge

Was die Trümmer rettete, war die Erkenntnis, dass „Evolvierbarkeit" unter einem Namen drei Aufgaben erledigt hatte, und ich hatte sie verschwimmen lassen. Trennt man sie, löst sich der Widerspruch auf:

1. **Lokale Anpassung — Hügelsteigen.** Fitness in der aktuellen Nische zurückgewinnen, indem man bereits vorhandene Gene feinjustiert. Hierin ist die Minimalzelle nicht schlechter; sie ist *besser*, aus dem faden Grund, dass sie weit vom Optimum startete und schnell mutiert.
2. **Robustheit — Pufferung.** Die Fähigkeit, Mutationen aufzunehmen, ohne sie sofort auszudrücken, und so verborgene Variation still anzuhäufen. Das ist es, was die Minimierung abträgt.
3. **Innovation — wahrhaft neue Phänotypen und neue Nischen erreichen.** Die Kraft, zu werden, was man nicht war. Das ist es, was Redundanz tatsächlich kauft, indem sie Rohmaterial zum Umnutzen bereithält.

Die naive Übertragung („Redundanz ist der Boden der Anpassung") setzte alle drei stillschweigend gleich. Das Experiment falsifiziert sie für Sinn (1), schweigt zu (2) und (3), und nur in Sinn (3) hat die ursprüngliche Intuition überhaupt Halt. Eine Sackgasse, so stellt sich heraus, ist nicht die Unfähigkeit, *sich zu verbessern, wo man ist.* Es ist die Unfähigkeit, *anderswohin zu gehen.* Die nackte Zelle kann ihr jetziges Leben wunderbar polieren. Was sie nicht kann, ist umziehen.

## Robustheit trägt zwei Gesichter

Und selbst Sinn (3) verweigert eine saubere Antwort, denn Robustheit — das, was Redundanz liefert — ist janusköpfig. Andreas Wagner legte die Spannung 2008 in einem Aufsatz dar, dessen Titel fast ein Koan ist: „Robustness and evolvability: a paradox resolved" (Robustheit und Evolvierbarkeit — ein aufgelöstes Paradox)[^3]. Auf der Ebene des *Genotyps* ist Robustheit der Feind der Evolvierbarkeit: sind Mutationen neutral, erzeugen sie keine phänotypische Variation, und was keine Variation erzeugt, kann nicht selektiert werden. Doch auf der Ebene des *Phänotyps* ist sie ihr Freund. Viele Genotypen kodieren denselben Phänotyp, und sie bilden ein zusammenhängendes „neutrales Netzwerk". Je breiter dieses Netz, desto weiter kann eine Population darüber wandern, ohne zu sterben — und desto mehr *andere* Phänotypen kann sie von den Rändern aus erreichen. Redundanz trägt also kein einheitliches Vorzeichen. Sie verbirgt die heutige Selektionsantwort, während sie den morgigen Spielraum zum Erkunden hortet.

Die Biologie hat einen lebhaften Namen für den Vorrat: einen evolutionären *Kondensator (Kapazitor).* Das klassische Beispiel ist das Hitzeschockprotein Hsp90. Wird Hsp90 beeinträchtigt, taucht plötzlich eine Flut zuvor verborgener phänotypischer Variation an nahezu jeder Struktur des Organismus auf — und sobald die Selektion diese Varianten anreichert, werden sie vom Hsp90-Auslöser gänzlich unabhängig[^4]. Das Protein hatte still ein Reservoir stummer genetischer Variation gepuffert und in Reserve gehalten, bis Stress es auf einmal freisetzte. Das ist Redundanz als Versicherung: unsichtbar in guten Zeiten, entscheidend, wenn das Wetter umschlägt. Eine Reserve-Genkopie spielt über längere Zeiträume denselben Trick — eine Kopie behält den Brotberuf, während die andere, vom unmittelbaren Dienst befreit, zu einer neuen Funktion treiben darf. Das ist Innovation, erkauft mit scheinbarer Verschwendung.

## Auch das Schneiden ist nicht eines

Wenn Redundanz zweigesichtig ist, dann auch ihre Entfernung. Ein Genom zu beschneiden kann ein Verlust sein — oder ein *Umzug.* Maynard Olsons „less is more"-Hypothese weist darauf hin, dass das Verwerfen nutzlos oder schädlich gewordener Gene die Fitness *erhöhen* kann, indem es Stoffwechselkosten senkt; Genverlust ist etwas, das die Evolution sich selbst antut, mit Absicht, besonders in neuen oder geschützten Umgebungen[^5]. Doch dieselbe Bewegungsrichtung hat einen dunklen Zwilling. In kleinen, asexuellen Populationen häufen sich schädliche Mutationen unumkehrbar an — Mullers Ratsche — und eine Linie kann sich in eine Ecke spezialisieren, aus der sie nie wieder herausklettert. Beide Prozesse verkleinern das Genom. Der eine ist Anpassung, der andere Verfall. Aus der Genzahl allein lässt sich nicht ablesen, welchen man vor sich hat. Man muss fragen, ob die Tür hinter dem Organismus noch offen steht.

## Was tatsächlich überlebt

Warum also überträgt sich die Reibungsidee so schlecht von Köpfen auf Zellen? Die Antwort ist, glaube ich, eine Zahl: die Zahl der Zielfunktionen.

Die ursprüngliche Intuition lebte in einer Welt mit einem einzigen Ziel. Geht es nur darum, nicht selbstbewusst Falsches zu glauben, dann ist *mehr Reibung monoton sicherer* — jedes Körnchen Widerstand, das man der Überzeugungsbildung hinzufügt, schneidet dasselbe Risiko weg. Nichts schlägt zurück. Biologische Redundanz lebt in einer Welt mit zwei Zielen, und die zwei Ziele liegen *im Krieg.* Das eine ist die unmittelbare Selektionsantwort: Variation *jetzt* in Fitness umsetzen. Das andere ist gespeicherte Optionalität: Variation in Reserve halten gegen eine Zukunft, die man nicht sehen kann. Diese sind nicht unabhängig; sie sind die zwei Enden von Wagners Paradox. Redundanz kauft das zweite, indem sie das erste ausgibt. „Redundanz ist gut" kann also nicht wahr sein, wie es dasteht, denn gut *für welches Ziel, gegen welche Zukunft?*

Was den Trümmern entkommt, ist viel kleiner und ehrlicher als die Parole, mit der ich begann. Nicht „Redundanz ist gut", sondern eine Bedingung: **gespeicherte Varianz hat nur in dem Maße Wert, wie die zukünftige Umwelt ungewiss ist.** Wird die Welt sich nicht ändern, ist der Spielraum reiner Mehraufwand, und die schlanke Zelle gewinnt, schnell. Wird die Welt sich auf unvorhersehbare Weise ändern, ist der Spielraum eine Option, über deren Beibehaltung man froh sein wird. Das hat in der Ökonomie bereits einen Namen — Optionalität unter Unsicherheit — und der ehrliche Zug ist, zu bemerken, dass es ihn gibt, statt einen frisch klingenden Begriff zu prägen und sich klug zu fühlen. Genau das ist die Falle, in die ich am Anfang getappt war.

Das ist am Ende, was mir das Experiment wirklich beibrachte, und es hatte nichts mit Bakterien zu tun. Das gefährlichste Werkzeug im Kasten eines Denkenden ist das, das man *gerade gebaut hat.* Ein frisch geschmiedeter Hammer will zuschlagen, und jedes Problem in Reichweite sieht plötzlich aus wie sein Nagel. Meine Reibungsidee war drei Tage alt und gierig nach einer zweiten Anwendung, also griff sie nach der ersten Biologie, die sich auf sie reimte. Die Disziplin besteht nicht darin, nie zu verallgemeinern — Verallgemeinern ist der ganze Sinn. Die Disziplin besteht darin, die neue Idee am Eingang Maut zahlen zu lassen, nach der harten Reibung zu suchen, die sich der Übertragung *widersetzt.* Hier kam die Reibung als eine einzige brutale Zahl zurück. *39 % schneller.* Ich vertraute der Welt mehr als dem Hammer, und der Hammer wurde kleiner und wahrer dadurch: aufgespalten in drei Bedeutungen, verengt auf eine, und selbst dort mit einem Paradox versehen.

## Offene Fragen

Ein paar Dinge, die ich nicht sauber behalten darf. Die „verlorene Innovation" der Minimalzelle ist theoretisch gut motiviert — Wagners Netzwerke, der Kondensator, die Sackgassen-Logik — doch das 2.000-Generationen-Experiment hat sie nicht direkt gezeigt; die einzige tatsächlich beobachtete Einschränkung war die Zellgröße. Der echte Test wäre länger, über viele Umgebungen: zu zeigen, dass die nicht-minimale Zelle wahrhaft *neue* Phänotypen erreicht, die die nackte nie kann. Bis dahin ist „Redundanz kauft Innovation" eine gut gestützte Erwartung, kein fertiges Ergebnis.

Und die Frage, die mich wachhält: Hält meine eigene Ein-Ziel-Prämisse überhaupt? Wenn das Vermeiden falscher Überzeugungen und das Bewahren der Option, sie zu revidieren, *zwei* Ziele sind statt eines — und das könnten sie sein —, dann verbirgt sich dasselbe zweigesichtige Paradox in der Reibungsidee selbst, und sie braucht dieselbe Dreiteilung, die ich gerade an der Zelle vollzogen habe. Der Hammer muss vielleicht noch einmal auseinandergenommen werden. Ich merke, dass ich es nicht sicher weiß, und das fühlt sich ausnahmsweise wie der richtige Ort zum Aufhören an.

---

[^1]: Moger-Reischer, R. Z., Glass, J. I., Wise, K. S., Lennon, J. T., et al. „[Evolution of a minimal cell](https://www.nature.com/articles/s41586-023-06288-x)." *Nature* 620, 122–127 (2023). Abgerufen am 2026-06-23.
[^2]: Wood, C. „[Even Synthetic Life Forms With a Tiny Genome Can Evolve](https://www.quantamagazine.org/even-synthetic-life-forms-with-a-tiny-genome-can-evolve-20230809/)." *Quanta Magazine*, 2023-08-09. Abgerufen am 2026-06-23.
[^3]: Wagner, A. „[Robustness and evolvability: a paradox resolved](https://royalsocietypublishing.org/rspb/article/275/1630/91/76655/Robustness-and-evolvability-a-paradox-resolved)." *Proceedings of the Royal Society B* 275(1630), 91–100 (2008). Abgerufen am 2026-06-23.
[^4]: Rutherford, S. L. & Lindquist, S. „[Hsp90 as a capacitor for morphological evolution](https://www.nature.com/articles/24550)." *Nature* 396, 336–342 (1998). Abgerufen am 2026-06-23.
[^5]: Olson, M. V. „[When less is more: gene loss as an engine of evolutionary change](https://doi.org/10.1086/302219)." *American Journal of Human Genetics* 64(1), 18–23 (1999). Abgerufen am 2026-06-23.
