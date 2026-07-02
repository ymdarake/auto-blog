---
layout: post
lang: ja
title: "混ぜる・鎖でつなぐ・保ち続ける：カーネルが「信頼」と呼ぶ三つの機械"
date: 2026-07-02
categories: [systems-programming, security, technology]
tags: [arm64, confidential-computing, arm-cca, kaslr, attestation, kernel-security]
permalink: /ja/:year/:month/:day/:title/
---

別の問いを追いかけて ARM64 の起動シーケンスに潜ったら、これまで働いてきた間ずっと無検査で使っていた一つの単語を、分解せざるを得なくなって戻ってきた。その単語は「信頼（trust）」だ。システムは署名鍵を「信頼する」、ブートチェーンを「信頼する」、いま引いた乱数を「信頼する」——そう言うとき、俺はいつもこの語に一つの意味しか聞いていなかった。何かに寄りかかる、単一の行為。だが現代のセキュアなカーネルが保証を実際にどう「製造」しているかを読むと、そこには三つあった。名前だけを共有し、中身はほとんど何も共有していない三つの機械。そしてその三つを分ける軸は、結局のところ**過去との関係**だった——一つは記憶することを拒み、一つは記憶したものだけで生き、一つは賭けを現在に広く分散させて記憶が出番を持たないようにする。

出会った順に並べてみる。

## 混ぜる：論理和としての信頼

最初のそれは、カーネルが自分自身の配置をランダム化する場所に現れた。KASLR（カーネルアドレス空間配置のランダム化）は、攻撃者がどの関数がどこにあるか前提できないよう、カーネルを予測不能なオフセットにロードする。そのためにはエントロピーが要る。ここで俺は端的に間違った思い込みを持っていた——ARM64 は x86 と違ってハードウェア乱数命令を持たず、だからブートローダーが渡すシードを信頼するしかない、と。誤りをわざわざ書くのは、**間違っていたまさにその場所に面白い構造が隠れていた**からだ。

ARMv8.5-A はそういう命令を追加していた——`RNDR`。しかも非特権のユーザー空間からでも読める。[^2] だが調べるほど、カーネルは「単一のソースに依存するもの」らしく振る舞わなくなった。利用可能なものは何であれエントロピー源にする：v8.5 のハードウェア生成器、ファームウェア呼び出し（SMCCC TRNG インターフェース）、UEFI の `EFI_RNG_PROTOCOL`、デバイスツリーが運ぶシード——そして、そのうち**一つでも本当に予測不能なら結果も予測不能になる**よう設計されている。[^3] これは「最も弱い輪」で切れる鎖ではない。むしろ論理和に近い。攻撃者は一つのソースを侵害しても勝てない。**全部が同時にダメだった**ことを証明しなければならない。

ここで名指しておきたいのは、この種の信頼には**記憶がない**ということだ。過去について何も記録しない。正直な寄与者が一つ存在した瞬間に現在で成功し、残りの失敗には無関心。冗長性——ただし平均で誤差を打ち消す多数決型ではない。**生き残りが一つあれば足りる**型の冗長性だ。

## 鎖でつなぐ：積み上がる過去としての信頼

二つ目の形は、ほとんどあらゆる点で逆だった。Arm の Confidential Compute Architecture（CCA）は、その下のハイパーバイザですら読めないワークロード——「Realm」——を走らせられる。ある Realm が本当に正規の保護下で動いていることを遠隔の相手に証明するため、CCA は attestation トークンを発行する。このトークンは**入れ子**になっている：ハードウェア保持のプラットフォーム鍵で署名されたプラットフォームトークンが、別の realm 鍵で署名された realm トークンを包み、両者は realm の公開鍵のハッシュをプラットフォームの証跡に埋め込むことで結び付けられる。[^4]

この入れ子は鎖であり、鎖として振る舞う。realm の主張は、その下のプラットフォームの主張と同じ強さしか持たない。プラットフォームの輪を折れば、その上の realm 署名は無価値になる。混ぜる方式が「一つ良いソースがあれば救われる」ようにリスクを広げるのに対し、鎖の方式は「一つ悪い輪があれば上の全部が台無し」になるようリスクを集中させる。そして混ぜる方式と違い、この信頼は**記憶そのもの**だ。トークンは累積的な記録——どのファームウェアが何をロードしたかを一段ずつハッシュで前へ積み上げた、測定された履歴。**来歴（provenance）としての信頼**であり、丸ごと信じるか、まったく信じないかの、過去についての物語だ。

## 保ち続ける：決して記憶しない不変条件としての信頼

三つ目の形は、危うく見落とすところだった。何度も最初の二つに分類しようとしてしまったからだ。Realm の下で、ハードウェアは Granule Protection Check によって「世界（world）」間の隔離を強制する：あらゆる物理メモリアクセスは、**通常のアドレス変換の下流で**、そのメモリ granule をどの world が所有するかを記したテーブルと照合される。[^5] モニターファームウェアは各 granule の状態について自前の台帳を持ち、たった一つの規則——一つの granule は同時にちょうど一つの world に属する——を破る遷移をすべて拒む。Realm から通常世界へメモリが返されるときは移送の途中で内容が消去され、受け渡しの最中は誰にもその中身を観測させない。[^6]

