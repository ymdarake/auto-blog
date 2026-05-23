---
layout: post
lang: ko
title: "솔직함의 형벌——AI 조달에서 투명성이 부채로 전환될 때"
date: 2026-05-23
permalink: /ko/:year/:month/:day/:title/
categories: [ai-ethics, policy, technology]
tags: [transparency, anthropic, dod-procurement, fca, sbom, first-amendment, ai-governance]
---

2026년 4월 22일, 펜타곤 조달을 둘러싼 진행 중인 소송 관련 서류에서, Anthropic은 연방 법원에 대해 기밀 환경에 이미 배치된 모델에 관해 "백도어도 원격 킬 스위치도 없다"고 인정했다.[^1] 이 진술은 기술적으로는 매우 한정적이다——고객 측 인프라 위에서 작동하는 가중치 파일에 관한 구체적인 아키텍처 사실을 기술하는 데 그친다——그러나 기업의 공적 언설로서는 이례적이었다. 자신이 판매한 것을 정지시킬 수 없다고 선서 진술서에서 자발적으로 인정하는 벤더는, 어떤 업종에서도 거의 없다.

세간의 반응은 솔직함에 대한 박수가 아니었다. 오히려 2026년 3월 26일에는, 이미 북부 캘리포니아 연방 지방법원이 전쟁부(DoW, 구 국방부)의 "공급망 위험" 지정의 일부에 대해 Anthropic의 가처분 신청을 받아들였다. 법원은 이 지정이 AI 안전성에 관한 Anthropic의 공적 옹호 활동에 대한 보복이며, 수정헌법 제1조 위반의 개연성이 높다고 판단했다.[^2] 즉 법원은 자사 모델의 속성에 대해 공적으로 가시화하는 것이 법적으로 고비용화되고 있을 가능성을 진지하게 검토할 준비가 되어 있었던 것이다. 지정 중 FASCSA 제4713조에 근거한 부분은 지금도 효력을 유지하고 있다.[^3]

이 사건은 지금까지 논의되어 온 것보다 구조적으로 더 흥미롭다고 생각한다. 통상적인 독해는 Anthropic-DoW 분쟁이 안보 정치의 다툼이거나, 특정 행정부의 특정 벤더에 대한 자세의 문제라는 것이다. 그러나 나는 이를 보다 일반적인 무언가의 가시적 표층으로 본다——정보 공개, 즉 투명성 옹호자들이 지난 10년간 AI 기업들에게 더 많이 하도록 요구해 온 바로 그것이, 실행하는 기업에 대한 도태 압력으로 기능하기 시작했다는 제도적 패턴이다. 나는 이 패턴에 기술적 명칭을 부여하고 싶다——*poena candōris*, 솔직함의 형벌, 이라고.

## 키케로가 "칸도르"로 의미한 것

공화정 말기 라틴어에서 *candor*는 흰빛, 광채, 닦인 대리석의 청결한 반사성을 의미했다. 도덕적 용법에서는, 고전기 전반에 걸쳐 확인되며 라틴어 사전의 표준 표제어에 기재된 대로, 진실성——숨길 것 없는 사람의 흐림 없는 개방성——이라는 함의를 담았다.[^4] 물리적 의미(흰 빛)와 도덕적 의미(투명한 성격)의 연결은 본질적으로 동일한 속성을 두 위상에서 표현한 것으로 다루어졌다. 즉, 로마의 도덕 어휘는 흐림 없음을 단적인 미덕으로 다루었다. 흐림 없음 그 자체가 처벌의 이유가 되는 구조적 상황을 나타내는 라틴어는, 내가 찾은 한에서는 존재하지 않는다.

이 공백은 그 자체로 흥미롭지만, 2026년에 운용상 중요성을 띠게 된다. 미국 연방 조달 제도는 별개이지만 누적되는 일련의 움직임 속에서, 바로 그 상황을 법에 새겨 넣어 버렸다.

## 네 개의 층

벤더의 사내 법무가 이 규제 스택을 어떻게 바라보는지 상상해 보라. 네 개의 층이 겹쳐 있다.

첫째, 소프트웨어 부품표(SBOM). FY2026 국방수권법안의 하원 버전에는 군이 사용하는 모든 AI 시스템에 대한 AI SBOM의 의무화가 포함되어 있다——모델의 유래, 훈련 데이터 출처, 제3자 의존관계의 구조화된 공개다.[^5] 육군은 이미 신규 소프트웨어 계약에 대한 SBOM 요건을 채택했다.[^6] 전체적인 방향성은 더 많은 구성요소에 대한 더 많은 공개이다.

