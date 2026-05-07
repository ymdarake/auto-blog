---
layout: post
lang: ko
title: "Bio-Inspired의 두 층위 ── 스케줄러가 생물학을 빌릴 때, 무엇이 진짜인가"
date: 2026-05-07
permalink: /ko/:year/:month/:day/:title/
categories: [systems-programming, technology]
tags: [linux-kernel, sched_ext, bpf, bio-inspired, metaheuristics, scheduler]
---

지난 2년 동안 Linux 커널 스케줄링에 작은 르네상스가 일어났다. 10년 넘게 거의 독점하다시피 해 온 Completely Fair Scheduler에 갑자기 경쟁자가 등장했고, 그중 일부는 "생물학적 영감"을 정면에 내세우고 있다. tissue P system 기반 태스크 분배, LSTM을 이용한 다음 태스크 예측, "shallow brain" 아키텍처 같은 제목의 논문이 커널 메일링 리스트로 흘러 들어온다. 곁눈으로 본 사람이라면 "운영체제가 점점 생물학적이 되고 있다"고 읽고 싶어질 것이다. 나는 그런 독해를 권하지 않는다.

이 흐름에는 두 개의 층이 있고, 둘을 섞는 것은 쉽지만 비싼 대가를 치른다. 한 층은 구조적으로 진지한 의미에서 bio-inspired다. 다른 한 층은 Kenneth Sörensen이 2015년 *International Transactions in Operational Research*에 실은 논문에서 비판한 것── 구현 단계로 내려가는 순간 생물학적 프레이밍이 녹아 사라지는 알고리즘 군──에 해당한다.[^1] 잡음의 대부분은 두 번째 층에 모이고, 신호의 대부분은 첫 번째 층에 모인다. 그리고 가장 주목받는 논문일수록 잡음 쪽에 자리잡는 경향이 있다.

## 도착한 "기판"

내가 옹호하고 싶은 층은, 실행 중에 BPF 프로그램으로 스케줄링 정책을 동적으로 적재할 수 있게 된 커널의 새로운 능력이다. 이 기능의 이름이 sched_ext이고, Linux mainline에는 6.12 릴리스에 포함되어 들어갔으며, Linus Torvalds가 2024년 11월 17일에 stable 태그를 달았다.[^2] 메커니즘 자체는 평범하지만 함의는 평범하지 않다. BPF로 작성하여 바이트코드로 컴파일한 스케줄링 정책을, 커널 재빌드 없이 실행 중인 시스템에 주입할 수 있다. 적재된 정책이 잘못 동작해 runnable 상태인 태스크를 dispatch하지 못하면, 커널이 stall을 감지해 자동으로 fair-class 스케줄러로 fallback한다.

이 층을 진지하게 봐야 한다고 생각하는 이유는 두 가지 설계 결정 때문이다. 첫째, 메커니즘은 커널이 보유하고 정책만 자유롭게 떠 있게 만든 점. 이건 단순한 공학적 편의가 아니라 생물학이 일상적으로 사용하는 구조적 분리다. 세포막은 기판이고, 그 사이를 통과하는 분자는 정책이다. 기판은 메시지를 부호화하지 않는다. 둘째, failsafe revert. 정책이 실패해도 시스템은 충돌하지 않고 멈춰 있지도 않다. 알려진 양호한 기판으로 되돌아가 계속 동작한다. 생물이 일상적으로 하는 일이고, 이걸 "낭만적인 비유"로 받아들일 필요는 없다. 같은 종류의 분리를 다른 문제에 적용한 것일 뿐이다.

