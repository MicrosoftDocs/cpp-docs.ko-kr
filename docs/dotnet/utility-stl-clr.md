---
title: utility(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: faf7f607f9433fa3e4813957b24220a5e66e1e49
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008619"
---
# <a name="utility-stlclr"></a>utility(STL/CLR)

STL/CLR 헤더를 포함 `<cliext/utility>` 하 여 템플릿 클래스 `pair` 및 여러 지원 템플릿 함수를 정의 합니다.

## <a name="syntax"></a>구문

```cpp
#include <utility>
```

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/utility>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|클래스|설명|
|-----------|-----------------|
|[pair(STL/CLR)](#pair)|요소 쌍을 래핑합니다.|

|연산자|설명|
|--------------|-----------------|
|[operator== (pair)(STL/CLR)](#op_eq)|쌍 같음 비교입니다.|
|[operator! = (pair) (STL/CLR)](#op_neq)|쌍이 비교와 같지 않습니다.|
|[연산자< (쌍) (STL/CLR)](#op_lt)|쌍이 비교 보다 작음|
|[operator \< = (쌍) (STL/CLR)](#op_lteq)|보다 작거나 같음 비교입니다.|
|[연산자> (쌍) (STL/CLR)](#op_gt)|페어링 보다 큼 비교입니다.|
|[연산자>= (쌍) (STL/CLR)](#op_gteq)|쌍 보다 크거나 같음 비교입니다.|

|기능|설명|
|--------------|-----------------|
|[make_pair(STL/CLR)](#make_pair)|값 쌍의 쌍을 만듭니다.|

## <a name="pair-stlclr"></a><a name="pair"></a> pair (STL/CLR)

템플릿 클래스는 값 쌍을 래핑하는 개체를 설명 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>매개 변수

*Value1*<br/>
래핑된 첫 번째 값의 형식입니다.

*Value2*<br/>
래핑된 두 번째 값의 형식입니다.

## <a name="members"></a>구성원

|형식 정의|설명|
|---------------------|-----------------|
|[pair::first_type(STL/CLR)](#first_type)|래핑된 첫 번째 값의 형식입니다.|
|[pair::second_type(STL/CLR)](#second_type)|래핑된 두 번째 값의 형식입니다.|

|멤버 개체|설명|
|-------------------|-----------------|
|[pair::first(STL/CLR)](#first)|첫 번째 저장 된 값입니다.|
|[pair::second(STL/CLR)](#second)|저장 된 두 번째 값입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[pair::pair(STL/CLR)](#pair_pair)|Pair 개체를 생성 합니다.|
|[pair::swap(STL/CLR)](#swap)|두 쌍의 내용을 바꿉니다.|

|연산자|설명|
|--------------|-----------------|
|[pair::operator=(STL/CLR)](#op_as)|저장 된 값 쌍을 바꿉니다.|

## <a name="remarks"></a>설명

개체는 값의 쌍을 저장 합니다. 이 템플릿 클래스를 사용 하 여 두 값을 단일 개체로 결합 합니다. 또한 여기에 설명 된 개체는 `cliext::pair` 관리 되는 형식만 저장 하 고 관리 되지 않는 형식 쌍을 저장 하려면에 선언 된를 사용 `std::pair` `<utility>` 합니다.

## <a name="pairfirst-stlclr"></a><a name="first"></a> pair:: first (STL/CLR)

래핑된 첫 번째 값입니다.

### <a name="syntax"></a>구문

```cpp
Value1 first;
```

### <a name="remarks"></a>설명

개체는 첫 번째 래핑된 값을 저장 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a> pair:: first_type (STL/CLR)

래핑된 첫 번째 값의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *Value1*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a> pair:: operator = (STL/CLR)

저장 된 값 쌍을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 쌍입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 저장 된 값 쌍을 *오른쪽*에 저장 된 값 쌍의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a> pair::p air (STL/CLR)

Pair 개체를 생성 합니다.

### <a name="syntax"></a>구문

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
저장할 쌍입니다.

*val1*<br/>
저장할 첫 번째 값입니다.

*val2*<br/>
저장할 두 번째 값입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`pair();`

생성 된 기본 값을 사용 하 여 저장 된 쌍을 초기화 합니다.

생성자는 다음과 같습니다.

`pair(pair<Value1, Value2>% right);`

`right.` [pair:: FIRST (STL/clr)](#first) 및 `right.` [PAIR:: second (stl/clr)](#second)를 사용 하 여 저장 된 쌍을 초기화 합니다.

`pair(pair<Value1, Value2>^ right);`

`right->` [pair:: FIRST (STL/clr)](#first) 및 `right>` [PAIR:: second (stl/clr)](#second)를 사용 하 여 저장 된 쌍을 초기화 합니다.

생성자는 다음과 같습니다.

`pair(Value1 val1, Value2 val2);`

*val1* 및 *val2*를 사용 하 여 저장 된 쌍을 초기화 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a> pair:: second (STL/CLR)

래핑된 두 번째 값입니다.

### <a name="syntax"></a>구문

```cpp
Value2 second;
```

### <a name="remarks"></a>설명

개체는 래핑된 두 번째 값을 저장 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a> pair:: second_type (STL/CLR)

래핑된 두 번째 값의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *Value2*의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a> pair:: swap (STL/CLR)

두 쌍의 내용을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
콘텐츠를 교환할 쌍입니다.

### <a name="remarks"></a>설명

멤버 함수는와 오른쪽 사이에 저장 된 값 쌍을 바꿉니다 **`*this`** . *right*

### <a name="example"></a>예제

```cpp
// cliext_pair_swap.cpp
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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a> make_pair (STL/CLR)

`pair`값 쌍에서을 만듭니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>매개 변수

*Value1*<br/>
래핑된 첫 번째 값의 형식입니다.

*Value2*<br/>
래핑된 두 번째 값의 형식입니다.

*first*<br/>
래핑할 첫 번째 값입니다.

*second*<br/>
래핑할 두 번째 값입니다.

### <a name="remarks"></a>설명

템플릿 함수가 `pair<Value1, Value2>(first, second)`을 반환합니다. 이를 사용 하 여 `pair<Value1, Value2>` 값 쌍에서 개체를 생성 합니다.

### <a name="example"></a>예제

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a> operator! = (pair) (STL/CLR)

쌍이 비교와 같지 않습니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left == right)` . 이를 사용 하 여 두 쌍이 요소 별로 비교 될 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a> 연산자 &lt; (쌍) (STL/CLR)

쌍이 비교 보다 작음

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second` . 이를 사용 하 여 두 쌍이 요소에 의해 비교 될 때 *왼쪽* 이 *오른쪽* 에 정렬 되는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a> operator &lt; = (쌍) (STL/CLR)

보다 작거나 같음 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(right < left)` . 이를 사용 하 여 두 쌍이 요소 별로 비교 될 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a> operator = = (페어링) (STL/CLR)

쌍 같음 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `left.first ==` `right.first &&` `left.second ==` `right.second` . 이를 사용 하 여 두 쌍이 요소 별로 비교 될 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되었는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a> 연산자 &gt; (쌍) (STL/CLR)

페어링 보다 큼 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `right` `<` `left` . 이를 사용 하 여 두 쌍이 요소 별로 비교 될 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a> operator &gt; = (쌍) (STL/CLR)

쌍 보다 크거나 같음 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 쌍입니다.

*오른쪽*<br/>
비교할 오른쪽 쌍입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left < right)` . 이를 사용 하 여 두 쌍이 요소에 의해 비교 될 때 *왼쪽* 이 *오른쪽* 앞에 정렬 되지 않는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
