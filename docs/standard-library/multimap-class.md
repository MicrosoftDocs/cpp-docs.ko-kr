---
title: multimap 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25dffabfe01bb68af180d67b5b47dfee44ce30ff
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153147"
---
# <a name="multimap-class"></a>multimap 클래스

C++ 표준 라이브러리 multimap 클래스는 각 요소가 데이터 값과 정렬 키를 갖고 있는 쌍인 컬렉션에서 데이터의 저장과 검색에 사용됩니다. 키 값은 고유할 필요가 없으며 데이터를 자동으로 정렬하는 데 사용됩니다. multimap 요소의 값은 연관된 키 값을 제외하고 직접적으로 변경할 수 있습니다. 대신, 이전 요소와 관련된 키 값을 삭제하고 새 요소와 연결된 새 키 값을 삽입해야 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>매개 변수

`Key` Multimap에 저장 되는 키 데이터 형식입니다.

`Type` Multimap에 저장 되는 요소 데이터 형식

`Traits` Multimap 내에서 해당 상대 순서를 결정 하는 정렬 키로 두 요소 값을 비교할 수 있는 함수 개체를 제공 하는 형식입니다. 이진 조건자 `less<Key>`가 기본값입니다.

C++14에서는 형식 매개 변수가 없는 `std::less<>` 또는 `std::greater<>` 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)를 참조하세요

