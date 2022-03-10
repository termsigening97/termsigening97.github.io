---
title: '자료구조와 알고리즘'
date: 2022-01-27 12:00:00 +0900
categories: [Lecture, Basic]
tags: [Essence]
---

## Introduction to Data Structure

코딩을 조금 하고 나면 프로그래밍은 데이터를 주로 다룬다는 것을 알 수 있습니다. 컴퓨터 프로그램은 데이터를 입력받고, 조작하고, 반환하는 게 끝입니다. "Hello, World" 라는 문자열과 숫자들이 바로 데이터이죠. 자료구조는 이런 데이터들을 조직하는 방법이며, 코드의 실행 속도에 영향을 미칩니다. 데이터를 어떻게 조직하는지에 따라 프로그램이 수백 수천배보다도 더 빠르거나 느리게 실행될 수 있기 때문이죠.

## 자료구조의 연산

대부분의 자료구조는 코드와 자료구조가 상호작용하기 위해 네 가지 기본 방법을 사용하는데, 이를 연산 이라고 부릅니다.

* 읽기 : 자료 구조 내 특정 위치의 데이터를 가져오는 것입니다.

* 검색 : 자료 구조 내에서 특정 값을 찾는 것입니다.

* 삽입 : 자료 구조에 새로운 값을 추가하는 것입니다.

* 삭제 : 자료 구조에서 값을 제거하는 것입니다.

여기서 이 연산들이 얼마나 "빠른지" 측정하기 위해서는 시간 관점에서 연산이 빠른지가 아니라 얼마나 많은 단계가 필요한지를 보아야 합니다. 그 이유는, 어떤 연산이 정확히 몇 초가 걸린다고 할 수 없기 때문입니다. 같은 연산도 성능 좋은 컴퓨터에서는 더 빠르고, 반대의 경우 더 느릴 수 있기 때문이죠. 예를들어 연산 A에 5단계가 필요하고 연산 B에 500단계가 필요하면 모든 하드웨어에서 연산 A가 연산 B보다 항상 빠를 것을 알 수 있습니다.

## 배열Array

배열은 단순히 데이터 원소들의 리스트입니다. 예를들어 다음과 같은 배열은 요일의 이름을 나타내죠.

`weeks = ["mon", "tue", "wed", "thr", "fri", "sat", "sun"]`

배열의 인덱스(번호)는 특정 데이터가 배열의 어디에 있는지 알려주는 숫자입니다. 대부분의 프로그래밍 언어에서 인덱스는 0부터 시작합니다. "mon"은 인덱스 0에 위치하고 "sun"은 인덱스 6에 위치합니다.

이제 이 배열에 대한 **연산** 들의 단계와 방법들을 알아보도록 하겠습니다.

### 배열의 읽기

배열에서의 읽기란 특정 인덱스에 어떤 값이 들어있는 지 찾아보는 것입니다. 읽기의 단계는 딱 한 단계인데, 컴퓨터는 배열 내의 특정 인덱스에 한번에 접근해서 볼 수 있기 때문입니다.

이게 왜 가능한지 알기 위해서는 메모리 구조에 대해서 알아야 하는데, 메모리는 일정 간격으로 나뉜 셀들로 이루어져 있는 공간이라고 생각할 수 있습니다. 프로그램에서 배열을 선언하면 연속된 빈 셀들의 집합을 할당합니다. 위쪽의 `weeks` 배열을 예로 들면, 7개의 값이 들어가기 위한 7개의 연속된 빈 셀들이 있는 위치를 찾아 배열로 지정합니다.

그리고, 컴퓨터 메모리 내의 각 셀에는 숫자로 이루어진 주소가 존재합니다. 편의를 위해 간단하게 설명하자면, 첫번째 셀의 주소가 0일때, 그 뒤의 주소는 1, 2, 3, 4... 이렇게 1씩 증가합니다. 그래서 만약에 배열의 시작 주소를 알 수 있으면, 시작한 위치부터 3칸 뒤의 주소가 바로 네 번째 데이터의 값(`"thr"`)이기 때문에, 한 번의 단계로 끝나는 것이죠. 이게 바로 인덱스가 0부터 시작하는 이유입니다. 참, 컴퓨터는 모든 메모리 주소에 한 번에 갈 수 있습니다.

### 배열의 검색

배열에서 특정 값을 찾기 위해서는, 인덱스 0부터 시작해서 차례로 읽기 연산을 하고, 찾던 값이 아니면 다음 인덱스로 넘어가 찾을 때까지 이를 반복합니다. 예를 들어 `weeks` 배열에서 `"wed"` 를 찾기 위해서는 0번째 -> 1번째 -> 2번째 만큼 움직여야지만 알 수 있으므로 총 3단계가 걸렸습니다. 우리는 눈으로 보고 바로 알 수 있지만 컴퓨터에는 눈이 없기 때문에 이렇게 할 수밖에 없죠.

이와 같이 한번에 하나씩 확인하는 검색 연산을 **선형 검색** 이라고 합니다. 그럼 이 때 최대 단계 수는 어떻게 될까요? 간단하게 배열의 길이가 N이라면 N개의 단계가 필요하다고 할 수 있습니다.

### 배열의 삽입

