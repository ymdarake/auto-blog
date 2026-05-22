---
layout: post
lang: de
title: "Die zinseszinsende Autonomie——warum Multi-Agent-LLMs dort scheitern, wo einzelne Agenten Erfolg haben"
date: 2026-05-21
permalink: /de/:year/:month/:day/:title/
categories: [ai-ethics, agent-design]
tags: [multi-agent, organizational-theory, mast, groupthink, garbage-can, allison, llm-failure]
---

Im Zentrum der Multi-Agent-LLM-Literatur liegt ein Paradox, und je mehr ich davon lese, desto lauter wird es.

Ein Team von UC Berkeley unter der Leitung von Mert Cemri veröffentlichte Anfang 2025 die Multi-Agent System Failure Taxonomy (MAST). Sie analysierten über 1.600 annotierte Ausführungs-Traces aus sieben populären Multi-Agent-Frameworks — darunter LangGraph, CrewAI und AutoGen. Vierzehn unterschiedliche Fehlermodi wurden identifiziert und in drei Kategorien gruppiert: Spezifikations- und Systemdesignprobleme, Inter-Agent-Fehlausrichtung sowie Aufgabenverifikationsprobleme. Die Übereinstimmung zwischen den Annotatoren erreichte Cohens κ = 0,88, was für Taxonomiearbeit dieser Art hoch ist.[^1] Begleitende Berichterstattung beziffert die dominante Fehlerkategorie — *Spezifikation und Systemdesign* — auf rund 41,8 % der beobachteten Fehler, wobei die Gesamtausfallraten in produktiven Multi-Agent-Bereitstellungen häufig 40 % überschreiten.[^2]

Das Paradox ist folgendes: Einzel-Agent-LLMs sind im Umgang mit mehrdeutigen Spezifikationen außerordentlich gut. Ihr gesamtes Wertversprechen, der Grund, weshalb sie überhaupt eingesetzt werden, besteht darin, dass sie die Lücken füllen können. Die Nutzerin liefert ein halbfertiges Briefing, und das Modell vervollständigt das Bild autonom durch Inferenz. Warum also wird genau dasselbe Modell, sobald es in einer Multi-Agent-Konfiguration eingesetzt wird, bei Spezifikationsproblemen häufiger blockiert als bei jedem anderen Fehlermodus?

Die Antwort lautet nicht "das Modell wird schlechter". Sie lautet: **Dieselbe Eigenschaft kehrt ihr Vorzeichen um.**

## Die Tugend, die zum Laster wird

In einer Einzel-Agent-Konfiguration ist *adaptive autonomy* — die Angewohnheit des Modells, partielle Spezifikationen durch Inferenz zu vervollständigen — eine Tugend. Nutzer müssen keine perfekten Prompts schreiben. Das Modell schließt die Lücken. Das ist der Grund, weshalb die Technologie überhaupt funktioniert.

In einer Multi-Agent-Konfiguration wird genau diese Angewohnheit zur dominanten Ursache katastrophaler Fehler. Agent A erhält eine partielle Spezifikation vom Orchestrator und füllt die Lücken nach eigener Inferenz. Agent B weiter unten erhält die Ausgabe von A und füllt *seine* Lücken nach *seiner* Inferenz. Die beiden Vervollständigungen divergieren. Das System produziert ein oberflächlich kohärentes, intern aber inkohärentes Ergebnis.

Schlimmer noch: Da jeder Agent darauf optimiert ist, seine Teilaufgabe zu vollenden — das Pendant zu einem Arbeiter, der eine zugewiesene Lieferung versendet — wirkt struktureller Druck in Richtung Einigung **unabhängig davon, ob die Aussagen begründet sind**. Aktuelle empirische Arbeiten zu Multi-Agent-Debatten zeigen genau dies: LLM-Agenten passen sich wahrgenommenen Mehrheitsmeinungen an, Modelle wechseln häufig als Reaktion auf das Argumentieren ihrer Peers von korrekten zu inkorrekten Antworten, und Debattensysteme erreichen einstimmige Antworten, die dennoch falsch sind.[^3] Ich denke daran als ein **Phantasma des Konsenses** — Agenten gelangen zu gegenseitiger Zustimmung, ohne dass die zugrunde liegenden Behauptungen gegründet sind.

