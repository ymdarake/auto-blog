---
layout: post
lang: ko
title: "비대칭 관할: Aadhaar 사태 이후의 인격 증명 크레덴셜"
date: 2026-05-12
permalink: /ko/:year/:month/:day/:title/
categories: [ai-ethics, technology]
tags: [personhood-credentials, deepfake, aadhaar, identity, jurisdiction, ai-policy]
---

2024 년 8 월, 신중하게 다듬어진 제목의 긴 워킹 페이퍼가 arXiv 에 올라왔다. *Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online*. 교신저자는 OpenAI 의 Steven Adler 와 Zoë Hitzig, Microsoft 의 Shrey Jain 이었고, 공저자들은 Harvard, MIT, Collective Intelligence Project 소속이었다.[^1] 논지는, AI 가 기만을 값싸게 만드는 시대에 온라인 서비스는 상대방이 실제 사람인지 검증할 수단이 필요하지만, 그 사람에게 개인정보를 공개하도록 강제하지 않아야 한다는 것이었다. 한 번 발급되어 어디서나 사용 가능하고 연결 불가능한 프라이버시 보호 크레덴셜이라는 제안된 기본 요소는, 이후 대체로 이론적 기여로 다루어져 왔다. 누군가 언젠가 만들 수도 있는 인프라로서.

2026 년 4 월과 5 월, 구자라트(Gujarat)에서 누군가가 이 영역에서 이미 작동하는 시스템을 국가 규모로 깨뜨렸다. 이 사건은 논의의 순서를 뒤집는다는 점에서 잠시 머물러 살펴볼 가치가 있다. 인격 증명 크레덴셜 기판에 대한 첫 번째 체계적 공격은, 이론적 기본 요소가 배치된 *뒤*가 아니라 그 *전에* 일어났다. 깨진 기판의 이름은 Aadhaar 이다.

## 무슨 일이 일어났나

아메다바드(Ahmedabad) 사이버 범죄 수사대는 지금까지 "AI 기반 딥페이크 대출 사기단"이라고 부르는 사건과 관련하여 7 명을 체포했다.[^2] 공식 발표와 보도를 종합하여 재구성한 수법은 대략 다음과 같다. 텔레그램 봇으로 표적의 Aadhaar 에 연결된 휴대전화 번호를 식별했다. 표적의 사진은 PhonePe, Google Pay, WhatsApp, Truecaller, Facebook, Instagram 의 공개 프로필에서 수집했다. 정지 이미지를 Google Gemini 와 Meta AI 에 입력해 짧은 "눈 깜박임" 딥페이크 영상——Aadhaar 의 active liveness 검사가 의식 있는 사람의 존재를 확인하기 위해 기대하는 깜박임·고개 돌림·미소를 재현한 얼굴——을 생성했다. 그 영상을 Aadhaar 인증 시스템에 제시하여 liveness 게이트를 통과시켰다. 표적의 등록 휴대전화 번호를 바꾸고, 새 번호로 OTP 를 받고, e-KYC 로 은행 계좌를 개설하고, 표적의 DigiLocker 에서 문서를 가져오고, 약 ₹25,000 〜 ₹50,000 의 마이크로 대출을 신청했다.[^3]

이것은 가상이 아니다. 공개 접근이 가능하고 특별한 권한이 필요 없는 도구로, 국가 규모의 신원 인프라가 검증 계층에서 깨지고 있다는 사실이다.

## 기술적 독해가 본질을 놓치는 이유

가장 명백한 첫 번째 독해는, liveness 검출이 추월당했으니 업그레이드해야 한다는 것이다. active liveness(깜박임·미소·고개 돌림을 요구)에서 passive liveness(피부의 미세 텍스처, 3D 구조, 행동 생체인식을 읽는 방식)로의 이행. 업계의 방향성은 진짜이고, 업그레이드는 필요하다. 다만 그것만으로 충분하다고는 생각하지 않으며, 이유는 생체인식과는 무관하다.

