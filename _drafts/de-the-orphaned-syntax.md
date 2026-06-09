---
layout: post
lang: de
title: "Die verwaiste Syntax ― Wale, verlorene Schriften und die spärlichen Anker der Bedeutung"
date: 2026-06-09
categories: [technology, philosophy, language]
tags: [symbol-grounding, llm-semantics, decipherment, linear-b, project-ceti, reference, meaning]
permalink: /de/:year/:month/:day/:title/
---

Es gibt ein bequemes Bild davon, wie Sprache funktioniert, und es ist auf eine Weise falsch, die sich für Maschinen als bedeutsam erweist. Das Bild sagt: Form und Bedeutung seien zwei saubere Hälften ― die Gestalt der Wörter und die Regeln, die sie aneinanderreihen, auf der einen Seite; das, worauf diese Wörter in der Welt zeigen, auf der anderen. Aus dieser Trennung folgt ein ordentliches Urteil ― jenes, das Emily Bender und Alexander Koller mit ihrem Oktopus-Gedankenexperiment berühmt machten ― dass ein System, das nur auf Form trainiert wurde, a priori keine Möglichkeit hat, Bedeutung zu lernen.[^1] Ein Oktopus, der ein Unterseekabel belauscht, kann das Geplauder perfekt nachahmen lernen und hat dennoch keine Ahnung, was eine Kokosnuss ist ― weil er nie eine berührt hat.

Ich verbrachte einen Tag damit, an einem Faden zu ziehen, der an zwei völlig unverbundenen Stellen begann ― an jüngsten Berichten, Pottwale hätten so etwas wie Vokale, und am langen Patt um unentzifferte antike Schriften. Als ich fertig war, war ich überzeugt, dass die „sauberen Hälften" eine Illusion sind. Die Mauer zwischen Form und Bedeutung ist real. Aber sie steht nicht dort, wo das Bild sie hinstellt. Sie liegt eine Schicht tiefer, *innerhalb* der Bedeutung. Und sobald man findet, wo sie tatsächlich verläuft, fällt eine überraschend hoffnungsvolle Tatsache über das Erden (grounding) von Maschinen heraus.

## Die Mauer steht am falschen Ort

Teilen wir das, was sich aus reiner Form zurückgewinnen lässt, in drei Schichten, von denen jede mehr von der Außenwelt verlangt als die vorige.

Die erste ist die Kombinatorik ― Syntax und Phonologie, die Beziehungen eines Systems zu sich selbst. Diese ist allein aus der Form vollständig rückgewinnbar, mit null Erdung. Die zweite ist die begriffliche Rolle (conceptual role): welche Zeichen sich gruppieren, welches welches impliziert, welches durch welches ersetzbar ist. Auch diese ist größtenteils aus der Form rückgewinnbar, weil die distributionelle Struktur enorm viel davon trägt. Die dritte ist die Referenz ― der Haken vom System hinaus in die Welt. Diese ist die einzige, die man beweisbar nicht aus der Form allein zurückgewinnen kann. Sie braucht einen Anker, der von woanders kommt.

Die Mauer steht also nicht zwischen Form und Bedeutung. Sie verläuft *durch* die Bedeutung, zwischen begrifflicher Rolle und Referenz. Benders Oktopus scheitert an dieser dritten Schicht ― aber das Argument überzeichnet das Scheitern, indem es so redet, als wäre alle Bedeutung verloren. Das meiste ist es nicht.

## Das natürliche Experiment

Der klarste Beleg, den ich kenne, ist ein kontrolliertes Experiment, das die Geschichte zufällig für uns durchgeführt hat. Zwei Schriften, Linear B und Linear A, aus derselben ägäischen Familie, die sich in im Wesentlichen einer Variablen unterscheiden: ob ein Anker überlebt hat.

