---
description: Priority_queue 클래스에 대해 자세히 알아보세요.
title: priority_queue 클래스
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
ms.openlocfilehash: 38b8411d20df5275997406b72e050fde803df0fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340647"
---
# <a name="priority_queue-class"></a>priority_queue 클래스

항상 가장 크거나 우선 순위가 가장 높은 일부 기본 컨테이너 형식의 최상위 요소에 대한 액세스를 제한하는 기능 제한을 제공하는 템플릿 컨테이너 어댑터 클래스입니다. priority_queue에 새 요소를 추가하고 priority_queue의 최상위 요소를 검사하거나 제거할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>매개 변수

*입력할*\
priority_queue에 저장되는 요소 데이터 형식입니다.

*컨테이너*\
priority_queue를 구현하는 데 사용된 기본 컨테이너의 형식입니다.

*과*\
두 요소값을 정렬 키로 비교하여 priority_queue에서 상대적인 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다. 이 인수는 선택 사항이며 기본값은 이진 조건자 `less<typename Container::value_type>`입니다.

## <a name="remarks"></a>설명

`Type`Queue 개체의 첫 번째 템플릿 매개 변수에서 규정 된 클래스의 요소는 [value_type](#value_type) 와 동의어 이며, `Container` 두 번째 템플릿 매개 변수 규정 된 기본 컨테이너 클래스의 요소 형식과 일치 해야 합니다. 해당 `Type` 형식의 개체를 복사 하 고 해당 형식의 변수에 값을 할당할 수 있도록를 할당할 수 있어야 합니다.

Priority_queue는 클래스의 저장 된 함수 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다 `Traits` . 일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다.

priority_deque에 적합한 기본 컨테이너 클래스에는 `front`, `push_back`, `pop_back` 및 임의 액세스 반복기의 작업을 지원하는 [deque 클래스](../standard-library/deque-class.md) 및 기본 [vector 클래스](../standard-library/vector-class.md) 또는 기타 시퀀스 컨테이너가 포함됩니다. 기본 컨테이너 클래스는 제한된 시퀀스 컨테이너 멤버 함수 집합만 공용 인터페이스로 표시하는 컨테이너 어댑터 내에서 캡슐화되어 있습니다.

`priority_queue`에 요소를 추가하고 priority_deque에서 요소를 제거하는 과정은 복잡한 로그 작업입니다. `priority_queue`에서 요소에 액세스하는 과정은 복잡한 상수 작업입니다.

C++ 표준 라이브러리를 통해 정의되는 컨테이너 어댑터에는 stack, queue, priority_queue의 세 가지 형식이 있습니다. 각 어댑터는 일부 기본 컨테이너 클래스의 기능을 제한하여 표준 데이터 구조에 대해 정확하게 제어되는 인터페이스를 제공합니다.

- [Stack 클래스](../standard-library/stack-class.md) 는 LIFO (선입 last out) 데이터 구조를 지원 합니다. 쌓여 있는 접시 더미의 예로 이해할 수 있습니다. 요소(접시)는 기본 컨테이너의 끝에 있는 마지막 요소인 스택의 맨 위에서만 삽입하거나 검사하거나 제거할 수 있습니다. 맨 위 요소로만 액세스를 제한하는 것이 stack 클래스를 사용하는 이유입니다.

- [Queue 클래스](../standard-library/queue-class.md) 는 FIFO (선입 선출) 데이터 구조를 지원 합니다. 은행 창구 직원을 만나려고 줄 서 있는 사람들의 예로 이해할 수 있습니다. 요소(사람)는 줄의 뒤에 추가될 수 있고 줄의 앞에서 제거됩니다. 줄의 앞과 뒤는 모두 검사할 수 있습니다. queue 클래스를 사용하는 이유는 이 방식으로 앞과 뒤의 요소만 액세스할 수 있기 때문입니다.

- priority_queue 클래스는 가장 큰 요소가 항상 최상위 위치에 있도록 요소를 정렬합니다. 이 클래스는 요소의 삽입과 최상위 요소의 검사 및 제거를 지원합니다. 나이, 키 또는 기타 조건을 기준으로 정렬된 줄을 선 사람들의 예로 이해할 수 있습니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[priority_queue](#priority_queue)|비어 있거나 기본 컨테이너 개체 또는 다른 `priority_queue` 범위의 복사본인 `priority_queue`를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[container_type](#container_type)|`priority_queue`에서 조정할 기본 컨테이너를 제공하는 형식입니다.|
|[size_type](#size_type)|`priority_queue`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|`priority_queue`에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[empty](#empty)|`priority_queue`이 비어 있는지를 테스트합니다.|
|[창을](#pop)|`priority_queue`의 가장 큰 요소를 최상위 위치에서 제거합니다.|
|[push](#push)|operator<의 요소 우선 순위에 따라 priority_queue에 요소를 추가합니다.|
|[size](#size)|`priority_queue`에 있는 요소 수를 반환합니다.|
|[top](#top)|`priority_queue`의 최상위 위치에 있는 가장 큰 요소에 대한 const 참조를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<queue>

**네임스페이스:** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a> priority_queue:: container_type

조정할 기본 컨테이너를 제공하는 형식입니다.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Container`의 동의어입니다. C++ 표준 라이브러리 시퀀스 컨테이너 클래스 `deque` 및 기본 클래스인 `vector`는 priority_queue 개체의 기본 컨테이너로 사용하기 위한 요구 사항을 충족합니다. 이 요구 사항을 충족하는 사용자 정의 형식도 사용할 수 있습니다.

`Container`에 대한 자세한 내용은 [priority_queue 클래스](../standard-library/priority-queue-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`container_type`을 선언하고 사용하는 방법에 대한 예제는 [priority_queue](#priority_queue)의 예제를 참조하세요.

## <a name="priority_queueempty"></a><a name="empty"></a> priority_queue:: empty

priority_queue가 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** priority_queue 비어 있으면이 고, 그렇지 않으면입니다. **`false`** priority_queue 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="priority_queuepop"></a><a name="pop"></a> priority_queue::p op

priority_queue의 가장 큰 요소를 최상위 위치에서 제거합니다.

```cpp
void pop();
```

### <a name="remarks"></a>설명

멤버 함수를 적용하려면 priority_queue는 비어 있지 않아야 합니다. priority_queue의 최상위 위치에는 항상 컨테이너에서 가장 큰 요소가 있습니다.

### <a name="example"></a>예제

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a> priority_queue::p riority_queue

비어 있거나 기본 컨테이너 개체 또는 다른 priority_queue 범위의 복사본인 priority_queue를 생성합니다.

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>매개 변수

*_comp*\
priority_queue의 요소 순서를 지정하는 데 사용되는 **constTraits** 형식의 비교 함수로, 기본 컨테이너의 비교 함수를 기본값으로 사용합니다.

*_Cont*\
생성된 priority_queue가 복사본이 되는 기본 컨테이너입니다.

*오른쪽*\
생성된 set가 복사본으로 지정될 priority_queue입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

### <a name="remarks"></a>설명

처음 세 생성자는 각각 빈 초기 priority_queue을 지정 하 고, 두 번째 생성자는 요소의 순서를 설정 하는 데 사용할 비교 함수 ()의 형식을 지정 하며, 세 번째 생성자 `comp` `container_type` 는 사용할 ()을 명시적으로 지정 합니다 `_Cont` . 키워드는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 생성자는 priority_queue *오른쪽* 의 복사본을 지정 합니다.

마지막 세 생성자는 \[ 일부 컨테이너의 *범위를* *먼저* 복사 하 고 값을 사용 하 여 및 클래스의 비교 함수 형식을 지정 하는 내 높아집니다를 통해 priority_queue를 초기화 합니다 `Traits` `container_type` .

### <a name="example"></a>예제

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="priority_queuepush"></a><a name="push"></a> priority_queue::p 밀어넣기

operator<의 요소 우선 순위에 따라 priority_queue에 요소를 추가합니다.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
priority_queue의 맨 위에 추가되는 개체입니다.

### <a name="remarks"></a>설명

priority_queue의 최상위 위치에는 컨테이너에서 가장 큰 요소가 있습니다.

### <a name="example"></a>예제

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuesize"></a><a name="size"></a> priority_queue:: size

priority_queue에 있는 요소의 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

priority_queue의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="priority_queuesize_type"></a><a name="size_type"></a> priority_queue:: size_type

priority_queue에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>설명

이 형식은 priority_queue에 의해 조정되는 기본 컨테이너의 `size_type`과 동일한 의미입니다.

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="priority_queuetop"></a><a name="top"></a> priority_queue:: top

가장 큰 요소에 대한 const 참조를 priority_queue 위쪽에 반환합니다.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>반환 값

함수, priority_queue 개체에 의해 결정 되는 가장 큰 요소에 대 한 참조 `Traits` 입니다.

### <a name="remarks"></a>설명

멤버 함수를 적용하려면 priority_queue는 비어 있지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuevalue_type"></a><a name="value_type"></a> priority_queue:: value_type

priority_queue에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>설명

이 형식은 priority_queue에 의해 조정되는 기본 컨테이너의 `value_type`과 동일한 의미입니다.

### <a name="example"></a>예제

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
