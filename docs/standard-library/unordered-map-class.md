---
title: unordered_map 클래스
description: '`unordered_map`다양 한 길이의 요소 시퀀스를 제어 하는 c + + 표준 라이브러리 컨테이너 클래스에 대 한 API 참조입니다.'
ms.date: 9/9/2020
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::contains
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::contains
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
ms.openlocfilehash: 81428295f79d71227bf0fdf72e18f2fde30ac763
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564110"
---
# <a name="unordered_map-class"></a>unordered_map 클래스

클래스 템플릿은 형식의 다양 한 길이 요소 시퀀스를 제어 하는 개체를 설명 합니다 `std::pair<const Key, Ty>` . 시퀀스는 해시 함수로 약하게 정렬됩니다. 즉, 시퀀스를 버킷이라고 하는 하위 시퀀스의 정렬된 집합으로 분할합니다. 비교 함수는 각 버킷 내에서 요소 쌍이 동일하게 정렬되었는지 여부를 확인합니다. 각 요소는 두 개체, 정렬 키와 값을 저장합니다. 시퀀스는 최소한 모든 버킷이 대략 동일한 크기일 경우 시퀀스의 요소 수와 상관없이 작업 수를 사용하여 임의 요소를 조회, 삽입, 제거하는 방식으로 나타냅니다(일정 시간). 모든 요소가 하나의 버킷에 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간). 또한, 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 가리키고 있는 반복기만 무효화됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>매개 변수

*키인지*\
키 형식입니다.

*Ty*\
매핑된 형식입니다.

*해시로*\
해시 함수 개체 형식입니다.

*Pred*\
같음 비교 함수 개체 형식입니다.

*#C4*\
할당자 클래스입니다.

## <a name="members"></a>멤버

