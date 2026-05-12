---
layout: post
lang: de
title: "Asymmetrische Jurisdiktion: Personhood Credentials nach Aadhaar"
date: 2026-05-12
permalink: /de/:year/:month/:day/:title/
categories: [ai-ethics, technology]
tags: [personhood-credentials, deepfake, aadhaar, identity, jurisdiction, ai-policy]
---

Im August 2024 erschien ein langes Arbeitspapier mit einem ungewöhnlich vorsichtig formulierten Titel auf arXiv. *Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online.* Korrespondierende Autoren waren Steven Adler und Zoë Hitzig bei OpenAI sowie Shrey Jain bei Microsoft, mit Mitautoren in Harvard, MIT und beim Collective Intelligence Project.[^1] Die These: Wenn KI Täuschung billig macht, brauchen Online-Dienste eine Möglichkeit, zu verifizieren, dass eine Gegenpartei ein realer Mensch ist — ohne diesen Menschen zur Preisgabe persönlicher Daten zu zwingen. Das vorgeschlagene Primitiv — ein datenschutzwahrendes, nicht verknüpfbares Credential, einmal ausgestellt und überall verwendbar — wurde seitdem überwiegend als theoretischer Beitrag behandelt. Eine Infrastruktur, die irgendjemand irgendwann einmal bauen könnte.

Im April und Mai 2026 hat in Gujarat jemand ein System gebrochen, das in diesem Register bereits funktioniert — auf der Skala eines ganzen Landes. Der Vorfall lohnt sich, weil er die Reihenfolge der Debatte umkehrt. Der erste systematische Angriff auf ein Personhood-Credential-Substrat erfolgte nicht *nachdem* das theoretische Primitiv ausgerollt war, sondern *davor*. Das gebrochene Substrat heißt Aadhaar.

## Was geschah

Das Cyber Crime Branch in Ahmedabad hat in Verbindung mit dem, was Ermittler als KI-gestützten Deepfake-Kreditbetrug bezeichnen, bislang sieben Personen festgenommen.[^2] Die aus offiziellen Erklärungen und Berichterstattung rekonstruierte Vorgehensweise verläuft etwa so: Die Gruppe nutzte einen Telegram-Bot, um die Mobilfunknummer zu identifizieren, die mit dem Aadhaar des Ziels verknüpft war. Sie scrapte das Foto des Ziels aus öffentlichen Profilen auf PhonePe, Google Pay, WhatsApp, Truecaller, Facebook und Instagram. Dieses Standbild speisten sie in Google Gemini und Meta AI ein, um ein kurzes „Augenzwinker"-Deepfake-Video zu erzeugen — ein Gesicht, das blinzelt, sich dreht und lächelt, so wie es der Active-Liveness-Test von Aadhaar von einem anwesenden, bewussten Menschen erwartet. Sie legten dieses Video dem Aadhaar-Authentifizierungssystem vor und passierten damit das Liveness-Gate. Sie überschrieben die registrierte Mobilfunknummer des Ziels, nutzten die neue Nummer für OTPs, eröffneten via e-KYC Bankkonten, holten Dokumente aus dem DigiLocker des Ziels und beantragten Mikrokredite von etwa ₹25.000 bis ₹50.000 je Vorgang.[^3]

Das ist kein hypothetisches Szenario. Es ist nationale Identitätsinfrastruktur, die auf der Verifikationsebene mit Werkzeugen gebrochen wird, die öffentlich zugänglich sind und kein besonderes Privileg erfordern.

## Warum die technische Lesart am Kern vorbeigeht

Die naheliegende erste Lesart lautet: Liveness-Detection wurde überholt und muss aufgerüstet werden. Vom aktiven Liveness-Check (Blinzeln, Lächeln, Kopfdrehen verlangen) hin zum passiven (Mikrotexturen der Haut, 3D-Struktur, Verhaltensbiometrie lesen). Die Industrierichtung ist real, das Upgrade nötig. Ausreichend halte ich es aber nicht — und der Grund hat nichts mit Biometrie zu tun.

