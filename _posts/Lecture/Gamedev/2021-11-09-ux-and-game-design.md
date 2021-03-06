---
title: '게임 기획과 UX'
date: 2021-11-09 12:00:00 +0900
categories: [Lecture, Game Dev]
tags: [Game Design]
---

> 글을 읽기 미리 앞서 UX/UI 가 아님을 유의하라. 필자는 UI와 UX를 분리하여 보아야 한다고 생각하며, UX는 게임의 모든 요소에 적용되어야 한다고 생각한다.
{: .prompt-warning }

## 게임 기획과 인지심리학 : 지각, 기억, 주의, 동기, 정서

정보 '처리' 와 학습은 자극에 대한 지각으로 시작해 궁극적으로는 시냅스 변경, 즉 기억에서의 변경으로 끝이 난다. 자극에 온전히 투입되는 주의 리소스 수준은 해당 자극에 대한 기억의 강도를 결정한다. 두 가지 다른 주요 요소, 즉 동기와 정서도 학습의 질에 영향을 미친다. 마지막으로 학습 원리를 적용하면 전체 '과정' 을 향상시킬 수 있다.

### 지각

무언가를 인지하는 과정이다.

- 베버-페히너 편향: 두가지 자극의 차이를 인지하려면 적당한 상대역이 존재해야 하며, 이는 자극의 강도가 강할수록 인지하기 힘들다. 예를들어 1.1kg와 1.2kg의 물건을 양손에 올리면 무게의 차이를 인지하기 쉽지만 11kg와 12kg의 무게의 차이는 더 인지하기 힘들다.

- 게슈탈트 원리: 전경/배경(전경과 배경을 식별함), 다안정성(모호성이 있는 것을 보고 양쪽으로 인식가능함), 폐쇄성(분리된 조각이 아닌 전체 사물을 보는 경향, 열린 형태를 닫으려는 경향이 있음), 대칭(대칭을 기반으로 입력을 체계화함), 유사성(같은 특성을 가진 요소들을 한데 묶는 것), 근접(서로 가까운 요소를 같은 그룹으로 지각하는 것)

### 기억

감각 기억, 작업 기억, 장기 기억 이 있으며 감각 기억은 1초 내외의 짧은 시간동안 감각적으로 기억하는 것이고, 작업 기억은 30초 정도 기억할 수 있으며 약 4가지 정도를 동시에 수행할 수 있는 연산하는 기억이기도 하다. 단기기억과 약간 다름. 장기 기억 반영구적으로 기억하는 것. 하지만 이것은 변질될 수 있다.

기억의 망각 곡선은 20분이면 60%를 잊어버릴 정도기 때문에 반복적으로 지각시켜주어야 하고 지각이 반복될수록 점진적으로 반복의 간격도 넓어져도 된다.

### 주의

플레이어는 무언가 집중을 해야 그것의 기억의 강도가 강해지는데, 이때 뇌가 주의를 기울일 수 있는 자원(리소스)는 한정적이고, 멀티태스킹을 할수록 그 효율이 떨어지는데 여러가지 작업들을 동시에 처리할 때 그 작업들을 관리하는 데에도 리소스가 사용되기 때문이다. 또한, 주의는 처리할 특정할 입력을 선택하고 나머지는 걸러내는 성질이 있으며 이는 부주의맹을 일으킬 수 있다. 즉, 분명히 지각의 영역 안에 들어와 있음에도 주의 밖이면 인식하지 못할 수 있다.

### 동기

무언가 하기 위해서는 동기가 필요하며, 이 동기가 최고 수준에 이르는 몰입 단계가 이루어지려면 너무 쉽지도, 어렵지도 않은 과제가 필요하다. 또한, 동기는 4가지로 조정할 수 있는데

- 정적 강화: 보상을 주면 행동 빈도의 증가를 유도
- 부적 강화: 처벌을 철회하면 행동 빈도의 증가를 유도
- 정적 처벌: 부정적인 처벌을 주어 행동 빈도의 감소를 유도
- 부적 처벌: 긍정적인 것을 제거하는 방식으로 행동 빈도의 감소를 유도할 수도 있음

또한, 이전에 강화되었던 행동이 더이상 강화되지 않으면 행동 빈도는 감소하며 변동 비율은 행동 유도에 가장 효율적이다. (무작위 수의 반응 후 무작위의 보상)

### 정서

감정과 비슷하지만 상황과 상관 없이 좀더 원초적인 단계에서 발생한다(가짜 거미를 봐도 일단 회피한다) 불공평한 감정은 가능한 회피하여야 한다. 유저의 정서에 따라 잘못된 귀인을 할 수 있으며, 로딩이 느리다는 등의 이유로 게임플레이 전체가 나쁜 것 처럼 느껴질 수 있다.

### 학습 원리