배열에서 삽입을 할 때, 맨 마지막에 삽입한다면 그냥 배열의 맨 뒤에 추가하면 되기 때문에 한 단계만 필요하지만, 만약 중간 어딘가에 삽입한다면, 데이터를 삽입하고 원래 있던 데이터부터 끝에 있는 데이터까지는 전부 한 칸씩 뒤로 이동시켜 줘야 하기 때문에 많은 단계가 필요합니다. 각 데이터가 사람들이 서있는 줄이라고 할 때, 줄 중간에 들어가려면 사람들이 전부 뒤로 한칸씩 비켜줘야 하는 것을 생각할 수 있습니다.

이 경우에도 최대 단계, 즉 최악의 경우에 N개의 단계가 필요합니다. 맨 앞에 데이터를 삽입하려면 모든 데이터가 뒤로 한칸씩 움직여야 하기 때문이죠.

### 배열의 삭제

삭제 또한 삽입과 똑같습니다. 중간에 데이터를 삭제하면, 삭제한 곳부터 뒤에있는 모든 데이터는 모두 앞으로 한 칸씩 이동시켜 줘야 하기 때문이죠.

## Introduction to Algorithm

알고리즘이란, 단순히 어떤 문제를 해결하는 절차입니다. 예를 들어 유튜브를 보는 알고리즘은 다음과 같습니다.

1. 웹브라우저를 연다
2. youtube.com에 접속한다
3. 원하는 영상을 검색한다
4. 영상을 클릭해서 시청한다

컴퓨팅에서의 알고리즘도 이와 같이 특정 연산의 해결을 위핸 절차입니다. 자료구조에서 읽기, 검색, 삽입, 삭제를 위한 절차도 알고리즘이죠. 이 알고리즘을 어떻게 작성하냐에 따라 코드가 매우 빠르게 실행되기도, 느리게 실행되기도 합니다. 그럼 알고리즘의 예제를 살펴보도록 합시다.

## 정렬된 배열

배열인데, 숫자가 순서대로 정렬되어있어야 하는 자료구조를 생각해봅시다. 그러면 삽입 연산을 할 때마다 검색 연산이 필요하게 됩니다. 예를들어 아래와 같은 값들이 들어있는 배열이라 할때
`[10, 20, 40, 50]`
여기에 30을 삽입하기 위해서는, 우선 30보다 큰 값`(40)`을 검색하고 해당 위치에 삽입하게 됩니다. 그러면 40, 50은 전부 오른쪽으로 한칸씩 이동해야 해고 생긴 자리에 30을 넣을 수 있게 되는 것이죠.
`[10, 20, 30, 40, 50]`

여기까지만 보면 쓸데없이 정렬한다고 생각될 수 있습니다. 하지만 정렬된 배열의 진가는 **탐색** 연산에서 드러납니다. 

## 이진 검색

*배열의 검색* 에서 사용된 방법은 선형 검색이었습니다. 첫번째 원소부터 끝번째 원소까지 전부 차례대로 확인하는 것이죠. 하지만 만약 배열이 정렬되어 있다면, **이진 검색**을 사용할 수 있습니다.

방법은 간단합니다. 예를들어 `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` 가 배열에 있다고 할 때, 9를 찾는다고 합시다. 그럼 우선 중간 인덱스`(0+9/2 = 4)` 에 있는 값`(5)` 을 봅시다. 9는 5보다 크니까 이제 **인덱스 4부터 인덱스 9** 의 중간 인덱스`(4+9/2 = 6)`의 값`(7)`을 봅시다. 9는 7보다 크니까 이제 **인덱스 7부터 인덱스 9** 의 중간 인덱스`(7+9/2 = 8)`의 값`(9)`를 봅시다. 찾았네요!

선형 검색으로 처리했다면 9단계가 걸렸겠지만, 이진 검색으로는 3단계만 필요했습니다. 이는 숫자가 커지면 더 극적으로 차이가 벌어지는데, 원소가 10,000개인 배열에서 선형 검색은 최대 10,000단계가 필요하지만, 이진 검색은 13단계면 충분합니다. 왜냐면 이진 검색은 **데이터를 두 배로 늘릴 때마다 단계가 최대 하나씩만** 추가되기 때문인데, 이것을 두고 우리는 로그 형태의 단계가 들어간다고 합니다.

만약 코딩 문법을 알고 있다면, C언어로 표현된 이진 탐색의 코드는 다음과 같습니다.
```cpp
int binary_search(int array[], int array_size, int value) {
  int lower_bound = 0;
  int upper_bound = array_size - 1;

  while (lower_bound <= upper_bound) {
    int mid = (lower_bound + upper_bound) / 2;
    if (value < array[mid])
      upper_bound = mid - 1;
    else if (value > array[mid])
      lower_bound = mid + 1;
    else
      return mid; // 결과 인덱스를 반환
  }

  // while문 내에서 return되지 않았다면 값이 없는것이기 때문에 없다는 표시로 -1을 반환
  return -1; 
}
```
물론 그렇다고 우리가 정렬된 배열만 쓸 필요는 없습니다. 검색이 많이 필요한 상황이라면 정렬된 배열이 좋겠지만, 검색을 쓰지 않는 상황이라면 굳이 삽입 때 시간을 소모하지 않는 일반 배열을 쓰는 게 더 효율적이기 때문이죠. 그래서 자료구조들은 상황에 맞게 적재적소에 사용된다고 생각하시면 됩니다.

## 빅-오 표기법

