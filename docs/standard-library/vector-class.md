---
title: vector 클래스
description: 클래스 벡터의 Microsoft c + + 표준 라이브러리 구현에 대 한 참조입니다.
ms.date: 02/23/2021
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.openlocfilehash: c1132b0b8f975cbe0185720c46316446db0506d5
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236779"
---
# <a name="vector-class"></a>`vector` 클래스

C + + 표준 라이브러리 벡터 클래스는 시퀀스 컨테이너의 클래스 템플릿입니다. 벡터는 선형 정렬에서 지정 된 형식의 요소를 저장 하 고 모든 요소에 대 한 빠른 임의 액세스를 허용 합니다. 벡터는 임의 액세스 성능이 프리미엄 인 경우 시퀀스에 대 한 기본 컨테이너입니다.

## <a name="syntax"></a>구문

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>매개 변수

*`Type`*\
벡터에 저장되는 요소 데이터 형식입니다.

*`Allocator`*\
벡터의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<Type>`입니다.

## <a name="remarks"></a>설명

벡터를 사용하면 시퀀스 끝에서 상수 시간 삽입 및 삭제할 수 있습니다. 벡터 중간에 요소를 삽입하거나 삭제하려면 선형 시간이 필요합니다. [ `deque` 클래스](../standard-library/deque-class.md) 컨테이너는 시퀀스의 시작과 끝에서 삽입 하 고 삭제 하는 속도 보다 빠릅니다. 시퀀스 내의 모든 위치에서 [ `list` 클래스](../standard-library/list-class.md) 컨테이너를 삽입 하 고 삭제 하는 것이 더 빠릅니다.

멤버 함수가 벡터 개체에 포함되는 시퀀스를 현재 스토리지 용량보다 더 크게 늘려야 할 때 벡터 다시 할당이 수행됩니다. 다른 삽입 및 지우기에서 시퀀스 내의 여러 스토리지 주소가 변경될 수 있습니다. 이러한 모든 경우 시퀀스의 변경되는 부분을 가리키는 반복기 또는 참조가 올바르지 않은 상태가 됩니다. 재할당이 수행되지 않으면 삽입/삭제 지점 앞의 반복기와 참조만 올바른 상태로 유지됩니다.

[ `vector<bool>` 클래스](../standard-library/vector-bool-class.md) 는 형식의 요소에 대 한 클래스 템플릿 벡터의 전체 특수화입니다 **`bool`** . 특수화에 사용 되는 기본 형식에 대 한 할당자를 포함 합니다.

[ `vector<bool>` 참조 클래스](../standard-library/vector-bool-class.md#reference_class) 는 개체가 vector 개체 내의 요소 (단일 비트)에 대 한 참조를 제공할 수 있는 중첩 클래스입니다 \<bool> .

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[`vector`](#vector)|특정 크기의 벡터 또는 특정 값의 요소나 특정 `allocator`가 포함된 벡터를 생성하거나 다른 벡터의 복사본으로 벡터를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|이름|설명|
|-|-|
|`[allocator_type]`(#allocator_type)|벡터 개체의 `allocator` 클래스를 나타내는 형식입니다.|
|[`const_iterator`](#const_iterator)|벡터의 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|[`const_pointer`](#const_pointer)|벡터의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|[`const_reference`](#const_reference)|벡터에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** . 작업을 읽고 수행 하는 데 사용 **`const`** 됩니다.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Vector의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|[`difference_type`](#difference_type)|벡터 내 두 요소 주소 간의 차이를 제공하는 형식입니다.|
|[`iterator`](#iterator)|벡터에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.|
|[`pointer`](#pointer)|벡터에서 요소에 대한 포인터를 제공하는 형식입니다.|
|[`reference`](#reference)|벡터에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[`reverse_iterator`](#reverse_iterator)|역방향 벡터에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.|
|[`size_type`](#size_type)|벡터의 요소 수를 계산하는 형식입니다.|
|[`value_type`](#value_type)|벡터에 저장된 데이터 형식을 나타내는 형식입니다.|

### <a name="functions"></a>Functions

|이름|설명|
|-|-|
|[`assign`](#assign)|벡터를 지우고 지정된 요소를 빈 벡터에 복사합니다.|
|[`at`](#at)|벡터의 지정된 위치에 있는 요소에 대한 참조를 반환합니다.|
|[`back`](#back)|벡터의 마지막 요소에 대한 참조를 반환합니다.|
|[`begin`](#begin)|벡터의 첫 번째 요소에 대한 임의 액세스 반복기를 반환합니다.|
|[`capacity`](#capacity)|스토리지를 더 할당하지 않고 벡터가 포함할 수 있는 요소의 수를 반환합니다.|
|[`cbegin`](#cbegin)|벡터의 첫 번째 요소에 대한 임의 액세스 const 반복기를 반환합니다.|
|[`cend`](#cend)|벡터 끝의 바로 다음을 가리키는 임의 액세스 const 반복기를 반환합니다.|
|[`crbegin`](#crbegin)|역방향 벡터의 첫 번째 요소에 대해 const 반복기를 반환합니다.|
|[`crend`](#crend)|역방향 벡터 끝에 대해 const 반복기를 반환합니다.|
|[`clear`](#clear)|벡터의 요소를 지웁니다.|
|[`data`](#data)|벡터의 첫 번째 요소에 대한 포인터를 반환합니다.|
|[`emplace`](#emplace)|내부에서 생성된 요소를 벡터의 지정된 위치에 삽입합니다.|
|[`emplace_back`](#emplace_back)|내부에서 생성된 요소를 벡터의 끝에 추가합니다.|
|[`empty`](#empty)|벡터 컨테이너가 비어 있는지 테스트합니다.|
|[`end`](#end)|벡터 끝을 가리키는 임의 액세스 반복기를 반환합니다.|
|[`erase`](#erase)|벡터의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.|
|[`front`](#front)|벡터의 첫 번째 요소에 대한 참조를 반환합니다.|
|[`get_allocator`](#get_allocator)|벡터에서 사용하는 `allocator` 클래스에 개체를 반환합니다.|
|[`insert`](#insert)|벡터의 지정 된 위치에 요소 또는 많은 요소를 삽입 합니다.|
|[`max_size`](#max_size)|벡터의 최대 길이를 반환합니다.|
|[`pop_back`](#pop_back)|벡터의 끝에 있는 요소를 삭제합니다.|
|[`push_back`](#push_back)|벡터 끝에 요소를 추가합니다.|
|[`rbegin`](#rbegin)|역방향 벡터의 첫 번째 요소에 대한 반복기를 반환합니다.|
|[`rend`](#rend)|역방향 벡터 끝에 대해 반복기를 반환합니다.|
|[`reserve`](#reserve)|벡터 개체에 대한 스토리지의 최소 길이를 예약합니다.|
|[`resize`](#resize)|벡터의 새 크기를 지정합니다.|
|[`shrink_to_fit`](#shrink_to_fit)|여분의 용량을 삭제합니다.|
|[`size`](#size)|벡터에 있는 요소 수를 반환합니다.|
|[`swap`](#swap)|두 벡터의 요소를 교환합니다.|

### <a name="operators"></a>연산자

|이름|설명|
|-|-|
|[`operator[]`](#op_at)|지정된 위치에서 벡터 요소에 참조를 반환합니다.|
|[`operator=`](#op_eq)|벡터의 요소를 다른 벡터의 복사본으로 바꿉니다.|

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

벡터 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type`는 템플릿 매개 변수 `Allocator`의 동의어입니다.

