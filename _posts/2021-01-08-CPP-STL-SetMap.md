---
title: '[C++ STL] 연관 컨테이너 set & map'
date: 2021-01-08 20:58:00 +0900
categories: [Lectures, Language]
tags: [Basic]
---

 모든 연관 컨테이너는 노드 기반 컨테이너이고, 균형 이진 트리로 구현되었고 균형 이진 트리의 모든 특징을 가집니다.

연관 컨테이너는 총 4가지가 있지만, 전부 서로 비슷하고 크게 다르지 않아 하나를 잘 이해한다면 나머지도 쉽게 이해할 수 있습니다. 실제로, 모든 연관 컨테이너들은 같은 인터페이스(생성자, 멤버 함수, 연산자)를 사용합니다.

 연관 컨테이너는 정렬 기준인 조건자에 따라 원소를 자동으로 정렬하는 컨테이너입니다. 이 정렬 기준은 컨테이너를 처음 생성할 때 템플릿 매개변수로 지정할 수 있습니다. 이 템플릿 형식은 아래에 각 컨테이너별로 정리되어질 것입니다. 이렇게 자기 멋대로 정렬을 하기 때문에 시퀀스 컨테이너처럼 맨 뒤에 넣거나, 특정 위치에 원소를 넣거나 하는 작업은 할 수 없습니다.

 그렇다면 왜 연관 컨테이너를 사용할까요? 연관 컨테이너는 균형 이진 트리의 구조이기 때문에 탐색과 삽입에서 로그의 시간 복잡도를 가지고 있어 매우 빠르게 처리할 수 있습니다. 연관 컨테이너를 완벽하게 다루고 싶다면, 균형 이진 트리를 이해하고 있어야 합니다.

> **연관 컨테이너의 생성자**

| set s; | s는 빈 컨테이너 |
| set s(pred); | s는 빈 컨테이너고 정렬 기준은 pred 조건자 |
| set s(s2) | s는 s2 컨테이너의 복사본 |
| set s(b, e) | s는 반복자 구간 \[b, e)로 초기화된 원소 |
| set s(b, e, pred) | s는 반복자 구간 \[b, e)로 초기화된 원소이고 정렬 기준은 pred 조건자 |

예시로는 set을 사용하였고, 연관 컨테이너 공통입니다.

> **연관 컨테이너의 멤버 함수**

| s.begin(), s.end() | s의 첫/끝 원소를 가리키는 반복자 |
| s.clear(), s.empty() | s의 모든 원소를 제거한다, s가 비었는지 여부 |
| s.size(), s.max\_size() | s의 원소의 개수, s가 담을 수 있는 최대 원소의 개수(메모리 크기) |
| s.count(k) | k와 일치하는 값의 개수 |
| s.erase(p) | 반복자 p가 가리키는 원소를 제거하고 다음 원소의 반복자를 반환한다 |
| s.erase(b,e) | 반복자 구간 \[b, e)의 모든 원소를 제거하고 다음 원소의 반복자를 반환한다 |
| s.erase(k) | k와 일치하는 값을 모두 제거하고 제거한 개수를 반환한다 |
| s.insert(k) | k를 삽입하고, 그 원소 위치의 반복자와 성공여부의 bool값의 pair를 반환한다 |
| s.insert(p, k) | p가 가르키는 위치에 k를 삽입하고, 그 원소 위치의 반복자를 반환한다 |
| s.insert(b, e) | 반복자 구간 \[b, e)의 원소를 삽입한다 |
| s.swap(s2) | s와 s2를 서로 교환한다 |
| s.lower\_bound(k) | k 값의 시작 구간을 가리키는 반복자 |
| s.upper\_bound(k) | k 값의 끝 구간을 가리키는 반복자 |

여기서 insert 함수에서 위치 지정은 "삽입 탐색을 시작할 위치"입니다. 무슨 말이냐면, 원소가 정렬된 위치를 찾기 위한 연산이 시작되는 부분입니다. 만약 삽입 후에도 정렬 순서가 맞다면 삽입이 바로 끝나지만 아니라면 로그의 시간이 걸립니다.