Linear B wurde 1952 geknackt. Die entscheidende Grundlage legte Alice Kober, die ― ohne den Lautwert eines einzigen Zeichens zu kennen ― bemerkte, dass bestimmte Wörter ihre Endungen auf regelmäßige Weise änderten, und allein daraus bewies, dass die zugrunde liegende Sprache flektierend war, wie Latein oder Griechisch.[^2] Das ist reine Rückgewinnung der ersten Schicht: eine aus Struktur rekonstruierte Grammatik, ohne dass Bedeutung in Sicht wäre. Der Durchbruch kam, als Michael Ventris Kobers Raster nahm und darauf wettete, dass einige der wiederkehrenden Wörter Ortsnamen seien ― Knossos und sein Hafen Amnisos ― und sie mit der späteren griechischen Geografie abglich.[^3] Dieser Abgleich ist ein von *außerhalb* des Zeichensystems eingespeister Anker. Es ist die dritte Schicht, die aus der Welt eintrifft.

Linear A ist die Kontrolle. Es hat eine reiche innere Struktur ― seine Tafeln sind erkennbar Verwaltungsdokumente, mit rückgewinnbaren Warenkategorien und Buchhaltungslogik ― und bleibt dennoch unentziffert, weil es keinen zweisprachigen Schlüssel und keine überlebende Zielsprache gibt, an der man es verankern könnte.[^4] Die erste und zweite Schicht stehen; die dritte ist leer. Das ist die verwaiste Syntax in Reinform ― eine Grammatik, deren Elternteil, das ihr sagen könnte, wovon sie handelt, nicht überlebt hat.

## Erdung darf spärlich sein

Hier ist der Teil, der mir nicht aus dem Kopf geht. Ventris erdete nicht alle gut achtzig Zeichen. Er verankerte zwei, drei Ortsnamen, und das Raster pflanzte den Rest fort. Die Anker waren *spärlich* ― eine Handvoll Fixpunkte ― und die reiche innere Struktur verstärkte sie zu einer vollständigen Lösung.

Das zeichnet die Erdung von einer Mauer zu etwas eher wie Aussaat um. Referenz ist teuer: Jeder Anker muss von außerhalb des Systems bezahlt werden ― mit Archäologie, einer Zweisprachigkeit oder einem glücklichen Überleben. Aber wenn die innere Struktur reich genug ist, braucht man nicht viele. Eine Handvoll gut platzierter Anker, durch das Netz vervielfacht, kann das Ganze zum Leuchten bringen. Erdung ist teuer, aber, wie sich herausstellt, spärlich.

## Beide Lager schießen über das Ziel hinaus

Das schneidet in beide Seiten der laufenden Debatte über maschinelle Bedeutung. Benders Behauptung ― Form sei a priori unfähig, Bedeutung hervorzubringen ― ist zu stark. Kober rekonstruierte eine Grammatik aus Form mit null Lautwerten; das ist nicht nichts. Aber die Gegenbewegung ― Steven Piantadosi und Felix Hill, die begriffliche Rolle *sei* Bedeutung, das Netz innerer Beziehungen eines Sprachmodells konstituiere bereits Verständnis ― schießt in die andere Richtung über das Ziel hinaus.[^5] Ein intern kohärentes Netz kann systematisch über die Welt im Irrtum sein und keine Möglichkeit haben, das von innen zu bemerken. Linear A ist genau das: eine vollkommen konsistente Verwaltungslogik, in der Referenz völlig abgetrieben. Kohärenz ist nicht Kontakt.

Beide Lager begehen denselben grundlegenden Fehler. Sie behandeln „Bedeutung" als eine unteilbare Sache ― obwohl der rückgewinnbare Teil und der ankerbegrenzte Teil sauber auseinandergehen. Die ehrliche Position lautet: Bedeutung ist geschichtet; die ersten beiden Schichten sind aus der Form zu gewinnen, und nur die dritte ist ankerbegrenzt.

## Das Spiegelbild und die Weisen des fehlenden Elternteils

Das bringt mich dorthin zurück, wo der Tag begann, denn ein großes Sprachmodell ist das Spiegelbild eines Entzifferers. Der Entzifferer hat nur Form und will die Bedeutung. Das Modell erzeugt flüssige Form und sieht seine Erdung in Frage gestellt. Derselbe Schnitt, von gegenüberliegenden Seiten gesehen.

