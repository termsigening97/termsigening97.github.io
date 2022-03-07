---
title: '[C++ STL] 벡터(Vector)'
date: 2020-11-28 01:02:00 +0900
categories: [Lectures, Basic]
tags: [C++]
---

벡터(Vector)는 STL에서 컨테이너에 속합니다. 컨테이너는 같은 타입을 저장, 관리하기 위해 만들어진 클래스입니다. 그 중 벡터는 표준 시퀀스 컨테이너(Standard Sequence Container) 에 속하는데, 자신만의 삽입 순서를 가지는 컨테이너라는 뜻입니다. 무슨 말이냐면, 배열처럼 삽입되는 순서에 따라 원소의 위치가 결정되고 바뀌지 않습니다.

또한, 벡터는 배열 기반 컨테이너입니다. 배열처럼 메모리(RAM) 공간에 모든 원소가 이어져 있다는 뜻이죠. 이와 다르게는 노드 기반 컨테이너가 있는데, 컨테이너 내부의 원소들이 메모리의 무작위 위치에 저장되어 있습니다. 대신, 원소가 자신의 값과 다음 원소의 주소를 가지고 있습니다.

> vector_Ex01.cpp

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
	int N;
    
    	cin >> N;
    
	vector<int> V(N);

	for (int i = 0; i < V.size(); i++) {
		V[i] = i + 1;
	}

	for (int i = 0; i < V.size(); i++) {
		cout << V[i] << ' ';
	}

	return 0;
}
```

위의 코드는 1부터 N까지의 숫자를 벡터에 저장하고 출력하는 예제입니다. 벡터는 `vector<자료형> 이름;` 과 같은 방법으로 선언합니다. 선언이 끝나면, 우리가 평소에 사용하던 배열과 똑같이 사용할 수 있습니다. 대신, 몇몇 함수들이 추가되어 훨씬 사용하기 편하고, 기능이 많습니다.

`vector<자료형> 이름(크기);` 로 크기를 지정해 주면, 배열과 같이 미리 크기를 선언해줄 수 있습니다. 이 방법을 이용하면, 선언을 제외하고는 C언어의 배열과 완전히 똑같이 사용할 수 있습니다. 차이점은, 크기에 변수를 넣어 동적 배열로 사용할 수 있다는 점입니다. 또한 `V.size()` 를 사용하면 매우 편리하게 벡터의 크기를 알 수 있습니다.

> **생성자**

| vector v | v는 비어있는 벡터 |  |
| vector v(n) | v는 기본값으로 초기화된 n 크기의 벡터 |  |
| vector v(n, x) | v는 x로 초기화된 n 크기의 벡터 |  |
| vector v(v2) | v는 v2 벡터를 복사한 벡터 |  |
| vector v(b, e) | v는 반복자 구간 \[b, e)로 초기화된 벡터 |  |

생성자는 변수를 선언할 때 자동으로 이루어지는 작업입니다. 다음의 예제를 따라해서 결과를 확인해봅시다.

> **vector\_Ex02.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
	int N;

	cin >> N;

	vector<int> V(N, 3);
	vector<int> V2(V);

	for (int i = 0; i < V.size(); i++) {
		cout << V2[i] << ' ';
	}

	return 0;
}
```

> **멤버 함수**

| v.assign(n, x) | v에 x값으로 n개의 원소를 할당한다 |  |
| v.begin(), v.end() | v의 반복자 처음, 끝을 나타낸다 |  |
| v.size() | v의 크기를 나타낸다 |  |
| v.empty() | v가 비었는지 나타낸다 |  |
| v.clear() | v의 모든 원소를 제거한다 |  |
| v.front(), v.back() | v의 첫번째/마지막 원소를 참조한다 |  |
| v.insert(p, n, x) | p가 가리키는 위치에 n개의 x값을 삽입한다 |  |
| v.resize(n) | v의 크기를 n으로 변경한다 |  |
| v.resize(n, x) | x를 넣을시 변경 후 확장된 값을 x로 초기화한다 |  |
| v.capacity() | v가 할당된 공간의 크기를 나타낸다 |  |
| v.reserve(n) | v에 n개의 원소를 저장할 공간을 예약한다 |  |
| v.pop\_back() | v의 마지막 원소를 제거한다 |  |
| v.push\_back(x) | v의 마지막에 원소 x를 추가한다 |  |
| v.swap(v2) | v와 v2를 교환한다 |  |

멤버 함수는 만들어진 벡터에 멤버 연산자인 `.*` 을 이용해서 호출할 수 있습니다. 클래스의 개념을 알고 있다면 무엇인지 바로 알 수 있을겁니다. 함수를 직접 사용해보며, 결과를 확인합시다.

> **vector\_Ex03.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {

	vector<int> V(3);
	
	V.resize(6);

	for (int i = 0; i < V.size(); i++)
		cout << V[i];

	cout << endl;

	V.pop_back();
	V.pop_back();
	V.push_back(3);
	V.push_back(6);

	for (int i = 0; i < V.size(); i++)
		cout << V[i];

	cout << endl;

	return 0;
}
```

벡터끼리 ==, !=, <, >와 같은 비교 연산자를 사용할 수 있습니다. ==같은 경우는 모든 원소가 같은지 확인하고, <, >와 같은 대소 비교는 문자열 비교와 같이 사전 순서대로 비교합니다.

> **vector\_Ex04.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {

	vector<int> V1(5);
	vector<int> V2(5);
	for (int i = 0; i < 5; i++) {
		V1[i] = i;
		V2[i] = i + 1;
	}

	cout << "V1 : ";
	for (int i = 0; i < V1.size(); i++)
		cout << V1[i] << ' ';
	cout << "\nV2 : ";
	for (int i = 0; i < V2.size(); i++)
		cout << V2[i] << ' ';
	

	cout << "\nV1 == V2 : " << (V1 == V2) << endl;
	cout << "V1 > V2 : " << (V1 > V2) << endl;
	cout << "V1 <= V2 : " << (V1 <= V2) << endl;

	return 0;
}
```

