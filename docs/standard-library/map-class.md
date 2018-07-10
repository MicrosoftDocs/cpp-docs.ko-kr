---
title: map 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ff022d6bf28904328ace7cab543fe72b60236b7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863428"
---
# <a name="map-class"></a>map 클래스

각 요소가 데이터 값과 정렬 키를 갖고 있는 쌍인 컬렉션에서 데이터의 저장과 검색에 사용됩니다. 키 값은 고유하며 데이터를 자동으로 정렬하는 데 사용됩니다.

map에 있는 요소의 값은 직접 변경할 수 있습니다. 키 값은 상수이며 변경할 수 없습니다. 대신, 이전 요소와 관련된 키 값은 삭제되어야 하며 새 요소에 대한 새 키 값이 삽입되어야 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>매개 변수

`Key` 지도에 저장할 키 데이터 형식입니다.

`Type` Map에 저장 하는 요소 데이터 형식

`Traits` 지도에서 상대적 순서를 결정 하는 정렬 키로 두 요소 값을 비교할 수 있는 함수 개체를 제공 하는 형식입니다. 이 인수는 선택 사항이며 기본값은 이진 조건자 `less<Key>`입니다.

C++14에서는 형식 매개 변수가 없는 std::less<> 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers)를 참조하세요

`Allocator` Map의 할당 및 메모리 할당 취소에 대 한 세부 정보를 캡슐화 하는 저장 된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<pair<const Key, Type> >`입니다.

## <a name="remarks"></a>설명

C++ 표준 라이브러리 map 클래스의 특징은 다음과 같습니다.

- 연결된 키 값을 기반으로 요소 값을 효율적으로 검색하는 다양한 크기의 컨테이너

- 이는 해당 요소에 액세스할 수 있는 양방향 반복기를 제공하기 때문에 되돌릴 수 있습니다.

- 요소가 지정된 비교 함수에 따른 키 값으로 정렬되므로 정렬되어 있습니다.

- 고유합니다. 각 요소에 고유 키가 있어야 하기 때문입니다.

- 요소의 데이터 값은 키 값과 구별되기 때문에 쌍 연관 컨테이너입니다.

- 제공하는 기능은 제네릭이며 요소나 키 형식과 독립적이므로 템플릿 클래스입니다. 요소와 키에 사용되는 데이터 형식은 비교 함수 및 할당자와 함께 클래스 템플릿에서 매개 변수로 지정됩니다.

map 클래스에서 제공하는 반복기는 양방향 반복기이지만, [insert](#insert) 및 [map](#map) 클래스 멤버 함수의 버전은 기능 요구 사항이 양방향 반복기 클래스에서 보장하는 것보다 약한 입력 반복기를 템플릿 매개 변수로 사용합니다. 다른 반복기 개념은 상세 기능별로 관련되어 있습니다. 각 반복기 개념에는 고유한 요구 사항 및 그 요구 사항에 의해 제한된 작업을 수행하는 알고리즘이 있습니다. 입력 반복기를 역참조하여 몇 가지 개체를 참조하고 시퀀스의 다음 반복기로 증가될 수 있습니다.

컨테이너 형식을 선택할 때에는 응용 프로그램에서 요구하는 검색 및 삽입의 종류를 기준으로 하는 것이 좋습니다. 연관 컨테이너는 조회, 삽입 및 제거 작업에 최적화되어 있습니다. 명시적으로 이러한 작업을 지원하는 멤버 함수의 수행 시간은 최악의 경우 컨테이너의 요소 개수를 진수로 하는 로그값에 비례합니다. 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 명확히 가리키고 있는 반복기만 무효화됩니다.

값을 키와 연결하는 조건을 응용 프로그램이 충족할 경우 map을 연관 컨테이너로 선택하는 것이 좋습니다. 이러한 형식의 구조체를 위한 모델은 정의를 제공하는 연관 문자열 값이 있고 고유하게 나타나는 키 단어의 정렬된 목록입니다. 하나의 단어에 둘 이상의 올바른 정의가 있는 경우, 즉, 키가 고유하지 않은 경우 multimap은 선택의 컨테이너가 됩니다. 단어의 목록만 저장하려는 경우 set이 적절한 컨테이너일 수 있습니다. 단어가 여러 번 중복 발생하는 것을 허용한 경우 multiset이 적절할 수 있습니다.

map은 [key_compare](#key_compare) 형식의 저장된 함수 개체를 호출하여 제어하는 요소를 정렬합니다. 이 저장된 개체는 [key_comp](#key_comp) 메서드를 호출하여 액세스하는 비교 함수입니다. 일반적으로, 주어진 두 개의 요소는 하나의 요소가 다른 요소보다 작은지 또는 둘이 동등한지를 결정하기 위해 비교합니다. 모든 요소가 비교되면 동등하지 않은 요소의 정렬된 시퀀스가 생성됩니다.

> [!NOTE]
> 비교 함수는 표준 수학적 의미에서 엄밀히 약한 정렬을 발생시키는 이진 조건자입니다. 이진 조건자 f(x,y)는 두 인수 개체 x, y 및 반환값 `true` 또는 `false`가 있는 함수 개체입니다. 이진 조건자가 비재귀적, 비대칭 및 전이적인 경우 및 동등성이 전이적인 경우 set에 적용된 정렬은 엄밀히 약한 정렬입니다. 여기서, f(x,y) 및 f(y,x)가 모두 `false`인 경우 x 및 y 두 개체는 동등한 것으로 정의됩니다. 키 사이의 더 강력한 같음 조건이 동등 조건을 대체하는 경우, 정렬은 전체가 되고(모든 요소가 서로 상대적으로 정렬됨을 의미) 일치된 키는 서로 구분할 수 없게 됩니다.
>
> C++14에서는 형식 매개 변수가 없는 `std::less<>` 또는 `std::greater<>` 조건자를 지정하여 유형이 다른 조회를 사용하도록 설정할 수 있습니다. 자세한 내용은 [연관 컨테이너의 유형이 다른 조회](../standard-library/stl-containers.md#sequence_containers)를 참조하세요.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[map](#map)|특정 크기의 목록 또는 특정 값의 요소 또는 특정 `allocator`가 포함된 목록 또는 다른 map의 복사본으로 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|map 개체를 위한 `allocator` 클래스의 typedef|
|[const_iterator](#const_iterator)|map에서 `const` 요소를 읽을 수 있는 양방향 반복기에 대한 typedef|
|[const_pointer](#const_pointer)|map의 `const` 요소를 가리키는 포인터에 대한 typedef|
|[const_reference](#const_reference)|`const` 작업을 읽고 수행하기 위해 map에 저장된 `const` 요소를 참조하기 위한 typedef|
|[const_reverse_iterator](#const_reverse_iterator)|map에 있는 모든 `const` 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식|
|[difference_type](#difference_type)|반복기가 가리키는 요소 사이의 범위에 있는 map의 요소 개수에 대한 부호 있는 정수 typedef|
|[iterator](#iterator)|map의 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 위한 typedef|
|[key_compare](#key_compare)|map의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 위한 typedef|
|[key_type](#key_type)|각 map 요소에 저장된 정렬 키에 대한 typedef|
|[mapped_type](#mapped_type)|각 map 요소에 저장된 데이터에 대한 typedef|
|[pointer](#pointer)|map의 `const` 요소를 가리키는 포인터에 대한 typedef|
|[reference](#reference)|map에 저장된 요소에 대한 참조의 typedef|
|[reverse_iterator](#reverse_iterator)|역순 map의 요소를 읽거나 수정할 수 있는 양방향 반복기를 위한 typedef|
|[size_type](#size_type)|map의 요소 수에 대한 부호 없는 정수의 typedef|
|[value_type](#value_type)|map의 요소로 저장된 개체의 형식에 대한 typedef|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[at](#at)|지정된 키 값이 있는 요소를 찾습니다.|
|[begin](#begin)|map의 첫 번째 요소를 가리키는 반복기를 반환합니다.|
|[cbegin](#cbegin)|map의 첫 번째 요소를 가리키는 상수 반복기를 반환합니다.|
|[cend](#cend)|마지막 요소 바로 다음의 상수 반복기를 반환합니다.|
|[clear](#clear)|map의 모든 요소를 지웁니다.|
|[count](#count)|키가 매개 변수에서 지정한 키와 일치하는 map의 요소 수를 반환합니다.|
|[crbegin](#crbegin)|역순 map에서 첫 번째 요소를 가리키는 상수 반복기를 반환합니다.|
|[crend](#crend)|역순 map의 마지막 요소 바로 다음 위치를 가리키는 상수 반복기를 반환합니다.|
|[emplace](#emplace)|map에 생성된 요소를 삽입합니다.|
|[emplace_hint](#emplace_hint)|배치 힌트를 사용하여 map에 생성된 요소를 삽입합니다.|
|[empty](#empty)|map이 비어 있으면 `true`를 반환합니다.|
|[end](#end)|마지막 바로 다음 반복기를 반환합니다.|
|[equal_range](#equal_range)|반복기 쌍을 반환합니다. `map`에서 지정된 키보다 큰 키가 있는 첫 번째 요소를 가리키는 쌍의 첫 번째 반복기 `map`에서 키보다 크거나 같은 키가 있는 첫 번째 요소를 가리키는 쌍의 두 번째 반복기|
|[erase](#erase)|지정된 위치의 map에서 요소 또는 요소 범위를 제거합니다.|
|[find](#find)|map에서 지정된 키와 같은 키를 가진 요소의 위치를 가리키는 반복기를 반환합니다.|
|[get_allocator](#get_allocator)|map을 생성하는 데 사용되는 `allocator` 개체의 복사본을 반환합니다.|
|[insert](#insert)|요소 또는 요소의 범위를 map의 지정된 위치에 삽입합니다.|
|[key_comp](#key_comp)|map에서 순서 키로 사용되는 비교 개체의 복사본을 반환합니다.|
|[lower_bound](#lower_bound)|map에서 지정된 키보다 같거나 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[max_size](#max_size)|map의 최대 길이를 반환합니다.|
|[rbegin](#rbegin)|역순 map에서 첫 번째 요소를 가리키는 반복기를 반환합니다.|
|[rend](#rend)|역순 map에서 마지막 요소 바로 다음 위치를 가리키는 반복기를 반환합니다.|
|[size](#size)|map에 있는 요소 수를 반환합니다.|
|[swap](#swap)|두 map의 요소를 교환합니다.|
|[upper_bound](#upper_bound)|map에서 지정된 키보다 큰 키 값을 가진 첫 번째 요소에 반복기를 반환합니다.|
|[value_comp](#value_comp)|map에서 요소 값의 정렬에 사용되는 비교 개체의 복사본을 검색합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator&#91;&#93;](#op_at)|지정된 키 값을 사용하여 map에 요소를 삽입합니다.|
|[operator=](#op_eq)|map의 요소를 다른 map의 복사본으로 대체합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<map>

**네임스페이스:** std

## <a name="allocator_type"></a>  map::allocator_type

map 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>예제

`allocator_type`을 사용하는 예제는 [get_allocator](#get_allocator)의 예제를 참조하세요.

## <a name="at"></a>  map::at

지정된 키 값이 있는 요소를 찾습니다.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|매개 변수|설명|
|`key`|찾을 키 값입니다.|

### <a name="return-value"></a>반환 값

찾은 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값을 찾을 수 없는 경우 이 함수는 [out_of_range 클래스](../standard-library/out-of-range-class.md) 클래스의 개체를 throw합니다.

### <a name="example"></a>예제

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a>  map::begin

map에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>반환 값

map의 첫 번째 요소 또는 빈 map 다음 위치의 주소를 지정하는 양방향 반복기입니다.

### <a name="example"></a>예제

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a>  map::cbegin

범위에서 마지막 요소 바로 다음의 위치를 주소 지정하는 `const` 반복기를 반환합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 주소 지정하는 `const` 양방향 반복기입니다(빈 범위의 경우 `cbegin() == cend()`).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container`가 `begin()` 및 `cbegin()`를 지원하는 수정 가능(비`const`)한 컨테이너로 가정합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  map::cend

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