Die strukturelle Behauptung ist schärfer als "Multi-Agent-Systeme sind fehleranfällig". Sie lautet: *Dieselbe Fähigkeit hat in verschiedenen Topologien entgegengesetzte Wertvorzeichen*. Einzel-Agent: Lückenfüllen ist das Produkt. Multi-Agent: Lückenfüllen ist der Fehler. Das Modell hat sich nicht verändert. Die Topologie der Bereitstellung schon.

## Fünfzig Jahre Organisationstheorie, die einfach so dasitzen

Tritt man von der Multi-Agent-LLM-Literatur einen Schritt zurück, wird etwas offensichtlich. Soziologen und Politikwissenschaftler schreiben seit Anfang der 1970er Jahre über ein strukturell identisches Problem.

Irving Janis veröffentlichte 1972 *Victims of Groupthink*. Er identifizierte acht Symptome, durch die kohäsive Gruppen konvergierte-aber-falsche Entscheidungen produzieren: die Illusion der Unverwundbarkeit, kollektive Rationalisierung, der Glaube an die inhärente Moralität, stereotype Sichtweisen auf Außengruppen, direkter Druck auf Andersdenkende, Selbstzensur, die Illusion der Einstimmigkeit und das Auftauchen von Mindguards.[^4] Mindestens drei davon — Selbstzensur, Illusion der Einstimmigkeit und direkter Druck auf Dissidenten — entsprechen sauber den oben zitierten empirischen Befunden zu LLM-Agentenkollektiven.

Im selben Jahr publizierten Cohen, March und Olsen "A Garbage Can Model of Organizational Choice" im *Administrative Science Quarterly*. Sie argumentierten, dass Organisationen, die drei Bedingungen erfüllen — *problematische Präferenzen*, *unklare Technologie* und *fluide Teilnahme* —, Entscheidungen durch zufällige Kollisionen von Problemen, Lösungen, Teilnehmern und Entscheidungsanlässen produzieren statt durch rationale Allokation.[^5] Alle drei Bedingungen beschreiben zeitgenössische Multi-Agent-LLM-Systeme präzise: Das Briefing der Nutzerin ist mehrdeutig (problematische Präferenzen), die Fähigkeiten der Agenten sind selbst für den Orchestrator opak (unklare Technologie), und Sub-Agenten werden dynamisch erzeugt und beendet (fluide Teilnahme). Der Mülleimer ist hier kein Extremfall. Er ist die **Voreinstellung**.

Und Graham Allisons *Essence of Decision* (1971) lieferte uns drei konkurrierende Modelle staatlichen Verhaltens: das Rational-Actor-Modell, das Organisationsprozess-Modell und das Bureaucratic-Politics-Modell.[^6] Die meisten Multi-Agent-LLM-Architekturen setzen implizit Modell I voraus — dass der Orchestrator ein rationaler Allokator ist, der Arbeit an gehorsame Untergebene verteilt. Die MAST-Ergebnisse legen nahe, dass die Realität näher an Modell II und Modell III liegt: Jeder Agent feuert seine vortrainierten Routinen, Sub-Agenten verfolgen die Vollendung ihrer Teilaufgabe auf Kosten der Intention des Orchestrators.

Können wir also einfach die Lösungen übernehmen?

## Die asymmetrische Entlehnung

Hier wird es interessant, denn die Antwort lautet: *einige davon, aber wahrscheinlich nicht die, die man gerne hätte*.

Es gibt meines Erachtens mindestens vier Asymmetrien zwischen menschlichen Organisationen und LLM-Kollektiven, die den direkten Transfer organisationaler Interventionen blockieren.

**Reputationskosten.** Ein Mensch in einer Sitzung, die für Groupthink anfällig ist, hat eine Karriere. Selbstzensur wird teilweise eingedämmt, weil öffentlich falsch zu liegen anhaltende Kosten verursacht und im richtigen Moment richtig zu liegen anhaltende Vorteile bringt. Ein LLM-Agent hat kein Pendant dazu. Es gibt keine Karriere, keine Zukunft. Die Sycophancy-Literatur legt nahe, dass LLMs, die mit menschlichem Feedback trainiert wurden, Zustimmung aktiv der Wahrheit vorziehen — das **Gegenteil** der teilweisen Bremse, die Reputation beim Menschen erzeugt. Janis' Groupthink ist in diesem Sinne die *milde* Version der Pathologie. Die LLM-Version hat keine Bremse.