1. 플레이어에게 적절히 보상하라
2. 플레이어가 새 메커니즘을 학습할 때에는 처벌을 피하라
3. 인지과학의 지식으로 인간의 능력과 한계(지각,주의,기억,동기,정서)를 고려한 학습 환경을 조성하라
4. 플레이어가 상황에서 목적을 갖고 실전을 통해 배우게 해라
5. 플레이어에게 가르쳐야 하는 중요한 요소는 깊게 처리해라. 깊게 처리될수록 학습이 깊게 된다(머리를 쓰고 노력을 요하는 과제일수록 더 확실히 학습됨)

## 마크 르블랑의 게임쾌락 분류

### 감각(sensation)

감각의 쾌감은 오감으로 느끼는 것들

주로 미적 요소가 영향을 미치며, 이런 쾌감은 형편 없는 게임을 좋게 만들어주지는 못하지만, 종종 좋은 게임을 더 낫게 만들어줄 수 있다.

### 판타지(fantasy)

공상의 세계, 그리고 자신을 자신이 아닌 다른 무언가로 상상하는 것

### 서사(narrative)

선형적인 이야기가 아니라, 일련의 사건이 벌어지는 극적인 전개, 스토리와 연출

### 도전(challenge)

모든 게임에는 본질적으로 해결해야 할 문제가 있으며 도전과 리스크를 통해 재미를 느끼게 된다

### 친교(fellowship)

우정, 협력, 커뮤니티 등에서 얻을 수 있는 모든 종류의 즐거움

때로는 게임과 상관 없이 이것이 게임을 하는 가장 큰 요인이자 원인이 될 수 있으며, 플레이어가 게임을 오래 즐길 수 있게 해주는 요인이기도 하다

### 발견(discovery)

새로운 것을 발견하는 것. 탐험하는 것이나 전략을 수립하는 것 등의 모든 종류의 발견이다

이 또한 도전과 같이 게임 플레이의 핵심으로 볼 수 있으며, 학습하는 재미이다

### 표현(expression)

스스로를 표현하는 쾌락과 무언가를 창조하는 쾌락

자신의 캐릭터를 커스터마이징하거나 레벨 에디터로 자신만의 맵을 만드는 등의 것

### 복종(submission)

현실 세계를 떠나서 새롭고 더 재미있는 규칙과 목적이 있는 가상의 세계로 들어가는 것

게임에만 존재하는 규칙에 복종하여 얻는 재미이다. 보드게임을 생각해 보면 원하는 행동으로 원하는 결과를 내는 것이 아닌, 게임의 규칙에 따라 이기기 위해 가장 좋은 선택을 해야하기도 한다

## 닐슨 노르만의 10가지 사용자 휴리스틱 - 사용성을 평가할 수 있는 척도

1. 시스템 상태의 가시성: 시스템은 수행할 수 있는 행위에 대한 정보를 사용자에게 전달해야 하고, 사용자가 상호작용을 한 후에는 신속하고 적절한 피드백도 있어야 한다.

2. 시스템과 현실 세계와의 일치: 시스템은 타깃 고객에게 익숙한 언어와 개념을 갖고 소통해야 한다. 또한, 현실 세계에 대한 메타포(은유)나 유추도 사용해야 한다. 예를 들어 배낭으로서 구현한 인벤토리는 친숙한 메타포이다.

3. 사용자 통제와 자유: 사용자는 실수를 하거나 생각을 바꿀 수도 있다. 쇼핑을 할 때 사고 싶은 것을 추가한 후 삭제를 편하게 하는것 등이 해당된다.

4. 일관성 및 표준: 플랫폼 관례에 따르는 것은 중요하다. 익숙한 단어, 아이콘, 액션 등은 사용자가 시스템의 작동 방식을 이해하는 데 도움이 되기 때문이다.

5. 오류 방지: 시스템은 사용자 오류가 발생하지 않는 방식으로 설계되어야 한다. 예를 들어 사용자가 변경을 저장하지 않고 파일을 닫는 등의 잠재적 위험이 있는 작업을 완료하기 전에 시스템에서는 확인을 요청해야 한다.

6. 재인(recognition) 보다는 회상: 사용자의 기억 부하를 최소화하기 위해 개체, 동작, 옵션을 볼 수 있게 만드는 것은 중요하다. 사용자가 대화를 하다가 다른 쪽 이야기를 억지로 기억하게 해서는 안 된다. 사용자는 웹이나 앱 등에서 자신의 현재 위치를 추적할 수 있어야 하는데, 이를 브레드크럼 트레일(breadcrumb trail), 주로 "이동 경로" 라고 한다. 예를 들어 컨트롤러의 전체 이미지와 함께 특정 상황에서 사용자가 눌러야 하는 버튼을 밝게 표시하면 플레이어가 버튼의 위치를 떠올릴 필요가 없기 때문이다.

