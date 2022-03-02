---
title: '[C++ STL] 덱(Deque)'
date: 2020-12-23 22:37:00 +0900
categories: [Lectures, Language]
tags: [Basic]
---

**\[!\]** 덱은 벡터와 거의 유사하기 때문에, 글을 읽기 전에 [이곳](https://termsigening97.github.io/posts/CPP-STL-Vector/)을 눌러 벡터의 게시글을 먼저 읽고 오시는 것을 추천합니다.

 덱(Deque)은 벡터와 같은 시퀀스 컨테이너이고, 배열 기반 컨테이너입니다. 또, 대부분의 기능이 벡터와 동일하지만, 벡터의 단점들을 보완한 컨테이너입니다. 벡터(Vector) 글의 마지막을 보면, 벡터는 벡터의 크기보다 많은 원소를 할당하려고 하면, 메모리를 다시 할당하고, 할당된 메모리에 원소들을 복사하고, 원래의 메모리는 해제한다고 하였습니다. 덱은 이 문제를 보완하여, 여러 개의 메모리 블록을 할당하고, 원소를 추가할 때 메모리가 부족해질 때마다 일정한 크기의 새 메모리 블록을 할당하여 원소의 복사나 메모리의 재할당이 전혀 일어나지 않습니다.

> deque\_Ex01.cpp

```cpp
#include <iostream>
#include <deque>

using namespace std;

int main() {

	deque<int> d(5, 1);

	cout << "Init : ";
	for (size_t i = 0; i < d.size(); i++) {
		cout << d[i] << ' ';
	}
	
	cout << endl;

	d.pop_back();
	d.push_back(5);
	d.pop_front();
	d.push_front(3);

	cout << "Modi : ";
	for (size_t i = 0; i < d.size(); i++) {
		cout << d[i] << ' ';
	}

	return 0;
}
```

> **생성자**

| deque dq | dq는 비어있는 덱 |  |
| deque dq(n) | dq는 기본값으로 초기화된 n 크기의 덱 |  |
| deque dq(n, x) | dq는 x로 초기화된 n 크기의 덱 |  |
| deque dq(dq2) | dq는 dq2 덱을 복사한 덱 |  |
| deque dq(b, e) | dq는 반복자 구간 \[b, e)로 초기화된 덱 |  |

사용법은 모두 벡터와 같습니다.

> **멤버 함수**

| dq.assign(n, x) | dq에 x값으로 n개의 원소를 할당한다 |  |
| dq.begin(), dq.end() | dq의 반복자 처음, 끝을 나타낸다 |  |
| dq.size() | dq의 크기를 나타낸다 |  |
| dq.empty() | dq가 비었는지 나타낸다 |  |
| dq.clear() | dq의 모든 원소를 제거한다 |  |
| dq.front(), dq.back() | dq의 첫번째/마지막 원소를 참조한다 |  |
| dq.insert(p, n, x) | p가 가리키는 위치에 n개의 x값을 삽입한다 |  |
| dq.resize(n) | dq의 크기를 n으로 변경한다 |  |
| dq.resize(n, x) | x를 넣을시 변경 후 확장된 값을 x로 초기화한다 |  |
| dq.pop\_front(), dq.pop\_back() | dq의 첫번째/마지막 원소를 제거한다 |  |
| dq.push\_front(x), dq.push\_back(x) | dq의 첫번째/마지막에 원소 x를 추가한다 |  |
| dq.swap(dq2) | dq와 dq2를 교환한다 |  |

벡터와 다르게 pop\_front와 push\_front가 있는 것을 확인할 수 있습니다.

이 외의 사용법은 모두 벡터와 동일하기 때문에 따로 예제를 추가하지는 않겠습니다.