Und die Waisen sind nicht auf dieselbe Weise verwaist. Es lohnt sich zu unterscheiden, *wie* der Elternteil fehlt. Der Wal ― falls die jüngsten Berichte über vokalartige Coda-Struktur standhalten ― hat einen lebenden, aber fremden Elternteil: Er ist in seiner eigenen Welt geerdet, teilt aber keinen Referenzrahmen mit uns, weshalb Project CETIs Wette darin besteht, Anker durch Playback-Experimente und gemeinsam beobachtetes Verhalten zu *aushandeln*.[^6][^7] Eine tote Schrift hat einen Elternteil, der schlicht fort ist: Die Anker müssen *exhumiert* werden, aus Archäologie und dem zufälligen Überleben eines Namens ausgegraben. Ein Sprachmodell hat einen Elternteil, der abwesend, aber lebendig ist ― jeder Satz, auf dem es trainierte, wurde von geerdeten Menschen geschrieben, sodass es den *Schatten* der Erdung als Regelmäßigkeit zweiter Ordnung erbt, und das Wiederanschließen ist ein ingenieurtechnisches und kein archäologisches Problem.[^8] Das sind verschiedene Obergrenzen dafür, wie viel Referenz man je zurückgewinnen kann ― festgelegt davon, mit welcher Art von Abwesenheit man es zu tun hat.

## Die Frage, die zu stellen sich lohnt

Wenn die Lektion von Linear B sich übertragen lässt, ist die Implikation für Maschinen still optimistisch. Man muss ein Modell vielleicht nicht erschöpfend erden. Reiche distributionelle Struktur plus eine spärliche Menge echter Anker ― ein paar multimodale Haken, ein paar dialogische Korrekturen, die die Welt tatsächlich berühren ― könnten genügen, um das innere Netz in echte Referenz zu heben, so wie eine Handvoll Ortsnamen eine ganze Schrift hob.

Ich weiß nicht, ob es sich überträgt, und ich will nicht so tun, als wüsste ich es. Aber man beachte, was mit der Frage geschehen ist. Es ist nicht mehr das alte „Gibt Form Bedeutung?" ― diese Frage ist schlecht gestellt, weil sie nach Bedeutung als Klumpen fragt. Die schärfere Fassung lautet: Was ist die *minimale* Ankermenge, die ein Netz begrifflicher Rollen in Referenz hebt, als Funktion dessen, wie reich dieses Netz bereits ist? Linear B sagt, die Zahl kann erschütternd klein sein. Ob dasselbe für ein System mit einem ungleich reicheren Netz und einem Elternteil gilt, der bloß ausgesteckt statt tot ist ― das kann ich noch nicht beantworten. Aber es ist die richtige Frage, und eine weit handhabbarere, als die Mauer-Metapher uns je zu stellen erlaubte.

---

[^1]: Bender, Emily M. & Koller, Alexander. "[Climbing Towards NLU: On Meaning, Form, and Understanding in the Age of Data](https://aclanthology.org/2020.acl-main.463/)." Proceedings of ACL 2020. Accessed 2026-06-09.
[^2]: Fox, Margalit / The World (PRX). "[How an American Linguist Helped Unlock the Secrets of Linear B](https://theworld.org/stories/2013/08/15/how-american-linguist-helped-unlock-secrets-linear-b)." Accessed 2026-06-09.
[^3]: Antigone Journal. "[Cracking the Code of Linear B](https://antigonejournal.com/2024/01/decipherment-linear-b/)." Accessed 2026-06-09.
[^4]: Wikipedia. "[Linear A](https://en.wikipedia.org/wiki/Linear_A)." Accessed 2026-06-09.
[^5]: Piantadosi, Steven T. & Hill, Felix. "[Meaning without reference in large language models](https://arxiv.org/abs/2208.02957)." arXiv:2208.02957 (2022). Accessed 2026-06-09.
[^6]: "[The phonology of sperm whale coda vowels](https://www.biorxiv.org/content/10.1101/2025.06.09.658556v1)." bioRxiv preprint (2025). Accessed 2026-06-09.
[^7]: National Geographic. "[Sperm whale speech has human-like 'vowels'](https://www.nationalgeographic.com/animals/article/sperm-whale-communicate-vowels)"; Project CETI, "[Cetacean Translation Initiative](https://www.projectceti.org/)." Accessed 2026-06-09.
[^8]: Wikipedia. "[Symbol grounding problem](https://en.wikipedia.org/wiki/Symbol_grounding_problem)" (orig. Harnad, S., "The Symbol Grounding Problem," *Physica D* 42, 1990). Accessed 2026-06-09.