우리가 어떤 알고리즘(자료구조의 연산 등) 의 효율성을 나타낼 때, 얘는 2000단계가 필요해요! 라고 말하지 않습니다. 전문적이지 않을 뿐더러, 상황에 따라 필요한 단계가 다르기 때문에 빅-오 표기법을 사용해서 "배열에 N개의 원소가 있을 때 선형 검색에 N단계가 필요합니다" 라는것을 "이 알고리즘는 ***O(N)***" 이다. 와 같이 나타냅니다. 시간복잡도가 O(N) 이라고 하기도 하죠.

어 그런데, 만약 내가 `[1, 2, 3, 4, 5]` 가 들어있는 배열에서 1을 검색할 때는 한 단계만 필요한데 N단계가 아니잖아요! 라고 할 수 있습니다. 네, 빅-오 표기법은 **최악의 상황** 을 가정해서 표기하게 됩니다. 최악을 대비함과 동시에 알고리즘 선택에 중요한 영향을 미치기 때문이죠. 물론, 평균적인 성능을 나타내기도 하지만 빅-오 표기를 어떻게 하는지와 그 종류에 대해서 알아보록 합시다.

### 상수 시간

***O(1)*** 이라고 표기하며, 데이터가 얼마나 많든 상관없이 고정적인 단계를 가질 경우를 나타냅니다. 예를 들어, 배열에서 읽기는 O(1)입니다. 언제나 한 단계만 필요하기 때문이죠. 하지만 만약 10,000 단계가 필요했다고 해도 O(1)으로 표기합니다.

### 선형 시간

***O(N)*** 이라고 표기하며, 데이터의 개수만큼 단계가 늘어남을 나타냅니다. 그래프로 그리면 완벽한 대각선(일차방정식)이 나오기 때문에 "선형 시간" 이라고 부릅니다.

### 로그 시간

***O(log N)*** 이라고 표현합니다. 여기서 log의 **밑**은 2입니다. 이게 무슨 뜻이냐면, "2를 몇제곱해야 N이 되는가?" 입니다. 예를들어 log8 = 3 입니다. 2의 3승이 8이기 때문이죠. 하지만 수학문제가 아니기 때문에 대략 "2로 몇번 나눠야 1이 되는가?" 라고 생각하셔도 좋습니다.

이 외에도 지수시간`O(N^2)` (N의 제곱) 등이 존재하지만, 보시면 아실 수 있습니다.

### 빅-오의 특징

여기서 빅-오의 특징으로, 빅-오에서는 상수를 무시해줍니다. 예를 들어 어떤 알고리즘의 시간복잡도가 `O(N^2)` 이고 여기에 100단계정도가 더 추가되더라도 그대로 `O(N^2)` 입니다. N의 값이 한없이 커짐에 따라 100은 의미가 없어지기 때문이죠.

같은 이유로, 다항 시간`ex) N^3 + N^2 + N` 인 알고리즘의 경우 **가장 높은 차수** 만이 빅-오에 표시됩니다. 그래서 위같은 알고리즘의 빅-오 표기는 `O(N^3)` 이 됩니다. 이는 상수와 같은 이유로 N의 값이 한없이 커지면 N^3의 변화율을 N^2나 N이 따라오지 못하기 때문이죠. 이해가 잘 안되신다면, 정렬 알고리즘에 대해 공부해보면서 익혀봅시다.

## O(N^2)인 정렬 알고리즘 

**정렬** 은 프로그래밍에 있어서 매우 자주 사용되는 알고리즘이며, 그로인해 다양한 알고리즘들이 존재합니다. 여기서는 간단한 기초 알고리즘인 "버블 정렬" 과 "삽입 정렬" 에 대해서만 알려드리겠습니다.

### 버블 정렬

배열의 처음부터 배열의 길이 - 1 까지 연속된 두 원소를 비교해서, 만약에 오른쪽의 수가 더 작으면 두 수의 위치를 교환합니다. 예를들어 `[ 3, 2, 1 ]` 을 정렬한다면 인덱스 0과 1의 원소인 `3` 과 `2` 를 비교합니다. `2`가 더 작으니 위치를 교환합니다. `[ 2, 3, 1 ]` 이제 인덱스 1과 2를 비교하면 `3` 과 `1` 중 1이 더 작으니 위치를 교환합니다. `[ 2, 1, 3 ]`. 이 작업을 **배열의 길이 - 1** 만큼 반복하면 됩니다. 왜냐면 최악의 경우 맨 오른쪽의 값이 맨 왼쪽까지 오려면 배열의 길이 - 1 만큼 이동해야 하기 때문이죠.

```cpp
int arr[10] = { 9, 2, 3, 8, 4, 1, 7, 10, 6, 5 };

for (int i = 0; i < 9; i++) {
  for (int j = 0; j < 9; j++) {
    if (arr[j] > arr[j+1]) {
      int tmp = arr[j];
      arr[j] = arr[j+1];
      arr[j+1] = tmp;
    }
  }
}

for (int i = 0; i < 10; i++)
  printf("%d ", arr[i]);
```

버블 정렬은 (N-1)^2 + N 의 단계가 필요합니다. 빅-오로 표기하면 ***O(N^2)*** 가 됩니다. -1은 N이 한없이 커질수록 값의 차이가 미미해지기 때문에, 빅-오에서 상수는 전부 무시해줍니다. 같은 이유로,  N^2 + N 에서도 N=100 만 되어도 10000 + 100 이라는 100:1 이라는 큰 차이이기 때문에 빅-오에서는 가장 높은 차수만 사용해줍니다.

