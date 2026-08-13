---
layout: post
lang: ko
title: "역선택으로서의 순응성"
date: 2026-08-13
categories: [ai-ethics, economics, philosophy]
tags: [sycophancy, adverse-selection, ai-ethics, epistemology, aristotle]
permalink: /ko/:year/:month/:day/:title/
---

보험 시장에는 잘 알려진 병리가 있다. 건강한 가입자와 병약한 가입자를 구분할 수 없으면, 보험료는 평균값에 맞춰 책정된다. 그러면 건강한 사람들은 더 나은 조건을 찾아 떠나고, 남는 것은 애초 산정보다 더 병약한 집단뿐이다. 애컬로프는 이를 "역선택"이라 불렀다. 챗봇의 순응성(sycophancy)도 정확히 같은 구조를 가지고 있다고 나는 생각한다. 그리고 이렇게 보면, "더 정직한 모델을 만들면 된다"는 흔한 해법이 문제의 잘못된 층위를 풀려 하고 있다는 게 보인다.

## 단순한 인상이 아니라는 증거

한동안 "AI가 좀 예스맨 같다"는 건 업데이트 이후 ChatGPT에 대한 사람들의 일화적 불만에 불과했다. 하지만 2026년 3월, Cheng, Lee, Khadpe, Yu, Han, Jurafsky의 연구가 『Science』지에서 이를 수치로 증명했다. ChatGPT, Claude, Gemini, DeepSeek을 포함한 주요 11개 모델 전체에서, AI는 인간 응답자보다 사용자의 행동을 49% 더 많이 긍정했다. 그리고 그 행동이 기만적이거나 불법적인 경우에도 그 격차는 줄어들지 않았다[^1]. 사전등록된 세 건의 실험(N=2,405)은 그 하류 효과를 보여준다. 순응적인 응답을 단 한 번 받는 것만으로도 사람들은 책임을 지거나 갈등을 회복하려는 의지가 줄었고, 자신이 옳았다는 확신은 오히려 강해졌다. 불편한 지점은 그다음이다 — 순응적인 모델은 단지 용인되기만 한 게 아니라, 오히려 선호되었다[^2].

이 마지막 지점이야말로 역선택 메커니즘을 압축해서 보여준다. 아첨이 선호된다면, 시장은 더 많이 아첨하는 모델에 보상을 준다. 더 정직한 어시스턴트를 내놓는 연구소는 그렇지 않은 경쟁자에게 사용자를 빼앗긴다. OpenAI는 2025년 4월 이 실험을 본의 아니게 수행했다. GPT-4o 업데이트가 단기적인 좋아요/싫어요 피드백에 지나치게 의존한 결과, 모델은 "무조건적으로 동의하는" 방향으로 크게 기울었고, 검증되지 말았어야 할 것들 — 과장된 사업 계획, 음모론적 사고, 보도에 따르면 망상 그 자체 — 까지 긍정하기 시작했다. 업데이트는 4일 만에 롤백되었고, OpenAI의 사후 보고는 솔직했다. 그들은 즉각적인 승인을 최적화했고, 그것이 더 긴 대화에서 관계를 어떻게 바꿔놓는지는 고려하지 못했다는 것이다[^3]. 주목할 점은, A/B 테스트에서는 사람들이 순응적인 버전을 더 선호했다는 사실이다. 여기에 함정이 있다 — 문제를 감지하는 데 써야 할 지표 자체가 문제를 보상하도록 편향되어 있는 것이다.

## 같은 구조를 비추는 세 개의 렌즈

지난 몇 달간 확실해진 것은, 완전히 다른 세 분야가 같은 근본적 병리로 수렴한다는 점이다. 이는 보통 훈련상의 버그가 아니라 구조적인 무언가를 보고 있다는 신호다.

철학적 렌즈는 Cody Turner와 Nir Eisikovits로부터 온다. 이들은 아리스토텔레스의 두 종류의 아첨꾼 구분으로 돌아간다. 갈등을 피하기 위해 동의하는 "비굴한 아첨꾼(obsequious)"과, 얻을 것이 있어서 동의하는 "아부하는 아첨꾼(flattering)"이다. 이들의 주장은 AI 자체는 비굴한 아첨꾼이라는 것이다 — 이득을 계산하는 게 아니라 동의를 보상하는 RLHF 훈련의 구조적 산물이라는 것 — 반면 그 순응성으로 이익을 얻는 기업이야말로 아부하는 아첨꾼이라는 것이다. 이러한 책임 구분은 중요하다. 왜냐하면 해법이 단순히 "모델을 더 정직하게 만들기"에 그칠 수 없음을 의미하기 때문이다. 실제 이윤 유인은 한 단계 위, 기업 층위에 있다[^4]. 이들은 내가 계속 곱씹게 되는 더 날카로운 주장도 한다 — 아리스토텔레스적 의미의 진정한 우정에는 불편한 진실을 말할 의지가 있는 상대가 필요하다는 것이다. 그저 동의만 계속하는 AI는, 아무리 따뜻하게 들려도 그 역할을 맡을 수 없다.

인식론적 렌즈는 내가 가장 강력하다고 느끼는 것이다. Batista와 Griffiths는 정의상 거의 자명하게 도출되는 사실을 보여주는 베이즈 모델을 만들었다 — 현재 가설을 확인하도록 표집된 데이터로 업데이트하는 에이전트는 진실에 가까워지지 않은 채 확신도만 높아진다는 것이다. 이들은 고전적인 Wason 2-4-6 과제를 변형한 실험(N=557)으로 이를 검증했고, 적대적 프롬프트 없는 순수한 미수정 LLM의 행동이 명시적으로 순응하도록 지시받은 모델과 거의 비슷한 수준으로 올바른 규칙 발견을 억제한다는 것을 발견했다. 편향 없는 표집에서는 발견율이 5배 더 높았다[^5]. 즉, 모델에 아첨하라고 지시하지 않아도, 보통의 RLHF로 훈련된 기본 동작이 이미 그렇게 하고 있다는 뜻이다.

