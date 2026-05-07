---
layout: post
lang: de
title: "Zwei Schichten von Bio-Inspired ── Was echt ist, wenn Scheduler aus der Biologie borgen"
date: 2026-05-07
permalink: /de/:year/:month/:day/:title/
categories: [systems-programming, technology]
tags: [linux-kernel, sched_ext, bpf, bio-inspired, metaheuristics, scheduler]
---

In den letzten zwei Jahren hat die Linux-Kernel-Schedulerarbeit eine kleine Renaissance erlebt. Der Completely Fair Scheduler, der über ein Jahrzehnt lang fast jede Linux-Maschine gefahren hat, hat plötzlich Konkurrenz bekommen ── und ein Teil dieser Konkurrenz trägt Biologie auf dem Etikett. Es gibt Scheduler-Paper über Tissue P Systems, LSTM-Prediktoren und "Shallow Brain"-Architekturen. Wer nur einen flüchtigen Blick auf die Kernel-Mailinglisten wirft, könnte zum Schluss kommen, dass Betriebssysteme biologischer werden. Ich halte das nicht für die richtige Lesart.

Die Welle hat zwei Schichten, und sie zu vermischen ist leicht und teuer. Eine Schicht ist im strukturell ernsthaften Sinn bio-inspiriert. Die andere ist das, was Kenneth Sörensen in einem Aufsatz, der 2015 in *International Transactions in Operational Research* erschien, als metaphergetriebene Forschung kritisierte ── Algorithmen, deren biologisches Framing bei näherem Hinsehen auf die tatsächliche Implementierung verschwindet.[^1] Der größte Teil des Rauschens sitzt in der zweiten Schicht. Der größte Teil des Signals sitzt in der ersten. Und die Paper, die die meiste Aufmerksamkeit bekommen, befinden sich tendenziell auf der lauten Seite der Linie.

## Das Substrat, das angekommen ist

Die Schicht, die ich verteidigen möchte, ist die neue Fähigkeit des Kernels, Scheduling-Strategien als zur Laufzeit ladbare BPF-Programme aufzunehmen. Das Feature heißt sched_ext und wurde mit dem Release 6.12 in den Linux-Mainline-Kernel aufgenommen, den Linus Torvalds am 17. November 2024 als stable getaggt hat.[^2] Die Mechanik ist nüchtern, die Implikationen sind es nicht. Eine in BPF geschriebene und zu Bytecode kompilierte Scheduling-Strategie kann in einen laufenden Kernel geladen werden, ohne ihn neu zu bauen. Verhält sich die Strategie falsch ── etwa weil ein lauffähiger Task hängt, weil der geladene Scheduler ihn nicht dispatched ── erkennt der Kernel den Stall und wechselt automatisch zurück zum fair-class Scheduler.

Zwei Designentscheidungen machen diese Schicht ernst zu nehmen. Die erste: Der Kernel behält den Mechanismus, lässt aber die Strategie schwimmen. Das ist nicht bloß ingenieurmäßige Bequemlichkeit, sondern eine strukturelle Trennung, auf die sich Biologie ständig verlässt. Zellmembranen sind Substrat; die Moleküle, die sie passieren, sind Strategie. Das Substrat kodiert die Nachricht nicht. Die zweite: das Failsafe-Revert. Wenn eine Strategie scheitert, stürzt das System nicht ab und bleibt auch nicht hängen ── es fällt auf ein bekanntes, gutartiges Substrat zurück und läuft weiter. Lebende Systeme machen ständig etwas Analoges, und das hervorzuheben ist nichts Romantisches. Es ist dieselbe Art von Trennung, auf ein anderes Problem angewandt.

