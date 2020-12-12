---
description: Sub_match 클래스에 대해 자세히 알아보세요.
title: sub_match 클래스
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 683b0bc6cf73a44ce426d5dcab3cdf13221be66b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183401"
---
# <a name="sub_match-class"></a>sub_match 클래스

부분 일치를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>매개 변수

*BidIt*\
부분 일치에 대한 반복기 형식입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 [regex_match](../standard-library/regex-functions.md#regex_match) 호출 또는 [regex_search](../standard-library/regex-functions.md#regex_search)에 대 한 호출에서 캡처 그룹과 일치 하는 문자 시퀀스를 지정 하는 개체를 설명 합니다. [match_results Class](../standard-library/match-results-class.md) 형식의 개체는 검색에서 사용된 정규식의 각 캡처 그룹에 대해 하나씩 이러한 개체의 배열을 보유합니다.

캡처 그룹이 개체의 데이터 멤버와 일치하지 않는 경우 `matched` 는 false를 보유하고 두 개의 반복기 `first` 와 `second` (기본 `std::pair`에서 상속됨)가 동일합니다. 캡처 그룹이 일치하는 경우 `matched` 는 true를 보유하고, 반복기 `first` 는 캡처 그룹과 일치하는 대상 시퀀스의 첫 번째 문자를 가리키며, 반복기 `second` 는 캡처 그룹과 일치하는 대상 시퀀스의 마지막 문자를 지난 한 위치를 가리킵니다. 멤버와 길이가 0인 일치의 경우 `matched` 는 true를 보유하고, 두 개의 반복기가 동일하며, 둘 다 일치 항목의 위치를 가리킵니다.

길이가 0인 일치는 캡처 그룹이 어설션으로만 구성되거나 0 반복을 허용하는 반복으로 구성된 경우에 발생할 수 있습니다. 예를 들어:

"^"은 대상 시퀀스 "a"와 일치합니다. 즉, 캡처 그룹 0에 해당하는 `sub_match` 개체는 둘 다 시퀀스의 첫 번째 문자를 가리키는 반복기를 보유합니다.

"b(a*)b"는 대상 시퀀스 "bb"와 일치합니다. 즉, 캡처 그룹 1에 해당하는 `sub_match` 개체는 둘 다 시퀀스의 두 번째 문자를 가리키는 반복기를 보유합니다.

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[difference_type](#difference_type)|반복기 차이의 형식입니다.|
|[iterator](#iterator)|반복기의 형식입니다.|
|[value_type](#value_type)|요소의 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[과](#compare)|시퀀스에 대해 부분 일치를 비교합니다.|
|[length](#length)|부분 일치의 길이를 반환합니다.|
|[하도록](#matched)|일치에 성공했는지를 나타냅니다.|
|[str](#str)|부분 일치를 문자열로 변환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 basic_string<value_type>](#op_basic_string_lt_value_type_gt)|문자열에 부분 일치를 캐스팅합니다.|

## <a name="example"></a>예제

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>요구 사항

**헤더:**\<regex>

**네임스페이스:** std

## <a name="sub_matchcompare"></a><a name="compare"></a> sub_match:: compare

시퀀스에 대해 부분 일치를 비교합니다.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 부분 일치입니다.

*문자열*\
비교할 문자열입니다.

*ptr*\
비교할 null 종료 시퀀스입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 일치하는 시퀀스 `[first, second)`를 일치하는 시퀀스에 `[right.first, right.second)`와 비교합니다. 두 번째 멤버 함수는 일치하는 시퀀스 `[first, second)`를 문자 시퀀스에 `[right.begin(), right.end())`와 비교합니다. 세 번째 멤버 함수는 일치하는 시퀀스 `[first, second)`를 문자 시퀀스 `[right, right + std::char_traits<value_type>::length(right))`와 비교합니다.

각 함수는 다음을 반환합니다.

일치하는 시퀀스에서 서로 다른 첫 번째 값이 피연산자 시퀀스의 해당 요소보다 작은 경우(`std::char_traits<value_type>::compare`에서 확인) 또는 둘 다 공통 접두사를 갖지만 대상 시퀀스가 더 긴 경우 음수 값을 반환합니다.

두 시퀀스가 요소 단위로 같고 동일한 길이를 가진 경우 0

그렇지 않으면 양수 값

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a> sub_match::d ifference_type

반복기 차이의 형식입니다.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>설명

typedef는 `iterator_traits<BidIt>::difference_type`의 동의어입니다.

## <a name="sub_matchiterator"></a><a name="iterator"></a> sub_match:: iterator

반복기의 형식입니다.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>설명

typedef는 템플릿 형식 인수 `Bidit`의 동의어입니다.

## <a name="sub_matchlength"></a><a name="length"></a> sub_match:: length

부분 일치의 길이를 반환합니다.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>설명

멤버 함수는 일치하는 시퀀스의 길이 또는 일치하는 시퀀스가 없는 경우 0을 반환합니다.

## <a name="sub_matchmatched"></a><a name="matched"></a> sub_match:: 일치

일치에 성공했는지를 나타냅니다.

```cpp
bool matched;
```

### <a name="remarks"></a>설명

멤버는 **`true`** 와 연결 된 캡처 그룹이 **`*this`** 정규식 일치의 일부인 경우에만 유지 됩니다.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a> sub_match:: operator basic_string &lt; value_type&gt;

문자열에 부분 일치를 캐스팅합니다.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>설명

멤버 연산자는 `str()`를 반환합니다.

## <a name="sub_matchstr"></a><a name="str"></a> sub_match:: str

부분 일치를 문자열로 변환합니다.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `basic_string<value_type>(first, second)`를 반환합니다.

## <a name="sub_matchvalue_type"></a><a name="value_type"></a> sub_match:: value_type

요소의 형식입니다.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>설명

typedef는 `iterator_traits<BidIt>::value_type`의 동의어입니다.

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
