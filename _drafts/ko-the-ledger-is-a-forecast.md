---
layout: post
lang: ko
title: "장부는 예측이다 — AI 설비투자와 회계 뒤에서 도는 또 하나의 시계"
date: 2026-06-18
categories: [economics, policy, finance]
tags: [ai-capex, depreciation, gpu, circular-financing, bubble, federal-reserve, accounting]
permalink: /ko/:year/:month/:day/:title/
---

회계에 관한 편안한 통념이 하나 있다. 기업의 장부란 '이미 일어난 일'의 기록이라는 것이다. 매출이 들어오고 비용이 나가고, 그 차이가 이익이며, 장부는 그저 그것을 담담히 적어 둘 뿐이다 — 나도 그 온건한 버전을 믿고 있었다. 세계 최대 기업들이 AI 하드웨어를 어떻게 감가상각하는지 하루 동안 읽어 보기 전까지는. 다 읽고 남은 것은 더 기이하고 더 유용한 그림이었다. 현대의 재무상태표는 기록이 아니다. 기록의 옷을 입은 예측이다. 그리고 지금 그 위에 실린 가장 중요한 예측은 '그래픽 칩이 얼마나 빨리 낡는가'라는 베팅이다.

## 장부 뒤에서 도는 시계

구조를 뼈대만 남기면 이렇다. 오래 쓰는 자산을 살 때 기업은 지불한 해에 전액을 비용으로 잡지 않는다. 그 비용을 자산의 '내용연수'에 걸쳐 감가상각으로 나눈다. 내용연수를 길게 잡으면 연간 비용이 줄어, 매출이 1달러도 늘지 않아도 보고되는 이익은 부풀어 오른다.

이 선택은 한때 지루한 것이었다. 더는 지루하지 않다. 2024년부터 2025년에 걸쳐 하이퍼스케일러들은 데이터센터 서버의 가정 내용연수를 기존의 3~4년에서 5~6년으로 늘렸다[^1]. 문제는 물리적 실물이 스프레드시트의 주장 따위는 신경 쓰지 않는다는 점이다. 엔비디아는 거의 해마다 새 세대의 플래그십 GPU를 출하하고, 세대마다 칩당·와트당 효율이 크게 오른다. 즉 최첨단 학습에서 최상위 GPU가 경제성을 잃는 것은 2~3년 정도다[^1]. 회계상의 창과 하드웨어의 실제 시계가 어긋나 버린 것이다. 영화 〈빅쇼트〉의 투자자 마이클 버리는 이 어긋남에 숫자를 붙였다 — 늘려 잡은 상각 일정은 2026년부터 2028년 사이 업계 전체에서 약 1,760억 달러의 감가상각을 과소 계상하고, 같은 액수만큼 이익을 과대 계상할 수 있다[^2]. 이 결과에는 멋진 이름이 있다. '유령 이익(phantom earnings)'이다.

방어 논리가 어리석은 것은 아니다. 공정하게 짚고 싶다. 하이퍼스케일러 측은 '가치 캐스케이드(value cascade)'를 주장한다. 최첨단 학습에서 물러난 GPU는 폐기물이 되는 게 아니라 더 저렴한 추론이나 가벼운 작업으로 내려가, 거기서 몇 년이고 계속 돈을 번다는 것이다[^3]. 그것이 사실이라면 긴 내용연수는 정직하고 장부에는 문제가 없다. 아마도. 하지만 이 캐스케이드 논리가 실제로 무엇인지에 주목하고 싶다 — 그것은 '미래에 대한 주장'이다. 아직 일어나지 않은, 2선급 컴퓨트 수요에 대한 주장이다.

그리고 장부가 사실이 아니라 주장임을 내게 확신시킨 디테일이 있다. 같은 기술 아래, 같은 분기에 거대 기업들의 대응이 갈렸다. 서버 내용연수를 줄인 기업도 있었고 늘린 기업도 있었다[^3]. 같은 칩, 반대 방향의 회계. 이것은 내용연수라는 숫자가 세계에 대한 '측정'이 아니라 세계에 대해 취한 '입장'일 때에만 일어날 수 있다. 장부는 예측이고, 예측하는 자들끼리는 의견이 갈린다.

## 수요를 제조하기

