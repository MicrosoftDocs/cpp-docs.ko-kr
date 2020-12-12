---
description: Hash_multimap 클래스에 대해 자세히 알아보세요.
title: hash_multimap 클래스
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: b8cbf11bf633940140fb9a90b58ee1128b9efca6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324111"
---
# <a name="hash_multimap-class"></a>hash_multimap 클래스

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

컨테이너 클래스 hash_multimap은 C++ 표준 라이브러리의 확장이며, 각 요소가 값이 고유할 필요가 없는 정렬 키와 관련 데이터 값으로 구성된 쌍인 컬렉션에서 데이터를 스토리지하고 빠르게 검색하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_multimap에 저장되는 키 데이터 형식입니다.

*입력할*\
hash_multimap에 저장되는 요소 데이터 형식입니다.

*특징이*\
두 요소 값을 정렬 키로 비교 하 여 상대 순서를 확인할 수 있는 클래스 *특성* 중 하 나와 요소의 키 값을 형식의 부호 없는 정수에 매핑하는 단항 조건자 인 해시 함수의 두 함수 개체를 포함 하는 형식입니다 `size_t` . 이 인수는 선택 사항이며 기본값은 `hash_compare<Key, less<Key>>`입니다.

*할당자*\
hash_multimap의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<pair <const Key, Type>>`입니다.

## <a name="remarks"></a>설명

hash_multimap은 다음과 같습니다.

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 요소가 요소의 키 값에 적용된 해시 함수 값을 기반으로 하여 버킷으로 그룹화되기 때문에 해시됩니다.

- 해당 요소는 고유 키를 가질 필요가 없기 때문에 복수이며, 하나의 키 값은 이와 연관된 많은 요소 데이터 값을 가질 수 있습니다.

- 요소 값은 키 값과 구별되기 때문에 쌍 연관 컨테이너입니다.

- 클래스 템플릿은 제공 된 기능이 일반적 이므로 요소 또는 키로 포함 된 데이터의 특정 형식과 독립적 이기 때문입니다. 요소에 사용될 데이터 형식과 키는 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

해시는 정렬보다 훨씬 효율적입니다. 성공적인 해시는 정렬 방식에 대한 컨테이너의 요소 수 로그에 비례하는 시간과 비교할 때 삽입, 삭제, 찾기를 일정한 평균 시간 이내에 수행합니다. hash_multimap 요소의 값은 연관된 키 값을 제외하고 직접적으로 변경할 수 있습니다. 대신, 이전 요소와 관련된 키 값을 삭제하고 새 요소와 연결된 새 키 값을 삽입해야 합니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 해시된 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 명시적으로 이러한 작업을 지원하는 멤버 함수는 잘 설계된 해시 함수와 함께 사용할 경우 효율적이며, 컨테이너의 요소 수에 종속되지 않는 일정한 평균 시간으로 작업을 수행합니다. 잘 설계된 해시 함수는 해시된 값의 균일한 분포를 생성하고 충돌 수를 최소화합니다. 여기서 충돌은 특정 키 값이 동일한 해시된 값에 매핑될 때 발생합니다. 가능한 최악의 해시 함수가 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간).

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 hash_multimap입니다. 이 구조 형식의 모델은 단어들이 항상 유일하게 정의되지 않는 "정의" 같이 문자열 값과 연결된 키 단어들의 정렬된 목록입니다. 대신 키워드가 고유하게 정의되어 키가 고유한 경우 hash_map이 적절한 컨테이너가 됩니다. 반면에 단어 목록만 저장하는 경우에는 hash_set이 올바른 컨테이너가 됩니다. 단어를 여러 번 중복할 수 있는 경우 hash_multiset이 적절한 컨테이너 구조입니다.

hash_multimap은 [value_compare](../standard-library/value-compare-class.md) 형식의 저장된 해시 `Traits` 개체를 호출하여 제어하는 시퀀스를 정렬합니다. 이 저장된 개체는 [key_comp](../standard-library/hash-map-class.md#key_comp) 멤버 함수를 호출하여 액세스할 수 있습니다. 이러한 함수 개체는 [hash_compare](../standard-library/hash-compare-class.md)클래스의 개체와 동일 하 게 동작 해야 합니다 `<Key, less<Key>>` . 특히, `Key` 형식의 모든 값 `Key`에 대해 `Traits (Key)` 호출은 `size_t` 형식의 값 분포를 생성합니다.

일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 f (x, y)는 두 인수 개체 `x` 및 `y` 및 반환 값이 또는 인 함수 개체입니다 **`true`** **`false`** . 이진 조건자가 비재귀적, 비대칭 및 전이적이 고 동등성이 전이적 인 경우에는 hash_multimap에 적용 되는 순서가 엄격 `x` `y` 하지 않습니다. f (x, y) 및 f (y, x)가 모두 인 경우 두 개체 및는 동등한 것으로 정의 됩니다 **`false`** . 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 순서 지정 함수 및 컨테이너 개체에 저장된 해시 테이블의 현재 크기에 따라 달라집니다. 해시 테이블의 현재 크기를 확인할 수 없으므로 제어된 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

hash_multimap 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [hash_multimap](#hash_multimap) 클래스 멤버 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념에는 요구 사항의 고유한 hash_multimap이 있으며, 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 기능의 최소 hash_multimap이지만, 멤버 함수의 컨텍스트에서 반복기 범위 `[First, Last)`에 대해 설명하는 데에는 충분합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[hash_multimap](#hash_multimap)|특정 크기의 목록 또는 특정 값의 요소 또는 특정 `allocator`가 포함된 목록 또는 다른 `hash_multimap`의 복사본으로 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `hash_multimap` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_multimap` .|
|[const_pointer](#const_pointer)|의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `hash_multimap` .|
|[const_reference](#const_reference)|**`const`** `hash_multimap` 작업을 읽고 수행 하기 위해에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_multimap` .|
|[difference_type](#difference_type)|부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 `hash_multimap`의 요소의 개수를 표현하는 데 사용할 수 있습니다.|
|[iterator](#iterator)|`hash_multimap`에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[key_compare](#key_compare)|`hash_multimap`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|`hash_multimap`의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.|
|[mapped_type](#mapped_type)|`hash_multimap` 내에 저장된 데이터 형식을 나타내는 형식입니다.|
|[놓고](#pointer)|`hash_multimap`의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`hash_multimap` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 `hash_multimap`의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|`hash_multimap`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|두 요소를 정렬 키로 비교하여 `hash_multimap`에서 상대적 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[시작](#begin)|`hash_multimap`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`hash_multimap`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`hash_multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`hash_multimap`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `hash_multimap`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 `hash_multimap`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 `hash_multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `hash_multimap`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `hash_multimap`에 삽입합니다.|
|[empty](#empty)|`hash_multimap`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`hash_multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|`hash_multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[erase](#erase)|`hash_multimap`의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `hash_multimap` 내 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `hash_multimap` 개체의 복사본을 반환합니다.|
|[insert](#insert)|요소 또는 요소의 범위를 `hash_multimap`의 지정된 위치에 삽입합니다.|
|[key_comp](#key_comp)|`hash_multimap`에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.|
|[lower_bound](#lower_bound)|`hash_multimap`에서 지정된 키보다 같거나 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`hash_multimap`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `hash_multimap`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `hash_multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`hash_multimap`의 새 크기를 지정합니다.|
|[스왑을](#swap)|두 `hash_multimap`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`hash_multimap`에서 지정된 키보다 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`hash_multimap`에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[hash_multimap::operator=](#op_eq)|`hash_multimap`의 요소를 다른 `hash_multimap`의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<hash_map>

**네임스페이스:** stdext

## <a name="hash_multimapallocator_type"></a><a name="allocator_type"></a> hash_multimap:: allocator_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type`는 템플릿 매개 변수 `Allocator`의 동의어입니다.

`Allocator`에 대한 자세한 내용은 [hash_multimap 클래스](../standard-library/hash-multimap-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="hash_multimapbegin"></a><a name="begin"></a> hash_multimap:: begin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

hash_multimap의 첫 번째 요소 또는 빈 hash_multimap 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

의 반환 값이에 `begin` 할당 되는 경우 `const_iterator` hash_multimap 개체의 요소는 수정할 수 없습니다. 의 반환 값 `begin` 이에 할당 되는 경우 `iterator` hash_multimap 개체의 요소를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_multimapcbegin"></a><a name="cbegin"></a> hash_multimap:: cbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 첫 번째 요소 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

[hash_multimap](../standard-library/hash-multimap-class.md)의 첫 번째 요소 또는 빈 `hash_multimap` 다음의 위치 주소를 지정하는 상수 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="hash_multimapcend"></a><a name="cend"></a> hash_multimap:: cend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

[hash_multimap](../standard-library/hash-multimap-class.md)에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 양방향 반복기입니다. `hash_multimap`이 비어 있으면 `hash_multimap::cend == hash_multimap::begin`입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 hash_multimap의 끝에 도달했는지 여부를 테스트하는 데 사용됩니다.

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="hash_multimapclear"></a><a name="clear"></a> hash_multimap:: clear

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 hash_multimap::clear 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="hash_multimapconst_iterator"></a><a name="const_iterator"></a> hash_multimap:: const_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

Hash_multimap의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

`const_iterator`Hash_multimap 정의 된는 형식이 인 [value_type](#value_type)의 개체를 가리킵니다 `pair<const Key, Type>` . 키의 값은 첫 번째 멤버 쌍을 통해 제공되며 매핑된 요소의 값은 쌍의 두 번째 멤버를 통해 제공됩니다.

`const_iterator` `cIter` Hash_multimap의 요소를 가리키는를 역참조 하려면 연산자를 사용 `->` 합니다.

요소에 대 한 키의 값에 액세스 하려면 `cIter->first` 에 해당 하는를 사용 `(*cIter).first` 합니다. 요소에 대 한 매핑된 데이텀의 값에 액세스 하려면 `cIter->second` 에 해당 하는를 사용 `(*cIter).second` 합니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_multimapconst_pointer"></a><a name="const_pointer"></a> hash_multimap:: const_pointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

Hash_multimap의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 hash_multimap 개체의 요소에 액세스해야 합니다.

## <a name="hash_multimapconst_reference"></a><a name="const_reference"></a> hash_multimap:: const_reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

**`const`** 작업을 읽고 수행 하기 위해 hash_multimap에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="hash_multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_multimap:: const_reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

Hash_multimap의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 hash_multimap을 역방향으로 반복하는 데 사용됩니다.

`const_reverse_iterator`Hash_multimap에서 정의 된는 형식이 인 [value_type](#value_type)의 개체를 가리킵니다 .이 개체의 `pair<const Key, Type>` 첫 번째 멤버는 요소에 대 한 키이 고 두 번째 멤버는 요소가 보유 하 고 있는 매핑된 데이텀이 됩니다.

`const_reverse_iterator` `crIter` Hash_multimap의 요소를 가리키는를 역참조 하려면 연산자를 사용 `->` 합니다.

요소에 대 한 키의 값에 액세스 하려면 `crIter->first` 에 해당 하는를 사용 `(*crIter).first` 합니다. 요소에 대 한 매핑된 데이텀의 값에 액세스 하려면 `crIter->second` 에 해당 하는를 사용 `(*crIter).second` 합니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="hash_multimapcount"></a><a name="count"></a> hash_multimap:: count

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

키가 매개 변수로 지정된 키와 일치하는 hash_multimap의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_multimap에서 일치하는지 확인할 요소의 키입니다.

### <a name="return-value"></a>반환 값

hash_multimap에 정렬 키가 매개 변수 키와 일치하는 요소가 있는 경우 1이고, hash_multimap에 일치하는 키가 포함된 요소가 없는 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 범위에 있는 요소 중에서

**[lower_bound (** `key` **), upper_bound (** `key` **) )**

키 값 *키* 가 있는입니다.

### <a name="example"></a>예제

다음 예제에서는 hash_multimap::count 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_multimapcrbegin"></a><a name="crbegin"></a> hash_multimap:: crbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

역방향 hash_multimap에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_multimap](../standard-library/hash-multimap-class.md)에서 첫 번째 요소 또는 정방향 `hash_multimap`에서 마지막 요소의 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 [hash_multimap::begin](#begin)이 `hash_multimap`에서 사용되는 것처럼 역방향 hash_multimap에서 사용됩니다.

반환 값이 `crbegin`이면 `hash_multimap` 개체를 수정할 수 없습니다.

`crbegin`은 `hash_multimap`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapcrend"></a><a name="crend"></a> hash_multimap:: crend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

역방향 hash_multimap에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_multimap](../standard-library/hash-multimap-class.md)에서 마지막 요소 다음의 위치(정방향 `hash_multimap`의 첫 번째 요소 앞의 위치) 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 [hash_multimap::end](#end)가 hash_multimap에서 사용되는 것처럼 역방향 hash_multimap에서 사용됩니다.

반환 값이 `crend`이면 `hash_multimap` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 hash_multimap 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapdifference_type"></a><a name="difference_type"></a> hash_multimap::d ifference_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

반복기가 가리키는 요소 사이의 범위에 있는 hash_multimap의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 *[ first,  last)* 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소에서 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="hash_multimapemplace"></a><a name="emplace"></a> hash_multimap:: emplace

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

생성된 요소를 hash_multimap에 삽입합니다.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
[hash_multimap](../standard-library/hash-multimap-class.md)에 삽입할 요소를 이동 생성하는 데 사용되는 값입니다.

### <a name="return-value"></a>반환 값

`emplace` 멤버 함수는 새 요소가 삽입된 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

요소의 [hash_multimap::value_type](#value_type)은 쌍으로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapemplace_hint"></a><a name="emplace_hint"></a> hash_multimap:: emplace_hint

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

배치 힌트를 사용하여 hash_multimap에 생성된 요소를 삽입합니다.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_multimap`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_multimap](../standard-library/hash-multimap-class.md)에 삽입되는 요소를 이동 생성하는 데 사용되는 값입니다.

*_Where*\
올바른 삽입 지점 검색을 시작할 위치와 관련된 힌트입니다.

### <a name="return-value"></a>반환 값

[hash_multimap::emplace](#emplace) 멤버 함수는 새 요소를 `hash_multimap`에 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

요소의 [hash_multimap::value_type](#value_type)은 쌍으로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

삽입 지점이 *_Where* 바로 다음에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapempty"></a><a name="empty"></a> hash_multimap:: empty

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** hash_multimap 비어 있으면이 고, 그렇지 않으면입니다. **`false`** hash_multimap 비어 있지 않으면입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="hash_multimapend"></a><a name="end"></a> hash_multimap:: end

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

hash_multimap에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 양방향 반복기입니다. hash_multimap이 비어 있으면 hash_multimap::end == hash_multimap::begin입니다.

### <a name="remarks"></a>설명

`end`는 반복기가 hash_multimap의 끝에 도달했는지 여부를 테스트하는 데 사용됩니다.

`end`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="hash_multimapequal_range"></a><a name="equal_range"></a> hash_multimap:: equal_range

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

지정된 키보다 더 큰 키를 가진 hash_multimap의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 hash_multimap의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

멤버 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **첫째** , 하 한 반복기를 역참조 하려면 \* ()를 사용 `pr` 합니다. **첫 번째**). 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **둘째** , 상한 반복기를 역참조 하려면 (를 사용 \* `pr` 합니다. **second**).

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="hash_multimaperase"></a><a name="erase"></a> hash_multimap:: erase

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

지정된 위치에서 hash_multimap의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>매개 변수

*_Where*\
hash_multimap에서 제거할 요소의 위치입니다.

*기본*\
hash_multimap에서 제거된 첫 번째 요소의 위치입니다.

*최신*\
hash_multimap에서 제거된 마지막 요소 바로 뒤의 위치입니다.

*키인지*\
hash_multimap에서 제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소를 지정하는 양방향 반복기이거나 이러한 요소가 없을 경우 hash_multimap의 끝에 대한 포인터입니다.

세 번째 멤버 함수의 경우 hash_multimap에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>설명

멤버 함수는 예외를 throw하지 않습니다.

### <a name="example"></a>예제

다음 예제에서는 hash_multimap::erase 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="hash_multimapfind"></a><a name="find"></a> hash_multimap:: find

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

지정된 키와 같은 키를 가진 hash_multimap 내 요소의 첫 번째 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multimap에서 요소의 정렬 키와 일치 여부를 확인할 키입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 첫 번째 위치 또는 해당 키와 일치하는 항목이 없는 경우 hash_multimap의 마지막 요소 다음 위치에 대한 주소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 정렬 키가 `equivalent` 작음 비교 가능 보다 작음 관계를 기준으로 순서를 지정 하는 이진 조건자 아래의 인수 키에 해당 하는 hash_multimap의 요소를 주소 지정 하는 반복기를 반환 합니다.

`find`의 반환 값이 `const_iterator`에 할당된 경우 hash_multimap 개체는 수정할 수 없습니다. 의 반환 값 `find` 이에 할당 되는 경우 `iterator` hash_multimap 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapget_allocator"></a><a name="get_allocator"></a> hash_multimap:: get_allocator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

hash_multimap에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

hash_multimap 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_multimaphash_multimap"></a><a name="hash_multimap"></a> hash_multimap:: hash_multimap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

비어 있거나 일부 다른 hash_multimap의 전체 또는 부분에 대한 복사본인 hash_multimap을 생성합니다.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 hash_multimap 개체에 사용할 스토리지 할당자 클래스로, 기본값은 `Allocator`입니다.

*생략*\
map의 요소 순서를 지정하는 데 사용되는 `const Traits` 형식의 비교 함수로, 기본값은 `Traits`입니다.

*오른쪽*\
생성된 set가 복사본으로 지정될 map입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
복사할 원본 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 hash_multimap의 메모리 스토리지를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 hash_multimap을 초기화합니다.

모든 생성자는 hash_multimap의 키 간 순서를 설정하는 데 사용되며 나중에 [key_comp](#key_comp)를 호출하여 반환할 수 있는 `Traits` 형식의 함수 개체를 저장합니다.

처음 세 생성자는 빈 초기 hash_multimap를 지정 합니다. 두 번째는 요소의 순서를 설정 하는 데 사용할 비교 함수 (*Comp*)의 형식을 지정 하 고, 세 번째는 사용할 할당자 형식 ()을 명시적으로 지정 합니다 `_Al` . 키워드는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 생성자는 `Right` hash_multimap의 복사본을 지정합니다.

다음 세 생성자는 map의 범위 `First, Last)`를 복사하여, `Traits` 클래스 및 할당자의 비교 함수 형식을 지정할 때 명시도가 향상됩니다.

여덟 번째 생성자는 hash_multimap `Right`를 이동합니다.

마지막 3개 생성자는 initializer_list를 사용합니다.

## <a name="hash_multimapinsert"></a><a name="insert"></a> hash_multimap:: insert

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 요소 또는 요소의 범위를 삽입합니다.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
해당 요소를 이미 포함하고 있지 않을 경우 또는 보다 일반적으로 키가 동등하게 정렬된 요소를 이미 포함하고 있지 않을 경우 hash_multimap에 삽입되는 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치에 대한 힌트입니다.

*기본*\
맵에서 복사할 첫 번째 요소의 위치입니다.

*최신*\
맵에서 복사할 마지막 요소 바로 다음 위치입니다.

### <a name="return-value"></a>반환 값

처음 두 `insert` 멤버 함수는 새 요소가 삽입된 위치를 가리키는 반복기를 반환합니다.

세 번째 멤버 함수는 삽입할 요소에 initializer_list를 사용합니다.

네 번째 멤버 함수는 지정된 집합의 `[First, Last)` 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 맵에 요소 값의 시퀀스를 삽입합니다.

마지막 두 `insert` 멤버 함수는 삽입된 값을 이동-생성한다는 점을 제외하고 처음 두 함수와 똑같이 동작합니다.

### <a name="remarks"></a>설명

요소의 [value_type](#value_type) 은 쌍으로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

삽입 `insert` 지점이 바로 뒤에 오면 로그 시간 대신의 힌트 버전에 대 한 분할 상환 상수 시간에 삽입이 발생할 수 있습니다 .

## <a name="hash_multimapiterator"></a><a name="iterator"></a> hash_multimap:: iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>설명

`iterator`Hash_multimap에서 정의 된는 형식이 인 [value_type](#value_type)의 개체를 가리킵니다 .이 개체의 `pair` \< **const Key, Type**> 첫 번째 멤버는 요소에 대 한 키이 고 두 번째 멤버는 요소가 보유 하 고 있는 매핑된 데이텀이 됩니다.

`Iter`Hash_multimap의 요소를 가리키는 이라는 반복기를 역참조 하려면 연산자를 사용 `->` 합니다.

요소에 대 한 키의 값에 액세스 하려면 `Iter->first` 에 해당 하는를 사용 `(*Iter).first` 합니다. 요소에 대 한 매핑된 데이텀의 값에 액세스 하려면 `Iter->second` 에 해당 하는를 사용 `(*Iter).first` 합니다.

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

`iterator`를 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_multimapkey_comp"></a><a name="key_comp"></a> hash_multimap:: key_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

hash_multimap이 요소의 순서를 지정하는 데 사용하는 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

저장된 개체는 멤버 함수

`bool operator( const Key& left, const Key& right );`

**`true`** `left` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `right` .

### <a name="example"></a>예제

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="hash_multimapkey_compare"></a><a name="key_compare"></a> hash_multimap:: key_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 두 요소 간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare` 는 템플릿 매개 변수 *특성* 의 동의어입니다.

*특성* 에 대 한 자세한 내용은 [hash_multimap 클래스](../standard-library/hash-multimap-class.md) 항목을 참조 하세요.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="hash_multimapkey_type"></a><a name="key_type"></a> hash_multimap:: key_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type` 는 템플릿 매개 변수 *키* 의 동의어입니다.

*키* 에 대 한 자세한 내용은 [hash_multimap 클래스](../standard-library/hash-multimap-class.md) 항목의 설명 섹션을 참조 하세요.

### <a name="example"></a>예제

`key_compare`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_multimaplower_bound"></a><a name="lower_bound"></a> hash_multimap:: lower_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 hash_multimap 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_multimap에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

`lower_bound`의 반환 값이 `const_iterator`에 할당된 경우 hash_multimap 개체는 수정할 수 없습니다. 의 반환 값 `lower_bound` 이에 할당 되는 경우 `iterator` hash_multimap 개체를 수정할 수 있습니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapmapped_type"></a><a name="mapped_type"></a> hash_multimap:: mapped_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>설명

`mapped_type`은 템플릿 매개 변수 *Type* 의 동의어입니다.

*형식* 에 대 한 자세한 내용은 [hash_multimap 클래스](../standard-library/hash-multimap-class.md) 항목을 참조 하세요.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_multimapmax_size"></a><a name="max_size"></a> hash_multimap:: max_size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

hash_multimap의 최대 허용 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="hash_multimapoperator"></a><a name="op_eq"></a> hash_multimap:: operator =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap의 요소를 다른 hash_multimap의 복사본으로 바꿉니다.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`hash_multimap`에 복사되는 [hash_multimap](../standard-library/hash-multimap-class.md)입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `hash_multimap` 는 `operator=` 의 내용을로 복사 하거나 이동  `hash_multimap` 합니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
}
```

## <a name="hash_multimappointer"></a><a name="pointer"></a> hash_multimap::p ointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 hash_multimap 개체의 요소에 액세스해야 합니다.

## <a name="hash_multimaprbegin"></a><a name="rbegin"></a> hash_multimap:: rbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

역방향 hash_multimap에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 hash_multimap에서 첫 번째 요소 또는 정방향 hash_multimap에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 [begin](#begin)이 hash_multimap에서 사용되는 것처럼 역방향 hash_multimap에서 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당된 경우 hash_multimap 개체는 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당된 경우에는 hash_multimap 개체를 수정할 수 있습니다.

`rbegin`은 hash_multimap을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreference"></a><a name="reference"></a> hash_multimap:: reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="hash_multimaprend"></a><a name="rend"></a> hash_multimap:: rend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

역방향 hash_multimap에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 hash_multimap에서 마지막 요소 다음의 위치(정방향 hash_multimap의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`은 [end](#end)가 hash_multimap에서 사용되는 것처럼 역방향 hash_multimap에서 사용됩니다.

`rend`의 반환 값이 [const_reverse_iterator](#const_reverse_iterator)에 할당되는 경우에는 hash_multimap 개체를 수정할 수 없습니다. `rend`의 반환 값이 [reverse_iterator](#reverse_iterator)에 할당되는 경우에는 hash_multimap 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 hash_multimap 끝에 도달했는지 여부를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreverse_iterator"></a><a name="reverse_iterator"></a> hash_multimap:: reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

역방향 hash_multimap의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 hash_multimap을 역방향으로 반복하는 데 사용됩니다.

`reverse_iterator`Hash_multimap 정의 된는 형식이 인 [value_type](#value_type)의 개체를 가리킵니다 `pair` \< **const Key, Type**> . 키의 값은 첫 번째 멤버 쌍을 통해 제공되며 매핑된 요소의 값은 쌍의 두 번째 멤버를 통해 제공됩니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="hash_multimapsize"></a><a name="size"></a> hash_multimap:: size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

hash_multimap의 현재 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 hash_multimap::size 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="hash_multimapsize_type"></a><a name="size_type"></a> hash_multimap:: size_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 요소 수를 계산하는 부호 없는 정수 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="hash_multimapswap"></a><a name="swap"></a> hash_multimap:: swap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

두 hash_multimap의 요소를 교환합니다.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공하는 hash_multimap 또는 hash_multimap과 요소를 교환할 hash_multimap입니다.

### <a name="remarks"></a>설명

멤버 함수는 해당 요소를 교환할 두 hash_multimap의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="hash_multimapupper_bound"></a><a name="upper_bound"></a> hash_multimap:: upper_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 더 큰 키가 들어 있는 hash_multimap 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_multimap에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

`upper_bound`의 반환 값이 `const_iterator`에 할당된 경우 hash_multimap 개체는 수정할 수 없습니다. 의 반환 값이에 `upper_bound` 할당 되는 경우 `iterator` hash_multimap 개체를 수정할 수 있습니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="hash_multimapvalue_comp"></a><a name="value_comp"></a> hash_multimap:: value_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

멤버 함수는 키 값을 비교하여 hash_multimap의 요소 순서를 결정하는 함수 개체를 반환합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

hash_multimap이 요소의 순서를 지정하는 데 사용하는 비교 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

Hash_multimap *m* 의 경우 두 요소인 *e1* (*k1*, *d1*) 및 *e2*(*k2*, *d2*)는 [value_type](#value_type)형식의 개체이 고, 여기서 *k1* 와 *k2* 는 [key_type](#key_type) 형식의 키이 고 *d1* 및 *d2* 는 [mapped_type](#mapped_type)형식의 데이터입니다. 그런 다음는와 `m.value_comp()(e1, e2)` 동일 `m.key_comp()(k1, k2)` 합니다. 저장된 개체는 멤버 함수

`bool operator( value_type& left, value_type& right);`

**`true`** 의 키 값 `left` 이 보다 앞에 오고가 정렬 순서에서의 키 값과 같지 않은 경우를 반환 합니다 `right` .

### <a name="example"></a>예제

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_multimapvalue_type"></a><a name="value_type"></a> hash_multimap:: value_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

hash_multimap에 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>설명

`value_type` 는 \<const [key_type](#key_type), [mapped_type](#mapped_type)> \<key_type, mapped_type> 비상수 반복기 또는 참조를 사용 하 여 연관 컨테이너의 키를 변경할 수 없으므로 쌍이 아닌 쌍으로 선언 됩니다.

### <a name="example"></a>예제

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