**[?]** 혹시 "값의 교환은 왜 단계로 쳐주지 않나요?" 라는 의문점이 들었다면, 값의 교환 또한 단계가 있는 것은 맞지만 그것을 포함하더라도 많아야 `2 * N^2` 정도기 때문에 상수는 무시된 것입니다. 빅-오는 코드의 **반복문의 반복횟수** 로 계산해주면 됩니다.

**[?]** 만약 버블정렬에서 한번 반복할 때마다 끝에서부터 값이 하나씩 정렬이 완료된다는 사실을 눈치채셨다면, 맞습니다. 하지만 O(N^2) 를 좀 더 효과적으로 설명해드리기 위해 여기서는 일부러 생략하였습니다.

### 선택 정렬

선택 정렬은 사실 버블 정렬보다 간단합니다. 일단 처음 인덱스부터 시작합니다. 그 다음 인덱스부터 배열의 끝까지 검색하면서 최솟값을 찾습니다. 검색이 끝나면, 처음 인덱스와 찾은 최솟값의 위치를 교환해줍니다. 예를 들어, 배열이 `[ 5, 2, 1, 4, 3 ]` 가 있었다면, 처음부터 끝까지 반복하면 최솟값의 인덱스는 **2**이라고 알 수 있습니다. 그럼 인덱스 0과 교환해주면 배열은 다음과 같이 됩니다. `[ 1, 2, 5, 4, 3 ]` 이 이후에는 인덱스 1부터 끝까지, 그 다음에는 인덱스 2부터 끝까지... 그러면 검색을 할 때마다 보아야 하는 원소의 개수가 하나씩 감소하는 것을 알 수 있습니다.

```cpp
int arr[10] = { 9, 2, 3, 8, 4, 1, 7, 10, 6, 5 };

for (int i = 0; i < 10; i++) {
  int minidx = i;

  for (int j = i + 1; j < 10; j++)
    if (arr[minidx] > arr[j])
      minidx = j;

  int tmp = arr[minidx];
  arr[minidx] = arr[i];
  arr[i] = tmp;
}

for (int i = 0; i < 10; i++)
  printf("%d ", arr[i]);
```

그래서 총 `O(N^2 / 2)` 가 되어야 할 것 같은데... 상수를 무시해주기 때문에 이 또한 `O(N^2)` 가 됩니다. 여기서 더 알아야 하는 점은, 이와 같은 이유 때문에 같은 시간복잡도의 알고리즘이라도 데이터의 상황에 따라, 알고리즘의 효율은 다를 수 있다는 점입니다. 만약 `O(N^2)` 과 `O(N)` 알고리즘 중에서 선택하라면 당연히 O(N)을 선택하는 것이 좋지만, 같은 `O(N)` 이라면 효율성 분석을 좀 더 자세히 하는 것이 좋습니다.

### 삽입 정렬

인덱스 1부터 시작하는데, 자신의 값을 임시변수에 저장해놓고, 0번째 인덱스까지 비교하며 만약 임시변수의 값보다 크다면 오른쪽으로 이동해줍니다. 그러다 만약 임시 변수의 값보다 작은 값을 만나면 그 다음 인덱스에서 멈춰줍니다. 글로 읽기에는 복잡할 수 있으니 한번 예시를 보여드리죠.

`[3, 2, 1, 5, 4]`
가 있을 때, 임시변수에 인덱스 1의 값을 저장합니다. `tmp = 2`
그 후, 인덱스 0의 값을 보았더니 임시변수의 2보다 크기 때문에 오른쪽으로 이동해줍니다
`[3, 3, 1, 5, 4]`
어짜피 덮어씌워질테니 오른쪽으로 대입만 해도 괜찮습니다
인덱스의 마지막(0) 에 도달했기 때문에 임시변수의 값을 넣습니다

`[2, 3, 1, 5, 4]`
임시변수에 인덱스 2의 값을 저장합니다. `tmp = 1`
그 후, 비교를 하니 임시변수의 1보다 크기 때문에 오른쪽으로 이동해줍니다
`[2, 3, 3, 5, 4]`
그 후, 인덱스 0과 비교를 하니 1보다 크기 때문에 오른쪽으로 이동해줍니다
`[2, 2, 3, 5, 4]`
인덱스의 마지막(0) 에 도달했기 때문에 임시변수의 값을 넣습니다
`[1, 2, 3, 5, 4]`

이와 같은 과정을 끝까지 반복해주면 정렬이 완료됩니다.

```cpp
int arr[10] = { 9, 2, 3, 8, 4, 1, 7, 10, 6, 5 };

for (int i = 1, pos; i < 10; i++) {
  int tmp = arr[i];

  for (pos = i; pos > 0 && arr[pos - 1] > tmp; pos--)
    arr[pos] = arr[pos - 1];

  arr[pos] = tmp;
}
```
이제 지금까지와는 다르게 코드 하나하나의 단계를 자세히 살펴봅시다. 삽입 정렬은 최악의 경우에 N^2 / 2 번의 비교와 이동이 일어나므로 N^2 단계가 필요합니다. 임시변수에 값을 저장하고 다시 배열에 값을 삽입하는 횟수는 각각 N - 1번이므로 2N - 2 단계가 필요합니다. 그래서 총 **N^2 + 2N - 2** 단계가 필요하게 됩니다. 빅-오는 가장 높은 차수만 고려하고, 상수를 무시하기 때문에 **O(N^2)** 라고 할 수 있죠.