`Allocator` Map의 할당 및 메모리 할당 취소에 대 한 세부 정보를 캡슐화 하는 저장 된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<pair <const Key, Type> >`입니다.

## <a name="remarks"></a>설명

C++ 표준 라이브러리 multimap 클래스의 특징은 다음과 같습니다.

- 연관된 키 값을 기준으로 하며 요소 값의 효율적인 검색을 지원하는 가변 크기 컨테이너인 연관 컨테이너입니다.

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 해당 요소가 컨테이너 내에서 지정된 비교 함수에 따라 키 값을 기준으로 정렬되므로 정렬됩니다.

- 해당 요소는 고유 키를 가질 필요가 없기 때문에 복수이며, 하나의 키 값은 이와 연관된 많은 요소 데이터 값을 가질 수 있습니다.

- 요소의 데이터 값은 키 값과 구별되기 때문에 쌍 연관 컨테이너입니다.

- 제공하는 기능이 제네릭이고 요소 또는 키로 포함된 데이터의 특정 형식과 독립적이므로 템플릿 클래스입니다. 요소에 사용될 데이터 형식과 키는 대신 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

map 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [multimap](#multimap) 클래스 구성원 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 최소화된 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 관련된 상세 기능별로 범주를 구성합니다. 각 반복기 개념은 고유한 요구 사항이 있으며 이러한 요구 사항을 적용하는 알고리즘은 해당 반복기 형식이 제공하는 요구 사항으로 가정을 제한해야 합니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가되는 경우를 가정할 수 있습니다. 이는 최소한의 기능 모음이지만, 클래스 멤버 함수의 맥락에서 반복기 범위(`[First, Last)`)에 대해 설명하는 데에는 충분합니다.

컨테이너 형식은 일반적으로 응용 프로그램에서 필요한 검색과 삽입의 형식을 기준으로 선택해야 합니다. 연관 컨테이너들은 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 이러한 작업을 명시적으로 지원하는 멤버 함수는 컨테이너의 요소 개수를 진수로 하는 로그값에 평균적으로 비례하는 시간 안에 수행하므로 효율적입니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

응용 프로그램에서 값과 해당 키를 연결하는 조건을 만족할 경우 적절한 연관 컨테이너는 multimap입니다. 이 구조 형식의 모델은 단어들이 항상 유일하게 정의되지 않는 "정의" 같이 문자열 값과 연결된 키 단어들의 정렬된 목록입니다. 대신 키워드가 고유하게 정의되어 키가 고유한 경우, map이 적절한 컨테이너가 됩니다. 반면에, 단어의 목록만을 저장하는 경우에는 set이 올바른 컨테이너가 됩니다. 단어의 여러 번 중복이 허용된 경우는 multiset이 적절한 컨테이너 구조입니다.

multimap은 [key_compare](#key_compare) 형식의 저장된 함수 개체를 호출하여 제어하는 시퀀스를 정렬합니다. 이 저장된 개체는 [key_comp](#key_comp) 구성원 함수를 호출하여 액세스할 수 있는 비교 함수입니다. 일반적으로, 이 순서를 정하려면 요소의 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 기술적으로 설명하면, 비교 함수는 표준 함수의 의미에서 엄밀히 약한 정렬을 수행하는 이진 조건자입니다. 이진 조건자 `f(x,y)`는 두 인수 개체 `x` 및 `y`를 가지는 함수 개체이며 true 또는 false를 반환합니다. 이진 조건자가 비재귀적, 비대칭, 전이적인 경우 및 동등성이 전이적인 경우 set에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서 `x` 및 `y`가 모두 false인 경우 두 개체 `f(x,y)` 및 `f(y,x)`는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.

C++14에서는 형식 매개 변수가 없는 `std::less<>` 또는 `std::greater<>` 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers)를 참조하세요.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[multimap](#multimap)|비어 있거나 다른 `multimap`의 전체 또는 일부의 복사본인 `multimap`을 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 개체의 `multimap` 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|`const`에 있는 `multimap` 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[const_pointer](#const_pointer)|`const`에 있는 `multimap` 요소에 대한 포인터를 제공하는 형식입니다.|
|[const_reference](#const_reference)|`const` 작업을 읽고 수행하기 위해 `multimap`에 저장된 `const` 요소에 대한 참조를 제공하는 형식입니다.|
|[const_reverse_iterator](#const_reverse_iterator)|`const`에 있는 `multimap` 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[difference_type](#difference_type)|부호 있는 정수 형식은 반복기가 가리키는 요소 사이의 범위에 있는 `multimap`의 요소의 개수를 표현하는 데 사용할 수 있습니다.|
|[iterator](#iterator)|동일한 `multimap` 안에서 요소를 참조하는 두 반복기 사이의 차이를 제공하는 형식입니다.|
|[key_compare](#key_compare)|`multimap`의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.|
|[key_type](#key_type)|`multimap`의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.|
|[mapped_type](#mapped_type)|`multimap` 내에 저장된 데이터 형식을 나타내는 형식입니다.|
|[pointer](#pointer)|`const`에 있는 `multimap` 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|`multimap` 내에 저장된 요소에 대한 참조를 제공하는 형식입니다.|
|[reverse_iterator](#reverse_iterator)|역순 `multimap`의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.|
|[size_type](#size_type)|`const`의 `multimap` 요소에 대한 포인터를 제공하는 부호 없는 정수 형식입니다.|
|[value_type](#value_type)|두 요소를 정렬 키로 비교하여 `multimap`에서 상대적 순서를 결정할 수 있는 함수 개체를 제공하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[begin](#begin)|`multimap`의 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.|
|[cbegin](#cbegin)|`multimap`의 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[cend](#cend)|`multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[clear](#clear)|`multimap`의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수로 지정된 키와 일치하는 `multimap`의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 `multimap`에서 첫 번째 요소를 주소 지정하는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 `multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|생성된 요소를 `multimap`에 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 생성된 요소를 `multimap`에 삽입합니다.|
|[empty](#empty)|`multimap`가 비어 있는지 여부를 테스트합니다.|
|[end](#end)|`multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[equal_range](#equal_range)|요소의 키가 지정된 값과 일치하는 요소 범위를 찾습니다.|
|[erase](#erase)|지정된 위치에서 `multimap`의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.|
|[find](#find)|지정된 키와 같은 키를 가진 `multimap` 내 요소의 첫 번째 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|`allocator`을 생성하는 데 사용되는 `multimap` 개체의 복사본을 반환합니다.|
|[insert](#insert)|`multimap`에 요소 또는 요소의 범위를 삽입합니다.|
|[key_comp](#key_comp)|`multimap`에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.|
|[lower_bound](#lower_bound)|`multimap`에서 지정된 키보다 같거나 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|`multimap`의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 `multimap`에서 첫 번째 요소를 참조하는 반복기를 반환합니다.|
|[rend](#rend)|역순 `multimap`에서 마지막 요소 다음에 나오는 위치를 주소 지정하는 반복기를 반환합니다.|
|[size](#size)|`multimap`에 있는 요소 수를 반환합니다.|
|[swap](#swap)|두 `multimap`의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|`multimap`에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|멤버 함수는 키 값을 비교하여 `multimap`의 요소 순서를 결정하는 함수 개체를 반환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator=](#op_eq)|`multimap`의 요소를 다른 `multimap`의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<map>

**네임스페이스:** std

( **key**, **value**) 쌍은 `pair` 형식의 개체로 multimap에 저장됩니다. pair 클래스에는 \<map>에 의해 자동으로 포함되는 \<utility> 헤더가 필요합니다.

## <a name="allocator_type"></a>  multimap::allocator_type

multimap 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="begin"></a>  multimap::begin

multimap의 첫 번째 요소 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

multimap의 첫 번째 요소 또는 빈 multimap 다음의 위치 주소를 지정하는 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="cbegin"></a>  multimap::cbegin

범위의 첫 번째 요소를 주소 지정하는 `const` 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 `const` 양방향 액세스 반복기입니다(빈 범위의 경우 `cbegin() == cend()`).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container`가 `begin()` 및 `cbegin()`를 지원하는 수정 가능(비`const`)한 컨테이너로 가정합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multimap::cend

범위에서 마지막 요소 바로 다음의 위치를 주소 지정하는 `const` 반복기를 반환합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 `const` 양방향 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container`가 `end()` 및 `cend()`를 지원하는 수정 가능(비`const`)한 컨테이너로 가정합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="clear"></a>  multimap::clear

multimap의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

다음 예제에서는 multimap::clear 멤버 함수의 사용을 보여 줍니다.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="const_iterator"></a>  multimap::const_iterator

multimap의 **const** 요소 하나를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

`const_iterator` 의 개체에 multimap 점으로 정의 [value_type](#value_type), 유형을 `pair` * \< * **const 키**, **형식 * * * >* 합니다. 키의 값은 첫 번째 구성원 쌍을 통해 제공되며 매핑된 요소값은 쌍의 두 번째 구성원를 통해 제공됩니다.

역참조에 `const_iterator` `cIter` 사용 하는 multimap의 요소를 가리키는 **->** 연산자입니다.

요소에 대한 키의 값에 액세스하려면 `cIter` -> **first**를 사용합니다. 이 항목은 (\* `cIter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `cIter` -> **second**를 사용합니다. 이 항목은 (\* `cIter`). **second**와 같습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="const_pointer"></a>  multimap::const_pointer

multimap에서 **const** 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 multimap 개체의 요소에 액세스해야 합니다.

## <a name="const_reference"></a>  multimap::const_reference

**const** 작업을 읽고 수행하기 위해 multimap에 저장된 **const** 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>예제

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="const_reverse_iterator"></a>  multimap::const_reverse_iterator

multimap의 모든 **const** 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소값을 수정할 수 없으며 multimap을 역방향으로 반복하는 데 사용됩니다.

`const_reverse_iterator` 의 개체에 multimap 점으로 정의 [value_type](#value_type), 유형을 `pair` * \< * **const 키**, **형식 * * * >* 합니다. 키의 값은 첫 번째 구성원 쌍을 통해 제공되며 매핑된 요소값은 쌍의 두 번째 구성원를 통해 제공됩니다.

역참조에 `const_reverse_iterator` `crIter` 사용 하는 multimap의 요소를 가리키는 **->** 연산자입니다.

요소에 대한 키의 값에 액세스하려면 `crIter` -> **first**를 사용합니다. 이 항목은 (\* `crIter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `crIter` -> **second**를 사용합니다. 이 항목은 (\* `crIter`). **first**와 같습니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)의 예제를 참조하세요.

## <a name="count"></a>  multimap::count

키가 매개 변수로 지정된 키와 일치하는 multimap의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` Multimap에서 일치 시킬 요소의 키입니다.

### <a name="return-value"></a>반환 값

정렬 키가 매개 변수 키와 일치하는 요소가 있는 경우 해당 요소 수이고, multimap에 일치하는 키가 포함된 요소가 없는 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 범위에 있는 요소 중에서

[ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )

키 값 `key`를 가진 요소의 수를 반환합니다.

### <a name="example"></a>예제

다음 예제에서는 multimap::count 멤버 함수의 사용을 보여 줍니다.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multimap::crbegin

역방향 multimap에서 첫 번째 요소의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [multimap](../standard-library/multimap-class.md)에서 첫 번째 요소 또는 정방향 `multimap`에서 마지막 요소의 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 `multimap`에서 [begin](#begin)이 사용되는 것처럼 역방향 `multimap`에 사용됩니다.

반환 값이 `crbegin`이면 `multimap` 개체를 수정할 수 없습니다.

`crbegin`은 `multimap`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="crend"></a>  multimap::crend

역방향 multimap에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 상수 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [multimap](../standard-library/multimap-class.md)에서 마지막 요소 다음의 위치(정방향 `multimap`의 첫 번째 요소 앞의 위치) 주소를 지정하는 상수 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 [multimap::end](#end)가 `multimap`에 사용되는 것처럼 역방향 `multimap`에 사용됩니다.

반환 값이 `crend`이면 `multimap` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `multimap` 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="difference_type"></a>  multimap::difference_type

반복기가 가리키는 요소 사이의 범위에 있는 multimap의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type` 는 일반적으로 범위에 있는 요소의 수를 나타내는 데 사용 [*첫 번째*, *마지막*) 반복기 사이의 `first` 및 `last`를 가리키는 요소를 포함 합니다. 여 `first` 가 가리키는 요소 점을 포함 하지 않고 까지의 범위를 요소 및 `last`합니다.

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="emplace"></a>  multimap::emplace

생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|`args`|multimap에 삽입할 요소를 생성하기 위해 전달되는 인수입니다.|

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

### <a name="remarks"></a>설명

이 함수는 컨테이너 요소에 대한 참조는 무효화하지 않지만 컨테이너에 대한 모든 반복기는 무효화할 수 있습니다.

삽입하는 동안 예외가 throw되면 컨테이너는 변경되지 않고 예외가 다시 throw됩니다.

요소의 [value_type](../standard-library/map-class.md#value_type)은 쌍으로, 요소값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

### <a name="example"></a>예제

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="emplace_hint"></a>  multimap::emplace_hint

배치 힌트를 사용하여 생성된 요소를 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|`args`|multimap에 삽입할 요소를 생성하기 위해 전달되는 인수입니다.|
|`where`|올바른 삽입 지점 검색을 시작할 위치입니다. 이 지점이 `where` 바로 앞에 오면 로그 시간 대신 분할된 시간에 삽입할 수 있습니다.|

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

### <a name="remarks"></a>설명

이 함수는 컨테이너 요소에 대한 참조는 무효화하지 않지만 컨테이너에 대한 모든 반복기는 무효화할 수 있습니다.

대입 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다.

요소의 [value_type](../standard-library/map-class.md#value_type)은 쌍으로, 요소값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

코드 예제를 보려면 [map::emplace_hint](../standard-library/map-class.md#emplace_hint)를 참조하세요.

## <a name="empty"></a>  multimap::empty

multimap이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

multimap이 비어 있으면 **true**이고 비어 있지 않으면 **false**입니다.

### <a name="example"></a>예제

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="end"></a>  multimap::end

마지막 바로 다음 반복기를 반환합니다.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>반환 값

마지막 바로 다음 반복기입니다. multimap이 비어 있으면 `multimap::end() == multimap::begin()`입니다.

### <a name="remarks"></a>설명

**end**는 반복기가 multimap의 끝을 통과했는지를 테스트하는 데 사용됩니다.

**end**에서 반환한 값은 역참조해서는 안 됩니다.

코드 예제를 보려면 [multimap::find](#find)를 참조하세요.

## <a name="equal_range"></a>  multimap::equal_range

요소의 키가 지정된 값과 일치하는 요소 범위를 찾습니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

반복기 쌍. 여기서 첫 번째 반복기는 키의 [lower_bound](#lower_bound)이고 두 번째 반복기는 키의 [upper_bound](#upper_bound)입니다.

구성원 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **first**를 사용하고 하한 반복기를 역참조하려면 \*( `pr`. **first**)를 사용합니다. 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **second**를 사용하고 상한 반복기를 역참조하려면 \*( `pr`. **second**)를 사용합니다.

### <a name="example"></a>예제

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  multimap::erase

지정된 위치에서 multimap의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

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

`Where` 제거할 요소의 위치입니다.

`First` 제거할 첫 번째 요소의 위치입니다.

`Last` 제거할 마지막 요소 바로 다음 위치입니다.

`Key` 제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

처음 두 구성원 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 map의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 구성원 함수의 경우 multimap에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>설명

코드 예제를 보려면 [map::erase](../standard-library/map-class.md#erase)를 참조하세요.

## <a name="find"></a>  multimap::find

지정된 키와 같은 키를 포함하는 multimap 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 multimap에서 요소의 정렬 키를 일치 시킬 키 값입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 multimap의 마지막 요소(`multimap::end()`) 다음 위치를 가리키는 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 보다 작음 비교 가능 관계를 기반으로 순서를 적용하는 이진 조건자에서 정렬 키가 인수 키와 같은 multimap 내 요소를 가리키는 반복기를 반환합니다.

**find**의 반환 값이 **const_iterator**에 할당되는 경우 multimap 개체를 수정할 수 없습니다. **find**의 반환 값이 **iterator**에 할당되는 경우에는 multimap 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  multimap::get_allocator

multimap을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

multimap에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

multimap 클래스의 할당자는 클래스가 저장소를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
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

## <a name="insert"></a>  multimap::insert

multimap에 요소 또는 요소의 범위를 삽입합니다.

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
|`Val`|multimap에 삽입할 요소의 값입니다.|
|`Where`|올바른 삽입 지점 검색을 시작할 위치입니다. 이 지점이 `Where` 바로 앞에 오면 로그 시간 대신 분할된 시간에 삽입할 수 있습니다.|
|`ValTy`|map이 [value_type](../standard-library/map-class.md#value_type)의 요소를 생성하는 데 사용할 수 있는 인수 형식을 지정하고 `Val`을 인수로 완벽하게 전달하는 템플릿 매개 변수입니다.|
|`First`|복사할 첫 번째 요소의 위치입니다.|
|`Last`|복사할 마지막 요소 바로 다음 위치입니다.|
|`InputIterator`|[value_type](../standard-library/map-class.md#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.|
|`IList`|요소를 복사할 원본 [initializer_list](../standard-library/initializer-list.md)입니다.|

### <a name="return-value"></a>반환 값

단일 요소 삽입 멤버 함수 (1) 및 (2)는 multimap에 새 요소를 삽입한 위치로 반복기를 반환합니다.

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 multimap에 새 요소를 삽입한 위치를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 어떠한 포인터 또는 참조를 무효화하지 않지만 컨테이너에 대한 모든 반복기를 무효화할 수 있습니다.

요소를 한 개만 삽입하는 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

컨테이너의 [value_type](../standard-library/map-class.md#value_type)은 컨테이너에 속한 typedef이고 map의 경우 `multimap<K, V>::value_type`은 `pair<const K, V>`입니다. 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소는 요소의 데이터 값과 동일한 정렬된 쌍입니다.

범위 멤버 함수 (5)는 `[First, Last)` 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 multimap에 요소 값의 시퀀스를 입력하므로 `Last`는 삽입되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `m.insert(v.begin(), v.end());` 문은 `v`의 모든 요소를 `m`에 삽입합니다.

이니셜라이저 목록 구성원 함수 (6)은 [initializer_list](../standard-library/initializer-list.md)를 사용하여 요소를 map으로 복사합니다.

생성된 요소를 제 위치에 삽입하려면, 즉 복사 또는 이동 작업을 수행하지 않으려면 [multimap::emplace](#emplace) 및 [multimap::emplace_hint](#emplace_hint)를 참조하세요.

### <a name="example"></a>예제

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  multimap::iterator

multimap에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

**반복기** 의 개체에 multimap 점으로 정의 [value_type](#value_type), 유형을 `pair` * \< * **const 키**, **형식 * * * >* 합니다. 키의 값은 첫 번째 구성원 쌍을 통해 제공되며 매핑된 요소값은 쌍의 두 번째 구성원를 통해 제공됩니다.

multimap의 요소를 가리키는 **반복기**`Iter`를 역참조하려면 **->** 연산자를 사용합니다.

요소에 대한 키의 값에 액세스하려면 `Iter` -> **first**를 사용합니다. 이 항목은 (\* `Iter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `Iter` -> **second**를 사용합니다. 이 항목은 (\* `Iter`). **second**와 같습니다.

형식 **iterator**는 요소값을 수정할 때 사용할 수 있습니다.

### <a name="example"></a>예제

**반복기**를 선언하고 사용하는 방법의 예제는 [begin](#begin)의 예제를 참조하세요.

## <a name="key_comp"></a>  multimap::key_comp

multimap에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

multimap이 요소의 순서를 지정하는 데 사용하는 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

저장된 개체는 구성원 함수

**bool operator**( **const Key&** *x*, **const Key&** *y*);

를 정의합니다. 이 함수는 정렬 순서에서 *x*가 엄격하게 *y* 앞에 오면 true를 반환합니다.

### <a name="example"></a>예제

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  multimap::key_compare

multimap의 두 요소 간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

**key_compare**는 템플릿 매개 변수 `Traits`와 동일한 의미입니다.

`Traits`에 대한 자세한 내용은 [multimap 클래스](../standard-library/multimap-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="key_type"></a>  multimap::key_type

multimap의 각 요소를 구성하는 정렬 키 개체를 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

**key_type**은 템플릿 매개 변수 `Key`와 동일한 의미입니다.

`Key`에 대한 자세한 내용은 [multimap 클래스](../standard-library/multimap-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`key_type`를 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="lower_bound"></a>  multimap::lower_bound

multimap에서 지정된 키보다 크거나 같은 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 multimap 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 multimap에서 마지막 요소 다음 위치의 주소를 지정하는 반복기 또는 `const_iterator`입니다.

`lower_bound`의 반환 값이 `const_iterator`에 할당된 경우 multimap 개체는 수정할 수 없습니다. `lower_bound`의 반환 값이 **iterator**에 할당되는 경우에는 multimap 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="mapped_type"></a>  multimap::mapped_type

multimap에 저장된 데이터 형식을 나타내는 형식입니다.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>설명

`mapped_type`은 템플릿 매개 변수 `Type`과 동일한 의미입니다.

`Type`에 대한 자세한 내용은 [multimap 클래스](../standard-library/multimap-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`key_type`를 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="max_size"></a>  multimap::max_size

multimap의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

multimap의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimap"></a>  multimap::multimap

비어 있거나 다른 multimap의 전체 또는 일부분에 대한 복사본인 multimap을 생성합니다.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|`Al`|이 multimap 개체에 사용할 저장소 할당자 클래스로, 기본값은 Allocator입니다.|
|`Comp`|multimap의 요소 순서를 지정하는 데 사용되는 **constTraits** 형식의 비교 함수로, 기본값은 **Traits**입니다.|
|`Right`|생성된 set가 복사본으로 지정될 map입니다.|
|`First`|복사할 요소의 범위에서 첫 번째 요소의 위치입니다.|
|`Last`|복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.|
|`IList`|요소를 복사해올 initializer_list입니다.|

### <a name="remarks"></a>설명

모든 생성자는 multimap의 메모리 저장소를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체 형식을 저장합니다. 할당자 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 multimap을 초기화합니다.

모든 생성자는 multimap의 키 간 순서를 설정하는 데 사용되며 나중에 [key_comp](#key_comp)를 호출하여 반환할 수 있는 `Traits` 형식의 함수 개체를 저장합니다.

처음 3개 생성자 중 첫 번째 생성자는 빈 초기 multimap을 정의하고, 두 번째 생성자는 요소의 순서를 설정하는 데 사용할 비교 함수( `Comp`)의 형식을 지정하며, 세 번째 생성자는 사용할 할당자 형식( `Al`)을 명시적으로 지정합니다. `explicit` 키워드를 사용하는 경우 특정 종류의 자동 형식 변환이 수행되지 않습니다.

네 번째 생성자는 `Right` multimap의 복사본을 지정합니다.

다섯 번째 생성자는 `Right`를 이동하여 multimap의 복사본을 지정합니다.

여섯 번째, 일곱 번째 및 여덟 번째 생성자는 initializer_list의 구성원를 복사합니다.

다음 3개 생성자는 map의 범위 `[First, Last)`를 복사하며, 범위 내에서 클래스 **Traits** 및 allocator의 비교 함수 형식을 지정하는 명시도는 계속 높아집니다.

### <a name="example"></a>예제

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of geater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}

```

## <a name="op_eq"></a>  multimap::operator=

multimap의 요소를 다른 multimap의 복사본으로 대체합니다.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|`right`|`multimap`에 복사되는 [multimap](../standard-library/multimap-class.md)입니다.|

### <a name="remarks"></a>설명

`multimap`는 `operator=`에서 기존 요소를 지운 후에 `right`의 내용을 `multimap`로 복사하거나 이동합니다.

### <a name="example"></a>예제

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  multimap::pointer

multimap에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>설명

형식 **pointer**는 요소값을 수정할 때 사용할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 multimap 개체의 요소에 액세스해야 합니다.

## <a name="rbegin"></a>  multimap::rbegin

역방향 multimap에서 첫 번째 요소를 주소 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 multimap에서 첫 번째 요소 또는 정방향 multimap에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 multiset에서 [begin](#begin)이 사용되는 것처럼 역방향 multiset에 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당된 경우 multimap 개체는 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당된 경우에는 multimap 개체를 수정할 수 있습니다.

`rbegin`은 multmap을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="reference"></a>  multimap::reference

multimap에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>예제

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  multimap::rend

역방향 multimap에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 multimap에서 마지막 요소 다음의 위치(정방향 multimap의 첫 번째 요소 앞의 위치) 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 multimap에서 [end](../standard-library/map-class.md#end)가 사용되는 것처럼 역방향 multimap에 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당된 경우 multimap 개체는 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당된 경우에는 multimap 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 multimap 끝에 도달했는지를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="reverse_iterator"></a>  multimap::reverse_iterator

역방향 multimap의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 multimap을 역방향으로 반복하는 데 사용됩니다.

`reverse_iterator` 의 개체에 multimap 점으로 정의 [value_type](#value_type), 유형을 `pair` * \< * **const 키**, **형식 * * * >* 합니다. 키의 값은 첫 번째 구성원 쌍을 통해 제공되며 매핑된 요소값은 쌍의 두 번째 구성원를 통해 제공됩니다.

역참조에 `reverse_iterator` `rIter` 사용 하는 multimap의 요소를 가리키는-> 연산자입니다.

요소에 대한 키의 값에 액세스하려면 `rIter` -> **first**를 사용합니다. 이 항목은 (\* `rIter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `rIter` -> **second**를 사용합니다. 이 항목은 (\* `rIter`). **first**와 같습니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="size"></a>  multimap::size

multimap에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

multimap의 현재 길이입니다.

### <a name="example"></a>예제

다음 예제에서는 multimap::size 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="size_type"></a>  multimap::size_type

multimap에서 요소 수를 계산하는 부호 없는 정수 형식입니다.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)의 예제를 참조하세요.

## <a name="swap"></a>  multimap::swap

두 multimap의 요소를 교환합니다.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

`right` 요소를 제공 하는 multimap 또는 multimap의와 교환할 요소가 multimap `left`합니다.

### <a name="remarks"></a>설명

구성원 함수는 해당 요소를 교환할 두 multimap의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="upper_bound"></a>  multimap::upper_bound

multimap에서 지정된 키보다 큰 키를 가진 첫 번째 요소에 반복기를 반환합니다.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 multimap에서 요소의 정렬 키와 비교할 인수 키입니다.

### <a name="return-value"></a>반환 값

인수 키보다 큰 키가 들어 있는 multimap 내 요소의 위치 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 multimap에서 마지막 요소 다음 위치의 주소를 지정하는 반복기 또는 `const_iterator`입니다.

반환 값이 `const_iterator`에 할당된 경우 multimap 개체는 수정할 수 없습니다. 반환 값이 **iterator**에 할당되는 경우에는 multimap 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a derefenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  multimap::value_comp

구성원 함수는 키 값을 비교하여 multimap의 요소 순서를 결정하는 함수 개체를 반환합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

multimap이 요소의 순서를 지정하는 데 사용하는 비교 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

multimap *m*의 두 요소 *e*1( *k*1, *d*1) 및 *e*2( *k*2, `d`2)가 `value_type` 형식의 개체이고, *k*1 및 *k*2는 `key_type` 형식의 키이며 `d`1 및 `d`2는 `mapped_type` 형식의 데이터이면 *m.*`value_comp`( *e*1, *e*2)는 *m.*`key_comp`( *k*1, *k*2)와 동일합니다.

### <a name="example"></a>예제

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

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

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  multimap::value_type

map에 있는 요소로 저장된 개체의 형식을 나타내는 형식입니다.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>예제

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitely to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>참고자료

[\<지도 > 멤버](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[컨테이너](../cpp/containers-modern-cpp.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
