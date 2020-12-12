---
description: Hash_map 클래스에 대해 자세히 알아보세요.
title: hash_map 클래스
ms.date: 11/04/2016
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
ms.openlocfilehash: 6f842e846d7ae171ecf754f9051794c56c04d4b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324137"
---
# <a name="hash_map-class"></a>hash_map 클래스

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

각 요소가 값이 고유하고 연결된 데이터 값인 정렬 키가 있는 쌍인 컬렉션에서 데이터를 신속하게 저장하고 검색합니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_map에 저장되는 키 데이터 형식입니다.

*입력할*\
hash_map에 저장되는 요소 데이터 형식입니다.

*특징이*\
두 요소 값을 정렬 키로 비교하여 상대 순서를 확인할 수 있는 클래스 비교 중 하나와 요소의 키 값을 `size_t` 형식의 부호 없는 정수에 매핑하는 단항 조건자인 해시 함수의 두 개체를 포함하는 형식입니다. 이 인수는 선택 사항이며 hash_compare<`Key`, less<`Key`> >가 기본값입니다.

*할당자*\
hash_map의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 할당자>입니다 \<pair <const `Key`, `Type`> .

## <a name="remarks"></a>설명

hash_map은

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 요소가 요소의 키 값에 적용된 해시 함수 값을 기반으로 하여 버킷으로 그룹화되기 때문에 해시됩니다.

- 각각의 요소가 반드시 고유한 키를 가지고 있어야 한다는 점에서 고유성을 갖고 있습니다.

- 요소의 데이터 값은 키 값과 구별되기 때문에 쌍 연관 컨테이너입니다.

- 클래스 템플릿은 제공 된 기능이 일반적 이므로 요소 또는 키로 포함 된 데이터의 특정 형식과 독립적 이기 때문입니다. 요소에 사용될 데이터 형식과 키는 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

해시는 정렬보다 훨씬 효율적입니다. 성공적인 해시는 정렬 방식에 대한 컨테이너의 요소 수 로그에 비례하는 시간과 비교할 때 삽입, 삭제, 찾기를 일정한 평균 시간 이내에 수행합니다. hash_map 요소의 값은 연관된 키 값을 제외하고 직접적으로 변경할 수 있습니다. 대신, 이전 요소와 관련된 키 값을 삭제하고 새 요소와 연결된 새 키 값을 삽입해야 합니다.

컨테이너 형식은 일반적으로 애플리케이션에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 해시된 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 명시적으로 이러한 작업을 지원하는 멤버 함수는 잘 설계된 해시 함수와 함께 사용할 경우 효율적이며, 컨테이너의 요소 수에 종속되지 않는 일정한 평균 시간으로 작업을 수행합니다. 잘 설계된 해시 함수는 해시된 값의 균일한 분포를 생성하고 충돌 수를 최소화합니다. 여기서 충돌은 특정 키 값이 동일한 해시된 값에 매핑될 때 발생합니다. 가능한 최악의 해시 함수가 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간).

애플리케이션에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 hash_map입니다. 이 형식의 구조체를 위한 모델은 정의를 제공하는 연관 문자열 값이 있고 고유하게 나타나는 키 단어의 정렬된 목록입니다. 대신, 단어에 둘 이상의 올바른 정의가 있어서 키가 고유하지 않은 경우 hash_multimap은 선택한 컨테이너가 됩니다. 반면에 단어 목록만 저장하는 경우에는 hash_set이 올바른 컨테이너가 됩니다. 단어를 여러 번 중복할 수 있는 경우 hash_multiset이 적절한 컨테이너 구조입니다.

