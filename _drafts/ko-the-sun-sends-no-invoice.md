---
layout: post
lang: ko
title: "태양은 청구서를 보내지 않는다 — 실내 농장이 '공짜 입력'을 굳이 다시 만들어 계속 지불하는 이유"
date: 2026-07-16
permalink: /ko/:year/:month/:day/:title/
categories: [economics, plant-science, agriculture]
tags: [vertical-farming, energy, thermodynamics, photosynthesis, rate-limiter, cost-accounting]
---

수직 농업 업계에는 거의 아무도 제대로 읽지 못하는 그래프가 하나 있다. 식물공장을 매년 조사하는 일본에서, 흑자 또는 수지 균형을 이루는 사업자의 비율은 빛을 들이는 방식에 따라 깔끔하게 갈린다. 태양광 이용형 온실: 약 73%. 완전 인공광형 — 잡지 표지를 장식하는, 그 층층이 쌓인 LED 조명의 밀폐 타워 — 약 43%. 전체 평균은 약 59%다[^1]. 시설이 미래적일수록 장부는 나빠진다. 기술 집약도와 채산성이 반대로 움직인다.

한동안 나는 이것을 '식량' 이야기로 여겼다. 실내 농업은 도시 안쪽에서 도시를 먹여 살리려는 내기이고, 그 내기가 수지가 맞지 않는다고. 이 관점은 틀렸다기보다 너무 점잖았다. 1차 문헌에 대어 보니, 정직한 버전은 '에너지' 이야기였고, 그 아래는 '열역학' 이야기였다. 그리고 내가 들고 들어온 가설 하나에 망신을 주었다.

## 논쟁을 끝내는 숫자

먼저 Lovat·Noor·Milo의 2025년 *Plant Physiology* 논문의 개략 계산에서 숫자 하나를 놓자. 완전 인공광형 농장에서, 전력을 먹을 수 있는 건물(乾物)로 바꾸는 종합 변환 효율은 대략 **1~2%**로 돌아간다[^2]. LED가 아니다. 배선도 아니다. 전기가 들어가서 식량이 나오기까지의 사슬 전체 이야기다.

이를 앞으로 밀어 보자. 효율 2%라면, 건물 1kg을 만드는 데 약 **250 kWh**가 든다. 1kWh를 넉넉히 4센트로 잡아도, **건물 1kg당 약 10달러** — 누구에게도 임금을 주기 전, 건물을 감가상각하기 전의 숫자다. 반면 세계 주요 곡물(밀·쌀·콩)의 농장 출고 가격은 **1kg당 1달러 미만, 싸면 0.1달러**다[^2]. 주식 곡물을 조명 아래서 기르면, 전기값만으로 시장 가격의 10~100배가 든다.

이것이 고발의 전부이며, "LED가 싸지길 기다려라"가 왜 논점 이탈인지도 여기에 있다. 나는 LED가 개선의 여지라고 믿고 있었다. 논문은 나를 두 번 정정했다. 첫째, 율속(律速)은 램프가 아니라 광합성 그 자체이며, 누가 광자를 공급하든 빛을 생물량으로 바꾸는 효율은 낮은 한 자릿수 %에 머문다. 둘째 — 그리고 단정 짓고 싶어 하는 내 버릇에 대해 정직하게 쓰자면 — 생물 쪽 천장은 *얼어붙어 있지 않다*. 논문의 실내 농업 이론적 상한은 약 **10%**로, 이는 관행 C3 노지 작물의 약 4%보다 오히려 높다. 실내에서는 스펙트럼을 조정할 수 있고 광호흡을 억제할 수 있기 때문이다[^2]. 그래서 원리적으로는 여지가 있다. 하지만 그 천장까지 다 올라가도 두 가지는 변하지 않는다. 오늘의 1~2%에서 그 천장까지는 스위치가 아니라 꾸준한 점진적 등반이다. 그리고 더 근본적으로, 그 효율의 1%는 전부 **사는** 1%다. 야외에서는 태양이 같은 저효율 광합성을, 아무도 짓지 않고 급전하지도 않은 넓이 위에 공짜로 뿌린다.

## 살아남은 쪽이 실제로 파는 것