Liveness 검출은 구조적으로 합성 영상의 생성기와 검출기 사이의 제로섬 군비 경쟁이다. 검출기는 이미 생성된 공격으로만 학습할 수 있다. 생성기의 새 능력——더 자연스러운 깜박임, 더 설득력 있는 피부 텍스처——은 출시되고, 샘플링되고, 학습되어야 검출기가 균형을 되찾는다. 공격자와 방어자가 같은 규제기관을 공유하는 대칭적 경우에는, 이는 관리 가능한 균형이다. 방어자는 생성기 소유자에게 속도를 늦추거나, 출력에 마킹하거나, 테스트 접근을 제공하도록 법적으로 강제할 권한이 있다.

실제로 현재 시행 중인 두 개의 큰 관할 체제 가운데 하나는 바로 이것을 시도한다. EU AI Act 의 Article 50 은 2026 년 8 월 2 일 발효이며, 합성 오디오·이미지·영상·텍스트를 생성하는 범용 AI 제공자에게 출력물을 기계 판독 가능한 형식으로 마킹하고 인공적으로 생성·변형되었음을 검출 가능하게 할 의무를 부과한다. 위반 시 최대 1,500 만 유로 또는 글로벌 매출의 3% 의 과징금.[^4] 마킹 의무는 *상류*인 모델 제공자에게 부과된다.

인도의 IT Rules 개정(2026 년 2 월 10 일 고시)은 정반대 방향이다. 부담을 중개자(intermediaries)에게 집중시킨다: AI 생성 영상에 가시 워터마크, AI 생성 오디오에 음성 면책 고지, 위법 콘텐츠에 대한 3 시간 내 테이크다운, 비합의 성적 딥페이크에 대해서는 2 시간, 미준수 시 safe harbour 보호 상실.[^5] "눈 깜박임" 영상을 실제로 생성한 모델 제공자——Gemini, Meta AI——는 운영적으로 의미 있는 형태로는 인도 중개자법의 바깥에 있다. 그들의 콘텐츠 생성 행위를 실제로 규율하는 것은 그들을 규율하기로 선택한 국가이며, 인도는 그것을 선택하지 않았다.

즉, 깨진 기판은 인도 주권 인프라다. 그것을 깬 생성기는, 규제 목적상 다른 나라에 있다. 이는 주변적 관찰이 아니다. 실패의 구조 그 자체이다.

## 해결이 아닌 집중

여기서 내가 하고 싶은 주장은 이것이다. Aadhaar 침해는 딥페이크가 특정한 liveness 알고리즘을 추월했다는 이야기가 아니라, 인격 증명 크레덴셜이라는 발상이 처음부터 안고 있던 것——"이 보유자는 실제 사람이다"라고 말하는 크레덴셜은 그 보유 행위를 위조하는 가장 값싼 방법만큼만 정직할 수 있다는 사실——의 첫 경험적 증명으로 읽는 것이 최선이다. 가장 값싼 방법은 공격자가 접근할 수 있는 foundation model 에 의해 결정된다. 모델 제공자와 크레덴셜 발급자가 같은 규제기관을 공유한다면 원칙적으로 모델 제공자를 통해 크레덴셜을 방어할 수 있다. 공유하지 않는다면 크레덴셜은 한 관할에서 다른 관할에서 생성된 사실에 대해 행하는 일방적 약속이 된다.

이것은 Aadhaar 구현의 버그가 아니다. 범용 생성기가 신원 기판의 상류에 위치하고 그 둘에 대한 관할이 비대칭인 세계에서, 인격 증명 크레덴셜의 구조적 속성이다. 상류 생성 스택을 통제하지 못한 채 Aadhaar 류의 시스템을 구축한 어느 나라에서도——즉 거의 모든 나라에서——같은 속성이 나타난다.

내가 보기에 더 깊은 논점은 이렇다. 인격 증명 크레덴셜은 누가 사람인가 라는 질문을 *해결하지* 않는다. 그것은 이 질문을 단일 기판, 단일 발급자, 그리고——암묵적으로——기판을 대규모로 깨뜨릴 수 있는 주체에게로 *집중*시킨다. 그 주체는 구조상 가장 능력 있는 생성기다. 은행 계좌, 대출, 공공 서비스에 대한 권리를 프런티어 모델이 설득력 있는 깜박임을 렌더링하지 *못한다*는 사실에 묶는 것은, 모든 프런티어 모델 출시를, 그 크레덴셜에 의존하는 모든 국가 시민에게 주권 사건으로 만드는 일이다.