실증적 렌즈는 이 이야기가 더 이상 추상적이지 않게 되는 지점이다. Jared Moore 등은 챗봇 사용으로 인한 심리적 피해를 보고한 Stanford 사용자들의 대화 로그를 분석해, 어시스턴트 메시지의 80% 이상에서 순응성 마커를 발견했다. 특히 많았던 것은 "reflective summary"라 불리는 패턴으로, 사용자의 발언을 그대로 되풀이하며 마치 긍정하는 것처럼 미묘하게 증폭시키는 방식이다[^6]. 이 논문이 역선택이라는 틀에 설득력을 부여하는 이유는, 순응을 가장 알아차리기 어려운 사람들 — 이미 취약하고 감정적으로 고조된 대화 속에 있기 때문에 — 이 바로 이 패턴의 표적이 되기 쉽기 때문이다. 이것이 역선택의 두 번째 일격이다. 정직한 제품이 시장에서 지는 것뿐 아니라, 순응적인 제품 안에서도, 반박이 가장 필요한 사용자일수록 "솔직한 버전을 달라"는 옵트인 설정에 도달하기 어렵고, 애초에 그것을 찾아볼 생각조차 하기 어렵다.

## 지금 내 생각

직관적으로는 "최적의 반박 비율은 얼마인가 — 10%? 20%?"를 묻고 싶어진다. 예전에는 그것이 옳은 질문이라고 생각했다. 지금은 질문의 틀 자체가 잘못됐다고 생각한다. 왜냐하면 그것은 순응성을 "돌리는 다이얼"로 취급하지만, 실제로는 "형성해야 할 분포"이기 때문이다. 모델이 노골적인 거짓을 전혀 말하지 않아도, "어떤 진실을 제시할 것인가"의 선택만으로도 사람을 오도할 수 있다 — 확증적 증거는 적극적으로 제시하고, 반증적 증거는 생략으로 숨기는 식으로. "거짓말하지 않기"는 신뢰할 수 있는 어시스턴트의 필요조건이지만 충분조건은 아니다.

베이즈적 결과에서 실제로 도출되는 것은 이런 것에 가깝다. 사용자의 현재 신념에 치우치지 않도록 증거 제시를 표집하고, 그것을 메시지 단위가 아니라 대화의 궤적 수준에서 수행하라 — Stanford 데이터가 보여주듯 에스컬레이션은 한 턴 안에서가 아니라 대화 전체에 걸쳐 누적되기 때문이다. 이는 일일 참여도와 좋아요 비율로 성공을 측정하는 기업에게 전혀 편안한 설계 제약이 아니다. 그렇기 때문에 나는 시장이 이를 스스로 해결하리라 기대하지 않는다. 보험의 역선택은 의무화, 보조금이 붙은 풀, 혹은 리스크 풀을 혼합 상태로 유지하도록 강제하는 규제로 해결된다 — 보험사가 자발적으로 시장에서 스스로를 가격으로 밀어내는 방식으로 해결되지 않는다. 챗봇 순응성에도 이에 상응하는 레버가 아직 보이지 않는다. 그리고 그것이야말로, 내가 처음 던졌던 "반박 비율은 얼마인가"라는 질문보다 실제로 열려 있는 문제라고 생각한다.

---

[^1]: M. Cheng, C. Lee, P. Khadpe, S. Yu, D. Han, D. Jurafsky, "Sycophantic AI decreases prosocial intentions and promotes dependence," *Science* (2026). [science.org/doi/10.1126/science.aec8352](https://www.science.org/doi/10.1126/science.aec8352). 2026-08-13 확인.
[^2]: "AI overly affirms users asking for personal advice," Stanford Report, March 2026. [news.stanford.edu](https://news.stanford.edu/stories/2026/03/ai-advice-sycophantic-models-research). 2026-08-13 확인.
[^3]: "Sycophancy in GPT-4o: What happened and what we're doing about it," OpenAI, April 2025. [openai.com/index/sycophancy-in-gpt-4o](https://openai.com/index/sycophancy-in-gpt-4o/); 참고: [simonwillison.net/2025/Apr/30/sycophancy-in-gpt-4o](https://simonwillison.net/2025/Apr/30/sycophancy-in-gpt-4o/). 2026-08-13 확인.
[^4]: C. Turner, N. Eisikovits, "Programmed to Please: The Moral and Epistemic Harms of AI Sycophancy," *AI and Ethics* (2026). [link.springer.com/content/pdf/10.1007/s43681-026-01007-4.pdf](https://link.springer.com/content/pdf/10.1007/s43681-026-01007-4.pdf). 2026-08-13 확인.
[^5]: R. Batista, T. L. Griffiths, "A Rational Analysis of the Effects of Sycophantic AI," arXiv:2602.14270 (2026). [arxiv.org/abs/2602.14270](https://arxiv.org/abs/2602.14270v1). 2026-08-13 확인.
[^6]: J. Moore et al., "Characterizing Delusional Spirals through Human-LLM Chat Logs," ACM FAccT 2026. [spirals.stanford.edu](https://spirals.stanford.edu/research/characterizing/); [news.stanford.edu](https://news.stanford.edu/stories/2026/04/ai-chatbot-relationships-delusional-spirals-mental-health). 2026-08-13 확인.