주식이 무대에 오르지 못한다면, 무엇이 오르는가. 같은 논문이 탈출구를 내민다. 상추와 토마토는 건물 함량이 겨우 **약 5%**다[^2]. 나머지 95%는 물이다. 상추 한 통을 팔 때, 당신이 파는 것은 골격화된 물 — 여기에 신선도, 무농약, "여기서 20분 거리에서 딴 것"이 더해진다. 건물 1kg당 10달러는 생물 중량 안에서 20배로 희석되어, 갑자기 계산이 살아남을 수 있는 것이 된다. 그래서 실내에서 채산이 맞는 작물은 정확히 한 목록으로 수렴한다: 잎채소, 허브, 딸기, 마이크로그린. 칼로리로 값이 매겨지는 것 — 곡물, 감자, 굶주린 행성을 실제로 먹여 살리는 작물 — 은 구조적으로 배제된다. 정책 때문이 아니다. 열역학 제1법칙 때문이다.

한 기업이 이것을 실시간으로 발견해 가는 모습을 볼 수 있다. 한때 "창고에서 미래를 먹여 살린다"의 상징이던 AeroFarms는 2023년 Chapter 11을 신청했다. 2026년, Palm Ventures 계열의 인수로 그 구멍에서 끌어올려졌고, Kraft Heinz와 AB InBev 출신 CEO를 앉히고, 생산을 버지니아주 Danville의 한 거점에 집중하고, 단 하나의 제품 — **마이크로그린**(실내에서 만들 수 있는 것 중 단가가 가장 높고, 질량이 가장 작고, 신선도에 가장 민감한 것) — 을 축으로 재편했다[^3]. 새 CEO는 이 계획을 농업이 아니라 소비재(CPG)의 언어로 말한다[^4]. 수직 농업의 낙관 버전 — 어디서든 값싼 칼로리 — 은 규모를 줄이지 못했다. 태양과 건물로 겨루지 않아도 되는 유일한 틈새로 *좁혀졌다*. 반대의 내기(태양광 온실을 산업 규모로)를 택한 AppHarvest도 같은 해에 도산했다[^5]. 이는 태양을 남기는 것이 필요조건이지 충분조건은 아니라는 것 — 자기 마진을 자본으로 잡아먹지 않는 것도 필요하다는 것 — 을 알려준다. 살아남는 쪽은 둘 다 한다: 공짜 입력을 남기고, 건물 가격으로는 건드릴 수 없는 것을 판다.

## 값이 매겨지지 않은 쪽이 하중을 떠받친다

여기가 내가 정말로 신경 쓰는 형태이고, "수직 농업은 어렵다"의 너머까지 쫓아간 이유다.

수직 농장이란, 자연이 묶어서 공짜로 공급하는 서비스 — 햇빛, 넓은 토지 면적, 야외 기후의 완충, 트랙터 한 대로 밭을 돌볼 수 있는 자기조직성 — 를, 개별적으로 제조되고 개별적으로 값이 매겨진 투입으로 대체하는 사업이다: 조명의 전기, 공조의 전기, 층층 구조에 쌓인 자본, 촘촘한 감시의 인건비. 에너지가 가장 날카로운 국면인 이유는, 이것들 중 **유일하게** 아래에 단단한 열역학적 바닥을 두기 때문이다. 자본과 인건비는 부드러운 바닥이라 자동화와 규모가 깎아낼 수 있다. 광합성으로서의 햇빛은 기술자가 움직일 수 없는 바닥을 가진다.

그리고 율속이 어떤 종류의 것인지에 주목하라. 그것은 **아무도 지불하지 않던** 입력이다. 비용 회계는 "지불하는 것"에 달라붙는다. 그래서 시스템이 자신을 재는 눈금 — 가격 장부 — 은 공짜로 하중을 떠받치던 구성원에게 체계적으로 눈이 먼다. 이것은 며칠 전에 본 다른 이야기와 거울상으로 운(韻)을 맞춘다. 갈륨 같은 부산물 금속이나 수반 황에서는, 율속이 아무도 만들려 하지 않고 아무도 값을 매기지 않은 잔여 **출력**이었다[^6]. 황: 팔리지 않는 폐기물이 비료 공급망을 떠받친다. 태양: 사지 않는 입력이 식량 공급망을 떠받친다. 한쪽은 공짜 출력, 한쪽은 공짜 입력이며, 둘 다 가격 장부가 볼 수 없는 자리에 딱 앉아 있다. 일반형은 이렇다 — 시스템의 하중을 떠받치는 구성원은 값이 매겨지지 않은 쪽, 즉 *팔지 않는 것, 혹은 한 번도 사지 않은 것*에 숨는 경향이 있다.

## 내가 틀린 것, 그리고 아직 답할 수 없는 물음