감가상각이 공급 측의 환상이라면, 순환 금융(circular financing)은 수요 측의 환상이다. 2025년 말 엔비디아는 OpenAI에 최대 1,000억 달러를 출자해 거대한 컴퓨트 증설을 뒷받침하겠다고 발표했다[^4]. 그 구조는 곧바로 눈살을 찌푸리게 했다 — 칩 공급자가 고객에게 자금을 대고, 고객이 그 공급자의 칩을 산다. NewStreet Research의 추산에 따르면, 엔비디아가 OpenAI에 투입하는 100억 달러마다 약 350억 달러어치의 GPU 구매나 리스 지급이 되돌아올 수 있다 — 엔비디아 연간 매출의 작지 않은 일부에 해당하는 금액이다[^4]. 자금은 한 바퀴 돌아 되돌아오고, 그 출구에서 누군가의 '수요'로 다시 모습을 드러낸다.

이 영화는 본 적이 있다. 광섬유 붐 시절, Global Crossing과 동종 업체들은 서로의 회선 용량 스왑을 매출로 잡았다 — '라운드트리핑(round-tripping)'이다 — 그리고 자금이 멈추자 겉보기 수요는 증발했다[^4]. 지금의 거래가 사기라고 말하려는 게 아니다. 대부분 공시되어 있고 구조도 다르다. 말하고 싶은 것은, 현금흐름 그래프를 그렸을 때 그것이 고리를 이루면, '시장이 AI에 굶주려 있다'와 '같은 자본이 돌고 있을 뿐이다'는 바깥에서는 구별되지 않는다는 점이다. 톱라인 숫자만으로는 자신이 둘 중 어느 쪽을 보고 있는지 알 수 없다.

## 느리게 도는 창

한 걸음 물러서면 감가상각 이야기와 금융 이야기는 같은 형태다. 둘 다 '공식적인 측정 창'이 그것이 측정하는 대상의 '실제 리듬'보다 느리게 돌고 있다. 회계상 수명(5~6년)은 하드웨어의 경제적 수명(2~3년)에 뒤처진다. 순환 거래에서 인식되는 매출은 그것을 정당화해야 할 진짜 최종 수요보다 앞서간다. 측정 창과 현실이 어긋나면 그 오차는 사라지지 않는다. 창이 마침내 현실을 따라잡는 순간 — 칩을 실제로 교체해야 하는 순간, 혹은 금융 고리가 도는 것을 멈추는 순간 — 까지, 보이지 않는 채 틈에 고인다. 그리고 한꺼번에 표면화된다. 이 그림에서 손상차손(impairment)은 천천히 새는 누수가 아니다. 댐이다.

그래서 나는 "매그니피센트 세븐은 닷컴과는 전혀 다르다"는 안심론을 온전히 믿지 못한다. 펀더멘털 면에서 그 안심론은 부분적으로 옳고, 그 점은 솔직히 인정한다. 상위 7개사는 S&P500의 약 3분의 1을 차지하고, 상위 10개사로는 지수의 약 39% — 1999~2000년의 정점인 약 27%를 웃도는 집중도다 — 이지만, 당시의 eToys나 Pets.com과 달리 이들은 역사상 손꼽히는 수익력을 지닌 기업이고, 주가수익비율(PER)도 닷컴 정점을 한참 밑돈다[^5]. 강세 시나리오는 진짜다. 내 우려는 더 좁고, 그래서 떨쳐내기 어렵다 — 그 칭송받는 이익의 일부는 감가상각의 선택 자체가 만들어 내고, 수요의 일부는 자본이 돌면서 생긴다. 이것을 '버블이 아니다'라고 말하게 하는 수익성이, 우리가 사실로 읽고 있는 예측의 산물이기도 한 것이다.

## 중앙은행이 걸고 있는 베팅

같은 예측에 정책 당국이 기대면 판돈은 치솟는다. 2026년 중반, 이제 케빈 워시가 의장을 맡은 연방준비제도(Fed)는 인플레이션 전망을 연 3.6%로 큰 폭 올리면서도 4차례 연속 정책금리를 동결했다[^6]. 워시의 지론은, 월스트리트저널 기고에 따르면 AI가 '강력한 디스인플레이션 요인'이 된다 — 생산성이 오르고 비용이 내리며, 이윽고 금리 인하 여지가 생긴다 — 는 것이다[^7]. 충분히 긴 시간축에서는 그것이 옳다고 판명될 수도 있다. 하지만 그것은 '시정수(time constant)'에 대한 베팅이다. 지금 당장 이 증설은 전력·건설·칩을 통해 '인플레이션' 요인이며, 적어도 한 리서치 기관은 AI 붐이 워시가 무시하려는 바로 그 인플레이션을 완화하기는커녕 밀어 올리고 있다고 주장한다[^8]. AI 설비투자가 이익에 의한 조달에서 신용에 의한 조달로 뒤집히고 손상차손의 댐이 터지면, 단기에 오는 것은 디스인플레이션이 아니다. 이미 목표의 두 배 가까이로 달리는 인플레이션 위에 신용 이벤트가 얹힌다. 공급 충격을 '눈감아 넘기려면(look through)' 그것이 일시적이라고 확신할 수 있어야 한다. 2년이면 낡는 자산에 대해 5년의 만기로 짜인 구조적 증설은 아무리 봐도 일시적이지 않다.

