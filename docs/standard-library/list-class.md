---
description: '자세히 알아보기: list 클래스'
title: list 클래스
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: 9d73c1c61cb7e630ea936685aeaab20f778340ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284839"
---
# <a name="list-class"></a>list 클래스

C + + 표준 라이브러리 목록 클래스는 선형 배열에서 해당 요소를 유지 관리 하 고 시퀀스 내의 모든 위치에서 효율적인 삽입 및 삭제를 허용 하는 시퀀스 컨테이너의 클래스 템플릿입니다. 시퀀스는 양방향으로 링크된 요소의 목록으로 저장됩니다. 이러한 요소는 각각 특정 *Type* 형식의 멤버를 포함합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>매개 변수

*입력할*\
목록에 저장되는 요소 데이터 형식입니다.

*할당자*\
목록의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<Type>`입니다.

## <a name="remarks"></a>설명

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 요소에 대한 임의 액세스는 거의 발생하지 않으며 요소 삽입 또는 삭제는 시퀀스 끝에서만 수행하면 되는 시퀀스를 관리할 때는 벡터를 기본 컨테이너로 사용해야 합니다. 임의 액세스가 필요하며 시퀀스 시작과 끝의 삽입 및 삭제는 거의 수행되지 않는 경우에는 deque 클래스 컨테이너의 성능이 보다 뛰어납니다.

목록 멤버 함수 [merge](#merge), [reverse](#reverse), [unique](#unique), [remove](#remove) 및 [remove_if](#remove_if)는 목록 개체에 대한 작업을 위해 최적화되었으며, 동일한 제네릭 함수에 비해 성능이 우수합니다.

멤버 함수가 목록의 요소를 삽입하거나 지워야 하면 목록 다시 할당이 수행됩니다. 이러한 모든 경우에는 제어되는 시퀀스의 지워지는 부분을 가리키는 반복기 또는 참조만 유효하지 않은 상태가 됩니다.

\<list> [컨테이너](../standard-library/stl-containers.md) 클래스 템플릿 목록과 여러 지원 템플릿을 정의 하려면 c + + 표준 라이브러리 표준 헤더를 포함 합니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|Description|
|-|-|
|[list](#list)|특정 크기의 목록 또는 특정 값의 요소나 특정 `allocator`가 포함된 목록을 다른 목록의 복사본으로 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[allocator_type](#allocator_type)|목록 개체의 `allocator` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|목록의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .|
|[const_pointer](#const_pointer)|목록의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|[const_reference](#const_reference)|**`const`** 작업을 읽고 수행 하기 위해 목록에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|목록의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .|
|[difference_type](#difference_type)|동일한 목록 내의 요소를 참조하는 두 반복기 사이의 차이를 제공하는 형식입니다.|
|[iterator](#iterator)|목록에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[놓고](#pointer)|목록의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|**`const`** 작업을 읽고 수행 하기 위해 목록에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[reverse_iterator](#reverse_iterator)|역방향 목록의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|목록의 요소 수를 계산하는 형식입니다.|
|[value_type](#value_type)|목록에 저장된 데이터 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[assign](#assign)|목록에서 요소를 삭제하고 대상 목록에 요소의 새 집합을 복사합니다.|
|[뒤로](#back)|목록의 마지막 요소에 대한 참조를 반환합니다.|
|[시작](#begin)|목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|목록에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.|
|[cend](#cend)|목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 const 반복기를 반환합니다.|
|[clear](#clear)|목록의 모든 요소를 지웁니다.|
|[crbegin](#crbegin)|역방향 목록에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.|
|[crend](#crend)|역방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 목록의 지정된 위치에 삽입합니다.|
|[emplace_back](#emplace_back)|생성된 요소를 목록 끝부분에 추가합니다.|
|[emplace_front](#emplace_front)|생성된 요소를 목록 시작 부분에 추가합니다.|
|[empty](#empty)|목록이 비어 있는지 여부를 테스트합니다.|
|[end](#end)|목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.|
|[erase](#erase)|목록의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.|
|[앞뒤](#front)|목록의 첫 번째 요소에 대한 참조를 반환합니다.|
|[get_allocator](#get_allocator)|목록을 생성하는 데 사용된 `allocator` 개체의 복사본을 반환합니다.|
|[insert](#insert)|요소 하나 또는 여러 개나 요소의 범위를 목록의 지정된 위치에 삽입합니다.|
|[max_size](#max_size)|목록의 최대 길이를 반환합니다.|
|[결합](#merge)|요소를 인수 목록에서 제거하고 대상 목록에 삽입한 다음 새로 조합된 요소 집합을 오름차순 또는 기타 지정된 순서로 정렬합니다.|
|[pop_back](#pop_back)|목록의 끝에 있는 요소를 삭제합니다.|
|[pop_front](#pop_front)|목록의 시작 부분에 있는 요소를 삭제합니다.|
|[push_back](#push_back)|목록의 끝에 요소를 추가합니다.|
|[push_front](#push_front)|목록의 시작 부분에 요소를 추가합니다.|
|[rbegin](#rbegin)|역방향 목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.|
|[remove](#remove)|목록에서 지정된 값과 일치하는 요소를 지웁니다.|
|[remove_if](#remove_if)|지정된 조건자를 충족하는 요소를 목록에서 지웁니다.|
|[rend](#rend)|역방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.|
|[조정해](#resize)|목록의 새 크기를 지정합니다.|
|[되돌립니다](#reverse)|목록에 요소가 나타나는 순서를 반대로 바꿉니다.|
|[size](#size)|목록에 있는 요소 수를 반환합니다.|
|[sort](#sort)|오름차순 또는 기타 순서 관계를 기준으로 목록의 요소를 정렬합니다.|
|[splice](#splice)|인수 목록에서 요소를 제거하고 대상 목록에 삽입합니다.|
|[스왑을](#swap)|두 목록의 요소를 교환합니다.|
|[unique](#unique)|목록에서 인접하는 중복 요소 또는 기타 이진 조건자를 충족하는 인접 요소를 제거합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 =](#op_eq)|목록의 요소를 다른 목록의 복사본으로 바꿉니다.|

## <a name="requirements"></a>요구 사항

**헤더**: \<list>

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

목록 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type` 는 템플릿 매개 변수 *할당자* 의 동의어입니다.

