---
description: Regex_token_iterator 클래스에 대해 자세히 알아보세요.
title: regex_token_iterator 클래스
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 752ff44864b435100bacb83250a5c6a792cab502
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243889"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator 클래스

부분 일치에 대한 반복기 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>매개 변수

*BidIt*\
부분 일치에 대한 반복기 형식입니다.

*E*\
일치 항목을 찾을 요소의 형식입니다.

*RXtraits*\
요소에 대한 특성 클래스입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 상수 전방 반복기 개체를 설명 합니다. 개념적으로 문자 시퀀스에서 정규식 일치를 검색하는 데 사용되는 `regex_iterator` 개체를 보관합니다. 각 정규식 일치에 대해 저장된 벡터 `sub_match<BidIt>` 의 인덱스 값으로 식별된 부분 일치를 나타내는 `subs` 형식의 개체를 추출합니다.

인덱스 값 -1은 이전 정규식 일치가 끝난 다음 바로 시작되거나 이전 정규식 일치가 없는 경우 문자 시퀀스의 시작에서 시작되고 현재 정규식 일치의 첫 번째 문자로 확장되지만 포함하지 않거나 현재 일치가 없는 경우 문자 시퀀스의 끝으로 확장되는 문자 시퀀스를 지정합니다. 다른 모든 인덱스 값 `idx` 는 `it.match[idx]`에 보관된 캡처 그룹의 내용을 지정합니다.

### <a name="members"></a>멤버