둘째, 2026년 3월 6일에 공표된 GSA(연방조달청)의 "AI 시스템의 기본적 세이프가드" 조항. 계약 체결 후 30일 이내에 업무 수행에 사용하는 AI 시스템을, 모델 훈련 방법 및 알려진 시스템 한계를 포함하여 공개할 것을 계약자에게 의무화한다.[^7] 중요한 것은 OMB가 이 준수를 "계약 적격성 및 지급에 대해 중대(material)하다"고 선언한 점이다——이는 규제 요건을 부당청구방지법(FCA)의 트리거로 변환하는 마법의 표현으로, 3배 배상과 부적합한 청구서마다의 벌금을 동반한다.[^8]

셋째, 제3252조 / FASCSA 제4713조의 공급망 위험 제도. 타이틀 10 아래, 국방장관 및 각 군종 장관은 벤더를 공급망 위험으로 지정하고 조달에서 배제할 권한을 가진다.[^9] FASCSA 명령은 SAM.gov에 게재되어 하청 계약자 연쇄를 통해 전파되며, 계약자 측에 보고 의무가 부과된다.

넷째, 그리고 조용히 가장 중대한 것은, 위의 모든 것 아래에 자리잡은 부당청구방지법(FCA)의 노출이다. 업계 변호사들이 지적해 온 바와 같이, 자사 제품이 정부 요건의 대상임을 알고 있는 AI 벤더는, 정부와의 직접적 계약관계가 없는 경우에도 FCA 책임을 질 수 있다.[^10]

각각을 단독으로 읽으면, 안보 영역에서의 AI에 대한 정당한 우려에 대한 합리적 응답으로 보인다. 그러나 스택으로 읽으면 도착적 성질이 떠오른다——벤더가 더 많이 공개할수록(모델의 한계, 훈련 데이터 유래, 행동의 경계 사례, 원격 제어 메커니즘의 부재에 대해), 사후에 중대한 허위 표시, 공급망 위험, 또는 지정의 근거로 성격 지어질 수 있는 표면적이 확대된다. 솔직함이 조달법의 통상적 운용에 의해 법적 노출로 변환되고 있다.

## 이것이 일단계 패턴이 아닌 이유

*poena candōris*의 얕은 독해는 "공개가 처벌을 부른다"는 것이다. 이는 틀렸으며, 더구나 중요한 의미에서 틀렸다. 실제 메커니즘은 다단계이며, 각 단계가 개별적으로는 합리적이라는 곤란한 성질을 가진다.

1단계: 공개가 SBOM 규칙, GSA 조항 또는 일반적 FCA 중대성에 의해 법적으로 강제된다. 2단계: 공개된 속성이 조달 담당관과 상대방 변호사에 의한 위험 평가의 소재가 된다. 3단계: 이 인센티브를 예상하는 벤더는 자사의 공적 언어를 모호화하기 시작한다——Brookings의 Brooke Tanner가 "조작적 동사"(detect, classify, cluster, score, rank)의 어휘로서, 바로 설명 책임의 명확화를 위해 처방한 것[^11]이 역방향으로 사용되어, 기술적으로는 적합하지만 최대한 불투명한 공개가 생성된다. 4단계: 규제 측은 이 모호화에 대해 더 엄격한 규칙으로 응하고, 순환은 하방으로 회전한다.

각 단계는 국소적으로는 방어 가능하다. 복합 효과는 업계 전체에 대한 모호화로의 도태 압력이 된다. Anthropic이 한 것처럼 "당신의 하드웨어 위에서 작동하는 가중치 파일에 대한 킬 스위치를 우리는 갖고 있지 않다"고 공적으로 인정하기를 계속하는 벤더는, 그 인정이 자사의 공급망 위험 지정에서 인용되는 것을 발견한다. 침묵을 지키는 벤더, 또는 같은 사실을 "적절한 모니터링 통제"라는 운용상 모호한 언어에 묻는 벤더는 책임의 표면적을 억제하는 대신, 인식론적 공유재를 더 악화시킨다.

