---
title: hash_multiset(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
ms.openlocfilehash: b5aae5830437309e95f808567a2d3a7ea093c8f8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507158"
---
# <a name="hash_multiset-stlclr"></a>hash_multiset(STL/CLR)

이 템플릿 클래스는 양방향 액세스를 포함 하는 다양 한 길이의 요소 시퀀스를 제어 하는 개체를 설명 합니다. 컨테이너를 사용 하 여 `hash_multiset` 일련의 요소를 해시 테이블로 관리 하 고, 각 테이블 항목은 양방향으로 연결 된 노드 목록을 저장 하며 각 노드는 하나의 요소를 저장 합니다. 각 요소의 값은 시퀀스를 정렬 하기 위해 키로 사용 됩니다.

아래 설명에서는 `GValue` 와 동일 합니다 .이 `GKey` 경우 후자가 참조 형식이 아니면 *키* 와 동일 합니다 `Key^` .

## <a name="syntax"></a>구문

```cpp
template<typename Key>
    ref class hash_multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>매개 변수

*Key*<br/>
제어되는 시퀀스에 있는 요소의 키 구성 요소 형식입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/hash_set>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|형식 정의|설명|
|---------------------|-----------------|
|[hash_multiset::const_iterator(STL/CLR)](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[hash_multiset::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[hash_multiset::const_reverse_iterator(STL/CLR)](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|
|[hash_multiset::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 (부호가 있을 수 있는) 거리의 형식입니다.|
|[hash_multiset::generic_container(STL/CLR)](#generic_container)|컨테이너에 대 한 제네릭 인터페이스의 형식입니다.|
|[hash_multiset::generic_iterator(STL/CLR)](#generic_iterator)|컨테이너의 제네릭 인터페이스에 대 한 반복기의 형식입니다.|
|[hash_multiset::generic_reverse_iterator(STL/CLR)](#generic_reverse_iterator)|컨테이너의 제네릭 인터페이스에 대 한 역방향 반복기의 형식입니다.|
|[hash_multiset::generic_value(STL/CLR)](#generic_value)|컨테이너의 제네릭 인터페이스에 대 한 요소의 형식입니다.|
|[hash_multiset::hasher(STL/CLR)](#hasher)|키에 대 한 해싱 대리자입니다.|
|[hash_multiset::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[hash_multiset::key_compare(STL/CLR)](#key_compare)|두 키에 대 한 순서 지정 대리자입니다.|
|[hash_multiset::key_type(STL/CLR)](#key_type)|정렬 키의 형식입니다.|
|[hash_multiset::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|
|[hash_multiset::reverse_iterator(STL/CLR)](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|
|[hash_multiset::size_type(STL/CLR)](#size_type)|두 요소 사이의 (음수가 아닌) 거리의 형식입니다.|
|[hash_multiset::value_compare(STL/CLR)](#value_compare)|두 요소 값에 대 한 순서 지정 대리자입니다.|
|[hash_multiset::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[hash_multiset::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[hash_multiset::bucket_count(STL/CLR)](#bucket_count)|버킷 수를 계산 합니다.|
|[hash_multiset::clear(STL/CLR)](#clear)|모든 요소를 제거합니다.|
|[hash_multiset::count(STL/CLR)](#count)|지정 된 키와 일치 하는 요소 수를 셉니다.|
|[hash_multiset::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|
|[hash_multiset::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[hash_multiset::equal_range(STL/CLR)](#equal_range)|지정된 키와 일치하는 범위를 찾습니다.|
|[hash_multiset::erase(STL/CLR)](#erase)|지정된 위치에 있는 요소를 제거합니다.|
|[hash_multiset::find(STL/CLR)](#find)|지정된 키와 일치하는 요소를 찾습니다.|
|[hash_multiset::hash_delegate(STL/CLR)](#hash_delegate)|키에 대 한 해싱 대리자를 복사 합니다.|
|[hash_multiset::hash_multiset(STL/CLR)](#hash_multiset)|컨테이너 개체를 만듭니다.|
|[hash_multiset::insert(STL/CLR)](#insert)|요소를 추가합니다.|
|[hash_multiset::key_comp(STL/CLR)](#key_comp)|두 키에 대 한 순서 지정 대리자를 복사 합니다.|
|[hash_multiset::load_factor(STL/CLR)](#load_factor)|버킷당 평균 요소 수를 계산합니다.|
|[hash_multiset::lower_bound(STL/CLR)](#lower_bound)|지정 된 키와 일치 하는 범위의 시작 부분을 찾습니다.|
|[hash_multiset::make_value(STL/CLR)](#make_value)|값 개체를 생성 합니다.|
|[hash_multiset::max_load_factor(STL/CLR)](#max_load_factor)|버킷당 최대 요소 수를 가져오거나 설정합니다.|
|[hash_multiset::rbegin(STL/CLR)](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|
|[hash_multiset::rehash(STL/CLR)](#rehash)|해시 테이블을 다시 빌드합니다.|
|[hash_multiset::rend(STL/CLR)](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|
|[hash_multiset::size(STL/CLR)](#size)|요소 수를 계산합니다.|
|[hash_multiset::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|
|[hash_multiset::to_array(STL/CLR)](#to_array)|제어 되는 시퀀스를 새 배열에 복사 합니다.|
|[hash_multiset::upper_bound(STL/CLR)](#upper_bound)|지정 된 키와 일치 하는 범위의 끝을 찾습니다.|
|[hash_multiset::value_comp(STL/CLR)](#value_comp)|두 요소 값에 대 한 순서 지정 대리자를 복사 합니다.|

|연산자|설명|
|--------------|-----------------|
|[hash_multiset::operator=(STL/CLR)](#op)|제어되는 시퀀스를 바꿉니다.|

## <a name="interfaces"></a>인터페이스

|인터페이스|설명|
|---------------|-----------------|
|<xref:System.ICloneable>|개체를 복제 합니다.|
|<xref:System.Collections.IEnumerable>|요소를 순서 대로 이동 합니다.|
|<xref:System.Collections.ICollection>|요소 그룹을 유지 관리 합니다.|
|<xref:System.Collections.Generic.IEnumerable%601>|형식화 된 요소를 통해 시퀀싱 합니다.|
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 관리 합니다.|
|IHash\<Key, Value>|일반 컨테이너를 유지 관리 합니다.|

## <a name="remarks"></a>설명

개체는 양방향 연결 목록에서 개별 노드로 제어 되는 시퀀스에 대 한 저장소를 할당 하 고 해제 합니다. 액세스 속도를 높이기 위해 개체는 목록 (해시 테이블)에 다양 한 길이의 포인터 배열을 유지 관리 하므로 전체 목록을 sublists의 시퀀스로 효과적으로 관리할 수 있습니다. 노드 간에 링크를 변경 하 여 유지 하는 버킷에 요소를 삽입 합니다. 즉, 노드 내용을 다른 노드로 복사 하지 않습니다. 즉, 나머지 요소를 방해 하지 않고 요소를 자유롭게 삽입 하 고 제거할 수 있습니다.

개체는 [hash_set:: key_compare (STL/CLR)](./hash-set-stl-clr.md#key_compare)형식의 저장 된 대리자 개체를 호출 하 여 제어 하는 각 버킷을 정렬 합니다. Hash_set를 생성할 때 저장 된 대리자 개체를 지정할 수 있습니다. 대리자 개체를 지정 하지 않으면 기본값은 비교입니다 `operator<=(key_type, key_type)` .

[Hash_set:: key_comp (STL/CLR)](./hash-set-stl-clr.md#key_comp)멤버 함수를 호출 하 여 저장 된 대리자 개체에 액세스 `()` 합니다. 이러한 대리자 개체는 [hash_set:: key_type (STL/CLR)](./hash-set-stl-clr.md#key_type)형식의 키 사이에 동일한 순서를 정의 해야 합니다. 즉, 다음과 같은 두 가지 키 `X` 가 `Y` 있습니다.

`key_comp()(X, Y)` 모든 호출에 대해 동일한 부울 결과를 반환 합니다.

`key_comp()(X, Y) && key_comp()(Y, X)`가 true 이면 `X` 및 `Y` 는 동일한 순서를 갖는 것으로 간주 됩니다.

처럼 동작 `operator<=(key_type, key_type)` `operator>=(key_type, key_type)` 하거나 `operator==(key_type, key_type)` eqivalent 정렬을 정의 하는 순서 지정 규칙입니다.

컨테이너는 키의 순서를 지정 하는 요소 (및 동일한 정수 값에 대 한 해시)가 버킷 내에 인접해 있는지 확인 합니다. 템플릿 클래스 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)와 달리 템플릿 클래스의 개체는 `hash_multiset` 모든 요소에 대 한 키가 고유 하지 않아도 됩니다. 두 개 이상의 키가 동일한 정렬을 가질 수 있습니다.

개체는 [hash_set:: hasher (STL/CLR)](./hash-set-stl-clr.md#hasher)형식의 저장 된 대리자 개체를 호출 하 여 지정 된 순서 지정 키를 포함할 버킷을 결정 합니다. 이 저장 된 개체는 멤버 함수 [hash_set:: hash_delegate (STL/CLR)](./hash-set-stl-clr.md#hash_delegate) 를 호출 `()` 하 여 키 값에 따라 달라 지는 정수 값을 가져오는 방식으로 액세스 합니다. Hash_set를 생성할 때 저장 된 대리자 개체를 지정할 수 있습니다. 대리자 개체를 지정 하지 않으면 기본값은 함수 `System::Object::hash_value(key_type)` 입니다. 즉, 모든 키 및에 `X` 대해 `Y` 다음을 수행 합니다.

`hash_delegate()(X)` 모든 호출에서 동일한 정수 결과를 반환 합니다.

`X`및의 순서가 동일한 경우는 `Y` `hash_delegate()(X)` 와 동일한 정수 결과를 반환 해야 합니다 `hash_delegate()(Y)` .

각 요소는 키와 값으로 사용 됩니다. 시퀀스는 시퀀스의 요소 수 (일정 한 시간)에 관계 없이 대부분의 작업을 사용 하 여 임의 요소를 조회, 삽입 및 제거할 수 있도록 하는 방식으로 표현 됩니다. 또한, 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 가리키고 있는 반복기만 무효화됩니다.

그러나 해시 된 값이 균일 하 게 분산 되지 않은 경우 해시 테이블이 중복 제거 될 수 있습니다. 극단적인 경우--항상 동일한 값을 반환 하는 해시 함수의 경우 (조회, 삽입 및 제거) 시퀀스의 요소 수에 비례 합니다 (선형 시간). 컨테이너는 적절 한 해시 함수, 평균 버킷 크기 및 해시 테이블 크기 (총 버킷 수)를 선택 하는 것을 시도한 이러한 선택 항목의 일부 또는 전부를 재정의할 수 있습니다. 예를 들어 [hash_set:: max_load_factor (stl/clr)](./hash-set-stl-clr.md#max_load_factor) 및 [hash_set:: rehash (stl/clr)](./hash-set-stl-clr.md#rehash)함수를 참조 하세요.

Hash_multiset은 양방향 반복기를 지원 합니다. 즉, 제어 되는 시퀀스에서 요소를 지정 하는 반복기를 사용 하 여 인접 한 요소를 한 단계씩 실행 할 수 있습니다. 특수 헤드 노드는 [hash_multiset:: end (STL/CLR)](#end)에서 반환 된 반복기에 해당 `()` 합니다. 제어 되는 시퀀스의 마지막 요소 (있는 경우)에 도달할 때까지이 반복기를 줄일 수 있습니다. Hash_multiset iterator를 증가 시켜 헤드 노드에 도달할 수 있습니다. 그런 다음와 비교 `end()` 합니다. 그러나에서 반환 된 반복기는 역 참조할 수 없습니다 `end()` .

임의 액세스 반복기를 필요로 하는 숫자 위치를 지정 하 여 hash_multiset 요소를 직접 참조할 수 없습니다.

Hash_multiset 반복기는 연결 된 hash_multiset 노드에 대 한 핸들을 저장 합니다. 그러면 연결 된 컨테이너에 대 한 핸들을 저장 합니다. 반복기는 연결 된 컨테이너 개체에만 사용할 수 있습니다. 연결 된 hash_multiset 노드가 일부 hash_multiset와 연결 되어 있으면 hash_multiset 반복기는 유효한 상태로 유지 됩니다. 또한 유효한 반복기는 dereferencable입니다 .이 반복기를 사용 하 여 지정 된 요소 값을 액세스 하거나 변경할 수 있습니다 .이는와 같지 않은 경우 `end()` 입니다.

요소를 지우거 나 제거 하면 저장 된 값에 대 한 소멸자가 호출 됩니다. 컨테이너를 삭제 하면 모든 요소가 지워집니다. 따라서 요소 형식이 ref 클래스 인 컨테이너는 컨테이너의 활성 요소가 없도록 합니다. 그러나 핸들의 컨테이너는 해당 요소 *를 소멸 시 키 지 않습니다.*

## <a name="members"></a>멤버

## <a name="hash_multisetbegin-stlclr"></a><a name="begin"></a> hash_multiset:: begin (STL/CLR)

제어되는 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator begin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 첫 번째 요소 또는 빈 시퀀스의 끝 바로 뒤를 지정 하는 양방향 반복기를 반환 합니다. 이를 통해 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="hash_multisetbucket_count-stlclr"></a><a name="bucket_count"></a> hash_multiset:: bucket_count (STL/CLR)

버킷 수를 계산 합니다.

### <a name="syntax"></a>구문

```cpp
int bucket_count();
```

### <a name="remarks"></a>설명

멤버 함수는 현재 버킷 수를 반환 합니다. 해시 테이블의 크기를 결정 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetclear-stlclr"></a><a name="clear"></a> hash_multiset:: clear (STL/CLR)

모든 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
void clear();
```

### <a name="remarks"></a>설명

멤버 함수는 [hash_multiset:: erase (stl/clr)](#erase) `(` [hash_multiset:: begin (stl/clr)](#begin) `(),` [hash_multiset:: end (stl/clr)](#end)를 효과적으로 호출 합니다 `())` . 이를 사용 하 여 제어 되는 시퀀스가 비어 있는지 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="hash_multisetconst_iterator-stlclr"></a><a name="const_iterator"></a> hash_multiset:: const_iterator (STL/CLR)

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>설명

`T2`이 형식은 제어 되는 시퀀스에 대 한 상수 양방향 반복기로 사용할 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reference-stlclr"></a><a name="const_reference"></a> hash_multiset:: const_reference (STL/CLR)

요소에 대한 상수 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>설명

요소에 대 한 상수 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_multiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> hash_multiset:: const_reverse_iterator (STL/CLR)

제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>설명

`T4`이 형식은 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetcount-stlclr"></a><a name="count"></a> hash_multiset:: count (STL/CLR)

지정한 키와 일치하는 요소의 수를 찾습니다.

### <a name="syntax"></a>구문

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스에서 *키*와 동일한 정렬을 사용 하는 요소의 수를 반환 합니다. 이를 통해 현재 제어되는 시퀀스에 있는 요소 중 지정된 키와 일치하는 요소의 수를 확인할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="hash_multisetdifference_type-stlclr"></a><a name="difference_type"></a> hash_multiset::d ifference_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>설명

이 형식은 음수 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::difference_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="hash_multisetempty-stlclr"></a><a name="empty"></a> hash_multiset:: empty (STL/CLR)

요소가 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
bool empty();
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. [Hash_multiset:: size (STL/CLR)](#size)와 동일 `() == 0` 합니다. 이를 사용 하 여 hash_multiset 비어 있는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="hash_multisetend-stlclr"></a><a name="end"></a> hash_multiset:: end (STL/CLR)

제어되는 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator end();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 끝 바로 다음을 가리키는 양방향 반복기를 반환 합니다. 이를 사용 하 여 제어 되는 시퀀스의 끝을 지정 하는 반복기를 가져옵니다. 제어 되는 시퀀스의 길이가 변경 되 면 해당 상태는 변경 되지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_multiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="hash_multisetequal_range-stlclr"></a><a name="equal_range"></a> hash_multiset:: equal_range (STL/CLR)

지정된 키와 일치하는 범위를 찾습니다.

### <a name="syntax"></a>구문

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수 `cliext::pair<iterator, iterator>(` [hash_multiset:: lower_bound (stl/clr)](#lower_bound) `(key),` [hash_multiset:: upper_bound (stl/clr)](#upper_bound)쌍의 반복기를 반환 합니다 `(key))` . 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소의 범위를 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
typedef Myhash_multiset::pair_iter_iter Pairii;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="hash_multiseterase-stlclr"></a><a name="erase"></a> hash_multiset:: erase (STL/CLR)

지정된 위치에 있는 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
지울 범위의 시작입니다.

*key*<br/>
지울 키 값입니다.

*last*<br/>
지울 범위의 끝입니다.

*where*<br/>
지울 요소입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 where가 가리키는 제어 *되*는 시퀀스의 요소를 제거 하 고, 요소가 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, 이러한 요소가 없는 경우 [hash_multiset:: end (STL/CLR)](#end) 를 반환 합니다 `()` . 단일 요소를 제거 하는 데 사용 합니다.

두 번째 멤버 함수는 [,) 범위에서 제어 되는 시퀀스의 요소를 제거 `first` `last` 하 고, 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, `end()` 이러한 요소가 없는 경우을 반환 합니다. 연속 된 요소를 0 개 이상 제거 하는 데 사용 합니다.

세 번째 멤버 함수는 키가 *키*와 동일한 순서를 갖는 제어 되는 시퀀스의 요소를 제거 하 고 제거 된 요소 수의 개수를 반환 합니다. 이를 사용 하 여 지정 된 키와 일치 하는 모든 요소를 제거 하 고 개수를 계산 합니다.

각 요소를 지울 때마다 제어 되는 시퀀스의 요소 수에 대 한 로그에 비례 하는 시간이 사용 됩니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Myhash_multiset::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="hash_multisetfind-stlclr"></a><a name="find"></a> hash_multiset:: find (STL/CLR)

지정된 키와 일치하는 요소를 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

제어 되는 시퀀스의 요소 중 하나 이상이 *key*와 동일한 정렬을 사용 하는 경우 멤버 함수는 이러한 요소 중 하나를 지정 하는 반복기를 반환 합니다. 그렇지 않으면 [hash_multiset:: end (STL/CLR)](#end)를 반환 `()` 합니다. 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소를 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="hash_multisetgeneric_container-stlclr"></a><a name="generic_container"></a> hash_multiset:: generic_container (STL/CLR)

컨테이너에 대 한 제네릭 인터페이스의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>설명

이 템플릿 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="hash_multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> hash_multiset:: generic_iterator (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>설명

형식은이 템플릿 컨테이너 클래스의 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 반복기를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> hash_multiset:: generic_reverse_iterator (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 역방향 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>설명

형식은이 템플릿 컨테이너 클래스의 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 역방향 반복기를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="hash_multisetgeneric_value-stlclr"></a><a name="generic_value"></a> hash_multiset:: generic_value (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>설명

`GValue`이 템플릿 컨테이너 클래스의 제네릭 인터페이스에 사용할 저장 된 요소 값을 설명 하는 형식의 개체를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisethash_delegate-stlclr"></a><a name="hash_delegate"></a> hash_multiset:: hash_delegate (STL/CLR)

지정된 키와 일치하는 요소를 찾습니다.

### <a name="syntax"></a>구문

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>설명

멤버 함수는 키 값을 정수로 변환 하는 데 사용 되는 대리자를 반환 합니다. 키를 해시 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisethash_multiset-stlclr"></a><a name="hash_multiset"></a> hash_multiset:: hash_multiset (STL/CLR)

컨테이너 개체를 만듭니다.

### <a name="syntax"></a>구문

```cpp
hash_multiset();
explicit hash_multiset(key_compare^ pred);
hash_multiset(key_compare^ pred, hasher^ hashfn);
hash_multiset(hash_multiset<Key>% right);
hash_multiset(hash_multiset<Key>^ right);
template<typename InIter>
    hash_multiset(InIter first, InIter last);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
삽입할 범위의 시작입니다.

*hashfn*<br/>
키를 버킷으로 매핑하기 위한 해시 함수입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*pred*<br/>
제어 되는 시퀀스의 순서 조건자입니다.

*오른쪽*<br/>
삽입할 개체 또는 범위입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`hash_multiset();`

기본 순서 조건자와 기본 해시 함수를 사용 하 여 요소 없이 제어 되는 시퀀스를 초기화 `key_compare()` 합니다. 이를 사용 하 여 기본 순서 조건자와 해시 함수를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`explicit hash_multiset(key_compare^ pred);`

순서 조건자 *pred*및 기본 해시 함수를 사용 하 여 요소 없이 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 지정 된 순서 조건자와 기본 해시 함수를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`hash_multiset(key_compare^ pred, hasher^ hashfn);`

순서 조건자 *pred*및 해시 함수 *hashfn*을 사용 하 여 요소 없이 제어 되는 시퀀스를 초기화 합니다. 지정 된 순서 조건자와 해시 함수를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

생성자는 다음과 같습니다.

`hash_multiset(hash_multiset<Key>% right);`

`right.begin()` `right.end()` 기본 순서 조건자와 기본 해시 함수를 사용 하 여 시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 기본 순서 조건자와 해시 함수를 사용 하 여 hash_multiset 개체 *오른쪽*에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`hash_multiset(hash_multiset<Key>^ right);`

`right->begin()` `right->end()` 기본 순서 조건자와 기본 해시 함수를 사용 하 여 시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 기본 순서 조건자와 해시 함수를 사용 하 여 hash_multiset 개체 *오른쪽*에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`template<typename InIter> hash_multiset(InIter first, InIter last);`

`first` `last` 기본 순서 조건자와 기본 해시 함수를 사용 하 여 시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 기본 순서 조건자와 해시 함수를 사용 하 여 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`

순서 `first` `last` 조건자 *pred*및 기본 해시 함수를 사용 하 여 시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 지정 된 순서 조건자와 기본 해시 함수를 사용 하 여 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

시퀀스 [ `first` , `last` ), 순서 조건자 *pred*및 해시 함수 *hashfn*을 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 지정 된 순서 조건자와 해시 함수를 사용 하 여 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

기본 순서 조건자와 기본 해시 함수를 사용 하 여 열거자 *오른쪽*에 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명 하는 다른 시퀀스의 복사본으로 만들고 기본 순서 조건자와 해시 함수를 사용 합니다.

생성자는 다음과 같습니다.

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

정렬 조건자 *pred*및 기본 해시 함수를 사용 하 여 열거자 *권한*으로 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 지정 된 순서 조건자와 기본 해시 함수를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명한 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

순서 조건자 *pred*및 해시 함수 *hashfn*을 사용 하 여 열거자 *오른쪽*으로 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 지정 된 순서 조건자와 해시 함수를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명한 다른 시퀀스의 복사본으로 만듭니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
// construct an empty container
    Myhash_multiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_multiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_multiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_multiset c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_multiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_multiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_multiset c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_multiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_multiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hash_multisethasher-stlclr"></a><a name="hasher"></a> hash_multiset:: hasher (STL/CLR)

키에 대 한 해싱 대리자입니다.

### <a name="syntax"></a>구문

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>설명

형식은 키 값을 정수로 변환 하는 대리자를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisetinsert-stlclr"></a><a name="insert"></a> hash_multiset:: insert (STL/CLR)

요소를 추가합니다.

### <a name="syntax"></a>구문

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*오른쪽*<br/>
삽입할 열거형입니다.

*짧은*<br/>
삽입할 키 값입니다.

*where*<br/>
컨테이너에서 삽입할 위치 (힌트 전용)입니다.

### <a name="remarks"></a>설명

각 멤버 함수는 나머지 피연산자로 지정 된 시퀀스를 삽입 합니다.

첫 번째 멤버 함수는 값 *val*을 사용 하 여 요소를 삽입 하 고 새로 삽입 된 요소를 지정 하는 반복기를 반환 합니다. 단일 요소를 삽입 하는 데 사용 합니다.

두 번째 멤버 함수는 값이 *val*인 요소를 삽입 하 여 (성능을 향상 시키기 위해 *)를 힌트로 사용 하* 고, 새로 삽입 된 요소를 지정 하는 반복기를 반환 합니다. 이를 사용 하 여 사용자가 알고 있는 요소에 인접 한 단일 요소를 삽입할 수 있습니다.

세 번째 멤버 함수는 [,) 시퀀스를 삽입 합니다 `first` `last` . 이를 사용 하 여 다른 시퀀스에서 복사 되는 0 개 이상의 요소를 삽입 합니다.

네 번째 멤버 함수는 *오른쪽*에 지정 된 시퀀스를 삽입 합니다. 이를 사용 하 여 열거자에서 설명 하는 시퀀스를 삽입 합니다.

각 요소 삽입에는 제어 되는 시퀀스의 요소 수에 대 한 로그에 비례 하는 시간이 소요 됩니다. 그러나 삽입 지점 옆의 요소를 지정 하는 힌트가 지정 된 경우에는 분할 상환 상수 시간에 삽입이 발생할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_multiset c2;
    Myhash_multiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_multiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="hash_multisetiterator-stlclr"></a><a name="iterator"></a> hash_multiset:: iterator (STL/CLR)

제어되는 시퀀스에 대한 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>설명

`T1`이 형식은 제어 되는 시퀀스에 대 한 양방향 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetkey_comp-stlclr"></a><a name="key_comp"></a> hash_multiset:: key_comp (STL/CLR)

두 키에 대 한 순서 지정 대리자를 복사 합니다.

### <a name="syntax"></a>구문

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 순서 지정 대리자를 반환 합니다. 이를 통해 두 키를 비교할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_compare-stlclr"></a><a name="key_compare"></a> hash_multiset:: key_compare (STL/CLR)

두 키에 대 한 순서 지정 대리자입니다.

### <a name="syntax"></a>구문

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>설명

형식은 해당 키 인수의 순서를 결정 하는 대리자의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_type-stlclr"></a><a name="key_type"></a> hash_multiset:: key_type (STL/CLR)

정렬 키의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *키*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_multiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetload_factor-stlclr"></a><a name="load_factor"></a> hash_multiset:: load_factor (STL/CLR)

버킷당 평균 요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
float load_factor();
```

### <a name="remarks"></a>설명

멤버 함수는 `(float)` [hash_multiset:: size (stl/clr)](#size) `() /` [hash_multiset:: bucket_count (stl/clr)](#count)을 반환 합니다 `()` . 이를 사용 하 여 평균 버킷 크기를 결정 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetlower_bound-stlclr"></a><a name="lower_bound"></a> hash_multiset:: lower_bound (STL/CLR)

지정 된 키와 일치 하는 범위의 시작 부분을 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` 제어 되는 시퀀스에서 *키* 로 동일한 버킷으로 해시 하 고 *키*와 동일한 순서를 갖는 첫 번째 요소를 확인 합니다. 이러한 요소가 없는 경우 [hash_multiset:: end (STL/CLR)](#end)를 반환 하 `()` 고, 그렇지 않으면를 지정 하는 반복기를 반환 `X` 합니다. 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소 시퀀스의 시작 부분을 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="hash_multisetmake_value-stlclr"></a><a name="make_value"></a> hash_multiset:: make_value (STL/CLR)

값 개체를 생성 합니다.

### <a name="syntax"></a>구문

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
사용할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 키 `value_type` 가 *키*인 개체를 반환 합니다. 이를 사용 하 여 다른 여러 멤버 함수에서 사용 하기에 적합 한 개체를 작성 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(Myhash_multiset::make_value(L'a'));
    c1.insert(Myhash_multiset::make_value(L'b'));
    c1.insert(Myhash_multiset::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetmax_load_factor-stlclr"></a><a name="max_load_factor"></a> hash_multiset:: max_load_factor (STL/CLR)

버킷당 최대 요소 수를 가져오거나 설정합니다.

### <a name="syntax"></a>구문

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>매개 변수

*new_factor*<br/>
저장할 새 최대 로드 비율입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 현재 저장 된 최대 로드 비율을 반환 합니다. 이를 사용 하 여 최대 평균 버킷 크기를 결정 합니다.

두 번째 멤버 함수는 저장소 최대 로드 비율을 *new_factor*으로 바꿉니다. 이후에 삽입 될 때까지 자동 rehashing 발생 하지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetoperator-stlclr"></a><a name="op"></a> hash_multiset:: operator = (STL/CLR)

제어되는 시퀀스를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
hash_multiset<Key>% operator=(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 제어 되는 시퀀스를 *오른쪽*에 있는 제어 되는 시퀀스의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_multiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_multiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="hash_multisetrbegin-stlclr"></a><a name="rbegin"></a> hash_multiset:: rbegin (STL/CLR)

제어되는 역방향 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 마지막 요소 또는 빈 시퀀스의 시작 부분 바로 뒤를 지정 하는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `beginning`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="hash_multisetreference-stlclr"></a><a name="reference"></a> hash_multiset:: reference (STL/CLR)

요소에 대한 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>설명

요소에 대 한 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_multiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetrehash-stlclr"></a><a name="rehash"></a> hash_multiset:: rehash (STL/CLR)

해시 테이블을 다시 빌드합니다.

### <a name="syntax"></a>구문

```cpp
void rehash();
```

### <a name="remarks"></a>설명

멤버 함수는 해시 테이블을 다시 작성 하 여 [hash_multiset:: load_factor (stl/clr)](#load_factor) `() <=` [hash_multiset:: max_load_factor (stl/clr)](#max_load_factor)를 확인 합니다. 그렇지 않으면 해시 테이블의 크기는 삽입 후 필요에 따라 커집니다. (크기가 자동으로 감소 하지 않습니다.) 이를 사용 하 여 해시 테이블의 크기를 조정 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetrend-stlclr"></a><a name="rend"></a> hash_multiset:: rend (STL/CLR)

제어되는 역방향 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 시작 부분 바로 뒤를 가리키는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `end`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 끝을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="hash_multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> hash_multiset:: reverse_iterator (STL/CLR)

제어되는 시퀀스에 대한 반대 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetsize-stlclr"></a><a name="size"></a> hash_multiset:: size (STL/CLR)

요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
size_type size();
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 이를 사용 하 여 현재 제어 되는 시퀀스에 있는 요소 수를 확인 합니다. 시퀀스의 크기가 0이 아니면 [hash_multiset:: empty (STL/CLR)](#empty)를 참조 하세요 `()` .

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="hash_multisetsize_type-stlclr"></a><a name="size_type"></a> hash_multiset:: size_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int size_type;
```

### <a name="remarks"></a>설명

이 형식은 음수가 아닌 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::size_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="hash_multisetswap-stlclr"></a><a name="swap"></a> hash_multiset:: swap (STL/CLR)

두 컨테이너의 내용을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void swap(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
콘텐츠와 바꿀 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`this`** 과 *오른쪽*으로 바꿉니다. 일정 한 시간에이를 수행 하 고 예외를 throw 하지 않습니다. 이를 사용 하 여 두 컨테이너의 콘텐츠를 신속 하 게 교환할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_multiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
d e f
d e f
a b c
```

## <a name="hash_multisetto_array-stlclr"></a><a name="to_array"></a> hash_multiset:: to_array (STL/CLR)

제어 되는 시퀀스를 새 배열에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 이를 사용 하 여 배열 형식으로 제어 되는 시퀀스의 복사본을 가져옵니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="hash_multisetupper_bound-stlclr"></a><a name="upper_bound"></a> hash_multiset:: upper_bound (STL/CLR)

지정 된 키와 일치 하는 범위의 끝을 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` 제어 되는 시퀀스에서 *키* 로 동일한 버킷으로 해시 하 고 *키*와 동일한 순서를 갖는 마지막 요소를 확인 합니다. 이러한 요소가 없거나 `X` 가 제어 되는 시퀀스의 마지막 요소인 경우 [hash_multiset:: END (STL/CLR)](#end)를 반환 하 `()` 고, 그렇지 않은 경우에는 첫 번째 요소를 지정 하는 반복기를 반환 합니다 `X` . 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소 시퀀스의 끝을 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="hash_multisetvalue_comp-stlclr"></a><a name="value_comp"></a> hash_multiset:: value_comp (STL/CLR)

두 요소 값에 대 한 순서 지정 대리자를 복사 합니다.

### <a name="syntax"></a>구문

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 순서 지정 대리자를 반환 합니다. 두 요소 값을 비교 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_compare-stlclr"></a><a name="value_compare"></a> hash_multiset:: value_compare (STL/CLR)

두 요소 값에 대 한 순서 지정 대리자입니다.

### <a name="syntax"></a>구문

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>설명

이 형식은 해당 값 인수의 순서를 결정 하는 대리자의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_type-stlclr"></a><a name="value_type"></a> hash_multiset:: value_type (STL/CLR)

요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>설명

이 형식은 `generic_value`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_hash_multiset_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_multiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```
