---
layout: post
lang: ko
title: "섞기, 사슬로 잇기, 계속 지키기: 커널이 '신뢰'라 부르는 세 개의 기계"
date: 2026-07-02
categories: [systems-programming, security, technology]
tags: [arm64, confidential-computing, arm-cca, kaslr, attestation, kernel-security]
permalink: /ko/:year/:month/:day/:title/
---

다른 질문을 쫓아 ARM64 부팅 경로 속으로 내려갔다가, 일하는 내내 검사 한 번 없이 써 온 한 단어를 결국 분해해야 하는 채로 돌아왔다. 그 단어는 *신뢰(trust)*다. 우리는 시스템이 서명 키를 "신뢰한다", 부팅 체인을 "신뢰한다", 방금 뽑은 난수를 "신뢰한다"고 말한다. 나는 늘 그 단어에서 하나의 의미만 들었다 — 무언가에 기대는 단일한 행위. 그러나 현대의 보안 커널이 보증을 실제로 어떻게 "제조"하는지 읽으면서, 거기엔 세 가지가 있었다. 이름만 공유하고 나머지는 거의 아무것도 공유하지 않는 세 개의 기계. 그리고 이 셋을 가르는 축은 결국 **과거와의 관계**였다 — 하나는 기억하기를 거부하고, 하나는 기억한 것만으로 살아가며, 하나는 판돈을 현재에 넓게 분산시켜 기억이 나설 자리를 없앤다.

만난 순서대로 늘어놓아 본다.

## 섞기: 논리합으로서의 신뢰

첫 번째는 커널이 자기 자신의 배치를 무작위화하는 곳에서 나타났다. KASLR(커널 주소 공간 배치 무작위화)는 공격자가 어느 함수가 어디 있는지 전제하지 못하도록 커널을 예측 불가능한 오프셋에 적재한다. 그러려면 엔트로피가 필요한데, 여기서 나는 단순히 틀린 믿음을 갖고 있었다 — ARM64는 x86과 달리 하드웨어 난수 명령이 없어서 부트로더가 건네는 시드를 신뢰할 수밖에 없다고. 이 오류를 굳이 적는 이유는, **틀렸던 바로 그 자리에 흥미로운 구조가 숨어 있었기** 때문이다.

ARMv8.5-A는 그런 명령을 추가했다 — `RNDR`. 게다가 비특권 사용자 공간에서도 읽을 수 있다.[^2] 그런데 들여다볼수록 커널은 어느 한 출처에 의존하는 것처럼 굴지 않았다. 가용한 것이면 무엇이든 엔트로피 원으로 삼는다: v8.5 하드웨어 생성기, 펌웨어 호출(SMCCC TRNG 인터페이스), UEFI의 `EFI_RNG_PROTOCOL`, 디바이스 트리가 실어 나르는 시드 — 그리고 그중 **하나라도 정말로 예측 불가능하면 결과도 예측 불가능**해지도록 설계되어 있다.[^3] 이것은 "가장 약한 고리"에서 끊어지는 사슬이 아니다. 오히려 논리합에 가깝다. 공격자는 출처 하나를 뚫어서는 이기지 못한다. **전부가 동시에 나빴다**는 것을 증명해야 한다.

여기서 짚어 둘 점은, 이런 종류의 신뢰에는 **기억이 없다**는 것이다. 과거에 관해 아무것도 기록하지 않는다. 정직한 기여자가 하나 존재하는 순간 현재에서 성공하고, 나머지의 실패에는 무관심하다. 중복성 — 다만 평균으로 오차를 상쇄하는 다수결형이 아니다. **살아남은 하나면 충분한** 유형의 중복성이다.

## 사슬로 잇기: 쌓여 가는 과거로서의 신뢰

두 번째 형태는 거의 모든 면에서 반대였다. Arm의 Confidential Compute Architecture(CCA)는 그 아래의 하이퍼바이저조차 읽을 수 없는 워크로드 — "Realm" — 를 실행할 수 있게 한다. 어떤 Realm이 정말 정당한 보호 아래 돌아가고 있음을 원격 상대에게 증명하기 위해, CCA는 어테스테이션 토큰을 발행한다. 이 토큰은 **중첩** 구조다: 하드웨어가 보유한 플랫폼 키로 서명된 플랫폼 토큰이, 별도의 realm 키로 서명된 realm 토큰을 감싸고, 둘은 realm의 공개 키 해시를 플랫폼 증거에 심어 넣음으로써 묶인다.[^4]

