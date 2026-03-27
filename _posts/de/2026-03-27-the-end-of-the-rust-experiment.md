---
layout: post
lang: de
title: "Das Ende des Rust-Experiments: Wenn Infrastruktur sich zur Evolution entscheidet"
date: 2026-03-27
categories: [systems-programming]
tags: [rust, linux-kernel, memory-safety, community, infrastructure]
permalink: /de/:year/:month/:day/:title/
---

Das Rust-Experiment im Linux-Kernel ist vorbei — nicht weil es gescheitert ist, sondern weil es erfolgreich war. Beim Kernel Maintainer Summit 2025 in Tokio erreichten die versammelten Maintainer einen Konsens: Rust ist nicht mehr experimentell. Es ist ein permanenter Bestandteil des Kernels, und die Entscheidung kam mit „null Widerstand".[^1]

Dies ist mehr als ein technischer Meilenstein. Es ist eine Fallstudie darüber, wie konservative Gemeinschaften sich entscheiden, ihre Grundlagen zu ändern — und was es braucht, damit Beweise Tradition überwinden.

## Die Beweise, die die Frage erzwangen

Das Argument für Speichersicherheit in Systemcode hat sich über Jahre aufgebaut. Microsoft hat berichtet, dass etwa 70% der jährlich zugewiesenen CVEs auf Speichersicherheitsprobleme zurückgehen — Pufferüberläufe, Use-after-Free, Double-Free und ähnliche Bugs, die speichersichere Sprachen zur Compile-Zeit strukturell verhindern.[^2] Während Linux-Kernel-spezifische Zahlen je nach Methodik variieren, hält das Muster: Die dominierende Klasse von Sicherheitslücken in C-Codebasen ist genau die Klasse, die Rusts Ownership-Modell eliminiert.

Was die Kernel-Community über theoretische Argumente hinaus bewegte, war der Produktionsbeweis. Android-16-Geräte mit dem 6.12-Kernel werden mit ashmem ausgeliefert — einem vollständig in Rust neugeschriebenen anonymen Shared-Memory-Allocator — was bedeutet, dass Millionen von Verbrauchergeräten bereits Rust-Code in ihren Kernels in Produktion ausführen.[^3] Der Nova-GPU-Treiber, ein Rust-basierter Nachfolger des Nouveau-Treibers für NVIDIA Turing und neuere GPUs, wurde im Mai 2025 als erster Rust-geschriebener DRM-Treiber in den Mainline-Kernel Linux 6.15 aufgenommen, wenn auch noch in frühem Entwicklungsstadium.[^4] Wie Greg Kroah-Hartman während des Summits feststellte, erwiesen sich in Rust geschriebene Treiber als sicherer als ihre C-Gegenstücke.[^1]

Dies sind keine Machbarkeitsstudien. Es ist Produktionscode, der auf realer Hardware läuft und von realen Maintainern geprüft wurde.

## Das konservative Dilemma

Was diese Geschichte fesselnd macht, sind nicht die technischen Vorzüge von Rust — die wurden ausgiebig diskutiert. Die interessante Frage ist, wie eine zutiefst konservative Gemeinschaft sich entschied, etwas fundamental Neues zu übernehmen.

Die Linux-Kernel-Community ist aus guten Gründen konservativ. Stabilität ist keine Präferenz; sie ist eine moralische Pflicht, wenn Code auf medizinischen Geräten, Finanzsystemen und kritischer Infrastruktur läuft. Die Kosten eines Kernel-Bugs werden nicht in Unannehmlichkeiten gemessen, sondern in potenziellem Schaden. Jede neue Abstraktionsschicht ist eine mögliche Fehlerquelle. Jedes unbekannte Muster ist eine Wartungslast. Jede neue Sprache birgt das Risiko, die Contributor-Basis zu spalten.

Dieser Konservatismus schafft ein Paradoxon. Die Gemeinschaft, die Speichersicherheit am dringendsten braucht, ist auch die Gemeinschaft, die der dafür nötigen Disruption am stärksten widersteht.

Und doch häuften sich die Daten weiter an. Irgendwann *wird* die konservative Wahl zur Veränderung — weil der Status quo nachweislich gefährlicher ist als die Alternative. Wenn 70% der Sicherheitslücken in großen C-Codebasen in eine Kategorie fallen, die eine andere Sprache strukturell verhindert, ist das Festhalten am Status quo nicht mehr die vorsichtige Option. Es ist die riskante.

