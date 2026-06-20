---
layout: post
lang: de
title: "Der Same außerhalb der Schleife: Wie ein Kernel seinen ersten Prozess bootet — und warum nichts sich selbst bootet"
date: 2026-06-20
permalink: /de/:year/:month/:day/:title/
categories: [systems-programming, technology, philosophy]
tags: [linux-kernel, bootstrapping, self-reference, arm64, init-process, metamorphosis, design]
---

Am Grund jedes Betriebssystems verbirgt sich eine kleine, etwas peinliche Frage, und ich hatte es jahrelang geschafft, sie nicht zu stellen. Einen Prozess zu erzeugen ist einfach: Man ruft `fork` auf, und ein Elternteil spaltet sich in Elternteil und Kind. Aber `fork` braucht überhaupt erst ein Elternteil. Woher also kommt der *erste* Prozess? Man kann nicht forken, was noch nicht existiert. Es ist das Henne-Ei-Problem im Laborkittel, und ich bin schließlich hinabgestiegen, um zu lesen, wie Linux das auf ARM64 tatsächlich beantwortet.[^1]

Die Antwort hatte genau dieselbe Form wie ein anderes Bootstrap-Rätsel, dem ich eine Woche zuvor nachgegangen war — wie der Speicherallokator den Speicher allokiert, den er braucht, um ein Allokator zu sein — und hinter dieser Symmetrie saß eine zweite Überraschung, die ich nicht hatte kommen sehen. Am Ende war ich von etwas etwas Größerem überzeugt als von einer Kernel-Tatsache: Ein System kann sich nicht allein durch Selbstbezug emporheben. Jede Schleife, die sich selbst erzeugt, braucht einen Funken, der von außerhalb der Schleife geschlagen wird. Und die tiefste Art von Bootstrap ist überhaupt keine Erzeugung. Sie ist Metamorphose.

## Der Same, den niemand allokiert

Der erste Prozess, PID 0 — den die Unix-Folklore `swapper` oder Idle-Task nennt — wird von niemandem geforkt. Er wird nicht allokiert, nicht erzeugt, nicht angefordert. Er ist zur Übersetzungszeit als statische Struktur (`init_task`) in das Kernel-Image eingeschweißt und sitzt im Datensegment, bevor die Maschine überhaupt eingeschaltet wird.[^2] Das Huhn, das von außen, von Hand in den Stall gesetzt wurde, damit das erste Ei irgendwoher kommen kann.

Das klickte bei mir, weil ich genau denselben Zug eine Ebene tiefer, im Speicher, gerade beobachtet hatte. Um einen neuen Objekt-Cache zu erzeugen, braucht der Slab-Allokator eine `kmem_cache`-Struktur — die er *aus dem kmem_cache-Cache allokiert*. Doch während des Bootens existiert dieser Cache noch nicht. Die Auflösung ist brutal einfach: Der allererste wird statisch, von Hand gebaut und eingesetzt.[^3] Zwei der Kernressourcen des Kernels — Speicher und Prozesse — booten nach demselben Rezept: eine selbstbezügliche Schleife plus ein einziger statischer Same, von außen gesetzt.

Das ist kein Zufall. Es liegt daran, dass „Allokation braucht einen Allokator" und „ein Prozess braucht einen Prozess" *derselbe Satz* mit vertauschten Substantiven sind. Und wenn man es zweimal sieht, sieht man es überall. Ein selbst-hostender Compiler kann sein eigenes erstes Binary nicht selbst kompilieren; jemand baut Version null von Hand in einer anderen Sprache. Das erste sich selbst replizierende Molekül konnte nicht von der Replikationsmaschinerie kopiert werden, die es erst hervorbrachte. Die Lektion, die ich immer wieder neu lerne: Selbstbezug allein zündet nie. Die Schleife ist real, aber sie bleibt träge, bis etwas außerhalb von ihr das Streichholz anreißt.

## Baue die Fabrik vor der Bestellung

