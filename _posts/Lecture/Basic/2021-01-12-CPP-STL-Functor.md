---
title: '[C++ STL 심화] 함수 객체, 함수자'
date: 2021-01-12 16:39:00 +0900
categories: [Lectures, Basic]
tags: [C++]
---

함수 객체 또는 함수자(functor)로 불리는 이것들은 C++의 operator() 연산자를 오버로딩한 클래스 객체입니다. 종류는 크게 2가지로 나눌 수 있으며, 각 세부 분류를 포함하면 다음과 같습니다.

| 일반 함수 객체 |   |
| --- | --- |
| 산술 연산 함수 객체 | +, -, \*, /, %, -(부호) 와 같은 산술 연산 |
| 비교 연산 조건자 | \==, !=, <, >, <=, >= 와 같은 비교 연산 |
| 논리 연산 조건자 | &&, \|\|, ! 와 같은 논리 연산 |

| 함수 어댑터 |   |
| --- | --- |
| 바인더 | 이항 함수 객체를 단항 함수 객체로 변환 |
| 부정자 | 함수 객체 조건자를 반대로 변환 |
| 함수 포인터 어댑터 | 함수 포인터를 STL이 요구하는 함수 객체로 변환 |
| 멤버 함수 포인터 어댑터 | 멤버 함수 포인터를 STL이 요구하는 함수 객체로 변환 |

 이 때, 조건자는 bool 타입을 반환하는 함수류(함수 객체, 함수, 함수 포인터) 입니다.

 다음의 예제는 함수류 내 3가지의 구현 방법을 설명합니다.

> **functor\_ex.cpp**

```cpp
#include <iostream>

using namespace std;

struct Object_Functor {
	const bool operator() (int a, int b) {
		return a < b;
	}
};

bool Function_Functor(int a, int b) {
	return a < b;
}

int main() {
	bool (*Pointer_Functor)(int, int) = Function_Functor;
	Object_Functor objFunctor;

	cout << objFunctor(20, 60) << endl;
	cout << Function_Functor(20, 60) << endl;
	cout << Pointer_Functor(20, 60) << endl;

	return 0;
}
```

 이 함수류에서 STL이 조건하는 조건자는 전부 함수 객체를 사용합니다. 또한, operator()를 오버로딩 할 때 const 키워드가 무조건 붙어있어야 합니다. 단순히 참/거짓을 판별하는 함수에서 실수로 값이 바뀌어버리면 문제가 발생할 수 있기 때문입니다. 더 정확하게는, 조건자가 변경되지 않을 것이라 예상하고 조건자를 내부적으로 복사하여 사용하는데, 이 때 값이 변경되어버리면 오류가 발생하기 때문입니다.

 단항 함수 객체의 경우 argument\_type(함수 인자 형식)와 result\_type(함수 리턴 형식)가 정의되어 있어야 하고, 이항 함수 객체는 first\_argument\_type(첫번째 인자 형식), second\_argument\_type(두번째 인자 형식), result\_type(리턴 형식)이  typedef를 이용하여 정의되어 있어야 합니다.

 어댑터(Adaptor)는 함수 객체를 변환할 때 위의 형식을 이용해 변환합니다. 하지만 위의 형식을 정의해 줄 필요는 없는 것이, STL에서 unary\_function과 binary\_function 이라는 클래스를 제공하기 때문에 함수 객체를 만들 때에는 이 클래스에서 상속하여 제작하면 됩니다.

>  **function\_object\_ex.cpp**

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

template<typename T>
struct Add {
	typedef T first_argument_Type;
	typedef T second_argument_Type;
	typedef T result_type;

	T operator()(const T& a, const T& b) {
		return a + b;
	}
};

template<typename T>
struct Add_Inherited : public binary_function<T, T, T> {
	T operator()(const T& a, const T& b) {
		return a + b;
	}
};
```

그럼 이제부터 STL에서 제공하는 함수자들을 자세하게 살펴보도록 합시다.

| 산술 연산 함수 객체 |   |
| --- | --- |
| plus<T> | 이항 + 연산 |
| minus<T> | 이항 \- 연산 |
| multiplies<T> | 이항 \* 연산 |
| divides<T> | 이항 / 연산 |
| modulus<T> | 이항 % 연산 |
| negate<T> | 단항 - 연산 (부호) |

함수 객체라는 개념은 어렵고 복잡해보여도, 실제 사용할 때에는 매우 간단합니다.

> **plus\_ex.cpp**

```cpp
#include <iostream>
#include <functional>

using namespace std;

int main() {
	plus<int> func;

	cout << func(1, 2) << endl;

	cout << func.operator()(10,20) << endl;

	cout << plus<int>()(1, 2) << endl;

	cout << plus<int>().operator()(10, 20) << endl;

	return 0;
}
```

다른 연산자들도 전부 사용 방법이 똑같기 때문에 생략하도록 하겠습니다.

| 비교 연산 조건자 |   |
| --- | --- |
| equal\_to<T> | 이항 == 연산 |
| not\_equal\_to<T> | 이항 !=  연산 |
| less<T> | 이항 <   연산 |
| less\_equal<T> | 이항 <= 연산 |
| greater<T> | 이항 >   연산 |
| greater\_equal<T> | 이항 >= 연산 |

조건자(Predicate)는 조건을 판단하는 거의 모든 알고리즘에 사용되며, 기본으로는 less<T>가 사용됩니다.

> **less\_ex.cpp**

```cpp
#include <iostream>
#include <functional>

