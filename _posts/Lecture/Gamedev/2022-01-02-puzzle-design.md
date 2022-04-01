---
title: '퍼즐 디자인'
date: 2022-01-02 12:00:00 +0900
categories: [Lecture, Game Dev]
tags: [Game Design]
---

## 퍼즐 디자인을 하는법

1. 목적이 없는 무작위 규칙으로 시작한다
- 좋은 퍼즐에서, 행위에는 예상 가능한 결과를 가지고 있다
- 좋은 퍼즐에서, 규칙은 주로 별로 복잡하지 않다

2. 특정 목적들로 실험을 한다. 반복적으로 규칙을 강화한다
- 게임 시스템에서 떼기 힘든 요소가 있다면, 그게 바로 목적이다(달성하기 힘든것)
- 좋은 퍼즐에서, 정답이 되는 행동의 순서를 찾는 것이 도전적이다

3. 플레이어의 측면으로 학습한다. 점진적으로 어려워지는 퍼즐을 만든다
- 좋은 퍼즐은, 해결하기 위한 모든 정보를 포함한다(숨겨졌어도 찾아낼 수 있어야한다)
- 좋은 퍼즐은, 필요한 만큼만 복잡하며, 필요한 만큼만 거대하다
- 퍼즐을 디자인 하는 것 또한 퍼즐이다
- 좋은 퍼즐은, 플레이어의 예상을 가지고 논다
- 좋은 퍼즐은, 게임 시스템에 대한 새로운 것을 가르친다

4. 예전 규칙을 완벽히 탐구했다면, 규칙을 확장하라

5. 재정렬하고, 다듬어라. 완벽한 퍼즐이라고 확신할 수 없다

## 좋은 퍼즐을 만드는 법 - GMT

### 메카닉Mechanic

모든 퍼즐 게임은 메카닉으로 시작한다. 그 게임이 어떻게 돌아갈지 정하는 탄탄한 룰을 의미한다. 그래서 기본적으로 메카닉이 얼마나 "영리하냐" 에 따라서 전체 퍼즐의 수와 난이도를 정한다.

게임에는 또한 목표(Goal)가 존재하는데, 플레이어가 달성하려고 하는 것이 무엇인지 명확해야 한다.

### 캐치Catch

`문제점/애로점`

좋은 퍼즐은 [캐치] 를 중심으로 만들어진다. 두 무엇이 언뜻 보기에 서로 직접적인 갈등관계에 있어보이는 논리적 모순을 의미한다. 예제를 들자면, 방에 [발판], [상자], [문] 이 있을때 발판 을 밟으면 문이 열린다. 그럼 발판을 밟고 문으로 나가면 될 것 같지만 발판에서 발을 떼면 문이 닫힌다. 그러니까 "한 가지를 하면 다른 한가지가 불가능하게 되는" 것이다. 그래서 당신은 상자를 발판 위에 올려놓아야 한다.

### 발견Revealation

정답을 위한 행동은 매우 간단하고, 수고가 들지 않지만 동시에 매우 어렵기도 하다. 틀 바깥에서 생각하도록 요구하고 게임이 동작하는 방식에 대해 다시 생각하게 하고, 게임의 컨셉을 측면에서 바라보도록 하기 때문이다. 또한 이것은 게임의 룰이 가능하게 하는 뻔하지 않지만 완전히 논리적인 결과를 드러내며 이후에 사용될 수 있는 도구이 된다. 이는 또한 이후에 더 크고 복잡한 퍼즐의 일부로 사용될 수도 있다.

그래서, 퍼즐을 푸는 것은 발견을 하는 것과 같다. 룰에 대한 더 깊은 통찰을 얻는 것이다.

### 추정Assumption

플레이어는 퍼즐을 관찰하고 추정한다. 주로 가장 간단하게 생각해낼 수 있는 해법을 먼저 생각해낼 것이다. 플레이어가 잘못된 추정을 하도록 퍼즐을 디자인하면 이점들이 있다.
1. 플레이어가 해법을 안다고 생각하게 유도함으로써 플레이어가 새 퍼즐을 시작할 때 압도당하지 않도록 한다
2. 잘못된 추정을 실행하는 도중, 사실 퍼즐이 어떻게 동작하는지 깨닫고 이 수수께끼가 어떻게 만들어졌는지에 대한 정신적 모델을 만들게 된다.
3. 이는 플레이어가 처음에는 퍼즐을 못 풀 것을 거의 보장한다.
4. 플레이어가 퍼즐의 핵심에 집중할 수 있도록 해준다. 예를 들어 아까의 발판 문 퍼즐에서, 퍼즐은 "문으로 어떻게 나가지" 가 아니라, "어떻게 문을 열어두지" 이다.

### 제시Presentation

지금까지의 모든 것들은 적절하게 제시하지 않으면 퍼즐이 모두 무너질 수 있다. 이는 퍼즐을 풀기 위해 무엇이 가능한 지 보여주는 것을 의미한다. 예를 들어, 아까의 발판 문 퍼즐에서 발판과 상자가 2개라고 했을 때, 상자를 아무데나 던져놓을 수도 있지만, 상자 하나를 발판 위에 올려놓으면 "상자로 발판을 누를 수 있다" 를 제시할 수 있다. 이런 메카닉의 제시 외에도 복잡한 퍼즐의 경우는 퍼즐의 해결방법에 대한 제시 또한 가능하다.

좋은 퍼즐은 꽤 미니멀리스트하여, 관련없는 요소는 거의 없다. 최고의 퍼즐이란 단지 몇개의 움직일 수 있는 요소만 있어서 플레이어가 가장 간단하게 퍼즐을 이해할 수 있도록 하는 것이다. 퍼즐의 제시 방법은 또한 명확한 피드백을 주어야 한다. 어떤 행위가 어떤 결과를 일으키는지를 추정할 수 있게 해야하기 때문이다.

### 커브Curve

그 어떤 퍼즐도 홀로 플레이어에게 주어지지 않는다. 이전에 있었던 퍼즐 위에 만들어지도록 구성된다. 퍼즐은 진행하며 배운 모든 요소를 사용하고, 퍼즐은 하나씩 점점 난이도를 높여가야 하기 때문이다.

Square Enix Montreal에서 정의한 퍼즐의 난이도의 4가지 기준이 있다.
1. 해답의 갯수가 많을수록 퍼즐이 쉬워진다
2. 해결까지 필요한 단계 수가 높을수록 더 어렵지만, 너무 높으면 지루하다
3. 매 순간에 플레이어에게 주어지는 선택지의 개수
4. 플레이어가 어떤 메카닉들에 미리 친숙해져 있어야 하는지

### 마무리

좋은 퍼즐은 게임의 룰에 의해 파생되며, 첫 눈에 불가능해 보이는 캐치가 있다. 개발자는 플레이어의 추정을 예측하여 캐치에 다다르도록 유도할 수 있다. 캐치를 극복하고 갈등을 해소하려면, 최고의 퍼즐은 플레이어에게 수평적(측면적) 사고Lateral Thinking와 게임 룰에 숨겨진 지식을 밝혀내기를 요구한다. 모든 퍼즐이 이렇지 않지만, 잘 만들어진 퍼즐에는 이런 요소들을 발견할 수 있다. 잘 만들어지지 못한다면 갈등이 너무 쉽게 풀리거나, 추정 단계가 없어서 수직적 사고Vertical Thinking로 해법으로 바로 다가가거나, 충분한 제시가 없어서 그저 귀찮게 느껴지게 되어 있을 수 있다.