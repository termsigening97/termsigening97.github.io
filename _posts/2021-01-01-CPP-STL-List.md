---
title: '[C++ STL] 리스트(List)'
date: 2021-01-01 14:12:00 +0900
categories: [Lectures, Language]
tags: [Basic]
---

리스트(List)는 시퀀스 컨테이너 중, "이중 연결 리스트" 라는 자료구조를 사용하는 노드 기반 컨테이너로 벡터(Vector)나 덱(Deque)와는 다른 성질을 가집니다. 리스트를 완전히 이해하기 위해서는, 이중 연결 리스트와 반복자를 먼저 공부해야 합니다.

> **list\_ex01.cpp**

```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
	list<int> lt(5);
	
	list<int>::iterator iter;

	for (iter = lt.begin(); iter != lt.end(); ++iter) {
		cout << *iter << ' ';
	}

	cout << endl;

	iter = lt.begin();
	iter++;

	iter = lt.insert(iter, 5);

	cout << "Inserted Object : " << *iter << endl;

	for (iter = lt.begin(); iter != lt.end(); ++iter) {
		cout << *iter << ' ';
	}

	return 0;
}
```

예제를 보면, \[\] 연산자나 at() 함수가 없는 것을 볼 수 있습니다. 왜냐하면, 리스트 컨테이너는 연결 리스트 자료구조이기 때문에 인덱스(숫자)로 접근하는 것이 불가능하기 때문입니다. 대신 리스트는 반복자(iterator)를 이용하여 원소를 접근, 할당합니다.

> **생성자**

| list lt | lt는 비어있는 리스트 |  |
| list lt(n) | lt는 기본값으로 초기화된 n 크기의 리스트 |  |
| list lt(n, x) | lt는 x로 초기화된 n 크기의 리스트 |  |
| list lt(lt2) | lt는 lt2 리스트를 복사한 리스트 |  |
| list lt(b, e) | lt는 반복자 구간 \[b, e)로 초기화된 리스트 |  |

사용법은 다른 시퀀스 컨테이너와 동일합니다.

> **멤버 함수**

| lt.assign(n, x) | lt에 x값으로 n개의 원소를 할당한다 |  |
| lt.begin(), lt.end() | lt의 반복자 처음, 끝을 나타낸다 |  |
| lt.size() | lt의 원소의 개수를 나타낸다 |  |
| lt.resize(n) | lt의 크기를 n으로 바꾸고 추가된 공간을 기본값으로 초기화한다 |  |
| lt.empty() | lt가 비었는지 나타낸다 |  |
| lt.clear() | lt의 모든 원소를 제거한다 |  |
| lt.front(), lt.back() | lt의 첫 번째 원소, 마지막 원소를 참조한다 |  |
| q = lt.insert(p,x) | p의 위치에 x값을 삽입하고, 그 원소를 가르키는 반복자를 반환한다 |  |
| q = lt.erase(p) | p의 위치의 값을 제거하고, 그 다음 원소를 가르키는 반복자를 반환한다 |  |
| lt.insert(p, n, x) | p의 위치에 n개의 x값를 삽입한다 |  |
| lt.pop\_back(), lt.pop\_front() | lt의 첫번째/마지막 원소를 제거한다 |  |
| lt.push\_back(x), lt.push\_front(x) | lt의 첫번째/마지막에 원소 x를 추가한다 |  |
| lt.remove(x) | x값에 해당하는 원소를 모두 제거한다 |  |
| lt.merge(lt2) | lt2를 lt로 합병하고 정렬한다 |  |
| lt.sort() | lt를 오름차순으로 정렬한다 |  |
| lt.reverse() | lt의 순서를 뒤집는다 |  |
| lt.unique() | lt의 인접한 원소의 값이 같은 노드들을 하나의 노드로 만든다 |  |
| lt.swap(lt2) | lt와 lt2를 교환한다 |  |

 리스트 컨테이너는 기본적으로 시퀀스 컨테이너의 모든 특징을 가집니다. 즉, 벡터나 덱에서 사용하던 기능을 이곳에서도 거의 전부 사용할 수 있습니다. 하지만, 위의 표에서 보다시피 리스트는 지원하는 기능이 훨씬 많습니다.

 그 중에서도 리스트만의 특징을 알아보도록 합니다. 리스트 컨테이너는 이중 연결 리스트이기 때문에, insert()와 erase() 함수가 O(1)의 성능을 보여줍니다. 배열 기반의 컨테이너의 경우는 원소를 삽입하면 뒤의 원소를 전부 밀어내야하는데, 리스트의 경우 자신의 앞뒤의 포인터만 수정해주면 되기 때문입니다. 또한, insert()와 erase()함수를 사용한 후에도 반복자를 계속하여 사용할 수 있습니다. 벡터나 덱의 경우는 원소를 삽입하면 메모리가 재할당될 수 있기 때문에 반복자를 무효화시키기 때문입니다.

remove(x)라는 함수는, 컨테이너를 탐색하며 x값에 해당하는 원소들을 모두 제거하는데, 이 함수는 리스트만이 가지고 있으며 컨테이너의 길이만큼만 반복하기 때문에 속도도 매우 빠릅니다. remove\_if(pred)라는 단항 조건자(predicate)를 매개변수로 하여 조건에 맞는 원소를 모두 지우는 작업도 가능합니다. 사용법은 다음과 같습니다.