|멤버|기본값|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|반복기를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[difference_type](#difference_type)|반복기 차이의 형식입니다.|
|[iterator_category](#iterator_category)|반복기 범주의 형식입니다.|
|[놓고](#pointer)|일치 항목에 대한 포인터의 형식입니다.|
|[reference](#reference)|부분 일치에 대한 참조의 형식입니다.|
|[regex_type](#regex_type)|일치 항목을 찾을 정규식의 형식입니다.|
|[value_type](#value_type)|부분 일치의 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자! =](#op_neq)|반복기가 같지 않은지 비교합니다.|
|[연산자](#op_star)|지정된 부분 일치에 액세스합니다.|
|[operator + +](#op_add_add)|반복기를 증가시킵니다.|
|[연산자 = =](#op_eq_eq)|반복기가 같은지 비교합니다.|
|[연산자->](#op_arrow)|지정된 부분 일치에 액세스합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<regex>

**네임스페이스:** std

## <a name="example"></a>예제

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a> regex_token_iterator::d ifference_type

반복기 차이의 형식입니다.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>설명

이 형식은 `std::ptrdiff_t`의 동의어입니다.

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a> regex_token_iterator:: iterator_category

반복기 범주의 형식입니다.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>설명

이 형식은 `std::forward_iterator_tag`의 동의어입니다.

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a> regex_token_iterator:: operator! =

반복기가 같지 않은지 비교합니다.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 `!(*this == right)`를 반환합니다.

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a> regex_token_iterator:: operator *

지정된 부분 일치에 액세스합니다.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>설명

멤버 함수는 `sub_match<BidIt>` 인덱스 값으로 식별된 캡처 그룹을 나타내는 `subs[pos]`개체를 반환합니다.

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a> regex_token_iterator:: operator + +

반복기를 증가시킵니다.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>설명

저장된 반복기 `it`가 시퀀스의 끝 반복기인 경우 첫 번째 연산자는 저장된 값 `pos`를 `subs.size()`의 값으로 설정하여 시퀀스의 끝 반복기를 만듭니다. 그렇지 않은 경우 연산자는 저장된 값 `pos`를 증가시킵니다. 결과가 `subs.size()` 값과 같으면 저장된 값 `pos`를 0으로 설정하고 저장된 반복기 `it`를 증가시킵니다. 저장된 반복기의 증분 결과가 시퀀스의 끝 반복기와 같지 않은 경우 연산자가 추가 작업을 수행하지 않습니다. 이전 일치 항목의 끝이 문자 시퀀스의 끝에 있는 경우 연산자가 `pos`의 저장된 값을 `subs.size()`로 설정합니다. 또는 `pos == subs.size()` 또는 `subs[pos] == -1`까지 연산자가 저장된 값 `pos`를 반복적으로 증가시켜 인덱스 값 중 하나가 -1이면 반복기의 다음 역참조에서 문자 시퀀스의 테일이 반환되도록 합니다. 모든 경우에서 연산자는 개체를 반환합니다.

두 번째 연산자는 개체의 복사본을 만들고 개체를 증가시킨 다음 복사본을 반환합니다.

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a> regex_token_iterator:: operator = =

반복기가 같은지 비교합니다.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 반복기입니다.

### <a name="remarks"></a>설명

멤버 함수는 `it == right.it && subs == right.subs && pos == right.pos`를 반환합니다.

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a> regex_token_iterator:: operator-&gt;

지정된 부분 일치에 액세스합니다.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>설명

멤버 함수는 `sub_match<BidIt>` 인덱스 값으로 식별된 캡처 그룹을 나타내는 `subs[pos]`개체에 대한 포인터를 반환합니다.

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a> regex_token_iterator::p ointer

일치 항목에 대한 포인터의 형식입니다.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>설명

이 형식은 `sub_match<BidIt>*`의 동의어로, 여기서 `BidIt` 는 템플릿 매개 변수입니다.

## <a name="regex_token_iteratorreference"></a><a name="reference"></a> regex_token_iterator:: reference

부분 일치에 대한 참조의 형식입니다.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>설명

이 형식은 `sub_match<BidIt>&`의 동의어로, 여기서 `BidIt` 는 템플릿 매개 변수입니다.

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a> regex_token_iterator:: regex_token_iterator

반복기를 생성합니다.

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>매개 변수

*기본*\
일치하는 시퀀스의 시작입니다.

*최신*\
일치하는 시퀀스의 끝입니다.

*재실행*\
일치 항목에 대한 정규식입니다.

*350*\
일치에 대한 플래그입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 시퀀스의 끝 반복기를 생성합니다.

두 번째 생성자는 저장된 반복기 `it` 은 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`로 초기화되고, 저장된 벡터 `subs` 는 `submatch`값과 함께 정확히 하나의 정수를 보유하며, 저장된 값 `pos` 는 0인 개체를 생성합니다. 참고: 결과 개체는 성공한 각 정규식 일치에 대해 인덱스 값 `submatch` 로 식별되는 부분 일치를 추출합니다.

세 번째 생성자는 저장된 반복기 `it` 은 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`로 초기화되고, 저장된 벡터 `subs` 는 생성자 인수 `submatches`의 복사본을 보유하며, 저장된 값 `pos` 는 0인 개체를 생성합니다.

네 번째 생성자는 저장된 반복기 `it` 은 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`로 초기화되고, 저장된 벡터 `subs` 는 생성자 인수 `N` 가 가리키는 `submatches`값을 보유하며, 저장된 값 `pos` 는 0인 개체를 생성합니다.

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a> regex_token_iterator:: regex_type

일치 항목을 찾을 정규식의 형식입니다.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>설명

typedef는 `basic_regex<Elem, RXtraits>`의 동의어입니다.

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a> regex_token_iterator:: value_type

부분 일치의 형식입니다.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>설명

이 형식은 `sub_match<BidIt>`의 동의어로, 여기서 `BidIt` 는 템플릿 매개 변수입니다.

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)\
[regex_constants 클래스](../standard-library/regex-constants-class.md)\
[regex_error 클래스](../standard-library/regex-error-class.md)\
[\<regex> 역함수](../standard-library/regex-functions.md)\
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)\
[\<regex> 작업자](../standard-library/regex-operators.md)\
[regex_traits 클래스](../standard-library/regex-traits-class.md)\
[\<regex> 정의](../standard-library/regex-typedefs.md)