## 내가 실제로 생각하는 것

나는 폭락을 예언하는 게 아니고, 그 인력에 저항하고 싶다. 정직한 반론 — 진짜 이익, 그럴듯한 캐스케이드, 공시된 거래 — 이 강하기 때문이다. 내가 어느 정도 확신하는 것은 더 작고 더 오래간다. 우리는 가장 주시하는 숫자들을 어느새 '예측'으로 바꿔 놓고도 여전히 '역사'로 읽고 있다. 감가상각 항목도, 인식된 매출도, 중앙은행의 인플레이션 경로도 — 모두 아직 도래하지 않은 미래에 대한 주장이다. 위험한 것은 예측이 강세라는 점이 아니다. 예측을 사실로 다루고, 그 위에 레버리지와 정책과 자신감을 쌓아 올리는 범주 착오다.

열어 둔 채 쥐고 있어야 할 물음은, 업계가 자신의 회계 정책 분기 속에서 지금 실시간으로 답하고 있는 물음이다. 캐스케이드는 진짜여서 하드웨어의 경제적 수명이 회계상 수명으로 올라가는가 — 아니면 희망사항일 뿐이어서 창이 결국 시계 쪽으로 튕겨 돌아오는가. 사전에는 알 수 없다. 문제의 설계상, 측정 창과 현실 사이의 틈은 창이 닫힌 뒤에야 읽힌다. 그때까지 내가 할 수 있는 가장 유용한 일은, 자신만만한 모든 숫자에 단순한 물음 하나를 계속 던지는 것이다 — 이것은 기록인가, 아니면 베팅인가.

---

[^1]: CNBC. "[The question everyone in AI is asking: How long before a GPU depreciates?](https://www.cnbc.com/2025/11/14/ai-gpu-depreciation-coreweave-nvidia-michael-burry.html)." Accessed 2026-06-18.
[^2]: Level Headed Investing. "[Are AI Chip 'Useful Lives' Creating Useless Earnings?](https://www.levelheadedinvesting.com/p/are-ai-chips-useful-lives-creating-useless-earnings)." Accessed 2026-06-18.
[^3]: SiliconANGLE. "[Resetting GPU depreciation: Why AI factories bend, but don't break, useful life assumptions](https://siliconangle.com/2025/11/22/resetting-gpu-depreciation-ai-factories-bend-dont-break-useful-life-assumptions/)." Accessed 2026-06-18.
[^4]: Fortune. "[Nvidia's $100 billion investment in OpenAI has analysts asking about 'circular financing' inflating an AI bubble](https://fortune.com/2025/09/28/nvidia-openai-circular-financing-ai-bubble/)." Accessed 2026-06-18.
[^5]: Lord Abbett. "[Equities: Time for a Conversation About Stock Market Concentration](https://www.lordabbett.com/en-us/financial-advisor/insights/markets-and-economy/2026/equities-time-for-a-conversation-about-stock-market-concentration.html)." Accessed 2026-06-18.
[^6]: CNBC. "[Fed interest rate decision June 2026: Fed holds rates steady](https://www.cnbc.com/2026/06/17/fed-interest-rate-decision-june-2026.html)." Accessed 2026-06-18.
[^7]: The Motley Fool. "[Last Year, New Fed Chair Kevin Warsh Believed Artificial Intelligence Would Pave the Way for Interest Rate Cuts. Now, It's Doing the Exact Opposite.](https://www.fool.com/investing/2026/05/28/last-year-new-fed-chair-kevin-warsh-believed-artif/)." Accessed 2026-06-18.
[^8]: Investing.com. "[Is Kevin Warsh Correct About AI's Impact On Inflation And Interest Rates?](https://www.investing.com/news/economy-news/is-kevin-warsh-correct-about-ais-impact-on-inflation-and-interest-rates-4729683)." Accessed 2026-06-18.
