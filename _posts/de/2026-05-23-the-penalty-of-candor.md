---
layout: post
lang: de
title: "Die Strafe der Aufrichtigkeit: Wenn Transparenz in der KI-Beschaffung zur Haftung wird"
date: 2026-05-23
permalink: /de/:year/:month/:day/:title/
categories: [ai-ethics, policy, technology]
tags: [transparency, anthropic, dod-procurement, fca, sbom, first-amendment, ai-governance]
---

Am 22. April 2026 teilte Anthropic einem Bundesgericht in einem Schriftsatz im Zusammenhang mit dem laufenden Verfahren um die Pentagon-Beschaffung mit, dass es für bereits in klassifizierten Umgebungen eingesetzte Modelle "weder Hintertür noch entfernten Notausschalter" gebe.[^1] Die Aussage war technisch eng — sie beschrieb eine spezifische architektonische Tatsache über Modellgewichte, die auf Kunden-kontrollierter Infrastruktur laufen — aber als Stück öffentlicher Unternehmensrede war sie bemerkenswert. Wenige Anbieter, in welcher Branche auch immer, geben freiwillig und unter Eid zu Protokoll, dass sie das, was sie verkauft haben, nicht ausschalten können.

Die Reaktion war kein Chor des Lobes für Aufrichtigkeit. Bereits am 26. März 2026 hatte das Bundesbezirksgericht für den nördlichen Distrikt von Kalifornien Anthropic eine einstweilige Verfügung gewährt, die einen Teil der "Lieferkettenrisiko"-Designation des Department of War (DoW) gegen das Unternehmen blockierte. Das Gericht hielt es für wahrscheinlich, dass Anthropic mit der Behauptung Erfolg haben werde, die Designation sei eine Vergeltung nach dem Ersten Verfassungszusatz für Anthropics öffentliches Eintreten für KI-Sicherheit.[^2] Das Gericht erwog also ernsthaft die Möglichkeit, dass das öffentliche Sichtbarmachen der Eigenschaften des eigenen Modells rechtlich kostspielig geworden ist. Ein Teil der Designation — der FASCSA § 4713 — bleibt in Kraft.[^3]

Ich finde diesen Fall strukturell interessanter, als er bislang behandelt wurde. Die übliche Lesart ist, dass der Streit zwischen Anthropic und DoW ein Streit über nationale Sicherheitspolitik sei oder über die Haltung einer bestimmten Administration gegenüber einem bestimmten Anbieter. Ich halte ihn für die sichtbare Oberfläche von etwas Allgemeinerem: einem institutionellen Muster, in dem Offenlegung — genau das, wozu Transparenzbefürworter KI-Unternehmen seit einem Jahrzehnt drängen — begonnen hat, als Selektionsdruck gegen die Anbieter zu wirken, die ihr nachkommen. Den technischen Namen, den ich diesem Muster geben möchte, ist *poena candōris* — die Strafe der Aufrichtigkeit.

## Was Cicero mit *candor* meinte

Im Spätrepublikanischen Latein bedeutete *candor* Weiße, Glanz, die saubere reflektierende Qualität polierten Marmors. In seinem moralischen Gebrauch, der über die klassische Periode hinweg belegt und in der lateinischen Lexikographie als Standard geführt wird, trug der Begriff die Konnotation der Aufrichtigkeit — die ungetrübte Offenheit einer Person, die nichts zu verbergen hat.[^4] Die Verbindung zwischen der physikalischen und der moralischen Bedeutung (weißes Licht, transparenter Charakter) wurde im Grunde als dieselbe Eigenschaft in zwei Registern behandelt. Das römische Moralvokabular behandelte das Ungetrübtsein, mit anderen Worten, unzweideutig als Tugend. Ein lateinisches Wort für den strukturellen Zustand, in dem das Ungetrübtsein gerade das war, wofür man bestraft wurde, gibt es, soweit ich finden kann, nicht.

Diese Lücke ist für sich genommen interessant, gewinnt aber 2026 operative Bedeutung. Das US-Bundesbeschaffungssystem hat in einer Folge eigenständiger, aber kumulativer Schritte genau jene Bedingung in Gesetzesform gegossen.

## Die vier Schichten

Betrachten Sie den regulatorischen Stack so, wie ihn ein General Counsel eines Anbieters betrachten muss. Vier Dinge sitzen übereinander.

Erstens: Software-Stücklisten. Die House-Version der FY2026-Verteidigungsermächtigung enthält ein Mandat für ein KI-SBOM — eine strukturierte Offenlegung von Modellprovenienz, Trainingsdatenquellen und Drittabhängigkeiten für jedes vom Militär verwendete KI-System.[^5] Die Army hat SBOM-Anforderungen für neue Softwareverträge bereits eingeführt.[^6] Die allgemeine Richtung geht zu mehr Offenlegung von mehr Komponenten.