다른 함수들은 간단하기 때문에 직접 사용해보면서 알 수 있지만 lower\_bound()와 upper\_bound()는 이해하기 까다로울 수 있기 때문에 설명하도록 하겠습니다. 두 함수는 찾은 원소(key)를 반복자(순차열 구간)로 반환합니다. lower\_bound()는 찾은 원소의 시작 반복자를, upper\_bound()는 찾은 원소의 다음 원소를 가리키는 반복자입니다. 그래서 lower\_bound()와 upper\_bound()가 같다면 찾는 원소는 없습니다.

> **bound\_ex.cpp**

```cpp
#include <iostream>
#include <set>

using namespace std;

int main() {

	set<int> s;

	for (int i = 10; i <= 90; i += 10)
		s.insert(i);

	set<int>::iterator lower;
	set<int>::iterator upper;

	lower = s.lower_bound(50);
	upper = s.upper_bound(50);

	cout << *lower << " & " << *upper;


	lower = s.lower_bound(150);
	upper = s.upper_bound(150);

	if (lower == upper)
		cout << "150은 set에 포함되어있지 않습니다" << endl;

	return 0;
}
```

출력 결과

```
50 & 60  
150은 set에 포함되어있지 않습니다
```

<br>

> **set의 템플릿 형식**

```cpp
template<  
    typename Key,  
    typename Pred=less<Key>,  
    typename Allocator=allocator<Key>
>  
class set
```

 **set 컨테이너**는 key라고 불리는 값의 집합으로 이루어진 컨테이너입니다. 멤버 함수인 insert()만으로 값을 삽입할 수 있으며, 삽입된 값은 정렬 기준에 따라 자동 정렬됩니다. 삽입된 원소들을 key라고 부르고, 이 key를 이용해서 정렬합니다. 또한, set의 특징은 모든 key가 유일하다는 점입니다. 다시 말해서 똑같은 값을 2번 이상 중복해서 컨테이너에 삽입할 수 없다는 뜻입니다. 

 **multiset 컨테이너**는 원소(key)를 중복해서 삽입할 수 있다는 것 외에는 set과 다른 점이 없고, <set> 에 포함되어있습니다.

<br>

***

<br>

> **map의 템플릿 형식**

```cpp
template<  
    typename Key,  
    typename Value,  
    typename Pred=less<Key>,  
    typename Allocator=allocator<pair<const Key, Value>>  
>  
class map
```

 **map 컨테이너**는 가장 자주 사용하는 컨테이너로 원소가 key와 value라는 값의 쌍으로 이루어져 있습니다. map 또한 set처럼 중복되는 key를 가질 수 없습니다. 그리고 여기서 map과 set의 중요한 차이점이 나옵니다. map 컨테이너는 원하는 key에 해당하는 원소의 value값에 접근할 수 있는 \[\] 연산자를 지원합니다. m\[k\] = v 같은 방식으로 사용하며, m 컨테이너의 k에 해당하는 key값의 value를 v로 수정하거나, 없을 경우 새로 추가합니다. map은 중요하고, 다른 대부분의 객체지향언어들이 지원하는 자료구조이기 때문에 예제를 보며 학습해봅시다.

 **multimap 컨테이너**는 원소(key)를 중복해서 삽입할 수 있다는 것 외에는 map과 다른 점이 없고, <map>에 포함되어있습니다.

> **map\_ex.cpp**

```cpp
#include <iostream>
#include <map>

using namespace std;

int main() {

	map<string, int> m;

	m.insert(pair<string, int>("C언어", 1500));
	m.insert(pair<string, int>("Java", 2000));
	m.insert(pair<string, int>("파이썬", 1800));
	m["C#"] = 2500;
	m["PHP"] = 1500;

	map<string, int>::iterator it;
	for (it = m.begin(); it != m.end(); it++) {
		cout << "도서명 : " << (*it).first << ", 가격 : " << (*it).second << endl;
	}

	return 0;
}
```