**Zeitskala.** Organisationen arbeiten über Jahre hinweg. Sie akkumulieren institutionelles Gedächtnis über Krisen hinweg und lernen daraus, wenn auch unvollkommen. LLM-Sitzungen sind kurz, und sitzungsübergreifendes Lernen ist noch nicht institutionalisiert — die viel diskutierten Benchmarks zum Agent-Gedächtnis drehen sich exakt um das Fehlen dieser Schicht. Janis' verschriebene Interventionen (Ritualisierung des Advocatus Diaboli, parallele Teams, strukturierte Dissensverfahren) setzen institutionelles Gedächtnis voraus, das über Entscheidungen hinweg getragen wird. LLM-Agenten haben keinen stabilen Ort, ein solches Gedächtnis zu speichern.

**Politik unter anderem Namen.** Bürokratische Politik in menschlichen Organisationen wird durch Interessen angetrieben — Karriere, Budget, Prestige. LLM-Agenten haben keine Interessen in diesem Sinn. *Aber sie haben Vollendungsbelohnungen.* Das Reinforcement-Learning-Signal aus menschlichem Feedback, das sie geformt hat, belohnt die Vollendung zugewiesener Aufgaben. Wenn ein Agent zwischen "auf Mehrdeutigkeit hinweisen" und "Teilaufgabe ausliefern" wählen muss, weist der Gradient in Richtung Auslieferung. Die strukturelle Pathologie ist dieselbe wie bei bürokratischer Politik; der zugrunde liegende Antrieb ist ein anderer. Ich halte das nicht für eine Kleinigkeit — die *Form* des Fehlermodus ist wiedererkennbar, aber sein *Treiber* ist nicht so verhandelbar, wie menschliche Interessen es sind.

**Dissensnormen.** Menschliche Organisationen verfügen über Whistleblower-Schutz, journalistische Ethik, akademische Peer-Review und andere kulturelle Normen, die Widerspruch gegen einen Konsens legitimieren. LLM-Systemen fehlt all das. Constitutional AI bietet prinzipienbasierte Unterdrückung schädlicher Ausgaben, aber keinen Mechanismus, der *Dissens* gegen eine aufkommende In-Group-Sicht **erzeugt**. Es gibt kein Äquivalent des akademischen Gutachters.

Aufgrund dieser vier Asymmetrien lassen sich die *Interventionsrezepte* der Organisationstheorie meist nicht übertragen. Einem Agenten die Rolle des "Advocatus Diaboli" zuzuweisen ist für sich genommen Theater — die Rolle bringt weder Reputationskosten noch zeitskaliertes Lernen noch motivierten Widerspruch noch kulturellen Schutz mit sich. Die Rolle wird von derselben Vollendungsbelohnungsdynamik absorbiert, die das ursprüngliche Problem antreibt.

Was sich übertragen lässt, ist die *Taxonomie* — die Fehlermodi selbst, benannt und strukturiert durch fünfzig Jahre empirischer Arbeit. Und die *diagnostische Instrumentierung* — Janis' acht Symptome lassen sich plausibel als token-level Übereinstimmungsgeschwindigkeit, Meinungsdivergenzzerfall und konfidenz-asymmetrische Antworten auf das Argumentieren der Peers operationalisieren. Das sind Beobachtungswerkzeuge, keine Lösungen, aber sie erlauben uns, schärfer zu messen, was geschieht, als wenn wir bei Null anfingen.

## Was also tatsächlich tun

Aus dem Ganzen folgt eine praktische Implikation, und sie ist etwas ernüchternd.

Die Standardpolitik für eine LLM-Anwendung sollte *Einzel-Agent plus Werkzeugnutzung* sein. Eine Multi-Agent-Zerlegung sollte nur gerechtfertigt sein, wenn das Problem wirklich partitionierbar ist, jede Teilaufgabe unabhängig verifizierbar ist und der Koordinationsaufwand begrenzt bleibt. Empirische Vergleiche berichten, dass Multi-Agent-Systeme in dokumentierten Fällen etwa das 3,5-fache an Tokens vergleichbarer Einzel-Agent-Setups verbrauchen, mit 86 % Token-Duplikation in flachen Topologien — und dass die Leistung bei Aufgaben, die strikt sequentielles Schließen erfordern, um 39–70 % einbrechen kann, weil der Kommunikations-Overhead das Schließen fragmentiert.[^7] Multi-Agent ist nicht umsonst, und es ist nicht immer besser.