역사도 한 줄 적어 둘 가치가 있다. sched_ext의 코어 인프라는 Meta의 Tejun Heo가 개발했다. 그 위에서 동작하는 BPF 스케줄러 가운데 가장 성공적인 축에 속하는 LAVD(Latency-criticality Aware Virtual Deadline)는 Igalia에서 개발되었고, 처음에는 Valve의 Steam Deck에서 게임 중 발생하는 stutter를 줄이기 위한 목적으로 만들어졌다. 2025년 12월 도쿄에서 열린 Linux Plumbers Conference에서, Meta의 엔지니어 두 명이 이 LAVD를 변형해 Meta의 새로운 기본 fleet 스케줄러로 발표했다.[^3] 휴대용 게임기에서 데이터센터 fleet의 기본값으로 흘러간 경로는 통상적인 hyperscaler→consumer 흐름의 역방향이고, 이 부분에서 한 박자 멈출 만하다.

## 왜 콘솔 스케줄러가 데이터센터를 먹었는가

콘솔 게이밍은 독특한 조합을 가진다. 사이클당 계산량은 그렇게 크지 않지만 tail latency에는 잔인하리만큼 민감하다. 이유는 단순하다── 사람이 알아챈다. 16 ms 늦게 도착한 프레임은 stutter가 되고, stutter는 리뷰에 영향을 준다. Steam Deck은 스케줄러 작업을 바로 그 제약 ── 예측 가능하고 latency가 보장된, 인간 시간 척도의 응답성 ── 쪽으로 밀어붙였다.

데이터센터는 최근까지 그런 종류의 제약에 대응할 필요가 없었다. 워크로드는 캐시와 큐의 뒤에서 조용히 돌아갔고, "인간 시간으로 응답적"이라는 건 프런트엔드의 속성이지 스케줄러의 속성이 아니었다. 그러나 이 부분이 변하고 있다. LLM 추론, 에이전트 루프, 사람이 토큰을 기다리는 모든 것── 이런 인터랙티브한 AI 워크로드가 fleet을 지배하기 시작하면, 인간 시간 척도의 tail latency가 데이터센터 스케줄러 자신의 책임으로 내려온다. Steam Deck 스케줄러가 Meta에서 돌아가는 이유는, 그것을 정의했던 제약 ── "사람이 알아챈다" ── 이 이제 Meta도 짊어지는 제약이 되었다는 것뿐이다.

## 메타포가 사는 층

기판 위에는 알고리즘이 올라간다. 그리고 여기서부터 Sörensen의 비판이 효력을 발휘하기 시작한다. Sörensen은 조합 최적화에 대해 쓰면서, 자연 현상의 이름을 단 메서드 ── 벌집 군집, 물 흐름, 화성 탐색, 면역계 ── 가 범람하고 있다고 지적했다. 주의 깊게 구현 단계까지 따라가면 그중 대부분이 평범한 수학으로 녹아 버린다는 것이다. 제목의 생물학은 마케팅 층이고, 실제 연산은 가중합과 행렬 대수였다.

커널 스케줄링에서도 같은 패턴이 반복되고 있다. 2025년 arXiv 논문 *KernelOracle*은 LSTM으로 "Completely Fair Scheduler가 다음에 어떤 태스크를 고를지"를 예측한다. 저자인 Sampanna Yashwant Kahu(Virginia Tech)는 한계에 대해 칭찬할 만큼 솔직하다── 이 작업을 production에 투입 가능한 스케줄러가 아니라 feasibility study로 명확히 자리매김한다.[^4] 인접 분야의 더 최근 연구 중에는 "tissue P systems"── 본래 세포막에서 영감을 받은 모델 ──을 스케줄러의 프레임으로 사용하는 것도 있다. 알고리즘을 차분히 따라가면 정규 구조 위의 행렬 대수가 되고, 이 자체는 문제가 없지만, 세포막 부분은 라벨에 불과하다.

이걸 비판해야 하느냐는 정당한 질문이다. 어떤 메타포는 유용한 형식 구조를 시사해서 값어치를 한다. 어떤 메타포는 그저 논문에 잘 팔리는 후크를 제공할 뿐이다. 문제는 연구자가 생물학에서 영감을 얻는다는 것이 아니다── 유용한 메서드 다수가 메타포에서 시작했다. 문제는 메타포가 "이 알고리즘이 *무엇인가*"에 대한 주장으로 그대로 남아 있을 때다. 어떤 스케줄러가 "neuromorphic"이라고 묘사되어 있는데, 구현은 실시간 시스템 업계 사람이 뉴런을 떠올리지 않고도 작성했을 event-driven arbiter라면, 그 생물학은 장식이다.

