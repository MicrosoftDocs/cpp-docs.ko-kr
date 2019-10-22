---
title: multiset 클래스
ms.date: 11/04/2016
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
ms.openlocfilehash: 83980094562e1c0083a879d1dc9aab591dc52d02
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689262"
---
# <a name="multiset-class"></a>multiset 클래스

C++ 표준 라이브러리 multiset 클래스는 포함된 요소값이 고유할 필요가 없고 데이터가 자동 정렬되는 기준인 키 값으로 사용된 컬렉션의 데이터를 저장 및 검색하는 데 사용됩니다. multiset 요소의 키 값은 직접 변경할 수 없습니다. 대신, 이전 값을 삭제하고 새 값의 요소를 삽입해야 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>매개 변수

*키* \
multiset에 저장되는 요소 데이터 형식입니다.

@No__t_1 *비교*
함수 개체를 제공하는 이 형식은 multiset 내에서의 상대적인 순서를 결정하는 정렬 키로 두 요소 값을 비교할 수 있습니다. 이진 조건자 **less**\<Key>가 기본값입니다.

C++14에서는 형식 매개 변수가 없는 `std::less<>` 또는 `std::greater<>` 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers)를 참조하세요.

*할당자* \
multiset의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 기본값은 `allocator<Key>`여야 합니다.

## <a name="remarks"></a>주의

C++ 표준 라이브러리 multiset 클래스의 특징은 다음과 같습니다.

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 해당 요소가 컨테이너 내에서 지정된 비교 함수에 따라 키 값을 기준으로 정렬되므로 정렬됩니다.

- 해당 요소는 고유 키를 가질 필요가 없으므로 하나의 키 값은 이와 관련된 많은 요소 값을 가질 수 있습니다.

- 해당 요소 값은 키 값과 구별되므로 간단한 연관 컨테이너입니다.

- 클래스 템플릿은 제공 된 기능이 일반적 이므로 요소로 포함 된 특정 데이터 형식과 독립적 이기 때문입니다. 사용될 데이터 형식은 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