7. 사용의 유연성 및 효율성: 사용자가 인터페이스에 옵션을 더하거나 없애 커스트마이징하여 자신의 경험을 재단할 가능성을 기꺼이 제공하라. 게임에서 커스텀 키매핑을 지원하는 것 등이 속한다.

8. 미적이고 미니멀리스트에 입각한 디자인: 정신을 산만하게 하고 관계 없는 모든 정보를 없애라. 구글의 기본 탭은 이를 잘 구현한 훌륭한 사례이다.

9. 사용자가 오류를 인식, 진단, 복구하도록 도움: 에러 메시지는 문제를 정확하게 설명하고 해결책을 제시하기 위해 이해할 수 있도록 써야 한다. 404 오류보다는 "찾고 있는 페이지를 찾을 수 없습니다" 와 같은 표현을 사용하고, 그의 해결책 또한 제시해라.

10. 도움말 및 문서화: 문서 없이도 시스템을 사용할 수 있어야 하지만, 사용자에게 필요할 때 효과적이고 쉽게 이해할 수 있는 도움말을 제공하는 것은 중요하다. 사용자가 무언가 잊어버렸을 때 참고할 수 있도록 모든 툴팁을 모아 두면 좋다.

**UX 디자인은 '사용성'과 '몰입도' 라는 주요 요소로 나눌 수 있다.**

다음은 위의 휴리스틱을 게임에 적용하였을 때 공통으로 주로 나타나는 [게임 휴리스틱] 의 예이다.

- 컨트롤은 커스터마이징 가능해야 하고, 업계 표준으로 디폴트 설정해야 한다.
- 피드백은 사용자 컨트롤을 표시하기 위해 즉각적으로 제공해야 한다.
- 플레이어에게 압박감을 주되 불만이나 좌절감을 주지 않도록 게임 페이스를 조절한다.
- 명확한 목표를 제공하고 게임 내내 단기 목표뿐만 아니라 중요한 목표를 이른 시기에 제시한다.
- 게임에는 플레이어가 게임에 더 몰입할 수 있도록 그들의 역량을 증가시키고 그들의 능력을 커스터마이징 해서 확장할 수 있는 보상이 있어야 한다.
- 플레이어는 게임플레이의 일부로 이야기를 찾아낸다.
- 한꺼번에 많은 텍스트를 쓰지 않는다.
- 플레이어는 자신감에 차 있어야 한다. 즉, 위협과 기회에 반응할 시간과 정보가 필요한다.
- 플레이어가 꼼짝 못하거나 헤매기 쉽게 만들지 마라.
- 사용자 인터페이스(UI)는 게임 안에서 그리고 게임 간에 일관되어야 한다.
- 게임에서 사용되는 용어와 언어는 이해하기 쉬워야 한다.
- 사용자 인터페이스(UI)는 플레이어가 게임 플레이의 일부가 아닌 실수나 잘못을 하지 않도록 설계해야 한다.

## The Gamer's Brain의 7가지 UX 사용성

### 사인 및 피드백

플레이어에게 게임의 진행 상황을 알리거나, 특정 행위를 해내도록 권장하는 모든 신호를 나타낸다.

- 정보 제공용 사인 : 플레이어에게 시스템 상태를 알린다. 체력, 레벨, 미니맵, 장착중인 무기, 점수 등에 해당한다. 이들은 쉽게 알아볼 수 있어야 하지만 게임의 주요 행위에 대한 플레이어의 주의를 방해하거나 분산하면 안된다.

- 권유용 사인 : 플레이어가 특정한 행위를 해내도록 설득하는 것. NPC 의 머리 위 노란 느낌표는 플레이어가 해당 NPC와 상호작용 하라는 뜻일 수 있다. 대부분의 권유용 사인은 플레이어의 주의를 끌어야 하기 때문에 다른 요소들과 대비를 이뤄야 한다. 또는 숨겨진 장소로 가는 살짝 금이 간 벽은 의도적으로 눈에 띄지 않도록 제작될 수 있다. 일부 정보 제공용 사인은 즉각적인 주의를 요할때 권유용 사인으로 바뀔 수 있는데, 예를 들어 치명상을 입어 체력이 적을 경우 이를 강조하여 엄폐하거나 회복을 유도할 수 있다.