using namespace std;

int main() {
	less<int> func;

	cout << func(1, 2) << endl;

	cout << func.operator()(10, 20) << endl;

	cout << less<int>()(1, 2) << endl;

	cout << less<int>().operator()(10, 20) << endl;

	return 0;
}
```

보이는 바와 같이 비교 연산 조건자 또한 산술 연산 함수 객체와 동일하게 사용됩니다.

| 논리 연산 조건자 |   |
| --- | --- |
| logical\_and<T> | 이항 && 연산 |
| logical\_or<T> | 이항 \|\|    연산 |
| logical\_not<T> | 이상 !    연산 |

논리 연산 조건자도 크게 다를 바 없이 위의 방법들처럼 사용하면 됩니다.

 이제 함수 어댑터들에 대해 살펴보도록 합시다. 바인더(binder)는 이항 삼수자를 단항 함수자로 변환하며, bind1st와 bind2nd가 존재합니다. 각각 '첫번째 인자'/'두번째 인자' 를 고정하여 단항 함수자로 변환합니다.

> **binder\_ex.cpp**

```cpp
#include <iostream>
#include <functional>

using namespace std;

int main() {
	binder1st<less<int>> binder = bind1st(less<int>(), 10);

	cout << binder(10) << " = " << less<int>()(10, 10) << endl;
	cout << binder(5) << " = " << less<int>()(10, 5) << endl;
	cout << binder(15) << " = " << less<int>()(10, 15) << endl;

	cout << bind1st(less<int>(), 10)(10) << " = " << less<int>()(10, 10) << endl;
	cout << bind1st(less<int>(), 10)(5) << " = " << less<int>()(10, 5) << endl;
	cout << bind1st(less<int>(), 10)(15) << " = " << less<int>()(10, 15) << endl;
}
```

예제는 less<int> 조건자의 첫번째 인자를 10으로 고정한 binder를 사용하였습니다. 여기서 bind1st를 bind2nd로 바꾸면 두번째 인자를 10으로 고정하는 binder가 됩니다.

 부정자(negator)는 조건을 반전(반대의 조건으로 변경)합니다. 단항 조건자의 not1, 이항 조건자의 not2가 존재합니다. not2(less<int>())(5, 10) 과 같은 방법으로 사용됩니다. 간단하기 때문에 예제는 첨부하지 않겠습니다.

 함수 포인터 어댑터는 일반 함수를 어댑터를 적용할 수 있는 함수 객체로 변환하는 ptr\_fun() 입니다. 직접 작성한 함수를 ptr\_fun() 에 매개변수로 넣으면 그 함수가 함수 객체처럼 동작할 수 있게 해줍니다. 간단한 함수 한두개로 굳이 함수 객체를 작성할 수고를 덜어 주는 함수죠.

 멤버 함수 포인터 어댑터는 멤버 함수를 함수 객체로 변환하여 알고리즘이 호출할 수 있도록 해줍니다. 객체로 멤버 함수를 호출하는 mem\_fun\_ref() 와 객체의 주소로 멤버 함수를 호출하는 mem\_fun() 가 존재합니다.

>  **mem\_fun\_ref\_ex.cpp**

```cpp
#include <iostream>
#include <vector>
#include <functional>
#include <algorithm>

using namespace std;

class Monster {
	int hp;
	int mp;
public:
	Monster(int _hp, int _mp) {
		this->hp = _hp;
		this->mp = _mp;
	}
	const void Info() {
		cout << "HP : " << hp << ", MP : " << mp << endl;
	}

};

int main() {
	vector<Monster> pools;
	pools.push_back(Monster(10, 20));
	pools.push_back(Monster(15, 30));
	pools.push_back(Monster(45, 20));

	for_each(pools.begin(), pools.end(), mem_fun_ref(&Monster::Info));

	return 0;
}
```

>  **mem\_fun\_ex.cpp**

```cpp
#include <iostream>
#include <vector>
#include <functional>
#include <algorithm>

using namespace std;

class Monster {
	int hp;
	int mp;
public:
	Monster(int _hp, int _mp) {
		this->hp = _hp;
		this->mp = _mp;
	}
	const void Info() {
		cout << "HP : " << hp << ", MP : " << mp << endl;
	}

};

int main() {
	vector<Monster*> pools;
	pools.push_back(new Monster(10, 20));
	pools.push_back(new Monster(15, 30));
	pools.push_back(new Monster(45, 20));

	for_each(pools.begin(), pools.end(), mem_fun(&Monster::Info));

	return 0;
}
```

 이것으로 C++ STL의 함수 객체에 대한 강좌는 끝나게 되었습니다. 그래서 함수자(Functor)는 왜 사용하나요? 알고리즘의 매개변수로 전달하여 같은 알고리즘 함수도 다르게 동작하게 하기 위해 주로 사용됩니다. 그냥 덧셈 뺄셈 하겠다고 함수자를 사용하는것은 절대 아니라는 거죠.