## <a name="clear"></a>  map::clear

map의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="example"></a>예제

다음 예제에서는 map::clear 멤버 함수의 사용을 보여 줍니다.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>  map::const_iterator

map의 **const** 요소 하나를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

map에 의해 정의된 `const_iterator`는 `pair`\< **constKey**, **Type**> 형식의 [value_type](#value_type) 개체인 요소를 가리킵니다. 여기서 첫 번째 멤버는 요소에 대한 키이고 두 번째 멤버는 요소에 포함된 매핑된 데이텀입니다.

역참조에 `const_iterator` `cIter` 사용 하 여 map에서 요소를 가리키는 **->** 연산자입니다.

요소에 대한 키의 값에 액세스하려면 `cIter` -> **first**를 사용합니다. 이 항목은 (\* `cIter`). **first**와 같습니다.

요소에 대한 매핑된 데이터의 값에 액세스하려면 `cIter` -> **second**를 사용합니다. 이 항목은 (\* `cIter`). **second**와 같습니다.

### <a name="example"></a>예제

`const_iterator`를 사용하는 예제는 [begin](#begin)에 대한 예제를 참조하세요.

## <a name="const_pointer"></a>  map::const_pointer

map의 **const** 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

`const_pointer` 형식을 사용하여 요소의 값을 수정할 수는 없습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 map 개체의 요소에 액세스해야 합니다.

## <a name="const_reference"></a>  map::const_reference

**const** 작업을 읽고 수행하기 위해 map에 저장된 **const** 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>예제

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>  map::const_reverse_iterator

map의 모든 **const** 요소를 읽을 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>설명

`const_reverse_iterator` 형식은 요소 값을 수정할 수 없으며 map을 역방향으로 반복하는 데 사용됩니다.

`const_reverse_iterator` 지도 점의 개체는 요소에 의해 정의 된 [value_type](#value_type), 즉 형식의 `pair<const Key, Type>`의 첫 번째 멤버 키 요소이 고 멤버 요소가 매핑된 데이터는 두 번째입니다.

map의 요소를 가리키는 `const_reverse_iterator crIter`을 역참조하려면 **->** 연산자를 사용합니다.

요소에 대 한 키의 값에 액세스 하려면 사용 하 여 `crIter`  ->  **첫 번째**, 같습니다. (\* `crIter`). **첫 번째**합니다.

요소에 대해 매핑된 데이터의 값에 액세스 하려면 사용 하 여 `crIter`  ->  **두 번째**, 같습니다. (\* `crIter`). **첫 번째**합니다.

### <a name="example"></a>예제

`const_reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rend](#rend)에 대한 예제를 참조하세요.

## <a name="count"></a>  map::count

키가 매개 변수로 지정된 키와 일치하는 map의 요소 수를 반환합니다.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 지도에서 일치 시킬 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

map에 정렬 키가 매개 변수 키와 일치하는 요소가 있는 경우 1이고, map에 일치하는 키가 포함된 요소가 없는 경우 0입니다.

### <a name="remarks"></a>설명

멤버 함수는 다음 범위에 있는 *x* 요소의 수를 반환합니다.

[ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )

고유한 결합형 컨테이너인 map의 경우 0 또는 1입니다.

### <a name="example"></a>예제

다음 예제에서는 map::count 멤버 함수의 사용을 보여 줍니다.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
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
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  map::crbegin

역방향 map에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

역방향 [map](../standard-library/map-class.md)에서 첫 번째 요소 또는 역방향이 해제된 `map`에서 마지막 요소의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crbegin`은 `map`에서 [begin](#begin)이 사용되는 것처럼 역방향 `map`에서 사용됩니다.

반환 값이 `crbegin`이면 `map` 개체를 수정할 수 없습니다.

`crbegin`은 `map`을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>  map::crend

역방향 map에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 const 반복기를 반환합니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

역방향 [map](../standard-library/map-class.md)에서 마지막 요소 다음 위치(역방향이 해제된 `map`의 첫 번째 요소 앞 위치)의 주소를 지정하는 const 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`crend`는 `map`에서 [end](#end)가 사용되는 것처럼 역방향 map에서 사용됩니다.

반환 값이 `crend`이면 `map` 개체를 수정할 수 없습니다.

`crend`를 사용하여 역방향 반복기가 `map` 끝에 도달했는지 여부를 테스트할 수 있습니다.

`crend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>  map::difference_type

반복기가 가리키는 요소 사이의 범위에 있는 map의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 컨테이너의 반복기를 빼거나 더할 때 반환되는 형식입니다. `difference_type`은 일반적으로 `first` 및 `last` 반복기 사이의 *[ first,  last)* 범위 내 요소 수를 나타내는 데 사용됩니다. 여기에는 `first`가 가리키는 요소에서 `last`가 가리키는 요소까지의 요소 범위가 포함됩니다(마지막 요소는 포함되지 않음).

입력 반복기 요구 사항을 충족하는 모든 반복기(set 등의 가역 컨테이너에서 지원하는 양방향 반복기 클래스 포함)에 대해 `difference_type`을 사용할 수는 있지만, 반복기 간의 빼기는 vector와 같은 임의 액세스 컨테이너가 제공하는 임의 액세스 반복기를 통해서만 지원됩니다.

### <a name="example"></a>예제

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>  map::emplace

생성된 요소를 map에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|매개 변수|설명|
|`args`|값이 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 map에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.|

### <a name="return-value"></a>반환 값

해당 `bool` 구성 요소가 삽입이 수행된 경우에는 true이고 map이 값이 동일한 요소를 순서에 이미 포함한 경우에는 false인 [pair](../standard-library/pair-structure.md)입니다. 반환 값 쌍의 반복기 구성 요소는 `bool` 구성 요소가 true인 경우에는 새로 삽입된 요소를 가리키고 `bool` 구성 요소가 false인 경우에는 기존 요소를 가리킵니다.

반복기 구성 요소를 액세스 하는 `pair` `pr`를 사용 하 여 `pr.first`역참조를 사용 하려면 `*pr.first`합니다. `bool` 구성 요소에 액세스하려면 `pr.second`를 사용합니다. 예제는 이 문서 뒷부분에 있는 샘플 코드를 참조하세요.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

대입 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다.

요소의 [value_type](#value_type)은 쌍이므로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

### <a name="example"></a>예제

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

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
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}

```

## <a name="emplace_hint"></a>  map::emplace_hint

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
|매개 변수|설명|
|`args`|map이 해당 요소를 이미 포함하고 있지 않거나, 보다 일반적으로는 키가 동등하게 정렬된 요소를 이미 포함하고 있지 않을 경우 map에 삽입할 요소를 생성하기 위해 전달되는 인수입니다.|
|`where`|올바른 삽입 지점 검색을 시작할 위치입니다. 이 지점이 `where` 바로 앞에 오면 로그 시간 대신 분할된 시간에 삽입할 수 있습니다.|

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

요소가 이미 있어서 삽입이 실패하면 해당 키와 함께 기존 요소에 대한 반복기가 반환됩니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

대입 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다.

요소의 [value_type](#value_type)은 쌍이므로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

### <a name="example"></a>예제

```cpp
// map_emplace.cpp
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
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="empty"></a>  map::empty

map이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

map이 비어 있으면 **true**이고, 비어 있지 않으면 **false**입니다.

### <a name="example"></a>예제

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>  map::end

마지막 바로 다음 반복기를 반환합니다.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>반환 값

마지막 바로 다음 반복기입니다. 맵이 비어 있으면 `map::end() == map::begin()`입니다.

### <a name="remarks"></a>설명

**end**는 반복기가 map의 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

**end**에서 반환한 값은 역참조해서는 안 됩니다.

코드 예제는 [map::find](#find)를 참조하세요.

## <a name="equal_range"></a>  map::equal_range

키의 [lower_bound](#lower_bound)와 [upper_bound](#upper_bound)를 나타내는 반복기 쌍을 반환합니다.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 맵에서 요소의 정렬 키와 비교할 인수 키 값입니다.

### <a name="return-value"></a>반환 값

구성원 함수가 반환하는 `pr` 쌍의 첫 번째 반복기에 액세스하려면 `pr`. **first**를 사용하고 하한 반복기를 역참조하려면 \*( `pr`. **first**)를 사용합니다. 구성원 함수가 반환하는 `pr` 쌍의 두 번째 반복기에 액세스하려면 `pr`. **second**를 사용하고 상한 반복기를 역참조하려면 \*( `pr`. **second**)를 사용합니다.

### <a name="example"></a>예제

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
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
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  map::erase

지정된 위치에서 map의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

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

`Key` 제거할 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

처음 두 멤버 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 map의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 멤버 함수의 경우 map에서 제거된 요소의 수를 반환합니다.

### <a name="example"></a>예제

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an intializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}

```

## <a name="find"></a>  map::find

지정된 키와 같은 키를 포함하는 맵 내 요소의 위치를 가리키는 반복기를 반환합니다.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 맵에서 요소의 정렬 키와 일치 하려면 키 값입니다.

### <a name="return-value"></a>반환 값

지정된 키를 포함하는 요소의 위치 또는 해당 키와 일치하는 항목이 없는 경우 map의 마지막 요소(`map::end()`) 다음 위치를 가리키는 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 보다 작음 비교 가능 관계를 기반으로 하는 순서를 적용하는 이진 조건자에서 정렬 키가 인수 키와 같은 맵 내 요소를 가리키는 반복기를 반환합니다.

**find**의 반환 값이 **const_iterator**에 할당되는 경우에는 map 개체를 수정할 수 없습니다. **find**의 반환 값이 **iterator**에 할당되는 경우에는 map 개체를 수정할 수 있습니다.

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
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
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

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  map::get_allocator

map를 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

map에서 사용되는 할당자입니다.

### <a name="remarks"></a>설명

map 클래스의 할당자는 클래스가 저장소를 관리하는 방법을 지정합니다. C++ 표준 라이브러리 컨테이너 클래스와 함께 제공되는 기본 할당자를 사용하면 대부분의 프로그래밍 요구 사항을 충족할 수 있습니다. 할당자 클래스를 직접 작성하고 사용하는 방법에 대해서는 고급 C++ 항목에서 다룹니다.

### <a name="example"></a>예제

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>  map::insert

map에 요소 또는 요소의 범위를 삽입합니다.

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
|매개 변수|설명|
|`Val`|키가 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 map에 삽입되는 요소의 값입니다.|
|`Where`|올바른 삽입 지점 검색을 시작할 위치입니다. 이 지점이 `Where` 바로 앞에 오면 로그 시간 대신 분할된 시간에 삽입할 수 있습니다.|
|`ValTy`|map이 [value_type](#value_type)의 요소를 생성하는 데 사용할 수 있는 인수 형식을 지정하고 `Val`을 인수로 완벽하게 전달하는 템플릿 매개 변수입니다.|
|`First`|복사할 첫 번째 요소의 위치입니다.|
|`Last`|복사할 마지막 요소 바로 다음 위치입니다.|
|`InputIterator`|[value_type](#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.|
|`IList`|요소를 복사할 원본 [initializer_list](../standard-library/initializer-list.md)입니다.|

### <a name="return-value"></a>반환 값

단일 요소 멤버 함수 (1) 및 (2)는 `bool` 구성 요소가 삽입이 수행된 경우에는 true이고 map이 키의 값이 동일한 요소를 이미 순서에 포함한 경우에는 false인 [pair](../standard-library/pair-structure.md)를 반환합니다. 반환 값 쌍의 반복기 구성 요소는 `bool` 구성 요소가 true인 경우에는 새로 삽입된 요소를 가리키고 `bool` 구성 요소가 false인 경우에는 기존 요소를 가리킵니다.

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 새 요소가 map에 삽입된 위치를 가리키는 반복기를 반환하고 동일한 키가 있는 요소가 존재하는 경우에는 기존 요소를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 반복기, 포인터 또는 참조를 무효화하지 않습니다.

요소를 한 개만 삽입하는 중 예외가 throw되면 컨테이너의 상태가 수정되지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

단일 요소 멤버 함수에서 반환한 `pair` `pr`의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 반환된 쌍 내에서 반복기를 역참조하려면 `*pr.first`를 사용하여 요소를 제공합니다. `bool` 구성 요소에 액세스하려면 `pr.second`를 사용합니다. 예제는 이 문서 뒷부분에 있는 샘플 코드를 참조하세요.

컨테이너의 [value_type](#value_type)은 컨테이너에 속한 형식 정의이고 map의 경우 `map<K, V>::value_type`은 `pair<const K, V>`입니다. 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소는 요소의 데이터 값과 동일한 정렬된 쌍입니다.

범위 멤버 함수 (5)는 `[First, Last)` 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 map에 요소 값의 시퀀스를 입력하므로 `Last`는 삽입되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `m.insert(v.begin(), v.end());` 문이 `v`의 모든 요소를 `m`에 삽입하려고 합니다. 범위에 고유 값이 있는 요소만 삽입됩니다. 중복 값은 무시됩니다. 어떤 요소가 거부되는지 관찰하려면 `insert`의 단일 요소 버전을 사용합니다.

이니셜라이저 목록 멤버 함수 (6)은 [initializer_list](../standard-library/initializer-list.md)를 사용하여 요소를 map으로 복사합니다.

생성된 요소를 삽입하고 복사 또는 이동 작업은 수행하지 않으려면 [map::emplace](#emplace) 및 [map::emplace_hint](#emplace_hint)를 참조하세요.

### <a name="example"></a>예제

```cpp
// map_insert.cpp
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
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
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
    map<int, string>  m3;
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

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  map::iterator

map에 있는 모든 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

**반복기** 지도 점의 개체는 요소에 의해 정의 된 [value_type](#value_type), 즉 형식의 `pair` * \< * **constKey** , **형식 * * * >* 의 첫 번째 멤버 키 요소이 고 멤버 요소가 매핑된 데이터는 두 번째입니다.

map의 요소를 가리키는 **iterator**`Iter`를 역참조하려면 **->** 연산자를 사용합니다.

요소에 대한 키의 값에 액세스하려면 `Iter` -> **first**를 사용합니다. 이 항목은 (\* `Iter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `Iter` -> **second**를 사용합니다. 이 항목은 (\* `Iter`). **second**와 같습니다.

### <a name="example"></a>예제

**iterator**를 선언하고 사용하는 방법에 대한 예제는 [begin](#begin)에 대한 예제를 참조하세요.

## <a name="key_comp"></a>  map::key_comp

map에서 키를 정렬하기 위해 사용하는 비교 개체의 복사본을 검색합니다.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>반환 값

map이 요소의 순서를 지정하는 데 사용하는 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

저장된 개체는 멤버 함수

**bool operator**( **constKey&**`left`, **const Key&**`right`);를

정의합니다. 이 함수는 `left`이 앞에 오며 정렬 순서가 `right`과 같지 않으면 **true**를 반환합니다.

### <a name="example"></a>예제

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
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

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
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

## <a name="key_compare"></a>  map::key_compare

map의 두 요소간 상대적 순서를 결정하는 두 정렬 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>설명

`key_compare`은 템플릿 매개 변수 `Traits`의 동의어입니다.

`Traits`에 대한 자세한 내용은 [map 클래스](../standard-library/map-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`key_compare`를 선언하고 사용하는 방법에 대한 예제는 [key_comp](#key_comp)의 예제를 참조하세요.

## <a name="key_type"></a>  map::key_type

각 map 요소에 저장된 정렬 키에 대해 설명하는 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

`key_type`은 템플릿 매개 변수 `Key`의 동의어입니다.

`Key`에 대한 자세한 내용은 [map 클래스](../standard-library/map-class.md) 항목의 설명 섹션을 참조하세요.

### <a name="example"></a>예제

`key_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="lower_bound"></a>  map::lower_bound

map에서 지정된 키보다 크거나 같은 키 값을 가진 첫 번째 요소에 대한 반복기를 반환합니다.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 맵에서 요소의 정렬 키와 비교할 인수 키 값입니다.

### <a name="return-value"></a>반환 값

인수 키보다 크거나 같은 키가 들어 있는 map 내 요소 위치의 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 map에서 마지막 요소 다음 위치의 주소를 지정하는 **iterator** 또는 `const_iterator`입니다.

`lower_bound`의 반환 값이 `const_iterator`에 할당되는 경우에는 map 개체를 수정할 수 없습니다. `lower_bound`의 반환 값이 **iterator**에 할당되는 경우에는 map 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>  map::map

비어 있거나 다른 map의 전체 또는 일부에 대한 복사본인 map을 생성합니다.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|매개 변수|설명|
|`Al`|이 map 개체에 사용할 저장소 할당자 클래스로, 기본값은 `Allocator`입니다.|
|`Comp`|map의 요소 순서를 지정하는 데 사용되는 `const Traits` 형식의 비교 함수로, 기본값은 `hash_compare`입니다.|
|`Right`|생성된 set을 복사할 map입니다.|
|`First`|복사할 요소의 범위에서 첫 번째 요소의 위치입니다.|
|`Last`|복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.|
|`IList`|요소를 복사할 원본 initializer_list입니다.|

### <a name="remarks"></a>설명

모든 생성자는 map의 메모리 저장소를 관리하며 나중에 [get_allocator](#get_allocator)를 호출하여 반환할 수 있는 할당자 개체의 형식을 저장합니다. 할당자 매개 변수는 대체 할당자를 대체하는 데 사용되는 전처리 매크로 및 클래스 선언에서 생략되는 경우가 많습니다.

모든 생성자는 해당 map를 초기화합니다.

모든 생성자는 map의 키 간 순서를 설정하는 데 사용되며 나중에 [key_comp](#key_comp)를 호출하여 반환할 수 있는 Traits 형식의 함수 개체를 저장합니다.

처음 세 생성자는 빈 초기 map을 정의하고, 두 번째 생성자는 요소의 순서를 설정하는 데 사용할 비교 함수(`Comp`)의 형식을 지정하며, 세 번째 생성자는 사용할 할당자 형식(`Al`)을 명시적으로 지정합니다. `explicit` 키워드를 사용하는 경우 특정 종류의 자동 형식 변환이 수행되지 않습니다.

네 번째 생성자는 `Right` map의 복사본을 지정합니다.

다섯 번째 생성자는 `Right`를 이동하여 map의 복사본을 지정합니다.

여섯 번째, 일곱 번째 및 여덟 번째 생성자는 멤버를 복사할 원본 initializer_list를 사용합니다.

다음 세 생성자는 map의 범위 `[First, Last)`를 복사하여, `Traits` 클래스 및 할당자의 비교 함수 형식을 지정할 때 명시도가 향상됩니다.

### <a name="example"></a>예제

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of geater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
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

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}

```

## <a name="mapped_type"></a>  map::mapped_type

map에 저장된 데이터를 나타내는 형식입니다.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>설명

`mapped_type` 형식은 클래스의 템플릿 매개 변수 `Type`의 동의어입니다.

`Type`에 대한 자세한 내용은 [map 클래스](../standard-library/map-class.md) 항목을 참조하세요.

### <a name="example"></a>예제

`mapped_type`을 선언하고 사용하는 방법에 대한 예제는 [value_type](#value_type)의 예제를 참조하세요.

## <a name="max_size"></a>  map::max_size

map의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

map의 최대 허용 길이입니다.

### <a name="example"></a>예제

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>  map::operator[]

지정된 키 값을 사용하여 map에 요소를 삽입합니다.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|매개 변수|설명|
|`key`|삽입할 요소의 키 값입니다.|

### <a name="return-value"></a>반환 값

삽입된 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값이 없으면 데이터 형식의 기본값과 함께 삽입됩니다.

`operator[]`는 `m[ key] = DataValue;`를 사용하여 맵 `m`에 요소를 삽입하는 데 사용할 수 있습니다. 여기서 `DataValue`는 키 값이 `key`인 요소의 `mapped_type` 값입니다.

`operator[]`를 사용하여 요소를 삽입하는 경우 반환된 참조는 삽입이 기존 요소를 변경하는지 또는 새 요소를 생성하는지 여부를 나타내지 않습니다. 구성원 함수 [find](#find) 및 [insert](#insert)는 지정된 키가 포함된 요소가 삽입 전에 이미 있는지를 확인하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>  map::operator=

map의 요소를 다른 map의 복사본으로 대체합니다.

```cpp
map& operator=(const map& right);

map& operator=(map&& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|-|-|
|매개 변수|설명|
|`right`|`map`에 복사되는 [map](../standard-library/map-class.md)입니다.|

### <a name="remarks"></a>설명

`map`에서 기존 요소를 지운 후 `operator=`는 `right`의 내용을 map으로 복사하거나 이동합니다.

### <a name="example"></a>예제

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

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

## <a name="pointer"></a>  map::pointer

map에서 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>설명

형식 **pointer**는 요소값을 수정할 때 사용할 수 있습니다.

대부분의 경우 [iterator](#iterator)를 사용하여 map 개체의 요소에 액세스해야 합니다.

## <a name="rbegin"></a>  map::rbegin

역방향 map에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>반환 값

역방향 map에서 첫 번째 요소 또는 역방향이 해제된 map에서 마지막 요소의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rbegin`은 [begin](#begin)이 map에서 사용되는 것처럼 역방향 map에서 사용됩니다.

`rbegin`의 반환 값이 `const_reverse_iterator`에 할당되는 경우에는 map 개체를 수정할 수 없습니다. `rbegin`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 map 개체를 수정할 수 있습니다.

`rbegin`은 map을 역방향으로 반복할 때 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>  map::reference

map에 저장된 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>예제

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  map::rend

역방향 map에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>반환 값

역방향 map에서 마지막 요소 다음 위치(역방향이 해제된 map의 첫 번째 요소 앞의 위치)의 주소를 지정하는 역방향 양방향 반복기입니다.

### <a name="remarks"></a>설명

`rend`는 map에서 [end](#end)가 사용되는 것처럼 역방향 map에서 사용됩니다.

`rend`의 반환 값이 `const_reverse_iterator`에 할당되는 경우에는 map 개체를 수정할 수 없습니다. `rend`의 반환 값이 `reverse_iterator`에 할당되는 경우에는 map 개체를 수정할 수 있습니다.

`rend`를 사용하여 역방향 반복기가 map의 끝에 도달했는지 여부를 테스트할 수 있습니다.

`rend`에서 반환한 값은 역참조되지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>  map::reverse_iterator

역방향 map의 요소를 읽거나 수정할 수 있는 양방향 반복기를 제공하는 형식입니다.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>설명

`reverse_iterator` 형식은 요소 값을 수정할 수 없으며 map을 역방향으로 반복하는 데 사용됩니다.

`reverse_iterator` 지도 점의 개체는 요소에 의해 정의 된 [value_type](#value_type), 즉 형식의 `pair` * \< * **constKey**, * *형식 * * * >* 의 첫 번째 멤버 키 요소이 고 멤버 요소가 매핑된 데이터는 두 번째입니다.

역참조에 `reverse_iterator` `rIter` 사용 하 여 map에서 요소를 가리키는 **->** 연산자입니다.

요소에 대한 키의 값에 액세스하려면 `rIter` -> **first**를 사용합니다. 이 항목은 (\* `rIter`). **first**와 같습니다. 요소에 대한 매핑된 데이터의 값에 액세스하려면 `rIter` -> **second**를 사용합니다. 이 항목은 (\* `rIter`). **first**와 같습니다.

### <a name="example"></a>예제

`reverse_iterator`를 선언하고 사용하는 방법에 대한 예제는 [rbegin](#rbegin)의 예제를 참조하세요.

## <a name="size"></a>  map::size

map에 있는 요소 수를 반환합니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

map의 현재 길이입니다.

### <a name="example"></a>예제

다음 예제에서는 map::size 멤버 함수를 사용하는 방법을 보여 줍니다.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>  map::size_type

map에서 요소 수를 나타낼 수 있는 부호 없는 정수 형식입니다.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>예제

`size_type`을 선언하고 사용하는 방법에 대한 예제는 [size](#size)에 대한 예제를 참조하세요.

## <a name="swap"></a>  map::swap

두 map의 요소를 교환합니다.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

`right` 요소를 대상 구조와 함께 제공 하는 인수 맵.

### <a name="remarks"></a>설명

멤버 함수는 해당 요소를 교환할 두 map의 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

### <a name="example"></a>예제

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>  map::upper_bound

map에서 지정된 키보다 큰 값을 가진 키가 포함된 첫 번째 요소에 대한 반복기를 반환합니다.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

`key` 검색 중인 맵에서 요소의 정렬 키 값과 비교 하기 위해 인수 키 값입니다.

### <a name="return-value"></a>반환 값

인수 키보다 큰 키가 들어 있는 map 내 요소 위치의 주소를 지정하거나, 키와 일치하는 항목이 없는 경우 map에서 마지막 요소 다음 위치의 주소를 지정하는 **iterator** 또는 `const_iterator`입니다.

반환 값이 `const_iterator`에 할당되는 경우에는 map 개체를 수정할 수 없습니다. 반환 값이 **iterator**에 할당되는 경우에는 map 개체를 수정할 수 있습니다.

### <a name="example"></a>예제

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  map::value_comp

멤버 함수는 키 값을 비교하여 map의 요소 순서를 결정하는 함수 개체를 반환합니다.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>반환 값

map이 요소의 순서를 지정하는 데 사용하는 비교 함수 개체를 반환합니다.

### <a name="remarks"></a>설명

map *m*의 경우 두 요소 *e*1( *k*1, *d*1) 및 *e*2( *k*2, `d`2)가 `value_type` 형식의 개체이면 *m.*`value_comp`( *e*1, *e*2)는 *m.*`key_comp`*(k*1, *k*2)와 동일합니다. 여기서 *k*1 및 *k*2는 `key_type` 형식의 키이고 `d`1 및`d`2는 `mapped_type` 형식의 데이터입니다. 저장된 개체는 멤버 함수

**bool operator**( **value_type&**`left`, **value_type&**`right`);를

정의합니다. 이 함수는 `left`의 키 값이 앞에 오고 정렬 순서의 `right` 키 값과 같지 않으면 **true**를 반환합니다.

### <a name="example"></a>예제

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

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

   if(vc1( *pr2.first, *pr1.first ) == true )
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

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  map::value_type

map의 요소로 저장된 개체의 형식입니다.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>예제

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
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

## <a name="see-also"></a>참고자료

[\<지도 > 멤버](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[컨테이너](../cpp/containers-modern-cpp.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