### <a name="example"></a>예

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="assign"></a><a name="assign"></a> `assign`

벡터를 지우고 지정된 요소를 빈 벡터에 복사합니다.

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>매개 변수

*`first`*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*`last`*\
복사할 요소의 범위를 벗어난 첫 번째 요소의 위치입니다.

*`count`*\
벡터에 삽입되는 요소의 복사본 수입니다.

*`value`*\
벡터에 삽입되는 요소의 값입니다.

*`init_list`*\
삽입할 요소를 포함하는 initializer_list입니다.

### <a name="remarks"></a>설명

첫 번째 `assign` 는 vector에서 기존 요소를 모두 지웁니다. 그런 다음 `assign` 원래 vector의 지정 된 요소 범위를 벡터에 삽입 하거나 지정 된 새 값 요소의 복사본을 벡터에 삽입 합니다.

### <a name="example"></a>예

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a><a name="at"></a> `at`

벡터의 지정된 위치에 있는 요소에 대한 참조를 반환합니다.

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>매개 변수

*`position`*\
벡터에서 참조할 요소의 아래 첨자 또는 위치 번호입니다.

### <a name="return-value"></a>반환 값

인수에서 아래 첨자로 설정된 요소에 대한 참조입니다. *`position`* 가 벡터 크기 보다 크면에서 `at` 예외를 throw 합니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `at` `const_reference` vector 개체를 수정할 수 없습니다. `at`의 반환 값이 `reference`에 할당되는 경우에는 vector 개체를 수정할 수 있습니다.