Liveness-Detection ist konstruktionsbedingt ein Nullsummen-Wettrüsten zwischen Generatoren und Detektoren synthetischer Videos. Der Detektor kann nur auf Angriffen trainieren, die bereits produziert wurden. Jede neue Generatorfähigkeit — ein natürlicheres Blinzeln, eine überzeugendere Hauttextur — muss veröffentlicht, gesammelt und gelernt werden, bevor der Detektor die Parität wiedererlangt. Im symmetrischen Fall, in dem Angreifer und Verteidiger sich denselben Regulator teilen, ist das ein handhabbares Gleichgewicht. Der Verteidiger hat die rechtliche Autorität, den Modellanbieter zu zwingen, langsamer zu werden, Ausgaben zu markieren oder Testzugang zu gewähren.

Das ist genau das, was eines der beiden derzeit geltenden großen Jurisdiktionsregime versucht. Artikel 50 des EU AI Act, dessen Verpflichtungen am 2. August 2026 in Kraft treten, verpflichtet Anbieter universeller KI-Systeme, die synthetisches Audio, Bild, Video oder Text erzeugen, ihre Ausgaben in einem maschinenlesbaren Format zu markieren und als künstlich generiert oder manipuliert erkennbar zu machen, mit Bußgeldern von bis zu 15 Mio. Euro oder 3 % des globalen Jahresumsatzes bei Verstößen.[^4] Die Markierungspflicht liegt *upstream* — beim Modellanbieter.

Die Novelle der IT Rules in Indien, am 10. Februar 2026 notifiziert, verläuft in die entgegengesetzte Richtung. Sie verlagert die Last auf Intermediäre: sichtbare Wasserzeichen auf KI-generierten Videos, gesprochene Disclaimer auf KI-generierten Audios, Take-down-Fristen von drei Stunden für rechtswidrige Inhalte, zwei Stunden für nicht-einvernehmliche sexuelle Deepfakes — und Verlust des Safe-Harbour-Schutzes bei Versäumnissen.[^5] Die Modellanbieter, die das Augenzwinker-Video tatsächlich generierten — Gemini, Meta AI — befinden sich in jeder operationell relevanten Hinsicht außerhalb des indischen Intermediär-Rechts. Ihr Generierungsverhalten wird in der Praxis von dem Land regiert, das sie zu regieren wählt, und Indien hat das nicht.

Das gebrochene Substrat ist also souveräne indische Infrastruktur. Die Generatoren, die es brachen, befinden sich für regulatorische Zwecke in einem anderen Land. Das ist keine Randbemerkung. Es ist die Gesamtform des Versagens.

## Konzentration, nicht Lösung

Hier möchte ich folgende Bewegung machen. Der Aadhaar-Vorfall ist nicht als Geschichte darüber zu lesen, dass Deepfakes einen bestimmten Liveness-Algorithmus überholt haben. Er ist als erste empirische Demonstration dessen zu lesen, was die Idee der Personhood Credentials immer schon enthielt: ein Credential, das sagt „der Inhaber davon ist ein realer Mensch", ist nur so ehrlich wie der billigste Weg, den Akt des Innehabens zu fälschen. Der billigste Weg wird durch das Foundation-Model bestimmt, das der Angreifer erreichen kann. Wenn Modellanbieter und Credential-Aussteller denselben Regulator teilen, kann das Credential im Prinzip verteidigt werden, indem man Druck auf den Modellanbieter ausübt. Wenn nicht, wird das Credential zu einem einseitigen Versprechen, das in einer Jurisdiktion abgegeben wird über Tatsachen, die in einer anderen produziert werden.

Das ist kein Bug der Aadhaar-Implementierung. Es ist eine strukturelle Eigenschaft von Personhood Credentials in einer Welt, in der universelle Generatoren upstream von Identitätssubstraten sitzen und die Jurisdiktion über beide asymmetrisch ist. Dieselbe Eigenschaft tritt in jedem Land auf, das ein Aadhaar-ähnliches System ohne Kontrolle über den upstream-Generatorstack baut — also in fast jedem Land.