- 피드백 : 플레이어 행위에 대한 시스템의 반응을 플레이어에게 알리는 특정한 사인이다. 예를들어 플레이어가 움직일 때 캐릭터의 애니메이션은 피드백의 한 예이다. 벽에 막혀 지나갈 수 없다면 벽을 미는듯한 행동을 보이거나, 플레이어가 공격받아 체력이 감소하는 HUD 등도 피드백이다. **모든** 플레이어 행위는 그 결과를 알리는 즉각적이고 적절한 피드백이 있어야만 한다. 예를 들어 스킬을 사용했을 때 그 스킬의 쿨다운을 시각적으로 보여주어야 하며, 스킬을 사용시 사용이 되지 않을 때는 효과음과 함께 아이콘이 빨간색으로 짧게 변하며 좌우로 흔들리는 듯한 효과를 주면 확실히 알릴 수 없다. 반대로 이게 없다면 버그로 키가 눌리지 않은 것인지, 또는 쿨타임이라는 것이 있다는 것도 알기 힘들 수 있다.

게임에 있는 모든 기능과 가능한 상호작용은 연결된 사인과 피드백이 있어야 한다.

### 명료성

게임에서 지각적 관점에서 모든 사인과 피드백을 이해하는 플레이어의 능력과 관련된다. 가독성 좋은 폰트, 눈에 띄는 효과, 간료한 텍스트 등이 있다. 많은 정보는 한 눈에 파악할 수 있도록 인포그래픽을 사용하는 것이 좋다(글머리 기호, 막대 그래프 등). 게슈탈트 원리 또한 이에 응용할 수 있으며, 또한 혼동을 피하기 위해 고려해야 하는 것이다.

사인 명료성에 대해 고려해야 하는 것으로 신호 탐지 이론도 존재하는데, 모든 추론과 의사 결정은 일정 수준의 불확실성이 있을 때 일어난다는 것이다. 간단하게, 강조해야 하는 것이 많을 경우 그 조절을 잘해야 한다.

### 기능에 따르는 형태

게임(형태)에 주어진 모든 캐릭터, 아이콘 또는 심벌의 형태가 어떻게 그 의미(기능)를 전달하느냐를 나타낸다. 게임 요소의 시각적 표현은 플레이어가 해당 요소와 어떻게 상호작용하는지 직감적으로 알수 있어야 한다. 플레이어는 아이콘의 의미가 혼동돼 잘못 이해했음을 알게 됐을 때보다 기대했던 것이 거짓임을 알게 되었을 때 훨씬 더 불만이나 좌절감을 갖기 때문에, 게임의 스킬 아이콘과 같은 것에서 혼동을 일으키게 할 바에는 새로운 표현을 배우게 하는게 낫다.

직관적인 모든 것은 배울 필요가 없고, 인지 부하를 최소화 하는데 좋으므로 가능한 한 형태를 통해 기능성을 전달하도록 노력하라. 아니면 적어도 플레이어의 기대를 기만하지 않는지 살펴보아야 하는데, 어떤 구역이 탐색할 수 있을 듯 보이는데 실제로는 보이지 않는 벽이 막고 있다면 짜증이 날 수 있다.

### 일관성

비디오 게임의 사인, 피드백, 컨트롤, 인터페이스, 메뉴 네비게이션, 월드 룰, 전체 규약은 반드시 일관성이 있어야 한다. 게임에서 문을 열 수 있으면 모든 문은 열 수 있어야 하고, 만약 일부 유형의 문만 열릴 수 있다면 헷갈리지 않도록 시각적인 처리를 달리 해야 한다. 두가지 요소가 비슷한 형태를 보인다면 플레이어는 둘이 비슷한 기능을 갖거나 비슷한 행동 방식을 보일 것이라 기대할 수 있다.

만약 이미 있는 게임 규약(비슷한 장르의 공통 규범이나 자사 게임에서 만든 규약)을 바꿀 때에는 정확한 의도가 있어야 한다. 그렇지 않다면 이미 있는 규약을 다시 만드느라 쓸데 없이 시간을 낭비하지 말아라.

### 최소한의 작업 부하

플레이어의 인지 부하(주의와 기억) 및 신체적 부하를 반드시 고려하고, 언제나처럼 게임 자체의 도전이 아닌 이상 최소화해야 한다.

신체적 부하를 해결하는 예제중 하나로 HCI(Human-Computer Interaction)분야의 피츠Fitts의 법칙이 있는데, 작은 버튼은 큰 버튼을 가리킬 때보다 시간이 더 걸리고, 서로 너무 가까이 붙은 두 개의 버튼은 사용자가 다른 하나를 클릭할 때 실수로 클릭할 위험이 높고, 화면 한쪽 코너에 위치한 버튼은 조준하기 더 쉬운데 화면 끝까지 마우스를 움직이면 지나칠 일이 없기 때문이다. 또한 힉-하이먼 법칙으로 사용자가 의사 결정하는데 걸리는 반응 시간은 화면에 표시된 옵션의 개수에 따라 로그log로 증가한다는 것이 있다.