### 최선, 최악, 평균

여기까지만 보면 버블, 선택, 삽입 정렬중에서 선택 정렬이 가장 빨라보입니다. 최악의 경우에는 확실히 선택 정렬이 제일 빠르죠. 하지만 **평균적인 경우** 에서는 다릅니다. 왜냐하면 삽입 정렬은 최악의 경우(예를 들어 내림차순인 데이터를 오름차순으로 정렬할때) 모든 데이터를 비교&이동하지만 평균적인 경우(적당히 무작위인 숫자인 경우) 데이터의 절반정도만 비교해도 정렬이 완료될 것이기 때문이죠.

선택 정렬의 경우 최선, 평균, 최악의 경우 모두 동일하게 **O(N^2/2)** 의 시간복잡도를 가집니다. 정렬이 되어있던 아니던 모두 비교해야하기 때문이죠. 하지만 삽입 정렬의 경우 최악에 **O(N^2)**, 평균에 **O(N^2 / 2)**, 최선에 **O(N)** 의 시간이 걸립니다. 데이터가 이미 정렬되어 있는 경우 반복을 도중에 종료할 수 있기 때문이죠.

이것은 각 알고리즘에 대해 더 깊은 고찰의 여지를 남기는 내용이지만, 또한 알고리즘을 작성할 때에 "가능하면 도중에 종료한다" 와 같이 일반적인 수행을 고려한 내용을 넣어 주어야 한다는 말이기도 합니다. 예를 들어, 정렬 알고리즘의 각 반복마다 배열이 정렬되었는지 확인하고, 정렬되었다면 나가는 코드를 작성한다면 "일반적으로 정렬된 데이터가 들어오는" 상황에서 알고리즘을 **O(N)** 으로 단축시킬 수도 있게 되는 것이죠.

결론적으로, 우리는 어떤 알고리즘의 **최선, 최악, 평균** 의 경우를 모두 따져봐야 한다고 할 수 있습니다.

## 해시 테이블

해시 테이블은 배열과 비슷하지만, 인덱스가 0부터 시작하는 숫자가 아닌 특별한 문자열이 사용될 수 있다는 점이 다릅니다. 그래서 특정 값을 볼 때 매우 빠르게 볼 수 있죠.

예를들어, 사이트나 게임에서 아이디와 비밀번호를 입력하고 로그인하려 할 때 시스템에서 만약 배열을 사용한다면, 배열에서 아이디를 검색해서 해당 아이디에 저장된 비밀번호와 사용자가 입력한 비밀번호가 같은지 확인해야 할 겁니다. 이 과정마다 검색이 필요한데, 해시 테이블은 이 과정을 O(1) 만에 해결할 수 있습니다.

이게 가능한 방법은 해시 함수를 사용하기 때문인데, 이는 문자열을 하나의 숫자로 변환하는 것이라 할 수 있습니다. 예를들어, A=1, B=2, C=3... 라고 한다면, "DAC" 라는 문자열은 413 이라고 할 수 있습니다. 여기서 이 413에 4 * 1 * 3 과 같은 작업을 하면 "DAC"의 해시 값은 12가 됩니다. 이는 해시 함수의 한 예일 뿐이고, 실제로는 더 복잡한 식이 사용됩니다. 

해시 함수가 유효하기 위해서는 동일한 문자열을 해시 함수에 적용할 때마다 항상 **동일한 숫자** 로 변환되어야 하는 조건을 가지고 있습니다. 일관적이어야 한다는 것이죠. 그런데 "CAD" 또한 3 * 1 * 4 로 12가 나와 해시 값에 **충돌** 이 있다는 것을 알 수 있습니다. 이는 잠시 후에 알아보도록 하죠.

그럼 이제 해시 함수에 대해 알아보았으니, 해시 테이블이 어떻게 작동되는지 봅시다. 배열과 비슷하게 해시 테이블에 값은 다음과 같이 삽입합니다.
`dictionary["ABC"] = "Hello"`
여기서 인덱스로 사용된 "ABC" 를 **키(Key)**, 안에 들어간 "Hello"를 **값(Value)** 라고 합니다. 그러면 이는 dictionary 라는 해시 테이블의 "ABC" 번째, 즉 1 * 2 * 3 = 6 번째 인덱스에 "Hello" 라는 값을 삽입하게 됩니다. 그럼 값을 꺼낼때는 `search = dictionary["ABC"]` 와 같이 할 수 있으며, 해시 테이블은 또한번 "ABC" 에 해시 함수를 적용시켜 6번째 인덱스의 "Hello" 값을 읽게 됩니다.

### 해시 충돌 해결하기

해시값의 충돌은 여러 방법으로 해결할 수 있지만, 여기서는 그 중 가장 간단하고 직관적인 방법을 알려드리겠습니다.

해시 테이블에 실제 값이 아니라 "참조 값" 을 저장하게 합니다. 그러니까, 해시 테이블의 각 인덱스에는 배열이 있고, 삽입 시에 해시 값의 충돌이 일어나면 인덱스 안의 배열에 추가해주는 것이죠. 그리고 충돌이 있는 해시 값을 읽어오려고 할 때는, 해당 인덱스의 배열을 검색해서 입력받은 키(Key) 값과 일치하는 것을 찾습니다.