### <a name="example"></a>예제

[get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="assign"></a><a name="assign"></a> 할당

목록에서 요소를 삭제하고 대상 목록에서 요소의 새 집합을 복사합니다.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*기본*\
인수 목록에서 복사할 요소 범위에 있는 첫 번째 요소의 위치입니다.

*최신*\
인수 목록에서 복사할 요소의 범위 밖에 있는 첫 번째 요소의 위치입니다.

*수*\
목록에 삽입되는 요소의 복사본의 수입니다.

*짧은*\
목록에 삽입되는 요소의 값입니다.

*IList*\
삽입할 요소를 포함하는 initializer_list입니다.

### <a name="remarks"></a>설명

대상 목록에서 기존 요소를 지운 다음 원본 목록이나 일부 다른 목록에서 지정된 범위의 요소를 대상 목록에 삽입하거나, 지정한 값의 새 요소 복사본을 대상 목록에 삽입하도록 지정합니다.

### <a name="example"></a>예제

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a><a name="back"></a> 뒤로

목록의 마지막 요소에 대한 참조를 반환합니다.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>반환 값

목록의 마지막 요소입니다. 목록이 비어 있으면 반환 값은 정의되지 않습니다.

### <a name="remarks"></a>설명

`back`의 반환 값이 `const_reference`에 할당된 경우 목록 개체는 수정할 수 없습니다. `back`의 반환 값이 `reference`에 할당된 경우 목록 개체는 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 목록의 요소에 액세스하려고 하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> begin

목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

목록의 첫 번째 요소 또는 빈 목록 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 `begin` 할당 된 경우 `const_iterator` 목록 개체의 요소는 수정할 수 없습니다. 의 반환 값 `begin` 이에 할당 된 경우 `iterator` 목록 개체의 요소를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 양방향 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

**`const`** 범위에서 마지막 요소 바로 다음 위치의 주소를 가리키는 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위 끝의 바로 다음을 가리키는 양방향 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `end()` `cend()` 합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="clear"></a><a name="clear"></a> 해제

목록의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

목록의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

[back](#back)의 예제를 참조하세요.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

목록의 요소에 대 한 포인터를 제공 **`const`** 합니다.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 목록 개체의 요소에 액세스해야 합니다.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

**`const`** 작업을 읽고 수행 하기 위해 목록에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>설명

`const_reference` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

목록의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 목록을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

[rbegin](#rbegin)에 대한 예제를 참조하세요.

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

역방향 목록에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 목록에서 첫 번째 요소의 주소를 지정하거나 역방향이 해제된 `list`에서 마지막 요소의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 `list`에서 [list::begin](#begin)이 사용되는 것처럼 역방향 목록에서 사용됩니다.

반환 값이 `crbegin`이면 목록 개체를 수정할 수 없습니다. [list::rbegin](#rbegin)은 목록을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

역방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>반환 값

역방향 [list](../standard-library/list-class.md)에서 마지막 요소 다음 위치(역방향이 해제된 `list`에서 첫 번째 요소 앞의 위치)의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 `list`에서 [list::end](#end)가 사용되는 것처럼 역방향 목록에서 사용됩니다.

반환 값이 `crend`이면 `list` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `list` 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

반복기가 가리키는 요소 사이의 범위에 있는 목록의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 [ `first`, `last`) 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소와 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 [vector 클래스](../standard-library/vector-class.md)와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

생성된 요소를 목록의 지정된 위치에 삽입합니다.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 [목록](../standard-library/list-class.md) 에서 첫 번째 요소가 삽입 되는 위치입니다.

*짧은*\
`list` 끝에 추가되는 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 `list`는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

생성된 요소를 목록 끝부분에 추가합니다.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
[목록의](../standard-library/list-class.md)끝에 추가 되는 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 `list`는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

생성된 요소를 목록 시작 부분에 추가합니다.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
[list](../standard-library/list-class.md)의 시작 부분에 추가할 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 `list`는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a><a name="empty"></a> 비우려면

목록이 비어 있는지 여부를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 목록이 비어 있으면이 고, 그렇지 않으면입니다. **`false`** 목록이 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a><a name="end"></a> end

목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>반환 값

목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 양방향 반복기입니다. 목록이 비어 있으면 `list::end == list::begin`입니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 목록의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다.

### <a name="example"></a>예제

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> 지우는

목록의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>매개 변수

*위치*\
목록에서 제거할 요소의 위치입니다.

*기본*\
목록에서 제거되는 첫 번째 요소의 위치입니다.

*최신*\
목록에서 제거되는 마지막 요소 바로 뒤의 위치입니다.

### <a name="return-value"></a>반환 값

제거되는 요소 뒤에 남아 있는 첫 번째 요소를 지정하는 양방향 반복기이거나, 남아 있는 요소가 없는 경우에는 목록 끝에 대한 포인터입니다.

### <a name="remarks"></a>설명

다시 할당은 수행되지 않으므로 반복기와 참조는 지워진 요소에 대해서만 유효하지 않게 됩니다.

`erase`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a><a name="front"></a> 앞뒤

목록의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>반환 값

목록이 비어 있으면 반환이 정의되지 않습니다.

### <a name="remarks"></a>설명

`front`의 반환 값이 `const_reference`에 할당된 경우 목록 개체는 수정할 수 없습니다. `front`의 반환 값이 `reference`에 할당된 경우 목록 개체는 수정할 수 있습니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 빈 목록의 요소에 액세스하려고 하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

목록을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

목록에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

목록 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> 넣거나

요소 하나 또는 여러 개나 요소의 범위를 목록의 지정된 위치에 삽입합니다.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 목록에서 첫 번째 요소를 삽입하는 위치입니다.

*짧은*\
목록에 삽입되는 요소의 값입니다.

*수*\
목록에 삽입되는 요소의 수입니다.

*기본*\
인수 목록에서 복사할 요소 범위에 있는 첫 번째 요소의 위치입니다.

*최신*\
인수 목록에서 복사할 요소의 범위 밖에 있는 첫 번째 요소의 위치입니다.

### <a name="return-value"></a>반환 값

처음 두 insert 함수는 새 요소가 목록에 삽입된 위치를 가리키는 반복기를 반환합니다.

### <a name="example"></a>예제

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> 반복

목록에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

[begin](#begin)의 예제를 참조하세요.

## <a name="list"></a><a name="list"></a> 은

특정 크기의 목록 또는 특정 값의 요소나 특정 할당자가 포함된 목록을 다른 목록 일부 또는 전체의 복사본으로 생성합니다.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 개체에 사용할 할당자 클래스입니다.

*수*\
생성된 목록의 요소 수입니다.

*짧은*\
목록에 있는 요소의 값입니다.

*오른쪽*\
생성된 목록이 복사본으로 지정될 목록입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
복사할 요소가 포함된 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체 (*Al*)를 저장 하 고 목록을 초기화 합니다.

[get_allocator](#get_allocator)는 목록을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

처음 두 생성자는 빈 초기 목록을 지정 하 고, 두 번째 생성자는 사용할 할당자 형식 (*Al*)을 지정 합니다.

세 번째 생성자는 클래스에 대 한 기본값의 요소에 대해 지정 된 수 (*개수*)의 반복을 지정 합니다 `Type` .

네 번째 및 다섯 번째 생성자는 값 *Val* 의 (*Count*) 요소 반복을 지정 합니다.

여섯 번째 생성자 *는 목록의 복사본을 지정 합니다.*

일곱 번째 생성자는 목록을 *오른쪽* 으로 이동 합니다.

여덟 번째 생성자는 initializer_list를 사용하여 요소를 지정합니다.

그 다음 두 생성자는 목록의 `[First, Last)` 범위를 복사합니다.

중간 다시 할당을 수행하는 생성자는 없습니다.

### <a name="example"></a>예제

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a><a name="max_size"></a> max_size

목록의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

목록의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a><a name="merge"></a> 결합

요소를 인수 목록에서 제거하고 대상 목록에 삽입한 다음 새로 조합된 요소 집합을 오름차순 또는 기타 지정된 순서로 정렬합니다.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 목록과 병합할 인수 목록입니다.

*생략*\
대상 목록의 요소를 정렬하는 데 사용되는 비교 연산자입니다.

### <a name="remarks"></a>설명

인수 목록 *오른쪽* 이 대상 목록과 병합 됩니다.

인수 목록과 대상 목록은 모두 결과 시퀀스 정렬의 기준으로 사용할 같은 비교 관계로 정렬되어야 합니다. 첫 번째 멤버 함수의 기본 순서는 오름차순입니다. 두 번째 멤버 함수는 클래스의 사용자 지정 비교 작업 *을 적용* 합니다 `Traits` .

### <a name="example"></a>예제

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

목록의 요소를 다른 목록의 복사본으로 바꿉니다.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`list`에 복사되는 [list](../standard-library/list-class.md)입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후 `list` 연산자는의 내용을로 복사 하거나 이동  `list` 합니다.

### <a name="example"></a>예제

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> 포인터

목록에 있는 요소에 대한 포인터를 제공합니다.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 목록 개체의 요소에 액세스해야 합니다.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

목록의 끝에 있는 요소를 삭제합니다.

```cpp
void pop_back();
```

### <a name="remarks"></a>설명

마지막 요소는 비워 둘 수 없습니다. `pop_back`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

목록의 시작 부분에 있는 요소를 삭제합니다.

```cpp
void pop_front();
```

### <a name="remarks"></a>설명

첫 번째 요소는 비워 둘 수 없습니다. `pop_front`은 예외를 throw할 수 없습니다.

### <a name="example"></a>예제

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

목록의 끝에 요소를 추가합니다.

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
목록 끝에 추가되는 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 목록은 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a><a name="push_front"></a> push_front

목록의 시작 부분에 요소를 추가합니다.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
목록의 시작 부분에 추가할 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 목록은 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

### <a name="example"></a>예제

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

반전된 목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

반전된 목록에서 첫 번째 요소 또는 반전 해제된 목록에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 목록에서 [begin](#begin)이 사용되는 것처럼 반전된 목록에서 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당된 경우 목록 개체는 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당된 경우 목록 개체는 수정할 수 있습니다.

`rbegin`은 목록을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a><a name="reference"></a> 참조일

목록에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>예제

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a><a name="remove"></a> 삭제

목록에서 지정된 값과 일치하는 요소를 지웁니다.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
요소에 값이 있는 경우 목록에서 해당 요소가 제거됩니다.

### <a name="remarks"></a>설명

남은 요소의 순서에는 영향을 주지 않습니다.

### <a name="example"></a>예제

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a><a name="remove_if"></a> remove_if

지정된 조건자를 충족하는 요소를 목록에서 지웁니다.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>매개 변수

*pred*\
요소로 충족된 경우 목록에서 요소가 삭제되는 단항 조건자입니다.

### <a name="example"></a>예제

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a><a name="rend"></a> rend

역방향 목록에서 마지막 요소 다음 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 목록에서 마지막 요소 다음 위치(역방향이 해제된 목록에서 첫 번째 요소 앞의 위치)의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 목록에서 [end](#end)가 사용되는 것처럼 반전된 목록에서 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당된 경우 목록 개체는 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당된 경우 목록 개체는 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 목록의 끝에 도달했는지 여부를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> 조정해

목록의 새 크기를 지정합니다.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>매개 변수

*_Newsize*\
목록의 새 크기입니다.

*짧은*\
새 크기가 원래 크기보다 클 경우 목록에 추가되는 새 요소의 값입니다. 값을 생략하면 새 요소에 클래스의 기본값이 할당됩니다.

### <a name="remarks"></a>설명

목록의 크기가 요청 된 크기 보다 작은 경우, *_Newsize* 요소가 요청 된 크기에 도달할 때까지 목록에 추가 됩니다.

목록의 크기가 요청 된 크기 보다 큰 경우 목록 끝에 가장 가까운 요소는 목록이 *_Newsize* 크기에 도달할 때까지 삭제 됩니다.

목록의 현재 크기가 요청한 크기와 동일하면 아무런 작업도 수행되지 않습니다.

[size](#size)는 목록의 현재 크기를 반영합니다.

### <a name="example"></a>예제

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a><a name="reverse"></a> 되돌립니다

목록에 요소가 나타나는 순서를 반대로 바꿉니다.

```cpp
void reverse();
```

### <a name="example"></a>예제

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

역방향 목록의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 목록을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

[rbegin](#rbegin)에 대한 예제를 참조하세요.

## <a name="size"></a><a name="size"></a> 크기가

목록에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

목록의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

목록의 요소 수를 계산하는 형식입니다.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>예제

[size](#size)의 예제를 참조하세요.

## <a name="sort"></a><a name="sort"></a> 정렬

오름차순 또는 다른 사용자 지정한 순서를 기준으로 목록의 요소를 정렬합니다.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>매개 변수

*생략*\
연속된 요소를 정렬하는 데 사용되는 비교 연산자입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 기본적으로 오름차순으로 요소를 배치합니다.

멤버 템플릿 함수는 클래스의 사용자 지정 비교 작업 *comp* 에 따라 요소를 정렬 합니다 `Traits` .

### <a name="example"></a>예제

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a><a name="splice"></a> 제외

요소를 원본 목록에서 제거한 다음 대상 목록에 삽입합니다.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 목록의 위치로, 이 위치 앞에서 삽입합니다.

*원본*\
대상 목록으로 삽입할 원본 목록입니다.

*Iter*\
원본 목록에서 삽입할 요소입니다.

*기본*\
원본 목록에서 삽입할 범위 내 첫 번째 요소입니다.

*최신*\
원본 목록에서 삽입할 범위 내 마지막 요소 다음의 첫 번째 위치입니다.

### <a name="remarks"></a>설명

멤버 함수의 첫 번째 쌍은 원본 목록의 모든 요소를 대상 목록에 삽입 합니다. *여기서* 참조 하는 위치 앞에는 소스 목록에서 모든 요소가 제거 됩니다. `&Source`와 같지 않아야 **`this`** 합니다.

멤버 함수의 두 번째 쌍은 *Iter* 에서 참조 하는 요소를 대상 *목록의 위치 앞* 에 삽입 하 고 원본 목록에서 *Iter* 를 제거 합니다. `Where == Iter || Where == ++Iter`인 경우 아무 것도 변경되지 않습니다.

멤버 함수의 세 번째 쌍은 [,)로 지정 된 범위를 `First` `Last` 에서 참조 하는 대상 목록의 요소 앞에 삽입 *하* 고 원본 목록에서 해당 요소 범위를 제거 합니다. 인 경우 `&Source == this` 범위는 `[First, Last)` *Where* 가 가리키는 요소를 포함 하지 않아야 합니다.

범위가 지정된 스플라이스가 `N`개 요소 및 `&Source != this`를 삽입하면 [iterator](../standard-library/forward-list-class.md#iterator) 클래스의 개체가 `N`배 증분됩니다.

모든 경우 스플라이스된 요소를 참조하는 반복기, 포인터 또는 참조는 유효하게 남아 있고 대상 컨테이너로 전송됩니다.

### <a name="example"></a>예제

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 목록의 요소를 교환합니다.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 목록 또는 요소를 *왼쪽* 목록과 교환할 목록입니다.

*비어*\
목록 *오른쪽* 에 있는 요소를 교환할 목록입니다.

### <a name="example"></a>예제

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a><a name="unique"></a> 고유

목록에서 인접하는 중복 요소 또는 기타 이진 조건자를 충족하는 인접 요소를 제거합니다.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>매개 변수

*pred*\
연속 요소를 비교하는 데 사용되는 이진 조건자입니다.

### <a name="remarks"></a>설명

이 함수는 목록이 정렬되어 있다고 가정하므로 모든 중복 요소는 인접합니다. 인접하지 않은 중복 항목은 삭제되지 않습니다.

첫 번째 멤버 함수는 이전 요소와 같은 것으로 확인된 모든 요소를 제거합니다.

두 번째 멤버 함수는 이전 요소와 비교할 때 *pred* 조건자 함수를 충족 하는 모든 요소를 제거 합니다. Pred 인수에 대해 헤더에 선언 된 이항 함수 개체를 사용 \<functional> 하거나 직접 만들  수 있습니다.

### <a name="example"></a>예제

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a><a name="value_type"></a> value_type

목록에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>설명

`value_type`은 템플릿 매개 변수 *Type* 의 동의어입니다.

### <a name="example"></a>예제

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