multiset 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [multiset](#multiset) 클래스 구성원 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 모음이지만, 클래스 구성원 함수의 맥락에서 반복기 범위[ `First`, `Last`)에 대해 설명하는 데에는 충분합니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 연관 컨테이너들은 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 이러한 작업을 명시적으로 지원하는 멤버 함수는 컨테이너의 요소 개수를 진수로 하는 로그값에 평균적으로 비례하는 시간 안에 수행하므로 효율적입니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 multiset입니다. multiset의 요소는 여러 개일 수 있고 자체 정렬 키로 사용되므로 키는 고유하지 않습니다. 이 형식의 구조에 대한 모델은 정렬된 목록입니다. 예를 들어, 단어 내의 단어가 두 번 이상 나타날 수 있습니다. 단어가 여러 번 나타날 수 있도록 허용되지 않은 경우 set가 적절한 컨테이너 구조입니다. 고유 키 단어 목록에 고유 정의가 연결된 경우 이 데이터를 포함하기 위한 적절한 구조는 map입니다. 대신 정의가 고유하지 않은 경우는 multimap이 적절한 컨테이너입니다.

Multiset는 *Compare*형식의 저장 된 함수 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다. 이 저장된 개체는 [key_comp](#key_comp) 구성원 함수를 호출하여 액세스할 수 있는 비교 함수입니다. 일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 *f*( *x*, *y*)는 두 인수 개체 *x*, *y* 및 반환 값 **true** 또는 **false**가 있는 함수 개체입니다. 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적인 경우 set에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서, *f*( *x,y*) 및 *f*( *y,x*)가 모두 false인 경우 x 및 y 두 개체는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

C++14에서는 형식 매개 변수가 없는 `std::less<>` 또는 `std::greater<>` 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers)를 참조하세요.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[multiset](#multiset)|비어 있거나 지정된 `multiset`의 전체 또는 일부의 복사본인 `multiset`을 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체에 대한 `multiset` 클래스의 typedef|
|[const_iterator](#const_iterator)|@No__t_1의 **const** 요소를 읽을 수 있는 양방향 반복기에 대 한 typedef|
|[const_pointer](#const_pointer)|@No__t_1의 **const** 요소에 대 한 포인터의 typedef입니다.|
|[const_reference](#const_reference)|**Const** 작업을 읽고 수행 하기 위해 `multiset`에 저장 된 **const** 요소에 대 한 참조의 typedef입니다.|
|[const_reverse_iterator](#const_reverse_iterator)|@No__t_1의 모든 **const** 요소를 읽을 수 있는 양방향 반복기에 대 한 typedef|
|[difference_type](#difference_type)|반복기가 가리키는 요소 사이의 범위에 있는 `multiset`의 요소 개수에 대한 부호 있는 정수 typedef|
|[iterator](#iterator)|`multiset`의 모든 요소를 읽거나 수정할 수 있는 양방향 반복기에 대한 typedef|
|[key_compare](#key_compare)|`multiset`의 두 요소간 상대적 순서를 결정하는 두 키를 비교할 수 있는 함수 개체에 대한 typedef|
|[key_type](#key_type)|`multiset`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체에 대한 typedef|
|[pointer](#pointer)|`multiset`의 요소를 가리키는 포인터에 대한 typedef|
|[reference](#reference)|`multiset`에 저장된 요소에 대한 참조의 typedef|
|[reverse_iterator](#reverse_iterator)|역순 `multiset`의 요소를 읽거나 수정할 수 있는 양방향 반복기에 대한 typedef|
|[size_type](#size_type)|`multiset`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_compare](#value_compare)|두 요소를 정렬 키로 비교하여 `multiset`에서 상대적 순서를 결정할 수 있는 함수 개체의 typedef|
|[value_type](#value_type)|해당 용량 내 `multiset` 요소로 저장된 개체를 값으로 설명하는 typedef|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[begin](#begin)|`multiset`의 첫 번째 요소를 가리키는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`multiset`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`multiset`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`multiset`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `multiset`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 set에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `multiset`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `multiset`에 삽입합니다.|
|[empty](#empty)|`multiset`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`multiset`에서 마지막 요소 다음 위치를 가리키는 반복기를 반환합니다.|
|[equal_range](#equal_range)|반복기 쌍을 반환합니다. `multiset`에서 지정된 키보다 큰 키가 있는 첫 번째 요소를 가리키는 쌍의 첫 번째 반복기 `multiset`에서 키보다 크거나 같은 키가 있는 첫 번째 요소를 가리키는 쌍의 두 번째 반복기|
|[erase](#erase)|지정된 위치에서 `multiset`의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.|
|[find](#find)|`multiset`에서 지정된 키와 같은 키를 가진 요소의 첫 번째 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`를 생성하는 데 사용된 `multiset` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`multiset`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_comp)|`multiset`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공합니다.|
|[lower_bound](#lower_bound)|`multiset`에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`multiset`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `multiset`의 첫 번째 요소를 가리키는 반복기를 반환합니다.|
|[rend](#rend)|역순 `multiset`에 마지막 요소 다음 위치를 가리키는 반복기를 반환합니다.|
|[size](#size)|`multiset`의 요소 수를 반환합니다.|
|[swap](#swap)|두 `multiset`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`multiset`에 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`multiset`에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator=](#op_eq)|`multiset`의 요소를 다른 `multiset`의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<set>

**네임스페이스:** std

## <a name="allocator_type"></a>  multiset::allocator_type

multiset 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>주의

`allocator_type`는 템플릿 매개 변수 `Allocator`의 동의어입니다.

`Allocator`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="begin"></a>  multiset::begin

multiset의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

multiset의 첫 번째 요소 또는 빈 multiset 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// multiset_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::const_iterator ms1_cIter;

   ms1.insert( 1 );
   ms1.insert( 2 );
   ms1.insert( 3 );

   ms1_Iter = ms1.begin( );
   cout << "The first element of ms1 is " << *ms1_Iter << endl;

   ms1_Iter = ms1.begin( );
   ms1.erase( ms1_Iter );

   // The following 2 lines would err as the iterator is const
   // ms1_cIter = ms1.begin( );
   // ms1.erase( ms1_cIter );

   ms1_cIter = ms1.begin( );
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;
}
```

```Output
The first element of ms1 is 1
The first element of ms1 is now 2
```

## <a name="cbegin"></a>  multiset::cbegin

범위의 첫 번째 요소를 주소 처리 하는 **const** 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 **const** 양방향 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()`).

### <a name="remarks"></a>주의

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `begin()` 및 `cbegin()`를 지 원하는 모든 종류의 수정 가능 (비 **const**) 컨테이너로 `Container` 하는 것이 좋습니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multiset::cend

범위에서 마지막 요소 바로 다음 위치의 주소를 나타내는 **const** 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 **const** 양방향 액세스 반복기입니다.

### <a name="remarks"></a>주의

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `end()` 및 `cend()`를 지 원하는 모든 종류의 수정 가능 (비 **const**) 컨테이너로 `Container` 하는 것이 좋습니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="clear"></a>  multiset::clear

multiset의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

```cpp
// multiset_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 1 );
   ms1.insert( 2 );

   cout << "The size of the multiset is initially "
        << ms1.size( ) << "." << endl;

   ms1.clear( );
   cout << "The size of the multiset after clearing is "
        << ms1.size( ) << "." << endl;
}
```

```Output
The size of the multiset is initially 2.
The size of the multiset after clearing is 0.
```

## <a name="const_iterator"></a>  multiset::const_iterator

multiset의 **const** 요소 하나를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>주의

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="const_pointer"></a>  multiset::const_pointer

multiset에서 **const** 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>주의

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 multiset 개체의 요소에 액세스해야 합니다.

## <a name="const_reference"></a>  multiset::const_reference

**const** 작업을 읽고 수행하기 위해 목록에 저장된 **const** 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>예제

```cpp
// multiset_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator

multiset의 모든 **const** 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>주의

`const_reverse_iterator` 형식은 요소값을 수정할 수 없으며 multiset를 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="count"></a>  multiset::count

키가 매개 변수로 지정된 키와 일치하는 multiset의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키* \
multiset에서 일치하는지 확인할 요소의 키입니다.

### <a name="return-value"></a>반환 값

정렬 키가 매개 변수 키와 일치하는 multiset의 요소 수입니다.

### <a name="remarks"></a>주의

멤버 함수는 다음 범위에 있는 *x* 요소의 수를 반환합니다.

\[ lower_bound(*key*), upper_bound(*key*) )

### <a name="example"></a>예제

다음 예제에서는 multiset::count 멤버 함수의 사용을 보여 줍니다.

```cpp
// multiset_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    multiset<int> ms1;
    multiset<int>::size_type i;

    ms1.insert(1);
    ms1.insert(1);
    ms1.insert(2);

    // Elements do not need to be unique in multiset,
    // so duplicates are allowed and counted.
    i = ms1.count(1);
    cout << "The number of elements in ms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = ms1.count(2);
    cout << "The number of elements in ms1 with a sort key of 2 is: "
         << i << "." << endl;

    i = ms1.count(3);
    cout << "The number of elements in ms1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in ms1 with a sort key of 1 is: 2.
The number of elements in ms1 with a sort key of 2 is: 1.
The number of elements in ms1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multiset::crbegin

반전된 multiset에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

반전된 multiset의 첫 번째 요소에 대한 주소를 지정하거나, 반전 해제된 multiset의 마지막 요소에 대한 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>주의

`crbegin`은 multiset에서 begin이 사용되는 것처럼 역방향 multiset에 사용됩니다.

반환 값이 `crbegin`이면 multiset 개체를 수정할 수 없습니다.

`crbegin`은 multiset를 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multiset_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

```Output
The first element in the reversed multiset is 30.
```

## <a name="crend"></a>  multiset::crend

역방향 multiset에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 multiset에서 마지막 요소 다음의 위치(정방향 multiset의 첫 번째 요소 앞의 위치) 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>주의

`crend`는 multiset에서 [end](#end)가 사용되는 것처럼 역방향 multiset에 사용됩니다.

반환 값이 `crend`이면 multiset 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 multiset 끝에 도달했는지를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// multiset_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crend( ) ;
   ms1_crIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>  multiset::difference_type

반복기가 가리키는 요소 사이의 범위에 있는 multiset의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>주의

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 [ `first`, `last`) 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소와 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;

   ms1.insert( 20 );
   ms1.insert( 10 );
   ms1.insert( 20 );

   ms1_bIter = ms1.begin( );
   ms1_eIter = ms1.end( );

   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );

   // The keys, and hence the elements, of a multiset are not unique
   cout << "The number '5' occurs " << df_typ5
        << " times in multiset ms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in multiset ms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in multiset ms1.\n";

   // Count the number of elements in a multiset
   multiset <int>::difference_type  df_count = 0;
   ms1_Iter = ms1.begin( );
   while ( ms1_Iter != ms1_eIter)
   {
      df_count++;
      ms1_Iter++;
   }

   cout << "The number of elements in the multiset ms1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in multiset ms1.
The number '10' occurs 1 times in multiset ms1.
The number '20' occurs 2 times in multiset ms1.
The number of elements in the multiset ms1 is: 3.
```

## <a name="emplace"></a>  multiset::emplace

배치 힌트를 사용하여 생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|*args*|multiset에 삽입할 요소를 생성하기 위해 전달되는 인수입니다.|

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

### <a name="remarks"></a>주의

이 함수는 컨테이너 요소에 대한 참조는 무효화하지 않지만 컨테이너에 대한 모든 반복기는 무효화할 수 있습니다.

배치 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다.

### <a name="example"></a>예제

```cpp
// multiset_emplace.cpp
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
    multiset<string> s1;

    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;

    s1.emplace("Bob");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="emplace_hint"></a>  multiset::emplace_hint

배치 힌트를 사용하여 생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|*args*|multiset에 삽입할 요소를 생성하기 위해 전달되는 인수입니다.|
|*where*|올바른 삽입 지점 검색을 시작할 위치입니다. *이 지점이 바로 앞에*오면 로그 시간 대신 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.|

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

### <a name="remarks"></a>주의

이 함수는 컨테이너 요소에 대한 참조는 무효화하지 않지만 컨테이너에 대한 모든 반복기는 무효화할 수 있습니다.

배치 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다.

코드 예제를 보려면 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)를 참조하세요.

## <a name="empty"></a>  multiset::empty

multiset가 비어 있는지를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

multiset가 비어 있으면 **true**이고 비어 있지 않으면 **false**입니다.

### <a name="example"></a>예제

```cpp
// multiset_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2;
   ms1.insert ( 1 );

   if ( ms1.empty( ) )
      cout << "The multiset ms1 is empty." << endl;
   else
      cout << "The multiset ms1 is not empty." << endl;

   if ( ms2.empty( ) )
      cout << "The multiset ms2 is empty." << endl;
   else
      cout << "The multiset ms2 is not empty." << endl;
}
```

```Output
The multiset ms1 is not empty.
The multiset ms2 is empty.
```

## <a name="end"></a>  multiset::end

마지막 바로 다음 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

마지막 바로 다음 반복기입니다. multiset이 비어 있으면 `multiset::end() == multiset::begin()`입니다.

### <a name="remarks"></a>주의

**end**는 반복기가 multiset의 끝을 통과했는지를 테스트하는 데 사용됩니다.

**end**에서 반환한 값을 역참조해서는 안 됩니다.

코드 예제를 보려면 [multiset::find](#find)를 참조하세요.

## <a name="equal_range"></a>  multiset::equal_range

지정된 키보다 더 큰 키를 가진 multiset의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 multiset의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키* \
검색 중인 multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

멤버 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **first**를 사용하고 하한 반복기를 역참조하려면 \*( `pr`. **first**)를 사용합니다. 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **second**를 사용하고 상한 반복기를 역참조하려면 \*( `pr`. **second**)를 사용합니다.

### <a name="example"></a>예제

```cpp
// multiset_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multiset<int, less<int> > IntSet;
   IntSet ms1;
   multiset <int> :: const_iterator ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = ms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.second ) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.first ) << "." << endl;

   // Compare the upper_bound called directly
   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *ms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = ms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key less than 40." << endl;
   else
      cout << "The element of multiset ms1 with a key >= 40 is: "
                << *( p1.first ) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The multiset ms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  multiset::erase

지정된 위치에서 multiset의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

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

*Where* \
제거할 요소의 위치입니다.

*첫 번째* \
제거할 첫 번째 요소의 위치입니다.

*마지막* \
제거할 마지막 요소 바로 다음 위치입니다.

*키* \
제거할 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

처음 두 구성원 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 multiset의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 구성원 함수의 경우 multiset에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>주의

코드 예제를 보려면 [set::erase](../standard-library/set-class.md#erase)를 참조하세요.

## <a name="find"></a>  multiset::find

지정된 키와 같은 키를 포함하는 multiset 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키* \
검색 중인 multiset에서 요소의 정렬 키와 일치 여부를 확인할 키 값입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 multiset의 마지막 요소(`multiset::end()`) 다음 위치를 가리키는 반복기입니다.

### <a name="remarks"></a>주의

멤버 함수는 작음 비교 가능 보다 작음 관계를 기반으로 순서를 지정 하는 이진 조건자의 인수 *키* 와 동일한 키를 갖는 multiset의 요소를 참조 하는 반복기를 반환 합니다.

@No__t_0의 반환 값이 `const_iterator`에 할당 된 경우에는 multiset 개체를 수정할 수 없습니다. @No__t_0의 반환 값이 `iterator`에 할당 되는 경우 multiset 개체를 수정할 수 있습니다.

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
    multiset<int> s1({ 40, 45 });
    cout << "The starting multiset s1 is: " << endl;
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

    cout << "The modified multiset s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a>  multiset::get_allocator

multiset를 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

multiset에서 사용되는 할당자입니다.

### <a name="remarks"></a>주의

multiset 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// multiset_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int>::allocator_type ms1_Alloc;
   multiset <int>::allocator_type ms2_Alloc;
   multiset <double>::allocator_type ms3_Alloc;
   multiset <int>::allocator_type ms4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multiset <int> ms1;
   multiset <int, allocator<int> > ms2;
   multiset <double, allocator<double> > ms3;

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms3.max_size( ) <<  "." << endl;

   // The following lines create a multiset ms4
   // with the allocator of multiset ms1
   ms1_Alloc = ms1.get_allocator( );
   multiset <int> ms4( less<int>( ), ms1_Alloc );
   ms4_Alloc = ms4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( ms1_Alloc == ms4_Alloc )
   {
      cout << "Allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "Allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  multiset::insert

multiset에 요소 또는 요소의 범위를 삽입합니다.

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

|매개 변수|설명|
|-|-|
|*Val*|multiset에 삽입할 요소의 값입니다.|
|*Where*|올바른 삽입 지점 검색을 시작할 위치입니다. *이 지점이 바로 앞에*오면 로그 시간 대신 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.|
|*ValTy*|Multiset가 [value_type](../standard-library/map-class.md#value_type)의 요소를 생성 하는 데 사용할 수 있는 인수 형식을 지정 하 고 *Val* 을 인수로 사용 하는 템플릿 매개 변수입니다.|
|*첫째*|복사할 첫 번째 요소의 위치입니다.|
|*마지막*|복사할 마지막 요소 바로 다음 위치입니다.|
|*InputIterator*|[value_type](../standard-library/map-class.md#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.|
|*IList*|요소를 복사할 원본 [initializer_list](../standard-library/initializer-list.md)입니다.|

### <a name="return-value"></a>반환 값

단일 요소 삽입 멤버 함수 (1) 및 (2)는 multiset에 새 요소를 삽입한 위치로 반복기를 반환합니다.

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 multiset에 새 요소를 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>주의

이 함수는 어떠한 포인터 또는 참조를 무효화하지 않지만 컨테이너에 대한 모든 반복기를 무효화할 수 있습니다.

요소를 한 개만 삽입하는 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

컨테이너의 [value_type](../standard-library/map-class.md#value_type)은 컨테이너에 속한 형식 정의이고 set의 경우 `multiset<V>::value_type`은 `const V` 형식입니다.

범위 멤버 함수 (5)는 `[First, Last)` 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 multiset에 요소 값의 시퀀스를 입력하므로 `Last`는 삽입되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `s.insert(v.begin(), v.end());` 문은 `v`의 모든 요소를 `s`에 삽입합니다.

이니셜라이저 목록 구성원 함수 (6)은 [initializer_list](../standard-library/initializer-list.md)를 사용하여 요소를 multiset로 복사합니다.

생성된 요소를 제 위치에 삽입하려면, 즉 복사 또는 이동 작업을 수행하지 않으려면 [multiset::emplace](#emplace) 및 [multiset::emplace_hint](#emplace_hint)를 참조하세요.

### <a name="example"></a>예제

```cpp
// multiset_insert.cpp
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
    multiset<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original multiset values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    s1.insert(1);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multiset<int> s2;
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

    cout << "The modified multiset values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    multiset<string>  s3;
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

    multiset<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a>  multiset::iterator

multiset의 모든 요소를 읽을 수 있는 상수 [양방향 반복기](../standard-library/bidirectional-iterator-tag-struct.md)를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>예제

`iterator`을 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="key_comp"></a>  multiset::key_comp

multiset에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

multiset가 요소의 순서를 지정하는 데 사용하는 함수 개체(템플릿 매개 변수 `Compare`)를 반환합니다.

`Compare`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="remarks"></a>주의

저장된 개체는 구성원 함수

**bool operator**( **const Key&** *x*, **const Key&** *y*);

를 정의합니다. 이 함수는 정렬 순서에서 *x*가 엄격하게 *y* 앞에 오면 true를 반환합니다.

[key_compare](#key_compare)와 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 `Compare`와 동일한 의미입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// multiset_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;
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
           << "where kc1 is the function object of ms1."
           << endl;
   }

   multiset <int, greater<int> > ms2;
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.
```

## <a name="key_compare"></a>  multiset::key_compare

multiset의 두 요소 간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>주의

`key_compare`는 템플릿 매개 변수 `Compare`의 동의어입니다.

`Compare`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="key_type"></a>  multiset::key_type

multiset의 두 요소 간 상대적 순서를 결정하는 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>주의

`key_type`는 템플릿 매개 변수 `Key`의 동의어입니다.

`Key`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`key_type`를 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="lower_bound"></a>  multiset::lower_bound

multiset에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키* \
검색 중인 multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키 보다 크거나 같은 키를 포함 하는 multiset 내 요소의 위치 주소를 가져오거나, 키와 일치 하는 항목이 없는 경우 multiset에서 마지막 요소 다음 위치의 주소를 나타내는 `iterator` 또는 `const_iterator`입니다.

### <a name="example"></a>예제

```cpp
// multiset_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.lower_bound( 20 );
   cout << "The element of multiset ms1 with a key of 20 is: "
        << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of multiset ms1 with a key of 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.end( );
   ms1_AcIter--;
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );
   cout << "The element of ms1 with a key matching "
        << "that of the last element is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The element of multiset ms1 with a key of 20 is: 20.
The multiset ms1 doesn't have an element with a key of 40.
The element of ms1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  multiset::max_size

multiset의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

multiset의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// multiset_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::size_type i;

   i = ms1.max_size( );
   cout << "The maximum possible length "
        << "of the multiset is " << i << "." << endl;
}
```

## <a name="multiset"></a>  multiset::multiset

비어 있거나 다른 multiset의 전체 또는 일부분에 대한 복사본인 multiset를 생성합니다.

```cpp
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|*Al*|이 multiset 개체에 사용할 스토리지 할당자 클래스로, 기본값은 `Allocator`입니다.|
|*생략*|multiset의 요소 순서를 지정하는 데 사용되는 `const Compare` 형식의 비교 함수로, 기본값은 `Compare`입니다.|
|*오른쪽*|생성된 multiset가 복사본으로 지정될 multiset입니다.|
|*첫째*|복사할 요소의 범위에서 첫 번째 요소의 위치입니다.|
|*마지막*|복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.|
|*IList*|요소를 복사해올 initializer_list입니다.|

### <a name="remarks"></a>주의

모든 생성자는 multiset의 메모리 스토리지를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 multiset를 초기화합니다.

모든 생성자는 multiset의 키 간 순서를 설정하는 데 사용되며 나중에 [key_comp](#key_comp)를 호출하여 반환할 수 있는 Compare 형식의 함수 개체를 저장합니다.

처음 세 생성자는 빈 초기 multiset를 지정 하 고, 두 번째 생성자는 요소의 순서를 설정 하는 데 사용할 비교 함수 (*Comp* *)의*형식을 지정 하며, 세 번째 생성자는 됩니다. **explicit** 키워드를 사용하는 경우 특정 종류의 자동 형식 변환이 수행되지 않습니다.

네 번째 생성자는 multiset *오른쪽*의 복사본을 지정 합니다.

다섯 번째 생성자는 *Right*를 이동 하 여 multiset의 복사본을 지정 합니다.

여섯 번째, 일곱 번째 및 여덟 번째 생성자는 요소를 복사할 원본 initializer_list를 지정합니다.

다음 3개 생성자는 multiset의 범위 `[First, Last)`를 복사하며, 비교 함수 및 할당자 형식을 지정하는 명시도는 계속 높아집니다.

### <a name="example"></a>예제

```cpp
// multiset_ctor.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;

    // Create an empty multiset ms0 of key type integer
    multiset <int> ms0;

    // Create an empty multiset ms1 with the key comparison
    // function of less than, then insert 4 elements
    multiset <int, less<int> > ms1;
    ms1.insert(10);
    ms1.insert(20);
    ms1.insert(20);
    ms1.insert(40);

    // Create an empty multiset ms2 with the key comparison
    // function of greater than, then insert 2 elements
    multiset <int, less<int> > ms2;
    ms2.insert(10);
    ms2.insert(20);

    // Create a multiset ms3 with the
    // allocator of multiset ms1
    multiset <int>::allocator_type ms1_Alloc;
    ms1_Alloc = ms1.get_allocator();
    multiset <int> ms3(less<int>(), ms1_Alloc);
    ms3.insert(30);

    // Create a copy, multiset ms4, of multiset ms1
    multiset <int> ms4(ms1);

    // Create a multiset ms5 by copying the range ms1[ first,  last)
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;
    ms1_bcIter = ms1.begin();
    ms1_ecIter = ms1.begin();
    ms1_ecIter++;
    ms1_ecIter++;
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);

    // Create a multiset ms6 by copying the range ms4[ first,  last)
    // and with the allocator of multiset ms2
    multiset <int>::allocator_type ms2_Alloc;
    ms2_Alloc = ms2.get_allocator();
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);

    cout << "ms1 =";
    for (auto i : ms1)
        cout << " " << i;
    cout << endl;

    cout << "ms2 =";
    for (auto i : ms2)
        cout << " " << i;
   cout << endl;

   cout << "ms3 =";
   for (auto i : ms3)
       cout << " " << i;
    cout << endl;

    cout << "ms4 =";
    for (auto i : ms4)
        cout << " " << i;
    cout << endl;

    cout << "ms5 =";
    for (auto i : ms5)
        cout << " " << i;
    cout << endl;

    cout << "ms6 =";
    for (auto i : ms6)
        cout << " " << i;
    cout << endl;

    // Create a multiset by moving ms5
    multiset<int> ms7(move(ms5));
    cout << "ms7 =";
    for (auto i : ms7)
        cout << " " << i;
    cout << endl;

    // Create a multiset with an initializer_list
    multiset<int> ms8({1, 2, 3, 4});
    cout << "ms8=";
    for (auto i : ms8)
        cout << " " << i;
    cout << endl;
}
```

## <a name="op_eq"></a>  multiset::operator=

다른 `multiset`의 요소를 사용하여 이 `multiset`의 요소를 대체합니다.

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|*right*|요소를 복사하거나 이동하는 원본 `multiset`입니다.|

### <a name="remarks"></a>주의

사용 되는 참조 형식 (lvalue 또는 rvalue)에 따라 *오른쪽* 의 요소를이 `multiset` 복사 하거나 이동 `operator=`. `operator=`가 실행되기 전에 이 `multiset`에 있는 요소가 삭제됩니다.

### <a name="example"></a>예제

```cpp
// multiset_operator_as.cpp
// compile with: /EHsc
#include <multiset>
#include <iostream>

int main( )
   {
   using namespace std;
   multiset<int> v1, v2, v3;
   multiset<int>::iterator iter;

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

## <a name="pointer"></a>  multiset::pointer

multiset에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>주의

형식 **pointer**는 요소값을 수정할 때 사용할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 multiset 개체의 요소에 액세스해야 합니다.

## <a name="rbegin"></a>  multiset::rbegin

반전된 multiset에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

반전된 multiset의 첫 번째 요소에 대한 주소를 지정하거나, 반전 해제된 multiset의 마지막 요소에 대한 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>주의

`rbegin`은 multiset에서 rbegin이 사용되는 것처럼 역방향 multiset에 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 multiset 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 multiset 개체를 수정할 수 있습니다.

`rbegin`은 multiset를 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multiset_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a multiset in a forward order
   cout << "The multiset is:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is:";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << " " << *ms1_rIter;
   cout << endl;

   // A multiset element can be erased by dereferencing to its key
   ms1_rIter = ms1.rbegin( );
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multiset is "<< *ms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed multiset is 30.
The multiset is: 10 20 30
The reversed multiset is: 30 20 10
After the erasure, the first element in the reversed multiset is 20.
```

## <a name="reference"></a>  multiset::reference

multiset에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>예제

```cpp
// multiset_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="rend"></a>  multiset::rend

역방향 multiset에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 multiset에서 마지막 요소 다음의 위치(정방향 multiset의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>주의

`rend`는 multiset에서 [end](#end)가 사용되는 것처럼 역방향 multiset에 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 multiset 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 multiset 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 multiset 끝에 도달했는지를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// multiset_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rend( ) ;
   ms1_rIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a multiset in a forward order
   cout << "The multiset is: ";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << *ms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is: ";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << *ms1_rIter << " ";
   cout << "." << endl;

   ms1_rIter = ms1.rend( );
   ms1_rIter--;
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rend( );
   --ms1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed multiset is " << *ms1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>  multiset::reverse_iterator

역방향 multiset의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>주의

`reverse_iterator` 형식은 multiset를 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="size"></a>  multiset::size

multiset에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

multiset의 현재 길이입니다.

### <a name="example"></a>예제

```cpp
// multiset_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: size_type i;

   ms1.insert( 1 );
   i = ms1.size( );
   cout << "The multiset length is " << i << "." << endl;

   ms1.insert( 2 );
   i = ms1.size( );
   cout << "The multiset length is now " << i << "." << endl;
}
```

```Output
The multiset length is 1.
The multiset length is now 2.
```

## <a name="size_type"></a>  multiset::size_type

multiset에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="swap"></a>  multiset::swap

두 multiset의 요소를 교환합니다.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽* \
대상 multiset와 교환할 요소를 제공하는 인수 집합입니다.

### <a name="remarks"></a>주의

구성원 함수는 해당 요소를 교환할 두 multiset의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// multiset_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2, ms3;
   multiset <int>::iterator ms1_Iter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );
   ms2.insert( 100 );
   ms2.insert( 200 );
   ms3.insert( 300 );

   cout << "The original multiset ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the member function version of swap
   ms1.swap( ms2 );

   cout << "After swapping with ms2, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the specialized template version of swap
   swap( ms1, ms3 );

   cout << "After swapping with ms3, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original multiset ms1 is: 10 20 30.
After swapping with ms2, list ms1 is: 100 200.
After swapping with ms3, list ms1 is: 300.
```

## <a name="upper_bound"></a>  multiset::upper_bound

multiset에 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키* \
검색 중인 multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 큰 키가 들어 있는 multiset 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 multiset에서 마지막 요소 다음 위치의 주소를 지정하는 **반복기** 또는 `const_iterator`입니다.

### <a name="example"></a>예제

```cpp
// multiset_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "The first element of multiset ms1 with a key greater "
           << "than 20 is: " << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key greater than 30." << endl;
   else
      cout << "The element of multiset ms1 with a key > 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.begin( );
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );
   cout << "The first element of ms1 with a key greater than"
        << endl << "that of the initial element of ms1 is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The first element of multiset ms1 with a key greater than 20 is: 30.
The multiset ms1 doesn't have an element with a key greater than 30.
The first element of ms1 with a key greater than
that of the initial element of ms1 is: 20.
```

## <a name="value_comp"></a>  multiset::value_comp

multiset에서 요소값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

multiset가 요소의 순서를 지정하는 데 사용하는 함수 개체(템플릿 매개 변수 `Compare`)를 반환합니다.

`Compare`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="remarks"></a>주의

저장된 개체는 구성원 함수

**bool operator**( **const Key&** `_xVal`, **const Key&** `_yVal`);

를 정의합니다. 이 함수는 `_xVal`이 앞에 오며 정렬 순서가 `_yVal`과 같지 않으면 true를 반환합니다.

[key_compare](#key_compare)와 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 `Compare`와 동일한 의미입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// multiset_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of ms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of ms1."
           << endl;
   }

   set <int, greater<int> > ms2;
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.
```

## <a name="value_compare"></a>  multiset::value_compare

두 요소를 정렬 키로 비교하여 multiset에서 상대적 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>주의

`value_compare`는 템플릿 매개 변수 `Compare`의 동의어입니다.

[Key_compare](#key_compare) 및 `value_compare`는 모두 템플릿 매개 변수 `Compare`의 동의어입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

`Compare`에 대한 자세한 내용은 [multiset 클래스](../standard-library/multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`value_compare`를 선언하고 사용하는 방법의 예제는 [value_comp](#value_comp)의 예제를 참조하세요.

## <a name="value_type"></a>  multiset::value_type

해당 용량 내에서 multiset의 요소로 저장된 개체를 값으로 설명하는 형식입니다.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>주의

`value_type`는 템플릿 매개 변수 `Key`의 동의어입니다.

[Key_type](#key_type) 및 `value_type`는 모두 템플릿 매개 변수 `Key`의 동의어입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

`Key`에 대한 자세한 내용은 이 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

```cpp
// multiset_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;

   multiset <int> :: value_type svt_Int;   // Declare value_type
   svt_Int = 10;             // Initialize value_type

   multiset <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   ms1.insert( svt_Int );         // Insert value into s1
   ms1.insert( skt_Int );         // Insert key into s1

   // A multiset accepts key_types or value_types as elements
   cout << "The multiset has elements:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;
}
```

```Output
The multiset has elements: 10 20.
```

## <a name="see-also"></a>참조

[컨테이너](../cpp/containers-modern-cpp.md)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
