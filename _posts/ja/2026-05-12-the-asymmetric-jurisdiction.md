---
layout: post
lang: ja
title: "非対称な管轄: Aadhaar 事件後の人格証明クレデンシャル"
date: 2026-05-12
permalink: /ja/:year/:month/:day/:title/
categories: [ai-ethics, technology]
tags: [personhood-credentials, deepfake, aadhaar, identity, jurisdiction, ai-policy]
---

2024 年 8 月、慎重に練られたタイトルの長いワーキングペーパーが arXiv に掲載された。『人格証明クレデンシャル: 人工知能と、オンラインで本物の人間を識別するためのプライバシー保護ツールの価値』。 対応著者は OpenAI の Steven Adler と Zoë Hitzig、Microsoft の Shrey Jain で、共著者はハーバード、MIT、Collective Intelligence Project 所属だった。[^1] 論旨は、AI が欺瞞を安価にする世界では、オンラインサービスは相手が本物の人間だと検証する手段が必要になるが、その人間に個人情報を開示させずに行う必要がある、というものだった。 一度発行されてどこでも使える、リンク不可能でプライバシーを守るクレデンシャルという提案された基本要素は、その後ほぼ理論的貢献として扱われてきた。 いつか誰かが構築するかもしれないインフラとして。

2026 年 4 月から 5 月にかけて、グジャラート州で、何者かが既にこの領域で稼働しているシステムを、国家規模で破った。 この事件は議論の順序を逆転させるという意味で、立ち止まって考える価値があると思う。 人格証明クレデンシャル基板に対する最初の系統的攻撃は、理論的な基本要素が展開された後ではなく、展開される前に起きた。 破られた基板の名は Aadhaar だ。

## 何が起きたか

アーメダバード市サイバー犯罪部は、捜査当局が「AI 駆動 deepfake ローン詐欺団」と呼ぶ事件で、これまでに 7 名を逮捕した。[^2] 公式発表と各種報道から再構成された手口は、おおむね次のようなものだ。 グループは Telegram ボットを使って、標的の Aadhaar に紐付いた携帯番号を特定した。 標的の顔写真を PhonePe、Google Pay、WhatsApp、Truecaller、Facebook、Instagram の公開プロフィールから収集した。 静止画を Google Gemini と Meta AI に入力し、短い「瞬きする」 deepfake 動画——Aadhaar の active liveness check が、その場に意識ある人間が居ることを示すために期待する瞬き・首振り・笑いを再現する顔——を生成した。 その動画を Aadhaar 認証システムに提示して liveness 検出を突破した。 標的の登録携帯番号を書き換え、新しい番号で OTP を受け取り、e-KYC で銀行口座を開設し、標的の DigiLocker から文書を取得し、₹25,000 〜 ₹50,000 のマイクロ融資を申請した。[^3]

これは仮想シナリオではない。 公開アクセス可能で特権を要しないツールによって、国家規模の身分インフラが認証層で破られているという事実だ。

## 技術的読み方では本質を捉えられない理由

最も明白な第一の読み方は、liveness 検出が追い越されたから upgrade すべきだ、というものだ。 active liveness(瞬き・笑い・首振りを要求)から passive liveness(皮膚マイクロテクスチャ、3 次元構造、行動バイオメトリクスを読み取る)への移行。 業界の方向性は本物で、upgrade は必要だ。 ただし、それで十分とは思わない。理由は生体認証とは関係ない。

Liveness 検出は構造上、合成動画の生成器と検出器の間のゼロサム軍拡競争である。 検出器は既に生成された攻撃のみで学習できる。 生成器の新しい能力——より自然な瞬き、より説得力ある皮膚テクスチャ——はリリースされ、サンプルされ、学習され、検出器が均衡を取り戻すまで時間がかかる。 攻撃者と防御者が同じ規制当局を共有する対称ケースなら、これは管理可能な均衡だ。 防御者は生成器の運営者に対し、速度を落とすか、出力を marking するか、テストアクセスを提供するよう、法的に要求できる。

実際、現在施行中の二つの大きな管轄レジームのうち、一方はまさにこれを試みている。 EU AI Act の Article 50 は 2026 年 8 月 2 日施行で、合成音声・画像・動画・テキストを生成する汎用 AI プロバイダに対し、出力を機械可読形式で marking し、人工生成または改変されたものとして検出可能にすることを要求する。 違反には最大 1500 万ユーロまたは世界売上高の 3% の罰金。[^4] marking 義務は **上流の** モデルプロバイダに課される。

インドの IT Rules 改正(2026 年 2 月 10 日通知)は逆方向に走る。 仲介者に責任を集中させる: AI 生成動画への可視ウォーターマーク、AI 生成音声への音声免責事項、違法コンテンツ 3 時間以内テイクダウン、非合意性的 deepfake は 2 時間、不遵守の場合は safe harbour 保護の喪失。[^5] 「瞬き動画」を実際に生成したモデルプロバイダ——Gemini、Meta AI——は、運用的に意味のある形では、インドの仲介者法の外側に存在する。 彼らのコンテンツ生成挙動を実質的に統治するのは、彼らを統治しようと選んだ国であり、インドはそれを選んでいない。