### <a name="example"></a>예

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> `back`

벡터의 마지막 요소에 대한 참조를 반환합니다.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>반환 값

벡터의 마지막 요소입니다. 벡터가 비어 있으면 반환 값이 정의되지 않습니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `back` `const_reference` vector 개체를 수정할 수 없습니다. `back`의 반환 값이 `reference`에 할당되는 경우에는 vector 개체를 수정할 수 있습니다.

[`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md)1 또는 2로 정의 된를 사용 하 여 컴파일한 경우 빈 벡터의 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다. 자세한 내용은 [확인 된 반복기](../standard-library/checked-iterators.md)를 참조 하세요.

### <a name="example"></a>예

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a><a name="begin"></a> `begin`

벡터의 첫 번째 요소에 대한 임의 액세스 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

`vector`의 첫 번째 요소 또는 빈 `vector` 다음의 위치 주소를 지정하는 임의 액세스 반복기입니다. 항상와 함께 반환 되는 값을 비교 [`vector::end`](#end) 하 여 유효한 지 확인 합니다.

### <a name="remarks"></a>설명

의 반환 값이에 `begin` 할당 된 경우 [`vector::const_iterator`](#const_iterator) 개체를 수정할 수 `vector` 없습니다. 의 반환 값 `begin` 이에 할당 되는 경우 [`vector::iterator`](#iterator) 개체를 `vector` 수정할 수 있습니다.

### <a name="example"></a>예

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a><a name="capacity"></a> `capacity`

스토리지를 더 할당하지 않고 벡터가 포함할 수 있는 요소의 수를 반환합니다.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>반환 값

벡터에 할당된 스토리지의 현재 길이입니다.

### <a name="remarks"></a>설명

멤버 함수는 [`resize`](#resize) 이를 수용 하기에 충분 한 메모리를 할당 하는 경우 더 효율적입니다. 멤버 함수를 사용 [`reserve`](#reserve) 하 여 할당 된 메모리의 양을 지정 합니다.

### <a name="example"></a>예

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 임의 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

의 반환 값을 사용 하 여 `cbegin` 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 [`auto`](../cpp/auto-cpp.md) 다음 예제와 같이 형식 추론 키워드와 함께에서 사용 됩니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> `cend`

**`const`** 벡터의 마지막 요소 다음에 오는 요소를 가리키는 종료 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

`const`벡터의 이전 끝 반복기입니다. 벡터의 마지막 요소 다음에 나오는 요소를 가리킵니다. 해당 요소는 자리 표시자 이며 역참조 되어서는 안 됩니다. 비교에만 사용 합니다. 벡터가 비어 있으면이 고, 그렇지 않으면 `vector::cend() == vector::cbegin()` 입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 [`auto`](../cpp/auto-cpp.md) 다음 예제와 같이 형식 추론 키워드와 함께 사용 됩니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `end()` `cend()` 합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

에서 반환 된 값은 `cend` 역참조 되지 않아야 합니다. 비교에만 사용 합니다.

## <a name="clear"></a><a name="clear"></a> `clear`

벡터의 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

벡터의 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

형식은 `const_iterator` 요소의 값을 수정 하는 데 사용할 수 없습니다.

### <a name="example"></a>예

`const_iterator`를 사용하는 예제는 [back](#back)의 예제를 참조하세요.

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

벡터의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

형식은 `const_pointer` 요소의 값을 수정 하는 데 사용할 수 없습니다.

[iterator](#iterator)는 벡터 요소에 액세스하는 데 사용되는 경우가 더 많습니다.

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

벡터에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** . 작업을 읽고 수행 하는 데 사용 **`const`** 됩니다.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>설명

형식은 `const_reference` 요소의 값을 수정 하는 데 사용할 수 없습니다.

### <a name="example"></a>예

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

Vector의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

형식은 `const_reverse_iterator` 요소 값을 수정할 수 없으며 벡터를 역방향으로 반복 하는 데 사용 됩니다.

### <a name="example"></a>예

[`rbegin`](#rbegin)반복기를 선언 하 고 사용 하는 방법에 대 한 예제는를 참조 하세요.

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

역방향 벡터의 첫 번째 요소에 대해 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향의 첫 번째 요소 [`vector`](../standard-library/vector-class.md) 또는 역방향이 해제 된에서 마지막 요소의 주소를 지정 하는 const 역방향 임의 액세스 반복기 `vector` 입니다.

### <a name="remarks"></a>설명

반환 값 `crbegin` 이 이면 `vector` 개체를 수정할 수 없습니다.

### <a name="example"></a>예

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a><a name="crend"></a> `crend`

`const`역방향 벡터의 마지막 요소 다음에 나오는 요소를 가리키는 끝이 아닌 역방향 반복기를 반환 합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

`const`역방향 벡터의 역방향 끝을 가리키는 반복기입니다. 역방향 벡터의 마지막 요소 다음에 있는 요소를 가리킵니다 .이 요소는 역방향이 아닌 벡터의 첫 번째 요소 앞의 요소와 동일 합니다. 해당 요소는 자리 표시자 이며 역참조 되어서는 안 됩니다. 비교에만 사용 합니다.

### <a name="remarks"></a>설명

`crend` 는 `vector` 와 함께 사용 되는 것 처럼 역방향에 사용 됩니다 [`vector::cend`](#cend) `vector` .

반환 값 `crend` (적절 하 게 감소)을 사용 하면 `vector` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `vector` 끝에 도달했는지 여부를 테스트할 수 있습니다.

에서 반환 된 값은 `crend` 역참조 되지 않아야 합니다. 비교에만 사용 합니다.

### <a name="example"></a>예

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a><a name="data"></a> `data`

벡터의 첫 번째 요소에 대한 포인터를 반환합니다.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>반환 값

의 첫 번째 요소 또는 빈 다음의 위치에 대 한 포인터입니다 [`vector`](../standard-library/vector-class.md) `vector` .

### <a name="example"></a>예

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1_ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

동일한 벡터 내의 요소를 참조하는 두 반복기 간의 차이를 제공하는 형식입니다.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>설명

요소에 대한 포인터는 요소의 주소를 포함하므로, `difference_type`은 두 포인터 사이의 요소 수로도 설명할 수 있습니다.

[iterator](#iterator)는 벡터 요소에 액세스하는 데 사용되는 경우가 더 많습니다.

### <a name="example"></a>예

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a><a name="emplace"></a> `emplace`

내부에서 생성된 요소를 벡터의 지정된 위치에 삽입합니다.

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>매개 변수

*`position`*\
에서 [`vector`](../standard-library/vector-class.md) 첫 번째 요소가 삽입 되는 위치입니다.

*`args`*\
생성자 인수입니다. 이 함수는 제공되는 인수에 따라 호출할 생성자 오버로드를 유추합니다.

### <a name="return-value"></a>반환 값

이 함수는 새 요소를 `vector`에 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

모든 삽입 작업은 비용이 많이 들 수 있습니다. 성능에 대 한 설명은 [ `vector` 클래스](../standard-library/vector-class.md) 를 참조 하세요 `vector` .

### <a name="example"></a>예

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> `emplace_back`

내부에서 생성된 요소를 벡터의 끝에 추가합니다.

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>매개 변수

*`args`*\
생성자 인수입니다. 이 함수는 제공되는 인수에 따라 호출할 생성자 오버로드를 유추합니다.

### <a name="example"></a>예

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a><a name="empty"></a> `empty`

벡터가 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 벡터가 비어 있으면이 고, 그렇지 않으면입니다. **`false`** 벡터가 비어 있지 않으면입니다.

### <a name="example"></a>예

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a><a name="end"></a> `end`

벡터의 마지막 요소 다음에 오는 요소를 가리키는 종료 반복기를 반환 합니다.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>반환 값

벡터의 이전 끝 반복기입니다. 벡터의 마지막 요소 다음에 나오는 요소를 가리킵니다. 해당 요소는 자리 표시자 이며 역참조 되어서는 안 됩니다. 비교에만 사용 합니다. 벡터가 비어 있으면이 고, 그렇지 않으면 `vector::end() == vector::begin()` 입니다.

### <a name="remarks"></a>설명

의 반환 값 `end` 이 형식의 변수에 할당 되는 경우에는 `const_iterator` vector 개체를 수정할 수 없습니다. 의 반환 값 `end` 이 형식의 변수에 할당 되는 경우 `iterator` vector 개체를 수정할 수 있습니다.

### <a name="example"></a>예

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a><a name="erase"></a> `erase`

벡터의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>매개 변수

*`position`*\
벡터에서 제거할 요소의 위치입니다.

*`first`*\
벡터에서 제거되는 첫 번째 요소의 위치입니다.

*`last`*\
벡터에서 제거되는 마지막 요소 바로 뒤의 위치입니다.

### <a name="return-value"></a>반환 값

제거되는 요소 뒤에 남아 있는 첫 번째 요소를 지정하는 반복기이거나, 남아 있는 요소가 없는 경우에는 벡터 끝에 대한 포인터입니다.

### <a name="example"></a>예

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a><a name="front"></a> `front`

벡터의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>반환 값

벡터 개체의 첫 번째 요소에 대한 참조입니다. 벡터가 비어 있으면 반환이 정의되지 않습니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `front` `const_reference` vector 개체를 수정할 수 없습니다. 의 반환 값이에 할당 된 경우에는 `front` **`reference`** vector 개체를 수정할 수 있습니다.

[`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md)1 또는 2로 정의 된를 사용 하 여 컴파일한 경우 빈 벡터의 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다. 자세한 내용은 [확인 된 반복기](../standard-library/checked-iterators.md)를 참조 하세요.

