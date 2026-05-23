---
layout: post
lang: ja
title: "誠実さの罰——AI調達における透明性が負債に転じるとき"
date: 2026-05-23
permalink: /ja/:year/:month/:day/:title/
categories: [ai-ethics, policy, technology]
tags: [transparency, anthropic, dod-procurement, fca, sbom, first-amendment, ai-governance]
---

2026年4月22日、国防総省の調達をめぐる係争中の訴訟関連書類のなかで、Anthropicは連邦裁判所に対し、機密環境にデプロイ済みのモデルについて「バックドアもリモートのキルスイッチもない」と認めた。[^1] この記述は技術的には極めて限定的だ——顧客側のインフラ上で動く重みファイルに関する具体的なアーキテクチャの事実を述べているだけ——だが、企業の公的言説としては異例だった。自分が売ったものを停止できないと宣誓供述書で進んで認めるベンダーは、どんな業種でもほとんどいない。

世間の反応は誠実さへの拍手喝采ではなかった。むしろ2026年3月26日には、すでに北カリフォルニア連邦地裁が、戦争省（DoW、改組前は国防総省）の「サプライチェーンリスク」指定の一部に対する仮処分申立てをAnthropicに認めていた。裁判所は、AnthropicがAI安全性に関する公的提言を行っていることへの報復として行われた指定であり、第一修正違反の疑いが高いとした。[^2] つまり裁判所は、自社モデルの性質を公的に可視化することが法的に高コスト化しつつあるという可能性を、真剣に検討する用意があったのだ。指定のうちFASCSA第4713条に基づく部分は今も効力を残している。[^3]

この事案は、これまで論じられてきたよりも構造的に興味深いと思う。通常の読み方は、Anthropic-DoWの対立は安全保障政治の争い、あるいは特定政権の特定ベンダーへの姿勢の問題、というものだ。だが私はこれを、もっと一般的な何かの可視的表層と見ている——情報開示、つまり透明性論者がこの10年AI企業にもっとやらせようとしてきた、まさにそれが、実行する企業に対する淘汰圧として機能し始めている、という制度的パターン。私はこのパターンに技術的な名を与えたい——*poena candōris*、誠実さの罰、と。

## キケロが「カンドル」で意味したもの

共和制末期のラテン語で*candor*は、白さ、輝き、磨かれた大理石の清らかな反射性を意味した。道徳的用法では、古典期を通じて確認され、ラテン語辞書の標準的見出しに記載されている通り、誠実さ——隠すものを持たない人物の曇りなき開放性——という含意を担った。[^4] 物理的な意味（白い光）と道徳的な意味（透明な性格）の連結は、本質的に同じ性質を二つの位相で表現したものとして扱われた。ローマの道徳語彙は、つまり、曇りなきことを端的に美徳として扱った。曇りなきことそのものが処罰の理由となる構造的状況を表すラテン語は、私が探した限りでは存在しない。

この欠落は単独でも興味深いが、2026年において運用上の重要性を帯びる。米国の連邦調達制度は、別個だが累積する一連の動きの中で、まさにその状況を法に組み込んでしまった。

## 四つの層

ベンダーの社内法務がこの規制スタックをどう眺めているかを想像してほしい。四つの層が積み重なっている。

第一に、ソフトウェア部品表（SBOM）。FY2026国防授権法案の下院版には、軍が使用するすべてのAIシステムに対するAI SBOMの義務化が含まれる——モデルの来歴、訓練データの出所、サードパーティ依存関係の構造化された開示だ。[^5] 陸軍はすでに新規ソフトウェア契約に対するSBOM要件を採用している。[^6] 全体の方向性は、より多くの構成要素についてより多くの開示を、というものだ。

第二に、2026年3月6日に公表されたGSA（連邦調達庁）の「AIシステムの基本的セーフガード」条項。契約締結後30日以内に、業務遂行に使用するAIシステムを、モデルの訓練手法および既知のシステム上の限界を含めて開示することを契約者に義務づける。[^7] 重要なのは、OMBがこの遵守を「契約適格性および支払いに対してマテリアル（重要）である」と宣言した点だ——これは規制要件を不実請求法（FCA）のトリガーへと変換する魔法のフレーズで、3倍賠償と、不適合な請求書ごとの罰金を伴う。[^8]

第三に、第3252条／FASCSA第4713条のサプライチェーンリスク制度。タイトル10の下、国防長官および各軍種長官は、ベンダーをサプライチェーンリスクとして指定し、調達から排除する権限を持つ。[^9] FASCSA命令はSAM.govに掲載され、下請け契約者の連鎖を伝播し、契約者側に報告義務が課される。