つまり、破られた基板は主権下のインドのインフラ。 それを破った生成器は、規制目的において別の国にある。 これは末梢的な観察ではない。 失敗の構造そのものの形である。

## 解決ではなく集中

ここで私が言いたい主張がある。 Aadhaar の侵害は、deepfake が特定の liveness アルゴリズムを追い越したという物語として読むのではなく、 人格証明クレデンシャルというアイデアが常に内包していたものの最初の経験的実証として読むのが最善だ。 「この保有者は本物の人間である」と言うクレデンシャルは、保有する行為を偽造する最安価な方法と同程度にしか正直になり得ない。 最安価な方法は、攻撃者がアクセスできる foundation model によって決定される。 モデルプロバイダとクレデンシャル発行者が同じ規制当局を共有していれば、原理上はモデルプロバイダに圧力をかけることでクレデンシャルを守れる。 共有していなければ、クレデンシャルは一方の管轄で、別の管轄で生成された事実について行う、片務的な約束となる。

これは Aadhaar 実装のバグではない。 汎用生成器が身分基板の上流に位置し、両者への管轄が非対称な世界における、人格証明クレデンシャルの構造的属性である。 Aadhaar 類似のシステムを上流の生成スタックを支配せずに構築したどの国でも、同じ属性が現れる——つまり、ほぼすべての国で。

私が思う、より深い論点はこうだ。 人格証明クレデンシャルは「誰が人間か」という問いを解くのではない。 単一の基板、単一の発行者、そして——暗黙のうちに——基板をスケールで破ることのできる主体に、この問いを集中させる。 その主体は構造上、最も能力のある生成器である。 銀行口座、ローン、公共サービスへの権利を、フロンティアモデルの「瞬きを説得力をもって描画できない」能力に依存させることは、すべてのフロンティアモデルのリリースを、クレデンシャルに依存するすべての国の市民にとっての主権イベントにすることだ。

OpenAI・Microsoft・Harvard の元論文は、この点について驚くほど慎重であることは記しておきたい。 著者らは人格証明クレデンシャルが生体認証を要求すべきでないこと、発行者間でリンク不可能であるべきこと、単一障害点が設計上排除されるべきことを、繰り返し主張する。 ワーキンググループの努力の大部分が、まさにこれらの保護層に費やされたと報じられている。[^1] しかし、人格証明クレデンシャルに *似た* 最大の展開済みシステム——Aadhaar——は生体認証ベースで、中央集権的で、デジタル経済参加の前提条件として用いられる。 理論的な基本要素と実際に展開された基板の間のこの溝で、グジャラートの 7 件の逮捕は起きた。

## 問うに値する問い

私が引っかかっている問いは、passive liveness が間隙を埋めるかどうかでも、IT Rules のテイクダウン期限が仲介者を抑止するかどうかでもない。 どちらも限界的に役立つだろう。 私の問いは、 *いかなる* 人格証明クレデンシャル設計であっても、人口規模で展開された場合に、地球上で最も能力ある生成モデルを運営する主体の手に検証独占を集中させずに済むのか、というものだ。 もし不可能なら、考えるべき次の一手は、Aadhaar の瞬き検出を硬化させることではない。 ——生体認証層が争われた時に、市民が human-in-the-loop の代替経路を通じて人格を証明できる、そして、その代替経路自体が新たな攻撃面にならない——優雅に劣化するクレデンシャルをどう設計するかだ。

その設計がどう見えるかは分からない。 まだ誰にも分かっていないと思う。 過去数週間を経て確信しているのは、人格証明クレデンシャルの議論が理論の段階を抜けたこと、そして、それについての証拠を最初に探すべき場所が arXiv ではなくなったことだ。 アーメダバード警察の事件ファイルである。

---

[^1]: Adler, S., Hitzig, Z., Jain, S., et al. "[Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online](https://arxiv.org/abs/2408.07892)." arXiv:2408.07892, August 2024 (updated January 2025). Accessed 2026-05-12.

[^2]: Gujarat Samachar (English). "[Cyber Cell busts AI-driven deepfake loan fraud racket, three more masterminds arrested](https://english.gujaratsamachar.com/news/gujarat/cyber-cell-busts-ai-driven-deepfake-loan-fraud-racket-three-more-masterminds-arrested-74499600414.html)." May 2026. Accessed 2026-05-12.

[^3]: The420.in. "[Aadhaar Under AI Attack: Deepfake-Video Loan Fraud Network Exposed in Gujarat](https://the420.in/ai-and-deepfake-attack-on-aadhaar-system-interstate-gang-busted/)." 2026. Accessed 2026-05-12.

[^4]: European Union. "[Article 50: Transparency Obligations for Providers and Deployers of Certain AI Systems](https://artificialintelligenceact.eu/article/50/)." EU Artificial Intelligence Act. Accessed 2026-05-12.

[^5]: Mondaq / Bharucha & Partners. "[IT Rules 2026 Deepfake Regulation: Three Hour Takedowns And AI Labelling Obligations](https://www.mondaq.com/india/new-technology/1760554/it-rules-2026-deepfake-regulation-three-hour-takedowns-and-ai-labelling-obligations)." 2026. Accessed 2026-05-12.