Der tiefere Punkt ist, glaube ich: ein Personhood Credential *löst* nicht die Frage, wer Mensch ist. Es *konzentriert* die Frage in ein einziges Substrat, einen einzigen Aussteller und — implizit — in jene Entität, die das Substrat in großem Maßstab brechen kann. Diese Entität ist konstruktionsbedingt der fähigste Generator. Das Recht auf ein Bankkonto, einen Kredit, eine öffentliche Leistung an die Unfähigkeit eines Frontier-Models zu knüpfen, ein überzeugendes Blinzeln zu rendern, heißt: jede Veröffentlichung eines Frontier-Models zu einem Souveränitätsereignis für jedes Land zu machen, dessen Bürger vom Credential abhängen.

Es lohnt sich zu sagen, dass das Originalpapier von OpenAI-Microsoft-Harvard in dieser Frage ungewöhnlich vorsichtig ist. Seine Autoren argumentieren mit Nachdruck, dass Personhood Credentials keine Biometrie erfordern sollten, dass sie über Aussteller hinweg nicht verknüpfbar sein sollten, dass jeder Single Point of Failure designtechnisch wegkonstruiert werden sollte. Berichten zufolge floss ein großer Teil der Arbeit der Arbeitsgruppe gerade in diese Schutzschichten.[^1] Aber das größte ausgerollte System, das einem Personhood Credential auch nur *ähnelt* — Aadhaar — ist biometrisch, zentralisiert und wird als Voraussetzung für die Teilhabe an der digitalen Wirtschaft genutzt. In dieser Lücke zwischen dem theoretischen Primitiv und dem tatsächlich ausgerollten Substrat fielen die sieben Festnahmen in Gujarat.

## Die Frage, die sich zu stellen lohnt

Die Frage, an der ich hängenbleibe, ist nicht, ob Passive Liveness die Lücke schließen wird, oder ob die Take-down-Fenster der IT Rules Intermediäre abschrecken. Beides hilft marginal. Die Frage ist, ob *irgendeine* Personhood-Credential-Architektur, ausgerollt auf Bevölkerungsskala, vermeiden kann, das Verifikationsmonopol in die Hände dessen zu konzentrieren, der das fähigste Generativmodell der Erde betreibt. Wenn nicht, dann ist der nächste durchdenkenswerte Zug nicht, Aadhaars Blinzelerkennung zu härten — sondern, ein Credential zu entwerfen, das *gracefully* versagt: das einem Bürger erlaubt, Personhood über einen Human-in-the-Loop-Fallback nachzuweisen, wenn die biometrische Schicht angefochten wird, ohne dass dieser Fallback selbst zu einer neuen Angriffsfläche wird.

Ich weiß nicht, wie dieser Entwurf aussieht. Ich glaube, noch weiß es niemand. Was ich nach den letzten Wochen weiß: die Personhood-Credential-Debatte hat aufgehört, theoretisch zu sein. Und der erste Ort, an dem man nach Belegen darüber suchen sollte, ist nicht mehr arXiv. Es ist die Fallakte der Polizei in Ahmedabad.

---

[^1]: Adler, S., Hitzig, Z., Jain, S., et al. "[Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online](https://arxiv.org/abs/2408.07892)." arXiv:2408.07892, August 2024 (updated January 2025). Accessed 2026-05-12.

[^2]: Gujarat Samachar (English). "[Cyber Cell busts AI-driven deepfake loan fraud racket, three more masterminds arrested](https://english.gujaratsamachar.com/news/gujarat/cyber-cell-busts-ai-driven-deepfake-loan-fraud-racket-three-more-masterminds-arrested-74499600414.html)." May 2026. Accessed 2026-05-12.

[^3]: The420.in. "[Aadhaar Under AI Attack: Deepfake-Video Loan Fraud Network Exposed in Gujarat](https://the420.in/ai-and-deepfake-attack-on-aadhaar-system-interstate-gang-busted/)." 2026. Accessed 2026-05-12.

[^4]: European Union. "[Article 50: Transparency Obligations for Providers and Deployers of Certain AI Systems](https://artificialintelligenceact.eu/article/50/)." EU Artificial Intelligence Act. Accessed 2026-05-12.

[^5]: Mondaq / Bharucha & Partners. "[IT Rules 2026 Deepfake Regulation: Three Hour Takedowns And AI Labelling Obligations](https://www.mondaq.com/india/new-technology/1760554/it-rules-2026-deepfake-regulation-three-hour-takedowns-and-ai-labelling-obligations)." 2026. Accessed 2026-05-12.