> **N차원 벡터**

2차원 배열이 정확히 무엇인지 기억하시나요? 배열 안의 각 원소에 배열이 있다면 이것은 2차원 배열입니다. 벡터도 똑같습니다. 벡터 안에 벡터가 들어있는 방식으로 2차원 벡터를 만들 수 있습니다.

> **vector\_Ex05.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
	vector<vector<int>> V(5, vector<int>(10, 2));

	for (vector<vector<int>>::size_type i = 0; i < V.size(); i++) {
		for (vector<int>::size_type j = 0; j < V[i].size(); j++) {
			cout << V[i][j] << ' ';
		}
		cout << endl;
	}

	return 0;
}
```

벡터를 초기화 할때, 벡터\<벡터\> 타입인 바깥쪽 벡터를 5개 생성하고, 안쪽 값은 벡터 타입인 안쪽 벡터를 10개 생성해줬습니다. 벡터 안에 벡터가 있는 것이니, 값 초기화를 벡터로 한다는 것이 이해가 되시나요? 그리고 이제, 안쪽 벡터의 원소는 전부 2로 초기화해주었습니다.

그런데 출력문을 보니 size\_type 이라는 이상한 타입이 있네요. 하지만 그냥 int로 해주어도 잘 작동합니다. 그렇다면 왜 size\_type가 있는 걸까요? 이것은 C++의 가장 큰 특징중 하나인 라이브러리의 강력한 재사용성입니다. 모든 컨테이너에는 size\_type가 있기 때문에 이것을 이용하면 함수 하나에서 모든 타입의 컨테이너들의 처리가 가능하게 해 줍니다. 정확한 사용 방법은 후에 template 라는 C++의 기능을 학습하며 공부하게 될 것입니다.

아래 코드는 위 코드와 동일한 기능을 합니다. 대신 C++의 `auto` 이용해서 코드를 훨씬 간단하게 작성할 수 있죠. 여기서 `auto` 는 자료형을 확실히 유추할 수 있을때만 사용할 수 있으며 컴파일 시간에 해당하는 타입으로 치환됩니다.

> **vector\_Ex05_1.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
	vector<vector<int>> V(5, vector<int>(10, 2));

	for (auto i = 0; i < V.size(); i++) {
		for (auto j = 0; j < V[i].size(); j++) {
			cout << V[i][j] << ' ';
		}
		cout << endl;
	}

	return 0;
}
```

자, 이제 벡터가 끝난 것 같지만 아직 하나 남았습니다. 벡터는 가변 배열이라는 것을 알고 계시죠? 그렇기 때문에 N차원 벡터의 원소들은 전부 **각기 다른 길이의 벡터**들을 담을 수 있습니다. 한번 예제를 보고 학습해봅시다.

> **vector\_Ex06.cpp**

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
	vector<vector<int>> V;

	vector<int> v1(5, 1);
	vector<int> v2(3, 2);
	vector<int> v3(7, 3);
	vector<int> v4(1, 4);
	vector<int> v5(9, 5);

	V.push_back(v1);
	V.push_back(v2);
	V.push_back(v3);
	V.push_back(v4);
	V.push_back(v5);

	for (size_t i = 0; i < V.size(); i++) {
		for (size_t j = 0; j < V[i].size(); j++) {
			cout << V[i][j] << ' ';
		}
		cout << endl;
	}

	return 0;
}
```

2차원 벡터에 벡터를 push\_back 해줌으로써 이제 원소마다 다른 길이인 벡터가 생겼습니다! 이런 배열을 Jagged Array라고 합니다.

어, 그런데 이번엔 size\_t가 있네요. 대체 헷갈리게 왜이러시는거죠?

그 이유는 v.size() 함수가 int가 아닌, size\_t 타입을 반환하기 때문에 해준 것입니다. 그리고 size\_t 타입은 unsigned int가 typedef로 이름만 바뀌어있는 것입니다. unsigned int는, "부호 없는" int타입이라는 뜻으로 원래 int의 범위가 약 -20억~+20억 이었다면 이 타입은 0 ~ 40억 까지가 범위가 됩니다. 마이너스 크기는 없기 때문이죠. 같은 int지만 약간 다르기때문에 int 대신 size\_t 타입을 사용하는것을 습관화하는것이 좋습니다.

마지막으로, 벡터의 중요한 특성을 알려드리겠습니다. 벡터는 길이가 자유자재로 변하는 가변 배열이라고 하였습니다. 하지만, 듣기에는 좋아 보이는 이 특성이 사실 벡터의 허점이기도 합니다. 벡터의 현재 크기보다 더 많은 원소를 할당하려고 하면, 메모리를 재할당해야 합니다. 그리고, 벡터가 원래 가지고 있던 모든 원소들을 다 복사해서 새로 할당된 메모리에 저장하고, 원래의 메모리는 해제합니다. 이 공간의 크기는 capacity() 함수로 확인할 수 있고, reserve() 함수로 할당할 수 있습니다.

여기까지 전부 이해했다면 벡터는 이제 끝났습니다! 다음 STL도 공부해봅시다.