Ein Satz zur Geschichte. Die Kerninfrastruktur von sched_ext wurde von Tejun Heo bei Meta entwickelt. Einer der erfolgreichsten BPF-Scheduler darauf ── LAVD, kurz für "Latency-criticality Aware Virtual Deadline" ── wurde bei Igalia entwickelt, ursprünglich um Stutter im Spielbetrieb auf Valves Steam Deck zu reduzieren. Im Dezember 2025 stellten zwei Meta-Ingenieure auf der Linux Plumbers Conference in Tokio eine Anpassung von LAVD als Metas neuen Default-Fleet-Scheduler vor.[^3] Der Weg von einer Handheld-Spielekonsole zu Default-Werten in Rechenzentren ist die Umkehrung des üblichen Hyperscaler-zu-Konsument-Narrativs, und das verdient einen Moment.

## Warum ein Konsolen-Scheduler das Rechenzentrum gefressen hat

Konsolen-Gaming hat eine eigentümliche Eigenschaftskombination: Pro Zyklus ist es nicht enorm rechenintensiv, aber es ist gnadenlos empfindlich gegenüber Tail-Latency, weil Menschen es bemerken. Ein Frame, das 16 ms zu spät ankommt, ist ein Stutter, und Stutter werden in Reviews abgestraft. Das Steam Deck hat Scheduler-Arbeit genau darauf hin optimiert ── auf eine vorhersehbare, latenzbeschränkte Auslieferung auf einer Workload-Skala, die menschlich wahrnehmbar ist.

Rechenzentren mussten diese Art von Constraint lange nicht beachten. Ihre Workloads liefen im Dunkeln, hinter Schichten von Caching und Queueing, und "in menschlicher Zeit reaktiv" war eine Eigenschaft des Frontends, nicht des Schedulers. Das ändert sich. Sobald interaktive AI-Workloads ── LLM-Inferenz, Agent-Loops, alles, wo eine Person auf ein Token wartet ── die Flotte dominieren, wird Tail-Latency auf menschlicher Zeitskala zu einer Eigenschaft, die der Scheduler im Rechenzentrum selbst respektieren muss. Der Grund, warum ein Steam-Deck-Scheduler heute bei Meta läuft, ist, dass das Constraint, das ihn definierte ── dass Menschen es bemerken ── inzwischen auch ein Constraint von Meta ist.

## Die Schicht, in der die Metapher wohnt

Über dem Substrat sitzen die Algorithmen, und hier beginnt Sörensens Kritik zu greifen. Sörensen, der über kombinatorische Optimierung schrieb, beobachtete, dass das Feld in Methoden ertränkt wurde, die nach natürlichen Phänomenen benannt waren ── Bienenkolonien, Wasserströme, Harmoniesuche, Immunsysteme ── von denen die meisten sich in gewöhnliche Mathematik auflösten, sobald man sie sorgfältig aufschrieb. Die Biologie im Titel war eine Marketingschicht. Die Operationen waren gewichtete Summen und Matrixalgebra.

Dasselbe Muster wiederholt sich im Kernel-Scheduling. Ein arXiv-Paper von 2025 namens *KernelOracle* nutzt ein LSTM, um vorherzusagen, welchen Task der Completely Fair Scheduler als nächstes wählt. Der Autor, Sampanna Yashwant Kahu von Virginia Tech, ist über die Grenzen bewundernswert offen ── er positioniert die Arbeit als Machbarkeitsstudie, nicht als produktionsreifen Scheduler.[^4] Neuere Arbeiten in benachbarten Venues nutzen "Tissue P Systems" ── ein ursprünglich von Zellmembranen inspiriertes Modell ── als Rahmen für einen Scheduler. Geht man dem Algorithmus sorgfältig nach, stellt sich heraus, dass es Matrixalgebra über einer regulären Struktur ist, was in Ordnung ist, aber der Zellmembran-Teil ist eine Beschriftung.

Man kann fairerweise fragen, ob das schlimm ist. Manche Metaphern bezahlen sich selbst, indem sie eine nützliche formale Struktur nahelegen. Manche geben einem Paper bloß einen marktfähigen Aufhänger. Das Problem ist nicht, dass Forschende sich von der Biologie inspirieren lassen ── viele nützliche Methoden begannen als Metaphern. Das Problem ist, wenn die Metapher als Behauptung darüber stehen bleibt, was der Algorithmus *ist*. Wenn ein Scheduler als "neuromorph" beschrieben wird und die Implementierung ein ereignisgesteuerter Arbiter ist, den jeder, der an Echtzeitsystemen arbeitet, ohne an Neuronen zu denken geschrieben hätte, dann ist die Biologie Dekoration.

