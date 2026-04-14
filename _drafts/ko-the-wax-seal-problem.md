---
layout: post
lang: ko
title: "밀랍 봉인 문제: 왜 진실의 라벨은 항상 지는가"
date: 2026-04-14
categories: [technology, policy]
tags: [c2pa, content-provenance, mRNA, information-integrity, truth-labeling]
permalink: /ko/:year/:month/:day/:title/
---

밀랍 봉인을 찍으려면 도구와 열, 정밀함, 그리고 아무도 갖고 있지 않은 인장이 필요하다. 깨뜨리는 데는 손톱 하나면 충분하다. 인증된 증명을 만드는 비용과 파괴하는 비용 사이의 이 비대칭이, 디지털 시대에 '진실에 라벨을 붙이는' 행위가 직면한 구조적 문제의 핵심이다.

2026년 초의 두 가지 사건이 이 문제를 불편할 정도로 구체적으로 보여준다.

## 모든 것을 이겼지만 게임에서는 진 표준

C2PA(Coalition for Content Provenance and Authenticity)는 제도적 지표만 놓고 보면 압도적인 성공 사례다. 2026년 1월 기준으로 연합의 회원 수는 6,000을 넘어섰다.[^1] 콘텐츠 인증 시장 규모는 약 20억 6천만 달러로 추산되며, 연간 약 26%씩 성장하고 있다.[^2] 하드웨어 통합도 소비자 기기에 도달했다. 2025년 말 출시된 Google의 Pixel 10은 센서 수준에서 모든 사진에 C2PA 인증 정보를 부여하며, C2PA 적합성 프로그램의 최고 보안 등급을 획득했다.[^3]

그러나 정작 중요한 곳에서는 아무 의미가 없다.

Instagram, X, WhatsApp — 콘텐츠 진위가 가장 중요한 플랫폼들이 업로드 시 C2PA 매니페스트를 포함한 모든 메타데이터를 제거한다.[^4] Pixel 10 카메라가 정성 들여 삽입한 출처 데이터는 사진이 실제로 소비되는 플랫폼에 도달하는 순간 조용히 사라진다.

더 심각한 것은 aimetadatacleaner.com 같은 사이트가 C2PA 메타데이터 제거를 공개적으로 서비스로 판매하며, Instagram의 'AI 생성' 라벨을 우회하는 튜토리얼까지 제공하고 있다는 점이다.[^5] 진실을 보호하기 위해 설계된 표준 자체가 우회 대상이 되어버렸다.

C2PA는 이 문제를 예견했다. '내구성 있는 콘텐츠 인증 정보(durable content credentials)' 사양에서는 비가시적 디지털 워터마크와 콘텐츠 핑거프린팅을 결합하여, 메타데이터가 제거된 후에도 외부 저장소에서 인증 정보를 재발견할 수 있는 메커니즘을 규정하고 있다.[^6] 그러나 이 워터마크는 손실 압축, 포맷 변환, 리사이징을 반복할수록 열화된다 — 정확히 소셜 미디어 플랫폼이 모든 이미지에 가하는 처리 그 자체다. 이론적 대안의 실질적 수명은 재인코딩 횟수로 측정된다.

구조적 문제는 잔인할 정도로 명확하다. C2PA 메타데이터를 삽입하려면 하드웨어 설계, PKI 인프라, 업계 간 협력, 그리고 지속적인 검증 서비스가 필요하다. 제거하는 것은 대부분의 이미지 처리 파이프라인에서 자동으로 일어나며, 의도적으로 벗기고 싶은 사람이라면 몇 초 만에, 무료로 할 수 있다.

## 과학이 스스로의 어휘를 버릴 때

2023년, Moderna는 자사에서 가장 유망한 암 치료제에서 '백신'이라는 단어를 조용히 제거했다. 수술 후 흑색종 환자에서 재발 위험을 49% 감소시킨 실적을 가진 mRNA 기술이었다.[^7] 과학적으로 mRNA 백신이던 것이 '개인 맞춤형 신생항원 치료제(individualized neoantigen therapy: INT)'가 되었다.

표면적인 이유의 일부는 기술적이었다. 환자는 이미 암에 걸린 상태이므로 전통적 의미의 예방이 아닌 치료라고 부르는 것이 정확하다는 논리였다. 그러나 MIT Technology Review가 보도했듯이, 다른 동기는 분명했다 — 미국 고위 관리들에 의해 증폭된 백신 기피 풍조로부터 거리를 두기 위해서였다.[^8]

그리고 상황은 더 악화되었다. 2025년 8월, HHS(보건복지부) 장관 로버트 F. 케네디 주니어가 약 5억 달러 규모의 연방 mRNA 연구 계약을 취소했다.[^9] 취소된 프로젝트에는 암과 HIV에 대한 mRNA 기술 연구가 포함되어 있었다 — 케네디가 겨냥하던 호흡기 백신과는 아무 관련도 없는 응용 분야였다.