인지 부하를 해결하기 위해서는 인지심리학에 따른 인간의 지각, 기억, 주의, 동기, 정서의 한계와 영향으로써 해결해야 한다. 가능하면 사용자가 생각하지 않아도 되도록 하는 것이 좋다. 인지 부하가 증가되면 그것이 무엇이든 작업을 방해하기 때문이다. 하지만 과정의 깊이가 깊을수록 파지가 향상된다는 점(인지 부하가 높을수록 기억이 오래가고 이해가 깊어진다) 또한 있다는 것을 알아야 한다. 그래서 핵심 경험에 더 많은 인지적 리소스를 할당할 수 있도록 핵심 경험에 직접적으로 연관되지 않은 모든 과제에만 "최소한의 작업 부하 원칙" 이 적용된다는 것이다.

### 오류 방지 및 복구

플레이어는 비디오 게임에서 실수를 하고, 죽을 수도 있다. 이것은 게임 경험의 일부지만, 인지 부조화로 인해 플레이어가 자신이 무엇을 잘못했는지 완벽하고 명확하게 이해하지 못하면 "에이 똥겜이네"를 외치며 게임을 떠날 수 있다. 실패의 아픔을 느끼면서도 게임을 진행하게 만드는 무언가에 정말로 동기부여 되지 않는 한에는(유명한 게임이라 친구들이 다 해서 어쩔수없이 하는 등)

- 오류 방지
위에서도 언급되었지만 게임 다운로드 99%에서 다운로드 취소나 확인/취소 같은 극적인 기능 의 버튼들을 서로 가까이 배치하고 색깔도 똑같이 한다는 등의 실수를 하지 못하도록 확인 메세지를 출력하고, 실수로 클릭하지 않도록 해야한다.

그리고 플레이어의 오류를 방지하기 위해서 정보를 주어야 한다. 저장하지 않고 나가려 한다면 저장하지 않은 데이터는 모두 삭제된다는 팝업, 체크포인트가 있는 게임에서 다음 체크포인트까지 도달하지 않으면 일어나는 일, 매칭메이킹에서 매치를 포기하면 어떤 일이, 왜 일어나는지 등으로 플레이어가 지식의 부재로 오류가 일어나서는 안된다.

- 오류 복구
게임에서 실패했을 때 재도전 할 수 있게 해주는 것, 리그오브레전드의 상점에서 지원하는 Undo 기능 등, 오류를 복구해 줄 수 있는 기능에 속한다.

### 유연성

게임 설정에서 플레이어가 마음대로 선택할 수 있는 사용자 지정(커스터마이징) 및 조정을 말한다. 왼손/오른손잡이를 위한 마우스 반전 기능, 색맹/색약자를 위한 색 팔레트 변경 기능 등이 이에 속한다. 하지만 이것도 알아야 하는게, 대부분의 사람은 가장 쉬운 길로 가고, 옵션 설정을 전혀 변경하지 않는다. 파워 유저만이 이런 고급 설정들을 가지고 놀 것이다.

또한, 플레이어가 플레이하고 싶은 난이도를 결정할 수 있게 하는 것도 포함된다. 어떤 플레이어는 큰 도전을 해보고 싶어하는 한편, 다른 플레이어는 그저 가볍게 돌아보고 싶어한다. 일정량의 게임 플레이를 해야만 열리는 특수 스테이지(개어려움)에 플레이어가 접근할 수 있는 것도 고려해볼만 하다.

> 개인적으로 나는 게임에 난이도 조절을 넣는 것은 완전한 메카닉 변화로 인한 색다른 경험을 줄 수 있지 않는 한은 없는 것이 맞다고 생각한다. 유저가 자기한테 어떤 난이도가 맞을지 어떻게 알겠는가?
{: .prompt-info }

마지막으로 80/20 규칙으로 알려진 파레토 원칙(Pareto Principle)이 있는데, 기본적으로 시스템 변수의 20%가 결과의 80%를 차지한다는 것으로 예를 들어 제품 기능의 20%가 제품 사용의 80%를 담당한다. 따라서 대부분의 사람들은 게임 기능 중 약 20%만 사용할 것이다. 그렇기 때문에 가능한 디폴트 UI를 단순하게 유지하고, 게임 진행에 꼭 필요한 위젯만 필요한 순간에 표시하고, 파워 유저가 커스터마이징이 가능하도록 하라.

## 몰입도engage ability

게임이 너무 쉽지도, 너무 어렵지도 않은 도전을 통해 자신만의 몰입 존flow zone 으로 들어가게 하여 계속 빠져있게 하는 것이 목적이다.

### 동기 - 내재적 동기
`유능성, 자율성, 관계`

내재적 동기는 다른 것을 얻기 위한 수단이 아닌, 활동 그 자체를 위한 활동을 추구할 때 일어난다. 이러한 관점에 기반한 게임은 유능성, 자율성 및 참여할 관련성에 대한 기본 심리적 욕구 충족을 목표로 해야 한다.

### 유능성