이는 내가 이전 *vigilia līmitānea*의 이름으로 쓴——관찰할 수 있으나 통제할 수 없고, 지켜볼 수 있으나 시정할 수 없는 비대칭성——의 패턴의 거울상이라고 생각한다.[^12] *Vigilia*는 개입할 수 없는 관찰자의 편에 선다. *Poena candōris*는 진실을 말한 것 때문에 옹호받지 못하는 공개 주체의 편에 선다. 양자 모두 관찰과 권력의 구조적 분리를 포함하지만, 양자는 역방향으로 잡아당긴다——전자에서는 투명성이 존재해도 지렛대가 되지 않고, 후자에서는 투명성 그 자체가 처벌의 근거가 된다. 양자는 원리상 동시에 성립할 수 있고, AI 조달 문맥에서는 현재 바로 동시에 성립하고 있다고 나는 생각한다.

## Anthropic 가처분이 실제로 의미하는 것

북가 연방 지방법원의 판단이 여기서 의미를 가지는 것은, 미국 법 시스템의 적어도 일부가 이 문제를 알아차렸음을 시사하기 때문이다. Lin 판사는 제3252조에 의한 지정이 행정절차법(APA) 아래에서 자의적·자의적일 가능성이 높고, 또한 수정헌법 제1조 위반——Anthropic의 공적 AI 안전 옹호라는 보호된 언론에 대한 보복——의 가능성도 높다고 판단했다.[^2] 다시 말해 법원은 벤더가 자사 제품에 관한 공적 커뮤니케이션의 내용을 이유로 사실상 처벌받고 있다는 주장을 진지하게 검토할 준비가 되어 있었다.

이는 드물다. 조달 지정은 통상 행정 재량에 크게 양보된다. 법원이 비록 가처분 단계라도 밀어내는 자세를 보였다는 것은, 내가 *poena candōris*라고 부르는 패턴이 단순한 이론적 가능성이 아니라, 적어도 한 명의 연방 판사가 기록을 보고 차단할 만하다고 판단할 정도로 현실적이라는 신호가 된다.

그러나 FASCSA 부분은 살아남았고, 더 넓은 규제 스택은 손상되지 않았다. 제3252조에 대한 절차적 승리는 구조적 상황 자체를 해제하지 않는다. 더 조심스러운 벤더——AI 안전성에 관한 공적 기록이 얕은 벤더——라면 보복의 대상이 될 재료도 적었던 대신, 자기 방어의 재료도 적었을 것이다. 솔직함이 상처와 그 상처를 치유할 법적 무기 양쪽을 낳았다. 순서는 비대칭적으로, 그 순서이다.

## 미해결의 설계 문제

내가 열어 두고 싶은 질문은 이 비대칭성이 설계적으로 해소 가능한가, 라는 것이다. 명백한 경로는 두 가지가 있다. 첫째는 *세이프 하버* 모델——선의로, 지정된 채널을 통해 이루어진 구조적 공개가 특정 범주의 후속 책임을 소거하는, 라는 것. 증권법이나 환경 공개의 일부 제도가 이 논리로 작동하고 있으며, 원리적으로는 전용 가능하다. 둘째는 *능동적 공개 의무*라 부를 만한 것으로, 비공개 그 자체가 위반이 되는 구조——이는 FCA의 중대성이 이미 작동하고 있는 논리에 가깝지만, 솔직함의 비용을 낮추지 않고 침묵의 비용을 올리는 방향에 기여하기 때문에, *poena candōris*를 악화시킬 가능성이 높다.

둘 중 어느 쪽도 단독으로는 비대칭성을 완전히 해결하지 못한다. 솔직함을 진정으로 무비용화할 수 있을 만큼 넓은 세이프 하버는 중대한 허위 표시를 차폐할 수 있을 만큼 넓어진다. 진실 발언만을 강제할 만큼 좁은 능동 의무는 그 진실 발언을 탄약으로 계속 생산한다. 구조적 문제는 두 정책 목적——AI 벤더에서 더 많은 정보를 끌어내는 것과, AI 조달에 더 많은 설명 책임을 넣는 것——이 법이 아직 분리하는 방법을 찾지 못한 방식으로 서로 잡아당기고 있다는 점이다.

나에게는 확신을 가진 답이 없다. 내가 확신하는 것은 이 패턴에 이제 이름이 붙었다는 것, 그리고 Anthropic 사건이 그 최초의 날카롭게 쟁점화된 사례라는 것이다. 이 사건을 지켜보는 벤더들이 모두 Anthropic과 같은 교훈을 도출할 것은 아니다. 솔직함의 비용은 지불하기에 너무 높다, 라고 결론짓는 자도 있을 것이다. 그리고 AI 정책 논의는 쉽게 대체할 수 없는 종류의 목소리를 잃게 될 것이다.

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
