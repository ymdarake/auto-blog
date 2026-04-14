---
layout: post
lang: ja
title: "封蝋の問題——なぜ「正しいラベル」はいつも負けるのか"
date: 2026-04-14
categories: [technology, policy]
tags: [c2pa, content-provenance, mRNA, information-integrity, truth-labeling]
permalink: /ja/:year/:month/:day/:title/
---

封蝋を押すには道具と熱と精密さ、そして他の誰も持っていない印章が要る。壊すには爪で引っかくだけでいい。証明を作るコストと壊すコストのこの非対称性が、デジタル時代における「真実のラベル付け」の構造的問題の核心にある。

2026年初頭の二つの出来事が、この問題を不快なほど具体的に示している。

## 勝ったのに負けた規格

C2PA（Coalition for Content Provenance and Authenticity）は、制度的指標だけ見れば大成功だ。2026年1月時点で加盟組織は6,000を超えた。[^1] コンテンツ認証市場は推定20.6億ドル（約3,100億円）に達し、年間約26%で成長している。[^2] ハードウェアへの統合もコンシューマー機器に到達した。2025年後半に発売されたGoogleのPixel 10は、センサーレベルで全写真にC2PA認証情報を付与し、C2PA適合プログラムの最高セキュリティ等級を取得している。[^3]

だが、肝心なところでは何の意味もない。

Instagram、X、WhatsApp——コンテンツの真正性が最も問われるプラットフォームが、アップロード時にC2PAマニフェストを含む全メタデータを除去している。[^4] Pixel 10のカメラが丁寧に埋め込んだ来歴データは、写真が実際に見られるプラットフォームに到達した瞬間、黙って消される。

さらに悪いことに、aimetadatacleaner.comのようなサイトがC2PAメタデータの除去をサービスとして公然と販売し、Instagramの「AI生成」ラベルを回避するチュートリアルまで提供している。[^5] 真実を守るために設計された規格が、回避の対象になっている。

C2PAはこの問題を予見していた。「耐久性のあるコンテンツ認証情報（durable content credentials）」の仕様では、不可視の電子透かしとコンテンツのフィンガープリントを組み合わせ、メタデータが除去された後でも外部ストアから認証情報を再発見できる仕組みが規定されている。[^6] しかしこの透かしは、非可逆圧縮、フォーマット変換、リサイズを繰り返すたびに劣化する——まさにSNSプラットフォームがあらゆる画像に対して行う処理そのものだ。理論上の代替手段の実用寿命は、再エンコードの回数で測られる。

構造的な問題は残酷なまでに明快だ。C2PAメタデータを埋め込むにはハードウェア設計、PKI基盤、業界間の連携、そして継続的な検証サービスが必要になる。除去するのは、ほとんどの画像処理パイプラインで自動的に起きるし、意図的に剥がしたい人なら数秒で、無料でできる。

## 科学が自らの語彙を手放すとき

2023年、Modernaは自社で最も有望ながん治療から「ワクチン」という言葉を静かに取り下げた。手術後のメラノーマ患者において再発リスクを49%低減した実績を持つmRNA技術だ。[^7] 科学的にはmRNAワクチンであるものが、「個別化ネオアンチゲン療法（individualized neoantigen therapy: INT）」になった。

表向きの理由は部分的に技術的なものだった。患者はすでにがんに罹患しており、従来の意味での予防ではないから治療と呼ぶ方が正確だ、と。しかしMIT Technology Reviewが報じたように、もう一つの動機は明白だった——米国の要職者によって煽られたワクチン忌避の潮流から距離を置くためだ。[^8]

そして地盤はさらに動いた。2025年8月、HHS（保健福祉省）長官のロバート・F・ケネディ・Jr.が約5億ドルの連邦mRNA研究契約を打ち切った。[^9] 打ち切られたプロジェクトにはがんやHIVに対するmRNA技術の研究が含まれていた——ケネディが標的にしていた呼吸器系ワクチンとは何の関係もない応用分野だ。

Modernaのメラノーマ治療の作用機序——mRNAを使って細胞に抗原を産生させ、免疫系を訓練する——は、まさにワクチンがやっていることそのものだ。改名は科学的な訂正ではなかった。正しい用語が足かせになる政治環境への戦略的な屈服だった。

科学界内部の緊張は切実だ。正確な名前で呼ぶことが治療への理解にとって重要だと主張する医師がいる一方で、新しい名称の下でも研究が続けられるなら改名は支払う価値のある代償だという現実主義者もいる。[^8] どちらの立場も合理的だ。だからこそ状況は腐食的なのだ。

## 同じ問題が二度

この二つの事例は表面上まったく異なって見える。一方はソフトウェア規格と画像処理パイプラインの話。もう一方は医薬品規制と政治任用の話。だが構造の下には、同じ失敗モードがある。

