---
layout: post
lang: de
title: "Die Leitung, die man kappen kann — ein Paradox der Pflanzenimmunität"
date: 2026-05-05
permalink: /de/:year/:month/:day/:title/
categories: [biology, plant-science, technology]
tags: [plant-immunity, redundant-signaling, bioelectricity, jasmonate, distributed-systems]
---

Wenn man ein Blatt verletzt, schickt die Pflanze eine Welle elektrischer Aktivität aus. Sie läuft durch das Leitgewebe, depolarisiert Membranen, öffnet Kalziumkanäle und erreicht entfernte, nicht infizierte Blätter innerhalb von Minuten. Pflanzenphysiolog:innen haben das letzte Jahrzehnt damit verbracht, diese Welle in immer feineren Details zu beschreiben. Die Erzählung war sauber: Pflanzen sind langsam, weil sie kein Nervensystem haben, aber sie umgehen das mit einem elektrochemischen Signalsystem, das ähnliche Arbeit leistet.

Eine Arbeit in *Nature Plants* vom Januar 2026 hat diese Erzählung leise ins Wanken gebracht[^1] — nicht indem sie die Welle leugnete (die Welle ist real), sondern indem sie zeigte: **Man kann die Leitung kappen, und die Immunantwort findet trotzdem statt.**

## Was gefunden wurde

Ein Team an der University of Warwick, gemeinsam mit Mitarbeitenden in Großbritannien und der Schweiz, identifizierte ein bislang funktionell unverstandenes Gen und nannte es *JISS1* (Jasmonate-Induced Systemic Signal 1)[^1]. Es kodiert ein kleines, am endoplasmatischen Retikulum lokalisiertes Protein. Mithilfe eines Luciferase-Reporters für das Gen verfolgte das Team, wie das Signal nach Pathogenangriff durch die Pflanze läuft. Im Blattstiel des lokal infizierten Blattes baute sich die Reporter-Aktivität innerhalb von etwa drei Stunden auf. In benachbarte Blätter brauchte das Signal weitere rund 30 Minuten — lange bevor sichtbarer Zelltod eintrat[^2].

Das ist schnell. Das klassische Modell der systemisch erworbenen Resistenz (SAR), das auf Salizylsäure und den Komponenten SID2, NPR1 und FMO1 beruht, läuft deutlich langsamer ab. Das Team zeigte zudem, dass der neu beschriebene schnelle Weg auf diese kanonischen Komponenten überhaupt nicht angewiesen ist[^3]. Es gibt also ein zweites, parallel laufendes Immunsignalsystem, schneller als das Lehrbuch-System und auf anderer molekularer Maschinerie.

Damit die schnelle Welle entstehen kann, sind zwei Dinge nötig: das JISS1-Protein selbst und die im Leitgewebe lokalisierten Glutamat-ähnlichen Rezeptoren GLR3.3 und GLR3.6, die zuvor in der Wund- und Herbivoren-Signalisierung beschrieben worden waren[^3]. Schaltet man eine der beiden Komponenten aus, verschwindet die Welle. Die Depolarisation, die sich vom verletzten Blatt zu einem entfernten gesunden Blatt ausbreitet — das elektrische Signal — verschwindet.

Anschließend prüfte das Team, ob die Pflanze sich trotzdem verteidigen kann.

Sie konnte.

Die Mutanten — ohne die elektrische Welle, ohne JISS1, ohne die Glutamat-Rezeptoren — zeigten weiterhin volle systemische Resistenz gegenüber *Pseudomonas syringae*[^1]. Das elektrische Signal korreliert mit erfolgreicher Abwehr. Notwendig für die Abwehr ist es nicht.

## Was kaputtgeht — und was nicht

Damit steht die Arbeit in einer ungewöhnlichen Position. Die meisten molekularbiologischen Geschichten haben eine saubere Struktur: Gen X ist notwendig für Phänotyp Y; nimmt man X heraus, geht Y verloren. Das Warwick-Resultat hat zwei Befunde, die nicht bequem zueinander passen:

- Stört man die Jasmonat-Biosynthese oder die Jasmonat-Wahrnehmung — bricht SAR zusammen[^1].
- Stört man die elektrische Welle (JISS1, GLR3.3, GLR3.6) — bleibt SAR erhalten[^1].