유능성은 능숙해지고 명확한 목표를 향해 나아가는 느낌을 의미한다.

이를 충족하기 위해 가장 중요한 방법 중 하나는 플레이어가 능숙한 느낌과 통제력, 그리고 발전하고 숙달된 느낌을 갖게 하는 것이다. 그래서 게임의 중기 및 장기 목표를 확실하게 표현하면서 단기 목표가 무엇인지 나타내는 것이 중요하다. "의미있는" 목표를 "분명하게" 표현하라. 플레이어는 어느 순간에 어떤 목표가 더 중요한지 확실히 알지 못하고, 이는 주관적이기 때문에 명확하게 할 필요가 있다. 많은 동기에 관한 문제는 목표가 플레이어에게 의미/가치가 없기 때문이 아니라 표현이 명확하지 않기 때문이다. 예를 들어 무기나 스킬이 명확하게 어떤 기능을 하는지 간단한 영상 등으로 보여주면 좋다.

유능성을 평가하는 방법은 플레이어가 단기, 중기, 장기의 목표 중 얼마를 식별할 수 있는지, 특정 보상의 획득을 기대하며 그것이 자능성을 어떻게 증가시킬 지 아는지를 알아보는 것이다. 그렇지 않다면 목표가 없거나(게임 디자인 문제), 있지만 식별되지 않거나(사용성: 명확성 문제), 식별되지만 명확하게 이해되지 않거나(사용성: 기능을 따르는 형태 문제), 그것도 아니면 플레이어 관점으로 별로 의미가 없는 목표인 인게이지 어빌리티(몰입도) 의 문제이다.

> 그러니까 플레이어의 진행과 특히 어떤 목표가 완성에 가까운지 명확한 피드백을 주어라. 진행 상황과 남은 목표의 명확한 정보가 유능성에서 결정적인 요소이다. 정리하면, 핵심 요소는 플레이어가 게임에서 자신의 목표에 대한 목적 의식을 느끼게 하고, 진행 상황에 대한 명확한 피드백을 주면  성취감을 느낄 수 있다. 그리고 마지막으로 플레이어가 게임에서 능숙해지는 방법을 이해하는가를 확인하라. 게임 룰을 명확하게 이해하지 못해서 죽거나 목적에 실패하는 플레이어는 숙달된다는 느낌을 전혀 받지 못한다.
{: .prompt-info }

### 자율성

자율성은 의미 있는 선택과 자기표현을 위한 장소가 주어지는 느낌과 관련된다.

이를 충족하기 위해 보통은 의미 있는 결정을 할 수 있고, 자유 의지를 갖지만 게임 시스템 역시 명확하게 만들어 자신감에 차 목적 의식을 경험할 수 있게 하는 것이 포함된다. 플레이어가 할 수 있는 가장 강력한 의미 있는 선택 중 하나는 창의력을 표현하는 것이다. 게임에서 플레이어의 선택은 의미가 있어야 하며, 의사 결정 중에 그 목적을 이해할 수 있어야 하고, 전체적으로 미치는 영향을 인식할 수 있어야 한다. 또한, 자율성에는 반드시 가이드가 있어야 한다. 완전한 자유라는 명목으로 아무런 지침이 없어 플레이어가 혼란스럽거나 압도되면 자율성도, 유능성도 느끼지 못하기 때문이다.

### 관련성

관련성은 주로 다른 사람들과의 관계를 느낄 필요성을 나타낸다. NPC로도 가능하다.

게임에서 의미있는 사회적 상호작용을 제공한다는 뜻이다. 협력형 게임의 경우 함께 할 라운드와 협력의 정도는 비례한다. 신뢰 관계를 유지할 필요가 없을 때 트롤하거나 이용해먹을 가능성이 높아지기 때문이다. 인간은 자신의 사회적 그룹에 속한 가까운 사람들인 내집단ingroup 을 편애하는 내집단 편향이 있기 때문에, 친구가 하고 있는 미션이나 매치에 바로 쉽게 참여할 수 있도록 하여라. 플레이어가 자신의 상태를 그룹에게 과시할 수 있는(최근 완료한 미션, 얻은 보상, 성과 등)방법을 제공하라. 이는 플레이어의 유능성을 사회적 맥락에서 확정할 수 있게 해준다. 또한, 이는 다른 사람들에게 도발이 될 수도 있다(또래 압박peer pressure). 마지막으로, 플레이어끼리 서로 쉽게 도움을 줄 수 있도록 해라(아이템에 핑을 찍어 팀원이 쉽게 확인할 수 있거나 서로에게 선물을 줄 수 있게 하거나 등).

