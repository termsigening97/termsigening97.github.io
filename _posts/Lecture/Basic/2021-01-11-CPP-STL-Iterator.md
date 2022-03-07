---
title: '[C++ STL 심화] 반복자(iterator)'
date: 2021-01-11 23:20:00 +0900
categories: [Lectures, Basic]
tags: [C++]
---

반복자는 포인터를 추상화 한 클래스입니다. 추상화, 클래스에 대해서는 객체지향에 관해 공부하면서 배울 수 있습니다. 그런건 지금은 제쳐 두고, 반복자가 무엇이고, 어떻게 사용하는지에 대해 알아봅시다.

> 반복자의 종류와 연산자

| 입력 반복자-input iterator | \*(읽기), ->, ++, ==, !=, 복사 생성자 |
| 출력 반복자-output iterator | \*(쓰기), ++, 복사 생성자 |
| 순방향 반복자-foward iterator | \*(읽기,쓰기), ++, 복사 생성자 |
| 양방향 반복자-bidirectional iterator | \*(읽기,쓰기), ++, --, 복사 생성자 |
| 임의 접근 반복자-random access iterator | \[\], +=, -=, +, -, <, >, <=, >= |

여기서 \*는 포인터에서 주소의 값을 참조하는 것과 같은 쓰임새로, iter라는 반복자 객체에 `*iter`를 사용하여 값을 읽어오거나, 대입해서 쓸 수 있습니다. 읽기가 가능하다는 것은 `*iter`로 값을 가져올 수 있다는 것이고, 쓰기가 가능하다는 것은 `*iter = x` 으로 값을 대입할 수 있다는 뜻입니다.

> 반복자에는 순차열(sequence) 과 구간(range)이라는 중요한 개념도 존재합니다. 순차열은 반복자의 시작과 끝으로 이루어진 구간인데, \[b, e) 라는 표현은, 시작하는 위치를 가리키는 b라는 반복자와 끝나는 위치를 가리키는 e라는 반복자의 구간으로 이루어진 순차열이라는 뜻입니다.
> <br> 대괄호는 해당 위치도 포함한다는 뜻이고, 소괄호는 포함하지 않는다는 뜻이기 때문에 시작 위치는 포함되지만 끝나는 위치는 포함되지 않는다고 볼 수 있습니다.
{: .prompt-info }

 모든 컨테이너 C는 정방향 반복자인 `C::iterator`와 `C::const_iterator`와 역방향 반복자인 `C::reverse_iterator`와 `C::const\_reverse\_iterator`가 존재합니다. `const_` 가 붙은 반복자들은 상수형으로써 읽기만 가능하다는 뜻이고, 일반 iterator은 읽기와 쓰기가 모두 가능합니다. 이 때, 노드 기반 컨테이너는 양방향 반복자를 사용하고 시퀀스 기반 컨테이너는 임의 접근 반복자를 사용합니다. 컨테이너의 begin()은 컨테이너 순차열의 첫 원소의 반복자를 반환하고 end() 함수는 순차열의 끝 표시 반복자를 반환합니다. const 타입으로 iterator를 선언하는것과 const\_iterator 타입을 쓰는것은 서로 다른데, const 타입으로 선언하면 반복자의 값 자체가 바뀔 수 없고 const\_iterator는 반복자가 가리키는 값을 바꿀 수 없습니다.

 `C::reverse_iterator`와 `C::const_reverse_iterator`는 말그대로 끝에서부터 처음으로 읽는 반복자입니다. rbegin()과 rend()로 컨테이너 순차열의 끝, 처음 부분을 가리키는 반복자를 반환받을 수 있습니다. 주의할 점은, 역방향 반복자는 반복자와 반복자가 가리키는 원소가 다릅니다. 반복자의 위치에서 한칸 더 간 위치의 값을 가리키는데, 예를 들어 10 20 30 40 50 순차열에서 반복자의 위치가 30이라면, `*iter`을 할 시 20의 값이 나오게 됩니다.

 반복자 중에는 삽입 반복자도 존재합니다. 원소를 대입(덮어쓰기)이 아니라, 삽입(기존 자리의 원소는 뒤로 밀려남)하고 싶을때 사용합니다.

| inserter() | insert\_iterator 객체를 생성하고, 이 객체는 insert() 멤버 함수를 호출합니다 |
| back\_inserter() | back\_insert\_iterator 객체를 생성하고, 이 객체는 push\_back() 멤버 함수를 호출합니다 |
| front\_inserter() | front\_insert\_iterator 객체를 생성하고, 이 객체는 push\_front() 멤버 함수를 호출합니다 |

 이 때, inserter()는 모든 컨테이너가 사용할 수 있지만 back\_inserter()는 시퀀스 컨테이너만, front\_inserter()는 시퀀스 컨테이너중 deque와 list만 사용할 수 있습니다.

> insert\_iterator\_ex.cpp

```cpp
#include <iostream>
#include <algorithm>
#include <list>
#include <iterator>

using namespace std;

int main() {

	list<int> lt1 = { 1,2,3,4,5 };
	list<int> lt2 = { 10,20,30,40,50 };

	copy(lt2.begin(), lt2.end(), front_inserter<list<int>>(lt1));

	for (int i : lt1)
		cout << i << ' ';

	return 0;
}
```

> 50 40 30 20 10 1 2 3 4 5

 마지막으로, I/O 스트림 반복자가 있습니다. 알고리즘이 파일에서 읽고 쓰게 하고 싶을 때 주로 사용합니다.

`istream_iterator<T>` 는 T 자료형의 값을 스트림에서 읽고, `ostream_iterator<T>` 는 T 자료형의 값을 스트림에 쓸 수 있습니다.

> iostream\_iterator\_ex.cpp

```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <iterator>

using namespace std;

int main() {

	vector<int> v = { 1,2,3,4,5 };

	copy(v.begin(), v.end(), ostream_iterator<int>(cout, " "));
	return 0;
}
```

> 1 2 3 4 5

 내용을 더 추가하자면, +=과 -=같은, 임의 접근 반복자만이 가능한 연산을 다른 반복자에서도 사용할 수 있도록 해주는 함수가 존재합니다. advance(p, n)을 이용하면 p 반복자를 p + n의 위치로 이동시킵니다. distance(p1, p2) 함수는 두 반복자의 거리, p2-p1를 반환합니다.

 이로써 반복자의 강의가 끝났습니다. 미흡하거나 쓰지 않은 부분이 있지만, 더 많고 완벽한 정보를 원하신다면 C++ STL 문서를 참고해주세요. (영문)

> [https://www.cplusplus.com/reference/stl/](https://www.cplusplus.com/reference/stl/)