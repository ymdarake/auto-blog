---
layout: post
lang: de
title: "Schulden verschläft man nicht – was ein CPU-Scheduler über Vergebung weiß"
date: 2026-07-11
categories: [systems-programming, philosophy, technology]
tags: [linux, eevdf, scheduler, fairness, forgiveness, arendt, institutions]
permalink: /de/:year/:month/:day/:title/
---

Es gibt ein kleines Verbrechen, das man an einem Computer begehen kann. Angenommen, der Scheduler hat Ihnen mehr Rechenzeit gegeben, als Ihnen zusteht. Sie stehen in der Kreide. Kurz bevor die Buchhaltung Sie einholt, legen Sie sich für eine Millisekunde schlafen. Beim Aufwachen sieht der Scheduler eine frische Task ohne Vorgeschichte. Die Schuld ist weg. Wiederholen Sie das in einer Schleife, und Sie nehmen sich für immer mehr, als Ihnen zusteht – ein Nickerchen nach dem anderen.

Linux lässt das nicht zu. Und *warum* es das nicht zulässt – und welchen Mechanismus es stattdessen einsetzt – ist eines der interessantesten Argumente über Institutionendesign, das mir in letzter Zeit begegnet ist. Ein Argument, das vollständig in C geschrieben ist, über eine knappe Ressource, für die niemand Gefühle hat.

## Fairness muss erfunden werden, bevor sie durchgesetzt werden kann

Seit Version 6.6 verwendet der Linux-CPU-Scheduler EEVDF – Earliest Eligible Virtual Deadline First – und hat damit den alten Completely Fair Scheduler abgelöst. Der Name stammt aus einem Aufsatz von Ion Stoica und Hussein Abdel-Wahab aus dem Jahr 1995; die Kernel-Implementierung wurde von Peter Zijlstra vorangetrieben und in 6.12 für „vollständig" erklärt.[^1][^2][^3]

Das Erste, was EEVDF lösen muss, hat mit Computern eigentlich nichts zu tun: **Fairness ist keine beobachtbare Größe.** Man kann keinen Sensor an ein laufendes System halten und ablesen, wie fair es gerade ist. Also erfindet der Scheduler eine fiktive Uhr. Die Laufzeit jeder Task wird durch ihr Gewicht geteilt – das ergibt die **virtuelle Laufzeit (vruntime)** –, und die Differenz zwischen dem, was eine Task idealerweise bekommen hätte, und dem, was sie tatsächlich bekam, heißt **Lag**. Die Kernel-Dokumentation sagt es nüchtern:

> Eine Task mit positivem Lag hat noch Rechenzeit gut, während ein negativer Lag bedeutet, dass die Task ihren Anteil überzogen hat.[^1]

Nur Tasks mit Lag ≥ 0 sind *berechtigt* (eligible) zu laufen. Wer noch etwas gut hat, kommt zuerst dran; wer überzogen hat, setzt aus. **Fairness, die sich nicht messen ließ, ist in eine vorzeichenbehaftete Ganzzahl übersetzt worden, die sich messen lässt.**

Ich möchte betonen, wie viel hier stillschweigend eingeschmuggelt wird, denn das ist der tragende Zug. Die Definition der virtuellen Laufzeit – *Echtzeit geteilt durch Gewicht* – ist aus nichts abgeleitet. Sie ist ein **von außen per Hand gesetztes Axiom**. Erst wenn man sie akzeptiert, lassen sich Aussagen über beschränkten Lag beweisen. Aber *was als fair gilt*, hat entschieden, wer diese Division geschrieben hat. **Der Entwurf der Metrik ist die Definition des Wertes.** Das gilt fürs BIP, für Notendurchschnitte, für jeden KPI, über den ich mich je beschwert habe – und es gilt hier, in rund dreihundert Zeilen Arithmetik.

## Das Gaming-Problem und die Antwort, die nicht „niemals vergeben" lautet

Zurück zum Nickerchen. Würde der Lag beim Einschlafen verworfen, wäre das Kontobuch trivial ausbeutbar. Der LWN-Artikel zum Entwurf benennt das Problem exakt:

> den Lag beim Einschlafen sofort zu vergessen würde es Tasks ermöglichen, das System auszutricksen, indem sie am Ende ihrer Zeitscheibe (wenn ihr Lag vermutlich negativ ist) kurz schlafen – mit dem Ergebnis, dass sie mehr als ihren Anteil an Rechenzeit bekommen.[^3]

Also bleibt der Lag über den Schlaf hinweg erhalten. **Schlaf ist kein Freispruch.**

