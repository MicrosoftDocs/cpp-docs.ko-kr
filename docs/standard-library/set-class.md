---
title: set 클래스
description: '`set`컬렉션에서 데이터를 저장 하 고 검색 하는 데 사용 되는 c + + 표준 라이브러리 컨테이너 클래스에 대 한 API 참조입니다.'
ms.date: 9/9/2020
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::contains
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], contains
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: cb19b0d9987ef4ff4624602426930c9f9920dbcd
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040017"
---
# <a name="set-class"></a>set 클래스

C + + 표준 라이브러리 컨테이너 클래스는 `set` 컬렉션에서 데이터를 저장 하 고 검색 하는 데 사용 됩니다. 의 요소 값은 `set` 고유 하며 데이터를 자동으로 정렬 하는 데 따른 키 값으로 사용 됩니다. 에 있는 요소의 값은 `set` 직접 변경할 수 없습니다. 대신, 이전 값을 삭제하고 새 값의 요소를 삽입해야 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>매개 변수

*키인지*\
set에 저장되는 요소 데이터 형식입니다.

*특징이*\
두 요소 값을 정렬 키로 비교하여 set에서 상대적인 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다. 이 인수는 선택 사항이 며, 이진 조건자 **less** *\<Key>* 값은 기본값입니다.

C + + 14에서는 `std::less<>` `std::greater<>` 형식 매개 변수가 없는 또는 조건자를 지정 하 여 유형이 다른 조회를 사용 하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers) 를 참조 하세요.