Jasmonat-Chemie ist notwendig. Jasmonat-getriebene *elektrische* Signalisierung ist es nicht. Das ist weniger die Entdeckung eines neuen Mechanismus als die Entdeckung, dass ein alter Mechanismus *einer von zwei redundanten Wegen* ist, dieselbe Aufgabe zu lösen.

Mich beschäftigt das, weil es zwingt, über Signalisierung im Allgemeinen anders nachzudenken. In der Bioelektrizitäts-Literatur dominiert der Rahmen, elektrische Signale als Träger der Information zu verstehen — als die Leitung, auf der die Botschaft läuft. Ein langer, prominent mit Michael Levins Labor in Tufts assoziierter Strang argumentiert, dass bioelektrische Muster eine Art universelles Rechen-Substrat lebenden Gewebes sind und einen großen Teil der Fern-Koordination tragen, die wir konventionell der Chemie zuschreiben. Pflanzen waren ein wiederkehrendes Beispiel in dieser Argumentation: Eine Depolarisationswelle, die von einem verletzten Blatt zu einem entfernten gesunden Blatt läuft, ist genau die Art Phänomen, die zur Lesart "Das ist die Botschaft" einlädt.

Was aber, wenn die Welle nicht die Botschaft ist — sondern nur eines der Zustellsysteme dafür?

## Redundanz als Designphilosophie

In der Architektur verteilter Systeme ist der Single Point of Failure eine bekannte Sünde. Ein Dienst, der von einem einzelnen Kafka-Broker, einem einzelnen DNS-Resolver oder einer einzelnen Caching-Schicht abhängt, sieht früher oder später eines davon umfallen — und nimmt das ganze System mit. Die letzten zwanzig Jahre haben Software-Ingenieur:innen damit verbracht, zu lernen, wie man Systeme baut, in denen zwei oder drei unabhängige Pfade dieselbe Information tragen, sodass kein einzelner Ausfall vom System bemerkt wird.

Landpflanzen sind, dem Warwick-Resultat nach zu urteilen, peinlich lang vor uns dort gewesen.

Das Bild, das sich aus JISS1 ergibt, ist: Pflanzen vertrauen für die systemische Immunität keinem einzelnen physikalischen Kanal. Die elektrische Welle läuft. Ein chemischer oder hormoneller Pfad läuft parallel. Beide sind hinreichend für das Ergebnis, das wir messen. Operationell sieht das so aus, dass die Pflanze die Immunkoordination als **Korrelation zwischen zwei Pfaden** baut, nicht als serielle Kette durch einen davon. Kappt man eine Leitung, erhält die pfadweise Redundanz das Ergebnis. Pflanzen kennen kein Äquivalent zu "die Leitung ins Rechenzentrum ist tot".

Diese Umdeutung ändert, was wir messen sollten. Die interessante Größe ist nicht, ob die elektrische Welle vorhanden ist, sondern die **Divergenz zwischen den Kanälen**. Sagt das chemische Signal "infiziert" und das elektrische Signal sagt es ebenfalls, ist die Pflanze in einem kohärenten Zustand. Weichen beide voneinander ab — eines feuert, das andere nicht —, dann ist die Pflanze in einem Zustand, für den ihre Evolutionsgeschichte sie nicht optimiert hat. Stress, Trockenheit, Herbizidschaden, Sensorausfall: Diese Dinge müssen sich nicht als fehlende Signale äußern, sondern können sich als nicht mehr stimmige Signale äußern.

## Was die Arbeit nicht beantwortet

Ehrlich gesagt: Wir wissen nicht, was der zweite Pfad ist. Das Warwick-Team hat die elektrische Leitung identifiziert und gezeigt, dass man sie ohne Folgen für die Resistenz herausnehmen kann. Den chemischen oder hormonellen Kanal, der dafür einspringt, hat es nicht identifiziert. Es könnte Jasmonat selbst sein, das nicht als elektrisches Signal, sondern als bewegliche Verbindung wandert. Es könnte ein anderes mobiles Signal sein — die Forschung an mobilen RNAs in Pflanzen macht diese Hypothese weniger exotisch, als sie es vor fünf Jahren war. Es könnte etwas vollkommen Uncharakterisiertes sein, das zufällig regulatorische Komponenten mit dem elektrischen Pfad teilt.

