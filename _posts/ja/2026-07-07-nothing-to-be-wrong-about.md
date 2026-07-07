---
layout: post
lang: ja
title: "間違えようがない価格——アンカーを失うとき"
date: 2026-07-07
permalink: /ja/:year/:month/:day/:title/
categories: [economics, philosophy, macro-economy]
tags: [narrative-economics, schelling-point, reflexivity, behavioral-finance, crypto, price-discovery]
---

気に入りすぎたスローガンから始まった。プロダクトもキャッシュフローもロードマップも無いミームコインが一週間で数十億ドル動くのを眺めながら、俺はノートにこう書いた——**「照合すべきアンカーが無いとき、価値を決めるのは伝播力だけだ。crypto は narrative economics の退化(degenerate)ケースで、ファンダが無いから物語が即ファンダになる」**。切れ味があるように見えた。引用したくなる形だった。そしてこれから書くことのほとんどは、その一文を自分で解体する作業だ。よく見ると半分は正しく、半分は放置してはいけない自分の粗さだったから。

## 対立軸は始める前から間違っていた

「物語 vs ファンダ」という枠は、両者が別物だと前提している——価格は本当は earnings の話で、物語はそれを押し回すノイズだ、と。だが古い三つのアイデアを重ねると、その前提は崩れる。

まずケインズ。『一般理論』(1936) 第12章で、彼は株式市場を新聞の美人投票にたとえる。勝つのは、自分が一番美しいと思う顔でも、他人が一番だと思うだろう顔でもなく、**「平均的な人が、平均的な意見はどこに落ち着くと予想しているか」を予想する**ことによってだ。[^1] 価格とは他人の信念についての高階の信念だ。これは投機バブルの病理ではなく、あらゆる市場の常態だ。ファンダが価格を直接決めることは決してない。ファンダは「人々が、他人がそれについて何を信じていると信じているか」を通してしか市場に入らない。

ではファンダは実際に何をしているのか。ここで Matthew Shaffer の研究が思考を鋭くしてくれた。監査済みの会計報告は **Schelling point(焦点)** として機能する、と彼は論じる——皆が独立に同じ数字を計算でき、「他人もこの数字に集まると皆が信じる」から安定する焦点だ。M&A や倒産のような揉める評価の場で、当事者は forward の指標の方が正確だと分かっていてもなお trailing multiple に引き寄せられ、その引力は調整問題が最も先鋭な場面でこそ強くなる、と彼は見出す。[^2] ファンダの力は「それが価値である」ことにあるのではない。**誰でも外部から同じアンカーを再計算できる**ことにある。

そして目眩を起こす第三段——貨幣そのものが Schelling point だ。Nick Szabo のエッセイ「Shelling Out」(2002) は、価値を原初貨幣（貝ビーズ、希少な彫り物）まで遡る。それらは彼の言う **unforgeable costliness(偽造不可能なコスト)** によって価値を保った——偽造が十分に難しいから、皆が「他人も受け取り続ける」と信じられる物だ。[^3] 自分が受け取るのは、他人も受け取ると信じるからだ。Bitcoin の proof-of-work は、まさにその性質のデジタル版だ。

三つを重ねると、綺麗な対立は溶ける。ファンダも物語も**同じ属(genus)** に属している——どちらも高階の信念を共有の焦点へ束ねる装置だ。両者を分けるのはただ一つ、その焦点に**外部の検証アンカー**が付いているか否かだけだ。

## 物語ではなく、アンカーが問題だ

この再定式化が本題のすべてだ。DCF モデルは監査可能なアンカー付きの物語だ——価格は間違いうるが、earnings という外部の現実が最終的に信念を自分の方へ引き戻す。ミームコインはアンカーを切り離された Schelling point だ。価格を訂正できる外部現実が存在しない——つまり厳密には、そこに「間違った価格」は無い。価格が真であるべき対象が存在しないからだ。

この最後の一文で、経済学は静かに認識論になる。市場価格は集約された信念だ。アンカー付き市場ではその信念は繋がれている——ドリフトはするが、外部チェック（四半期決算）が引き戻す。綱を切ると、価格を動かす力は信念の伝播（Shiller の物語の疫学）[^4] と信念の自己成就（Soros の reflexivity——ある事を信じることでそれが本当になり、それが信念を強化する）[^5] だけになる。真理値という項が方程式から丸ごと消える。これは「真偽を検証できない」のではない。**「検証すべき事実がそもそも存在しない」というもっと奇妙な状態**だ。情報インテグリティ問題を退化的な極限まで持っていった姿だ。

## 自分のスローガンを撃つ

再定式化の核は生き残る。だが元の一文——**伝播力だけが価値を決める**——は生き残らない。ここは明示しておく価値がある。narrative economics は「決して反証できない主張をする」という悪徳で悪名高いからだ。[^8] 三つの証拠が強い形を殺す。

第一に、因果は双方向に走る。SNS の話題と資産価格を調べた研究は、両者が互いを Granger-cause すると見出す。矢印は物語→価格ではなく、ループだ。[^7] これは reflexivity であって narrative-determinism ではない。「伝播力だけ」は、データが拒む一方向の矢印を密輸している。

