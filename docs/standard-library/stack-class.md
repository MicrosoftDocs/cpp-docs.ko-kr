---
description: '자세한 정보: stack 클래스'
title: stack 클래스
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: 6caec52124b247e405299d45f55a86c20f991abc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153865"
---
# <a name="stack-class"></a>stack 클래스

최근에 일부 기본 컨테이너 형식에 추가된 요소로만 액세스를 제한하는 템플릿 컨테이너 어댑터 클래스입니다. stack 클래스는 컨테이너에서 스택 작업만 수행되고 있음을 명확하게 해야 하는 경우에 사용됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>매개 변수

*입력할*\
스택에 저장되는 요소 데이터 형식입니다.

*컨테이너*\
스택을 구현하는 데 사용된 기본 컨테이너의 형식입니다. 기본값은 클래스 `deque` *\<Type>* 입니다.

## <a name="remarks"></a>설명

`Type`Stack 개체의 첫 번째 템플릿 매개 변수에서 규정 된 클래스의 요소는 [value_type](#value_type) 와 동의어 이며, `Container` 두 번째 템플릿 매개 변수 규정 된 기본 컨테이너 클래스의 요소 형식과 일치 해야 합니다. 해당 `Type` 형식의 개체를 복사 하 고 해당 형식의 변수에 값을 할당할 수 있도록를 할당할 수 있어야 합니다.

스택에 적합 한 기본 컨테이너 클래스에는 [deque](../standard-library/deque-class.md), [list 클래스](../standard-library/list-class.md)및 [vector 클래스](../standard-library/vector-class.md),, 및의 작업을 지 원하는 기타 시퀀스 컨테이너가 포함 됩니다 `back` `push_back` `pop_back` . 기본 컨테이너 클래스는 제한된 시퀀스 컨테이너 멤버 함수 집합만 공용 인터페이스로 표시하는 컨테이너 어댑터 내에서 캡슐화되어 있습니다.

스택 개체는 클래스의 요소가 같음 비교할 수 있는 경우에만 같음 비교할 수 `Type` 있으며 클래스의 요소가 보다 작음 비교할 수 있는 경우에만 보다 작음 `Type` 입니다.

- stack 클래스는 LIFO(후입선출) 데이터 구조를 지원합니다. 쌓여 있는 접시 더미의 예로 이해할 수 있습니다. 요소(접시)는 기본 컨테이너의 끝에 있는 마지막 요소인 스택의 맨 위에서만 삽입하거나 검사하거나 제거할 수 있습니다. 맨 위 요소로만 액세스를 제한하는 것이 stack 클래스를 사용하는 이유입니다.

- [queue 클래스](../standard-library/queue-class.md)는 FIFO(선입선출) 데이터 구조를 지원합니다. 은행 창구 직원을 만나려고 줄 서 있는 사람들의 예로 이해할 수 있습니다. 요소(사람)는 줄의 뒤에 추가될 수 있고 줄의 앞에서 제거됩니다. 줄의 앞과 뒤는 모두 검사할 수 있습니다. queue 클래스를 사용하는 이유는 이 방식으로 앞과 뒤의 요소만 액세스할 수 있기 때문입니다.

- [priority_queue 클래스](../standard-library/priority-queue-class.md)는 가장 큰 요소가 항상 최상위 위치에 있도록 요소를 정렬합니다. 이 클래스는 요소의 삽입과 최상위 요소의 검사 및 제거를 지원합니다. 나이, 키 또는 기타 조건을 기준으로 정렬된 줄을 선 사람들의 예로 이해할 수 있습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[겹치기](#stack)|비어 있거나 기본 컨테이너 개체의 복사본인 `stack`을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[container_type](#container_type)|`stack`에서 조정할 기본 컨테이너를 제공하는 형식입니다.|
|[size_type](#size_type)|`stack`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|`stack`에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[empty](#empty)|`stack`이 비어 있는지를 테스트합니다.|
|[창을](#pop)|`stack`의 맨 위에 있는 요소를 제거합니다.|
|[push](#push)|`stack`의 맨 위에 요소를 추가합니다.|
|[size](#size)|`stack`에 있는 요소 수를 반환합니다.|
|[top](#top)|`stack`의 맨 위에 있는 요소에 대한 참조를 반환합니다.|

## <a name="container_type"></a><a name="container_type"></a> container_type

조정할 기본 컨테이너를 제공하는 형식입니다.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Container`의 동의어입니다. 3개 C++ 표준 라이브러리 시퀀스 컨테이너 클래스(vector 클래스, list 클래스 및 기본 클래스인 deque)는 모두 stack 개체의 기본 컨테이너로 사용하기 위한 요구 사항을 충족합니다. 이러한 요구 사항을 충족하는 사용자 정의 형식도 사용할 수 있습니다.

`Container`에 대한 자세한 내용은 [stack 클래스](../standard-library/stack-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`container_type`을 선언하고 사용하는 방법에 대한 예제는 [stack::stack](#stack)의 예제를 참조하세요.

## <a name="empty"></a><a name="empty"></a> 비우려면

스택이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 스택이 비어 있으면이 고, 그렇지 않으면입니다. **`false`** 스택이 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a><a name="pop"></a> 창을

stack의 가장 윗부분의 요소를 제거합니다.

```cpp
void pop();
```

### <a name="remarks"></a>설명

구성원 함수를 적용하려면 스택이 비어 있지 않아야 합니다. 스택 맨 위 위치에는 가장 최근에 추가한 요소가 배치되며, 이 요소가 컨테이너 끝의 마지막 요소가 됩니다.

### <a name="example"></a>예제

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a><a name="push"></a> 누르기

스택의 맨 위에 요소를 추가 합니다.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
스택의 맨 위에 추가되는 요소입니다.

### <a name="remarks"></a>설명

스택 맨 위 위치에는 가장 최근에 추가한 요소가 배치되며, 이 요소가 컨테이너 끝의 마지막 요소가 됩니다.

### <a name="example"></a>예제

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a><a name="size"></a> 크기가

스택의 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

스택의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

스택에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>설명

이 형식은 스택에 의해 조정되는 기본 컨테이너의 `size_type`과 동일한 의미입니다.

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="stack"></a><a name="stack"></a> 겹치기

비어 있거나 기본 컨테이너 개체의 복사본인 스택을 생성합니다.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
생성된 스택이 복사본이 되는 컨테이너입니다.

### <a name="example"></a>예제

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a><a name="top"></a> 맨 위로

stack의 가장 윗부분의 요소에 대한 참조를 반환합니다.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>반환 값

스택의 맨 위에 있는 컨테이너의 마지막 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

구성원 함수를 적용하려면 스택이 비어 있지 않아야 합니다. 스택 맨 위 위치에는 가장 최근에 추가한 요소가 배치되며, 이 요소가 컨테이너 끝의 마지막 요소가 됩니다.

의 반환 값이에 할당 된 경우에는 `top` `const_reference` 스택 개체를 수정할 수 없습니다. 의 반환 값이에 `top` 할당 되는 경우 `reference` 스택 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a><a name="value_type"></a> value_type

스택에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>설명

이 형식은 스택에 의해 조정되는 기본 컨테이너의 `value_type`과 동일한 의미입니다.

### <a name="example"></a>예제

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
