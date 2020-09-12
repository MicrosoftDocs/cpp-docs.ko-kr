---
title: unordered_set 클래스
description: '`unordered_set`순서가 지정 되지 않은 컬렉션에서 데이터를 저장 하 고 검색 하는 데 사용 되는 c + + 표준 라이브러리 컨테이너 클래스에 대 한 API 참조입니다.'
ms.date: 9/9/2020
f1_keywords:
- unordered_set/std::unordered_set
- unordered_set/std::unordered_set::allocator_type
- unordered_set/std::unordered_set::const_iterator
- unordered_set/std::unordered_set::const_local_iterator
- unordered_set/std::unordered_set::const_pointer
- unordered_set/std::unordered_set::const_reference
- unordered_set/std::unordered_set::difference_type
- unordered_set/std::unordered_set::hasher
- unordered_set/std::unordered_set::iterator
- unordered_set/std::unordered_set::key_equal
- unordered_set/std::unordered_set::key_type
- unordered_set/std::unordered_set::local_iterator
- unordered_set/std::unordered_set::pointer
- unordered_set/std::unordered_set::reference
- unordered_set/std::unordered_set::size_type
- unordered_set/std::unordered_set::value_type
- unordered_set/std::unordered_set::begin
- unordered_set/std::unordered_set::bucket
- unordered_set/std::unordered_set::bucket_count
- unordered_set/std::unordered_set::bucket_size
- unordered_set/std::unordered_set::cbegin
- unordered_set/std::unordered_set::cend
- unordered_set/std::unordered_set::clear
- unordered_set/std::unordered_set::count
- unordered_set/std::unordered_set::contains
- unordered_set/std::unordered_set::emplace
- unordered_set/std::unordered_set::emplace_hint
- unordered_set/std::unordered_set::empty
- unordered_set/std::unordered_set::end
- unordered_set/std::unordered_set::equal_range
- unordered_set/std::unordered_set::erase
- unordered_set/std::unordered_set::find
- unordered_set/std::unordered_set::get_allocator
- unordered_set/std::unordered_set::hash
- unordered_set/std::unordered_set::insert
- unordered_set/std::unordered_set::key_eq
- unordered_set/std::unordered_set::load_factor
- unordered_set/std::unordered_set::max_bucket_count
- unordered_set/std::unordered_set::max_load_factor
- unordered_set/std::unordered_set::max_size
- unordered_set/std::unordered_set::rehash
- unordered_set/std::unordered_set::size
- unordered_set/std::unordered_set::swap
- unordered_set/std::unordered_set::unordered_set
- unordered_set/std::unordered_set::operator=
- unordered_set/std::unordered_set::hash_function
helpviewer_keywords:
- std::unordered_set
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::contains
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
- std::unordered_set::unordered_set
- std::unordered_set::operator=
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash_function
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
ms.openlocfilehash: 396465b24e9d7cf0facbe324c7b01479fe8e9b6b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040043"
---
# <a name="unordered_set-class"></a>unordered_set 클래스

클래스 템플릿은 형식의 다양 한 길이 요소 시퀀스를 제어 하는 개체를 설명 합니다 `const Key` . 시퀀스는 해시 함수로 약하게 정렬됩니다. 즉, 시퀀스를 버킷이라고 하는 하위 시퀀스의 정렬된 집합으로 분할합니다. 각 버킷 내에서 비교 함수는 요소 쌍의 순서가 동일한 지 여부를 확인 합니다. 각 요소는 정렬 키와 값으로 사용됩니다. 시퀀스는 최소한 모든 버킷이 대략 동일한 크기일 경우 시퀀스의 요소 수와 상관없이 작업 수를 사용하여 임의 요소를 조회, 삽입, 제거하는 방식으로 나타냅니다(일정 시간). 모든 요소가 하나의 버킷에 있는 최악의 경우에는 작업 수가 시퀀스의 요소 수에 비례합니다(선형 시간). 요소를 삽입 하면 반복기가 무효화 되지 않으며, 요소를 제거 하면 제거 된 요소를 가리키는 반복기만 무효화 됩니다.

## <a name="syntax"></a>구문

```cpp
template <
   class Key,
   class Hash = std::hash<Key>,
   class Pred = std::equal_to<Key>,
   class Alloc = std::allocator<Key>>
class unordered_set;
```