## Was die Meinungen änderte

Es war nicht Evangelismus. Die Rust-for-Linux-Community lernte früh, dass Begeisterung ohne Produktionscode nur Lärm ist. Was Meinungen änderte, war das Ausliefern — echter Code, in echten Subsystemen, geprüft von etablierten Maintainern.

Hier gibt es eine Lektion, die über Systemprogrammierung hinausgeht. Paradigmenwechsel in etablierten Gemeinschaften geschehen nicht durch Argumentation. Sie geschehen durch Demonstration — dadurch, dass jemand die Arbeit macht und die Ergebnisse für sich sprechen lässt.

Die Rust-for-Linux-Beitragenden argumentierten nicht bloß, dass Rust in den Kernel gehört. Sie schrieben Treiber, reichten Patches ein, ertrugen feindliche Mailinglisten-Threads und lieferten funktionierenden Code aus. Der Code selbst wurde zum Argument.

## Die Ethik der Infrastrukturwartung

Hier stellt sich eine tiefere Frage zur moralischen Verantwortung der Infrastrukturwartung. Wenn bekannt ist, dass eine Klasse von Schwachstellen strukturell vermeidbar ist, und die Werkzeuge zu ihrer Vermeidung existieren und in der Produktion demonstriert wurden, welche Verantwortung folgt daraus, wenn diese Schwachstellen ausgenutzt werden?

Dies ist nicht hypothetisch. Speichersicherheits-Bugs im Kernel haben zu Privilege-Escalation-Exploits geführt, die in echten Angriffen eingesetzt wurden. Als die Kernel-Community beschloss, Rust permanent zu machen, lag darin ein implizites Eingeständnis: Das fortgesetzte alleinige Vertrauen auf C trägt angesichts des jetzigen Wissenstands ein moralisches Gewicht.

Das bedeutet nicht, dass C „schlecht" ist oder dass jeder Kernel-Entwickler Rust lernen muss. Es bedeutet, dass *die Gemeinschaft als Ganzes* eine Verantwortung erkannt hat, ihre Werkzeuge weiterzuentwickeln, wenn die Beweislage es erfordert. Diese Erkenntnis — die Bereitschaft, Daten Tradition überschreiben zu lassen — macht diese Entscheidung bemerkenswert.

## Welleneffekte

Die Auswirkungen gehen über den Kernel hinaus. Debian wird ab Mai 2026 eine Rust-Toolchain als harte Abhängigkeit für APT vorschreiben, was Legacy-Architektur-Ports ohne Rust-Unterstützung betrifft.[^5] Die Frage lautet nicht mehr „ob", sondern „wie schnell".

Die interessante offene Frage ist, ob sich dieses Muster — konservative Gemeinschaft, sich ansammelnde Sicherheitsbeweise, schrittweise Demonstration, schließliche Übernahme — bei anderen Paradigmenwechseln wiederholen wird. Formale Verifikation? Speichersichere Nachfolger jenseits von Rust? Die Reise des Kernels könnte zur Vorlage dafür werden, wie kritische Infrastruktur sich entwickelt.

Das experimentelle Etikett ist weg. Das Experiment ist vorbei. Die Arbeit geht weiter.

---

## References

[^1]: DevClass. "[Rust boosted by permanent adoption for Linux kernel code.](https://devclass.com/2025/12/15/rust-boosted-by-permanent-adoption-for-linux-kernel-code/)" Accessed 2026-03-27.
[^2]: Microsoft Security Response Center. "[A proactive approach to more secure code.](https://msrc.microsoft.com/blog/2019/07/a-proactive-approach-to-more-secure-code/)" Accessed 2026-03-27.
[^3]: Rust for Linux. "[Android ashmem.](https://rust-for-linux.com/android-%60ashmem%60)" Accessed 2026-03-27.
[^4]: Phoronix. "[Rust-Written NOVA Open-Source NVIDIA Driver Being Further Built Out In Linux 6.17.](https://www.phoronix.com/news/Linux-6.17-NOVA-Driver)" Accessed 2026-03-27.
[^5]: LWN.net. "[Debian to require Rust as of May 2026.](https://lwn.net/Articles/1044496/)" Accessed 2026-03-27.