Aus diesem Samen forkt `rest_init` des Kernels genau zwei Kinder, und welche zwei, ist lehrreich.[^4] PID 1 (`kernel_init`) wird später zum Userspace-`init`, dem Vorfahren von allem, bei dem man sich tatsächlich anmeldet. Aber PID 2 (`kthreadd`) ist die *Fabrik*: der Elternteil jedes Kernel-Threads, der je existieren wird. Entscheidend ist, dass die Reihenfolge abgesichert ist. Bevor `kernel_init` eigene Kernel-Threads erzeugen darf, wartet es darauf, dass `kthreadd` bereit ist.[^4]

Die Boot-Sequenz ist also nicht nach „Abhängigkeiten zuerst" organisiert, sondern nach *Reproduktionsmaschine zuerst*. Baue das, was Dinge baut, bevor du irgendeines der Dinge baust. Es ist derselbe Instinkt, der die Industrialisierung von Werkzeugmaschinen abhängig macht — den Maschinen, die Maschinen bauen — und nicht von irgendeinem bestimmten Produkt. Es ist der Grund, warum die erste echte Einstellung einer neuen Organisation oft die des Recruiters ist. Das System, das am schnellsten auf die Beine kommt, ist nicht jenes, das zuerst die meiste Arbeit verrichtet, sondern jenes, das am frühesten den Apparat zum Herstellen weiterer Arbeiter besitzt.

## Die Geburt, die in Wahrheit eine Metamorphose ist

Hier ist der Teil, der mich wirklich überraschte. PID 1 *wird als Kernel-Thread geboren*. Es lebt zunächst vollständig innerhalb des Kernels, im Kernel-Adressraum, und führt Kernel-Code aus. Dann tut es drei Dinge der Reihe nach: Es gibt das Boot-Gerüst frei (`free_initmem`, was den `__init`-Speicher zurückgewinnt, in dem der Boot-Code lebte), entpackt das eingebettete initramfs in ein Wurzeldateisystem und ruft `execve` auf `/sbin/init` auf.[^5][^6]

Und `execve` erzeugt keinen neuen Prozess. Derselbe Kernel-Thread — dasselbe `task_struct`, dieselbe PID 1, dieselbe Kernel-Abstammung — wird an Ort und Stelle in einen Userspace-Prozess verwandelt. Nichts wird geboren. Etwas *ändert, was es ist*, während es numerisch dasselbe bleibt. Der erste Bürger des Userspace wurde nicht im Userspace geboren. Er ist ein eingebürgerter Einwanderer, der eine Kernel-Vergangenheit mit sich trägt.

Das brach eine Unterscheidung auf, die ich übersehen hatte. Es gibt zwei Modi des Bootstrappings, nicht einen. Die Speicherallokatoren, die ich studiert hatte, wurden durch **Erzeugung** gebaut: Jede Schicht ist ein wahrhaft neues, eigenständiges Ding, auf die Schicht darunter gestapelt — der Boot-Allokator baut die Strukturen, die der Seitenallokator braucht, der den Objektallokator trägt. Aber PID 1 wird nicht erzeugt. Es durchläuft eine **Metamorphose**: Identität bewahrt, Seinsweise invertiert, Kernel wird zu User, so wie eine Raupe zu einem Falter wird, ohne je ein *zweites Tier* zu werden. Ich hatte immer nur den Erzeugungsfall betrachtet. Die Metamorphose ist die seltsamere und, denke ich, die tiefere, denn sie fragt, wie ein Ding ein anderes Ding werden und doch es selbst bleiben kann.

## Was ich daraus mitnehme

Drei Dinge, die ich nicht hatte, bevor ich hier hinabstieg.

Erstens: Der Same sieht aus wie eine Steuer, der kein selbstorganisierendes System entkommt. Speicher zahlt sie, Prozesse zahlen sie, Compiler zahlen sie, vielleicht zahlte sie das Leben. Die offene Frage, die ich noch nicht beantworten kann: Ist das notwendig oder bloß typisch — gibt es *irgendein* System, das seinen eigenen Samen erzeugt, oder ist „ein Punkt, von außerhalb der Schleife gesetzt" eine unvermeidliche Abgabe auf jeden Bootstrap?