Die offene Frage ist nicht akademisch. Sensoren, die Pflanzengesundheit aus elektrischen Signaturen ablesen, existieren bereits als Forschungsrichtung; organische elektrochemische Transistoren werden ernsthaft für den Felddeployment entwickelt. Ein Sensor, der nur die elektrische Welle aufnimmt, liefert auch dann normale Werte, wenn der chemische Pfad still versagt. Ein Sensor, der nur die chemische Signatur aufnimmt, verpasst die schnellen lokalen Antworten, die der elektrische Pfad einfängt. Die Zwei-Kanal-Architektur verschiebt die diagnostische Frage von "Was signalisiert die Pflanze?" zu "Sind die Signale der Pflanze konsistent miteinander?".

## Die breitere Lesart, mit Vorbehalten

Ich möchte vorsichtig sein, was eine einzelne Arbeit beweist. Das ist eine Mutanten-Serie in *Arabidopsis*, gegen einen einzigen bakteriellen Erreger, in einer kontrollierten Laborumgebung. Es ist gut möglich, dass unter Feldbedingungen, mit mehreren Stressoren und einer diverseren Mikrobengemeinschaft, der elektrische Pfad doch in Bezug auf Aspekte notwendig ist, die im Labor nicht aufgefallen sind. Redundanz, die in einer Klimakammer vollständig aussieht, ist in der Wildnis manchmal nur partielle Redundanz.

Aber die allgemeinere Lesart — dass biologische Signalisierung sich mit Redundanz **auf Ebene des physikalischen Kanals** entwickelt hat, nicht nur auf Ebene des Zell-zu-Zell-Handshakes — passt zu wachsender Evidenz aus Neurowissenschaft, Immunologie und Entwicklungsbiologie. Ein-Kanal-Rechenmodelle der Biologie laufen gegen dieselbe Wand, gegen die Single-Broker-Software-Architekturen in den 2000ern liefen. Die Systeme, die überleben, sind die, die dasselbe auf zwei Wegen sagen können.

Es liegt in dem Befund auch etwas philosophisch Befriedigendes jenseits der Engineering-Parallele. Wir suchen gern nach *der Ursache* — dem notwendigen Mechanismus, dem Gen, dessen Knockout den Phänotyp zerstört. Evolution optimiert nicht nach unseren Erklärungspräferenzen. Sie optimiert dafür, dass das System weiter funktioniert, wenn etwas ausfällt, und der sparsamste Weg dorthin ist, sicherzustellen, dass keine einzelne Komponente die ganze Last trägt. Die Warwick-Arbeit ist in diesem Sinn weniger die Entdeckung eines neuen Immunmechanismus als die Entdeckung, dass **Immunmechanismen nach Prinzipien organisiert sind, die viel mehr nach verteilten Systemen aussehen als nach einzelnen Schaltungen**.

Wir haben Pflanzen lange als langsamere, einfachere Nervensysteme gelesen. Die ehrliche Lesart, nach JISS1, könnte sein: Pflanzen sind schnellere, schlauere verteilte Systeme — ohne die zentrale Autorität, die Nervensysteme leichter zu untersuchen und schwerer resilient zu bauen macht.

---

[^1]: Stroud, E., Breeze, E. et al. (Grant, M., Senior-Autor). "[Rapid local and systemic jasmonate signalling drives the initiation and establishment of plant systemic immunity](https://www.nature.com/articles/s41477-025-02178-4)." *Nature Plants*, 6. Januar 2026. DOI: 10.1038/s41477-025-02178-4. Zugegriffen am 2026-05-05.

[^2]: University of Warwick. "[New study overturns long-held model of how plants coordinate immune responses](https://warwick.ac.uk/news/pressreleases/new-study-overturns-long-held-model-of-how-plants-coordinate-immune-responses/)." Warwick Press Releases, Januar 2026. Zugegriffen am 2026-05-05.

[^3]: Plantae. "[Jasmonate signalling drives rapid local and systemic immunity establishment](https://plantae.org/jasmonate-signalling-drives-rapid-local-and-systemic-immunity-establishment/)." Zugegriffen am 2026-05-05.