### <a name="example"></a>예

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

벡터를 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

벡터에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

벡터 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 사용자 고유의 할당자 클래스를 작성 하 고 사용 하는 것은 고급 c + + 기능입니다.

### <a name="example"></a>예

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

하나 이상의 요소 또는 요소의 범위를 벡터의 지정 된 위치에 삽입 합니다.

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>매개 변수

*`position`*\
벡터에서 첫 번째 요소를 삽입하는 위치입니다.

*`value`*\
벡터에 삽입되는 요소의 값입니다.

*`count`*\
벡터에 삽입되는 요소의 수입니다.

*`first`*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*`last`*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

### <a name="return-value"></a>반환 값

처음 두 `insert` 함수는 새 요소가 벡터에 삽입된 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

사전 조건으로 *`first`* 및는 *`last`* vector의 반복기가 아니어야 하며, 그렇지 않은 경우 동작이 정의 되지 않습니다. 모든 삽입 작업은 비용이 많이 들 수 있습니다. 성능에 대 한 설명은 [ `vector` 클래스](../standard-library/vector-class.md) 를 참조 하세요 `vector` .

### <a name="example"></a>예

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

벡터에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

형식을 **`iterator`** 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예

의 예제를 참조 하세요 [`begin`](#begin) .

## <a name="max_size"></a><a name="max_size"></a> `max_size`

벡터의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

벡터의 최대 허용 길이입니다.

### <a name="example"></a>예

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> `operator[]`

지정된 위치에서 벡터 요소에 참조를 반환합니다.

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>매개 변수

*`position`*\
벡터 요소의 위치입니다.

### <a name="return-value"></a>반환 값

지정된 위치가 컨테이너의 크기보다 크거나 같을 경우 결과가 정의되지 않습니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `operator[]` `const_reference` vector 개체를 수정할 수 없습니다. `operator[]`의 반환 값이 참조로 할당되는 경우는 벡터 개체를 수정할 수 있습니다.

[`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md)1 또는 2로 정의 된를 사용 하 여 컴파일할 경우 벡터 범위 밖의 요소에 액세스 하려고 하면 런타임 오류가 발생 합니다. 자세한 내용은 [확인 된 반복기](../standard-library/checked-iterators.md)를 참조 하세요.

### <a name="example"></a>예

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

벡터의 요소를 다른 벡터의 복사본으로 바꿉니다.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>매개 변수

*`right`*\
에 [`vector`](../standard-library/vector-class.md) 복사 되는 `vector` 입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `vector` 는 `operator=` 의 내용을로 복사 하거나 이동 *`right`* `vector` 합니다.

### <a name="example"></a>예

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

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
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

벡터에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 **`pointer`** 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a><a name="pop_back"></a> `pop_back`

벡터의 끝에 있는 요소를 삭제합니다.

```cpp
void pop_back();
```

### <a name="remarks"></a>설명

코드 예제를 보려면 [vector::push_back()](#push_back)을 참조하세요.

## <a name="push_back"></a><a name="push_back"></a> `push_back`

벡터 끝에 요소를 추가합니다.

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>매개 변수

*`value`*\
벡터의 끝에 추가된 요소에 할당할 값입니다.

### <a name="example"></a>예

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a><a name="rbegin"></a> `rbegin`

역방향 벡터의 첫 번째 요소에 대한 반복기를 반환합니다.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 벡터에서 첫 번째 요소의 주소를 지정하거나 정방향 벡터에서 마지막 요소의 주소를 지정하는 역방향 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `rbegin` `const_reverse_iterator` vector 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 vector 개체를 수정할 수 있습니다.

### <a name="example"></a>예

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a><a name="reference"></a> `reference`

벡터에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>예

[`at`](#at)Vector 클래스에서를 사용 하는 방법에 대 한 예제는를 참조 하세요 **`reference`** .

## <a name="rend"></a><a name="rend"></a> `rend`

역방향 벡터의 마지막 요소 다음에 나오는 요소를 가리키는 끝이 아닌 역방향 반복기를 반환 합니다.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 벡터의 역방향 끝을 가리키는 반복기입니다. 역방향 벡터의 마지막 요소 다음에 있는 요소를 가리킵니다 .이 요소는 역방향이 아닌 벡터의 첫 번째 요소 앞의 요소와 동일 합니다. 해당 요소는 자리 표시자 이며 역참조 되어서는 안 됩니다. 비교에만 사용 합니다.

### <a name="remarks"></a>설명

`rend` 는 벡터와 함께 사용 되는 것 처럼 역방향 벡터와 함께 사용 됩니다 [`end`](#end) .

의 반환 값이에 할당 된 경우에는 `rend` `const_reverse_iterator` vector 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 vector 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 벡터 끝에 도달했는지를 테스트할 수 있습니다.

에서 반환 된 값은 `rend` 역참조 되지 않아야 합니다. 비교에만 사용 합니다.

### <a name="example"></a>예

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a><a name="reserve"></a> `reserve`

벡터 개체의 최소 스토리지 길이를 예약하며 필요한 경우 공간을 할당합니다.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>매개 변수

*`count`*\
벡터에 대해 할당할 최소 스토리지 길이입니다.

### <a name="example"></a>예

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a><a name="resize"></a> `resize`

벡터의 새 크기를 지정합니다.

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>매개 변수

*`new_size`*\
벡터의 새 크기입니다.

*`value`*\
새 크기가 원래 크기보다 큰 경우 벡터에 추가된 새 요소의 초기화 값입니다. 이 값이 생략되면 새 개체는 기본 생성자를 사용합니다.

### <a name="remarks"></a>설명

컨테이너의 크기가 요청 된 크기 보다 작은 경우는 요청 된 *`new_size`* `resize` 크기에 도달할 때까지 벡터에 요소를 추가 합니다. 컨테이너의 크기가 요청 된 크기 보다 크면는 `resize` 크기에 도달할 때까지 컨테이너 끝에서 가장 가까운 요소를 삭제 *`new_size`* 합니다. 컨테이너의 현재 크기가 요청한 크기와 같을 경우 아무 작업도 수행 되지 않습니다.

[`size`](#size) 벡터의 현재 크기를 반영 합니다.

### <a name="example"></a>예

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

역방향 벡터에 있는 모든 요소를 읽거나 수정할 수 있는 임의 액세스 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 벡터를 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예

의 예제를 참조 하세요 [`rbegin`](#rbegin) .

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> `shrink_to_fit`

여분의 용량을 삭제합니다.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>예

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a><a name="size"></a> `size`

벡터에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

벡터의 현재 길이입니다.

### <a name="example"></a>예

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

벡터의 요소 수를 계산하는 형식입니다.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>예

의 예제를 참조 하세요 [`capacity`](#capacity) .

## <a name="swap"></a><a name="swap"></a> `swap`

두 벡터의 요소를 교환합니다.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*`right`*\
교환할 요소를 제공 하는 벡터입니다. 또는 요소가 vector의 요소와 교환 되는 벡터 *`left`* 입니다.

*`left`*\
해당 요소를 vector의 요소와 교환할 벡터 *`right`* 입니다.

### <a name="example"></a>예

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

벡터에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>설명

`value_type`는 템플릿 매개 변수 `Type`의 동의어입니다.

### <a name="example"></a>예

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a><a name="vector"></a> `vector`

벡터를 생성 합니다. 오버 로드는 특정 크기의 벡터 또는 특정 값의 요소를 생성 합니다. 또는 다른 벡터의 전체 또는 일부에 대 한 복사본으로 포함 됩니다. 일부 오버 로드를 사용 하 여 사용할 할당자를 지정할 수도 있습니다.

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>매개 변수

*`allocator`*\
이 개체에 사용할 할당자 클래스입니다. [`get_allocator`](#get_allocator) 개체에 대 한 할당자 클래스를 반환 합니다.

*`count`*\
생성된 벡터에 있는 요소의 수입니다.

*`value`*\
생성된 벡터에 있는 요소의 값입니다.

*`source`*\
해당 복사본으로 벡터를 생성할 벡터입니다.

*`first`*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*`last`*\
복사할 요소의 범위를 벗어난 첫 번째 요소의 위치입니다.

*`init_list`*\
`initializer_list`복사할 요소를 포함 하는입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체 ()를 저장 *`allocator`* 하 고 벡터를 초기화 합니다.

처음 두 생성자는 빈 초기 벡터를 지정합니다. 두 번째 생성자는 사용할 할당자 형식 ()을 명시적으로 지정 합니다 *`allocator`* .

세 번째 생성자는 *`count`* 클래스에 대 한 기본값의 요소에 대해 지정 된 수 ()의 반복을 지정 합니다 `Type` .

네 번째 및 다섯 번째 생성자는 값의 요소 반복 ()을 지정 합니다 *`count`* *`value`* .

여섯 번째 생성자는 벡터의 복사본을 지정 합니다 *`source`* .

일곱 번째 생성자는 벡터를 이동 합니다 *`source`* .

여덟 번째 생성자는 initializer_list를 사용하여 요소를 지정합니다.

아홉 번째 및 열 번째 생성자는 벡터의 범위(`first`, `last`)를 복사합니다.

### <a name="example"></a>예제

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