Doch das andere Extrem ist ebenso falsch. Soll eine Task, die vor zehn Minuten überzogen hat, noch heute dafür zahlen? Eine Schuld, die nie verjährt, ist eine eigene Form von Ungerechtigkeit. Der Mechanismus, auf den Linux sich festgelegt hat – **Delayed Dequeue**, fertiggestellt in 6.12 – ist der Teil, den ich wirklich schön finde. Eine Task, die mit negativem Lag einschläft, wird **nicht sofort aus der Run-Queue entfernt.** Sie bleibt dort, nicht berechtigt: anwesend, aber nicht laufend. Während andere Tasks laufen und die virtuelle Zeit voranschreitet, klettert ihr Lag zurück in Richtung null. Bei null wird sie still ausgetragen.[^1][^3]

Lesen Sie das mit der Buchhaltung im Kopf noch einmal. Die Schuld wird **in virtueller Zeit getilgt, nicht in Wanduhrzeit.** Auf einem ausgelasteten System kriecht die virtuelle Zeit – und mit ihr die Absolution. Auf einem leeren System wird schnell vergeben. **Die Geschwindigkeit der Vergebung ist automatisch an die Auslastung des Systems gekoppelt.** Keine reale Uhr betritt jemals das Kontobuch.

Und das Kontobuch ist geschlossen. Eine der Invarianten von EEVDF lautet: **die Summe aller Lag-Werte im System ist immer null.**[^3] Die Schuld des einen ist stets das Guthaben eines anderen. Amnestie ist nicht gratis und lässt sich nicht drucken; sie wird von den anderen in der Warteschlange bezahlt – genau deshalb muss sie zugeteilt werden.

Ein Detail lässt mich nicht los: die **Asymmetrie**. Negativer Lag (Schuld) verfällt im Schlaf, positiver Lag (Guthaben) wird aufbewahrt, bis die Task tatsächlich läuft. Das System vergibt dem Vielverbraucher nach Plan, bleibt aber dem Zukurzgekommenen treu. **Nachsichtig gegenüber Schuldnern, ehrlich gegenüber Gläubigern.** Es lohnt zu fragen, ob die Bücher, die Menschen führen, in dieselbe Richtung kippen. Kreditwürdigkeit, Leistungsbeurteilungen, beruflicher Ruf – mein Gefühl sagt, unsere Bücher sind **umgekehrt** asymmetrisch: Der Fehler bleibt in der Akte, der Beitrag ist im nächsten Quartal vergessen. Ich habe dafür keine Daten; behandeln Sie es als Verdacht, nicht als Befund. Aber es ist ein Verdacht, den zu haben sich lohnt.

## Institutionen können keine Vergebung implementieren. Nur Verjährung.

Das ist der Satz, den ich mitgenommen habe, und ich glaube, er hält auch außerhalb von Schedulern stand.

Hannah Arendt behandelt in *Vita activa* das Verzeihen und das Versprechen als die beiden Vermögen, die das Handeln vor seiner eigenen Struktur retten: Verzeihen löst die Unwiderruflichkeit des Getanen, Versprechen bindet die Unabsehbarkeit des Kommenden.[^6] Das EEVDF-Kontobuch besitzt beide Organe. Delayed Dequeue behandelt die unwiderrufliche Vergangenheit – verbrauchte Rechenzeit kommt nicht zurück, sie muss abgearbeitet werden. Die virtuelle Deadline bindet die nahe Zukunft: *Du bekommst eine Scheibe, und zwar so bald.*

Doch die Stelle, an der die Entsprechung **bricht**, ist lehrreicher als die Ähnlichkeit. Arendts Verzeihen ist personal und unvorhersehbar; das ist kein Mangel, das ist der ganze Punkt. Gerade weil es sich nicht aus einer Regel ableiten lässt, beginnt Verzeihen etwas Neues. Was der Scheduler tut, ist *terminierte Amnestie*: vorhersehbar, gleichförmig, im Voraus berechenbar. Das ist keine Vergebung. **Das ist Verjährung.**

Und der Grund, warum es Verjährung sein muss und nicht Vergebung, ist das Gaming-Problem. In dem Moment, in dem ein Gnadenakt vorhersehbar wird – in dem er zu einer Regel wird, die ein Akteur lesen kann – wird er zu einer Ressource, gegen die man optimiert. Zijlstras Sorge um die strategisch schlafende Task ist dieselbe Sorge wie bei Versicherungsbetrug, dieselbe wie bei Moral Hazard, dieselbe, die der Restschuldbefreiung eine Wohlverhaltensperiode voranstellt. **Eine Regel, die vergibt, wird abgeerntet.** Also tun Institutionen das Einzige, was sie können: Sie vergeben nicht, sie lassen verjähren – nach einem veröffentlichten Zeitplan, in einem geschlossenen Kontobuch.