|형식 정의|설명|
|-|-|
|[allocator_type](#allocator_type)|스토리지 관리를 위한 할당자의 형식입니다.|
|[const_iterator](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[const_local_iterator](#const_local_iterator)|제어되는 시퀀스에 대한 상수 버킷 반복기의 형식입니다.|
|[const_pointer](#const_pointer)|요소에 대한 상수 포인터의 형식입니다.|
|[const_reference](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[difference_type](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[hasher](#hasher)|해시 함수의 형식입니다.|
|[iterator](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[key_equal](#key_equal)|비교 함수의 형식입니다.|
|[key_type](#key_type)|정렬 키의 형식입니다.|
|[local_iterator](#local_iterator)|제어되는 시퀀스에 대한 버킷 반복기의 형식입니다.|
|[mapped_type](#mapped_type)|각 키와 연결된 매핑된 값의 형식입니다.|
|[포인터(pointer)](#pointer)|요소에 대한 포인터의 형식입니다.|
|[reference](#reference)|요소에 대한 참조의 형식입니다.|
|[size_type](#size_type)|두 요소 사이의 부호가 없는 거리의 형식입니다.|
|[value_type](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|-|-|
|[at](#at)|지정된 키 값이 있는 요소를 찾습니다.|
|[시작](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[버킷](#bucket)|키 값에 대한 버킷 개수를 가져옵니다.|
|[bucket_count](#bucket_count)|버킷 개수를 가져옵니다.|
|[bucket_size](#bucket_size)|버킷의 크기를 가져옵니다.|
|[cbegin](#cbegin)|제어되는 시퀀스의 시작을 지정합니다.|
|[cend](#cend)|제어되는 시퀀스의 끝을 지정합니다.|
|[clear](#clear)|모든 요소를 제거합니다.|
|[count](#count)|지정한 키와 일치하는 요소의 수를 찾습니다.|
|[](#contains)<sup>c + + 20</sup> 포함|에 지정 된 키를 가진 요소가 있는지 여부를 확인 `unordered_map` 합니다.|
|[emplace](#emplace)|생성된 요소를 추가합니다.|
|[emplace_hint](#emplace_hint)|힌트와 함께 생성된 요소를 추가합니다.|
|[empty](#empty)|요소가 있는지 여부를 테스트합니다.|
|[end](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[equal_range](#equal_range)|지정된 키와 일치하는 범위를 찾습니다.|
|[erase](#erase)|지정된 위치에 있는 요소를 제거합니다.|
|[find](#find)|지정된 키와 일치하는 요소를 찾습니다.|
|[get_allocator](#get_allocator)|저장된 할당자 개체를 가져옵니다.|
|[hash_function](#hash)|저장된 해시 함수 개체를 가져옵니다.|
|[insert](#insert)|요소를 추가합니다.|
|[key_eq](#key_eq)|저장된 비교 함수 개체를 가져옵니다.|
|[load_factor](#load_factor)|버킷당 평균 요소 수를 계산합니다.|
|[max_bucket_count](#max_bucket_count)|최대 버킷 개수를 가져옵니다.|
|[max_load_factor](#max_load_factor)|버킷당 최대 요소 수를 가져오거나 설정합니다.|
|[max_size](#max_size)|제어되는 시퀀스의 최대 크기를 가져옵니다.|
|[rehash](#rehash)|해시 테이블을 다시 빌드합니다.|
|[size](#size)|요소 수를 계산합니다.|
|[스왑을](#swap)|두 컨테이너의 내용을 바꿉니다.|
|[unordered_map](#unordered_map)|컨테이너 개체를 만듭니다.|

|연산자|설명|
|-|-|
|[unordered_map::operator[]](#op_at)|지정된 키가 있는 요소를 찾거나 삽입합니다.|
|[unordered_map:: operator =](#op_eq)|해시 테이블을 복사합니다.|

## <a name="remarks"></a>설명

개체는 저장된 두 개체, [unordered_map::key_equal](#key_equal) 형식의 비교 함수 개체, [unordered_map::hasher](#hasher) 형식의 해시 함수 개체를 호출하여 제어하는 시퀀스를 정렬합니다. [Unordered_map:: key_eq](#key_eq)멤버 함수를 호출 하 여 첫 번째 저장 된 개체에 액세스 하 `()` 고, 멤버 함수 [unordered_map:: hash_function](#hash)를 호출 하 여 두 번째 저장 된 개체에 액세스 합니다 `()` . 특히 `X` 형식의 모든 값 `Y` 및 `Key`의 경우 두 인수 값이 순서 지정이 동일할 경우 호출 `key_eq()(X, Y)`에서 true를 반환하며, 호출 `hash_function()(keyval)`은 형식 `size_t`의 값 분포를 생성합니다. 클래스 템플릿 [Unordered_multimap 클래스](../standard-library/unordered-multimap-class.md)와 달리 형식의 개체는 제어 되는 `unordered_map` `key_eq()(X, Y)` 시퀀스의 두 요소에 대해 항상 false가 되도록 합니다. (키는 고유합니다.)

개체는 또한 최대 로드 비율(버킷당 최대 평균 요소 수를 원하는 대로 지정)를 저장합니다. 요소를 삽입 하면 [unordered_map:: load_factor](#load_factor) `()` 가 최대 로드 비율을 초과 하면 컨테이너는 버킷 수를 늘리고 필요에 따라 해시 테이블을 다시 작성 합니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 비교 함수, 삽입 순서, 최대 로드 비율, 현재 버킷 수에 따라 달라집니다. 제어된 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 하지만 동일하게 정렬된 요소의 하위 집합은 제어된 시퀀스에서 항상 인접해 있습니다.

개체는 [unordered_map::allocator_type](#allocator_type) 형식의 저장된 할당자 개체를 통해 제어하는 시퀀스에 대한 스토리지를 할당하고 해제합니다. 이러한 할당자 개체에는 형식의 개체와 동일한 외부 인터페이스가 있어야 합니다 `allocator` . 컨테이너 개체를 할당하는 경우 저장된 할당자 개체는 복사되지 않습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<unordered_map>

**네임스페이스:** std

## <a name="unordered_mapallocator_type"></a><a name="allocator_type"></a> unordered_map:: allocator_type

스토리지 관리를 위한 할당자의 형식입니다.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Alloc`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_mapat"></a><a name="at"></a> unordered_map:: at

지정된 키 값을 사용하여 unordered_map에서 요소를 찾습니다.

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>매개 변수

*키인지*\
찾을 키 값입니다.

### <a name="return-value"></a>반환 값

찾은 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값을 찾을 수 없는 경우 이 함수는 `out_of_range`클래스의 개체를 발생시킵니다.

### <a name="example"></a>예제

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
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

## <a name="unordered_mapbegin"></a><a name="begin"></a> unordered_map:: begin

제어되는 시퀀스 또는 버킷의 시작을 지정합니다.

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>매개 변수

*nbucket*\
버킷 번호입니다.

### <a name="remarks"></a>설명

처음 두 개의 멤버 함수는 시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 정방향 반복기를 반환합니다. 마지막 두 멤버 함수는 버킷 *nbucket* 첫 번째 요소 (또는 빈 버킷의 끝 바로 다음)를 가리키는 전방 반복기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="unordered_mapbucket"></a><a name="bucket"></a> unordered_map:: 버킷

키 값에 대한 버킷 개수를 가져옵니다.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
매핑할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 현재 키 값 *keyval* 에 해당 하는 버킷 번호를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapbucket_count"></a><a name="bucket_count"></a> unordered_map:: bucket_count

버킷 개수를 가져옵니다.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>설명

멤버 함수는 현재 버킷 수를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapbucket_size"></a><a name="bucket_size"></a> unordered_map:: bucket_size

버킷의 크기를 가져옵니다.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>매개 변수

*nbucket*\
버킷 번호입니다.

### <a name="remarks"></a>설명

멤버 함수는 버킷 번호 *nbucket* 크기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapcbegin"></a><a name="cbegin"></a> unordered_map:: cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 전방 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="unordered_mapcend"></a><a name="cend"></a> unordered_map:: cend

**`const`** 범위에서 마지막 요소 바로 다음 위치의 주소를 가리키는 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위 끝의 바로 다음을 가리키는 전방 액세스 반복기입니다.

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

## <a name="unordered_mapclear"></a><a name="clear"></a> unordered_map:: clear

모든 요소를 제거합니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

구성원 함수는 [unordered_map::erase](#erase)`(` [unordered_map::begin](#begin)`(),` [unordered_map::end](#end)`())`를 호출합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapconst_iterator"></a><a name="const_iterator"></a> unordered_map:: const_iterator

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 상수 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T1`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_local_iterator"></a><a name="const_local_iterator"></a> unordered_map:: const_local_iterator

제어되는 시퀀스에 대한 상수 버킷 반복기의 형식입니다.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>설명

형식은 버킷의 상수 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T5`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapconst_pointer"></a><a name="const_pointer"></a> unordered_map:: const_pointer

요소에 대한 상수 포인터의 형식입니다.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 상수 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_reference"></a><a name="const_reference"></a> unordered_map:: const_reference

요소에 대한 상수 참조의 형식입니다.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 상수 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapcontains"></a><a name="contains"></a> unordered_map:: contains

에 지정 된 키가 있는 요소가 있는지 여부를 확인 `unordered_map` 합니다.
C + + 20에서 도입 되었습니다.

```cpp
bool contains(const Key& key) const;
<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>매개 변수

*시계의*\
키의 형식입니다.

*키인지*\
찾을 요소의 키 값입니다.

### <a name="return-value"></a>반환 값

`true` 요소가 컨테이너에 있으면이 고, 그렇지 않으면입니다. `false` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

`contains()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

`template<class K> bool contains(const K& key) const` 가 투명 한 경우에만 오버 로드 확인에 참여 `key_compare` 합니다.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <unordered_map>
#include <iostream>

int main()
{
    std::unordered_map<int, bool> theUnorderedMap = {{0, false}, {1,true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMap.contains(1) << '\n';
    std::cout << theUnorderedMap.contains(2) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="unordered_mapcount"></a><a name="count"></a> unordered_map:: count

지정한 키와 일치하는 요소의 수를 찾습니다.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [unordered_map:: equal_range](#equal_range)로 구분 된 범위의 요소 수를 반환 합니다 `(keyval)` .

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_mapdifference_type"></a><a name="difference_type"></a> unordered_map::d ifference_type

두 요소 사이의 부호가 있는 거리의 형식입니다.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>설명

부호 있는 정수 형식은 제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T3`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_mapemplace"></a><a name="emplace"></a> unordered_map:: emplace

생성된 요소를 unordered_map의 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
값이 동등 하 게 `unordered_map` 정렬 된 요소를 이미 포함 하 고 있지 않은 경우에 삽입할 요소를 생성 하기 위해 전달 되는 인수입니다.

### <a name="return-value"></a>반환 값

`pair` **`bool`** 구성 요소가 삽입이 수행 된 경우 true를 반환 하 고,에 해당 키에 동일한 값이 있는 요소가 이미 포함 되어 있는 경우에는 false를 반환 `unordered_map` 하 고, 해당 반복기 구성 요소는 새 요소가 삽입 되었거나 요소가 이미 있었던 주소를 반환 하는입니다.

이 멤버 함수가 반환하는 `pr` 쌍의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 해당 구성 요소를 역참조하려면 `*(pr.first)`를 사용합니다. **`bool`** 이 멤버 함수가 반환 하는 쌍의 구성 요소에 액세스 하려면를 `pr` 사용 `pr.second` 합니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

삽입 중에 예외가 throw되었으나 컨테이너의 해시 함수에서 발생하지 않은 경우에는 컨테이너가 수정되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다.

코드 예제를 보려면 [map::emplace](../standard-library/map-class.md#emplace)를 참조하세요.

## <a name="unordered_mapemplace_hint"></a><a name="emplace_hint"></a> unordered_map:: emplace_hint

배치 힌트를 사용하여 생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
unordered_map이 해당 요소를 이미 포함하고 있지 않거나, 보다 일반적으로는 키가 동등하게 정렬된 요소를 이미 포함하고 있지 않을 경우 unordered_map에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치와 관련된 힌트입니다.

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

요소가 이미 있어서 삽입이 실패하면 기존 요소에 대한 반복기가 반환됩니다.

### <a name="remarks"></a>설명

이 함수는 참조를 무효화하지 않습니다.

삽입 중에 예외가 throw되었으나 컨테이너의 해시 함수에서 발생하지 않은 경우에는 컨테이너가 수정되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다.

요소의 [value_type](../standard-library/map-class.md#value_type)은 쌍이므로, 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소가 요소의 데이터 값과 동일한 정렬된 쌍입니다.

코드 예제를 보려면 [map::emplace_hint](../standard-library/map-class.md#emplace_hint)를 참조하세요.

## <a name="unordered_mapempty"></a><a name="empty"></a> unordered_map:: empty

요소가 있는지 여부를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapend"></a><a name="end"></a> unordered_map:: end

제어되는 시퀀스의 끝을 지정합니다.

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>매개 변수

*nbucket*\
버킷 번호입니다.

### <a name="remarks"></a>설명

처음 두 멤버 함수는 시퀀스 끝의 바로 다음을 가리키는 정방향 반복기를 반환합니다. 마지막 두 멤버 함수는 버킷 *n 버킷의* 끝 바로 다음을 가리키는 전방 반복기를 반환 합니다.

## <a name="unordered_mapequal_range"></a><a name="equal_range"></a> unordered_map:: equal_range

지정된 키와 일치하는 범위를 찾습니다.

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` `[X.first, X.second)` *keyval* 와 동일한 순서로 정렬 된 제어 되는 시퀀스의 요소만 구분 하는 반복기 쌍을 반환 합니다. 이러한 요소가 없는 경우 두 반복기는 `end()`입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="unordered_maperase"></a><a name="erase"></a> unordered_map:: erase

지정된 위치에서 unordered_map의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
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

처음 두 구성원 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 map의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 구성원 함수의 경우 unordered_map에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>설명

코드 예제를 보려면 [map::erase](../standard-library/map-class.md#erase)를 참조하세요.

## <a name="unordered_mapfind"></a><a name="find"></a> unordered_map:: find

지정된 키와 일치하는 요소를 찾습니다.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [unordered_map:: equal_range](#equal_range) `(keyval).first` 을 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="unordered_mapget_allocator"></a><a name="get_allocator"></a> unordered_map:: get_allocator

저장된 할당자 개체를 가져옵니다.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 할당자 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_maphash_function"></a><a name="hash"></a> unordered_map:: hash_function

저장된 해시 함수 개체를 가져옵니다.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 해시 함수 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_maphasher"></a><a name="hasher"></a> unordered_map:: hasher

해시 함수의 형식입니다.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Hash`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_mapinsert"></a><a name="insert"></a> unordered_map:: insert

unordered_map에 요소 또는 요소의 범위를 삽입합니다.

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);

// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>매개 변수

*짧은*\
키가 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 unordered_map에 삽입되는 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다.

*ValTy*\
Unordered_map에서 [value_type](../standard-library/map-class.md#value_type)요소를 생성 하는 데 사용할 수 있는 인수 형식을 지정 하 고 *Val* 을 인수로 사용 하는 템플릿 매개 변수입니다.

*기본*\
복사할 첫 번째 요소의 위치입니다.

*최신*\
복사할 마지막 요소 바로 다음 위치입니다.

*InputIterator*\
[value_type](../standard-library/map-class.md#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.

*IList*\
요소를 복사할 [initializer_list](../standard-library/initializer-list.md) 입니다.

### <a name="return-value"></a>반환 값

단일 요소 멤버 함수 (1) 및 (2)는 [](../standard-library/pair-structure.md) **`bool`** 구성 요소가 삽입 된 경우 true이 고 unordered_map에 이미 키에 동일한 값이 있는 요소가 이미 포함 되어 있는 경우 false 인 쌍을 반환 합니다. 반환 값 쌍의 반복기 구성 요소는 구성 요소가 true 인 경우 새로 삽입 된 요소를 가리키거나 **`bool`** 구성 요소가 false 인 경우에는 기존 요소를 가리킵니다 **`bool`** .

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 새 요소가 unordered_map에 삽입된 위치를 가리키는 반복기를 반환하고 동일한 키가 있는 요소가 존재하는 경우에는 기존 요소를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 반복기, 포인터 또는 참조를 무효화하지 않습니다.

요소를 하나만 삽입하는 중 예외가 throw되었으나 컨테이너의 해시 함수에서 발생하지 않은 경우에는 컨테이너의 상태가 수정되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

단일 요소 구성원 함수에서 반환한 `pair` `pr`의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 반환된 쌍 내에서 반복기를 역참조하려면 `*pr.first`를 사용하여 요소를 제공합니다. 구성 요소에 액세스 하려면를 **`bool`** 사용 `pr.second` 합니다. 예제는 이 문서 뒷부분에 있는 샘플 코드를 참조하세요.

컨테이너의 [value_type](../standard-library/map-class.md#value_type)은 컨테이너에 속한 typedef이고 map의 경우 `map<K, V>::value_type`은 `pair<const K, V>`입니다. 요소의 값은 첫 번째 구성 요소가 키 값과 동일하고 두 번째 구성 요소는 요소의 데이터 값과 동일한 정렬된 쌍입니다.

범위 멤버 함수 (5)는 `[First, Last)` 범위에서 반복기가 주소를 지정하는 각 요소에 해당하는 unordered_map에 요소 값의 시퀀스를 입력하므로 `Last`는 삽입되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `m.insert(v.begin(), v.end());` 문이 `v`의 모든 요소를 `m`에 삽입하려고 합니다. 범위에 고유 값이 있는 요소만 삽입됩니다. 중복 값은 무시됩니다. 어떤 요소가 거부되는지 관찰하려면 `insert`의 단일 요소 버전을 사용합니다.

이니셜라이저 목록 구성원 함수 (6)은 [initializer_list](../standard-library/initializer-list.md)를 사용하여 요소를 unordered_map으로 복사합니다.

생성된 요소를 제 위치에 삽입하려면, 즉 복사 또는 이동 작업을 수행하지 않으려면 [unordered_map::emplace](#emplace) 및 [unordered_map::emplace_hint](#emplace_hint)를 참조하세요.

코드 예제를 보려면 [map::insert](../standard-library/map-class.md#insert)를 참조하세요.

## <a name="unordered_mapiterator"></a><a name="iterator"></a> unordered_map:: iterator

제어되는 시퀀스에 대한 반복기의 형식입니다.

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T0`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapkey_eq"></a><a name="key_eq"></a> unordered_map:: key_eq

저장된 비교 함수 개체를 가져옵니다.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 비교 함수 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_equal"></a><a name="key_equal"></a> unordered_map:: key_equal

비교 함수의 형식입니다.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Pred`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_type"></a><a name="key_type"></a> unordered_map:: key_type

정렬 키의 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Key`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapload_factor"></a><a name="load_factor"></a> unordered_map:: load_factor

버킷당 평균 요소 수를 계산합니다.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `(float)` 버킷 당 평균 요소 수를 [unordered_map:: size](#size) `() / (float)` [unordered_map:: bucket_count](#bucket_count) `()` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_maplocal_iterator"></a><a name="local_iterator"></a> unordered_map:: local_iterator

버킷 반복기의 형식입니다.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>설명

형식은 버킷의 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T4`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapmapped_type"></a><a name="mapped_type"></a> unordered_map:: mapped_type

각 키와 연결된 매핑된 값의 형식입니다.

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Ty`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapmax_bucket_count"></a><a name="max_bucket_count"></a> unordered_map:: max_bucket_count

최대 버킷 개수를 가져옵니다.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>설명

멤버 함수는 현재 허용된 최대 버킷 개수를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_load_factor"></a><a name="max_load_factor"></a> unordered_map:: max_load_factor

버킷당 최대 요소 수를 가져오거나 설정합니다.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>매개 변수

*이용한*\
새로운 최대 로드 비율입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장된 최대 로드 비율을 반환합니다. 두 번째 멤버 함수는 저장 된 최대 로드 비율을 *인수로* 바꿉니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_size"></a><a name="max_size"></a> unordered_map:: max_size

제어되는 시퀀스의 최대 크기를 가져옵니다.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 개체가 제어할 수 있는 가장 긴 시퀀스의 길이를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }
```

```Output
max_size() == 536870911
```

## <a name="unordered_mapoperator"></a><a name="op_at"></a> unordered_map:: operator []

지정된 키가 있는 요소를 찾거나 삽입합니다.

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>매개 변수

*Keyval*\
찾거나 삽입할 키 값입니다.

### <a name="return-value"></a>반환 값

삽입된 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값이 없으면 데이터 형식의 기본값과 함께 삽입됩니다.

`operator[]`*m*[*key*] =를 사용 하 여 map *m* 에 요소를 삽입 하는 데 사용할 수 있습니다. `DataValue` 여기서은 키 `DataValue` `mapped_type` 값이 *key* 인 요소의 값입니다.

`operator[]`를 사용하여 요소를 삽입하는 경우 반환된 참조는 삽입이 기존 요소를 변경하는지 또는 새 요소를 생성하는지 여부를 나타내지 않습니다. 멤버 함수 [find](../standard-library/map-class.md#find) 및 [insert](../standard-library/map-class.md#insert)는 지정된 키가 포함된 요소가 삽입 전에 이미 있는지 여부를 확인하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>설명

구성원 함수는 `where` 반복기를 [unordered_map::insert](#insert)`(` [unordered_map::value_type](#value_type)`(keyval, Ty())`의 반환 값으로 결정합니다. (해당 요소가 없는 경우 지정 된 키를 가진 요소를 삽입 합니다.) 그런 다음에 대 한 참조를 반환 `(*where).second` 합니다.

## <a name="unordered_mapoperator"></a><a name="op_eq"></a> unordered_map:: operator =

다른 unordered_map의 요소를 사용하여 이 unordered_map의 요소를 대체합니다.

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
연산자 함수에서 콘텐츠를 할당하는 unordered_map입니다.

### <a name="remarks"></a>설명

첫 번째 버전은의 모든 요소를 *오른쪽* 에서이 unordered_map로 복사 합니다.

두 번째 버전은 모든 요소를 *오른쪽* 에서이 unordered_map로 이동 합니다.

실행 하기 전에이 unordered_map에 있는 모든 요소는 `operator=` 삭제 됩니다.

### <a name="example"></a>예제

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

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

## <a name="unordered_mappointer"></a><a name="pointer"></a> unordered_map::p ointer

요소에 대한 포인터의 형식입니다.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapreference"></a><a name="reference"></a> unordered_map:: reference

요소에 대한 참조의 형식입니다.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_maprehash"></a><a name="rehash"></a> unordered_map:: rehash

해시 테이블을 다시 빌드합니다.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>매개 변수

*nbuckets*\
요청된 버킷 수입니다.

### <a name="remarks"></a>설명

멤버 함수는 버킷 수를 최소한 *nbuckets* 변경 하 고 필요에 따라 해시 테이블을 다시 빌드합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="unordered_mapsize"></a><a name="size"></a> unordered_map:: size

요소 수를 계산합니다.

```cpp
size_type size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapsize_type"></a><a name="size_type"></a> unordered_map:: size_type

두 요소 사이의 부호가 없는 거리의 형식입니다.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>설명

부호 없는 정수 형식은 제어되는 시퀀스의 길이를 나타낼 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식 `T2`의 동의어로 설명됩니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }
```

```Output
size == 0
```

## <a name="unordered_mapswap"></a><a name="swap"></a> unordered_map:: swap

두 컨테이너의 내용을 바꿉니다.

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`*this`** 과 *오른쪽* 으로 바꿉니다. [Unordered_map:: get_allocator](#get_allocator) `() == right.get_allocator()` 는 일정 한 시간에이 작업을 수행 하 고, 형식의 저장 된 특성 개체를 복사 하는 경우에만 예외를 throw 하 `Tr` 고, 두 개의 제어 된 시퀀스에서 요소를 지정 하는 참조, 포인터 또는 반복기를 무효화 하지 않습니다. 그렇지 않으면 두 개의 제어되는 시퀀스에 있는 요소 수에 비례하여 많은 요소 할당 및 생성자 호출을 수행합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapunordered_map"></a><a name="unordered_map"></a> unordered_map:: unordered_map

컨테이너 개체를 만듭니다.

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>매개 변수

*항상*\
저장할 할당자 개체입니다.

*생략*\
저장할 비교 함수 개체입니다.

*해시로*\
저장할 해시 함수 개체입니다.

*Bucket_count*\
최소 버킷 수입니다.

*오른쪽*\
복사할 컨테이너입니다.

*기본*\
복사할 첫 번째 요소의 위치입니다.

*최신*\
복사할 마지막 요소 바로 다음 위치입니다.

*IList*\
복사할 요소가 포함된 initializer_list입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `right`에 의해 제어되는 시퀀스의 복사본을 지정합니다. 두 번째 생성자는 빈 제어 시퀀스를 지정합니다. 세 번째 생성자는 `[first, last)` 요소 값의 시퀀스를 삽입합니다. 네 번째 생성자는 `right`를 이동하여 시퀀스의 복사본을 지정합니다.

모든 생성자는 또한 여러 개의 저장된 값을 초기화합니다. 복사 생성자의 경우 값은 *오른쪽* 에서 가져옵니다. 그렇지 않은 경우:

버킷 최소 수는 인수 *Bucket_count*(있는 경우)입니다. 그렇지 않으면 여기에 구현 정의 값으로 설명 된 기본값입니다 `N0` .

해시 함수 개체는 인수 *해시*(있는 경우)입니다. 그렇지 않으면 `Hash()` 입니다.

비교 함수 개체는 인수 *Comp*(있는 경우)입니다. 그렇지 않으면 `Pred()` 입니다.

할당자 개체는 *Al* 인수입니다 (있는 경우). 그렇지 않으면 `Alloc()` 입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="unordered_mapvalue_type"></a><a name="value_type"></a> unordered_map:: value_type

요소의 형식입니다.

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>설명

형식은 제어되는 시퀀스의 요소를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>참조

[<unordered_map>](../standard-library/unordered-map.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