Moderna의 흑색종 치료제의 작용 기전 — mRNA를 사용하여 세포가 항원을 생산하도록 지시하고 면역 체계를 훈련시키는 것 — 은 정확히 백신이 하는 일이다. 이름 변경은 과학적 수정이 아니었다. 정확한 용어가 부담이 되는 정치적 환경에 대한 전략적 굴복이었다.

과학계 내부의 긴장은 절실하다. 정확한 이름으로 부르는 것이 치료에 대한 이해에 중요하다고 주장하는 의사들이 있는 반면, 새로운 이름 아래서라도 연구를 계속할 수 있다면 이름 변경은 지불할 가치가 있는 대가라는 현실주의자들도 있다.[^8] 두 입장 모두 합리적이다. 그래서 상황이 부식적인 것이다.

## 같은 문제, 두 번

이 두 사례는 겉으로 보기에 전혀 다르다. 하나는 소프트웨어 표준과 이미지 처리 파이프라인 이야기고, 다른 하나는 의약품 규제와 정치적 임명 이야기다. 그러나 구조 아래에는 동일한 실패 모드가 있다.

두 경우 모두 올바른 라벨을 붙이는 비용은 높다. C2PA에는 하드웨어 변경, PKI 인프라, 업계 협력이 필요하다. 과학 명명법에는 수십 년의 연구, 동료 심사, 전문가 합의가 필요하다. 그리고 두 경우 모두 올바른 라벨을 제거하거나 포기하는 비용은 거의 제로다. 메타데이터 제거는 이미지 처리의 기본 동작이고, 정치적 이름 변경은 예산 위협 하나면 충분하다.

규모는 이 비대칭을 해결하지 못한다. C2PA의 6,000개 회원 기관과 20억 달러 시장은 3대 콘텐츠 플랫폼이 이를 무시하는 것을 막지 못했다. 수십 년간의 백신 과학은 한 명의 정치적 임명자가 '백신'이라는 단어를 사용 불가능하게 만드는 것을 막지 못했다.

이것은 기술의 문제가 아니다. 인센티브의 문제다. 소셜 미디어 플랫폼이 메타데이터를 제거하는 것은 저장과 검증에 비용이 들고, 혜택을 받는 사용자가 그 비용을 부담하지 않기 때문이다. 정치인이 과학 용어를 공격하는 것은 정확성으로는 표를 얻지 못하지만 '기득권에 맞서 싸우는' 자세로는 많은 표를 얻기 때문이다.

## 무엇이 필요한가

솔직히 말하면, 기술적 수단만으로 비대칭을 역전시키는 것은 아마 불가능하다.

C2PA의 '내구성 있는 콘텐츠 인증 정보'는 진정으로 영리한 엔지니어링 솔루션이지만 물리적 한계에 직면한다 — 손실 압축을 한 번 반복할 때마다 워터마크는 열화된다. EU의 AI법과 디지털 서비스법은 다른 접근을 시도하며, 출처 데이터 보존을 태만히 한 경우 벌금을 부과한다. 메타데이터를 제거하는 비용이 유지하는 비용보다 높아지면 인센티브 구조가 뒤집힌다.

그러나 규제 또한 밀랍 봉인이다. 만드는 데 수년이 걸리고 단 한 번의 선거 주기로 무력화될 수 있다. mRNA의 이름 변경은 세계에서 가장 견고한 규제 인프라를 가진 나라에서 일어났다. 규제 인프라가 있었음에도 불구하고가 아니라.

이 비유로 계속 돌아오게 된다. 밀랍 봉인이 기능하는 것은 물리적으로 부술 수 없어서가 아니다 — 아이도 깰 수 있다. 깨뜨리는 행위에 사회적 결과가 따르기 때문에 기능하는 것이다. 밀랍은 그저 매체일 뿐이다. 진짜 보호는 '봉인이 깨졌다면 무언가 잘못된 것이다'라는, 그리고 '깨뜨린 사람에게 책임이 있다'는 공유된 이해에서 온다.

C2PA와 mRNA 양쪽 모두에 빠져 있는 것이 바로 이것이라고 생각한다. 더 나은 봉인이 아니라, 봉인을 깨뜨리는 것에 대한 결과의 사회적 인프라. 기술 표준과 과학 용어 모두 정확성에 대한 암묵적 헌신을 전제로 한다. 2026년 현재, 그 전제는 더 이상 자명하지 않다.

밀랍 봉인 문제는 처음부터 밀랍의 문제가 아니었다.

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