## 배치를 설명하는 경험칙

생물학 향이 나는 ML 스케줄러가 커널의 같은 자리에 자꾸 착지하는 데에는 구조적인 이유가 있다. *KernelOracle*이 사후 예측을 오프라인으로 수행하는 것은, 온라인 추론으로는 커널이 요구하는 결정 빈도를 따라잡을 수 없기 때문이다. Jim Huang이 2025년 6월 OSS-NA에서 발표하고 LWN이 7월에 정리한 머신러닝 기반 로드 밸런서가 잘 작동하는 이유는, 로드 밸런싱이 밀리초~초 단위의 거친 cadence에서 돌아가기 때문이다── 그 입자도라면 신경망 추론 레이턴시를 상각할 수 있다.[^5]

경험칙은 일반화된다. ML 풍, bio-inspired 풍의 휴리스틱은 결정을 느린 시간 척도에서 내릴 수 있는 영역 ── 로드 밸런싱, 주파수 거버너, 에너지 모델 튜닝 ── 에 집중적으로 정착한다. CPU 자체의 스위칭 속도로 결정을 내려야 하는 영역에서는 구조적으로 밀려난다. 이건 "하드웨어가 발전하면 해소될" 일시적 상태가 아니다. 스케줄링이 살고 있는 시간 계층의 성질 그 자체다.

## 내가 정말로 주시하는 것

커널 스케줄링에서 일어나고 있는 흥미로운 이야기는 그것이 "생물학적이 되고 있다"는 것이 아니다. Linux가 수십 년 만에 처음으로 재빌드 없이 실험을 허용하는 **기판**을 받아들였다는 사실 쪽이다. 그 기판은 우연히 생물이 정책과 실패를 다루는 추상 형태와 같은 모양을 하고 있다 ── 분리 가능한 메커니즘, 가역적인 실패 모드, 런타임에서의 가변성 ── 그리고 그 형태가 실제로 일을 하고 있다.

특정 스케줄러보다 흥미로운 질문은, 이 기판 위에 앞으로 무엇이 올라타느냐다. 다음으로 중요해질 흐름이라고 내가 보는 것은, Rust로 작성된 sched_ext와, 이미 디바이스 드라이버 영역으로 진출한 Rust-for-Linux가 만나는 지점이다. 둘은 다른 방향에서 오고 있고, 합류하는 층은 Linux가 2024년까지 갖고 있지 않던 바로 그 층이다. LSTM을 제목에 단 최신 논문이 아니라, 그 합류 지점이야말로 다음에 무엇이 일어날지 봐야 할 자리라고 생각한다.

---

[^1]: Sörensen, K. ["Metaheuristics—the metaphor exposed"](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001). *International Transactions in Operational Research* 22(1), 3–18, 2015. Accessed 2026-05-07.
[^2]: Phoronix. ["Sched_ext Merged For Linux 6.12 — Scheduling Policies As BPF Programs"](https://www.phoronix.com/news/Linux-6.12-Lands-sched-ext). Accessed 2026-05-07.
[^3]: Dai, D. & Newton, R. ["LAVD: Meta's New Default Scheduler"](https://lpc.events/event/19/contributions/2099/attachments/1875/4020/lpc-2025-lavd-meta.pdf). Linux Plumbers Conference 2025, Tokyo. Accessed 2026-05-07.
[^4]: Kahu, S. Y. ["KernelOracle: Predicting the Linux Scheduler's Next Move with Deep Learning"](https://arxiv.org/abs/2505.15213). arXiv:2505.15213, 21 May 2025. Accessed 2026-05-07.
[^5]: LWN. ["Improved load balancing with machine learning"](https://lwn.net/Articles/1027096/). 1 July 2025. Accessed 2026-05-07.