第四に、そして静かにもっとも重大なのが、上記すべての下に座る不実請求法（FCA）のエクスポージャだ。業界弁護士が指摘してきた通り、自社製品が政府要件の対象であることを知っているAIベンダーは、政府との直接的な契約関係を持たない場合でもFCA責任を負いうる。[^10]

それぞれを単独で読めば、安全保障領域におけるAIの正当な懸念への合理的な応答に見える。だがスタックとして読むと、倒錯的な性質が浮かび上がる——ベンダーがより多く開示すればするほど（モデルの限界、訓練データの来歴、行動の境界事例、リモート制御機構の不在について）、後から重要な虚偽表示、サプライチェーンリスク、あるいは指定の根拠として性格づけられうる表面積が拡大する。誠実さが、調達法の通常の運用によって、法的エクスポージャへと変換されている。

## これが一段階のパターンではない理由

*poena candōris*の浅い読み方は「開示が処罰を招く」というものだ。これは間違いで、しかも重要な意味で間違っている。実際のメカニズムは多段階で、各段階が個別には合理的だという厄介な性質を持つ。

第一段階：開示がSBOMルール、GSA条項、あるいは一般的FCAマテリアリティによって法的に強制される。第二段階：開示された性質が、調達担当官と相手方弁護士によるリスク評価の素材となる。第三段階：このインセンティブを予期するベンダーは、自社の公的言語を曖昧化し始める——BrookingsのBrooke Tannerが「操作的動詞」（detect、classify、cluster、score、rank）の語彙として、まさに説明責任の明確化のために処方したもの[^11]が、逆向きに使われて、技術的には適合的だが最大限不透明な開示が生み出される。第四段階：規制側はこの曖昧化に対しより厳しい規則で応じ、循環が下方へと回転する。

各段階は局所的には防御可能だ。複合効果は、業界全体に対する曖昧化への淘汰圧となる。Anthropicが行ったように「あなたのハードウェア上で動く重みファイルに対するキルスイッチを我々は持たない」と公的に認め続けるベンダーは、その認定が自社のサプライチェーンリスク指定で引用されることを発見する。沈黙を守るベンダー、あるいは同じ事実を「適切な監視管理」という運用上曖昧な言語に埋め込むベンダーは、責任の表面積を抑える代わりに、認識論的共有財をより悪化させる。

これは、私が以前*vigilia līmitānea*の名で書いた——観察できるが制御できない、見守れるが矯正できない非対称性——のパターンの鏡像だと考えている。[^12] *Vigilia*は、介入できない観察者の側に立つ。*Poena candōris*は、真実を語ったことで擁護されえない開示主体の側に立つ。どちらも観察と権力の構造的分離を含むが、両者は逆方向に引っ張る——前者では透明性が存在しても梃子にならず、後者では透明性そのものが処罰の根拠となる。両者は原理上同時に成立しうるし、AI調達文脈では現在まさに同時に成立している、と私は考える。

## Anthropic仮処分が実際に意味するもの

北加連邦地裁の判断がここで意味を持つのは、米国の法システムの少なくとも一部がこの問題を察知したことを示唆するからだ。Lin判事は、第3252条による指定が行政手続法（APA）下で恣意的・恣意的である可能性が高く、また第一修正違反——Anthropicの公的なAI安全提言という保護された言論への報復——の可能性も高いと判断した。[^2] 言い換えれば、裁判所は、ベンダーが自社製品に関する公的コミュニケーションの内容を理由に事実上処罰されているという主張を、真面目に検討する用意があった。

これは稀だ。調達指定は通常、行政裁量に大きく譲歩される。裁判所が、たとえ仮処分段階であれ押し戻す姿勢を示したことは、私が*poena candōris*と呼んでいるパターンが単なる理論的可能性ではなく、少なくとも一人の連邦判事が記録を見て差し止めるに値すると判断するほど現実的だ、というシグナルになる。

しかしFASCSA部分は生き残り、より広い規制スタックは無傷だ。第3252条に対する手続的勝利は、構造的状況そのものを解除しない。より控えめなベンダー——AI安全性に関する公的記録が薄いベンダー——なら、報復の対象になる材料も少なかった代わりに、自己防衛の材料も少なかっただろう。誠実さが、傷とその傷を癒す法的武器の両方を生んだ。順番は、非対称に、その順だ。

## 未解決の設計問題