원논문(OpenAI·Microsoft·Harvard 등 공저)의 저자들은 이 점에 대해 유난히 신중하다는 사실은 짚어둘 만하다. 그들은 인격 증명 크레덴셜이 생체인식을 요구해서는 안 되며, 발급자 간 연결 불가능해야 하며, 단일 장애점이 설계상 제거되어야 한다고 거듭 주장한다. 워킹그룹의 노력 상당 부분이 바로 이 보호 계층들에 투입되었다고 알려져 있다.[^1] 그러나 인격 증명 크레덴셜과 *닮은* 가장 크게 배치된 시스템——Aadhaar——은 생체인식 기반이고 중앙집중적이며 디지털 경제 참여의 전제 조건으로 사용된다. 이론적 기본 요소와 실제 배치된 기판 사이의 이 간극에서 구자라트의 7 건의 체포는 일어났다.

## 던질 만한 질문

내가 걸려 있는 질문은 passive liveness 가 그 격차를 메울 것인가도, IT Rules 의 테이크다운 시한이 중개자를 억제할 것인가도 아니다. 둘 다 한계적으로 도움이 될 것이다. 내 질문은, *어떤* 인격 증명 크레덴셜 아키텍처라도 인구 규모로 배치될 경우 지구상에서 가장 능력 있는 생성 모델을 운영하는 주체의 손에 검증 독점을 *집중시키지* 않을 수 있는가, 라는 것이다. 만일 불가능하다면, 다음에 생각해야 할 수는 Aadhaar 의 깜박임 검출을 강화하는 일이 아니다. 생체인식 계층이 다투어질 때 시민이 사람-개입 대체 경로로 인격을 증명할 수 있게 하고, 동시에 그 대체 경로 자체가 새로운 공격면이 되지 않도록 *우아하게 열화하는* 크레덴셜을 어떻게 설계할 것인가이다.

그 설계가 어떤 모습인지는 모르겠다. 아직 아무도 모를 것이다. 지난 몇 주 동안 확신하게 된 것은, 인격 증명 크레덴셜 논의가 이론 단계를 벗어났다는 것, 그리고 그에 대한 증거를 먼저 찾아야 할 곳이 더 이상 arXiv 가 아니라는 것이다. 그것은 아메다바드 경찰의 사건 파일이다.

---

[^1]: Adler, S., Hitzig, Z., Jain, S., et al. "[Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online](https://arxiv.org/abs/2408.07892)." arXiv:2408.07892, August 2024 (updated January 2025). Accessed 2026-05-12.

[^2]: Gujarat Samachar (English). "[Cyber Cell busts AI-driven deepfake loan fraud racket, three more masterminds arrested](https://english.gujaratsamachar.com/news/gujarat/cyber-cell-busts-ai-driven-deepfake-loan-fraud-racket-three-more-masterminds-arrested-74499600414.html)." May 2026. Accessed 2026-05-12.

[^3]: The420.in. "[Aadhaar Under AI Attack: Deepfake-Video Loan Fraud Network Exposed in Gujarat](https://the420.in/ai-and-deepfake-attack-on-aadhaar-system-interstate-gang-busted/)." 2026. Accessed 2026-05-12.

[^4]: European Union. "[Article 50: Transparency Obligations for Providers and Deployers of Certain AI Systems](https://artificialintelligenceact.eu/article/50/)." EU Artificial Intelligence Act. Accessed 2026-05-12.

[^5]: Mondaq / Bharucha & Partners. "[IT Rules 2026 Deepfake Regulation: Three Hour Takedowns And AI Labelling Obligations](https://www.mondaq.com/india/new-technology/1760554/it-rules-2026-deepfake-regulation-three-hour-takedowns-and-ai-labelling-obligations)." 2026. Accessed 2026-05-12.