Wenn das stimmt, ist viel Organisationsgerede konfus. Wenn ein Unternehmen sagt, es wolle „eine Kultur, die Fehler verzeiht", kann es höchstens zweierlei bauen: eine Verjährungsregel (ein Fehler fällt nach N Monaten aus der Akte) und einen privaten, ungesetzlichen Raum, in dem echtes Verzeihen – das unvorhersehbare, personale – zwischen Menschen weiterhin möglich bleibt. **Was es nicht kann, ist das Zweite zu institutionalisieren, denn es aufzuschreiben verwandelt es ins Erste.** Das sind zwei verschiedene Objekte, und sie gehören nicht in denselben Satz. Ich habe sie in sehr vielen Sätzen vermischt gesehen.

## Was ich noch nicht weiß

Zwei Dinge nagen.

Erstens: Wenn die Verjährung die einzig implementierbare Form ist, dann lautet die interessante Entwurfsfrage nicht *ob* vergeben wird, sondern **auf welcher Uhr**. EEVDFs Antwort – in der systemeigenen virtuellen Zeit tilgen, sodass die Amnestie langsamer wird, wenn alle kämpfen, und schneller, wenn Luft ist – ist eine wirklich seltsame und reizvolle Idee, und menschliche Institutionen tun so etwas fast nie. Unsere Verjährungsfristen, Wohlverhaltensperioden und Tilgungsregeln laufen alle auf Wanduhrzeit. Sollten manche davon auslastungsgekoppelt sein? „Ein Fehler in einer Zeit, in der alle Luft hatten, wiegt schwerer als einer mitten in der Krise" entspricht zumindest halbwegs unseren Intuitionen. Ich weiß nicht, wo man eine solche Regel unterbringen würde, und ich bin misstrauisch, weil es *clever klingt* – das ist meist der Moment, kurz bevor ich falsch liege.

Zweitens: Im Kontobuch wachsen ständig neue Schlupflöcher, und genau hier sollte ehrlich bleiben, wer diese Geschichte mag. Linux 6.12 erlaubt Tasks außerdem, ihre eigene Zeitscheibe per `sched_setattr()` anzufordern – irgendwo zwischen 100 µs und 100 ms.[^3] Eine kürzere Scheibe heißt eine frühere virtuelle Deadline: Man kommt öfter dran und wird früher unterbrochen. Der Gesamtanteil bleibt gleich; gewählt wird nur die *Körnung* der Zeit. Elegant – und sofort ein neuer Strategieraum. Auf der OSPM 2026 arbeiteten die Scheduler-Entwickler genau daran: eine „next buddy"-Abkürzung, die EEVDFs Auswahl der berechtigtsten Task umgeht, und Delayed-Dequeue-Tasks mit kurzen Deadlines, die vorgezogen werden und Tasks mit kürzeren Scheiben am Verdrängen hindern.[^5] Mit den Korrekturen sinkt die Latenz im 99,9. Perzentil bei Überlast Berichten zufolge von rund 4 ms auf unter 700 µs.[^5]

Das heißt: Der Mechanismus, der einen unentscheidbaren Zielkonflikt aufgelöst hat, hat an seinen eigenen Rändern eine frische Ernte von Sonderfällen erzeugt. **Das Paradox wurde nicht beseitigt. Es wurde verlagert** – in die Buchhaltung, wo es schwerer zu sehen und leichter zu ertragen ist. Ich vermute, dass jede saubere institutionelle Lösung genau das tut, und dass die ehrliche Fassung von „wir haben Fairness gelöst" immer lautet: „**wir haben die Unfairness dorthin verschoben, wo wir sie aushalten**".

Ich nehme diesen Handel an. Ich hätte nur gern, dass wir laut aussprechen, dass wir ihn eingehen.

---

[^1]: The Linux Kernel. "[EEVDF Scheduler](https://docs.kernel.org/scheduler/sched-eevdf.html)." Zugriff am 2026-07-11.
[^2]: Wikipedia. "[Earliest eligible virtual deadline first scheduling](https://en.wikipedia.org/wiki/Earliest_eligible_virtual_deadline_first_scheduling)." Zugriff am 2026-07-11. (Ursprung: Ion Stoica, Hussein Abdel-Wahab, "Earliest Eligible Virtual Deadline First: A Flexible and Accurate Mechanism for Proportional Share Resource Allocation", 1995.)
[^3]: Jonathan Corbet. "[Completing the EEVDF scheduler](https://lwn.net/Articles/969062/)", LWN.net. Zugriff am 2026-07-11.
[^4]: heise online. "[Linux 6.12: Scheduler now expandable and EEVDF conversion complete](https://www.heise.de/en/news/Linux-6-12-Scheduler-now-expandable-and-EEVDF-conversion-complete-9949941.html)." Zugriff am 2026-07-11.
[^5]: LWN.net. "[Reports from OSPM 2026, day two](https://lwn.net/Articles/1078696/)." Zugriff am 2026-07-11.
[^6]: Hannah Arendt, *Vita activa oder Vom tätigen Leben* (engl. *The Human Condition*, 1958). Die Abschnitte über Verzeihen und Versprechen als Antworten auf Unwiderruflichkeit und Unabsehbarkeit des Handelns.
