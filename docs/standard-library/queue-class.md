---
description: '자세히 알아보기: queue 클래스'
title: queue 클래스
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: b2b30e7a564fa1889d9adc2bb99e48ec1a623c25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340621"
---
# <a name="queue-class"></a>queue 클래스

일부 기본 컨테이너 형식의 앞과 뒤 요소에 대한 액세스를 제한하는 기능 제한을 제공하는 템플릿 컨테이너 어댑터 클래스입니다. 요소는 뒤에 추가하거나 앞에서 제거할 수 있으며 큐의 양쪽 끝에서 요소를 검사할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>매개 변수

*입력할*\
큐에 저장되는 요소 데이터 형식입니다.

*컨테이너*\
큐를 구현하는 데 사용된 기본 컨테이너의 형식입니다.

## <a name="remarks"></a>설명

`Type`Queue 개체의 첫 번째 템플릿 매개 변수에서 규정 된 클래스의 요소는 [value_type](#value_type) 와 동의어 이며, `Container` 두 번째 템플릿 매개 변수 규정 된 기본 컨테이너 클래스의 요소 형식과 일치 해야 합니다. 해당 `Type` 형식의 개체를 복사 하 고 해당 형식의 변수에 값을 할당할 수 있도록를 할당할 수 있어야 합니다.

큐에 적합 한 기본 컨테이너 클래스에는 [deque](../standard-library/deque-class.md) 및 [list](../standard-library/list-class.md),,, 및의 작업을 지 원하는 기타 시퀀스 컨테이너가 포함 됩니다 `front` `back` `push_back` `pop_front` . 기본 컨테이너 클래스는 제한된 시퀀스 컨테이너 멤버 함수 집합만 공용 인터페이스로 표시하는 컨테이너 어댑터 내에서 캡슐화되어 있습니다.

큐 개체는 클래스의 요소가 같음 비교할 수 있는 경우에만 같음 비교할 수 `Type` 있으며 클래스의 요소가 `Type` 보다 작음 비교할 수 있는 경우에만 보다 작음 비교 됩니다.

C++ 표준 라이브러리를 통해 정의되는 컨테이너 어댑터에는 stack, queue, priority_queue의 세 가지 형식이 있습니다. 각 어댑터는 일부 기본 컨테이너 클래스의 기능을 제한하여 표준 데이터 구조에 대해 정확하게 제어되는 인터페이스를 제공합니다.

- [Stack 클래스](../standard-library/stack-class.md) 는 LIFO (선입 last out) 데이터 구조를 지원 합니다. 쌓여 있는 접시 더미의 예로 이해할 수 있습니다. 요소(접시)는 기본 컨테이너의 끝에 있는 마지막 요소인 스택의 맨 위에서만 삽입하거나 검사하거나 제거할 수 있습니다. 맨 위 요소로만 액세스를 제한하는 것이 stack 클래스를 사용하는 이유입니다.

- queue 클래스는 FIFO(선입선출) 데이터 구조를 지원합니다. 은행 창구 직원을 만나려고 줄 서 있는 사람들의 예로 이해할 수 있습니다. 요소(사람)는 줄의 뒤에 추가될 수 있고 줄의 앞에서 제거됩니다. 줄의 앞과 뒤는 모두 검사할 수 있습니다. queue 클래스를 사용하는 이유는 이 방식으로 앞과 뒤의 요소만 액세스할 수 있기 때문입니다.

- [priority_queue 클래스](../standard-library/priority-queue-class.md)는 가장 큰 요소가 항상 최상위 위치에 있도록 요소를 정렬합니다. 이 클래스는 요소의 삽입과 최상위 요소의 검사 및 제거를 지원합니다. 나이, 키 또는 기타 조건을 기준으로 정렬된 줄을 선 사람들의 예로 이해할 수 있습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[큐](#queue)|비어 있거나 기본 컨테이너 개체의 복사본인 `queue`을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[container_type](#container_type)|`queue`에서 조정할 기본 컨테이너를 제공하는 형식입니다.|
|[size_type](#size_type)|`queue`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|`queue`에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[뒤로](#back)|`queue` 뒤에 마지막으로 가장 최근에 추가된 요소에 대한 참조를 반환합니다.|
|[empty](#empty)|`queue`이 비어 있는지를 테스트합니다.|
|[앞뒤](#front)|`queue` 앞의 첫 번째 요소에 대한 참조를 반환합니다.|
|[창을](#pop)|`queue` 앞에서 요소를 제거합니다.|
|[push](#push)|`queue` 뒤에 요소를 추가합니다.다.|
|[size](#size)|`queue`에 있는 요소 수를 반환합니다.|

## <a name="back"></a><a name="back"></a> 뒤로

queue 뒤에 마지막으로 가장 최근에 추가된 요소에 대한 참조를 반환합니다.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>반환 값

queue의 마지막 요소입니다. queue가 비어 있으면 반환 값이 정의되지 않습니다.

### <a name="remarks"></a>설명

`back`의 반환 값이 `const_reference`에 할당된 경우 queue 개체를 수정할 수 없습니다. 의 반환 값이에 할당 된 경우에는 `back` `reference` queue 개체를 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 queue의 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a><a name="container_type"></a> container_type

조정할 기본 컨테이너를 제공하는 형식입니다.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Container`의 동의어입니다. 2개 C++ 표준 라이브러리 시퀀스 컨테이너 클래스(list 클래스 및 기본 deque 클래스)는 queue 개체의 기본 컨테이너로 사용하기 위한 요구 사항을 충족합니다. 이 요구 사항을 충족하는 사용자 정의 형식도 사용할 수 있습니다.

`Container`에 대한 자세한 내용은 [queue 클래스](../standard-library/queue-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`container_type`을 선언하고 사용하는 방법에 대한 예제는 [queue](#queue)의 예제를 참조하세요.

## <a name="empty"></a><a name="empty"></a> 비우려면

queue가 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 큐가 비어 있으면이 고, 그렇지 않으면입니다. **`false`** 큐가 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a><a name="front"></a> 앞뒤

queue 앞의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>반환 값

큐의 첫 번째 요소입니다. queue가 비어 있으면 반환 값이 정의되지 않습니다.

### <a name="remarks"></a>설명

`front`의 반환 값이 `const_reference`에 할당된 경우 queue 개체를 수정할 수 없습니다. 의 반환 값이에 할당 된 경우에는 `front` `reference` queue 개체를 수정할 수 있습니다.

멤버 함수는가 `reference` 비어 있지 않아야 하는 제어 되는 시퀀스의 첫 번째 요소에 대 한를 반환 합니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 queue의 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a><a name="pop"></a> 창을

queue 앞에서 요소를 제거합니다.

```cpp
void pop();
```

### <a name="remarks"></a>설명

구성원 함수를 적용하려면 queue가 비어 있지 않아야 합니다. queue의 맨 위 위치에는 가장 최근에 추가한 요소가 배치되며, 이 요소가 컨테이너 끝의 마지막 요소가 됩니다.

### <a name="example"></a>예제

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a><a name="push"></a> 누르기

queue 뒤에 요소를 추가합니다.다.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
queue 끝에 추가되는 요소입니다.

### <a name="remarks"></a>설명

queue의 뒤 위치에는 가장 최근에 추가한 요소가 배치되며, 이 요소가 컨테이너 끝의 마지막 요소가 됩니다.

### <a name="example"></a>예제

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a><a name="queue"></a> 큐

비어 있거나 기본 컨테이너 개체의 복사본인 queue를 생성합니다.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
**`const`** 생성 된 큐를 복사 해야 하는 컨테이너입니다.

### <a name="remarks"></a>설명

queue의 기본 컨테이너는 deque입니다. list는 기본 컨테이너로 지정할 수 있지만 vector는 필수 `pop_front` 구성원 함수를 포함하지 않으므로 기본 컨테이너로 지정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a><a name="size"></a> 크기가

queue에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

queue의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

queue에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>설명

이 형식은 queue에 의해 조정되는 기본 컨테이너의 `size_type`과 동일한 의미입니다.

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [queue::front](#front)의 예제를 참조하세요.

## <a name="value_type"></a><a name="value_type"></a> value_type

queue에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>설명

이 형식은 queue에 의해 조정되는 기본 컨테이너의 `value_type`과 동일한 의미입니다.

### <a name="example"></a>예제

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