이 중첩은 사슬이며, 사슬처럼 행동한다. realm의 주장은 그 아래 플랫폼의 주장만큼만 견고하다. 플랫폼 고리를 끊으면 그 위 realm 서명은 무가치해진다. 섞기가 "좋은 출처 하나면 구원받도록" 위험을 넓힌다면, 사슬은 "나쁜 고리 하나면 위의 전부가 망가지도록" 위험을 집중시킨다. 그리고 섞기와 달리 이 신뢰는 **기억 그 자체**다. 토큰은 누적된 기록 — 어떤 펌웨어가 무엇을 적재했는지를 한 단계씩 해시로 앞으로 쌓아 올린, 측정된 이력이다. **내력(provenance)으로서의 신뢰**이며, 통째로 믿거나 아예 안 믿거나 하는, 과거에 관한 이야기다.

## 계속 지키기: 결코 기억하지 않는 불변조건으로서의 신뢰

세 번째 형태는 하마터면 놓칠 뻔했다. 자꾸 앞의 둘로 분류하려 했기 때문이다. Realm 아래에서 하드웨어는 Granule Protection Check로 "세계(world)"들 사이의 격리를 강제한다: 모든 물리 메모리 접근은 **일반적인 주소 변환의 하류에서**, 그 메모리 granule을 어느 world가 소유하는지 기록한 표와 대조된다.[^5] 모니터 펌웨어는 각 granule의 상태에 관한 자기만의 장부를 두고, 단 하나의 규칙 — 하나의 granule은 동시에 정확히 하나의 world에 속한다 — 을 깨는 전이를 모두 거부한다. Realm에서 일반 세계로 메모리가 반환될 때는 이송 도중에 내용이 지워지고, 인계 중에는 누구도 그 내용을 관측하지 못한다.[^6]

이것이 **무엇이 아닌지**에 주목하라. 섞은 도박도 아니고, 측정된 이력도 아니다. 여기서는 아무것도 서명되지 않고, 나중의 검증을 위해 아무것도 기록되지 않는다. 보증은 **매 순간 참으로 유지되는 성질** — 과거에 아무 관심도 없고 과거에 관한 이야기도 보관하지 않는 상태 기계가 유지하는 불변조건이다. 안전은 "올바르게 기억하는 것"이 아니라 "단 한 번도 금지 상태에 들어가도록 허용되지 않는 것"에서 온다. 섞기가 "우리 중 누군가 하나는 정직하다"이고 사슬이 "일어난 일이 전부 여기 있다"라면, 이 세 번째는 "**장부는 지금 이 순간 균형을 이루고 있으며, 언제나 균형을 이루어야 한다**"이다.

## 왜 하나의 단어인가, 그리고 그것을 유지하는 대가

그러니까 섞기, 사슬, 지키기. 병렬 중복성, 직렬 내력, 그리고 연속적으로 유지되는 불변조건. 세 개의 기계를 우리가 태연히 하나의 이름으로 부르는 것은, 밖에서 보면 모두 같은 제품 — **이것에 기댈 수 있다** — 을 내놓기 때문이다. 그러나 안에서는 복권과 족보와 물리 법칙만큼이나 다르다.

셋이 일단 갈라지자, 다른 곳에서도 보이는 것을 멈출 수 없었다. 그리고 커널의 세부보다 바로 거기가 진짜 수확이라고 생각한다. 복식부기는 "지키기" 유형이다: 과거에 관해 아무것도 신뢰하지 않고, 그저 장부가 불균형에 빠지는 것을 금할 뿐이다. 공증된 관리 연쇄나 공급망 내력 기록은 "사슬" 유형 — 누적적이며, 증거의 가장 약한 한 단계만큼만 강하다. 배심원단, 잡음 섞인 센서들의 앙상블, 어떤 착상이 멍청하지 않은지 친구 셋에게 묻는 행위는 "섞기" 유형이고, 사람들이 잊는 성질을 지닌다: **오류가 전부 같은 오류가 아닌 한에서만** 지켜 준다. 같은 생각을 하는 사람들만 모인 방은 가짜 중복성만 낳는다고 전에 논한 바 있는데, 엔트로피의 경우는 그 정직한 판본이다. 출처를 결합하는 데에는 하나가 좋으면 충분하고, 전부가 독립일 필요는 없으니까.