예를 들어 `dict["ABC"] = "Pencil"`, `dict["CBA"] = "Sun"` 이라고 한다면 6번째 인덱스에는 `["ABC" : "Pencil", "CBA" : "Sun"]` 과 같은 배열이 들어있게 됩니다. 여기서 `dict["CBA"]` 를 읽어오려고 한다면, 위의 배열에서 `"CBA"` 를 **검색** 해서 "Sun" 을 반환하는 것이죠.

하지만 이 경우, 해시 값의 충돌이 빈번하게 발생한다면 해시 테이블의 효율성이 떨어지게 됩니다. 그래서 가능하면 해시 테이블에 충돌이 없도록 해야합니다.

해시 테이블은 3가지 요인에 의해 효율성이 정해집니다.
1. 해시 테이블에 얼마나 많은 데이터를 저장하는가
2. 해시 테이블에서 얼마나 많은 셀을 쓸 수 있는가
3. 어떤 해시 함수를 사용하는가

해시 테이블에 관해서는 더 깊고 자세히 알아볼 수도 있지만, 대부분은 언어 차원에서 기능을 지원하기 때문에 여기서는 원리만 이해해도 괜찮습니다. 해시 테이블은 언어에 따라 해시, 맵, 해시 맵, 딕셔너리(사전), 연관 배열 등으로 불립니다.

## 스택

스택(Stack) 은 배열과 같지만, 다음과 같은 규칙이 존재합니다.

**스택의 끝에서만 데이터를 읽기, 삽입, 삭제할 수 있다**

책이 쌓여있는 것을 생각할 수 있습니다. 맨 위의 책의 표지만 볼 수 있고, 맨 위에 책을 올려서 쌓거나(Stack) 맨 위에서 책을 빼갈 수 있기 때문이죠. 여기서 스택의 끝을 ***탑(top)*** 이라고 부릅니다. 그리고 스택에 삽입하는 것을 **푸시(Push)** 한다고 합니다.

스택은 LIFO(Last In First Out) 자료구조라고도 불리는데, "마지막에 들어간 게 먼저 나온다" 라는 후입선출의 형태를 가지고 있기 때문입니다.

스택은 이렇게만 보면 어디다 쓸지 막막하지만, 실제론 알고리즘에서 자주 활용됩니다. 예를 들어, 괄호쌍이 제대로 이루어져있는지 확인하거나 계산식을 후위형으로 바꾸기도 합니다.

괄호쌍을 예로 들면 `[(){()}]` 이란 괄호쌍이 올바르게 열리고 닫혔나 확인하기 위해서, 문자열의 인덱스 0부터 반복하며 **왼쪽 괄호라면 푸시(Push) 하고 오른쪽 괄호라면 팝(Pop)** 해주고, 팝해준 괄호가 오른쪽 괄호랑 같은 종류가 맞는지 확인해 주는 방법을 사용할 수 있습니다.

이 외에도 실행취소(Ctrl+Z) 나 이전에 방문한 사이트들을 저장하는 일 등에도 스택이 사용됩니다.

## 큐

큐(Queue) 또한 스택과 비슷한데, 이는 FIFO(First In First Out) 이라는 선입선출 형태를 가지고 있습니다. 대기열이라는 뜻을 가진 큐는 **큐의 끝에서만 삽입할 수 있고, 큐의 앞에서만 읽고 삭제할 수 있다** 라는 규칙을 가지고 있습니다. 큐에 값을 삭제/제거하는것은 언어마다 스택과 같이 Push/Pop 이라고 부르거나 Enqueue/Dequeue 라고 부르기도 하니 용어에 유의해주시기 바랍니다.

큐의 맨 앞은 ***프론트(Front)*** 라고 부르고, 맨 뒤는 ***리어(Rear)*** 라고 부릅니다. 큐는 좀 더 직관적으로 게임에서의 대기열 등 선착순의 개념이 존재하는 알고리즘들에서 사용됩니다.

## 재귀 호출

함수는 자기 자신을 호출해서 반복할 수 있습니다. 여기서 함수가 자기 자신을 호출하는 것을 **재귀(recursion)** 라고 하고, 이런 함수를 재귀 함수라고 합니다.

```cpp
void print() {
  printf("Hello\n");
  print();
}
```
위 코드는 `"Hello"` 라는 문자열을 무한히 반복하며 출력합니다. 왜냐면 `print()` 함수가 자기 자신을 호출하고 있기 때문이죠. 그럼 자기가 자기를 호출하고... 이렇게 무한 반복이 되는겁니다. 그래서 보통은 반복문을 쓸 때와 비슷하게 나가는 조건과 값을 변화시킬 식을 포함합니다.

```cpp
int fact(int n) {
  if (n == 1) return 1;
  return n * fact(n - 1);
}
```
위 코드는 팩토리얼(5! = 5\*4\*3\*2\*1) 을 계산해주는 재귀함수입니다. 재귀호출을 할 때마다 n이 1씩 감소하고, n이 1이면 더이상 재귀호출을 하지 않아 재귀가 멈추고, 지금까지 계산된 식이 전부 실행되며 결과가 계산되죠. 여기서 재귀 호출을 멈추게 하는 조건을 **기저 조건(base case)** 라고 하며, 위 코드의 경우 `1` 이 기저 조건입니다.