> **list\_removeif\_ex.cpp**

```cpp
#include <iostream>
#include <list>

using namespace std;

bool Compare(int x) {
	return x % 2 == 0 && x > 0;
}

int main() {
	list<int> lt(10);
	
	list<int>::iterator iter;

	int tmp = -4;
	for (iter = lt.begin(); iter != lt.end(); ++iter, ++tmp)
		*iter = tmp;

	for (iter = lt.begin(); iter != lt.end(); ++iter)
		cout << *iter << ' ';

	cout << endl;
	
	lt.remove_if(Compare);

	for (iter = lt.begin(); iter != lt.end(); ++iter)
		cout << *iter << ' ';

	return 0;
}
```

Compare 함수에 리스트 컨테이너의 모든 원소가 하나씩 전달되어서 조건에 맞으면 해당 노드를 삭제하는 방식으로 동작합니다. 현 예제에서는 10개의 원소를 -4~5으로 초기화한 후, "양수 중에서 짝수인 수"만 remove\_if() 함수로 제거하였습니다. remove\_if()에 전달하는 자료형은 조건자로써 함수, 함수 객체, 함수 포인터를 전달하게 됩니다. 이 조건자에 대해서는 다른 게시글에서 다루도록 하겠습니다.

리스트 컨테이너에는 sort() 라는 멤버함수가 존재합니다. STL의 <algorithm> 라이브러리에는 거의 대부분의 컨테이너들에 통용되는 알고리즘(정렬, 탐색 등)이 들어있는데, 리스트는 자료구조의 특성으로 이 라이브러리의 sort()를 사용할 수 없기 때문에 자체적으로 제작된 sort() 함수가 존재합니다. 이 멤버함수는 기본적으로 오름차순으로 정렬하지만, 조건자를 매개변수로 전달해주면 원하는 조건을 이용할 수 있습니다. greater<int>()와 less<int>()는 STL에 내장된 조건 함수로 각각 오름차순/내림차순 을 지원합니다. 위의 remove\_if() 예제와 동일한 방법이기 때문에 따로 예제는 첨부하지 않겠습니다.

merge() 함수는 두개의 리스트를 합치고 정렬하는 함수입니다. lt.merge(lt2) 을 실행하면 lt2 리스트의 원소는 사라지고 lt에 합병 후 오름차순으로 정렬됩니다. 만약 다른 정렬방식을 사용하고 싶다면, 두번째 매개변수로 조건자를 넘겨줄 수 있습니다. lt.merge(lt2, pred)와 같이 이용하면 됩니다. 이 때 주의할 점은 두 리스트가 같은 정렬방식으로 정렬되어있어야 한다는 것입니다.

리스트의 큰 특징중 하나로 splice()라는 함수가 존재합니다. 이 함수는 다른 리스트 컨테이너의 한 부분을 잘라붙일 수 있습니다.

> **list\_splice\_ex01.cpp**

```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
	list<int> lt1;
	list<int> lt2;
	
	list<int>::iterator iter;

	int num = 10;
	for (int i = 0; i < 5; i++, num += 10) {
		lt1.push_back(num);
		lt2.push_back(num / 10);
	}

	lt1.splice(lt1.begin(), lt2);

	for (iter = lt1.begin(); iter != lt1.end(); ++iter)
		cout << *iter << ' ';


	return 0;
}
```

- lt1.splice(iter, lt2)

와 같은 방식으로 사용하며, lt1의 iter가 가르키는 위치에 lt2의 모든 원소를 넣습니다. 다른 방법으로는, lt1.splice(iter1, lt2, iter2) 가 있는데 lt1에 lt2를 붙여넣는다는 것은 동일하지만 lt2의 iter2가 가르키는 위치의 원소만을 넣습니다.

마지막으로, 두 반복자로 부분구간을 넣는 방식이 있습니다.

> **list\_splice\_ex02.cpp**

```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
	list<int> lt1;
	list<int> lt2;
	
	list<int>::iterator iter1;

	int num = 10;
	for (int i = 0; i < 5; i++, num += 10) {
		lt1.push_back(num);
		lt2.push_back(num / 10);
	}

	list<int>::iterator lt2_it1, lt2_it2;
	
	lt2_it1 = lt2.begin();
	lt2_it1++;
	lt2_it2 = lt2.end();
	lt2_it2--;
	lt1.splice(lt1.begin(), lt2, lt2_it1, lt2_it2);

	for (iter1 = lt1.begin(); iter1 != lt1.end(); ++iter1)
		cout << *iter1 << ' ';


	return 0;
}
```

- lt1.splice(iter, lt2, b, e)

와 같은 방식으로 사용하며, \[b, e) 만큼의 반복자 영역을 잘라 붙입니다. 마지막으로, splice()는 단지 두 리스트를 연결하는 것이기 때문에 O(1)의 시간이 걸립니다! 

그래서, 리스트 컨테이너는 언제 사용하는게 좋을까요? 리스트는 중간에 삽입, 제거가 빈번하게 발생하거나 상대적인 순서가 중요하다면 주로 사용하게 됩니다. 또한, 리스트는 다른 리스트와 결합하고 싶을 때 큰 장점을 발휘하는 컨테이너입니다. 그렇기 때문에 주로 벡터나 덱을 자주 사용하지만, 특수한 경우에 큰 힘을 발휘하는 컨테이너라고 생각하면 됩니다.