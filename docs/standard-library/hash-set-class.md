---
description: Hash_set 클래스에 대해 자세히 알아보세요.
title: hash_set 클래스
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
ms.openlocfilehash: 36bcb0e1f35fd8012ad1398a481bdae17b6d1424
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324098"
---
# <a name="hash_set-class"></a>hash_set 클래스

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

컨테이너 클래스 hash_set은 C++ 표준 라이브러리의 확장이며, 포함된 요소의 값이 고유하고 키 값으로 사용되는 컬렉션에서 데이터를 스토리지하고 빠르게 검색하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_set에 저장되는 요소 데이터 형식입니다.

*특징이*\
두 요소 값을 정렬 키로 비교 하 여 상대 순서를 확인할 수 있는 이진 조건자 인 클래스 비교 중 하 나와 요소의 키 값을 형식의 부호 없는 정수에 매핑하는 단항 조건자 인 해시 함수의 두 함수 개체를 포함 하는 형식입니다 `size_t` . 이 인수는 선택 사항이며 기본값은 `hash_compare<Key, less<Key> >`입니다.

*할당자*\
hash_set의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<Key>`입니다.

## <a name="remarks"></a>설명

Hash_set은 다음과 같습니다.

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다. 또한 해당 요소 값은 키 값과 구별되므로 간단한 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 요소가 요소의 키 값에 적용된 해시 함수 값을 기반으로 하여 버킷으로 그룹화되기 때문에 해시됩니다.

- 각각의 요소가 반드시 고유한 키를 가지고 있어야 한다는 점에서 고유성을 갖고 있습니다. 또한 hash_set은 간단한 연관 컨테이너이므로 해당 요소도 고유합니다.

- 제공 하는 기능이 제네릭이 고 요소 또는 키로 포함 된 데이터의 특정 형식과 독립적 이기 때문에 클래스 템플릿입니다. 요소에 사용될 데이터 형식과 키는 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

해시는 정렬보다 훨씬 효율적입니다. 성공적인 해시는 정렬 방식에 대한 컨테이너의 요소 수 로그에 비례하는 시간과 비교할 때 삽입, 삭제, 찾기를 일정한 평균 시간 이내에 수행합니다. set 요소의 값은 직접 변경할 수 없습니다. 대신, 이전 값을 삭제하고 새 값의 요소를 삽입해야 합니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 해시된 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 명시적으로 이러한 작업을 지원하는 멤버 함수는 잘 설계된 해시 함수와 함께 사용할 경우 효율적이며, 컨테이너의 요소 수에 종속되지 않는 일정한 평균 시간으로 작업을 수행합니다. 잘 설계된 해시 함수는 해시된 값의 균일한 분포를 생성하고 충돌 수를 최소화합니다. 여기서 충돌은 특정 키 값이 동일한 해시된 값에 매핑될 때 발생합니다. 가능한 최악의 해시 함수가 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간).

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 hash_set입니다. hash_set의 요소는 고유하며 자체 정렬 키로 사용됩니다. 이 형식의 구조에 대한 모델은 정렬된 목록입니다. 예를 들어, 단어 내의 단어는 한 번만 나타날 수 있습니다. 단어를 여러 번 중복할 수 있는 경우 hash_multiset이 적절한 컨테이너 구조입니다. 고유 키 단어 목록에 값이 연결된 경우 이 데이터를 포함하기 위한 적절한 구조는 hash_map입니다. 대신 Key가 고유하지 않은 경우 hash_multimap이 적절한 컨테이너입니다.

Hash_set value_compare 형식의 저장 된 해시 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다 `Traits` . [](#value_compare) 이 저장된 개체는 [key_comp](#key_comp) 멤버 함수를 호출하여 액세스할 수 있습니다. 이러한 함수 개체는<키 hash_compare 클래스의 개체와 동일 하 게 동작 해야 합니다 *\<Key> >.* 특히, Key 형식의 모든 값에 대해 `key` 호출 특성 ()은 `key` size_t 형식의 값 분포를 생성 합니다.

일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 *f*(*x*, *y*)는 두 인수 개체 x, y 및 반환 값 true 또는 false가 있는 함수 개체입니다. 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적인 경우 hash_set에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서, *f*(*x*, *y*) 및 *f*(*y*, *x*)가 모두 false인 경우 *x* 및 *y* 두 개체는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 순서 지정 함수 및 컨테이너 개체에 저장된 해시 테이블의 현재 크기에 따라 달라집니다. 해시 테이블의 현재 크기를 확인할 수 없으므로 제어된 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

hash_set 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [hash_set](#hash_set) 클래스 멤버 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 모음이지만, 클래스 멤버 함수의 맥락에서 반복기 범위[`first`, `last`)에 대해 설명하는 데에는 충분합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[hash_set](#hash_set)|비어 있거나 다른 `hash_set`의 전체 또는 일부의 복사본인 `hash_set`을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `hash_set` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_set` .|
|[const_pointer](#const_pointer)|의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `hash_set` .|
|[const_reference](#const_reference)|**`const`** `hash_set` 작업을 읽고 수행 하기 위해에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_set` .|
|[difference_type](#difference_type)|부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 `hash_set`의 요소의 개수를 표현하는 데 사용할 수 있습니다.|
|[iterator](#iterator)|`hash_set`에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[key_compare](#key_compare)|`hash_set`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|해당 용량 내 `hash_set` 요소로 저장된 개체를 정렬 키로 설명하는 형식입니다.|
|[놓고](#pointer)|`hash_set`의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`hash_set` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 `hash_set`의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|`hash_set`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_compare](#value_compare)|`hash_set`의 두 요소 값을 비교하여 상대 순서를 확인할 수 있는 클래스 비교의 이진 조건자와 요소를 해시하는 단항 조건자인 두 함수 개체를 제공하는 형식입니다.|
|[value_type](#value_type)|해당 용량 내 `hash_set` 요소로 저장된 개체를 값으로 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[시작](#begin)|`hash_set`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`hash_set`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`hash_set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`hash_set`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `hash_set`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 `hash_set`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 `hash_set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `hash_set`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `hash_set`에 삽입합니다.|
|[empty](#empty)|`hash_set`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`hash_set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|지정된 키보다 더 큰 키를 가진 `hash_set`의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 `hash_set`의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.|
|[erase](#erase)|지정된 위치에서 `hash_set`의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `hash_set` 내 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `hash_set` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`hash_set`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_comp)|`hash_set`에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.|
|[lower_bound](#lower_bound)|`hash_set`에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`hash_set`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `hash_set`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `hash_set`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`hash_set`에 있는 요소 수를 반환합니다.|
|[스왑을](#swap)|두 `hash_set`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`hash_set`에서 지정된 키보다 같거나 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`hash_set`의 요소 키 값을 해시하고 정렬하는 데 사용되는 해시 특성 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[hash_set:: operator =](#op_eq)|`hash_set`의 요소를 다른 `hash_set`의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<hash_set>

**네임스페이스:** stdext

## <a name="hash_setallocator_type"></a><a name="allocator_type"></a> hash_set:: allocator_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type` 는 템플릿 매개 변수 *할당자* 의 동의어입니다.

*할당자* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목의 설명 섹션을 참조 하세요.

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="hash_setbegin"></a><a name="begin"></a> hash_set:: begin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

hash_set의 첫 번째 요소 또는 빈 hash_set 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 `begin` 할당 되는 경우 `const_iterator` hash_set 개체의 요소는 수정할 수 없습니다. 의 반환 값 `begin` 이에 할당 되는 경우 `iterator` hash_set 개체의 요소를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="hash_setcbegin"></a><a name="cbegin"></a> hash_set:: cbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

[hash_set](../standard-library/hash-set-class.md)의 첫 번째 요소 또는 빈 `hash_set` 다음의 위치 주소를 지정하는 상수 양방향 반복기입니다.

### <a name="remarks"></a>설명

`cbegin`의 반환 값을 사용하여 `hash_set` 개체의 요소를 수정할 수 없습니다.

### <a name="example"></a>예제

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="hash_setcend"></a><a name="cend"></a> hash_set:: cend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

[hash_set](../standard-library/hash-set-class.md)에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 양방향 반복기입니다. `hash_set`이 비어 있으면 `hash_set::cend == hash_set::begin`입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 `hash_set`의 끝에 도달했는지 여부를 테스트하는 데 사용됩니다. `cend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="hash_setclear"></a><a name="clear"></a> hash_set:: clear

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="hash_setconst_iterator"></a><a name="const_iterator"></a> hash_set:: const_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

Hash_set의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)에 대한 예제를 참조하세요.

## <a name="hash_setconst_pointer"></a><a name="const_pointer"></a> hash_set:: const_pointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

Hash_set의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [const_iterator](#const_iterator) 를 사용 하 여 hash_set 개체의 요소에 액세스 해야 합니다 **`const`** .

## <a name="hash_setconst_reference"></a><a name="const_reference"></a> hash_set:: const_reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

**`const`** 작업을 읽고 수행 하기 위해 hash_set에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="hash_setconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_set:: const_reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

Hash_set의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 hash_set을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="hash_setcount"></a><a name="count"></a> hash_set:: count

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

키가 매개 변수로 지정된 키와 일치하는 hash_set의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_set에서 일치하는지 확인할 요소의 키입니다.

### <a name="return-value"></a>반환 값

hash_set에 정렬 키가 매개 변수 키와 일치하는 요소가 포함되어 있는 경우 1입니다.

hash_set에 일치하는 키가 있는 요소가 포함되지 않은 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수가 다음 범위에 있는 요소의 수를 반환합니다.

\[ lower_bound(*key*), upper_bound(*key*) ).

### <a name="example"></a>예제

다음 예제에서는 hash_set::count 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="hash_setcrbegin"></a><a name="crbegin"></a> hash_set:: crbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_set에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_set](../standard-library/hash-set-class.md)에서 첫 번째 요소 또는 정방향 `hash_set`에서 마지막 요소의 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 [hash_set::begin](#begin)이 hash_set에서 사용되는 것처럼 역방향 hash_set에서 사용됩니다.

반환 값이 `crbegin`이면 `hash_set` 개체를 수정할 수 없습니다.

`crbegin`은 `hash_set`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="hash_setcrend"></a><a name="crend"></a> hash_set:: crend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_set](../standard-library/hash-set-class.md)에서 마지막 요소 다음의 위치(정방향 `hash_set`의 첫 번째 요소 앞의 위치) 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 [hash_set::end](#end)가 `hash_set`에서 사용되는 것처럼 역방향 `hash_set`에서 사용됩니다.

반환 값이 `crend`이면 `hash_set` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `hash_set` 끝에 도달했는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="hash_setdifference_type"></a><a name="difference_type"></a> hash_set::d ifference_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 hash_set의 요소 개수를 표현하는 데 사용할 수 있습니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 [ `first`, `last`) 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소와 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector 또는 deque와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="hash_setemplace"></a><a name="emplace"></a> hash_set:: emplace

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

생성된 요소를 hash_set에 삽입합니다.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_set`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_set](../standard-library/hash-set-class.md)에 삽입될 요소의 값입니다.

### <a name="return-value"></a>반환 값

`emplace`멤버 함수는 **`bool`** 삽입이 수행 된 경우 구성 요소에서를 반환 하 **`true`** 고, **`false`** 해당 `hash_set` 키가 순서 지정 시 동일한 값을가지고 해당 반복기 구성 요소에서 새 요소가 삽입 되었거나 요소가 이미 있었던 주소를 반환 하는 요소를 이미 포함 하는 경우를 반환 합니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="hash_setemplace_hint"></a><a name="emplace_hint"></a> hash_set:: emplace_hint

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

생성된 요소를 hash_set에 삽입합니다.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_set`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_set](../standard-library/hash-set-class.md)에 삽입될 요소의 값입니다.

*_Where*\
올바른 삽입 지점 검색을 시작할 위치입니다. 삽입 지점이 *_Where* 바로 뒤에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 있습니다.

### <a name="return-value"></a>반환 값

[hash_set::emplace](#emplace) 멤버 함수는 새 요소가 `hash_set`에 삽입되거나 동일한 순서를 가진 기존 요소가 있는 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

삽입 지점이 *_Where* 바로 다음에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="hash_setempty"></a><a name="empty"></a> hash_set:: empty

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** hash_set 비어 있으면이 고, 그렇지 않으면입니다. **`false`** hash_set 비어 있지 않으면입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="hash_setend"></a><a name="end"></a> hash_set:: end

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

hash_set에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 양방향 반복기입니다. hash_set이 비어 있으면 hash_set::end == hash_set::begin입니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 hash_set의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다. `end`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="hash_setequal_range"></a><a name="equal_range"></a> hash_set:: equal_range

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키와 같은 키를 가진 hash_set의 첫 번째 요소와 지정된 키보다 큰 키를 가진 hash_set의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](../standard-library/set-class.md#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](../standard-library/set-class.md#upper_bound)입니다.

멤버 함수가 반환하는 pr 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **먼저**, 하위 바운드 반복기를 역참조 하려면 \* ( `pr` . **첫 번째**). 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **둘째**, 상한 반복기를 역참조 하려면 ()를 사용 \* `pr` 합니다. **second**).

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="hash_seterase"></a><a name="erase"></a> hash_set:: erase

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

지정된 위치에서 hash_set의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>매개 변수

*_Where*\
hash_set에서 제거할 요소의 위치입니다.

*기본*\
hash_set에서 제거되는 첫 번째 요소의 위치입니다.

*최신*\
hash_set에서 제거되는 마지막 요소 바로 뒤의 위치입니다.

*키인지*\
hash_set에서 제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소를 지정하는 양방향 반복기이거나 이러한 요소가 없을 경우 hash_set의 끝에 대한 포인터입니다. 세 번째 멤버 함수의 경우 hash_set에서 제거된 요소의 수입니다.

### <a name="remarks"></a>설명

멤버 함수는 예외를 throw하지 않습니다.

### <a name="example"></a>예제

다음 예제에서는 hash_set::erase 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="hash_setfind"></a><a name="find"></a> hash_set:: find

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키와 같은 키를 가진 hash_set 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_set에서 요소의 정렬 키와 일치 여부를 확인할 인수 키입니다.

### <a name="return-value"></a>반환 값

`iterator`지정 된 `const_iterator` 키에 해당 하는 요소의 위치 주소를 지정 하거나, 키와 일치 하는 항목이 없는 경우 hash_set에서 마지막 요소 다음 위치의 주소를 지정 하는 또는입니다.

### <a name="remarks"></a>설명

멤버 함수는 hash_set의 요소를 주소 지정 하는 반복기를 반환 합니다 .이 요소는 정렬 키가 `equivalent` 보다 작음 작음 비교 가능 관계를 기준으로 순서를 지정 하는 이진 조건자 아래의 인수 키에 해당 합니다.

의 반환 값이에 할당 된 경우에는 `find` `const_iterator` hash_set 개체를 수정할 수 없습니다. 의 반환 값 `find` 이에 할당 되는 경우 `iterator` hash_set 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="hash_setget_allocator"></a><a name="get_allocator"></a> hash_set:: get_allocator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

Hash_set에서 메모리를 관리 하는 데 사용 하는 할당자 (템플릿 매개 변수 *할당자*)입니다.

*할당자* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목의 설명 섹션을 참조 하세요.

### <a name="remarks"></a>설명

hash_set 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_sethash_set"></a><a name="hash_set"></a> hash_set:: hash_set

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

비어 있거나 다른 `hash_set`의 전체 또는 일부의 복사본인 `hash_set`을 생성합니다.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 `hash_set` 개체에 사용할 스토리지 할당자 클래스로, 기본값은 `Allocator`입니다.

*생략*\
`hash_set`의 요소 순서를 지정하는 데 사용되는 `const Traits` 형식의 비교 함수로, 기본값은 `hash_compare`입니다.

*오른쪽*\
생성된 `hash_set`이 복사본으로 지정될 `hash_set`입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

### <a name="remarks"></a>설명

모든 생성자는 `hash_set`의 메모리 스토리지를 관리하며 나중에 [hash_set::get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 hash_set을 초기화합니다.

모든 생성자는 `hash_set`의 키 간 순서를 설정하는 데 사용되며 나중에 [hash_set::key_comp](#key_comp)를 호출하여 반환할 수 있는 `Traits` 형식의 함수 개체를 저장합니다. `Traits`에 대한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목을 참조하세요.

첫 번째 생성자는 빈 초기 `hash_set`을 정의하고, 두 번째 생성자는 요소의 순서를 설정하는 데 사용할 비교 함수(`Comp`)의 형식을 지정하며, 세 번째 생성자는 사용할 할당자 형식(`Al`)을 명시적으로 지정합니다. 키 단어는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 및 다섯 번째 생성자는 `hash_set` `Right`의 복사본을 지정합니다.

마지막 여섯 번째, 일곱 번째 및 여덟 번째 생성자는 요소에 initializer_list를 사용합니다.

마지막 3개 생성자는 `hash_set`의 범위 [ `First`, `Last`)를 복사하며, 범위 내에서 클래스 Traits 및 allocator의 비교 함수 형식을 지정하는 명시도는 계속 높아집니다.

여덟 번째 생성자는 `hash_set` `Right`를 이동합니다.

`hash_set` 컨테이너에 있는 요소의 실제 순서는 해시 함수, 순서 지정 함수 및 해시 테이블의 현재 크기에 따라 달라지고, 일반적으로 순서 지정 함수에 의해서만 결정된 경우 set 컨테이너에서 예상 가능하던 것처럼 실제 순서를 예상할 수는 없습니다.

## <a name="hash_setinsert"></a><a name="insert"></a> hash_set:: insert

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

`hash_set`에 요소 또는 요소의 범위를 삽입합니다.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_set`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 `hash_set`에 삽입될 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다. 삽입 지점이 `_Where` 바로 뒤에 오면 로그 시간 대신 분할 상수 시간에 삽입이 발생할 수 있습니다.

*기본*\
`hash_set`에서 복사할 첫 번째 요소의 위치입니다.

*최신*\
`hash_set`에서 복사할 마지막 요소 바로 다음 위치입니다.

*IList*\
요소를 복사해올 initializer_list입니다.

### <a name="return-value"></a>반환 값

첫 번째 `insert` 멤버 함수는 **`bool`** 삽입이 수행 된 경우 구성 요소에서를 반환 하 **`true`** 고, **`false`** 해당 키가 순서 지정 `hash_set` 시 동일한 값을가지고 해당 반복기 구성 요소에서 새 요소가 삽입 되었거나 요소가 이미 있었던 주소를 반환 하는 요소가에 이미 포함 된 경우를 반환 합니다.

이 멤버 함수가 반환하는 `pr` 쌍의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 해당 구성 요소를 역참조하려면 `*(pr.first)`를 사용합니다. **`bool`** 이 멤버 함수가 반환 하는 쌍의 구성 요소에 액세스 하려면 `pr` 를 사용 하 고 해당 구성 요소를 `pr.second` 역참조 하려면를 사용 `*(pr.second)` 합니다.

두 번째 `insert` 멤버 함수는 새 요소를 `hash_set`에 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

세 번째 멤버 함수는 initializer_list에 요소를 삽입합니다.

세 번째 멤버 함수는 지정된 `hash_set`의 [`First`, `Last`) 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 `hash_set`에 요소 값의 시퀀스를 삽입합니다.

## <a name="hash_setiterator"></a><a name="iterator"></a> hash_set:: iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>설명

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

`iterator`를 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_setkey_comp"></a><a name="key_comp"></a> hash_set:: key_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 요소 키 값을 해시하고 정렬하는 데 사용되는 해시 특성 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

Hash_set에서 요소를 정렬 하는 데 사용 하는 함수 개체를 반환 합니다 .이 개체는 템플릿 매개 변수 *특성* 입니다.

*특성* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 구성원 함수

`bool operator( const Key& _xVal, const Key& _yVal );`

**`true`** `_xVal` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[key_compare](#key_compare)와 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 *Traits* 와 동일한 의미입니다. 두 형식 모두 hash_set 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="hash_setkey_compare"></a><a name="key_compare"></a> hash_set:: key_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare` 는 템플릿 매개 변수 *특성* 의 동의어입니다.

*특성* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목을 참조 하세요.

`key_compare` 및 [value_compare](#value_compare)는 둘 다 템플릿 매개 변수 *Traits* 와 동일한 의미입니다. 두 형식 모두 set 및 multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, map 및 multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="hash_setkey_type"></a><a name="key_type"></a> hash_set:: key_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

해당 용량 내에서 hash_set의 요소로 저장된 개체를 정렬 키로 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type` 는 템플릿 매개 변수 *키* 의 동의어입니다.

*키* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목의 설명 섹션을 참조 하세요.

`key_type` 및 [value_type](#value_type)은 둘 다 템플릿 매개 변수 *Key* 의 동의어입니다. 두 형식 모두 hash_set 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_setlower_bound"></a><a name="lower_bound"></a> hash_set:: lower_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 인수 키 보다 크거나 같은 키를 가진 hash_set의 요소 위치 주소를 가져오거나, 키와 일치 하는 항목이 없는 경우 hash_set에서 마지막 요소 다음 위치의 주소를 나타내는 또는입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="hash_setmax_size"></a><a name="max_size"></a> hash_set:: max_size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

hash_set의 최대 허용 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="hash_setoperator"></a><a name="op_eq"></a> hash_set:: operator =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 요소를 다른 hash_set의 복사본으로 바꿉니다.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`hash_set`에 복사되는 [hash_set](../standard-library/hash-set-class.md)입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `hash_set` 는 `operator=` 의 내용을로 복사 하거나 이동  `hash_set` 합니다.

### <a name="example"></a>예제

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="hash_setpointer"></a><a name="pointer"></a> hash_set::p ointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 hash_set 개체의 요소에 액세스해야 합니다.

## <a name="hash_setrbegin"></a><a name="rbegin"></a> hash_set:: rbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_set에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 hash_set에서 첫 번째 요소 또는 정방향 hash_set에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 [begin](#begin)이 hash_set에서 사용되는 것처럼 역방향 hash_set에서 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 hash_set 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우 hash_set 개체를 수정할 수 있습니다.

`rbegin`은 hash_set을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="hash_setreference"></a><a name="reference"></a> hash_set:: reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="hash_setrend"></a><a name="rend"></a> hash_set:: rend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_set에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 hash_set에서 마지막 요소 다음의 위치(정방향 hash_set의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`은 [end](#end)가 hash_set에서 사용되는 것처럼 역방향 hash_set에서 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당되는 경우 hash_set 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우 hash_set 개체를 수정할 수 있습니다. `rend`에서 반환한 값은 역참조되지 않아야 합니다.

`rend`를 사용하여 역방향 반복기가 hash_set 끝에 도달했는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="hash_setreverse_iterator"></a><a name="reverse_iterator"></a> hash_set:: reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_set의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 hash_set을 역방향으로 반복하는 데 사용됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="hash_setsize"></a><a name="size"></a> hash_set:: size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

hash_set의 현재 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="hash_setsize_type"></a><a name="size_type"></a> hash_set:: size_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="hash_setswap"></a><a name="swap"></a> hash_set:: swap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_set의 요소를 교환합니다.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 hash_set과 교환할 요소를 제공하는 인수 hash_set입니다.

### <a name="remarks"></a>설명

멤버 함수는 해당 요소를 교환할 두 hash_set의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="hash_setupper_bound"></a><a name="upper_bound"></a> hash_set:: upper_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_set에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 인수 키 보다 크거나 같은 키를 가진 hash_set의 요소 위치 주소를 가져오거나, 키와 일치 하는 항목이 없는 경우 hash_set에서 마지막 요소 다음 위치의 주소를 나타내는 또는입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="hash_setvalue_comp"></a><a name="value_comp"></a> hash_set:: value_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

Hash_set에서 요소를 정렬 하는 데 사용 하는 함수 개체를 반환 합니다 .이 개체는 템플릿 매개 변수 *비교* 입니다.

*비교* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목의 설명 섹션을 참조 하세요.

### <a name="remarks"></a>설명

저장된 개체는 구성원 함수

`bool operator( const Key& _xVal, const Key& _yVal );`

**`true`** `_xVal` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `_yVal` .

[Value_compare](../standard-library/set-class.md#value_compare) 와 [key_compare](../standard-library/set-class.md#key_compare) 는 모두 템플릿 매개 변수 *비교* 의 동의어입니다. 두 형식 모두 hash_set 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="hash_setvalue_compare"></a><a name="value_compare"></a> hash_set:: value_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

hash_set의 두 요소 값을 비교하여 상대 순서를 확인할 수 있는 클래스 비교의 이진 조건자와 요소를 해시하는 단항 조건자인 두 함수 개체를 제공하는 형식입니다.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>설명

`value_compare` 는 템플릿 매개 변수 *특성* 의 동의어입니다.

*특성* 에 대 한 자세한 내용은 [hash_set 클래스](../standard-library/hash-set-class.md) 항목을 참조 하세요.

[Key_compare](#key_compare) 와는 모두 `value_compare` 템플릿 매개 변수 *특성* 의 동의어입니다. 두 형식 모두 hash_set 및 hash_multiset 클래스용으로 제공되며 이러한 클래스에 사용되는 경우에는 동일하지만, hash_map 및 hash_multimap 클래스와의 호환성을 위해 제공되는 경우에는 서로 다릅니다.

### <a name="example"></a>예제

`value_compare`를 선언하고 사용하는 방법의 예제는 [value_comp](#value_comp)의 예제를 참조하세요.

## <a name="hash_setvalue_type"></a><a name="value_type"></a> hash_set:: value_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

해당 용량 내에서 hash_set의 요소로 저장된 개체를 값으로 설명하는 형식입니다.

```cpp
typedef Key value_type;
```

### <a name="example"></a>예제

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