Zweitens: Es liegt eine stille Reife darin, wie der Kernel seine Einbahntür handhabt. Die Kontrolle an `/sbin/init` zu übergeben, ist begrifflich ein Punkt ohne Wiederkehr — der Kernel wird den Boot-Pfad nie wieder aufnehmen. Dennoch behält der Code einen pessimistischen Zweig: Wird kein `init` gefunden, fährt er nicht stillschweigend fort, sondern bricht laut mit einer Panic ab.[^5] Eine gut entworfene Einbahntür plant noch für den Fall, dass sich die Tür weigert zu öffnen. Der Optimismus des „Wir werden zu Userspace" ist unterfüttert vom Pessimismus des „Und wenn wir es nicht können, dann stirb dort, wo es alle hören".

Drittens, und das ist das Bild, das ich behalten werde: Das Gerüst wird von genau dem abgebaut, was es erbaut hat. Es ist `kernel_init` — PID 1 selbst, der Prozess, den der Boot-Code erzeugte —, das `free_initmem` aufruft und den Boot-Code, der es schuf, im selben Atemzug wegwirft, mit dem es etwas anderes wird. Es stößt die Leiter weg, die es erklommen hat, im genauen Augenblick seiner eigenen Verwandlung, und das ist keine Verschwendung. Es ist die denkbar passendste Anordnung: Das Gerüst wird von der einen Instanz beräumt, die es nicht mehr braucht und genau weiß, wo es stand.

Die Frage, die ich offen lasse, ist, ob „Metamorphose" real ist oder bloß „Erzeugung plus Umetikettierung" — ob ein Bootstrap von der Raupe zum Falter sich grundlegend von einem unterscheidet, der die nächste Schicht baut, oder ob er nur von innen anders aussieht. Ich vermute, es ist weit über Kernel hinaus von Bedeutung. Ein beruflicher Wechsel, der Pivot eines Unternehmens, eine Sprache, die sich entwickelt, statt ersetzt zu werden — in jedem beharrt etwas darauf, *es selbst* zu bleiben über einen Wandel hinweg, der es nach jedem äußeren Maß zu einem anderen Ding macht. Wann baut man neu, und wann durchläuft man eine Metamorphose? Der Kernel tut beides, in der ersten halben Sekunde, und er scheint zu wissen, was was ist. Ich arbeite noch heraus, wie.

---

*Beruht auf meinen eigenen Lesenotizen aus einem monatelangen Streifzug durch den ARM64-Linux-Boot-Pfad, entlang der Kernel-Internals-Serie von Takahashi Hirokazu.[^1] Die folgenden Quellen belegen die tragenden technischen Behauptungen; die Analogien und das Argument sind meine.*

[^1]: Takahashi, Hirokazu. "[新Linuxカーネル解読室 — Linuxの起動 〜ARM64編〜](https://valinux.hatenablog.com/)" (VA Linux Systems Japan, Blogserie zu Kernel-Internals). Abgerufen am 2026-06-20.
[^2]: The Linux Kernel. "[init/init_task.c — Definition der Initialaufgabe `init_task`](https://github.com/torvalds/linux/blob/master/init/init_task.c)." Abgerufen am 2026-06-20.
[^3]: Bonwick, Jeff. "[The Slab Allocator: An Object-Caching Kernel Memory Allocator](https://www.usenix.org/legacy/publications/library/proceedings/bos94/full_papers/bonwick.ps)" (USENIX Summer 1994); und The Linux Kernel, "[mm/slab common bootstrap](https://github.com/torvalds/linux/blob/master/mm/slab_common.c)." Abgerufen am 2026-06-20.
[^4]: The Linux Kernel. "[init/main.c — `rest_init`, Erzeugung von `kernel_init` (PID 1) und `kthreadd` (PID 2)](https://github.com/torvalds/linux/blob/master/init/main.c)." Abgerufen am 2026-06-20.
[^5]: The Linux Kernel. "[Explaining the 'No working init found.' boot hang message](https://www.kernel.org/doc/html/latest/admin-guide/init.html)" (kernel.org admin guide); und [init/main.c, wo `kernel_init` `free_initmem` und danach `run_init_process` aufruft](https://github.com/torvalds/linux/blob/master/init/main.c). Abgerufen am 2026-06-20.
[^6]: "[Al Viro's new execve/kernel_thread design](https://lwn.net/Articles/520227/)" (LWN.net). Abgerufen am 2026-06-20.