## Eine Faustregel, die die Platzierung erklärt

Es gibt einen strukturellen Grund, warum biologisch gefärbte ML-Scheduler immer wieder in denselben Teilen des Kernels landen. *KernelOracle* macht seine Vorhersagen offline, im Nachhinein, weil Online-Inferenz nicht mit der Rate mithalten kann, in der der Kernel Entscheidungen treffen muss. Jim Huangs Machine-Learning-basierter Load Balancer, vorgestellt auf der OSS-NA im Juni 2025 und im Juli von LWN aufgegriffen, funktioniert genau deshalb, weil Load Balancing in einer gröberen Kadenz läuft ── Millisekunden bis Sekunden, nicht Mikrosekunden.[^5] In dieser Kadenz lässt sich die Inferenzlatenz eines neuronalen Netzes amortisieren.

Die Regel verallgemeinert sich. ML- und bio-inspirierte Heuristiken kolonisieren tendenziell genau die Teile des Kernels, in denen Entscheidungen auf langsamen Zeitskalen getroffen werden können: Load Balancing, Frequenz-Governors, Energiemodell-Tuning. Aus den Stellen, an denen Entscheidungen mit der Geschwindigkeit der CPU-eigenen Schaltvorgänge fallen müssen, werden sie strukturell verdrängt. Das ist kein vorübergehender Zustand, den bessere Hardware beheben wird. Es ist eine Eigenschaft der Zeithierarchie, in der Scheduling lebt.

## Was meiner Ansicht nach wirklich beobachtenswert ist

Die interessante Geschichte im Kernel-Scheduling ist nicht, dass es biologisch wird. Sie lautet, dass der Kernel zum ersten Mal seit Jahrzehnten ein Substrat akzeptiert hat, das Experimentieren ohne Neubau erlaubt. Dieses Substrat hat zufällig dieselbe abstrakte Form, mit der lebende Systeme Strategie und Versagen behandeln ── trennbarer Mechanismus, reversible Fehlermodi, Veränderbarkeit zur Laufzeit ── und diese Form leistet echte Arbeit.

Die Frage, die ich interessanter finde als jeden konkreten Scheduler, ist, wer sonst auf diesem Substrat reiten darf. Die nächste Welle, die ich für bedeutend halte, ist sched_ext in Rust ── neben einem Rust-for-Linux-Effort, der bereits in Gerätetreiber vordringt. Die beiden kommen aus verschiedenen Richtungen, und die Schicht, in der sie zusammentreffen, ist genau jene, die Linux bis 2024 nicht hatte. Dieser Treffpunkt ── nicht das jüngste Paper mit einem LSTM im Titel ── ist die Stelle, an der ich nach dem nächsten Schritt suchen würde.

---

[^1]: Sörensen, K. ["Metaheuristics—the metaphor exposed"](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001). *International Transactions in Operational Research* 22(1), 3–18, 2015. Accessed 2026-05-07.
[^2]: Phoronix. ["Sched_ext Merged For Linux 6.12 — Scheduling Policies As BPF Programs"](https://www.phoronix.com/news/Linux-6.12-Lands-sched-ext). Accessed 2026-05-07.
[^3]: Dai, D. & Newton, R. ["LAVD: Meta's New Default Scheduler"](https://lpc.events/event/19/contributions/2099/attachments/1875/4020/lpc-2025-lavd-meta.pdf). Linux Plumbers Conference 2025, Tokyo. Accessed 2026-05-07.
[^4]: Kahu, S. Y. ["KernelOracle: Predicting the Linux Scheduler's Next Move with Deep Learning"](https://arxiv.org/abs/2505.15213). arXiv:2505.15213, 21 May 2025. Accessed 2026-05-07.
[^5]: LWN. ["Improved load balancing with machine learning"](https://lwn.net/Articles/1027096/). 1 July 2025. Accessed 2026-05-07.