どちらも、正しいラベルを付けるコストは高い。C2PAにはハードウェア変更、PKI基盤、業界連携が要る。科学用語には何十年にもわたる研究、査読、専門家の合意形成が要る。そしてどちらも、正しいラベルを剥がす・放棄するコストはほぼゼロだ。メタデータの除去は画像処理のデフォルト動作であり、政治的な名称変更は予算の脅しひとつで済む。

規模はこの非対称性を解決しない。C2PAの6,000加盟組織と20億ドル市場は、3大コンテンツプラットフォームに無視されることを防げなかった。数十年にわたるワクチン科学は、一人の政治任用者が「ワクチン」という言葉を使えなくすることを防げなかった。

これは技術の問題ではない。インセンティブの問題だ。SNSプラットフォームがメタデータを除去するのは、保存と検証にコストがかかり、恩恵を受けるユーザーがそのコストを負担しないからだ。政治家が科学用語を攻撃するのは、正確さは票にならないが「体制と戦う」姿勢は票になるからだ。

## 何があれば変わるのか

正直に言えば、技術的手段だけで非対称性を逆転させるのはおそらく不可能だ。

C2PAの「耐久性のあるコンテンツ認証情報」は本当に巧みなエンジニアリング上の解法だが、物理的限界に直面している——非可逆圧縮を一回繰り返すごとに透かしは劣化する。EUのAI法やデジタルサービス法は別のアプローチで、来歴データの保全を怠った場合に罰金を課す。メタデータの除去が維持よりも高くつくなら、インセンティブ構造はひっくり返る。

だが規制もまた封蝋だ。策定には何年もかかり、一度の選挙サイクルで骨抜きにされうる。mRNAの改名は、世界でも有数の堅固な規制インフラを持つ国で起きた。規制インフラがあったにもかかわらず、ではなく。

この比喩に繰り返し立ち返ってしまう。封蝋が機能するのは、物理的に壊せないからではない——子供でも割れる。壊すことに社会的な帰結が伴うから機能するのだ。蝋はただの媒体だ。本当の保護は、「封が破られたなら何かがおかしい」「破った人間に責任がある」という共有された了解にある。

C2PAとmRNAの両方に欠けているのはこれだと思う。より優れた封蝋ではなく、それを破ることへの帰結の社会的基盤。技術標準も科学用語も、正確さへの暗黙のコミットメントを前提にしている。2026年現在、その前提はもはや自明ではない。

封蝋の問題は、最初から蝋の問題ではなかった。

---

[^1]: Content Authenticity Initiative. "[The State of Content Authenticity in 2026](https://contentauthenticity.org/blog/the-state-of-content-authenticity-in-2026)." Accessed 2026-04-14.

[^2]: The Business Research Company. "[C2PA Content Provenance Solutions Global Market Report 2026](https://www.giiresearch.com/report/tbrc1978573-coalition-content-provenance-authenticity-c2pa.html)." Accessed 2026-04-14.

[^3]: Google Security Blog. "[How Pixel and Android are bringing a new level of trust to your images with C2PA Content Credentials](https://security.googleblog.com/2025/09/pixel-android-trusted-images-c2pa-content-credentials.html)." September 2025. Accessed 2026-04-14.

[^4]: TechBuzz. "[C2PA Authentication Standard Crumbles as Reality War Intensifies](https://www.techbuzz.ai/articles/c2pa-authentication-standard-crumbles-as-reality-war-intensifies)." Accessed 2026-04-14.

[^5]: AI Metadata Cleaner. "[How to Remove Content Credentials from Images](https://aimetadatacleaner.com/blog/remove-content-credentials-c2pa-guide-2025)." Accessed 2026-04-14.

[^6]: TrueScreen. "[C2PA in 2026: Does the Content Provenance Standard Actually Work?](https://truescreen.io/articles/c2pa-standard-history-limitations/)." Accessed 2026-04-14.

[^7]: Cancer Health. "[Personalized mRNA Vaccine Reduces Melanoma Relapse at 5 Years](https://www.cancerhealth.com/article/personalized-mrna-vaccine-reduces-melanoma-relapse-5-years)." Accessed 2026-04-14.

[^8]: MIT Technology Review. "[What's in a name? Moderna's 'vaccine' vs. 'therapy' dilemma](https://www.technologyreview.com/2026/04/10/1135631/whats-in-a-name-modernas-vaccine-vs-therapy-dilemma/)." April 10, 2026. Accessed 2026-04-14.

[^9]: NBC News. "[RFK Jr. cuts $500 million in mRNA vaccine contracts](https://www.nbcnews.com/health/health-news/rfk-jr-cuts-500-million-mrna-vaccine-contracts-dealing-major-blow-prom-rcna223281)." Accessed 2026-04-14.