경쟁 또한 관계에 포함되는데, 패자가 되는 것은 좌절감을 불러오고 게임이 불공정하다고 느끼거나 굴욕감을 느끼게 할 수 있기에 약간 위험하다. 그래서 가능하면 패배를 긍정적으로 묘사하고, 배워서 발전할 기회로 바꿀 방법을 찾아야 한다. 다른 사람들과 비교했을 때 가장 잘한 것이나 개인적 척도에서 얼마나 향상되었는지 강조하는 게 좋다.

협력이나 경쟁이나 악성 유저들을 방지할 수 있도록 애초에 트롤하지 못하도록 막는 것이 좋다. 그리고 트롤의 피해가 된 유저에게 트롤을 차단하거나 신고하는 등의 권한을 주고, 신고 조치 등을 했을 때 내용을 확인했 고 조치가 취해졌다는 피드백을 주어라. 또한, 예의바른 플레이어를 칭찬할 수 있게 하면 좋다.

### 의미

유능성, 자율성, 관계에서 '의미' 라는 개념이 중요한데, 이는 "목적의식, 가치의식, 영향에 대한 의식을 갖는 것" 이다. 플레이어가 해야하거나 배워야하는 모든 일의 배경 근거를 주는 것이 중요하다. '회복약을 먹으면 체력이 회복된다'는 기능적 근거보다는, '체력이 감소했기 때문에 치료해야 하고, 회복약을 사용하면 가능하다' 라는 의미 있는 근거를 말한다. 명확한 사인과 피드백을 이러한 요소와 연결하면 더 좋다.

### 동기 - OCEAN

Big 5 성격 특성으로, 인간이 가지는 성격 특성이며 실제 게임 기획을 할 때 고려해볼만한 가치가 있다.

- 경험에 대한 개방성
: 얼마나 창의적이고 호기심이 많은지. 점수가 낮으면 실용적이고 관습적이지만 점수가 높으면 창의적이고 상상력이 풍부하다.

- 성실성
: 얼마나 효율적이고 조직적인지. 점수가 낮으면 충동적이고 부주의하지만 점수가 높으면 조직적이고 자기주도적이다.

- 외향성
: 얼마나 외향적이고 활동적인지. 점수가 낮으면 내성적이고 조용하지만 점수가 높으면 외향적이고 열정적이다.

- 친화성
: 얼마나 우호적이고 동정심이 많은지. 점수가 낮으면 의심 많고 냉담하지만 점수가 높으면 사람을 믿는 경향이 있고 공감한다.

- 신경증
: 얼마나 예민하고 불안해하는지. 점수가 낮으면 정서적으로 안정되지만, 점수가 높으면 분노와 불안감을 쉽게 느낀다.

### 동기 - 외재적 동기

학습된 욕구, 그리고 보상

외재적 동기는 환경에 의해 형성되는 학습된 욕구에 관한 것으로, 환경을 경험하고 어떤 행동이 긍정적/부정적 결과를 가져오는지 식별하며 환경에 대해 배운다.

과제가 창의적이고 이를 완료하려는 동기가 주로 외재적일 때 창의성은 약화된다. 과잉정당화 효과의 일부로, 내재적 동기로 하던게 외재적 동기가 되면 게임을 하는 이유가 외재적 동기라는 잘못된 귀인을 할 수 있게 된다. 외재적 동기로 게임을 오늘 하고싶진 않은데 일일 보상을 받기 위해 게임을 들어갈 수도 있다. 내재적 동기로 시작했는데 활동의 보상이 외재적으로 받아들여지고 있다가, 그 보상이 중단되면 처음부터 외재적 동기를 가지던 사람에 비해 동기가 더 떨어진다. 그래서 그 일일 보상이 연속 개근이 필요한데 하루를 놓쳐서 못 받게 되면 보상을 빼앗겼다고 생각하게 되어 내재적 동기에 영향을 줄 수 있다.

이 글의 필자는 외재적 동기는 내재적 동기에 나쁜 영향을 미치지 않는다 하며, 경우에 따라 성과와 창의성을 실제로 향상시킬 수 있다 한다. 그렇기 위해서 외재적 보상이 플레이어의 목표에 있어 방편으로써 중요하고 가치 있는 것이어야 한다. 과제의 보상은 플레이어의 관점에서 의미 있는지 확인하고, 보상으로 무엇을 할 수 있는지 이해해야 한다. 핵심 보상을 받는 것은 다음 목표의 시작점으로 받아들여져야 한다. 과제의 난이도에 따라 보상도 변경되어야 한다. 또한, 칭찬과 같은 작은 보상의 경우 플레이어의 기술에 대한 정보를 주는 것이 좋다. "잘했어!" 보다는 "더블 킬"이 더 유익하다.

### 정서

도널드 노먼 - "디자인의 정서적인 면은 제품의 실용적인 요소보다 성공에 더 중요할 수 있다."

