---
title: multiset(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
- begin member [STL/CLR]
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
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
ms.openlocfilehash: a6bb7a262df21a835f1e870f2bce29480467c543
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508550"
---
# <a name="multiset-stlclr"></a>multiset(STL/CLR)

이 템플릿 클래스는 양방향 액세스를 포함 하는 다양 한 길이의 요소 시퀀스를 제어 하는 개체를 설명 합니다. 컨테이너를 사용 하 여 요소의 `multiset` 시퀀스를 (거의) 분산 된 노드 트리로 관리할 수 있습니다. 각 노드는 하나의 요소를 저장 합니다.

아래 설명에서는 `GValue` 와 동일 합니다 .이 `GKey` 경우 후자가 참조 형식이 아니면 *키* 와 동일 합니다 `Key^` .

## <a name="syntax"></a>구문

```cpp
template<typename Key>
    ref class multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>매개 변수

*Key*<br/>
제어되는 시퀀스에 있는 요소의 키 구성 요소 형식입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/set>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|형식 정의|설명|
|---------------------|-----------------|
|[multiset::const_iterator(STL/CLR)](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[multiset::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[multiset::const_reverse_iterator(STL/CLR)](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|
|[multiset::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 (부호가 있을 수 있는) 거리의 형식입니다.|
|[multiset::generic_container(STL/CLR)](#generic_container)|컨테이너에 대 한 제네릭 인터페이스의 형식입니다.|
|[multiset::generic_iterator(STL/CLR)](#generic_iterator)|컨테이너의 제네릭 인터페이스에 대 한 반복기의 형식입니다.|
|[multiset::generic_reverse_iterator(STL/CLR)](#generic_reverse_iterator)|컨테이너의 제네릭 인터페이스에 대 한 역방향 반복기의 형식입니다.|
|[multiset::generic_value(STL/CLR)](#generic_value)|컨테이너의 제네릭 인터페이스에 대 한 요소의 형식입니다.|
|[multiset::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[multiset::key_compare(STL/CLR)](#key_compare)|두 키에 대 한 순서 지정 대리자입니다.|
|[multiset::key_type(STL/CLR)](#key_type)|정렬 키의 형식입니다.|
|[multiset::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|
|[multiset::reverse_iterator(STL/CLR)](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|
|[multiset::size_type(STL/CLR)](#size_type)|두 요소 사이의 (음수가 아닌) 거리의 형식입니다.|
|[multiset::value_compare(STL/CLR)](#value_compare)|두 요소 값에 대 한 순서 지정 대리자입니다.|
|[multiset::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[multiset::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[multiset::clear(STL/CLR)](#clear)|모든 요소를 제거합니다.|
|[multiset::count(STL/CLR)](#count)|지정 된 키와 일치 하는 요소 수를 셉니다.|
|[multiset::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|
|[multiset::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[multiset::equal_range(STL/CLR)](#equal_range)|지정된 키와 일치하는 범위를 찾습니다.|
|[multiset::erase(STL/CLR)](#erase)|지정된 위치에 있는 요소를 제거합니다.|
|[multiset::find(STL/CLR)](#find)|지정된 키와 일치하는 요소를 찾습니다.|
|[multiset::insert(STL/CLR)](#insert)|요소를 추가합니다.|
|[multiset::key_comp(STL/CLR)](#key_comp)|두 키에 대 한 순서 지정 대리자를 복사 합니다.|
|[multiset::lower_bound(STL/CLR)](#lower_bound)|지정 된 키와 일치 하는 범위의 시작 부분을 찾습니다.|
|[multiset::make_value(STL/CLR)](#make_value)|값 개체를 생성 합니다.|
|[multiset::multiset(STL/CLR)](#multiset)|컨테이너 개체를 만듭니다.|
|[multiset::rbegin(STL/CLR)](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|
|[multiset::rend(STL/CLR)](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|
|[multiset::size(STL/CLR)](#size)|요소 수를 계산합니다.|
|[multiset::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|
|[multiset::to_array(STL/CLR)](#to_array)|제어 되는 시퀀스를 새 배열에 복사 합니다.|
|[multiset::upper_bound(STL/CLR)](#upper_bound)|지정 된 키와 일치 하는 범위의 끝을 찾습니다.|
|[multiset::value_comp(STL/CLR)](#value_comp)|두 요소 값에 대 한 순서 지정 대리자를 복사 합니다.|

|연산자|설명|
|--------------|-----------------|
|[multiset::operator=(STL/CLR)](#op_as)|제어되는 시퀀스를 바꿉니다.|
|[operator! = (multiset) (STL/CLR)](#op_neq)|`multiset`개체가 다른 개체와 다른 지 여부를 확인 `multiset` 합니다.|
|[연산자< (multiset) (STL/CLR)](#op_lt)|`multiset`개체가 다른 개체 보다 작거나 같은지 여부를 확인 `multiset` 합니다.|
|[연산자<= (multiset) (STL/CLR)](#op_lteq)|`multiset`개체가 다른 개체 보다 작거나 같은지 여부를 확인 `multiset` 합니다.|
|[operator = = (multiset) (STL/CLR)](#op_eq)|`multiset`개체가 다른 개체와 같은지 여부를 확인 `multiset` 합니다.|
|[연산자> (multiset) (STL/CLR)](#op_gt)|`multiset`개체가 다른 개체 보다 큰지 여부를 확인 `multiset` 합니다.|
|[operator>= (multiset)(STL/CLR)](#op_gteq)|`multiset`개체가 다른 개체 보다 크거나 같은지 여부를 확인 `multiset` 합니다.|

## <a name="interfaces"></a>인터페이스

|인터페이스|설명|
|---------------|-----------------|
|<xref:System.ICloneable>|개체를 복제 합니다.|
|<xref:System.Collections.IEnumerable>|요소를 순서 대로 이동 합니다.|
|<xref:System.Collections.ICollection>|요소 그룹을 유지 관리 합니다.|
|<xref:System.Collections.Generic.IEnumerable%601>|형식화 된 요소를 통해 시퀀싱 합니다.|
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 관리 합니다.|
|ITree\<Key, Value>|일반 컨테이너를 유지 관리 합니다.|

## <a name="remarks"></a>설명

개체는 개별 노드로 제어 되는 시퀀스에 대 한 저장소를 할당 하 고 해제 합니다. 노드 간에 링크를 변경 하 여 계속 정렬 된 (거의) 분산 된 트리에 요소를 삽입 합니다. 즉, 나머지 요소를 방해 하지 않고 요소를 자유롭게 삽입 하 고 제거할 수 있습니다.

개체는 multiset:: key_compare 형식의 저장 된 대리자 개체 [(STL/CLR)](#key_compare)를 호출 하 여 제어 하는 시퀀스를 정렬 합니다. Multiset를 생성할 때 저장 된 대리자 개체를 지정할 수 있습니다. 대리자 개체를 지정 하지 않으면 기본값은 비교입니다 `operator<(key_type, key_type)` . 이 저장 된 개체는 멤버 함수 [multiset:: key_comp (STL/CLR)](#key_comp)멤버 함수를 호출 하 여 액세스 `()` 합니다.

이러한 대리자 개체는 [multiset:: key_type (STL/CLR)](#key_type)형식의 키에 대해 엄격 하 고 약한 순서를 적용 해야 합니다. 즉, 다음과 같은 두 가지 키 `X` 가 `Y` 있습니다.

`key_comp()(X, Y)` 모든 호출에 대해 동일한 부울 결과를 반환 합니다.

`key_comp()(X, Y)`이 true 이면은 false 여야 합니다 `key_comp()(Y, X)` .

`key_comp()(X, Y)`이 true 이면 `X` 가 앞에 정렬 된 것입니다 `Y` .

`!key_comp()(X, Y) && !key_comp()(Y, X)`가 true 이면 `X` 및 `Y` 는 동일한 순서를 갖는 것으로 간주 됩니다.

제어 되는 `X` 시퀀스의 앞에 오는 모든 요소의 경우 `Y` `key_comp()(Y, X)` 는 false입니다. 기본 대리자 개체의 경우 키가 값을 감소 시 키 지 않습니다. 템플릿 클래스 [집합 (STL/CLR)](../dotnet/set-stl-clr.md)과 달리 템플릿 클래스의 개체는 `multiset` 모든 요소에 대 한 키가 고유 하지 않아도 됩니다. 두 개 이상의 키가 동일한 정렬을 가질 수 있습니다.

각 요소는 e 및 값으로 사용 됩니다. 시퀀스는 시퀀스의 요소 수에 대 한 로그 (로그 시간)에 비례 하는 여러 연산이 있는 임의 요소를 조회, 삽입 및 제거할 수 있도록 하는 방식으로 표현 됩니다. 또한, 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 가리키고 있는 반복기만 무효화됩니다.

Multiset는 양방향 반복기를 지원 합니다. 즉, 제어 되는 시퀀스에서 요소를 지정 하는 반복기를 사용 하 여 인접 한 요소를 한 단계씩 실행 할 수 있습니다. 특수 헤드 노드는 [multiset:: end (STL/CLR)](#end)에서 반환 된 반복기에 해당 `()` 합니다. 제어 되는 시퀀스의 마지막 요소 (있는 경우)에 도달할 때까지이 반복기를 줄일 수 있습니다. Multiset 반복기를 증가 시켜 헤드 노드에 도달할 수 있습니다. 그런 다음와 비교 `end()` 합니다. 그러나에서 반환 된 반복기는 역 참조할 수 없습니다 `end()` .

임의 액세스 반복기를 필요로 하는 숫자 위치를 지정 하면 multiset 요소를 직접 참조할 수 없습니다.

Multiset 반복기는 연결 된 multiset 노드에 대 한 핸들을 저장 합니다. 그러면 해당 핸들은 연결 된 컨테이너에 대 한 핸들을 저장 합니다. 반복기는 연결 된 컨테이너 개체에만 사용할 수 있습니다. Multiset 반복기는 연결 된 multiset 노드가 일부 multiset와 연결 된 경우에만 유효한 상태로 유지 됩니다. 또한 유효한 반복기는 dereferencable입니다 .이 반복기를 사용 하 여 지정 된 요소 값을 액세스 하거나 변경할 수 있습니다 .이는와 같지 않은 경우 `end()` 입니다.

요소를 지우거 나 제거 하면 저장 된 값에 대 한 소멸자가 호출 됩니다. 컨테이너를 삭제 하면 모든 요소가 지워집니다. 따라서 요소 형식이 ref 클래스 인 컨테이너는 컨테이너의 활성 요소가 없도록 합니다. 그러나 핸들의 컨테이너는 해당 요소 *를 소멸 시 키 지 않습니다.*

## <a name="members"></a>멤버

## <a name="multisetbegin-stlclr"></a><a name="begin"></a> multiset:: begin (STL/CLR)

제어되는 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator begin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 첫 번째 요소 또는 빈 시퀀스의 끝 바로 뒤를 지정 하는 양방향 반복기를 반환 합니다. 이를 통해 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::iterator it = c1.begin();
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

## <a name="multisetclear-stlclr"></a><a name="clear"></a> multiset:: clear (STL/CLR)

모든 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
void clear();
```

### <a name="remarks"></a>설명

멤버 함수는 [multiset:: erase (stl/clr)](#erase) `(` [multiset:: begin (stl/clr)](#begin) `(),` [multiset:: end (stl/clr)](#end)를 효과적으로 호출 합니다 `())` . 이를 사용 하 여 제어 되는 시퀀스가 비어 있는지 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetconst_iterator-stlclr"></a><a name="const_iterator"></a> multiset:: const_iterator (STL/CLR)

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>설명

`T2`이 형식은 제어 되는 시퀀스에 대 한 상수 양방향 반복기로 사용할 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reference-stlclr"></a><a name="const_reference"></a> multiset:: const_reference (STL/CLR)

요소에 대한 상수 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>설명

요소에 대 한 상수 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> multiset:: const_reverse_iterator (STL/CLR)

제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>설명

`T4`이 형식은 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetcount-stlclr"></a><a name="count"></a> multiset:: count (STL/CLR)

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
// cliext_multiset_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetdifference_type-stlclr"></a><a name="difference_type"></a> multiset::d ifference_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>설명

이 형식은 음수 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::difference_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="multisetempty-stlclr"></a><a name="empty"></a> multiset:: empty (STL/CLR)

요소가 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
bool empty();
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. [Multiset:: size (STL/CLR)](#size)와 동일 `() == 0` 합니다. Multiset이 비어 있는지 여부를 테스트 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetend-stlclr"></a><a name="end"></a> multiset:: end (STL/CLR)

제어되는 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator end();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 끝 바로 다음을 가리키는 양방향 반복기를 반환 합니다. 이를 사용 하 여 제어 되는 시퀀스의 끝을 지정 하는 반복기를 가져옵니다. 제어 되는 시퀀스의 길이가 변경 되 면 해당 상태는 변경 되지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Mymultiset::iterator it = c1.end();
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

## <a name="multisetequal_range-stlclr"></a><a name="equal_range"></a> multiset:: equal_range (STL/CLR)

지정된 키와 일치하는 범위를 찾습니다.

### <a name="syntax"></a>구문

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 iterator: `cliext::pair<iterator, iterator>(` [: lower_bound (stl/clr)](#lower_bound) `(key),` [multiset:: upper_bound (stl/clr)](#upper_bound)쌍의 쌍을 반환 합니다 `(key))` . 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소의 범위를 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
typedef Mymultiset::pair_iter_iter Pairii;
int main()
    {
    Mymultiset c1;
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

## <a name="multiseterase-stlclr"></a><a name="erase"></a> multiset:: erase (STL/CLR)

지정된 위치에 있는 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
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

첫 번째 멤버 함수는 where가 가리키는 제어 *되*는 시퀀스의 요소를 제거 하 고, 요소를 제거 하 고 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, 이러한 요소가 존재 하지 않는 경우 [multiset:: end (STL/CLR)](#end) 를 반환 합니다 `()` . 단일 요소를 제거 하는 데 사용 합니다.

두 번째 멤버 함수는 [,) 범위에서 제어 되는 시퀀스의 요소를 제거 `first` `last` 하 고, 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, `end()` 이러한 요소가 없는 경우을 반환 합니다. 연속 된 요소를 0 개 이상 제거 하는 데 사용 합니다.

세 번째 멤버 함수는 키가 *키*와 동일한 순서를 갖는 제어 되는 시퀀스의 요소를 제거 하 고 제거 된 요소 수의 개수를 반환 합니다. 이를 사용 하 여 지정 된 키와 일치 하는 모든 요소를 제거 하 고 개수를 계산 합니다.

각 요소를 지울 때마다 제어 되는 시퀀스의 요소 수에 대 한 로그에 비례 하는 시간이 사용 됩니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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
    Mymultiset::iterator it = c1.end();
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

## <a name="multisetfind-stlclr"></a><a name="find"></a> multiset:: find (STL/CLR)

지정된 키와 일치하는 요소를 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

제어 되는 시퀀스의 요소 중 하나 이상이 *key*와 동일한 정렬을 사용 하는 경우 멤버 함수는 이러한 요소 중 하나를 지정 하는 반복기를 반환 합니다. 그렇지 않으면 [multiset:: end (STL/CLR)](#end)를 반환 `()` 합니다. 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소를 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetgeneric_container-stlclr"></a><a name="generic_container"></a> multiset:: generic_container (STL/CLR)

컨테이너에 대 한 제네릭 인터페이스의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>설명

이 템플릿 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
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

## <a name="multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> multiset:: generic_iterator (STL/CLR)

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
// cliext_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> multiset:: generic_reverse_iterator (STL/CLR)

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
// cliext_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="multisetgeneric_value-stlclr"></a><a name="generic_value"></a> multiset:: generic_value (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>설명

`GValue`이 템플릿 컨테이너 클래스의 제네릭 인터페이스에 사용할 저장 된 요소 값을 설명 하는 형식의 개체를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetinsert-stlclr"></a><a name="insert"></a> multiset:: insert (STL/CLR)

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
// cliext_multiset_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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
    Mymultiset c2;
    Mymultiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultiset c3;
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

## <a name="multisetiterator-stlclr"></a><a name="iterator"></a> multiset:: iterator (STL/CLR)

제어되는 시퀀스에 대한 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>설명

`T1`이 형식은 제어 되는 시퀀스에 대 한 양방향 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetkey_comp-stlclr"></a><a name="key_comp"></a> multiset:: key_comp (STL/CLR)

두 키에 대 한 순서 지정 대리자를 복사 합니다.

### <a name="syntax"></a>구문

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 순서 지정 대리자를 반환 합니다. 이를 통해 두 키를 비교할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multisetkey_compare-stlclr"></a><a name="key_compare"></a> multiset:: key_compare (STL/CLR)

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
// cliext_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multisetkey_type-stlclr"></a><a name="key_type"></a> multiset:: key_type (STL/CLR)

정렬 키의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *키*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetlower_bound-stlclr"></a><a name="lower_bound"></a> multiset:: lower_bound (STL/CLR)

지정 된 키와 일치 하는 범위의 시작 부분을 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` 제어 되는 시퀀스에서 *키*와 동일한 순서가 지정 된 첫 번째 요소를 확인 합니다. 이러한 요소가 없으면 [multiset:: end (STL/CLR)](#end)가 반환 `()` 되 고, 그렇지 않으면를 지정 하는 반복기를 반환 `X` 합니다. 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소 시퀀스의 시작 부분을 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetmake_value-stlclr"></a><a name="make_value"></a> multiset:: make_value (STL/CLR)

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
// cliext_multiset_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(Mymultiset::make_value(L'a'));
    c1.insert(Mymultiset::make_value(L'b'));
    c1.insert(Mymultiset::make_value(L'c'));

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetmultiset-stlclr"></a><a name="multiset"></a> multiset:: multiset (STL/CLR)

컨테이너 개체를 만듭니다.

### <a name="syntax"></a>구문

```cpp
multiset();
explicit multiset(key_compare^ pred);
multiset(multiset<Key>% right);
multiset(multiset<Key>^ right);
template<typename InIter>
    multisetmultiset(InIter first, InIter last);
template<typename InIter>
    multiset(InIter first, InIter last,
        key_compare^ pred);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*pred*<br/>
제어 되는 시퀀스의 순서 조건자입니다.

*오른쪽*<br/>
삽입할 개체 또는 범위입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`multiset();`

기본 순서 조건자를 사용 하 여 요소 없이 제어 되는 시퀀스를 초기화 합니다 `key_compare()` . 기본 순서 조건자를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 하는 데 사용 합니다.

생성자는 다음과 같습니다.

`explicit multiset(key_compare^ pred);`

순서 조건자 *pred*를 사용 하 여 요소 없이 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 지정 된 순서 조건자를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`multiset(multiset<Key>% right);`

기본 순서 조건자를 사용 하 여 시퀀스 [ `right.begin()` ,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다 `right.end()` . 이를 사용 하 여 기본 순서 조건자를 사용 하 여 multiset 개체 *오른쪽*에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`multiset(multiset<Key>^ right);`

기본 순서 조건자를 사용 하 여 시퀀스 [ `right->begin()` ,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다 `right->end()` . 이를 사용 하 여 기본 순서 조건자를 사용 하 여 multiset 개체 *오른쪽*에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`template<typename InIter> multiset(InIter first, InIter last);`

기본 순서 조건자를 사용 하 여 시퀀스 [ `first` ,)를 사용 하 여 제어 되는 시퀀스를 초기화 합니다 `last` . 이를 사용 하 여 제어 되는 시퀀스를 기본 순서 조건자를 사용 하 여 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

순서 조건자 pred를 사용 하 여 시퀀스 [ `first` , `last` )를 *pred*사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 지정 된 순서 조건자를 사용 하는 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

기본 순서 조건자를 사용 하 여 열거자 *오른쪽*으로 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 기본 순서 조건자를 사용 하 여 열거자에서 설명한 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

정렬 조건자 *pred*를 사용 하 여 열거자 *오른쪽*으로 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 지정 된 순서 조건자를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명한 다른 시퀀스의 복사본으로 만듭니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
// construct an empty container
    Mymultiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mymultiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultiset c8(%c3);
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
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="multisetoperator-stlclr"></a><a name="op_as"></a> multiset:: operator = (STL/CLR)

제어되는 시퀀스를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 제어 되는 시퀀스를 *오른쪽*에 있는 제어 되는 시퀀스의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Mymultiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="multisetrbegin-stlclr"></a><a name="rbegin"></a> multiset:: rbegin (STL/CLR)

제어되는 역방향 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 마지막 요소 또는 빈 시퀀스의 시작 부분 바로 뒤를 지정 하는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `beginning`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultiset::reverse_iterator rit = c1.rbegin();
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

## <a name="multisetreference-stlclr"></a><a name="reference"></a> multiset:: reference (STL/CLR)

요소에 대한 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>설명

요소에 대 한 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetrend-stlclr"></a><a name="rend"></a> multiset:: rend (STL/CLR)

제어되는 역방향 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 시작 부분 바로 뒤를 가리키는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `end`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 끝을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::reverse_iterator rit = c1.rend();
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

## <a name="multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> multiset:: reverse_iterator (STL/CLR)

제어되는 시퀀스에 대한 반대 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetsize-stlclr"></a><a name="size"></a> multiset:: size (STL/CLR)

요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
size_type size();
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 이를 사용 하 여 현재 제어 되는 시퀀스에 있는 요소 수를 확인 합니다. 시퀀스의 크기가 0이 아니면 [multiset:: empty (STL/CLR)](#empty)를 참조 하세요 `()` .

### <a name="example"></a>예제

```cpp
// cliext_multiset_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetsize_type-stlclr"></a><a name="size_type"></a> multiset:: size_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int size_type;
```

### <a name="remarks"></a>설명

이 형식은 음수가 아닌 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::size_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="multisetswap-stlclr"></a><a name="swap"></a> multiset:: swap (STL/CLR)

두 컨테이너의 내용을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
콘텐츠와 바꿀 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`this`** 과 *오른쪽*으로 바꿉니다. 일정 한 시간에이를 수행 하 고 예외를 throw 하지 않습니다. 이를 사용 하 여 두 컨테이너의 콘텐츠를 신속 하 게 교환할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultiset c2;
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

## <a name="multisetto_array-stlclr"></a><a name="to_array"></a> multiset:: to_array (STL/CLR)

제어 되는 시퀀스를 새 배열에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 이를 사용 하 여 배열 형식으로 제어 되는 시퀀스의 복사본을 가져옵니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetupper_bound-stlclr"></a><a name="upper_bound"></a> multiset:: upper_bound (STL/CLR)

지정 된 키와 일치 하는 범위의 끝을 찾습니다.

### <a name="syntax"></a>구문

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `X` 제어 되는 시퀀스에서 *키*와 동일한 순서가 지정 된 마지막 요소를 확인 합니다. 이러한 요소가 없거나 `X` 가 제어 되는 시퀀스의 마지막 요소 이면 [multiset:: END (STL/CLR)](#end)가 반환 되 고, `()` 그렇지 않은 경우에는에서 첫 번째 요소를 지정 하는 반복기를 반환 합니다 `X` . 이를 사용 하 여 제어 되는 시퀀스에서 현재 지정 된 키와 일치 하는 요소 시퀀스의 끝을 찾을 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetvalue_comp-stlclr"></a><a name="value_comp"></a> multiset:: value_comp (STL/CLR)

두 요소 값에 대 한 순서 지정 대리자를 복사 합니다.

### <a name="syntax"></a>구문

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 순서 지정 대리자를 반환 합니다. 두 요소 값을 비교 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_compare-stlclr"></a><a name="value_compare"></a> multiset:: value_compare (STL/CLR)

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
// cliext_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_type-stlclr"></a><a name="value_type"></a> multiset:: value_type (STL/CLR)

요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>설명

이 형식은 `generic_value`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-multiset-stlclr"></a><a name="op_neq"></a> operator! = (multiset) (STL/CLR)

목록이 같지 않음 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left == right)` . 이를 사용 하 여 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lt"></a> 연산자 &lt; (multiset) (STL/CLR)

비교 보다 작음 목록입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는 해당 하는 가장 낮은 위치에 대해서도 true를 반환 합니다 `i` `!(right[i] < left[i])` `left[i] < right[i]` . 그렇지 않으면 `left->size() < right->size()` 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 에 정렬 되었는지 여부를 테스트 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lteq"></a> operator &lt; = (multiset) (STL/CLR)

보다 작거나 같음 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(right < left)` . 이를 사용 하 여 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-multiset-stlclr"></a><a name="op_eq"></a> operator = = (multiset) (STL/CLR)

동일한 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

Operator 함수는 *left* 및 *right* 로 제어 되는 시퀀스의 길이가 같고 각 위치에 대해가 인 경우에만 true를 반환 합니다 `i` `left[i] ==` `right[i]` . 이를 사용 하 여 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되었는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gt"></a> 연산자 &gt; (multiset) (STL/CLR)

비교 보다 큼을 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `right` `<` `left` . 이를 사용 하 여 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gteq"></a> operator &gt; = (multiset) (STL/CLR)

보다 크거나 같음 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left < right)` . 이를 사용 하 여 두 다중 집합를 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 앞에 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_multiset_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