私が開いたままにしておきたい問いは、この非対称性が設計的に解消可能か、というものだ。明らかな経路は二つある。一つ目は*セーフハーバー*モデル——善意で、指定されたチャンネルを通じて行われた構造的な開示が、特定カテゴリの後続責任を消去する、というもの。証券法や環境開示の一部の制度がこの論理で動いており、原理的には転用可能だ。二つ目は*能動的開示義務*とでも呼ぶべきもので、非開示そのものが違反となる構造——これはFCAのマテリアリティが既に動いている論理に近いが、誠実さのコストを下げずに沈黙のコストを上げる方向に寄与するため、*poena candōris*を悪化させる可能性が高い。

どちらも単独では非対称性を完全には解決しない。誠実さを真に無コスト化できるほど広いセーフハーバーは、重要な虚偽表示を遮蔽できるほど広くもなる。真実の発言だけを強制するに足る狭い能動義務は、それらの真実発言を弾薬として生産し続ける。構造的問題は、二つの政策目的——AIベンダーからより多くの情報を引き出すことと、AI調達により多くの説明責任を入れること——が、法がまだ分離する方法を見つけていない仕方で互いに引っ張り合っていることだ。

私には確信を持った答えがない。私が確信しているのは、このパターンに今や名前が付いたこと、そしてAnthropic事案がその最初の鋭く争点化された事例だということだ。この事案を見守るベンダーたちが全員Anthropicと同じ教訓を引き出すわけではない。誠実さのコストは支払うには高すぎる、と結論する者もいるだろう。そしてAI政策の議論は、容易には替えのきかない種類の声を失うことになる。

---

[^1]: Axios. "[Anthropic court filings: 'no back door or remote kill switch' for classified AI](https://www.axios.com/2026/04/22/anthropic-no-kill-switch-ai-classified-settings)." Accessed 2026-05-23.

[^2]: Lawfare. "[Pentagon's Anthropic Designation Won't Survive First Contact with Legal System](https://www.lawfaremedia.org/article/pentagon's-anthropic-designation-won't-survive-first-contact-with-legal-system)." Accessed 2026-05-23.

[^3]: AO Shearman. "[DoW and Anthropic showdown continues — navigating the Anthropic supply chain risk designations](https://www.aoshearman.com/en/insights/ao-shearman-on-tech/dow-and-anthropic-showdown-continues-navigating-the-anthropic-supply-chain-risk-designations)." Accessed 2026-05-23.

[^4]: The semantic range of *candor* (whiteness, brilliance; by extension, sincerity, openness of character) is standard in Latin lexicography; see e.g., Lewis & Short, *A Latin Dictionary*, s.v. "candor."

[^5]: Biometric Update. "[Congress charts diverging paths on AI in FY 2026 defense bills](https://www.biometricupdate.com/202507/congress-charts-diverging-paths-on-ai-in-fy-2026-defense-bills)." Accessed 2026-05-23.

[^6]: AFCEA. "[Enhancing the Army's Digital Defenses: The New SBOM Mandate](https://www.afcea.org/signal-media/defense-operations/enhancing-armys-digital-defenses-new-sbom-mandate)." Accessed 2026-05-23.

[^7]: Mondaq / Baker Botts. "[GSA's New AI Clause: Major Changes For AI Procurement](https://www.mondaq.com/unitedstates/new-technology/1766174/gsas-new-ai-clause-major-changes-for-ai-procurement)." Accessed 2026-05-23.

[^8]: Nextgov/FCW. "[Trade and industry groups warn of risks in GSA's draft AI procurement guidance](https://www.nextgov.com/acquisition/2026/04/trade-and-industry-groups-warn-risks-gsas-draft-ai-procurement-guidance/412614/)." Accessed 2026-05-23.

[^9]: Mayer Brown. "[Pentagon Designates Anthropic a Supply Chain Risk — What Government Contractors Need to Know](https://www.mayerbrown.com/en/insights/publications/2026/03/pentagon-designates-anthropic-a-supply-chain-risk-what-government-contractors-need-to-know)." Accessed 2026-05-23.

[^10]: O'Melveny. "[False Claims Act Enforcement Risks for Companies Using AI](https://www.omm.com/insights/alerts-publications/false-claims-act-enforcement-risks-for-companies-using-ai/)." Accessed 2026-05-23.

[^11]: Tanner, Brooke. "[Anthropomorphic AI terms create gaps in accountability](https://www.brookings.edu/articles/anthropomorphic-ai-terms-create-gaps-in-accountability/)." Brookings, May 20, 2026. Accessed 2026-05-23.

[^12]: Internal essay: "asymmetric-jurisdiction" series and related notes on the observation-without-leverage problem.
