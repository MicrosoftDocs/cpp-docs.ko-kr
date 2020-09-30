---
title: priority_queue(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: fd87c39db279fb70d5c5b5f20e583251dc519755
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502399"
---
# <a name="priority_queue-stlclr"></a>priority_queue(STL/CLR)

템플릿 클래스는 액세스가 제한 된 다양 한 길이의 정렬 된 요소 시퀀스를 제어 하는 개체를 설명 합니다. 컨테이너 어댑터를 사용 하 여 `priority_queue` 기본 컨테이너를 우선 순위 큐로 관리 합니다.

아래 설명에서 후자가 `GValue` ref 형식이 아닌 경우는 *값* 과 같습니다 `Value^` . 마찬가지로, `GContainer` 후자가 ref 형식이 아닌 경우는 *컨테이너* 와 동일 합니다 `Container^` .

## <a name="syntax"></a>구문

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>매개 변수

*값*<br/>
제어되는 시퀀스의 요소 형식입니다.

*컨테이너*<br/>
기본 컨테이너의 형식입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/queue>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|형식 정의|설명|
|---------------------|-----------------|
|[priority_queue::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[priority_queue::container_type(STL/CLR)](#container_type)|기본 컨테이너의 형식입니다.|
|[priority_queue::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[priority_queue::generic_container(STL/CLR)](#generic_container)|컨테이너 어댑터에 대 한 제네릭 인터페이스의 형식입니다.|
|[priority_queue::generic_value(STL/CLR)](#generic_value)|컨테이너 어댑터의 제네릭 인터페이스에 대 한 요소의 형식입니다.|
|[priority_queue::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|
|[priority_queue::size_type(STL/CLR)](#size_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[priority_queue::value_compare(STL/CLR)](#value_compare)|두 요소에 대 한 순서 지정 대리자입니다.|
|[priority_queue::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[priority_queue::assign(STL/CLR)](#assign)|모든 요소를 바꿉니다.|
|[priority_queue::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|
|[priority_queue::get_container(STL/CLR)](#get_container)|기본 컨테이너에 액세스합니다.|
|[priority_queue::pop(STL/CLR)](#pop)|H물리학 est 우선 순위 요소를 제거 합니다.|
|[priority_queue::priority_queue(STL/CLR)](#priority_queue)|컨테이너 개체를 만듭니다.|
|[priority_queue::push(STL/CLR)](#push)|새 요소를 추가 합니다.|
|[priority_queue::size(STL/CLR)](#size)|요소 수를 계산합니다.|
|[priority_queue::top(STL/CLR)](#top)|우선 순위가 가장 높은 요소에 액세스 합니다.|
|[priority_queue::to_array(STL/CLR)](#to_array)|제어 되는 시퀀스를 새 배열에 복사 합니다.|
|[priority_queue::value_comp(STL/CLR)](#value_comp)|두 요소의 순서 지정 대리자를 복사합니다.|

|속성|설명|
|--------------|-----------------|
|[priority_queue::top_item(STL/CLR)](#top_item)|우선 순위가 가장 높은 요소에 액세스 합니다.|

|연산자|설명|
|--------------|-----------------|
|[priority_queue::operator=(STL/CLR)](#op_as)|제어되는 시퀀스를 바꿉니다.|

## <a name="interfaces"></a>인터페이스

|인터페이스|설명|
|---------------|-----------------|
|<xref:System.ICloneable>|개체를 복제 합니다.|
|IPriorityQueue\<Value, Container>|일반 컨테이너 어댑터를 유지 관리 합니다.|

## <a name="remarks"></a>설명

개체는 `Container` 요소를 저장 하 고 요청 시 증가 하는 형식의 기본 컨테이너를 통해 제어 하는 시퀀스에 대 한 저장소를 할당 하 고 해제 `Value` 합니다. 시퀀스를 힙으로 정렬 된 상태로 유지 합니다 .이는 우선 순위가 가장 높은 요소 (최상위 요소)를 쉽게 액세스 하 고 제거할 수 있습니다. 개체는 새 요소를 푸시하는 데 대 한 액세스를 제한 하 고 우선 순위가 가장 높은 요소만 팝 하 여 우선 순위 큐를 구현 합니다.

개체는 [priority_queue:: value_compare (STL/CLR)](#value_compare)형식의 저장 된 대리자 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다. Priority_queue를 생성할 때 저장 된 대리자 개체를 지정할 수 있습니다. 대리자 개체를 지정 하지 않으면 기본값은 비교입니다 `operator<(value_type, value_type)` . 멤버 함수 [priority_queue:: value_comp (STL/CLR)](#value_comp)를 호출 하 여이 저장 된 개체에 액세스 `()` 합니다.

이러한 대리자 개체는 [priority_queue:: value_type (STL/CLR)](#value_type)형식의 값에 대해 엄격 하 고 약한 순서를 적용 해야 합니다. 즉, 다음과 같은 두 가지 키 `X` 가 `Y` 있습니다.

`value_comp()(X, Y)` 모든 호출에 대해 동일한 부울 결과를 반환 합니다.

`value_comp()(X, Y)`이 true 이면은 false 여야 합니다 `value_comp()(Y, X)` .

`value_comp()(X, Y)`이 true 이면 `X` 가 앞에 정렬 된 것입니다 `Y` .

`!value_comp()(X, Y) && !value_comp()(Y, X)`가 true 이면 `X` 및 `Y` 는 동일한 순서를 갖는 것으로 간주 됩니다.

제어 되는 `X` 시퀀스의 앞에 오는 모든 요소의 경우 `Y` `key_comp()(Y, X)` 는 false입니다. 기본 대리자 개체의 경우 키가 값을 감소 시 키 지 않습니다.

따라서 우선 순위가 가장 높은 요소는 다른 요소 보다 먼저 정렬 되지 않는 요소 중 하나입니다.

기본 컨테이너는 요소가 힙으로 정렬 된 상태로 유지 됩니다.

컨테이너는 임의 액세스 반복기를 지원 해야 합니다.

순서가 지정 된 요소는 푸시되는 것과 다른 순서로 팝 될 수 있습니다. (정렬은 안정적이 지 않습니다.)

따라서 기본 컨테이너의 후보에는 [deque (stl/clr)](../dotnet/deque-stl-clr.md) 및 [vector (stl/clr)](../dotnet/vector-stl-clr.md)가 포함 됩니다.

## <a name="members"></a>멤버

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a> priority_queue:: assign (STL/CLR)

모든 요소를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
삽입할 컨테이너 어댑터입니다.

### <a name="remarks"></a>설명

멤버 함수는 `right.get_container()` 를 기본 컨테이너에 할당 합니다. 이를 사용 하 여 큐의 전체 내용을 변경 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a> priority_queue:: const_reference (STL/CLR)

요소에 대한 상수 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>설명

요소에 대 한 상수 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a> priority_queue:: container_type (STL/CLR)

기본 컨테이너의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Container`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a> priority_queue::d ifference_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>설명

이 형식은 음수 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a> priority_queue:: empty (STL/CLR)

요소가 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
bool empty();
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. [Priority_queue:: size (STL/CLR)](#size)와 동일 `() == 0` 합니다. 이를 사용 하 여 priority_queue 비어 있는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a> priority_queue:: generic_container (STL/CLR)

컨테이너에 대 한 제네릭 인터페이스의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>설명

이 템플릿 컨테이너 어댑터 클래스에 대 한 제네릭 인터페이스를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a> priority_queue:: generic_value (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>설명

`GValue`이 템플릿 컨테이너 클래스의 제네릭 인터페이스에 사용할 저장 된 요소 값을 설명 하는 형식의 개체를 설명 하는 형식입니다. 은 `GValue` `value_type` 이거나 `value_type^` `value_type` 가 참조 형식인 경우입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a> priority_queue:: get_container (STL/CLR)

기본 컨테이너에 액세스합니다.

### <a name="syntax"></a>구문

```cpp
container_type get_container();
```

### <a name="remarks"></a>설명

멤버 함수는 기본 컨테이너를 반환 합니다. 이를 사용 하 여 컨테이너 래퍼에서 적용 되는 제한을 무시 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a> priority_queue:: operator = (STL/CLR)

제어되는 시퀀스를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 컨테이너 어댑터입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 제어 되는 시퀀스를 *오른쪽*에 있는 제어 되는 시퀀스의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a> priority_queue::p op (STL/CLR)

가장 높은 proirity 요소를 제거 합니다.

### <a name="syntax"></a>구문

```cpp
void pop();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 우선 순위가 가장 높은 요소를 제거 합니다. 이를 사용 하 여 한 번에 하나의 요소로 큐를 단축 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a> priority_queue::p riority_queue (STL/CLR)

컨테이너 어댑터 개체를 생성 합니다.

### <a name="syntax"></a>구문

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>매개 변수

*계속*<br/>
복사할 컨테이너입니다.

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*pred*<br/>
제어 되는 시퀀스의 순서 조건자입니다.

*오른쪽*<br/>
삽입할 개체 또는 범위입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`priority_queue();`

기본 순서 조건자를 사용 하 여 빈 래핑된 컨테이너를 만듭니다. 기본 순서 조건자를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

생성자는 다음과 같습니다.

`priority_queue(priority_queue<Value, Container>% right);`

순서 조건자가 포함 된의 복사본 인 래핑된 컨테이너를 만듭니다 `right.get_container()` `right.value_comp()` . 이를 사용 하 여 첫 번째 제어 되는 시퀀스를 지정 합니다 .이 시퀀스는 동일한 순서 조건자를 사용 하 여 queue 개체 *오른쪽*에 의해 제어 되는 시퀀스의 복사본입니다.

생성자는 다음과 같습니다.

`priority_queue(priority_queue<Value, Container>^ right);`

순서 조건자가 포함 된의 복사본 인 래핑된 컨테이너를 만듭니다 `right->get_container()` `right->value_comp()` . 이를 사용 하 여 동일한 순서 조건자를 사용 하 여 큐 개체에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 `*right` 합니다.

생성자는 다음과 같습니다.

`explicit priority_queue(value_compare^ pred);`

순서 조건자 *pred*를 사용 하 여 빈 래핑된 컨테이너를 만듭니다. 이를 사용 하 여 지정 된 순서 조건자를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`priority_queue(value_compare^ pred, container_type cont);`

순서 조건자 *pred*을 사용 하 여 빈 래핑된 컨테이너를 만든 다음 *계속* 해 서 사용 하는 모든 요소를 푸시합니다 .이 컨테이너는 지정 된 순서 조건자를 사용 하 여 기존 컨테이너에서 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`template<typename InIt> priority_queue(InIt first, InIt last);`

기본 순서 조건자를 사용 하 여 빈 래핑된 컨테이너를 만든 다음 시퀀스 [ `first` ,)를 푸시합니다 `last` . 지정 된 순서 조건자를 사용 하 여 지정 된 eqeuence에서 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

생성자는 다음과 같습니다.

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

순서 조건자 *pred*를 사용 하 여 빈 래핑된 컨테이너를 만든 다음 시퀀스 [ `first` ,)를 푸시합니다 `last` . 지정 된 순서 조건자를 사용 하 여 지정 된 seqeuence에서 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

생성자는 다음과 같습니다.

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

순서 조건자 *pred*을 사용 하 여 빈 래핑된 컨테이너를 만든 다음, *연속* 의 모든 요소와 시퀀스 [ `first` ,)를 푸시합니다 `last` . 지정 된 순서 조건자를 사용 하 여 기존 컨테이너 및 지정 된 seqeuence에서 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a> priority_queue::p 밀어넣기 (STL/CLR)

새 요소를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
void push(value_type val);
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스에 값이 포함 된 요소를 삽입 하 `val` 고 제어 되는 시퀀스의 순서를 다시 정렬 하 여 힙 규칙을 유지 합니다. 이를 사용 하 여 다른 요소를 큐에 추가 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a> priority_queue:: reference (STL/CLR)

요소에 대한 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>설명

요소에 대 한 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a> priority_queue:: size (STL/CLR)

요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
size_type size();
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 이를 사용 하 여 현재 제어 되는 시퀀스에 있는 요소 수를 확인 합니다. 시퀀스의 크기가 0이 아니면 [priority_queue:: empty (STL/CLR)](#empty)를 참조 하세요 `()` .

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a> priority_queue:: size_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int size_type;
```

### <a name="remarks"></a>설명

이 형식은 음수가 아닌 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a> priority_queue:: to_array (STL/CLR)

제어 되는 시퀀스를 새 배열에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 이를 사용 하 여 배열 형식으로 제어 되는 시퀀스의 복사본을 가져옵니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a> priority_queue:: top (STL/CLR)

우선 순위가 가장 높은 요소에 액세스 합니다.

### <a name="syntax"></a>구문

```cpp
reference top();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 최상위 (가장 높은 우선 순위) 요소에 대 한 참조를 반환 합니다. 이를 사용 하 여 우선 순위가 가장 높은 요소를 알고 있으면이 요소에 액세스 합니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a> priority_queue:: top_item (STL/CLR)

우선 순위가 가장 높은 요소에 액세스 합니다.

### <a name="syntax"></a>구문

```cpp
property value_type back_item;
```

### <a name="remarks"></a>설명

속성은 비어 있지 않아야 하는 제어 되는 시퀀스의 최상위 (가장 높은 우선 순위) 요소에 액세스 합니다. 이를 사용 하면 우선 순위가 가장 높은 요소를 읽거나 쓸 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a> priority_queue:: value_comp (STL/CLR)

두 요소의 순서 지정 대리자를 복사합니다.

### <a name="syntax"></a>구문

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 순서 지정 대리자를 반환 합니다. 이를 통해 두 값을 비교할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a> priority_queue:: value_compare (STL/CLR)

두 값에 대 한 순서 지정 대리자입니다.

### <a name="syntax"></a>구문

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>설명

형식은 첫 번째 인수가 두 번째 인수 앞에 정렬 되는지 여부를 결정 하는 대리자의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a> priority_queue:: value_type (STL/CLR)

요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *값*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