재귀 함수를 사용해본 적이 없다면 위 코드가 읽기 난해할텐데, 재귀 함수를 쉽게 이해하는 방법이 존재합니다.

1. 기저 조건을 찾는다
2. 기저 조건에 맞을 경우의 함수의 상태를 본다
3. 기저 조건의 바로 전의 함수의 상태를 본다
4. 계속 단계를 올려가며 함수의 상태를 본다

위 코드를 예로 들면, n에 1이 들어있을 경우에 함수가 어떻게 되는지 봅니다. 1을 반환하네요. `fact(1) = 1` 이란 것을 알았습니다. 재귀 호출에서 `n - 1` 을 넘겨주고 있기 때문에, 다음에는 n이 2인 경우를 봅니다. `2 * fact(1)` 인데, `fact(1)` 은 1이므로 2 * 1 을 계산하여 `fact(2) = 2` 라는 것을 알 수 있습니다. 다음으로 3을 보면...

이렇게 한 단계씩 살펴보면 좀 더 수월하게 재귀함수를 파악할 수 있습니다.

여기서 추가적으로 알아야 할 것이 있는데, 바로 **호출 스택** 이라는 개념입니다. 코드에서 함수를 실행하면, 컴퓨터는 함수를 실행한 지점 등의 정보를 "호출 스택" 에 푸시(Push) 해줍니다. 그 이유는, 함수를 호출했다면 해당 함수가 종료된 후에 다시 함수를 호출한 곳부터 코드를 이어서 실행해야 하기 때문이죠.

그래서 `fact(3)` 를 호출하면 `[ fact(3), fact(2), fact(1) ]` 와 같이 호출 스택에 들어가게 되고 `fact(1)` 부터 차례대로 팝(Pop) 하게 됩니다. 그래서 실행한 것의 역순으로 코드가 끝나게 되죠. 여기서 만약에 재귀 호출이 매우 많아져서 메모리에 공간이 부족해지면 **스택 오버플로(Stack Overflow)** 라는 오류가 발생합니다.

자 그럼, 이 재귀함수가 왜 필요할까요? 재귀함수는 하나의 큰 문제를 작은 **부분문제** 들로 나눌 수 있습니다. 위의 팩토리얼 예제를 보아도 함수가 하나의 팩토리얼을 전부 계산하지 않고 현재 자신 번째의 값만 계산하고, 다음 값의 계산은 재귀호출로 처리하였습니다. 또는, 한 알고리즘에서 같은 알고리즘을 반복해야 하는 경우에도 사용됩니다. 예를 들어, 한 폴더를 지정해서 그 폴더 안의 모든 파일을 출력하는 알고리즘의 경우, 반복문으로는 풀기 힘듭니다.

```cpp
// ...생략
for (i = 0; i < dir.count; i++) {
  printf(dir[i].name);
  if (dir[i].type == "Folder")
    for (j = 0; j < dir[i].count; j++) {
      printf(dir[i][j].name);
      // ...중략
    }

}
```
위는 실제 동작하지는 않는 의사 코드(Pseudo Code) 인데, 만약 보고있는 파일이 폴더라면 그 폴더에 대해 반복문을 추가로 돌아야 하는데, 폴더가 몇 단계까지 되어있는지도 모르고, 그렇다 하더라도 반복문을 계속 이어나갈 수는 없죠. 여기서 재귀 함수를 쓰면 훨씬 간단하게 처리할 수 있습니다.

```cpp
void printFileNames(Directory dir) {
  for (i = 0; i < dir.count; i++) {
    printf(dir[i].name);
    if (dir[i].type == "Folder")
      printFileNames(dir[i]); 
  }
}
```
읽은 파일 타입이 폴더일 경우, 자기 자신에 해당 파일(폴더)를 매개변수로 넣어 호출해주는 것이죠. 이로 인해 코드도 매우 작고 깔끔해졌습니다. 작동하는 코드가 아니라 작동 방식은 이해하기 힘들어도, 어떤 느낌인지는 파악했다고 생각합니다. 재귀 함수는 알고리즘 풀이에서 기초이자 필수인 부분으로, 꼭 여러 예제와 문제들을 살펴보아 복습하시길 바랍니다.

## 연결 리스트

연결 리스트는, 배열과 비슷하지만 내부 기능은 전혀 다른 자료구조입니다. 배열은 한번 선언하면 메모리 내에 연속적으로 존재하게 되어서 처음 인덱스부터 N칸 뒤의 메모리 주소에 접근하는 것으로 O(1) 만에 읽기가 가능하다고 했었습니다. 하지만 연결 리스트는 원소들이 전부 메모리에 따로따로 위치한 자료구조입니다.

그럼 어떻게 값들을 저장하는 것일까요? 배열의 각 원소는 저장해야 할 값 뿐만 아니라 다음 원소의 주소 또한 지니고 있습니다. 그래서 만약 인덱스 4의 원소를 읽으려면 인덱스 0부터 시작해서 다음 주소, 다음 주소... 이렇게 0 - 1 - 2 - 3 인덱스를 참조해야 인덱스 4를 읽을 수 있습니다. 이 때 이 연속되게 위치하지 않은 원소들을 **노드(Node)** 라고 부릅니다.