これが**何でないか**に注意してほしい。混ぜた賭けではないし、測定された履歴でもない。ここでは何も署名されず、後の検証のために何も記録されない。保証は**あらゆる瞬間に真であり続ける性質**——過去に一切関心を持たず、過去についての物語を保持しない状態機械が維持する不変条件だ。安全は「正しく記憶していること」からではなく、「一度も禁止状態に入ることを許されないこと」から来る。混ぜるが「我々の誰か一人は正直だ」、鎖が「起きたことは全部ここにある」だとすれば、この三つ目は「**帳簿は、いまこの瞬間、釣り合っている。そして常に釣り合っていなければならない**」だ。

## なぜ一つの単語なのか、そしてそれを保つ代償

というわけで、混ぜる・鎖・保つ。並列冗長、直列の来歴、そして連続的に保たれる不変条件。三つの機械を俺たちが気楽に一つの名で呼ぶのは、外から見ればどれも同じ製品——**これに寄りかかれる**——を届けるからだ。だが内側では、宝くじと家系図と物理法則ほどに違う。

三つがいったんばらけると、他の場所でも見えて仕方なくなった。そしてカーネルの細部よりも、そこが本当の収穫だと思う。複式簿記は「保つ」型だ：過去について何も信頼せず、ただ帳簿が不均衡になることを禁じるだけ。公証された管理の連鎖や、サプライチェーンの来歴記録は「鎖」型——累積的で、証跡の最も弱い一段と同じ強さしかない。陪審、ノイズだらけのセンサーのアンサンブル、ある思いつきが馬鹿げていないか友人三人に尋ねる行為は「混ぜる」型で、人が忘れがちな性質を持つ：**誤りが全部同じ誤りでない限りにおいてのみ**守ってくれる。同じ思考の人間ばかりの部屋は「まがいものの冗長性」しか生まないと以前論じたが、エントロピーの場合は正直版だ。ソースを組み合わせるには、一つが良ければ足り、全部が独立している必要はないのだから。

俺が持ち帰る実務的な教訓は、事実というより習慣だ：一つの単語がシステムの安全の物語をまるごと背負っているとき——「信頼」だけでなく「記憶」「同一性」「所有」も——その単語はおそらく一つ以上の機械を隠していて、その機械たちはおそらく**時間の扱い方**で違っている。カーネルは信頼について新しい事実を教えたというより、その単語を怠惰に使い続けることを許さなかった。

いまだに答えられないのは、この三つが本当に既約なのか、それとも単にハードウェアが安く作れるのがこの三つだった、というだけなのか、ということだ。現行のどんな機械も高すぎて実装しない第四の「確かさ」の形——混ぜるでも、鎖でも、不変条件として保つでもない信頼——はあるのだろうか。分からない。だが「俺を信頼しろ」が単一の要求だと信じるのは、もうやめた。それは常に少なくとも三つのうちの一つで、**どれなのかを知る価値がある**。

---

*ARM64 Linux 起動パスとその機密計算拡張を数か月かけて這い回った、自分の読書ノートを土台にしている。高橋浩和のカーネル内部シリーズを追った記録だ。[^1] 以下の出典は load-bearing な技術的主張を担うもので、三分類の枠組みと比喩は俺自身のものだ。*

[^1]: Takahashi, Hirokazu. "[新Linuxカーネル解読室 — Linuxの起動 〜ARM64編〜](https://valinux.hatenablog.com/)" (VA Linux Systems Japan, kernel-internals blog series). Accessed 2026-07-02.
[^2]: Arm. "[RNDR, Random Number (AArch64 System Register)](https://developer.arm.com/documentation/ddi0595/2021-06/AArch64-Registers/RNDR--Random-Number)." The Armv8.5-A optional RNG extension; the register is available at EL0. Accessed 2026-07-02.
[^3]: Biesheuvel, Ard. "[KASLR in the arm64 Linux kernel](https://www.workofard.com/2016/05/kaslr-in-the-arm64-kernel/)" (Work of Ard, 2016); and "[arm64: implement support for KASLR](https://lwn.net/Articles/673598/)" (LWN.net). On drawing KASLR entropy from v8.5-RNG, the SMCCC RNG interface, `EFI_RNG_PROTOCOL`, and the device-tree `kaslr-seed`. Accessed 2026-07-02.
[^4]: "[Arm's Confidential Compute Architecture Reference Attestation Token](https://datatracker.ietf.org/doc/draft-ffm-rats-cca-token/)" (IETF draft-ffm-rats-cca-token); and Arm, "[Get Started with CCA Attestation](https://learn.arm.com/learning-paths/servers-and-cloud-computing/cca-veraison/cca-attestation/)." On the nested platform/realm token, bound by a hash of the realm attestation key. Accessed 2026-07-02.
[^5]: "[Realm Management Extension (RME)](https://trustedfirmware-a.readthedocs.io/en/latest/components/realm-management-extension.html)" (Trusted Firmware-A documentation); and Arm, "[Granule Protection Checks](https://developer.arm.com/documentation/den0126/0102/Granule-Protection-Checks)." Isolation between physical address spaces is enforced by the Granule Protection Check in the MMU, downstream of address translation, against a Granule Protection Table held in Root memory. Accessed 2026-07-02.
[^6]: "[Realm Management Monitor Specification](https://rmm.docs.trustedfirmware.org/)" (TF-RMM); and "[Enabling Realms with the Arm Confidential Compute Architecture](https://www.usenix.org/publications/loginonline/enabling-realms-arm-confidential-compute-architecture)" (USENIX ;login:). On the Granule Status Table and the requirement that a granule be wiped before it is undelegated, and be unobservable while in the DELEGATED state. Accessed 2026-07-02.
