---
title: adapter(STL/CLR)
ms.date: 06/15/2018
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
ms.openlocfilehash: 3278371cc7afb08f0d461c77cde9578e1f2840c6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502424"
---
# <a name="adapter-stlclr"></a>adapter(STL/CLR)

STL/CLR 헤더는 `<cliext/adapter>` 두 개의 템플릿 클래스 ( `collection_adapter` 및 `range_adapter` ) 및 템플릿 함수를 지정 합니다 `make_collection` .

## <a name="syntax"></a>구문

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/adapter>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|클래스|설명|
|-----------|-----------------|
|[collection_adapter(STL/CLR)](#collection_adapter)|BCL (기본 클래스 라이브러리) 컬렉션을 범위로 래핑합니다.|
|[range_adapter(STL/CLR)](#range_adapter)|BCL 컬렉션으로 범위를 래핑합니다.|

|함수|설명|
|--------------|-----------------|
|[make_collection(STL/CLR)](#make_collection)|반복기 쌍을 사용 하 여 범위 어댑터를 만듭니다.|

## <a name="members"></a>멤버

## <a name="collection_adapter-stlclr"></a><a name="collection_adapter"></a> collection_adapter (STL/CLR)

STL/CLR 컨테이너로 사용할 .NET 컬렉션을 래핑합니다. 는 `collection_adapter` 간단한 STL/CLR 컨테이너 개체를 설명 하는 템플릿 클래스입니다. BCL (기본 클래스 라이브러리) 인터페이스를 래핑하고 제어 되는 시퀀스를 조작 하는 데 사용 하는 반복기 쌍을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Coll>
    ref class collection_adapter;

template<>
    ref class collection_adapter<
        System::Collections::ICollection>;
template<>
    ref class collection_adapter<
        System::Collections::IEnumerable>;
template<>
    ref class collection_adapter<
        System::Collections::IList>;
template<>
    ref class collection_adapter<
        System::Collections::IDictionary>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::ICollection<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IEnumerable<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IList<Value>>;
template<typename Key,
    typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IDictionary<Key, Value>>;
```

#### <a name="parameters"></a>매개 변수

*Coll*<br/>
래핑된 컬렉션의 형식입니다.

### <a name="specializations"></a>특수화

|전문 분야|설명|
|--------------------|-----------------|
|IEnumerable|요소를 통해 시퀀스 합니다.|
|ICollection|요소 그룹을 유지 관리 합니다.|
|IList|요소의 정렬 된 그룹을 유지 관리 합니다.|
|IDictionary|{Key, value} 쌍의 집합을 유지 관리 합니다.|
|IEnumerable\<Value>|형식화 된 요소를 통해 시퀀스 합니다.|
|ICollection\<Value>|형식화 된 요소의 그룹을 유지 관리 합니다.|
|IList\<Value>|형식화 된 요소의 정렬 된 그룹을 유지 관리 합니다.|
|IDictionary\<Value> |형식화 된 {key, value} 쌍의 집합을 유지 관리 합니다.|

### <a name="members"></a>멤버

|형식 정의|설명|
|---------------------|-----------------|
|[collection_adapter::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[collection_adapter::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[collection_adapter::key_type(STL/CLR)](#key_type)|사전 키의 형식입니다.|
|[collection_adapter::mapped_type(STL/CLR)](#mapped_type)|사전 값의 형식입니다.|
|[collection_adapter::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|
|[collection_adapter::size_type(STL/CLR)](#size_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[collection_adapter::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[collection_adapter::base(STL/CLR)](#base)|래핑된 BCL 인터페이스를 지정 합니다.|
|[collection_adapter::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[collection_adapter::collection_adapter(STL/CLR)](#collection_adapter_collection_adapter)|어댑터 개체를 생성 합니다.|
|[collection_adapter::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[collection_adapter::size(STL/CLR)](#size)|요소 수를 계산합니다.|
|[collection_adapter::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|

|연산자|설명|
|--------------|-----------------|
|[collection_adapter::operator=(STL/CLR)](#op_eq)|저장 된 BCL 핸들을 바꿉니다.|

### <a name="remarks"></a>설명

이 템플릿 클래스를 사용 하 여 BCL/CLR 컨테이너로 BCL 컨테이너를 조작 합니다. 은 `collection_adapter` BCL 인터페이스에 대 한 핸들을 저장 하며,이를 통해 요소의 시퀀스를 제어 합니다. `collection_adapter`개체는 `X` `X.begin()` `X.end()` 요소를 순서 대로 방문 하는 데 사용 하는 입력 반복기 쌍을 반환 합니다. 일부 특수화를 사용 하 여 제어 되는 `X.size()` 시퀀스의 길이를 결정할 수도 있습니다.

## <a name="collection_adapterbase-stlclr"></a><a name="base"></a> collection_adapter:: base (STL/CLR)

래핑된 BCL 인터페이스를 지정 합니다.

### <a name="syntax"></a>구문

```cpp
Coll^ base();
```

### <a name="remarks"></a>설명

멤버 함수는 저장 된 BCL 인터페이스 핸들을 반환 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_base.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);
    return (0);
    }
```

```Output
x x x x x x
base() same = True
```

## <a name="collection_adapterbegin-stlclr"></a><a name="begin"></a> collection_adapter:: begin (STL/CLR)

제어되는 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator begin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 첫 번째 요소 또는 빈 시퀀스의 끝 바로 뒤를 지정 하는 입력 반복기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_begin.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mycoll::iterator it = c1.begin();
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

## <a name="collection_adaptercollection_adapter-stlclr"></a><a name="collection_adapter_collection_adapter"></a> collection_adapter:: collection_adapter (STL/CLR)

어댑터 개체를 생성 합니다.

### <a name="syntax"></a>구문

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>매개 변수

*컬렉션*<br/>
래핑할 BCL 핸들입니다.

*오른쪽*<br/>
복사할 개체입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`collection_adapter();`

을 사용 하 여 저장 된 핸들을 초기화 합니다 **`nullptr`** .

생성자는 다음과 같습니다.

`collection_adapter(collection_adapter<Coll>% right);`

`right.` [collection_adapter:: BASE (STL/CLR)](#base)를 사용 하 여 저장 된 핸들을 초기화 `()` 합니다.

생성자는 다음과 같습니다.

`collection_adapter(collection_adapter<Coll>^ right);`

`right->` [collection_adapter:: BASE (STL/CLR)](#base)를 사용 하 여 저장 된 핸들을 초기화 `()` 합니다.

생성자는 다음과 같습니다.

`collection_adapter(Coll^ collection);`

을 사용 하 여 저장 된 핸들을 초기화 합니다 `collection` .

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');

    // construct an empty container
    Mycoll c1;
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);

    // construct with a handle
    Mycoll c2(%d6x);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mycoll c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mycoll c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
base() null = True
x x x x x x
x x x x x x
x x x x x x
```

## <a name="collection_adapterdifference_type-stlclr"></a><a name="difference_type"></a> collection_adapter::d ifference_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>설명

형식은 서명 된 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_difference_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mycoll::difference_type diff = 0;
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
}
```

```Output
a b c
end()-begin() = 3
```

## <a name="collection_adapterend-stlclr"></a><a name="end"></a> collection_adapter:: end (STL/CLR)

제어되는 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator end();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 끝 바로 뒤를 가리키는 입력 반복기를 반환 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_end.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapteriterator-stlclr"></a><a name="iterator"></a> collection_adapter:: iterator (STL/CLR)

제어되는 시퀀스에 대한 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>설명

`T1`이 형식은 제어 되는 시퀀스에 대 한 입력 반복기로 사용할 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_iterator.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapterkey_type-stlclr"></a><a name="key_type"></a> collection_adapter:: key_type (STL/CLR)

사전 키의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>설명

형식은 `Key` 또는에 대 한 특수화에서 템플릿 매개 변수의 동의어이 고, `IDictionary` `IDictionary<Value>` 그렇지 않으면 정의 되지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_key_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adaptermapped_type-stlclr"></a><a name="mapped_type"></a> collection_adapter:: mapped_type (STL/CLR)

사전 값의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>설명

형식은 `Value` 또는에 대 한 특수화에서 템플릿 매개 변수의 동의어이 고, `IDictionary` `IDictionary<Value>` 그렇지 않으면 정의 되지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_mapped_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adapteroperator-stlclr"></a><a name="op_eq"></a> collection_adapter:: operator = (STL/CLR)

저장 된 BCL 핸들을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 어댑터입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 저장 된 bcl 핸들을 *오른쪽*에 저장 된 bcl 핸들의 복사본으로 바꾸는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mycoll c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="collection_adapterreference-stlclr"></a><a name="reference"></a> collection_adapter:: reference (STL/CLR)

요소에 대한 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>설명

요소에 대 한 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_reference.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
    {   // get a reference to an element
        Mycoll::reference ref = *it;
        System::Console::Write("{0} ", ref);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adaptersize-stlclr"></a><a name="size"></a> collection_adapter:: size (STL/CLR)

요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
size_type size();
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 또는에 대 한 특수화에 정의 되어 있지 않습니다 `IEnumerable` `IEnumerable<Value>` .

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_size.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adaptersize_type-stlclr"></a><a name="size_type"></a> collection_adapter:: size_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int size_type;
```

### <a name="remarks"></a>설명

이 형식은 음수가 아닌 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_size_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    Mycoll::size_type size = c1.size();
    System::Console::WriteLine("size() = {0}", size);
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adapterswap-stlclr"></a><a name="swap"></a> collection_adapter:: swap (STL/CLR)

두 컨테이너의 내용을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
콘텐츠와 바꿀 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 저장 된 BCL 핸들을 **`*this`** 와 *오른쪽*으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
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
x x x x x
x x x x x
a b c
```

## <a name="collection_adaptervalue_type-stlclr"></a><a name="value_type"></a> collection_adapter:: value_type (STL/CLR)

요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *값*(특수화에 있는 경우)의 동의어입니다. 그렇지 않으면의 동의어입니다 `System::Object^` .

### <a name="example"></a>예제

```cpp
// cliext_collection_adapter_value_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display contents "a b c" using value_type
    for (Mycoll::iterator it = c1.begin();
        it != c1.end(); ++it)
    {   // store element in value_type object
        Mycoll::value_type val = *it;

        System::Console::Write("{0} ", val);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="make_collection-stlclr"></a><a name="make_collection"></a> make_collection (STL/CLR)

`range_adapter`반복기 쌍에서을 만듭니다.

### <a name="syntax"></a>구문

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>매개 변수

*Iter*<br/>
래핑된 반복기의 형식입니다.

*first*<br/>
래핑할 첫 번째 반복기입니다.

*last*<br/>
래핑할 두 번째 반복기입니다.

### <a name="remarks"></a>설명

템플릿 함수가 `gcnew range_adapter<Iter>(first, last)`을 반환합니다. 이를 사용 하 여 `range_adapter<Iter>` 반복기 쌍에서 개체를 생성 합니다.

### <a name="example"></a>예제

```cpp
// cliext_make_collection.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in d1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Collections::ICollection^ p1 =
        cliext::make_collection(d1.begin(), d1.end());
    System::Console::WriteLine("Count = {0}", p1->Count);
    System::Console::WriteLine("IsSynchronized = {0}",
        p1->IsSynchronized);
    System::Console::WriteLine("SyncRoot not nullptr = {0}",
        p1->SyncRoot != nullptr);

    // copy the sequence
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);

    a1[0] = L'|';
    p1->CopyTo(a1, 1);
    a1[4] = L'|';
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
Count = 3
IsSynchronized = False
SyncRoot not nullptr = True
| a b c |
```

## <a name="range_adapter-stlclr"></a><a name="range_adapter"></a> range_adapter (STL/CLR)

여러 BCL (기본 클래스 라이브러리) 인터페이스를 구현 하는 데 사용 되는 반복기 쌍을 래핑하는 템플릿 클래스입니다. Range_adapter를 사용 하 여 BCL/CLR 범위를 BCL 컬렉션과 같이 조작할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<typename Iter>
    ref class range_adapter
        :   public
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<Value>,
        System::Collections::Generic::ICollection<Value>
    { ..... };
```

#### <a name="parameters"></a>매개 변수

*Iter*<br/>
래핑된 반복기와 연결 된 형식입니다.

### <a name="members"></a>멤버

|멤버 함수|설명|
|---------------------|-----------------|
|[range_adapter::range_adapter(STL/CLR)](#range_adapter_range_adapter)|어댑터 개체를 생성 합니다.|

|연산자|설명|
|--------------|-----------------|
|[range_adapter::operator=(STL/CLR)](#range_adapter_op_eq)|저장 된 반복기 쌍을 바꿉니다.|

### <a name="interfaces"></a>인터페이스

|인터페이스|설명|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|컬렉션의 요소를 반복 합니다.|
|<xref:System.Collections.ICollection>|요소 그룹을 유지 관리 합니다.|
|<xref:System.Collections.Generic.IEnumerable%601>|컬렉션의 형식화 된 요소를 반복 합니다.|
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 관리 합니다.|

### <a name="remarks"></a>설명

Range_adapter는 일련의 요소를 구분 하는 반복기 쌍을 저장 합니다. 개체는 요소를 순서 대로 반복할 수 있도록 하는 네 가지 BCL 인터페이스를 구현 합니다. 이 템플릿 클래스를 사용 하 여 BCL 컨테이너와 마찬가지로 STL/CLR 범위를 조작할 수 있습니다.

## <a name="range_adapteroperator-stlclr"></a><a name="range_adapter_op_eq"></a> range_adapter:: operator = (STL/CLR)

저장 된 반복기 쌍을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 어댑터입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 저장 된 반복기 쌍을 *오른쪽*에 저장 된 반복기 쌍의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_range_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Myrange c1(d1.begin(), d1.end());

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myrange c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="range_adapterrange_adapter-stlclr"></a><a name="range_adapter_range_adapter"></a> range_adapter:: range_adapter (STL/CLR)

어댑터 개체를 생성 합니다.

### <a name="syntax"></a>구문

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
래핑할 첫 번째 반복기입니다.

*last*<br/>
래핑할 두 번째 반복기입니다.

*오른쪽*<br/>
복사할 개체입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`range_adapter();`

기본 생성 반복기를 사용 하 여 저장 된 반복기 쌍을 초기화 합니다.

생성자는 다음과 같습니다.

`range_adapter(range_adapter<Iter>% right);`

*오른쪽*에 저장 된 쌍을 복사 하 여 저장 된 반복기 쌍을 초기화 합니다.

생성자는 다음과 같습니다.

`range_adapter(range_adapter<Iter>^ right);`

에 저장 된 쌍을 복사 하 여 저장 된 반복기 쌍을 초기화 합니다 `*right` .

생성자는 다음과 같습니다.

`range_adapter(Iter^ first, last);`

*first* 및 *last*를 사용 하 여 저장 된 반복기 쌍을 초기화 합니다.

### <a name="example"></a>예제

```cpp
// cliext_range_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // construct an empty adapter
    Myrange c1;

    // construct with an iterator pair
    Myrange c2(d1.begin(), d1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another adapter
    Myrange c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying an adapter handle
    Myrange c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
a b c
a b c
```