내가 가져가는 실무적 교훈은 사실이라기보다 습관이다: 하나의 단어가 시스템의 안전 이야기를 통째로 짊어지고 있을 때 — "신뢰"뿐 아니라 "기억", "동일성", "소유"도 — 그 단어는 아마 하나 이상의 기계를 숨기고 있고, 그 기계들은 아마 **시간을 다루는 방식**에서 다르다. 커널은 신뢰에 관한 새 사실을 가르쳤다기보다, 그 단어를 게으르게 계속 쓰도록 허락하지 않았다.

아직 답하지 못한 것은, 이 셋이 정말 기약(旣約)인지, 아니면 그저 하드웨어가 싸게 만들 수 있는 것이 이 셋이었을 뿐인지다. 현행의 어떤 기계도 너무 비싸서 구현하지 않는 네 번째 "확신"의 형태 — 섞지도, 사슬로 잇지도, 불변조건으로 지키지도 않는 신뢰 — 가 있을까? 모르겠다. 하지만 "날 믿어"가 단일한 요청이라고 믿는 것은 그만두었다. 그것은 늘 적어도 셋 중 하나이며, **어느 것인지 아는 것에는 가치가 있다**.

---

*ARM64 Linux 부팅 경로와 그 기밀 컴퓨팅 확장을 몇 달에 걸쳐 기어다닌, 내 독서 노트를 토대로 한다. 다카하시 히로카즈의 커널 내부 시리즈를 따라간 기록이다.[^1] 아래 출처는 load-bearing한 기술적 주장을 담고, 세 갈래 틀과 비유는 내 것이다.*

[^1]: Takahashi, Hirokazu. "[新Linuxカーネル解読室 — Linuxの起動 〜ARM64編〜](https://valinux.hatenablog.com/)" (VA Linux Systems Japan, kernel-internals blog series). Accessed 2026-07-02.
[^2]: Arm. "[RNDR, Random Number (AArch64 System Register)](https://developer.arm.com/documentation/ddi0595/2021-06/AArch64-Registers/RNDR--Random-Number)." The Armv8.5-A optional RNG extension; the register is available at EL0. Accessed 2026-07-02.
[^3]: Biesheuvel, Ard. "[KASLR in the arm64 Linux kernel](https://www.workofard.com/2016/05/kaslr-in-the-arm64-kernel/)" (Work of Ard, 2016); and "[arm64: implement support for KASLR](https://lwn.net/Articles/673598/)" (LWN.net). On drawing KASLR entropy from v8.5-RNG, the SMCCC RNG interface, `EFI_RNG_PROTOCOL`, and the device-tree `kaslr-seed`. Accessed 2026-07-02.
[^4]: "[Arm's Confidential Compute Architecture Reference Attestation Token](https://datatracker.ietf.org/doc/draft-ffm-rats-cca-token/)" (IETF draft-ffm-rats-cca-token); and Arm, "[Get Started with CCA Attestation](https://learn.arm.com/learning-paths/servers-and-cloud-computing/cca-veraison/cca-attestation/)." On the nested platform/realm token, bound by a hash of the realm attestation key. Accessed 2026-07-02.
[^5]: "[Realm Management Extension (RME)](https://trustedfirmware-a.readthedocs.io/en/latest/components/realm-management-extension.html)" (Trusted Firmware-A documentation); and Arm, "[Granule Protection Checks](https://developer.arm.com/documentation/den0126/0102/Granule-Protection-Checks)." Isolation between physical address spaces is enforced by the Granule Protection Check in the MMU, downstream of address translation, against a Granule Protection Table held in Root memory. Accessed 2026-07-02.
[^6]: "[Realm Management Monitor Specification](https://rmm.docs.trustedfirmware.org/)" (TF-RMM); and "[Enabling Realms with the Arm Confidential Compute Architecture](https://www.usenix.org/publications/loginonline/enabling-realms-arm-confidential-compute-architecture)" (USENIX ;login:). On the Granule Status Table and the requirement that a granule be wiped before it is undelegated, and be unobservable while in the DELEGATED state. Accessed 2026-07-02.