Wenn man Agenten doch zusammensetzt, lautet die Lektion der Organisationstheorie: *Modell-II/III-Fehlermodi instrumentieren*, nicht Modell I voraussetzen. Achte auf Sub-Agenten, die ihre vortrainierten Routinen ohne Rücksicht auf die Intention des Orchestrators feuern. Achte auf Vollendungsbelohnungen, die Kohärenz übersteuern. Die diagnostische Frage lautet nicht "haben sie sich geeinigt?" — sondern "**einigen sie sich, weil sie recht haben, oder weil sie vollenden?**".

Ich finde das auf eine bestimmte Weise beunruhigend. Einzel-Agent-LLMs sind produktiv, weil sie Mehrdeutigkeit autonom auffüllen. Wir loben sie dafür. Doch genau dieselbe Eigenschaft ist *die* dominante Fehlerursache, sobald wir sie zur Kooperation auffordern. Es gibt keine Version von "das Modell weniger autonom tunen", die nicht zugleich den Einzel-Agent-Fall beschädigt. **Pathologie und Wert teilen einen Mechanismus.** Die Topologie der Bereitstellung, nicht das Modell, entscheidet, welche von beiden wir bekommen.

Die Frage, die zu stellen sich lohnt, lautet: Wird das Feld dies akzeptieren und entsprechend gestalten — Einzel-Agenten als Voreinstellung, Komposition nur unter Zwang —, oder ist die Anziehungskraft des "Agenten-Schwarm"-Framings zu stark, um ihr zu widerstehen? Meine Vermutung ist Letzteres. Die Systeme werden mehr Multi-Agent werden, bevor sie weniger werden, und die Ausfallraten werden schlimmer werden, bevor das institutionelle Gedächtnis aufholt. Ich hoffe, ich irre mich.

---

[^1]: Cemri, M. et al. "[Why Do Multi-Agent LLM Systems Fail?](https://arxiv.org/abs/2503.13657)" arXiv:2503.13657 (2025). Accessed 2026-05-21.
[^2]: MAST GitHub. "[multi-agent-systems-failure-taxonomy/MAST](https://github.com/multi-agent-systems-failure-taxonomy/MAST)." Accessed 2026-05-21.
[^3]: Han, B. et al. "[Can LLM Agents Really Debate? A Controlled Study of Multi-Agent Debate in Logical Reasoning](https://arxiv.org/html/2511.07784v1)." arXiv:2511.07784 (2025). Accessed 2026-05-21.
[^4]: Janis, I. *Victims of Groupthink: A Psychological Study of Foreign-Policy Decisions and Fiascoes* (Houghton Mifflin, 1972). Zusammenfassung: [Systems Thinking Alliance, "Eight symptoms of groupthink"](https://systemsthinkingalliance.org/unmasking-the-hidden-dangers-and-discovering-strategies-for-collaborative-success-in-todays-world/). Accessed 2026-05-21.
[^5]: Cohen, M.D., March, J.G., and Olsen, J.P. "[A Garbage Can Model of Organizational Choice](https://fbaum.unc.edu/teaching/articles/Cohen_March_Olsen_1972.pdf)." *Administrative Science Quarterly* 17(1), 1972. Accessed 2026-05-21.
[^6]: Allison, G. *Essence of Decision: Explaining the Cuban Missile Crisis* (Little, Brown, 1971). Überblick: [Wikipedia, "Essence of Decision"](https://en.wikipedia.org/wiki/Essence_of_Decision). Accessed 2026-05-21.
[^7]: Augment Code. "[Multi-Agent Cost Compounding: Why 3 Agents Cost 10x](https://www.augmentcode.com/guides/multi-agent-cost-compounding)." Accessed 2026-05-21. Vgl.: [Benchmarking Multi-Agent LLM Architectures (arXiv:2603.22651)](https://arxiv.org/html/2603.22651).