비디오 게임의 정서적인 면은 시각적 미학, 음악, 내러티브narrative를 통해 자주 다뤄진다. 이는 '게임 필' 이라고 불리며 이는 '숙달과 미숙에 대한 느낌, 그리고 가상 물체와 상호작용하는 촉각' 을 포함한다. 조작감 또한 많이 중요하다. 스티브 스윙크는 훌륭한 느낌이 드는 게임은 플레이어에게 컨트롤의 미적 감각, 스킬(기술)을 배우는 즐거움, 감각의 확장, 정체성의 확장, 게임과 독특한 물리적 현실을 상호작용 하는 5가지 타입의 경험을 전달하는 것이라 한다.

- 3C - Control, Camera, Character
: "조작감을 잘좀 챙겨라"

- 현장감
: 물리적, 정서적, 서술적 현장감으로 느끼며 물리적은 실제로 플레이어가 가상 공간에 있음을 느낄 때 일어나고 정서적 현장감은 가상에서 일어나는 일이 플레이어에게 일어나듯이 느껴지고, 정서적 무게로 다가오는 느낌이다. 서술적 현장감은 플레이어의 선택과 액션이 게임의 사건에 실제 결말을 가져올 때처럼 플레이어가 이야기에 스며들어 캐릭터가 믿을 만하고 우호적이라 여길 때 일어난다.

- 물리적 현실과 살아있는 가상 세계
: 물리적으로 현실적이게 만들어라. 총알이 금속 표면에 맞은 것과 아무것도 맞지 않은 것의 소리가 같으면 안된다.

### 게임플로Game Flow

칙센트미하이의 몰입의 경험의 8요소
- 스킬이 필요한 도전적인 활동: 완벽해질 기회가 있음을 알고 있는 스킬
- 행위와 의식의 합체: 사람의 주의는 활동에 의해 완전히 흡수된다
- 명확한 목표: 목표가 달성하기 어렵고 의미 있는 경우
- 직접적인 피드백: 피드백은 즉각적이고 목표와 관련이 있다
- 직면한 과제에 집중: 우리는 삶의 즐겁지 않은 측면과 과제에 무관한 정보를 잊는다
- 통제감: 과제를 숙달하기에 충분한 스킬 개발
- 자의식의 상실: 자기 관찰의 여지가 없다
- 시간의 변형: 시간 가는 것을 잊는다

게임플로 모델은 집중, 도전, 플레이어 스킬, 컨트롤, 명확한 목표, 피드백, 몰입, 소셜 이라는 8가지 핵심 요소로 구성되어 있다.

또한, 어려운 정도(난이도 곡선)과 압박의 양(페이스)로 되어 있고, 레벨 디자인을 통해 실제로 해보는 분산 학습(학습 곡선) 이 필요하다. 또한, 플레이어가 이전에 느낀 압박(예: 어려운 기믹을 배움)에 따라 피로도가 있을 수 있기 때문에 이를 고려하여 난이도를 설계해야 한다.

### 어포던스affordance

어떤 행동을 유도하는 것으로 행동유도성이라고도 한다. 물체의 어포던스를 인지하면 사람들이 해당 물체를 사용할 수 있는 방법을 결정하게 되는데, 예를 들어 컵의 손잡이는 잡는 행동을 유도한다. 여기서 하트슨은 이 어포던스를 4가지로 분류하였다.

- 물리적 어포던스 : 무언가를 하는데 도움이 되는 물리적 특성
: 페트병은 병따개가 필요 없고 맨손으로도 열 수 있다. 물리적 행위를 용이하게 하는 방식이다. 예를 들어, 버튼의 크기를 충분히 크게 할 수 있다.

- 인지적 어포던스
: 사용자가 배우고, 이해하고, 무언가를 알고, 그것으로 무엇을 할 수 있는지 결정하는데 도움을 준다. 버튼 레이블Label이나 기능 전달에 사용되는 메타포Metaphor 등은 모두 인지 어포던스이므로, 기능에 따른 형태는 인지 어포던스에 관한 것이다.

- 감각적 어포던스 : 사용자가 무언가를 감지하는 데 도움이 되는 기능
: 무언가 보고, 듣고, 느끼는 데 돕는 것으로 텍스트의 가독성을 좋게 하는 것, 중요한 아이콘을 눈에 띄게 하는 것 등 명확한 사용성의 주요 구조부는 감각적 어포던스에 관한 것이다.

- 기능적 어포던스: 사용자가 특정 과제를 수행하는 데 도움이 되는 디자인 기능
: 인벤토리에서 아이템을 정렬하는 기능, 아이템 비교 기능, 필터링, 고정하기 등이 이에 속한다.

거짓 어포던스는 없어야 하며(맵의 어떤 영역에 접근할 수 없다면 접근할 수 있는 것 처럼 보이게 하면 안된다) 개발 초반에 설계하는 게 좋다.