*할당자*\
set의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<Key>`입니다.

## <a name="remarks"></a>설명

C++ 표준 라이브러리 set의 특성은 다음과 같습니다.

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다. 또한 해당 요소 값은 키 값 이므로 단순 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 해당 요소가 컨테이너 내에서 지정된 비교 함수에 따라 키 값을 기준으로 정렬되므로 정렬됩니다.

- 각각의 요소가 반드시 고유한 키를 가지고 있어야 한다는 점에서 고유성을 갖고 있습니다. set는 또한 간단한 연관 컨테이너이므로 해당 요소도 고유합니다.

집합은 제공 된 기능이 일반적이 고 요소로 포함 된 데이터의 특정 형식과 독립적 이기 때문에 클래스 템플릿으로도 설명 됩니다. 사용될 데이터 형식은 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 이러한 작업을 명시적으로 지 원하는 멤버 함수는 컨테이너의 요소 수에 대 한 로그에 비례 하는 평균 시간으로이 작업을 수행 하는 것이 효율적입니다. 요소를 삽입할 경우 어떤 반복기도 무효화 되지 않으며, 요소를 제거 하면 제거 된 요소를 가리키는 반복기만 무효화 됩니다.

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 set입니다. set의 요소는 고유하며 자체 정렬 키로 사용됩니다. 이 형식의 구조에 대한 모델은 정렬된 목록입니다. 예를 들어, 단어 내의 단어는 한 번만 나타날 수 있습니다. 단어의 여러 번 중복이 허용된 경우는 multiset이 적절한 컨테이너 구조입니다. 고유 키 단어 목록에 값이 연결된 경우 이 데이터를 포함하기 위한 적절한 구조는 map입니다. 대신 키가 고유 하지 않은 경우 multimap은 선택의 컨테이너가 됩니다.

set는 [key_compare](#key_compare) 형식의 저장된 함수 개체를 호출하여 제어하는 시퀀스를 정렬합니다. 이 저장된 개체는 [key_comp](#key_comp) 구성원 함수를 호출하여 액세스할 수 있는 비교 함수입니다. 일반적으로이 순서를 설정 하려면 요소를 비교할 수 있어야 합니다. 즉, 두 요소가 동일 하거나 (어느 것도 다른 것 보다 작지 않음) 하나가 다른 것 보다 작음을 결정할 수 있습니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 *f*(*x, y*)는 두 인수 개체 *x* 및 *y* 와 또는의 반환 값이 있는 함수 개체입니다 **`true`** **`false`** . 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적 인 경우 집합에 적용 된 정렬은 엄격한 약한 정렬입니다. 여기서 *f* *x, y*) 및 *f*(*y, x*)가 모두 false 인 경우 *x* 및 *y* 두 개체는 동등한 것으로 정의 됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

C + + 14에서는 `std::less<>` `std::greater<>` 형식 매개 변수가 없는 또는 조건자를 지정 하 여 유형이 다른 조회를 사용 하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers) 를 참조 하세요.

multiset 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [set](#set) 클래스 구성원 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 집합 이지만, `First` 클래스 멤버 함수의 컨텍스트에서 반복기 범위 (,)에 대해 설명 하는 데에는 충분 `Last` 합니다.

### <a name="constructors"></a>생성자

|속성|Description|
|-|-|
|[set](#set)|비어 있거나 모든 복사본이거나 또는 일부 다른 집합 부분인 집합을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|Description|
|-|-|
|[allocator_type](#allocator_type)|set 개체의 `allocator` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|집합의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .|
|[const_pointer](#const_pointer)|집합의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|[const_reference](#const_reference)|**`const`** 작업을 읽고 수행 하기 위해 set에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|집합에 있는 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .|
|[difference_type](#difference_type)|부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 set의 요소의 개수를 표현하는 데 사용할 수 있습니다.|
|[반복](#iterator)|set에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[key_compare](#key_compare)|set의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|해당 용량 내 set 요소로 저장된 개체를 정렬 키로 설명하는 형식입니다.|
|[놓고](#pointer)|set에서 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|set에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 set의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|set에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_compare](#value_compare)|두 요소를 비교하여 set에서 상대적인 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.|
|[value_type](#value_type)|해당 용량 내 set 요소로 저장된 개체를 값으로 설명하는 형식입니다.|

### <a name="functions"></a>Functions

|Name|Description|
|-|-|
|[시작](#begin)|`set`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`set`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[해제](#clear)|`set`의 모든 요소를 지웁니다.|
|[contains](#contains)<sup>c + + 20</sup> 포함|에 지정 된 키를 가진 요소가 있는지 확인 `set` 합니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `set`의 요소 수를 반환합니다.|
|[crbegin](#rbegin)|역순 `set`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#rend)|역순 `set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `set`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `set`에 삽입합니다.|
|[empty](#empty)|`set`가 비어 있는지 여부를 테스트합니다.|
|[종단](#end)|`set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|지정된 키보다 더 큰 키를 가진 `set`의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 `set`의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.|
|[erase](#erase)|지정된 위치에서 set의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `set` 내 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `set` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`set`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_comp)|`set`에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.|
|[lower_bound](#lower_bound)|set에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`set`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `set`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`set`에 있는 요소 수를 반환합니다.|
|[스왑을](#swap)|두 `set`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`set`에 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`set`에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|Name|Description|
|-|-|
|[연산자 =](#op_eq)|set의 요소를 다른 set의 복사본으로 대체합니다.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

set 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type` 는 템플릿 매개 변수 [할당자](../standard-library/set-class.md)의 동의어입니다.

multiset가 요소의 순서를 지정하는 데 사용하는 함수 개체(템플릿 매개 변수 `Allocator`)를 반환합니다.

`Allocator`에 대한 자세한 내용은 [set 클래스](../standard-library/set-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="begin"></a><a name="begin"></a> 시작

set의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

set의 첫 번째 요소 또는 빈 set 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 할당 된 경우에는 `begin` `const_iterator` set 개체의 요소를 수정할 수 없습니다. 의 반환 값이에 할당 된 경우에는 `begin` `iterator` set 개체의 요소를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 양방향 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

의 반환 값을 사용 하 여 `cbegin` 범위의 요소를 수정할 수 없습니다.

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

에서 반환 된 값은 `cend` 역참조 되지 않아야 합니다.

## <a name="clear"></a><a name="clear"></a> 해제

set의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

집합의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

형식은 `const_iterator` 요소의 값을 수정 하는 데 사용할 수 없습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

집합의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

형식은 `const_pointer` 요소의 값을 수정 하는 데 사용할 수 없습니다.

대부분의 경우에는 [const_iterator](#const_iterator)를 사용하여 const set 개체의 요소에 액세스해야 합니다.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

**`const`** 작업을 읽고 수행 하기 위해 set에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>예제

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference can't be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

집합에 있는 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

형식은 `const_reverse_iterator` 요소 값을 수정할 수 없으며 집합을 역방향으로 반복 하는 데 사용 됩니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="contains"></a><a name="contains"></a> 에서는

에 지정 된 키를 가진 요소가 있는지 확인 `set` 합니다.

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>매개 변수

*시계의*\
키의 형식입니다.

*키인지*\
찾을 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

`true` 에 요소가 있으면 `set` 이 고, 그렇지 않으면 `false` 입니다.

### <a name="remarks"></a>설명

`contains()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

`template<class K> bool contains(const K& key) const` 가 투명 한 경우에만 오버 로드 확인에 참여 `key_compare` 합니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](https://docs.microsoft.com/cpp/standard-library/stl-containers#heterogeneous-lookup-in-associative-containers-c14) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <set>
#include <iostream>

int main()
{
    std::set<int> theSet = {1, 2};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theSet.contains(2) << '\n';
    std::cout << theSet.contains(3) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="count"></a><a name="count"></a> 수

키가 매개 변수로 지정된 키와 일치하는 set의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
set에서 일치하는지 확인할 요소의 키입니다.

### <a name="return-value"></a>반환 값

set에 정렬 키가 매개 변수 키와 일치하는 요소가 포함되어 있는 경우 1입니다. 집합에 일치 하는 키가 있는 요소가 포함 되지 않은 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수가 다음 범위에 있는 요소의 수를 반환합니다.

\[ lower_bound(*key*), upper_bound(*key*) ).

### <a name="example"></a>예제

다음 예제에서는 set::count 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

역순 set에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 set에서 첫 번째 요소 또는 정방향 set에서 마지막 요소의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 set에서 [begin](#begin)이 사용되는 것처럼 역방향 set에 사용됩니다.

반환 값 `crbegin` 이 이면 set 개체를 수정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

역순 set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 set에서 마지막 요소 다음의 위치(정방향 set의 첫 번째 요소 앞의 위치) 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 set에서 [end](#end)가 사용되는 것처럼 역방향 set에 사용됩니다.

반환 값 `crend` 이 이면 set 개체를 수정할 수 없습니다. 에서 반환 된 값은 `crend` 역참조 되지 않아야 합니다.

`crend`를 사용하여 역방향 반복기가 set 끝에 도달했는지를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 set의 요소의 개수를 표현하는 데 사용할 수 있습니다.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 *[ first,  last)* 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소에서 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

`difference_type`는 입력 반복기 요구 사항을 충족 하는 모든 반복기 (set 등의 가역 컨테이너에서 지 원하는 양방향 반복기 클래스 포함)에 사용할 수 있지만, 반복기 간의 빼기는 vector와 같은 임의 액세스 컨테이너가 제공 하는 임의 액세스 반복기 에서만 지원 됩니다.

### <a name="example"></a>예제

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there's at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
값이 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 set에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

삽입이 수행된 경우 해당 bool 요소가 true를 반환하고, 해당 값에 순서 내의 동일한 값이 들어 있는 요소가 map에 이미 포함되어 있는 경우 flase를 반환하는 [쌍](../standard-library/pair-structure.md)입니다. 반환 값 쌍의 반복기 구성 요소는 bool 구성 요소가 true인 경우 새 요소가 삽입된 주소를 반환하거나, 부울 구성 요소가 false인 경우 요소가 이미 있었던 주소를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

Emplacement 중에 예외가 throw 되 면 컨테이너의 상태가 수정 되지 않습니다.

### <a name="example"></a>예제

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
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
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

배치 힌트를 사용하여 생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
set가 해당 요소를 이미 포함하고 있지 않거나, 보다 일반적으로는 값이 동등하게 정렬된 요소를 이미 포함하고 있지 않을 경우 set에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다. *이 지점이 바로 앞에*오면 로그 시간 대신 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

요소가 이미 있어서 삽입이 실패하면 기존 요소에 대한 반복기가 반환됩니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

Emplacement 중에 예외가 throw 되 면 컨테이너의 상태가 수정 되지 않습니다.

### <a name="example"></a>예제

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> 비우려면

set가 비어 있는지 여부를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 집합이 비어 있으면이 고, 그렇지 않으면입니다. **`false`** 집합이 비어 있지 않으면입니다.

### <a name="example"></a>예제

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a><a name="end"></a> 종단

마지막 바로 다음 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

마지막 바로 다음 반복기입니다. 집합이 비어 있으면 `set::end() == set::begin()`입니다.

### <a name="remarks"></a>설명

**end**는 반복기가 집합의 끝을 통과했는지를 테스트하는 데 사용됩니다.

**End** 에서 반환한 값을 역참조 해서는 안 됩니다.

코드 예제를 보려면 [set::find](#find)를 참조하세요.

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

지정된 키보다 더 크거나 같은 키를 가진 set의 첫 번째 요소와 지정된 키보다 더 큰 키를 가진 set의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

멤버 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **먼저**, 하위 바운드 반복기를 역참조 하려면 \* ( `pr` . **첫 번째**). 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **둘째**, 상한 반복기를 역참조 하려면 ()를 사용 \* `pr` 합니다. **second**).

### <a name="example"></a>예제

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> 지우는

지정된 위치에서 set의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>매개 변수

*위치*\
제거할 요소의 위치입니다.

*기본*\
제거할 첫 번째 요소의 위치입니다.

*최신*\
제거할 마지막 요소 바로 다음 위치입니다.

*키인지*\
제거할 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

처음 두 구성원 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 set의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 구성원 함수의 경우 set에서 제거된 요소의 수를 반환합니다.

### <a name="example"></a>예제

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a><a name="find"></a> 찾아낼

지정된 키와 같은 키를 포함하는 집합 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 집합에서 요소의 정렬 키와 일치하는지 확인할 키 값입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 집합의 마지막 요소(`set::end()`) 다음 위치를 가리키는 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 작음 비교 가능 보다 작음 관계를 기반으로 순서를 지정 하는 이진 조건자의 인수 *키* 와 동일한 키를 가진 집합의 요소를 참조 하는 반복기를 반환 합니다.

의 반환 값이에 할당 된 경우에는 `find` `const_iterator` set 개체를 수정할 수 없습니다. 의 반환 값이에 할당 된 경우에는 `find` `iterator` set 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

set를 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

set에서 메모리를 관리하는 데 사용하는 할당자(템플릿 매개 변수 `Allocator`)입니다.

`Allocator`에 대한 자세한 내용은 [set 클래스](../standard-library/set-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="remarks"></a>설명

set 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> 넣거나

set에 요소 또는 요소의 범위를 삽입합니다.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>매개 변수

*짧은*\
값이 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 set에 삽입되는 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다. *이 지점이 바로 앞에*오면 로그 시간 대신 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

*ValTy*\
집합에서 [value_type](../standard-library/map-class.md#value_type)요소를 생성 하는 데 사용할 수 있는 인수 형식을 지정 하 고 *Val* 을 인수로 사용 하는 템플릿 매개 변수입니다.

*기본*\
복사할 첫 번째 요소의 위치입니다.

*최신*\
복사할 마지막 요소 바로 다음 위치입니다.

*InputIterator*\
[value_type](../standard-library/map-class.md#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.

*IList*\
요소를 복사할 [initializer_list](../standard-library/initializer-list.md) 입니다.

### <a name="return-value"></a>반환 값

단일 요소 멤버 함수 (1) 및 (2)는 [pair](../standard-library/pair-structure.md) **`bool`** 구성 요소가 삽입 된 경우 true이 고 집합에 정렬에 동일한 값의 요소가 이미 포함 되어 있는 경우 false 인 쌍을 반환 합니다. 반환 값 쌍의 반복기 구성 요소는 구성 요소가 true 인 경우 새로 삽입 된 요소를 가리키거나 **`bool`** 구성 요소가 false 인 경우에는 기존 요소를 가리킵니다 **`bool`** .

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 새 요소가 set에 삽입된 위치를 가리키는 반복기를 반환하고 동일한 키가 있는 요소가 존재하는 경우에는 기존 요소를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 반복기, 포인터 또는 참조를 무효화하지 않습니다.

하나의 요소만 삽입 하는 동안 예외가 throw 되 면 컨테이너의 상태가 수정 되지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

단일 요소 구성원 함수에서 반환한 `pair` `pr`의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 반환된 쌍 내에서 반복기를 역참조하려면 `*pr.first`를 사용하여 요소를 제공합니다. 구성 요소에 액세스 하려면를 **`bool`** 사용 `pr.second` 합니다. 예제는 이 문서 뒷부분에 있는 샘플 코드를 참조하세요.

컨테이너의 [value_type](../standard-library/map-class.md#value_type)은 컨테이너에 속한 형식 정의이고 set의 경우 `set<V>::value_type`은 `const V`입니다.

범위 멤버 함수 (5)는 범위에서 반복기가 주소를 지정 하는 각 요소에 해당 하는 집합에 요소 값의 시퀀스를 삽입 `[First, Last)` 하므로는 `Last` 삽입 되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `s.insert(v.begin(), v.end());` 문이 `v`의 모든 요소를 `s`에 삽입하려고 합니다. 범위에 고유 값이 있는 요소만 삽입됩니다. 중복 값은 무시됩니다. 어떤 요소가 거부되는지 관찰하려면 `insert`의 단일 요소 버전을 사용합니다.

이니셜라이저 목록 구성원 함수 (6)은 [initializer_list](../standard-library/initializer-list.md)를 사용하여 요소를 set로 복사합니다.

생성된 요소를 제 위치에 삽입하려면, 즉 복사 또는 이동 작업을 수행하지 않으려면 [set::emplace](#emplace) 및 [set::emplace_hint](#emplace_hint)를 참조하세요.

### <a name="example"></a>예제

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

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

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> 반복

set의 모든 요소를 읽을 수 있는 상수 [양방향 반복기](../standard-library/bidirectional-iterator-tag-struct.md)를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>예제

`iterator`을 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="key_comp"></a><a name="key_comp"></a> key_comp

set에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

set가 요소의 순서를 지정하는 데 사용하는 함수 개체(템플릿 매개 변수 `Traits`)를 반환합니다.

에 대 한 자세한 내용은 `Traits` [set 클래스](../standard-library/set-class.md) 항목을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 구성원 함수

**bool operator ()**(**const key&** `_xVal` , **const key&** `_yVal` );

**`true`** `_xVal` 가 보다 앞에 있고 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[Key_compare](#key_compare) 와 [value_compare](#value_compare) 는 모두 템플릿 매개 변수의 동의어입니다 `Traits` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a><a name="key_compare"></a> key_compare

set의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare`는 템플릿 매개 변수 `Traits`의 동의어입니다.

에 대 한 자세한 내용은 `Traits` [set 클래스](../standard-library/set-class.md) 항목을 참조 하세요.

`key_compare`및 [value_compare](#value_compare) 는 모두 템플릿 매개 변수의 동의어입니다 `Traits` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="key_type"></a><a name="key_type"></a> key_type

해당 용량 내에서 set의 요소로 저장된 개체를 정렬 키로 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type`는 템플릿 매개 변수 `Key`의 동의어입니다.

`Key`에 대한 자세한 내용은 [set 클래스](../standard-library/set-class.md) 항목의 설명 섹션을 참조하세요.

`key_type`및 [value_type](#value_type) 는 모두 템플릿 매개 변수의 동의어입니다 `Key` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="lower_bound"></a><a name="lower_bound"></a> lower_bound

set에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 set 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 set에서 마지막 요소 다음 위치의 주소를 지정하는 반복기 또는 `const_iterator`입니다.

### <a name="example"></a>예제

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a><a name="max_size"></a> max_size

set의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

set의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

다른 `set`의 요소를 사용하여 이 `set`의 요소를 대체합니다.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
이 `set`에 할당할 새 요소를 제공하는 `set`입니다.

### <a name="remarks"></a>설명

첫 번째 버전의에서는 `operator=` *오른쪽*에 대 한 [lvalue 참조](../cpp/lvalue-reference-declarator-amp.md) 를 사용 하 여 *오른쪽* 에서이로 요소를 복사 합니다 `set` .

두 번째 버전은 right에 대해 [rvalue 참조](../cpp/rvalue-reference-declarator-amp-amp.md)를 사용하여 *오른쪽* 에서로 요소를 이동 `set` 합니다.

연산자 함수가 실행되기 전에 이 `set`에 있었던 모든 요소는 삭제됩니다.

### <a name="example"></a>예제

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

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

## <a name="pointer"></a><a name="pointer"></a> 포인터

set에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>설명

**pointer** 형식은 요소값을 수정할 때 사용할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 set 개체의 요소에 액세스해야 합니다.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

역순 set에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 set에서 첫 번째 요소 또는 정방향 set에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 set에서 [begin](#begin)이 사용되는 것처럼 역방향 set에 사용됩니다.

의 반환 값이에 할당 된 경우에는 `rbegin` `const_reverse_iterator` set 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 set 개체를 수정할 수 있습니다.

`rbegin`은 set를 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a><a name="reference"></a> 참조일

set에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>예제

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a><a name="rend"></a> rend

역순 set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 set에서 마지막 요소 다음의 위치(정방향 set의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 set에서 [end](#end)가 사용되는 것처럼 역방향 set에 사용됩니다.

의 반환 값이에 할당 된 경우에는 `rend` `const_reverse_iterator` set 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 set 개체를 수정할 수 있습니다. 에서 반환 된 값은 `rend` 역참조 되지 않아야 합니다.

`rend`를 사용하여 역방향 반복기가 set 끝에 도달했는지를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

역순 set의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

형식은 `reverse_iterator` 역방향으로 집합을 반복 하는 데 사용 됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="set"></a><a name="set"></a> 설정

비어 있거나 모든 복사본이거나 또는 일부 다른 집합 부분인 집합을 생성합니다.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 집합 개체에 사용할 저장소 할당자 클래스로, 기본값은 `Allocator` 입니다.

*생략*\
set의 요소 순서를 지정하는 데 사용되는 `const Traits` 형식의 비교 함수로, 기본값은 `Compare`입니다.

*Rght*\
생성된 set가 복사본으로 지정될 set입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
요소를 복사해올 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 set의 메모리 스토리지를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 set를 초기화합니다.

모든 생성자는 `Traits` 집합의 키 사이에 순서를 설정 하는 데 사용 되 고 나중에 [key_comp](#key_comp)를 호출 하 여 반환할 수 있는 형식의 함수 개체를 저장 합니다.

처음 세 생성자는 빈 초기 집합을 지정 하 고, 두 번째 생성자는 요소의 순서를 설정 하는 데 사용할 비교 함수 ()의 형식을 지정 하며, 세 번째 생성자는 `comp` 사용할 할당자 형식 ()을 명시적으로 지정 합니다 `al` . 키워드는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 생성자는 `right` set의 복사본을 지정합니다.

그 다음 3개 생성자는 initializer_list를 사용하여 요소를 지정합니다.

다음 세 생성자는 `first` `last` 클래스 `Traits` 및 **할당자**의 비교 함수 유형을 지정 하는 내 높아집니다가 늘어나는 집합의 범위 [,)를 복사 합니다.

여덟 번째 생성자는 `right`를 이동하여 set의 복사본을 지정합니다.

### <a name="example"></a>예제

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a><a name="size"></a> 크기가

집합에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

set의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

set에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="swap"></a><a name="swap"></a> 스왑을

두 set의 요소를 교환합니다.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 set와 교환할 요소를 제공하는 인수 집합입니다.

### <a name="remarks"></a>설명

구성원 함수는 해당 요소를 교환할 두 set의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> upper_bound

set에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 인수 키 보다 큰 키를 포함 하는 집합 내 요소의 위치 주소를 가져오거나 해당 키와 일치 하는 항목이 없는 경우 set에서 마지막 요소 다음 위치의 주소를 설정 하는 또는입니다.

### <a name="example"></a>예제

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> value_comp

set에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

set가 요소의 순서를 지정하는 데 사용하는 함수 개체(템플릿 매개 변수 `Traits`)를 반환합니다.

에 대 한 자세한 내용은 `Traits` [set 클래스](../standard-library/set-class.md) 항목을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 구성원 함수

**bool operator**(**const key&** `_xVal` , **const key&** `_yVal` );

**`true`** `_xVal` 가 보다 앞에 있고 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[Value_compare](#value_compare) 와 [key_compare](#key_compare) 는 모두 템플릿 매개 변수의 동의어입니다 `Traits` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a><a name="value_compare"></a> value_compare

두 요소값을 비교하여 set에서 상대적인 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>설명

`value_compare`는 템플릿 매개 변수 `Traits`의 동의어입니다.

에 대 한 자세한 내용은 `Traits` [set 클래스](../standard-library/set-class.md) 항목을 참조 하세요.

[Key_compare](#key_compare) 와 `value_compare` 는 모두 템플릿 매개 변수의 동의어입니다 `Traits` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

`value_compare`를 선언하고 사용하는 방법의 예제는 [value_comp](#value_comp)의 예제를 참조하세요.

## <a name="value_type"></a><a name="value_type"></a> value_type

해당 용량 내에서 set의 요소로 저장된 개체를 값으로 설명하는 형식입니다.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>설명

`value_type`는 템플릿 매개 변수 `Key`의 동의어입니다.

`Key`에 대한 자세한 내용은 [set 클래스](../standard-library/set-class.md) 항목의 설명 섹션을 참조하세요.

[Key_type](#key_type) 와 `value_type` 는 모두 템플릿 매개 변수의 동의어입니다 `Key` . Set 및 multiset 클래스에 대해 두 형식이 모두 제공 됩니다 .이 클래스는 map 및 multimap 클래스와의 호환성을 위해 고유 합니다.

### <a name="example"></a>예제

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
