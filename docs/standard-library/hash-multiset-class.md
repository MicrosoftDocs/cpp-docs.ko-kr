---
description: Hash_multiset 클래스에 대해 자세히 알아보세요.
title: hash_multiset 클래스
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 567eef22098b99cf3a3109bfd911ecbcd518876b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231812"
---
# <a name="hash_multiset-class"></a>hash_multiset 클래스

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

컨테이너 클래스 hash_multiset은 C++ 표준 라이브러리의 확장이며, 포함된 요소의 값이 키 값으로 사용되며 고유할 필요가 없는 컬렉션에서 데이터를 저장하고 빠르게 검색하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_multiset에 저장되는 요소 데이터 형식입니다.

*특징이*\
두 요소 값을 정렬 키로 비교 하 여 상대 순서를 확인할 수 있는 이진 조건자 인 클래스 비교 중 하 나와 요소의 키 값을 형식의 부호 없는 정수에 매핑하는 단항 조건자 인 해시 함수의 두 함수 개체를 포함 하는 형식입니다 `size_t` . 이 인수는 선택 사항이며 기본값은 `hash_compare<Key, less<Key> >`입니다.

*할당자*\
hash_multiset의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<Key>`입니다.

## <a name="remarks"></a>설명

Hash_multiset은

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다. 또한 해당 요소 값은 키 값과 구별되므로 간단한 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 요소가 요소의 키 값에 적용된 해시 함수 값을 기반으로 하여 버킷으로 그룹화되기 때문에 해시됩니다.

- 각각의 요소가 반드시 고유한 키를 가지고 있어야 한다는 점에서 고유성을 갖고 있습니다. hash_multiset은 간단한 연관 컨테이너이기도 하므로 요소 역시 고유합니다.

- 제공 하는 기능이 제네릭이 고 요소 또는 키로 포함 된 데이터의 특정 형식과 독립적 이기 때문에 클래스 템플릿입니다. 요소에 사용될 데이터 형식과 키는 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

해시는 정렬보다 훨씬 효율적입니다. 성공적인 해시는 정렬 방식에 대한 컨테이너의 요소 수 로그에 비례하는 시간과 비교할 때 삽입, 삭제, 찾기를 일정한 평균 시간 이내에 수행합니다. set 요소의 값은 직접 변경할 수 없습니다. 대신, 이전 값을 삭제하고 새 값의 요소를 삽입해야 합니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 해시된 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 명시적으로 이러한 작업을 지원하는 멤버 함수는 잘 설계된 해시 함수와 함께 사용할 경우 효율적이며, 컨테이너의 요소 수에 종속되지 않는 일정한 평균 시간으로 작업을 수행합니다. 잘 설계된 해시 함수는 해시된 값의 균일한 분포를 생성하고 충돌 수를 최소화합니다. 여기서 충돌은 특정 키 값이 동일한 해시된 값에 매핑될 때 발생합니다. 가능한 최악의 해시 함수가 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간).

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 hash_multiset입니다. hash_multiset의 요소는 여러 개일 수 있고 자체 정렬 키로 사용되므로 키는 고유하지 않습니다. 이 형식의 구조에 대한 모델은 정렬된 목록입니다. 예를 들어, 단어 내의 단어가 두 번 이상 나타날 수 있습니다. 단어가 여러 번 나타날 수 있도록 허용되지 않은 경우 hash_set가 적절한 컨테이너 구조입니다. 고유 키 단어 목록에 고유 정의가 연결된 경우 이 데이터를 포함하기 위한 적절한 구조는 hash_map입니다. 대신, 정의가 고유하지 않은 경우는 hash_multimap이 적절한 컨테이너입니다.

hash_multiset은 형식 [value_compare](#value_compare)의 저장된 해시 특성 개체를 호출하여 제어하는 시퀀스를 정렬합니다. 이 저장된 개체는 [key_comp](#key_comp) 멤버 함수를 호출하여 액세스할 수 있습니다. 이러한 함수 개체는 클래스의 개체와 동일 하 게 동작 해야 합니다 `hash_compare<Key, less<Key> >` . 특히 형식의 모든 값 *키* 에 대해 `Key` 호출은 `Trait(Key)` 형식의 값 분포를 생성 합니다 `size_t` .

일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 *f*(*x*, *y*)는 두 인수 개체 x, y 및 반환 값 true 또는 false가 있는 함수 개체입니다. 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적인 경우 hash_multiset에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서, *f*(*x*, *y*)와 *f*(*y*, *x*)가 모두 false인 경우 x 및 y 두 개체는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 순서 지정 함수 및 컨테이너 개체에 저장된 해시 테이블의 현재 크기에 따라 달라집니다. 해시 테이블의 현재 크기를 확인할 수 없으므로 제어된 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

hash_multiset 클래스에서 제공하는 반복기는 양방향 반복기이지만, insert 및 hash_multiset 클래스 멤버 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항 hash_multiset이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 hash_multiset이지만, 클래스 멤버 함수의 맥락에서 반복기 범위(`first`, `last`)에 대해 설명하는 데에는 충분합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[hash_multiset](#hash_multiset)|비어 있거나 다른 `hash_multiset`의 전체 또는 일부의 복사본인 `hash_multiset`을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `hash_multiset` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_multiset` .|
|[const_pointer](#const_pointer)|의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `hash_multiset` .|
|[const_reference](#const_reference)|**`const`** `hash_multiset` 작업을 읽고 수행 하기 위해에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_multiset` .|
|[difference_type](#difference_type)|동일한 `hash_multiset` 안에서 요소를 다루는 두 반복기 사이의 차이를 제공하는 부호 있는 정수 형식입니다.|
|[iterator](#iterator)|`hash_multiset`에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[key_compare](#key_compare)|`hash_multiset`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|해당 용량 내 `hash_set` 요소로 저장된 개체를 정렬 키로 설명하는 형식입니다.|
|[놓고](#pointer)|`hash_multiset`의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`hash_multiset` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 `hash_multiset`의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|`hash_multiset`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_compare](#value_compare)|`hash_multiset`의 두 요소 값을 비교하여 상대 순서를 확인할 수 있는 클래스 비교의 이진 조건자와 요소를 해시하는 단항 조건자인 두 함수 개체를 제공하는 형식입니다.|
|[value_type](#value_type)|해당 용량 내 `hash_multiset` 요소로 저장된 개체를 값으로 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[시작](#begin)|`hash_multiset`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`hash_multiset`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`hash_multiset`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`hash_multiset`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `hash_multiset`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 `hash_multiset`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 `hash_multiset`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `hash_multiset`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `hash_multiset`에 삽입합니다.|
|[empty](#empty)|`hash_multiset`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`hash_multiset`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|지정된 키보다 더 큰 키를 가진 `hash_multiset`의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 `hash_multiset`의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.|
|[erase](#erase)|지정된 위치에서 `hash_multiset`의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `hash_multiset` 내 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `hash_multiset` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`hash_multiset`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_compare)|`hash_multiset`에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.|
|[lower_bound](#lower_bound)|`hash_multiset`에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`hash_multiset`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `hash_multiset`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `hash_multiset`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`hash_multiset`에 있는 요소 수를 반환합니다.|
|[스왑을](#swap)|두 `hash_multiset`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`hash_multiset`에서 지정된 키보다 같거나 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`hash_multiset`의 요소 키 값을 해시하고 정렬하는 데 사용되는 해시 특성 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[hash_multiset:: operator =](#op_eq)|hash_multiset의 요소를 다른 hash_multiset의 복사본으로 바꿉니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<hash_set>

**네임스페이스:** stdext

## <a name="hash_multisetallocator_type"></a><a name="allocator_type"></a> hash_multiset:: allocator_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="hash_multisetbegin"></a><a name="begin"></a> hash_multiset:: begin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

hash_multiset의 첫 번째 요소 또는 빈 hash_multiset 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 `begin` 할당 되는 경우 `const_iterator` hash_multiset 개체의 요소는 수정할 수 없습니다. 의 반환 값 `begin` 이에 할당 되는 경우 `iterator` hash_multiset 개체의 요소를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="hash_multisetcbegin"></a><a name="cbegin"></a> hash_multiset:: cbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

[hash_multiset](../standard-library/hash-multiset-class.md)의 첫 번째 요소 또는 빈 `hash_multiset` 다음의 위치 주소를 지정하는 상수 양방향 반복기입니다.

### <a name="remarks"></a>설명

`cbegin`의 반환 값을 사용하여 `hash_multiset` 개체의 요소를 수정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="hash_multisetcend"></a><a name="cend"></a> hash_multiset:: cend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

[hash_multiset](../standard-library/hash-multiset-class.md)에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 양방향 반복기입니다. `hash_multiset`이 비어 있으면 `hash_multiset::cend == hash_multiset::begin`입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 `hash_multiset`의 끝에 도달했는지 여부를 테스트하는 데 사용됩니다. `cend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="hash_multisetclear"></a><a name="clear"></a> hash_multiset:: clear

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="hash_multisetconst_iterator"></a><a name="const_iterator"></a> hash_multiset:: const_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

Hash_multiset의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_multisetconst_pointer"></a><a name="const_pointer"></a> hash_multiset:: const_pointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

Hash_multiset의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [const_iterator](#const_iterator) 를 사용 하 여 hash_multiset 개체의 요소에 액세스 해야 합니다 **`const`** .

## <a name="hash_multisetconst_reference"></a><a name="const_reference"></a> hash_multiset:: const_reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

**`const`** 작업을 읽고 수행 하기 위해 hash_multiset에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="hash_multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_multiset:: const_reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

Hash_multiset의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 hash_multiset을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="hash_multisetcount"></a><a name="count"></a> hash_multiset:: count

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

키가 매개 변수로 지정된 키와 일치하는 hash_multiset의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_multiset에서 일치하는지 확인할 요소의 키입니다.

### <a name="return-value"></a>반환 값

hash_multiset에서 개 변수로 지정된 키가 있는 요소 수입니다.

### <a name="remarks"></a>설명

멤버 함수가 다음 범위에 있는 요소의 수를 반환합니다.

\[ lower_bound(*key*), upper_bound(*key*) ).

### <a name="example"></a>예제

다음 예제에서는 hash_multiset:: count 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="hash_multisetcrbegin"></a><a name="crbegin"></a> hash_multiset:: crbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_multiset에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_multiset](../standard-library/hash-multiset-class.md)에서 첫 번째 요소 또는 정방향 `hash_multiset`에서 마지막 요소의 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 `hash_multiset`에서 [hash_multiset::begin](#begin)이 사용되는 것처럼 역방향 `hash_multiset`에 사용됩니다.

반환 값이 `crbegin`이면 `hash_multiset` 개체를 수정할 수 없습니다.

`crbegin`은 `hash_multiset`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="hash_multisetcrend"></a><a name="crend"></a> hash_multiset:: crend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_multiset에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_multiset](../standard-library/hash-multiset-class.md)에서 마지막 요소 다음의 위치(정방향 `hash_multiset`의 첫 번째 요소 앞의 위치) 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 `hash_multiset`에서 [hash_multiset::end](#end)가 사용되는 것처럼 역방향 `hash_multiset`에 사용됩니다.

반환 값이 `crend`이면 `hash_multiset` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 hash_multiset 끝에 도달했는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="hash_multisetdifference_type"></a><a name="difference_type"></a> hash_multiset::d ifference_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

동일한 hash_multiset 내에서 요소의 주소를 지정하는 두 반복기 사이의 차이를 제공하는 부호 있는 정수 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 [ `first`, `last`) 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소와 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector 또는 deque와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="hash_multisetemplace"></a><a name="emplace"></a> hash_multiset:: emplace

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

생성된 요소를 hash_multiset에 삽입합니다.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_multiset`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_multiset](../standard-library/hash-multiset-class.md)에 삽입될 요소의 값입니다.

### <a name="return-value"></a>반환 값

`emplace` 멤버 함수는 새 요소가 삽입된 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="hash_multisetemplace_hint"></a><a name="emplace_hint"></a> hash_multiset:: emplace_hint

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

배치 힌트를 사용하여 hash_multiset에 생성된 요소를 삽입합니다.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_multiset`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_multiset](../standard-library/hash-multiset-class.md)에 삽입될 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다. 삽입 지점이 바로 뒤에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 *있습니다.*

### <a name="return-value"></a>반환 값

[hash_multiset::emplace](#emplace) 멤버 함수는 새 요소를 `hash_multiset`에 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

삽입 지점이 *바로 뒤에* 오면 로그 시간 대신 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="hash_multisetempty"></a><a name="empty"></a> hash_multiset:: empty

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** hash_multiset 비어 있으면이 고, 그렇지 않으면입니다. **`false`** hash_multiset 비어 있지 않으면입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="hash_multisetend"></a><a name="end"></a> hash_multiset:: end

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

hash_multiset에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 양방향 반복기입니다. hash_multiset이 비어 있으면 hash_multiset::end == hash_multiset::begin입니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 hash_multiset의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다. `end`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="hash_multisetequal_range"></a><a name="equal_range"></a> hash_multiset:: equal_range

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키보다 더 큰 키를 가진 hash_multiset의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 hash_multiset의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

멤버 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **첫째** , 하 한 반복기를 역참조 하려면 \* ()를 사용 `pr` 합니다. **첫 번째**). 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **둘째** , 상한 반복기를 역참조 하려면 (를 사용 \* `pr` 합니다. **second**).

### <a name="example"></a>예제

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="hash_multiseterase"></a><a name="erase"></a> hash_multiset:: erase

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

지정된 위치에서 hash_multiset의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>매개 변수

*위치*\
hash_multiset에서 제거할 요소의 위치입니다.

*기본*\
hash_multiset에서 제거된 첫 번째 요소의 위치입니다.

*최신*\
hash_multiset에서 제거된 마지막 요소 바로 뒤의 위치입니다.

*키인지*\
hash_multiset에서 제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소를 지정하는 양방향 반복기이거나 이러한 요소가 없을 경우 hash_multiset의 끝에 대한 포인터입니다. 세 번째 멤버 함수의 경우 hash_multiset에서 제거된 요소의 수입니다.

### <a name="remarks"></a>설명

멤버 함수는 예외를 throw하지 않습니다.

### <a name="example"></a>예제

다음 예제에서는 hash_multiset::erase 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="hash_multisetfind"></a><a name="find"></a> hash_multiset:: find

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키와 같은 키를 가진 hash_multiset 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multiset에서 요소의 정렬 키와 일치 여부를 확인할 인수 키입니다.

### <a name="return-value"></a>반환 값

지정된 키에 해당하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 hash_multiset의 마지막 요소 다음 위치에 대한 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

### <a name="remarks"></a>설명

멤버 함수는 hash_multiset의 요소를 주소 지정 하는 반복기를 반환 합니다 .이 요소는 정렬 키가 `equivalent` 보다 작음 작음 비교 가능 관계를 기준으로 순서를 지정 하는 이진 조건자 아래의 인수 키에 해당 합니다.

의 반환 값이에 할당 된 경우에는 `find` `const_iterator` hash_multiset 개체를 수정할 수 없습니다. 의 반환 값 `find` 이에 할당 되는 경우 `iterator` hash_multiset 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="hash_multisetget_allocator"></a><a name="get_allocator"></a> hash_multiset:: get_allocator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

hash_multiset에서 메모리를 관리하는 데 사용하는 할당자(클래스의 템플릿 매개 변수 `Allocator`)입니다.

`Allocator`에 대한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="remarks"></a>설명

hash_multiset 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_multisethash_multiset"></a><a name="hash_multiset"></a> hash_multiset:: hash_multiset

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

비어 있거나 다른 `hash_multiset`의 전체 또는 일부의 복사본인 `hash_multiset`을 생성합니다.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 `hash_multiset` 개체에 사용할 스토리지 할당자 클래스로, 기본값은 `Allocator`입니다.

*생략*\
`hash_multiset`의 요소 순서를 지정하는 데 사용되는 `const Traits` 형식의 비교 함수로, 기본값은 `hash_compare`입니다.

*오른쪽*\
생성된 `hash_multiset`이 복사본으로 지정될 `hash_multiset`입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
복사할 요소가 포함된 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 `hash_multiset`의 메모리 스토리지를 관리하며 나중에 [hash_multiset::get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 hash_multiset을 초기화합니다.

모든 생성자는 `hash_multiset`의 키 간 순서를 설정하는 데 사용되며 나중에 [hash_multiset::key_comp](#key_comp)를 호출하여 반환할 수 있는 `Traits` 형식의 함수 개체를 저장합니다. `Traits`에 대한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목을 참조하세요.

처음 세 생성자는 빈 초기를 지정 하 `hash_multiset` 고, 두 번째 생성자는 요소의 순서를 설정 하는 데 사용할 비교 함수 (*Comp*)의 형식을 지정 하며, 세 번째 생성자는 사용할 할당자 형식 (*Al*)을 명시적으로 지정 합니다. 키워드는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 생성자는 `hash_multiset` `Right`를 이동합니다.

다섯 번째, 여섯 번째 및 일곱 번째 생성자에는 initializer_list가 사용됩니다.

마지막 3개 생성자는 `hash_multiset`의 범위 [`first`, `last`)를 복사하며, 범위 내에서 클래스 Compare 및 allocator의 비교 함수 형식을 지정하는 명시도는 계속 높아집니다.

해시된 set 컨테이너에 있는 요소의 실제 순서는 해시 함수, 순서 지정 함수 및 해시 테이블의 현재 크기에 따라 달라지고, 일반적으로 순서 지정 함수에 의해서만 결정된 경우 set 컨테이너에서 예상 가능하던 것처럼 실제 순서를 예상할 수는 없습니다.

## <a name="hash_multisetinsert"></a><a name="insert"></a> hash_multiset:: insert

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에 요소 또는 요소의 범위를 삽입합니다.

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>매개 변수

*기본값*\
hash_multiset이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 hash_multiset에 삽입될 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다. 삽입 지점이 바로 뒤에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 *있습니다.*

*기본*\
hash_multiset에서 복사할 첫 번째 요소의 위치입니다.

*최신*\
hash_multiset에서 복사할 마지막 요소 바로 다음 위치입니다.

*IList*\
복사할 요소가 포함된 initializer_list입니다.

### <a name="return-value"></a>반환 값

처음 두 insert 멤버 함수는 새 요소가 삽입된 위치를 가리키는 반복기를 반환합니다.

다음 3개 멤버 함수에는 initializer_list가 사용됩니다.

세 번째 멤버 함수는 지정된 hash_multiset의 [`first`, `last`) 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 hash_multiset에 요소 값의 시퀀스를 삽입합니다.

### <a name="remarks"></a>설명

삽입 지점이 *바로 뒤에* 오면 로그 시간 대신 insert의 힌트 버전에 대 한 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

## <a name="hash_multisetiterator"></a><a name="iterator"></a> hash_multiset:: iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>설명

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

`iterator`을 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_multisetkey_comp"></a><a name="key_comp"></a> hash_multiset:: key_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

컨테이너의 요소를 해시 하 고 정렬 하는 데 사용 되는 함수 개체를 포함 하는 hash_multiset 템플릿 매개 변수 *특성* 을 반환 합니다.

*특성* 에 대 한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 멤버 함수

`bool operator<(const Key& _xVal, const Key& _yVal);`

**`true`** `_xVal` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[key_compare](#key_compare)와 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 *Traits* 와 동일한 의미입니다. 두 형식 모두 hash_multiset 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="hash_multisetkey_compare"></a><a name="key_compare"></a> hash_multiset:: key_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 두 요소 값을 비교하여 상대 순서를 확인할 수 있는 클래스 비교의 이진 조건자와 요소를 해시하는 단항 조건자인 두 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare` 는 템플릿 매개 변수 *특성* 의 동의어입니다.

*특성* 에 대 한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목을 참조 하세요.

`key_compare` 및 value_compare는 둘 다 템플릿 매개 변수 *Traits* 와 동일한 의미입니다. 두 형식 모두 hash_set 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="hash_multisetkey_type"></a><a name="key_type"></a> hash_multiset:: key_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 두 요소 간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type` 는 템플릿 매개 변수 *키* 의 동의어입니다.

`key_type` 및 [value_type](../standard-library/hash-set-class.md#value_type)은 둘 다 템플릿 매개 변수 *Key* 의 동의어입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

*키* 에 대 한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목의 설명 섹션을 참조 하세요.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_multisetlower_bound"></a><a name="lower_bound"></a> hash_multiset:: lower_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 hash_multiset 내 첫 번째 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_multiset에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="hash_multisetmax_size"></a><a name="max_size"></a> hash_multiset:: max_size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

hash_multiset의 최대 허용 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="hash_multisetoperator"></a><a name="op_eq"></a> hash_multiset:: operator =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 요소를 다른 hash_multiset의 복사본으로 바꿉니다.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`hash_multiset`에 복사되는 [hash_multiset](../standard-library/hash-multiset-class.md)입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `hash_multiset` 는 `operator=` 의 내용을로 복사 하거나 이동  `hash_multiset` 합니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="hash_multisetpointer"></a><a name="pointer"></a> hash_multiset::p ointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 multiset 개체의 요소에 액세스해야 합니다.

## <a name="hash_multisetrbegin"></a><a name="rbegin"></a> hash_multiset:: rbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_multiset에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 hash_multiset에서 첫 번째 요소 또는 정방향 hash_multiset에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 [begin](#begin)이 hash_multiset에서 사용되는 것처럼 역방향 hash_multiset에서 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 hash_multiset 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우 hash_multiset 개체를 수정할 수 있습니다.

`rbegin`은 hash_multiset을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreference"></a><a name="reference"></a> hash_multiset:: reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="hash_multisetrend"></a><a name="rend"></a> hash_multiset:: rend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_multiset에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 hash_multiset에서 마지막 요소 다음의 위치(정방향 hash_multiset의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 [end](#end)가 hash_multiset에서 사용되는 것처럼 역방향 hash_multiset에서 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 hash_multiset 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우 hash_multiset 개체를 수정할 수 있습니다. `rend`에서 반환한 값은 역참조되지 않아야 합니다.

`rend`를 사용하여 역방향 반복기가 hash_multiset 끝에 도달했는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreverse_iterator"></a><a name="reverse_iterator"></a> hash_multiset:: reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_multiset의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 hash_multiset을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="hash_multisetsize"></a><a name="size"></a> hash_multiset:: size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

hash_multiset의 현재 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="hash_multisetsize_type"></a><a name="size_type"></a> hash_multiset:: size_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="hash_multisetswap"></a><a name="swap"></a> hash_multiset:: swap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_multiset의 요소를 교환합니다.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 hash_multiset과 교환할 요소를 제공하는 인수 hash_multiset입니다.

### <a name="remarks"></a>설명

멤버 함수는 해당 요소를 교환할 두 hash_multiset의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="hash_multisetupper_bound"></a><a name="upper_bound"></a> hash_multiset:: upper_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multiset에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 큰 키가 들어 있는 hash_multiset 내 첫 번째 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_multiset에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="hash_multisetvalue_comp"></a><a name="value_comp"></a> hash_multiset:: value_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

컨테이너의 요소를 해시 하 고 정렬 하는 데 사용 되는 함수 개체를 포함 하는 hash_multiset 템플릿 매개 변수 *특성* 을 반환 합니다.

*특성* 에 대 한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 멤버 함수

**bool operator**( **constKey&**`_xVal`, **const Key&** *_yVal*);을

**`true`** `_xVal` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[key_compare](#key_compare)와 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 *Traits* 와 동일한 의미입니다. 두 형식 모두 hash_multiset 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="hash_multisetvalue_compare"></a><a name="value_compare"></a> hash_multiset:: value_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

hash_multiset의 두 요소 값을 비교하여 상대 순서를 확인할 수 있는 클래스 비교의 이진 조건자와 요소를 해시하는 단항 조건자인 두 함수 개체를 제공하는 형식입니다.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>설명

`value_compare` 는 템플릿 매개 변수 *특성* 의 동의어입니다.

*특성* 에 대 한 자세한 내용은 [hash_multiset 클래스](../standard-library/hash-multiset-class.md) 항목을 참조 하세요.

[Key_compare](#key_compare) 와는 모두 `value_compare` 템플릿 매개 변수 *특성* 의 동의어입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

`value_compare`를 선언하고 사용하는 방법의 예제는 [value_comp](#value_comp)의 예제를 참조하세요.

## <a name="hash_multisetvalue_type"></a><a name="value_type"></a> hash_multiset:: value_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 대신 사용하는 것이 좋습니다.

해당 용량 내에서 hash_multiset의 요소로 저장된 개체를 값으로 설명하는 형식입니다.

```cpp
typedef Key value_type;
```

### <a name="example"></a>예제

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