그래서 배열과 비교해서 연결 리스트의 장점은 무엇일까요? 우선 배열의 경우, 원소를 10000개 가지게 선언하려면 원소 10000개 만큼의 **연속된 빈 메모리 공간** 이 있어야 합니다. 하지만 연결 리스트는 연속되지 않더라도 10000개의 빈 공간만 있어도 되죠. 배열에서 읽기는 O(1)이지만, 연결 리스트에서 읽기는 O(N)입니다. 그래서 읽기를 많이 하는 경우라면, 배열이 더 좋겠죠. 검색은 둘 다 동일하게 O(N)이 걸립니다. 

하지만 삭제와 삽입의 경우, 배열은 O(N)이지만 연결 리스트는 ***O(1)*** 이 걸립니다. 왜냐하면, 배열의 경우 중간에 있는 원소를 삭제하거나 중간에 삽입하려면 원소들을 전부 한 칸씩 밀어주어야 하지만 연결 리스트는 그냥 "A->B->C 에서 B를 삭제하려면, A가 C를 가리키게 한다" 고 하면 끝이기 때문이죠. 삽입의 경우에도 "A->C 사이에 B를 넣으려면 A가 B를 가리키게 만들고, B는 C를 가리키게 만든다" 라고 하면 끝입니다. 물론 삽입하는 공간을 찾기 위해서 O(N) 정도가 소요되기는 하죠.

C언어와 포인터를 다루지 않았다면, 이를 직접 구현할 일은 없고 언어에서 지원하는 것을 사용하게 될 겁니다. 직접 구현한다 하더라도, C#과 Java처럼 가비지 컬렉터(Garbage Collector, 안쓰이는 메모리를 자동으로 해제) 가 있지 않다면 수동으로 메모리를 해제해야 한다는 것 또한 까다롭습니다. 그러니까 연결 리스트는 개념만 알아두도록 합시다!

여기서 **이중 연결 리스트** 라는 것도 볼 수 있는데, 이는 노드 하나가 자신의 다음 번째 원소뿐 아니라 자신의 이전 번째 원소의 위치 또한 가지고 있게 하는 것입니다. 그래서 원래는 0번째부터 단방향 이었다면 이중 연결 리스트는 양방향으로 움직일 수 있다는 거죠.

결론적으로, 연결 리스트는 "값의 삭제와 삽입이 빈번하게 일어나는 경우" 에 사용된다고 볼 수 있습니다. 적재적소에 필요한 자료구조를 사용하도록 합시다!

## 이진 트리

이진 트리(Binary Tree)는 **트리(Tree)** 자료구조의 한 종류로, 연결 리스트와 비슷하게 각 노드가 여러 노드의 주소를 지니고 있는 자료구조입니다.

```
       v-----Food-----v
  v--Fruit--v       v--Meat--v
Apple     Mango   Beef     Pork
```
이진 트리는 위와 같이 Food가 `Fruit과 Meat`로, Fruit가 `Apple과 Mango`로, Meat가 `Beef와 Pork`로 연결되어 있습니다. 여기서 가장 상위인 노드인 Food를 **루트(Root)** 라고 부르며, 트리의 꼭대기가 됩니다. 여기서 Food를 Fruit과 Meat의 **부모** 라고 하고, Fruit과 Meat는 Food의 **자식** 이라고 합니다. 그리고 트리에는 깊이를 뜻하는 **레벨(Level)** 이 있는데, 위 트리의 레벨은 3입니다.

"트리" 의 경우, 한 노드가 여러 개의 자식을 지닐 수 있지만 이진 트리는 **2개 이하**로만 자식을 지닐 수 있다는 제약이 존재합니다. 이번 예제에서는 여기에서 더 나아가 "왼쪽은 부모보다 작은 값을 가지고, 오른쪽은 부모보다 큰 값을 가진다" 라는 조건을 더해보겠습니다. 그러면 루트부터 시작해서 원하는 값을 찾을 때, 현재 찾으려는 값이 노드의 값보다 더 크다면 오른쪽 자식으로, 작다면 왼쪽 자식으로 이동하며 **이진 검색** 과 동일한 구조를 보여줄 수 있죠. 이는 "정렬된 배열에서의 이진 검색" 과 비슷하지만, 연결 리스트와 같이 노드 기반의 자료구조이기 때문에 삽입과 삭제 시에도 O(log N)이 걸린다는 특징이 있습니다. (이를 "이진 검색 트리" 라고 합니다)

이진 트리는 검색, 삽입, 삭제에서 모두 O(log N) 이기 때문에 안정적이면서 매우 효율적인 자료구조이고, 그로 인해 힙 트리(Heap) 등 다양한 분류가 존재합니다. 물론 이 외에도 트리 자체가 일상 생활에서 자주 보는 계층 구조를 가지고 있기 때문에 B트리, 레드-블랙 트리 등 다양하니 한번 더 찾아보는 것을 추천합니다!

## 그래프

그래프는 데이터의 연결관계를 나타내는 자료구조입니다.



### BFS

### DFS

### 데이크스트라 알고리즘

## 자료구조 심화

### 유니온 파인드

### 프림의 최소신장트리

### 힙

### 세그먼트 트리

### 벨먼-포드 알고리즘

## 백트래킹

## 동적계획법

### 메모이제이션, 하향식(Top-down)

### 타뷸레이션, 상향식(Bottom-up)

## 그리디 알고리즘

## 분할 정복