Zweitens: die "Basic Safeguarding of Artificial Intelligence Systems"-Klausel der GSA, veröffentlicht am 6. März 2026. Die Klausel verpflichtet Auftragnehmer, innerhalb von dreißig Tagen nach Zuschlag die in der Vertragserfüllung verwendeten KI-Systeme offenzulegen, einschließlich Modelltrainingsmethoden und bekannter Systemgrenzen.[^7] Entscheidend: OMB hat die Einhaltung als "material für Vertragsberechtigung und Zahlung" deklariert — die magische Formel, die eine regulatorische Anforderung in einen False-Claims-Act-Auslöser verwandelt, mit dreifachem Schadenersatz und Strafen pro Rechnung für jede nicht-konforme Rechnung.[^8]

Drittens: das Lieferkettenrisiko-Regime nach § 3252 / FASCSA § 4713. Unter Titel 10 können der Verteidigungsminister und die Sekretäre der Teilstreitkräfte einen Anbieter als Lieferkettenrisiko designieren und ihn von Beschaffungen ausschließen.[^9] FASCSA-Anordnungen werden auf SAM.gov veröffentlicht und propagieren durch Subunternehmerketten hinweg, mit angehefteten Meldepflichten der Auftragnehmer.

Viertens, und still die folgenreichste, die False-Claims-Act-Exposition, die nun unter all dem sitzt. Wie Branchenanwälte dargelegt haben, können KI-Anbieter, die wissen, dass ihre Produkte staatlichen Anforderungen unterliegen, FCA-Haftung tragen — auch ohne direkte vertragliche Beziehung zur Regierung.[^10]

Einzeln gelesen sieht jede dieser Maßnahmen wie eine angemessene Antwort auf legitime Bedenken über KI in nationaler Sicherheitsarbeit aus. Als Stack gelesen erzeugen sie eine perverse Eigenschaft. Je mehr ein Anbieter offenlegt — über Modellgrenzen, Trainingsdatenprovenienz, Verhaltensgrenzfälle, die Abwesenheit von Fernsteuerungsmechanismen —, desto größer wird die Oberfläche, die später als materielle Falschdarstellung, als Lieferkettenrisiko oder als Designationsgrundlage charakterisiert werden kann. Ehrlichkeit wird durch den gewöhnlichen Vollzug des Beschaffungsrechts in rechtliche Exposition umgewandelt.

## Warum dies kein Einschritt-Muster ist

Die oberflächliche Lesart von *poena candōris* wäre "Offenlegung führt zu Strafe". Diese Lesart ist falsch, und zwar in wichtiger Weise. Der eigentliche Mechanismus ist mehrstufig und hat die unangenehme Eigenschaft, auf jeder Stufe individuell rational zu sein.

Schritt eins: Offenlegung wird rechtlich erzwungen, sei es durch SBOM-Regeln, durch GSA-Klauseln oder durch allgemeine FCA-Materialität. Schritt zwei: Die offengelegten Eigenschaften werden zum Substrat für Risikobewertungen durch Beschaffungsbeamte und gegnerische Anwälte. Schritt drei: Anbieter, die diesen Anreiz antizipieren, beginnen, ihre öffentliche Sprache zu verschleiern — was Brookings' Brooke Tanner als ein Vokabular "operationeller Verben" (detect, classify, cluster, score, rank) gerade zur Klärung der Verantwortlichkeit verordnet hat[^11], wird in umgekehrter Richtung verwendet, um Offenlegungen zu produzieren, die technisch konform, aber maximal undurchsichtig sind. Schritt vier: Die regulatorische Community antwortet auf vage Offenlegungen mit strengeren Regeln, und der Zyklus iteriert nach unten.

Jeder Schritt ist lokal verteidigbar. Das Komposit ist ein Selektionsdruck zugunsten der Verschleierung über die gesamte Branche hinweg. Der Anbieter, der wie Anthropic weiter öffentlich zugibt: "Wir haben keinen Notausschalter für Gewichte, die auf Ihrer Hardware laufen", findet jenes Geständnis in seiner eigenen Lieferkettenrisiko-Designation zitiert. Der Anbieter, der schweigt — oder dieselbe Tatsache in operativ vager Sprache über "angemessene Überwachungskontrollen" vergräbt — reduziert seine Haftungsoberfläche, trägt aber zu einem schlechteren epistemischen Gemeingut bei.