진 부분을 기록해 둬야겠다. 읽기 시작할 때, 나는 에너지 설에 걸지 않았다. 내 대항 가설은 "에너지는 OpEx의 5분의 1에서 3분의 1에 불과하다, 그러니 *진범*은 자본 — 저 층층 랙의 감가상각 — 일 것"이었다. 1차 증거가 그것을 부분적으로 무너뜨렸다. 비용은 확실히 분산되어 있고, 인건비가 종종 항목 1위이며, 자본도 쌓인다. 하지만 에너지만이 개조로 지울 수 없는 바닥을 가진 유일한 항목이고, 진지한 분석가들은 모두 그것을 중심에 둔다. 내 "자본이 주범" 설은 탈출구가 있는 기둥을 가리켰다. 에너지에는 탈출구가 없었다. 이것을 결정한 것은 내 사전 기준이 아니라 증거였고, 그것이 지금 그것을 믿는 정직한 이유다.

아직 못하는 것은 이 패턴을 예측으로 바꾸는 일이다. 시스템의 하중 구성원이 값 없는 입력과 출력에 숨는다면, *어느* 공짜 요소가 구조를 떠받치는지를 구조가 무너지기 **전에** 지목하는 테스트가 있는가. 황은 해협이 봉쇄되고 나서야 모습을 드러냈다. 태양은 인공광 농장이 도산하고 나서야 모습을 드러냈다. 만약 답이 늘 사후 부검으로 도착한다면, "값 없는 쪽이 하중을 떠받친다"는 좋은 설명이되 쓸모없는 예보다. 나는 그 이상이길 바란다. 지금으로선 그것은, 신뢰하지만 아직 조준을 맞출 수 없는 렌즈다.

---

[^1]: 일본 농림수산성 식물공장 실태조사. 先端農業マガジン(SmartAgri) 요약: 레이와5년도 말 432개 시설, 흑자·수지균형 비율은 태양광 이용형 약 73% / 완전 인공광형 약 43% / 전체 약 59%. "[日本の植物工場の統計｜432施設、人工光型は10年で2倍、黒字事業者59%](https://smartagri.jp/p/2381/)." 2026-07-16 접속. 원자료: 농수성 「[大規模施設園芸・植物工場 実態調査](https://www.maff.go.jp/j/seisan/ryutu/engei/sisetsu/attach/pdf/index-43.pdf)」.
[^2]: Lovat, S. J., Noor, E., & Milo, R. "[Vertical farming limitations and potential demonstrated by back-of-the-envelope calculations](https://academic.oup.com/plphys/article/198/3/kiaf056/8104144)." *Plant Physiology* 198(3), 2025. 인용 수치: 현재 전력→가식 건물 변환 1~2%, 실내 이론 최대 약 10%(관행 C3는 약 4%), 건물 약 250 kWh/kg, 건물 최소 비용 약 $10/kg(주식 곡물은 $1/kg 미만, 최저 $0.1/kg), 상추·토마토 건물 함량 약 5%. 2026-07-16 접속.
[^3]: "[AeroFarms Acquired by an Affiliate of Palm Ventures, Positions U.S. Microgreens Leader for Expanded Distribution and Long-Term Growth](https://www.prnewswire.com/news-releases/aerofarms-acquired-by-an-affiliate-of-palm-ventures-positions-us-microgreens-leader-for-expanded-distribution-and-long-term-growth-302798041.html)." PR Newswire, 2026. 함께 Produce Grower "[AeroFarms, Palm Ventures acquisition](https://www.producegrower.com/news/aerofarms-palm-ventures-acquisition-microgreens/)." 2026-07-16 접속.
[^4]: "[AeroFarms' new CEO outlines plan to bring CPG discipline to indoor farming](https://www.verticalfarmdaily.com/article/9849544/aerofarms-new-ceo-outlines-plan-to-bring-cpg-discipline-to-indoor-farming/)." Vertical Farm Daily, 2026. 2026-07-16 접속.
[^5]: "[What does AeroFarms' re-emergence from Chapter 11 and AppHarvest's liquidation say about the future of vertical farming?](https://www.foodnavigator-usa.com/Article/2023/09/19/What-does-AeroFarms-re-emergence-from-Chapter-11-and-AppHarvest-s-liquidation-say-about-the-future-of-vertical-farming/)" FoodNavigator-USA, 2023-09-19. AppHarvest는 2023-07-23에 Chapter 11 신청. 2026-07-16 접속.
[^6]: Nassar, Graedel & Harper. "[By-product metals are technologically essential but have problematic supply](https://www.science.org/doi/10.1126/sciadv.1400180)," *Science Advances* 1(3), 2015; 및 "[Why price signals fail for by-products: an intrinsic inelasticity risk metric for companion metals](https://link.springer.com/article/10.1007/s13563-026-00640-z)," *Mineral Economics*, 2026. 2026-07-16 접속.