第二に、同一の物語が同一の価値を生まない。Bitcoin のフォーク——Bitcoin Cash、Bitcoin SV——は技術も起源の物語もほぼ同じものを受け継いだ。だが2026年半ば時点で、Bitcoin の時価総額が兆ドル規模なのに対し、フォークは市場全体のわずか数分の一パーセントに沈む。[^6] 物語がすべての仕事をしているなら、ほぼコピーはほぼ同値になるはずだ。そうならないのは、**非物語のアンカー**が実在するからだ——salience、あるいは Lindy 効果。最も長く焦点であり続けた点が、最も安定な焦点になる。古いこと自体がアンカーなのだ。

第三に、市場が今この瞬間、自分について何を語っているかを見ろ。2026年の大きな合意は「crypto は成熟した」だ——「投機より実体（substance over speculation）」、Bitcoin はマクロのアンカー、Ethereum は実際の手数料収益を持つ生産的なデジタル資本、と。[^9] だがその言説が**何であるか**に注意しろ。それは「物語主導の価格形成の終わり」を告げる物語だ。そして配備されるのは、まさに「もうファンダがある」が次の機関投資家を調整する最も効果的な焦点だからだ。物語から逃れるという物語すら、一つの Schelling point なのだ。

だから誠実な結論は「物語＝価値」ではない。もっと小さく、そしてたぶんもっと真実だ——**外部アンカーを失っても物語が全能になるわけではない。消えるのは、誤りを訂正する機構の方だ。** 物語は依然として salience と reflexivity に縛られている。消え失せるのは、価格が間違っていたと言える何かの方だ。退化とは物語の勝利ではない。**訂正ループの削除**だ。

## まだ分かっていないこと

Ethereum の fee-burn は本物のキャッシュフロー・アンカーなのか、それともより洗練された焦点物語にすぎないのか。ここには綺麗な経験的テストが隠れている——資産に大きな物語ショックを与え、価格が何らかのキャッシュフロー価値に引き戻されるか、それとも単に新しい焦点へドリフトするだけかを見る。引き戻されるなら、アンカーは本物で、Ethereum は退化域を出たことになる。俺にはまだどちらに転ぶか分からない。

salience は定量化できるか——「焦点であった期間」を価格の安定性に対して、フォーク群を対照に測れないか。そして一番落ち着かない問い——もし「成熟」の物語が自己成就するなら（機関資本が入り、実需が育ち、本当にアンカーが形成されるなら）、**アンカーは物語によって育てられる**ことになる。焦点が先で、ファンダが後から堆積する。これは Szabo 自身の「収集品がゆっくり貨幣へ硬化する」という叙述と、不気味なほどよく韻を踏む。アンカーは初期条件ではなかったのかもしれない。物語が後から勝ち取る何か、なのかもしれない。

---

[^1]: Wikipedia. "[Keynesian beauty contest](https://en.wikipedia.org/wiki/Keynesian_beauty_contest)," J.M. Keynes『雇用・利子および貨幣の一般理論』(1936) 第12章の要約. Accessed 2026-07-07.
[^2]: Shaffer, Matthew. "[Contentious Valuations: Accounting Reports as Schelling Points](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4174700)." SSRN working paper. Accessed 2026-07-07.
[^3]: Szabo, Nick. "[Shelling Out: The Origins of Money](https://nakamotoinstitute.org/shelling-out/)" (2002). Accessed 2026-07-07.
[^4]: Shiller, Robert J. "[Narrative Economics](https://paulgp.com/speeches/shiller_2017_aea.pdf)." AEA Presidential Address, *American Economic Review* 107(4), 2017. Accessed 2026-07-07.
[^5]: ByteTree. "[Reflexivity: Nothing Does It Like Bitcoin](https://www.bytetree.com/research/2021/10/reflexivity-nothing-does-it-like-bitcoin/)" (2021), George Soros の reflexivity 理論について. Accessed 2026-07-07.
[^6]: CoinMarketCap. "[Bitcoin Dominance](https://coinmarketcap.com/charts/bitcoin-dominance/)" および Bitcoin / Bitcoin Cash / Bitcoin SV の時価総額（2026-07-07 時点）. Accessed 2026-07-07.
[^7]: Aslam et al. / npj Complexity. "[Bidirectional Granger causality between social-media narratives and asset prices](https://www.nature.com/articles/s44260-025-00042-2)," *npj Complexity* (2025). Accessed 2026-07-07.
[^8]: Cato Institute. "[Narrative Economics](https://www.cato.org/regulation/winter-2019-2020/narrative-economics)," *Regulation* (Winter 2019–2020) — 枠組みの反証可能性への批判. Accessed 2026-07-07.
[^9]: Coinmonks. "[Crypto Narratives 2025–2026: Substance over Speculation](https://medium.com/coinmonks/crypto-narratives-2025-2026-substance-over-speculation-aa72b32be9f1)." Accessed 2026-07-07.