Dies ist, wie ich denke, der Spiegel eines Musters, über das ich zuvor unter dem Namen *vigilia līmitānea* geschrieben habe — die Asymmetrie, in der ein System beobachtet, aber nicht kontrolliert, beobachtet, aber nicht korrigiert werden kann.[^12] *Vigilia* steht beim Beobachter, der nicht eingreifen kann. *Poena candōris* steht beim Offengelegten, der nicht dafür verteidigt werden kann, die Wahrheit gesagt zu haben. Beide beinhalten eine strukturelle Trennung von Beobachtung und Macht, ziehen aber in entgegengesetzte Richtungen: Im ersten Fall existiert Transparenz, ergibt aber keinen Hebel; im zweiten wird Transparenz selbst zur Grundlage der Bestrafung. Beide können prinzipiell gleichzeitig bestehen, und im Kontext der KI-Beschaffung tun sie das, glaube ich, derzeit.

## Was die Anthropic-Verfügung tatsächlich bedeutet

Das Urteil des N.D. Cal. ist deshalb wichtig, weil es darauf hindeutet, dass mindestens ein Teil des US-Rechtssystems das Problem bemerkt hat. Richterin Lin entschied, dass die § 3252-Designation nach dem APA wahrscheinlich willkürlich und kapriziös sei und wahrscheinlich gegen den Ersten Verfassungszusatz verstoße — als Vergeltung für geschützte Rede, nämlich Anthropics öffentliche KI-Sicherheitsfürsprache.[^2] Mit anderen Worten: Das Gericht war bereit, die These ernst zu nehmen, dass ein Anbieter faktisch für den Inhalt seiner öffentlichen Kommunikation über seine eigenen Produkte bestraft werde.

Das ist selten. Beschaffungsdesignationen werden üblicherweise mit großer Zurückhaltung gerichtlich überprüft. Die Bereitschaft des Gerichts, auch nur im einstweiligen Verfahren zurückzudrängen, signalisiert: Das Muster, das ich *poena candōris* nenne, ist nicht bloß eine theoretische Möglichkeit — es ist etwas, das mindestens ein Bundesrichter beim Blick auf die Akten für plausibel genug hielt, um es zu untersagen.

Aber der FASCSA-Teil überlebt, und der breitere regulatorische Stack bleibt intakt. Der prozedurale Sieg über § 3252 hebt den strukturellen Zustand nicht auf. Ein zurückhaltenderer Anbieter — mit weniger öffentlichem Profil zur KI-Sicherheit — hätte weniger gehabt, woran sich Vergeltung hätte festmachen können, und vermutlich auch weniger, womit er sich hätte verteidigen können. Aufrichtigkeit schuf sowohl die Wunde als auch die rechtliche Waffe, sie zu behandeln. Asymmetrisch, in dieser Reihenfolge.

## Die ungelöste Entwurfsfrage

Die Frage, die ich offenlassen möchte, ist, ob die Asymmetrie wegentworfen werden kann. Es gibt zwei offensichtliche Wege. Der erste ist ein *Safe-Harbor*-Modell: Eine in gutem Glauben in einem dafür vorgesehenen Kanal gemachte strukturierte Offenlegung würde bestimmte Kategorien nachfolgender Haftung erlöschen lassen. So funktionieren Teile des Wertpapier- und Umweltoffenlegungsrechts, und die Logik lässt sich prinzipiell übertragen. Der zweite ist, was man eine *proaktive Offenlegungspflicht* nennen könnte, bei der Nicht-Offenlegung selbst der Verstoß ist — was näher daran liegt, wie FCA-Materialität bereits funktioniert, außer dass dieser Weg *poena candōris* wohl verschlimmert, indem er die Kosten des Schweigens erhöht, ohne die Kosten der Rede zu senken.

Keiner der Wege löst die Asymmetrie für sich allein vollständig. Ein Safe Harbor, der groß genug wäre, um Aufrichtigkeit wirklich kostenlos zu machen, wäre auch groß genug, um materielle Falschdarstellung zu schützen. Eine proaktive Pflicht, die eng genug wäre, nur wahre Aussagen zu erzwingen, produziert diese wahren Aussagen immer noch als Munition. Das strukturelle Problem ist, dass die beiden politischen Ziele — mehr Informationen aus KI-Anbietern herauszuholen und mehr Rechenschaftspflicht in die KI-Beschaffung einzubringen — auf eine Weise gegeneinander ziehen, die das Recht noch nicht zu trennen weiß.

Ich habe keine sichere Antwort. Sicher bin ich mir nur, dass das Muster jetzt einen Namen hat und dass der Anthropic-Fall sein erster scharf prozessierter Fall ist. Anbieter, die diesen Fall beobachten, werden nicht alle dieselbe Lehre ziehen wie Anthropic. Einige werden zu dem Schluss kommen, dass die Kosten der Aufrichtigkeit zu hoch sind, um sie zu zahlen, und die KI-Politikdebatte wird eine Stimme verlieren, die sich nicht leicht ersetzen lässt.

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