### <a name="parameters"></a>매개 변수

*키인지*\
키 형식입니다.

*해시로*\
해시 함수 개체 형식입니다.

*Pred*\
같음 비교 함수 개체 형식입니다.

*#C4*\
할당자 클래스입니다.

## <a name="members"></a>멤버

### <a name="typedefs"></a>Typedefs

|Name|Description|
|-|-|
|[allocator_type](#allocator_type)|스토리지 관리를 위한 할당자의 형식입니다.|
|[const_iterator](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[const_local_iterator](#const_local_iterator)|제어되는 시퀀스에 대한 상수 버킷 반복기의 형식입니다.|
|[const_pointer](#const_pointer)|요소에 대한 상수 포인터의 형식입니다.|
|[const_reference](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[difference_type](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[hasher](#hasher)|해시 함수의 형식입니다.|
|[반복](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[key_equal](#key_equal)|비교 함수의 형식입니다.|
|[key_type](#key_type)|정렬 키의 형식입니다.|
|[local_iterator](#local_iterator)|제어되는 시퀀스에 대한 버킷 반복기의 형식입니다.|
|[놓고](#pointer)|요소에 대한 포인터의 형식입니다.|
|[reference](#reference)|요소에 대한 참조의 형식입니다.|
|[size_type](#size_type)|두 요소 사이의 부호가 없는 거리의 형식입니다.|
|[value_type](#value_type)|요소의 형식입니다.|

### <a name="functions"></a>Functions

|Name|Description|
|-|-|
|[시작](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[버킷](#bucket)|키 값에 대한 버킷 개수를 가져옵니다.|
|[bucket_count](#bucket_count)|버킷 개수를 가져옵니다.|
|[bucket_size](#bucket_size)|버킷의 크기를 가져옵니다.|
|[cbegin](#cbegin)|제어되는 시퀀스의 시작을 지정합니다.|
|[cend](#cend)|제어되는 시퀀스의 끝을 지정합니다.|
|[해제](#clear)|모든 요소를 제거합니다.|
|[contains](#contains)<sup>c + + 20</sup> 포함|에 지정 된 키를 가진 요소가 있는지 확인 `unordered_set` 합니다.|
|[count](#count)|지정한 키와 일치하는 요소의 수를 찾습니다.|
|[emplace](#emplace)|생성된 요소를 추가합니다.|
|[emplace_hint](#emplace_hint)|힌트와 함께 생성된 요소를 추가합니다.|
|[empty](#empty)|요소가 있는지 여부를 테스트합니다.|
|[종단](#end)|제어되는 시퀀스의 끝을 지정합니다.|
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
|[unordered_set](#unordered_set)|컨테이너 개체를 만듭니다.|

### <a name="operators"></a>연산자

|Name|Description|
|-|-|
|[unordered_set:: operator =](#op_eq)|해시 테이블을 복사합니다.|

## <a name="remarks"></a>설명

개체는 두 개의 저장 된 개체를 호출 하 여 제어 하는 시퀀스를 정렬 합니다. [unordered_set:: key_equal](#key_equal) 형식의 비교 함수 개체와 [unordered_set:: hasher](#hasher)형식의 해시 함수 개체입니다. [Unordered_set:: key_eq](#key_eq)멤버 함수를 호출 하 여 첫 번째 저장 된 개체에 액세스 하 `()` 고, 멤버 함수 [unordered_set:: hash_function](#hash)를 호출 하 여 두 번째 저장 된 개체에 액세스 합니다 `()` . 특히 `X` 형식의 모든 값 `Y` 및 `Key`의 경우 두 인수 값이 순서 지정이 동일할 경우 호출 `key_eq()(X, Y)`에서 true를 반환하며, 호출 `hash_function()(keyval)`은 형식 `size_t`의 값 분포를 생성합니다. 클래스 템플릿 [Unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)와 달리 형식의 개체는 제어 되는 `unordered_set` `key_eq()(X, Y)` 시퀀스의 두 요소에 대해 항상 false가 되도록 합니다. (키는 고유합니다.)

개체는 또한 최대 로드 비율(버킷당 최대 평균 요소 수를 원하는 대로 지정)를 저장합니다. 요소를 삽입 하면 [unordered_set:: load_factor](#load_factor) `()` 가 최대 로드 비율을 초과 하면 컨테이너는 버킷 수를 늘리고 필요에 따라 해시 테이블을 다시 작성 합니다.

제어된 시퀀스의 실제 요소 순서는 해시 함수, 비교 함수, 삽입 순서, 최대 로드 비율, 현재 버킷 수에 따라 달라집니다. 제어 되는 시퀀스의 요소 순서는 일반적으로 예측할 수 없습니다. 하지만 동일하게 정렬된 요소의 하위 집합은 제어된 시퀀스에서 항상 인접해 있습니다.

개체는 [unordered_set:: allocator_type](#allocator_type)형식의 저장 된 할당자 개체를 통해 제어 하는 시퀀스에 대 한 저장소를 할당 하 고 해제 합니다. 이러한 할당자 개체에는 형식의 개체와 동일한 외부 인터페이스가 있어야 합니다 `allocator` . 저장 된 할당자 개체는 컨테이너 개체가 할당 될 때 복사 되지 않습니다.

## <a name="unordered_setallocator_type"></a><a name="allocator_type"></a> unordered_set:: allocator_type

스토리지 관리를 위한 할당자의 형식입니다.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Alloc`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="begin"></a><a name="begin"></a> 시작

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
// unordered_set_begin.cpp
// compile using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>

using namespace std;

typedef unordered_set<char> MySet;

int main()
{
    MySet c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents using range-based for
    for (auto it : c1) {
    cout << "[" << it << "] ";
    }

    cout << endl;

    // display contents using explicit for
    for (MySet::const_iterator it = c1.begin(); it != c1.end(); ++it) {
        cout << "[" << *it << "] ";
    }

    cout << std::endl;

    // display first two items
    MySet::iterator it2 = c1.begin();
    cout << "[" << *it2 << "] ";
    ++it2;
    cout << "[" << *it2 << "] ";
    cout << endl;

    // display bucket containing 'a'
    MySet::const_local_iterator lit = c1.begin(c1.bucket('a'));
    cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[a] [b] [c]
[a] [b] [c]
[a] [b]
[a]
```

## <a name="bucket"></a><a name="bucket"></a> 버킷

키 값에 대한 버킷 개수를 가져옵니다.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
매핑할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 현재 키 값 *keyval*에 해당 하는 버킷 번호를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a><a name="bucket_count"></a> bucket_count

버킷 개수를 가져옵니다.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>설명

멤버 함수는 현재 버킷 수를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="bucket_size"></a><a name="bucket_size"></a> bucket_size

버킷의 크기를 가져옵니다.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>매개 변수

*nbucket*\
버킷 번호입니다.

### <a name="remarks"></a>설명

멤버 함수는 버킷 번호 *nbucket*크기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 전방 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

의 반환 값을 사용 하 여 `cbegin` 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 isContainer<T>::iterator
auto i2 = Container.cbegin();

// i2 isContainer<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

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
// i1 isContainer<T>::iterator
auto i2 = Container.cend();

// i2 isContainer<T>::const_iterator
```

에서 반환 된 값은 `cend` 역참조 되지 않아야 합니다.

## <a name="clear"></a><a name="clear"></a> 해제

모든 요소를 제거합니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

멤버 함수는 [unordered_set:: erase](#erase) `(` [unordered_set:: begin](#begin) `(),` [unordered_set:: end](#end)를 호출 `())` 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 상수 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 구현 정의 형식에 대 한 동의어로 여기에 설명 되어 `T1` 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
    std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_local_iterator"></a><a name="const_local_iterator"></a> const_local_iterator

제어되는 시퀀스에 대한 상수 버킷 반복기의 형식입니다.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>설명

형식은 버킷의 상수 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 구현 정의 형식에 대 한 동의어로 여기에 설명 되어 `T5` 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

요소에 대한 상수 포인터의 형식입니다.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 상수 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_pointer p = &*it;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

요소에 대한 상수 참조의 형식입니다.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 상수 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_reference ref = *it;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="contains"></a><a name="contains"></a> 에서는

에 지정 된 키를 가진 요소가 있는지 여부를 확인 `unordered_set` 합니다.

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

`true` 요소가 컨테이너에 있으면이 고, 그렇지 않으면입니다. `false` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

`contains()` 는 c + + 20의 새로운 기능은입니다. 이를 사용 하려면 [/sd: c + + 최신](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 합니다.

`template<class K> bool contains(const K& key) const` 가 투명 한 경우에만 오버 로드 확인에 참여 `key_compare` 합니다.

### <a name="example"></a>예제

```cpp
// Requires /std:c++latest
#include <unordered_set>
#include <iostream>

int main()
{
    std::unordered_set<int> theUnorderedSet = { 1, 2 };

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedSet.contains(2) << '\n';
    std::cout << theUnorderedSet.contains(3) << '\n';
    
    return 0;
}
```

```Output
true
false
```

## <a name="count"></a><a name="count"></a> 수

지정한 키와 일치하는 요소의 수를 찾습니다.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [unordered_set:: equal_range](#equal_range)로 구분 된 범위의 요소 수를 반환 합니다 `(keyval)` .

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

두 요소 사이의 부호가 있는 거리의 형식입니다.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>설명

부호 있는 정수 형식은 제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다. 구현 정의 형식에 대 한 동의어로 여기에 설명 되어 `T3` 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
end()-begin() == 3
begin()-end() == -3
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
값이 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 unordered_set에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

`pair` **`bool`** 구성 요소가 삽입이 수행 된 경우 true를 반환 하 고,에 해당 키에 동일한 값이 있는 요소가 이미 포함 되어 있는 경우에는 false를 반환 `unordered_set` 하 고, 해당 반복기 구성 요소는 새 요소가 삽입 되었거나 요소가 이미 있었던 주소를 반환 하는입니다.

이 멤버 함수가 반환하는 `pr` 쌍의 반복기 구성 요소에 액세스하려면 `pr.first`를 사용하고 해당 구성 요소를 역참조하려면 `*(pr.first)`를 사용합니다. **`bool`** 이 멤버 함수가 반환 하는 쌍의 구성 요소에 액세스 하려면를 `pr` 사용 `pr.second` 합니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

삽입 하는 동안 예외가 throw 되었지만 컨테이너의 해시 함수에서 발생 하지 않는 경우 컨테이너는 수정 되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다.

코드 예제를 보려면 [set:: emplace](../standard-library/set-class.md#emplace)를 참조 하세요.

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

배치 힌트를 사용하여 생성된 요소를 제 위치에 삽입합니다. 복사 또는 이동 작업은 수행되지 않습니다.

```cpp
template <class... Args>
iterator emplace_hint(
const_iteratorwhere,
Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
unordered_set가 해당 요소를 이미 포함하고 있지 않거나, 보다 일반적으로는 키가 동등하게 정렬된 요소를 이미 포함하고 있지 않을 경우 unordered_set에 삽입되는 요소를 생성하기 위해 전달되는 인수입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치에 대 한 힌트입니다.

### <a name="return-value"></a>반환 값

새로 삽입된 요소에 대한 반복기입니다.

요소가 이미 있어서 삽입이 실패하면 기존 요소에 대한 반복기가 반환됩니다.

### <a name="remarks"></a>설명

이 함수는 반복기나 참조를 무효화 되지 않습니다.

삽입 하는 동안 예외가 throw 되었지만 컨테이너의 해시 함수에서 발생 하지 않는 경우 컨테이너는 수정 되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다.

코드 예제를 보려면 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)를 참조하세요.

## <a name="empty"></a><a name="empty"></a> 비우려면

요소가 있는지 여부를 테스트합니다.

```cpp
bool empty() const;
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="end"></a><a name="end"></a> 종단

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

처음 두 멤버 함수는 시퀀스 끝의 바로 다음을 가리키는 정방향 반복기를 반환합니다. 마지막 두 멤버 함수는 버킷 *n 버킷의*끝 바로 다음을 가리키는 전방 반복기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect last two items "[a] [b] "
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << "[" << *it2 << "] ";
    --it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a] [b]
[a]
```

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

지정된 키와 일치하는 범위를 찾습니다.

```cpp
std::pair<iterator, iterator>
equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` `[X.first, X.second)` *keyval*와 동일한 순서로 정렬 된 제어 되는 시퀀스의 요소만 구분 하는 반복기 쌍을 반환 합니다. 이러한 요소가 없는 경우 두 반복기는 `end()`입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
    c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="erase"></a><a name="erase"></a> 지우는

지정된 위치에서 unordered_set의 요소 또는 요소의 범위를 제거하거나 지정된 키와 일치하는 요소를 제거합니다.

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

처음 두 구성원 함수의 경우 제거된 요소 뒤에 남은 첫 번째 요소 또는 이러한 요소가 없을 경우 unordered_set의 끝에 있는 요소를 지정하는 양방향 반복기입니다.

세 번째 구성원 함수의 경우 unordered_set에서 제거된 요소의 수를 반환합니다.

### <a name="remarks"></a>설명

코드 예제를 보려면 [set::erase](../standard-library/set-class.md#erase)를 참조하세요.

## <a name="find"></a><a name="find"></a> 찾아낼

지정된 키와 일치하는 요소를 찾습니다.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>매개 변수

*keyval*\
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [unordered_set:: equal_range](#equal_range) `(keyval).first` 을 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
    << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
    << std::boolalpha << (it != c1.end())
    << ": [" << *it << "] " << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

저장된 할당자 개체를 가져옵니다.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 할당자 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="hash_function"></a><a name="hash"></a> hash_function

저장된 해시 함수 개체를 가져옵니다.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 해시 함수 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a><a name="hasher"></a> hasher

해시 함수의 형식입니다.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Hash`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a><a name="insert"></a> 넣거나

unordered_set에 요소 또는 요소의 범위를 삽입합니다.

```cpp
// (1) single element
pair<iterator, bool> insert(const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool> insert(ValTy&& Val);

// (3) single element with hint
iterator insert(const_iterator Where, const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(const_iterator Where, ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First, InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type> IList);
```

### <a name="parameters"></a>매개 변수

*짧은*\
키가 동등하게 정렬된 요소가 이미 포함되어 있지 않으면 unordered_set에 삽입되는 요소의 값입니다.

*위치*\
올바른 삽입 지점 검색을 시작할 위치입니다.

*ValTy*\
Unordered_set에서 [value_type](../standard-library/map-class.md#value_type)요소를 생성 하는 데 사용할 수 있는 인수 형식을 지정 하 고 *Val* 을 인수로 사용 하는 템플릿 매개 변수입니다.

*기본*\
복사할 첫 번째 요소의 위치입니다.

*최신*\
복사할 마지막 요소 바로 다음 위치입니다.

*InputIterator*\
[value_type](../standard-library/map-class.md#value_type) 개체를 생성하는 데 사용할 수 있는 형식의 요소를 가리키는 [입력 반복기](../standard-library/input-iterator-tag-struct.md)의 요구 사항을 충족하는 템플릿 함수 인수입니다.

*IList*\
요소를 복사할 [initializer_list](../standard-library/initializer-list.md) 입니다.

### <a name="return-value"></a>반환 값

단일 요소 멤버 함수 (1) 및 (2)는 [pair](../standard-library/pair-structure.md) **`bool`** 구성 요소가 삽입 된 경우 true이 고 unordered_set에 이미 키에 동일한 값이 있는 요소가 이미 포함 되어 있는 경우 false 인 쌍을 반환 합니다. 반환 값 쌍의 반복기 구성 요소는 구성 요소가 true 인 경우 새로 삽입 된 요소를 가리키거나 **`bool`** 구성 요소가 false 인 경우에는 기존 요소를 가리킵니다 **`bool`** .

힌트가 있는 단일 요소 멤버 함수 (3) 및 (4)는 새 요소가 unordered_set에 삽입된 위치를 가리키는 반복기를 반환하고 동일한 키가 있는 요소가 존재하는 경우에는 기존 요소를 가리키는 반복기를 반환합니다.

### <a name="remarks"></a>설명

이 함수는 반복기, 포인터 또는 참조를 무효화하지 않습니다.

하나의 요소만 삽입 하는 동안 예외가 throw 되지만 컨테이너의 해시 함수에서 발생 하지 않는 경우 컨테이너의 상태가 수정 되지 않습니다. 예외가 해시 함수에서 throw된 경우 결과는 정의되어 있지 않습니다. 여러 요소를 삽입하는 중 예외가 throw되면 컨테이너는 지정되지 않았으나 유효한 상태로 남아 있습니다.

`pair` `pr` 단일 요소 멤버 함수에서 반환 된의 반복기 구성 요소에 액세스 하려면를 사용 하 `pr.first` 고 반환 된 쌍 내에서 반복기를 역참조 하려면를 사용 하 여 `*pr.first` 요소를 제공 합니다. 구성 요소에 액세스 하려면를 **`bool`** 사용 `pr.second` 합니다. 예제는 이 문서 뒷부분에 있는 샘플 코드를 참조하세요.

컨테이너의 [value_type](../standard-library/map-class.md#value_type)은 컨테이너에 속한 형식 정의이고 set의 경우 `unordered_set<V>::value_type`은 `const V`입니다.

범위 멤버 함수 (5)는 범위에서 반복기가 주소를 지정 하는 각 요소에 해당 하는 unordered_set에 요소 값의 시퀀스를 삽입 `[First, Last)` 합니다. 따라서 *Last* 는 삽입 되지 않습니다. 컨테이너 멤버 함수 `end()`는 컨테이너의 마지막 요소 바로 뒤에 있는 위치를 참조합니다. 예를 들어 `s.insert(v.begin(), v.end());` 문이 `v`의 모든 요소를 `s`에 삽입하려고 합니다. 범위에 고유 값이 있는 요소만 삽입됩니다. 중복 값은 무시됩니다. 어떤 요소가 거부되는지 관찰하려면 `insert`의 단일 요소 버전을 사용합니다.

이니셜라이저 목록 멤버 함수 (6)는 [initializer_list](../standard-library/initializer-list.md) 을 사용 하 여 요소를 unordered_set에 복사 합니다.

생성된 요소를 제 위치에 삽입하려면, 즉 복사 또는 이동 작업을 수행하지 않으려면 [set::emplace](../standard-library/set-class.md#emplace) 및 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)를 참조하세요.

코드 예제를 보려면 [set:: insert](../standard-library/set-class.md#insert)를 참조 하세요.

## <a name="iterator"></a><a name="iterator"></a> 반복

Unordered_set의 요소를 읽을 수 있는 상수 [전방 반복기](../standard-library/forward-iterator-tag-struct.md) 를 제공 하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>예제

**반복기**를 선언 하 고 사용 하는 방법에 대 한 예제는 [begin](../standard-library/set-class.md#begin) 의 예제를 참조 하세요.

## <a name="key_eq"></a><a name="key_eq"></a> key_eq

저장된 비교 함수 개체를 가져옵니다.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>설명

멤버 함수는 저장된 비교 함수 개체를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="key_equal"></a><a name="key_equal"></a> key_equal

비교 함수의 형식입니다.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Pred`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="key_type"></a><a name="key_type"></a> key_type

정렬 키의 형식입니다.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Key`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="load_factor"></a><a name="load_factor"></a> load_factor

버킷당 평균 요소 수를 계산합니다.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `(float)` 버킷 당 평균 요소 수를[unordered_set:: size](#size) `() / (float)` [unordered_set:: bucket_count](#bucket_count) `()` 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="local_iterator"></a><a name="local_iterator"></a> local_iterator

버킷 반복기의 형식입니다.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>설명

형식은 버킷의 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 구현 정의 형식에 대 한 동의어로 여기에 설명 되어 `T4` 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="max_bucket_count"></a><a name="max_bucket_count"></a> max_bucket_count

최대 버킷 개수를 가져옵니다.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>설명

멤버 함수는 현재 허용된 최대 버킷 개수를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="max_load_factor"></a><a name="max_load_factor"></a> max_load_factor

버킷당 최대 요소 수를 가져오거나 설정합니다.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>매개 변수

*이용한*\
새로운 최대 로드 비율입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 저장된 최대 로드 비율을 반환합니다. 두 번째 멤버 함수는 저장 된 최대 로드 비율을 *인수로*바꿉니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="max_size"></a><a name="max_size"></a> max_size

제어되는 시퀀스의 최대 크기를 가져옵니다.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 개체가 제어할 수 있는 가장 긴 시퀀스의 길이를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

해시 테이블을 복사합니다.

```cpp
unordered_set& operator=(const unordered_set& right);

unordered_set& operator=(unordered_set&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
로 복사 되는 [unordered_set](../standard-library/unordered-set-class.md) `unordered_set` 입니다.

### <a name="remarks"></a>설명

에서 기존 요소를 지운 후에 `unordered_set` 는 `operator=` 의 내용을로 복사 하거나 이동 *right* `unordered_set` 합니다.

### <a name="example"></a>예제

```cpp
// unordered_set_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_set<int> v1, v2, v3;
    unordered_set<int>::iterator iter;

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

요소에 대한 포인터의 형식입니다.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 포인터로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="reference"></a><a name="reference"></a> 참조일

요소에 대한 참조의 형식입니다.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 요소에 대한 참조로 사용될 수 있는 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="rehash"></a><a name="rehash"></a> rehash

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
// std__unordered_set__unordered_set_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="size"></a><a name="size"></a> 크기가

요소 수를 계산합니다.

```cpp
size_type size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="size_type"></a><a name="size_type"></a> size_type

두 요소 사이의 부호가 없는 거리의 형식입니다.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>설명

부호 없는 정수 형식은 제어되는 시퀀스의 길이를 나타낼 수 있는 개체를 설명합니다. 구현 정의 형식에 대 한 동의어로 여기에 설명 되어 `T2` 있습니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 컨테이너의 내용을 바꿉니다.

```cpp
void swap(unordered_set& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`*this`** 과 *오른쪽*으로 바꿉니다. [Unordered_set:: get_allocator](#get_allocator) `() == right.get_allocator()` 는 일정 한 시간에이 작업을 수행 하 고, 형식의 저장 된 특성 개체를 복사 하는 경우에만 예외를 throw 하 `Tr` 고, 두 개의 제어 된 시퀀스에서 요소를 지정 하는 참조, 포인터 또는 반복기를 무효화 하지 않습니다. 그렇지 않으면 두 개의 제어되는 시퀀스에 있는 요소 수에 비례하여 많은 요소 할당 및 생성자 호출을 수행합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents "[f] [e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="unordered_set"></a><a name="unordered_set"></a> unordered_set

컨테이너 개체를 만듭니다.

```cpp
unordered_set(const unordered_set& Right);

explicit unordered_set(
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_set(unordered_set&& Right);

unordered_set(initializer_list<Type> IList);

unordered_set(initializer_list<Type> IList, size_typebucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp,
    const Allocator& Al);

template <class InputIterator>
unordered_set(
    InputIteratorfirst,
    InputIteratorlast,
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>매개 변수

*InputIterator*\
반복기 형식입니다.

*항상*\
저장할 할당자 개체입니다.

*생략*\
저장할 비교 함수 개체입니다.

*해시로*\
저장할 해시 함수 개체입니다.

*bucket_count*\
최소 버킷 수입니다.

*오른쪽*\
복사할 컨테이너입니다.

*IList*\
복사할 요소를 포함하는 initializer_list입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 *Right*로 제어 되는 시퀀스의 복사본을 지정 합니다. 두 번째 생성자는 빈 제어 시퀀스를 지정합니다. 세 번째 생성자는 *오른쪽* 에서 여덟 번째까지 이동 하 여 시퀀스의 복사본을 지정 합니다 .이 생성자는 initializer_list를 사용 하 여 복사할 요소를 지정 합니다. 아홉 번째 생성자는 `[first, last)` 요소 값의 시퀀스를 삽입합니다.

모든 생성자는 또한 여러 개의 저장된 값을 초기화합니다. 복사 생성자의 경우 값은 *오른쪽*에서 가져옵니다. 그렇지 않은 경우:

버킷 최소 수는 인수 *bucket_count*(있는 경우)입니다. 그렇지 않으면 여기에 구현 정의 값으로 설명 된 기본값 `N0` 입니다.

해시 함수 개체는 인수 *해시*(있는 경우)입니다. 그렇지 않으면 `Hash()` 입니다.

비교 함수 개체는 인수 *Comp*(있는 경우)입니다. 그렇지 않으면 `Comp()` 입니다.

할당자 개체는 *Al*인수입니다 (있는 경우). 그렇지 않으면 `Alloc()` 입니다.

## <a name="value_type"></a><a name="value_type"></a> value_type

요소의 형식입니다.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>설명

형식은 제어되는 시퀀스의 요소를 설명합니다.

### <a name="example"></a>예제

```cpp
// std__unordered_set__unordered_set_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```