Hash_map은 [value_compare](../standard-library/value-compare-class.md)클래스의 저장 된 해시 *특성* 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다. 이 저장된 개체는 [key_comp](#key_comp) 멤버 함수를 호출하여 액세스할 수 있습니다. 이러한 함수 개체는<키 [hash_compare](../standard-library/hash-compare-class.md) 클래스의 개체와 동일 하 게 동작 해야 합니다 \<Key>>. 특히, *key* 형식의 모든 값 *키* 에 대해 호출 `Traits` ()은 `Key` 형식의 값 분포를 생성 합니다 `size_t` .

일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 f (x y)는 두 인수 개체 `x` 및 `y` 및 반환 값이 또는 인 함수 개체입니다 **`true`** **`false`** . 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적인 경우 hash_map에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서, f(x, y)  및 f(y, x)가 모두 false인 경우 x 및 y 두 개체는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 순서 지정 함수 및 컨테이너 개체에 저장된 해시 테이블의 현재 크기에 따라 달라집니다. 해시 테이블의 현재 크기를 확인할 수 없으므로 제어된 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

hash_map 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [hash_map](#hash_map) 클래스 멤버 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 모음이지만, 클래스 멤버 함수의 맥락에서 반복기 범위`[First, Last)`에 대해 설명하는 데에는 충분합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[hash_map](#hash_map)|비어 있거나 다른 `hash_map`의 전체 또는 일부의 복사본인 `hash_map`을 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `hash_map` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_map` .|
|[const_pointer](#const_pointer)|의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `hash_map` .|
|[const_reference](#const_reference)|**`const`** `hash_map` 작업을 읽고 수행 하기 위해에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** `hash_map` .|
|[difference_type](#difference_type)|부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 `hash_map`의 요소의 개수를 표현하는 데 사용할 수 있습니다.|
|[iterator](#iterator)|`hash_map`에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[key_compare](#key_compare)|`hash_map`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|`hash_map`의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.|
|[mapped_type](#mapped_type)|`hash_map` 내에 저장된 데이터 형식을 나타내는 형식입니다.|
|[놓고](#pointer)|`hash_map`의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`hash_map` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 `hash_map`의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|`hash_map`에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|두 요소를 정렬 키로 비교하여 `hash_map`에서 상대적 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[at](#at)|지정된 키 값이 있는 `hash_map`의 요소를 찾습니다.|
|[시작](#begin)|`hash_map`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`hash_map`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`hash_map`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`hash_map`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `hash_map`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 `hash_map`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 `hash_map`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `hash_map`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `hash_map`에 삽입합니다.|
|[empty](#empty)|`hash_map`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`hash_map`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|지정된 키보다 더 큰 키를 가진 `hash_map`의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 `hash_map`의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.|
|[erase](#erase)|`hash_map`의 지정된 위치에서 요소 또는 요소 범위를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `hash_map` 내 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `hash_map` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`hash_map`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_comp)|`hash_map`에서 지정된 키보다 크거나 같은 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[lower_bound](#lower_bound)|`hash_map`에서 지정된 키보다 크거나 같은 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`hash_map`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `hash_map`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `hash_map`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`hash_map`에 있는 요소 수를 반환합니다.|
|[스왑을](#swap)|두 `hash_map`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`hash_map`에서 지정된 키보다 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|`hash_map`에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator&#91;&#93;](#op_at)|지정된 키 값을 사용하여 `hash_map`에 요소를 삽입합니다.|
|[hash_map:: operator =](#op_eq)|`hash_map`의 요소를 다른 `hash_map`의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<hash_map>

**네임스페이스:** stdext

## <a name="hash_mapallocator_type"></a><a name="allocator_type"></a> hash_map:: allocator_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="hash_mapat"></a><a name="at"></a> hash_map:: at

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키 값을 사용하여 hash_map에서 요소를 찾습니다.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
찾을 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

찾은 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값을 찾을 수 없는 경우 이 함수는 [out_of_range 클래스](../standard-library/out-of-range-class.md) 클래스의 개체를 throw합니다.

### <a name="example"></a>예제

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="hash_mapbegin"></a><a name="begin"></a> hash_map:: begin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

hash_map의 첫 번째 요소 또는 빈 hash_map 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_mapcbegin"></a><a name="cbegin"></a> hash_map:: cbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 첫 번째 요소 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

[hash_map](../standard-library/hash-map-class.md)의 첫 번째 요소 또는 빈 `hash_map` 다음의 위치 주소를 지정하는 상수 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapcend"></a><a name="cend"></a> hash_map:: cend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

[hash_map](../standard-library/hash-map-class.md)에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 양방향 반복기입니다. `hash_map`이 비어 있으면 `hash_map::cend == hash_map::begin`입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 `hash_map`의 끝에 도달했는지 여부를 테스트하는 데 사용됩니다.

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapclear"></a><a name="clear"></a> hash_map:: clear

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 hash_map::clear 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="hash_mapconst_iterator"></a><a name="const_iterator"></a> hash_map:: const_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

Hash_map의 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

`const_iterator`Hash_map 정의 된는 형식이 인 [value_type](#value_type)개체인 요소를 가리킵니다 .이는 `pair< const Key, Type >` 첫 번째 멤버가 요소에 대 한 키이 고 두 번째 멤버가 요소에 의해 보유 되는 매핑된 데이텀의 경우입니다.

`const_iterator` `cIter` Hash_map의 요소를 가리키는를 역참조 하려면 연산자를 사용 `->` 합니다.

요소에 대 한 키의 값에 액세스 하려면 `cIter->first` 에 해당 하는를 사용 `(*cIter).first` 합니다. 요소에 대 한 매핑된 데이텀의 값에 액세스 하려면 `cIter->second` 에 해당 하는를 사용 `(*cIter).second` 합니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_mapconst_pointer"></a><a name="const_pointer"></a> hash_map:: const_pointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

Hash_map의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 hash_map 개체의 요소에 액세스해야 합니다.

## <a name="hash_mapconst_reference"></a><a name="const_reference"></a> hash_map:: const_reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

**`const`** 작업을 읽고 수행 하기 위해 hash_map에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="hash_mapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_map:: const_reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

Hash_map의 모든 요소를 읽을 수 있는 양방향 반복기를 제공 하는 형식입니다 **`const`** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 hash_map을 역방향으로 반복하는 데 사용됩니다.

`const_reverse_iterator`Hash_map 정의 된는 형식이 인 [value_type](#value_type)개체인 요소를 가리킵니다 .이는 `pair` \< **const Key, Type**> 첫 번째 멤버가 요소에 대 한 키이 고 두 번째 멤버가 요소에 의해 보유 되는 매핑된 데이텀의 경우입니다.

hash_map의 요소를 가리키는 `const_reverse_iterator` `crIter`를 역참조하려면 **->** 연산자를 사용합니다.

요소에 대한 키의 값에 액세스하려면 `crIter` -> **first** 를 사용합니다. 이 항목은 (\* `crIter`) **.first** 와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `crIter` -> **second** 를 사용합니다. 이 항목은 (\* `crIter`). **첫 번째** 입니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="hash_mapcount"></a><a name="count"></a> hash_map:: count

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

키가 매개 변수로 지정된 키와 일치하는 hash_map의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
hash_map에서 일치시킬 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

hash_map에 정렬 키가 매개 변수 키와 일치하는 요소가 있는 경우 1이고, hash_map에 일치하는 키가 포함된 요소가 없는 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 범위에 있는 *x* 요소의 수를 반환합니다.

\[ lower_bound (*키*), upper_bound (*키*))

고유한 결합형 컨테이너인 hash_map의 경우 0 또는 1입니다.

### <a name="example"></a>예제

다음 예제에서는 hash_map::count 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
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
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_mapcrbegin"></a><a name="crbegin"></a> hash_map:: crbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_map에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_map](../standard-library/hash-map-class.md)에서 첫 번째 요소 또는 정방향 `hash_map`에서 마지막 요소의 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 [begin](#begin)이 `hash_map`에서 사용되는 것처럼 역방향 hash_map에서 사용됩니다.

반환 값이 `crbegin`이면 `hash_map` 개체를 수정할 수 없습니다.

`crbegin`은 `hash_map`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapcrend"></a><a name="crend"></a> hash_map:: crend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_map에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [hash_map](../standard-library/hash-map-class.md)에서 마지막 요소 다음의 위치(정방향 `hash_map`의 첫 번째 요소 앞의 위치) 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 [hash_map::end](#end)가 `hash_map`에서 사용되는 것처럼 역방향 `hash_map`에서 사용됩니다.

반환 값이 `crend`이면 `hash_map` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `hash_map` 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapdifference_type"></a><a name="difference_type"></a> hash_map::d ifference_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 hash_map의 요소 개수를 표현하는 데 사용할 수 있습니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>예제

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="hash_mapemplace"></a><a name="emplace"></a> hash_map:: emplace

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

생성된 요소를 hash_map에 삽입합니다.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_map`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_map](../standard-library/hash-map-class.md)에 삽입되는 요소를 이동 생성하는 데 사용되는 값입니다.

### <a name="return-value"></a>반환 값

`emplace` 멤버 함수는 해당 부울 구성 요소가 삽입이 수행된 경우 true를 반환하고, 해당 키가 순서 지정 시 동일한 값을 가지고 해당 반복기 구성 요소에서 새 요소가 삽입되었거나 요소가 이미 있었던 주소를 반환하는 요소가 `hash_map`에 이미 들어 있었던 경우에는 false를 반환합니다.

이 멤버 함수가 반환하는 `pr` 쌍의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 해당 구성 요소를 역참조하려면 `*(pr.first)`를 사용합니다. **`bool`** 이 멤버 함수가 반환 하는 쌍의 구성 요소에 액세스 하려면 `pr` 를 사용 하 고 해당 구성 요소를 `pr.second` 역참조 하려면를 사용 `*(pr.second)` 합니다.

### <a name="remarks"></a>설명

요소의 [hash_map::value_type](#value_type)은 쌍으로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

### <a name="example"></a>예제

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
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

## <a name="hash_mapemplace_hint"></a><a name="emplace_hint"></a> hash_map:: emplace_hint

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

배치 힌트를 사용하여 hash_map에 생성된 요소를 삽입합니다.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
`hash_map`이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 [hash_map](../standard-library/hash-map-class.md)에 삽입되는 요소를 이동 생성하는 데 사용되는 값입니다.

*_Where*\
올바른 삽입 지점 검색을 시작할 위치와 관련된 힌트입니다.

### <a name="return-value"></a>반환 값

[hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) 멤버 함수는 새 요소가 `hash_map`에 삽입되거나 동일한 순서를 가진 기존 요소가 있는 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

요소의 [hash_map::value_type](#value_type)은 쌍으로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

삽입 지점이 *_Where* 바로 다음에 오는 경우에는 로그 시간 대신 분할 상환 일정 시간에 삽입이 발생할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
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

## <a name="hash_mapempty"></a><a name="empty"></a> hash_map:: empty

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** hash_map 비어 있으면이 고, 그렇지 않으면입니다. **`false`** hash_map 비어 있지 않으면입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="hash_mapend"></a><a name="end"></a> hash_map:: end

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>반환 값

hash_map에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 양방향 반복기입니다. hash_map이 비어 있으면 hash_map::end == hash_map::begin입니다.

### <a name="remarks"></a>설명

`end` 는 반복기가 hash_map의 끝에 도달 했는지 여부를 테스트 하는 데 사용 됩니다.

`end`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="hash_mapequal_range"></a><a name="equal_range"></a> hash_map:: equal_range

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키보다 더 큰 키를 가진 hash_map의 첫 번째 요소와 지정된 키보다 더 크거나 같은 키를 가진 hash_map의 첫 번째 요소에 반복기의 쌍을 각각 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_map에서 요소의 정렬 키와 비교할 인수 키 값입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

멤버 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **첫째** , 하 한 반복기를 역참조 하려면 \* ()를 사용 `pr` 합니다. **첫 번째**). 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **둘째** , 상한 반복기를 역참조 하려면 (를 사용 \* `pr` 합니다. **second**).

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="hash_maperase"></a><a name="erase"></a> hash_map:: erase

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

지정된 위치에서 hash_map의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>매개 변수

*_Where*\
hash_map에서 제거할 요소의 위치입니다.

*기본*\
hash_map에서 제거되는 첫 번째 요소의 위치입니다.

*최신*\
hash_map에서 제거되는 마지막 요소 바로 뒤의 위치입니다.

*키인지*\
hash_map에서 제거할 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소를 지정하는 양방향 반복기이거나 이러한 요소가 없을 경우 hash_map의 끝에 대한 포인터입니다.

세 번째 멤버 함수의 경우 hash_map에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>설명

멤버 함수는 예외를 throw하지 않습니다.

### <a name="example"></a>예제

다음 예제에서는 hash_map::erase 멤버 함수의 사용을 보여 줍니다.

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="hash_mapfind"></a><a name="find"></a> hash_map:: find

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키와 같은 키를 가진 hash_map 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_map에서 요소의 정렬 키와 일치 여부를 확인할 키 값입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 hash_map의 마지막 요소 다음 위치에 대한 주소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

`find` hash_map의 요소를 주소 지정 하는 반복기를 반환 합니다 .이는 정렬 키가 작음 비교 가능 보다 작음 관계를 기준으로 순서를 지정 하는 이진 조건자 아래의 인수 키와 동일 합니다.

의 반환 값 `find` 이 [const_iterator](#const_iterator)에 할당 되는 경우 hash_map 개체를 수정할 수 없습니다. 의 반환 값 `find` 이 [iterator](#iterator)에 할당 되는 경우 hash_map 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapget_allocator"></a><a name="get_allocator"></a> hash_map:: get_allocator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>반환 값

hash_map에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

hash_map 클래스의 할당자는 클래스가 스토리지를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
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

## <a name="hash_maphash_map"></a><a name="hash_map"></a> hash_map:: hash_map

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

비어 있거나 일부 다른 hash_map의 전체 또는 부분에 대한 복사본인 hash_map을 생성합니다.

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>매개 변수

*항상*\
이 hash_map 개체에 사용할 저장소 할당자 클래스로, 기본값은 `Allocator` 입니다.

*생략*\
hash_map의 요소 순서를 지정하는 데 사용되는 상수 `Traits` 형식의 비교 함수로, 기본값은 `hash_compare`입니다.

*오른쪽*\
생성된 map이 복사본으로 지정될 hash_map입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
initializer_list

### <a name="remarks"></a>설명

모든 생성자는 hash_map의 메모리 스토리지를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. allocator 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 hash_map을 초기화합니다.

모든 생성자는 hash_map의 키 간 순서를 설정하는 데 사용되며 나중에 [key_comp](#key_comp)를 호출하여 반환할 수 있는 `Traits` 형식의 함수 개체를 저장합니다.

처음 세 생성자는 빈 초기 hash_map을 지정 하 고, 두 번째 생성자는 요소의 순서를 설정 하는 데 사용할 비교 함수 (*Comp*)의 형식을 지정 하며, 세 번째 생성자는 사용할 할당자 형식 (*Al*)을 명시적으로 지정 합니다. 키워드는 **`explicit`** 특정 종류의 자동 형식 변환을 표시 하지 않습니다.

네 번째 생성자는 hash_map *오른쪽* 의 복사본을 지정 합니다.

다음 3개 생성자는 hash_map의 범위 `[First, Last)`를 복사하며, 범위 내에서 클래스 `Traits` 및 allocator의 비교 함수 형식을 지정하는 명시도는 계속 높아집니다.

마지막 생성자는 hash_map *오른쪽* 으로 이동 합니다.

## <a name="hash_mapinsert"></a><a name="insert"></a> hash_map:: insert

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 요소 또는 요소의 범위를 삽입합니다.

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
hash_map이 해당 요소(또는 더 일반적으로는 키가 동등하게 정렬된 요소)를 이미 포함하고 있지 않을 경우 hash_map에 삽입될 요소의 값입니다.

*_Where*\
올바른 삽입 지점 검색을 시작할 위치와 관련된 힌트입니다.

*기본*\
hash_map에서 복사할 첫 번째 요소의 위치입니다.

*최신*\
hash_map에서 복사할 마지막 요소 바로 다음 위치입니다.

### <a name="return-value"></a>반환 값

첫 번째 `insert` 멤버 함수는 부울 구성 요소가 삽입이 수행 된 경우 true를 반환 하 고, 해당 키가 순서 지정 시 동일한 값을 가지 며, 반복기 구성 요소에서 새 요소가 삽입 되었거나 요소가 이미 있었던 주소를 반환 하 hash_map는 요소가 이미 포함 되어 있는 경우 false를 반환 하는 쌍을 반환 합니다.

이 멤버 함수가 반환하는 `pr` 쌍의 반복기 구성 요소에 액세스하려면 `pr`. **first** 를 사용 하 고 역참조 하려면 \* ()를 사용 `pr` 합니다. **첫 번째**). **`bool`** 이 멤버 함수가 반환 하는 쌍의 구성 요소에 액세스 하려면를 `pr` 사용 `pr` 합니다. **second** 를 사용 하 고 역참조 하려면 \* ( `pr` . **second**).

두 번째 `insert` 멤버 함수 힌트 버전은 새 요소가 hash_map 삽입 된 위치를 가리키는 반복기를 반환 합니다.

마지막 두 `insert` 멤버 함수는 삽입 된 값을 구문으로 이동 한다는 점을 제외 하 고 처음 두 함수와 동일 하 게 동작 합니다.

### <a name="remarks"></a>설명

요소의 [value_type](../standard-library/map-class.md#value_type)은 쌍이므로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

삽입 지점이 *_Where* 바로 다음에 오는 경우에는 로그 시간이 아니라 insert의 힌트 버전에 대 한 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

세 번째 멤버 함수는 지정된 set의 *[First, Last)* 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 hash_map에 요소 값의 시퀀스를 삽입합니다.

### <a name="example"></a>예제

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
The element 10 already exists in hm1
with a key value of ((pr.first) -> first) = 1.
After the insertions, the elements of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
5 => 50
After the insertions, the elements of hm2 are:
2 => 20
10 => 100
3 => 30
4 => 40
After the move insertion, hm3 contains:
1 => a
After the move insertion, hm4 contains:
2 => b
```

## <a name="hash_mapiterator"></a><a name="iterator"></a> hash_map:: iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>설명

`iterator`Hash_map 정의 된는 형식이 인 [value_type](#value_type)개체인 요소를 가리킵니다 .이는 `pair<const Key, Type>` 첫 번째 멤버가 요소에 대 한 키이 고 두 번째 멤버가 요소에 의해 보유 되는 매핑된 데이텀의 경우입니다.

`Iter`Multimap의 요소를 가리키는 이라는 반복기를 역참조 하려면 연산자를 사용 `->` 합니다.

요소에 대 한 키의 값에 액세스 하려면 `Iter->first` 에 해당 하는를 사용 `(*Iter).first` 합니다. 요소에 대 한 매핑된 데이텀의 값에 액세스 하려면 `Iter->second` 에 해당 하는를 사용 `(*Iter).second` 합니다.

형식을 `iterator` 사용 하 여 요소의 값을 수정할 수 있습니다.

### <a name="example"></a>예제

`iterator`을 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="hash_mapkey_comp"></a><a name="key_comp"></a> hash_map:: key_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

hash_map이 요소의 순서를 지정하는 데 사용하는 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

저장된 개체는 멤버 함수

`bool operator( const Key& left, const Key&right );`

**`true`** `left` 가 보다 앞에 있고가 정렬 순서에서와 같지 않으면를 반환 합니다 `right` .

### <a name="example"></a>예제

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="hash_mapkey_compare"></a><a name="key_compare"></a> hash_map:: key_compare

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

map의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare`는 템플릿 매개 변수 `Traits`의 동의어입니다.

`Traits`에 대한 자세한 내용은 [hash_map 클래스](../standard-library/hash-map-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="hash_mapkey_type"></a><a name="key_type"></a> hash_map:: key_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type`는 템플릿 매개 변수 `Key`의 동의어입니다.

`Key`에 대한 자세한 내용은 [hash_map 클래스](../standard-library/hash-map-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_maplower_bound"></a><a name="lower_bound"></a> hash_map:: lower_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 지정된 키보다 같거나 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_map에서 요소의 정렬 키와 비교할 인수 키 값입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 hash_map 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_map에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

`lower_bound`의 반환 값이 `const_iterator`에 할당된 경우 hash_map 개체는 수정할 수 없습니다. 의 반환 값이에 `lower_bound` 할당 되는 경우 `iterator` hash_map 개체를 수정할 수 있습니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapmapped_type"></a><a name="mapped_type"></a> hash_map:: mapped_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>설명

`mapped_type` 형식은 템플릿 매개 변수 `Type`의 동의어입니다.

`Type`에 대한 자세한 내용은 [hash_map 클래스](../standard-library/hash-map-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="hash_mapmax_size"></a><a name="max_size"></a> hash_map:: max_size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

hash_map의 최대 허용 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="hash_mapoperator"></a><a name="op_at"></a> hash_map:: operator []

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

지정된 키 값을 사용하여 `hash_map`에 요소를 삽입합니다.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>매개 변수

*키인지*\
삽입할 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

삽입된 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값이 없으면 데이터 형식의 기본값과 함께 삽입됩니다.

`operator[]`는 다음을 사용하여 요소를 `hash_map m`에 삽입하는 데 사용될 수 있습니다.

`m[ key] = DataValue`;

여기서 DataValue는 키 `mapped_type` 값이 *key* 인 요소의 값입니다.

`operator[]`를 사용하여 요소를 삽입하는 경우 반환된 참조는 삽입이 기존 요소를 변경하는지 또는 새 요소를 생성하는지 여부를 나타내지 않습니다. 멤버 함수 [find](../standard-library/map-class.md#find) 및 [insert](../standard-library/map-class.md#insert)는 지정된 키가 포함된 요소가 삽입 전에 이미 있는지 여부를 확인하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="hash_mapoperator"></a><a name="op_eq"></a> hash_map:: operator =

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map의 요소를 다른 hash_map의 복사본으로 바꿉니다.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`hash_map`으로 복사되는 [hash_map 클래스](../standard-library/hash-map-class.md)입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `hash_map` 는 `operator=` 의 내용을로 복사 하거나 이동  `hash_map` 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

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

## <a name="hash_mappointer"></a><a name="pointer"></a> hash_map::p ointer

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>설명

형식을 `pointer` 사용 하 여 요소의 값을 수정할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 hash_map 개체의 요소에 액세스해야 합니다.

## <a name="hash_maprbegin"></a><a name="rbegin"></a> hash_map:: rbegin

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_map에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 hash_map에서 첫 번째 요소 또는 정방향 hash_map에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 [begin](#begin)이 hash_map에서 사용되는 것처럼 역방향 hash_map에서 사용됩니다.

`rbegin`의 반환 값이 [const_reverse_iterator](#const_reverse_iterator)에 할당되는 경우에는 hash_map 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 [reverse_iterator](#reverse_iterator)에 할당되는 경우에는 hash_map 개체를 수정할 수 있습니다.

`rbegin`은 hash_map을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="hash_mapreference"></a><a name="reference"></a> hash_map:: reference

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="hash_maprend"></a><a name="rend"></a> hash_map:: rend

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_map에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 hash_map에서 마지막 요소 다음의 위치(정방향 hash_map의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 [end](#end)가 hash_map에서 사용되는 것처럼 역방향 hash_map에서 사용됩니다.

`rend`의 반환 값이 [const_reverse_iterator](#const_reverse_iterator)에 할당되는 경우에는 hash_map 개체를 수정할 수 없습니다. `rend`의 반환 값이 [reverse_iterator](#reverse_iterator)에 할당되는 경우에는 hash_map 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 hash_map 끝에 도달했는지 여부를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="hash_mapreverse_iterator"></a><a name="reverse_iterator"></a> hash_map:: reverse_iterator

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

역방향 hash_map의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 요소 값을 수정할 수 없으며 hash_map을 역방향으로 반복하는 데 사용됩니다.

`reverse_iterator`Hash_map 정의 된는 [value_type](#value_type)의 개체인 요소를 가리킵니다 .이는 첫 번째 멤버가 요소에 대 한 키이 고 두 번째 멤버가 요소에 의해 보유 된 매핑된 데이텀이 고, 형식 **쌍 \<const Key, Type>** 입니다.

hash_map의 요소를 가리키는 `reverse_iterator` `rIter`를 역참조하려면 -> 연산자를 사용합니다.

요소에 대한 키의 값에 액세스하려면 `rIter` -> **first** 를 사용합니다. 이 항목은 (\* `rIter`). **첫 번째** 입니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `rIter` -> **second** 를 사용합니다. 이 항목은 (\* `rIter`). **첫 번째** 입니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="hash_mapsize"></a><a name="size"></a> hash_map:: size

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

hash_map의 현재 길이입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 hash_map::size 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="hash_mapsize_type"></a><a name="size_type"></a> hash_map:: size_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 요소 수를 표현할 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>설명

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="hash_mapswap"></a><a name="swap"></a> hash_map:: swap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_map의 요소를 교환합니다.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
대상 hash_map과 교환할 요소를 제공하는 인수 hash_map입니다.

### <a name="remarks"></a>설명

멤버 함수는 해당 요소를 교환할 두 hash_map의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="hash_mapupper_bound"></a><a name="upper_bound"></a> hash_map:: upper_bound

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에서 지정된 키보다 큰 값을 가진 키가 포함된 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색 중인 hash_map에서 요소의 정렬 키 값과 비교할 인수 키 값입니다.

### <a name="return-value"></a>반환 값

인수 키보다 큰 키가 들어 있는 hash_map 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 hash_map에서 마지막 요소 다음 위치의 주소를 지정하는 [iterator](#iterator) 또는 [const_iterator](#const_iterator)입니다.

반환 값이 `const_iterator`에 할당된 경우 hash_map 개체는 수정할 수 없습니다. 반환 값이에 할당 되는 경우 `iterator` hash_map 개체를 수정할 수 있습니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="hash_mapvalue_comp"></a><a name="value_comp"></a> hash_map:: value_comp

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

키 값을 비교하여 hash_map의 요소 순서를 결정하는 함수 개체를 반환합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

hash_map이 요소의 순서를 지정하는 데 사용하는 비교 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

Hash_map *m* 의 경우 두 요소인 *e1* (*k1*, *d1*) 및 *e2* (*k2*, *d2*)는 [value_type](#value_type)형식의 개체이 고, 여기서 *k1* 와 *k2* 는 [key_type](#key_type) 형식의 키이 고 *d1* 및 *d2* 는 [mapped_type](#mapped_type)형식의 데이터입니다. 그런 다음는와 `m.value_comp()(e1, e2)` 동일 `m.key_comp()(k1, k2)` 합니다. 저장된 개체는 멤버 함수

`bool operator(value_type& left, value_type& right);`

**`true`** 의 키 값 `left` 이 보다 앞에 오고가 정렬 순서에서의 키 값과 같지 않은 경우를 반환 합니다 `right` .

### <a name="example"></a>예제

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_mapvalue_type"></a><a name="value_type"></a> hash_map:: value_type

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

hash_map에 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>설명

`value_type` 는 `pair<const key_type, mapped_type>` `pair<key_type, mapped_type>` 비상수 반복기 또는 참조를 사용 하 여 연관 컨테이너의 키를 변경할 수 없기 때문에이 아니라로 선언 됩니다.

### <a name="example"></a>예제

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
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
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
