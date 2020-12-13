---
description: Match_results 클래스에 대해 자세히 알아보세요.
title: match_results 클래스
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 55c73f558f4355c66a6c6180007bee0d83045a51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149333"
---
# <a name="match_results-class"></a>match_results 클래스

부분 일치 시퀀스를 보유합니다.

## <a name="syntax"></a>구문

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>매개 변수

*BidIt*\
부분 일치에 대한 반복기 형식입니다.

*#C4*\
스토리지 관리를 위한 할당자의 형식입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 `sub_match<BidIt>` 정규식 검색에서 생성 된 형식 요소의 수정할 수가 없는 시퀀스를 제어 하는 개체를 설명 합니다. 각 요소는 해당 요소에 해당하는 캡처 그룹과 일치하는 하위 시퀀스를 가리킵니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[match_results](#match_results)|개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[allocator_type](#allocator_type)|스토리지 관리를 위한 할당자의 형식입니다.|
|[char_type](#char_type)|요소의 형식입니다.|
|[const_iterator](#const_iterator)|부분 일치에 대한 상수 반복기 형식입니다.|
|[const_reference](#const_reference)|요소 const 참조의 형식입니다.|
|[difference_type](#difference_type)|반복기 차이의 형식입니다.|
|[iterator](#iterator)|부분 일치에 대한 반복기 형식입니다.|
|[reference](#reference)|요소 참조의 형식입니다.|
|[size_type](#size_type)|부분 일치 수의 형식입니다.|
|[string_type](#string_type)|문자열의 형식입니다.|
|[value_type](#value_type)|부분 일치의 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[시작](#begin)|부분 일치 시퀀스의 시작을 지정합니다.|
|[empty](#empty)|부분 일치가 없는지 테스트합니다.|
|[end](#end)|부분 일치 시퀀스의 끝을 지정합니다.|
|[format](#format)|부분 일치의 서식을 지정합니다.|
|[get_allocator](#get_allocator)|저장된 할당자를 반환합니다.|
|[length](#length)|부분 일치의 길이를 반환합니다.|
|[max_size](#max_size)|부분 일치의 최대 수를 가져옵니다.|
|[position](#position)|하위 그룹의 시작 오프셋을 가져옵니다.|
|[prefix](#prefix)|첫 번째 부분 일치 전의 시퀀스를 가져옵니다.|
|[size](#size)|부분 일치 수를 계산합니다.|
|[str](#str)|부분 일치 항목을 반환합니다.|
|[접미사](#suffix)|마지막 부분 일치 후 시퀀스를 가져옵니다.|
|[스왑을](#swap)|두 match_results 개체를 바꿉니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 =](#op_eq)|match_results 개체를 복사합니다.|
|[연산자\[\]](#op_at)|하위 개체에 액세스합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<regex>

**네임스페이스:** std

## <a name="example"></a>예제

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a> match_results:: allocator_type

스토리지 관리를 위한 할당자의 형식입니다.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>설명

Typedef는 템플릿 인수 *할당* 의 동의어입니다.

## <a name="match_resultsbegin"></a><a name="begin"></a> match_results:: begin

부분 일치 시퀀스의 시작을 지정합니다.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>설명

멤버 함수는 시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 임의 액세스 반복기를 반환합니다.

## <a name="match_resultschar_type"></a><a name="char_type"></a> match_results:: char_type

요소의 형식입니다.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>설명

typedef는 `iterator_traits<BidIt>::value_type`형식의 동의어로, 검색된 문자 시퀀스의 요소 형식입니다.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a> match_results:: const_iterator

부분 일치에 대한 상수 반복기 형식입니다.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>설명

typedef는 제어되는 시퀀스의 상수 임의 액세스 반복기로 사용될 수 있는 개체를 설명합니다.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a> match_results:: const_reference

요소 const 참조의 형식입니다.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>설명

typedef는 제어되는 시퀀스의 요소에 대한 상수 참조로 사용될 수 있는 개체를 설명합니다.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a> match_results::d ifference_type

반복기 차이의 형식입니다.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>설명

typedef는 `iterator_traits<BidIt>::difference_type`형식의 동의어이며, 제어되는 시퀀스의 요소를 가리키는 두 반복기 사이의 차이를 나타낼 수 있는 개체에 대해 설명합니다.

## <a name="match_resultsempty"></a><a name="empty"></a> match_results:: empty

부분 일치가 없는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="remarks"></a>설명

멤버 함수는 정규식 검색에 실패한 경우에만 true를 반환합니다.

## <a name="match_resultsend"></a><a name="end"></a> match_results:: end

부분 일치 시퀀스의 끝을 지정합니다.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>설명

멤버 함수는 시퀀스 끝의 바로 다음을 가리키는 반복기를 반환합니다.

## <a name="match_resultsformat"></a><a name="format"></a> match_results:: format

부분 일치의 서식을 지정합니다.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>매개 변수

*OutIt*\
출력 반복기 형식입니다.

*제한이*\
쓸 출력 스트림입니다.

*bcp.fmt*\
서식 문자열입니다.

*flags*\
서식 플래그입니다.

### <a name="remarks"></a>설명

각 멤버 함수는 *fmt* 형식의 컨트롤 아래에 서식 있는 텍스트를 생성 합니다. 첫 번째 멤버 함수는 해당 인수에 의해 정의 된 시퀀스에 서식 있는 텍스트를 *쓰고를 반환* *합니다.* 두 번째 멤버 함수는 서식 있는 텍스트의 복사본을 포함 하는 문자열 개체를 반환 합니다.

서식 있는 텍스트를 생성하려면 서식 문자열의 리터럴 텍스트를 일반적으로 대상 시퀀스로 복사합니다. 서식 문자열의 각 이스케이프 시퀀스가 대표 텍스트로 대체됩니다. 복사 및 교체 정보는 함수에 전달된 서식 플래그에서 제어합니다.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a> match_results:: get_allocator

저장된 할당자를 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>설명

멤버 함수는에서 **`*this`** 개체를 할당 하는 데 사용 하는 할당자 개체의 복사본을 반환 합니다 `sub_match` .

## <a name="match_resultsiterator"></a><a name="iterator"></a> match_results:: iterator

부분 일치에 대한 반복기 형식입니다.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어되는 시퀀스의 임의 액세스 반복기로 사용될 수 있는 개체를 설명합니다.

## <a name="match_resultslength"></a><a name="length"></a> match_results:: length

부분 일치의 길이를 반환합니다.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>매개 변수

*부분*\
부분 일치 항목의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 `(*this)[sub].length()`를 반환합니다.

## <a name="match_resultsmatch_results"></a><a name="match_results"></a> match_results:: match_results

개체를 생성합니다.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>매개 변수

*#c4*\
저장할 할당자 개체입니다.

*오른쪽*\
복사할 match_results 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 부분 일치 항목을 보유하지 않는 `match_results` 개체를 구성합니다. 두 번째 생성자는 `match_results` *오른쪽* 의 복사본 인 개체를 생성 합니다.

## <a name="match_resultsmax_size"></a><a name="max_size"></a> match_results:: max_size

부분 일치의 최대 수를 가져옵니다.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 개체가 제어할 수 있는 가장 긴 시퀀스의 길이를 반환합니다.

## <a name="match_resultsoperator"></a><a name="op_eq"></a> match_results:: operator =

match_results 개체를 복사합니다.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
복사할 match_results 개체입니다.

### <a name="remarks"></a>설명

멤버 연산자는로 제어 되는 시퀀스를 **`*this`** *right* 로 제어 되는 시퀀스의 복사본으로 바꿉니다.

## <a name="match_resultsoperator"></a><a name="op_at"></a> match_results:: operator []

하위 개체에 액세스합니다.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>매개 변수

*개의*\
부분 일치 항목의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 요소 *n* 에 대 한 참조를 반환 하거나, `sub_match` `size() <= n` 캡처 그룹 *n* 이 일치 항목의 일부가 아닌 경우 빈 개체에 대 한 참조를 반환 합니다.

## <a name="match_resultsposition"></a><a name="position"></a> match_results::p o

하위 그룹의 시작 오프셋을 가져옵니다.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>매개 변수

*부분*\
부분 일치 항목의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 `std::distance(prefix().first, (*this)[sub].first)`, 즉 대상 시퀀스의 첫 번째 문자부터 제어되는 시퀀스의 `n` 요소가 가리키는 부분 일치의 첫 번째 문자까지 거리를 반환합니다.

## <a name="match_resultsprefix"></a><a name="prefix"></a> match_results::p 접두어

첫 번째 부분 일치 전의 시퀀스를 가져옵니다.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>설명

멤버 함수는 대상 시퀀스의 시작에서 시작되고 `sub_match<BidIt>` 에서 끝나는 문자 시퀀스 즉, 일치하는 하위 시퀀스 앞에 오는 텍스트를 가리키는 `(*this)[0].first`형식의 개체에 대한 참조를 반환합니다.

## <a name="match_resultsreference"></a><a name="reference"></a> match_results:: reference

요소 참조의 형식입니다.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>설명

이 형식은 `const_reference`형식의 동의어입니다.

## <a name="match_resultssize"></a><a name="size"></a> match_results:: size

부분 일치 수를 계산합니다.

```cpp
size_type size() const;
```

### <a name="remarks"></a>설명

멤버 함수는 검색에 사용된 정규식에서 캡처 그룹 수보다 1이 큰 수를 반환하고, 검색되지 않은 경우 0을 반환합니다.

## <a name="match_resultssize_type"></a><a name="size_type"></a> match_results:: size_type

부분 일치 수의 형식입니다.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>설명

이 형식은 `Alloc::size_type`형식의 동의어입니다.

## <a name="match_resultsstr"></a><a name="str"></a> match_results:: str

부분 일치 항목을 반환합니다.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>매개 변수

*부분*\
부분 일치 항목의 인덱스입니다.

### <a name="remarks"></a>설명

멤버 함수는 `string_type((*this)[sub])`를 반환합니다.

## <a name="match_resultsstring_type"></a><a name="string_type"></a> match_results:: string_type

문자열의 형식입니다.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>설명

이 형식은 `basic_string<char_type>`형식의 동의어입니다.

## <a name="match_resultssuffix"></a><a name="suffix"></a> match_results:: suffix

마지막 부분 일치 후 시퀀스를 가져옵니다.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `sub_match<BidIt>` 에서 시작되고 대상 시퀀스의 끝에서 끝나는 문자 시퀀스 즉, 일치하는 하위 시퀀스 뒤에 오는 텍스트를 가리키는 `(*this)[size() - 1].second` 형식의 개체에 대한 참조를 반환합니다.

## <a name="match_resultsswap"></a><a name="swap"></a> match_results:: swap

두 match_results 개체를 바꿉니다.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
바꾸려는 match_results 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 및의 내용을 **`*this`** 일정 한  시간 내에 교환 하 고 예외를 throw 하지 않습니다.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a> match_results:: value_type

부분 일치의 형식입니다.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>설명

typedef는 `sub_match<BidIt>`형식의 동의어입니다.

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)
