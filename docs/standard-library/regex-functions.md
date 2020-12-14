---
description: '자세한 정보: &lt; regex &gt; 함수'
title: '&lt;regex&gt; 함수'
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: aa2186d7b394d1b603d5600d1977efa8d268a32f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253340"
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt; 함수

|Name|설명|
|-|-|
|[regex_match](#regex_match)|정규식이 전체 대상 문자열과 일치하는지 여부를 테스트합니다.|
|[regex_replace](#regex_replace)|일치하는 정규식을 바꿉니다.|
|[regex_search](#regex_search)|정규식 일치 항목을 검색합니다.|
|[스왑을](#swap)|두 `basic_regex` 또는 `match_results` 개체를 교환 합니다.|

## <a name="regex_match"></a><a name="regex_match"></a> regex_match

정규식이 전체 대상 문자열과 일치하는지 여부를 테스트합니다.

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>매개 변수

*BidIt*\
부분 일치에 대한 반복기 형식입니다. 일반적인 경우에는, 또는 중 하나입니다 `string::const_iterator` `wstring::const_iterator` `const char*` `const wchar_t*` .

*#C4*\
일치 결과 할당자 클래스입니다.

*E*\
일치 항목을 찾을 요소의 형식입니다. 일반적인 경우에는 `string` , `wstring` `char*` 또는 `wchar_t*` 입니다.

*RXtraits*\
요소에 대한 특성 클래스입니다.

*Alloc2*\
정규식 할당자 클래스입니다.

*IOtraits*\
문자열 특성 클래스입니다.

*IOalloc*\
문자열 할당자 클래스입니다.

*flags*\
일치에 대한 플래그입니다.

*기본*\
일치하는 시퀀스의 시작입니다.

*최신*\
일치하는 시퀀스의 끝입니다.

*맞추기*\
일치 결과입니다. Elem type: [smatch](../standard-library/regex-typedefs.md#smatch) for `string` , [wsmatch](../standard-library/regex-typedefs.md#wsmatch) for `wstring` , [cmatch](../standard-library/regex-typedefs.md#cmatch) for `char*` 또는 [wcmatch](../standard-library/regex-typedefs.md#wcmatch) 에 해당 `wchar_t*` 합니다.

*ptr*\
일치하는 시퀀스의 시작에 대한 포인터입니다. *Ptr* 이 이면 `char*` 및를 사용 `cmatch` `regex` 합니다. 그런 다음 *ptr* 이 `wchar_t*` 및를 사용 `wcmatch` `wregex` 합니다.

*재실행*\
일치 항목을 찾을 정규식입니다. 및의 경우를 입력 `regex` `string` `char*` `wregex` 하 고, 및의 경우을 입력 `wstring` `wchar_t*` 합니다.

*문자열*\
일치하는 문자열입니다. *Elem* 형식에 해당 합니다.

### <a name="remarks"></a>설명

각 템플릿 함수는 전체 피연산자 시퀀스 *str* 이 정규식 인수 *re* 와 정확히 일치 하는 경우에만 true를 반환 합니다. [Regex_search](../standard-library/regex-functions.md#regex_search) 를 사용 하 여 대상 시퀀스 내에서 부분 문자열을 일치 시키고 `regex_iterator` 여러 개의 일치 항목을 찾습니다. `match_results` 개체를 사용하는 함수는 일치에 성공했는지 여부를 반영하도록 멤버를 설정하고 그런 경우 정규식의 다양한 캡처 그룹이 캡처됩니다.

`match_results` 개체를 사용하는 함수는 일치에 성공했는지 여부를 반영하도록 멤버를 설정하고 그런 경우 정규식의 다양한 캡처 그룹이 캡처됩니다.

### <a name="example"></a>예제

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a><a name="regex_replace"></a> regex_replace

일치하는 정규식을 바꿉니다.

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>매개 변수

*OutIt*\
대체에 대한 반복기 형식입니다.

*BidIt*\
부분 일치에 대한 반복기 형식입니다.

*RXtraits*\
요소에 대한 특성 클래스입니다.

*#C4*\
정규식 할당자 클래스입니다.

*E*\
일치 항목을 찾을 요소의 형식입니다.

*flags*\
일치에 대한 플래그입니다.

*기본*\
일치하는 시퀀스의 시작입니다.

*bcp.fmt*\
대체에 대한 형식입니다.

*최신*\
일치하는 시퀀스의 끝입니다.

*제한이*\
출력 반복기입니다.

*재실행*\
일치 항목을 찾을 정규식입니다.

*문자열*\
일치하는 문자열입니다.

### <a name="remarks"></a>설명

첫 번째 함수는 [Regex_iterator 클래스](../standard-library/regex-iterator-class.md) 개체를 생성 하 고이 개체를 사용 하 여 `iter(first, last, re, flags)` 입력 범위를 `[first, last)` 일련의 버킷이라고로 분할 `T0 M0 T1 M1...TN-1 MN-1 TN` `Mn` 합니다. 여기서은 반복기에서 검색 한 n 번째 일치 항목입니다. 일치하는 항목이 없으면 `T0`은 전체 입력 범위이고 `N`은 0입니다. `(flags & format_first_only) != 0`이면 첫 번째 일치 항목만 사용되고 `T1`은 일치 항목 뒤에 오는 모든 입력 텍스트이며 `N`은 1입니다. 범위에 있는 각에 대해 `i` `[0, N)` `(flags & format_no_copy) == 0` 범위의 텍스트를 `Ti` 반복기 *출력* 에 복사 하는 경우입니다. 그런 다음 `m.format(out, fmt, flags)` 를 호출 `m` 합니다. 여기서는 `match_results` `iter` 하위 시퀀스에 대 한 iterator 개체에서 반환 `Mi` 되는 개체입니다. 마지막으로, `(flags & format_no_copy) == 0` 범위의 텍스트를 `TN` 반복기 *out* 에 복사 합니다. 함수는를 *반환 합니다*.

두 번째 함수는 형식 `basic_string<charT>`의 지역 변수 `result`를 생성하고 `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`를 호출합니다. `result`를 반환합니다.

### <a name="example"></a>예제

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a><a name="regex_search"></a> regex_search

정규식 일치 항목을 검색합니다.

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>매개 변수

*BidIt*\
부분 일치에 대한 반복기 형식입니다.

*#C4*\
일치 결과 할당자 클래스입니다.

*E*\
일치 항목을 찾을 요소의 형식입니다.

*RXtraits*\
요소에 대한 특성 클래스입니다.

*Alloc2*\
정규식 할당자 클래스입니다.

*IOtraits*\
문자열 특성 클래스입니다.

*IOalloc*\
문자열 할당자 클래스입니다.

*flags*\
일치에 대한 플래그입니다.

*기본*\
일치하는 시퀀스의 시작입니다.

*최신*\
일치하는 시퀀스의 끝입니다.

*맞추기*\
일치 결과입니다.

*ptr*\
일치하는 시퀀스의 시작에 대한 포인터입니다.

*재실행*\
일치 항목을 찾을 정규식입니다.

*문자열*\
일치하는 문자열입니다.

### <a name="remarks"></a>설명

각 템플릿 함수는 해당 피연산자 *시퀀스에서 정규식 인수에 대* 한 검색이 성공 하는 경우에만 true를 반환 합니다. `match_results` 개체를 사용하는 함수는 검색에 성공했는지를 반영하도록 구성원를 설정하고 그런 경우 정규식의 다양한 캡처 그룹이 캡처됩니다.

### <a name="example"></a>예제

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 `basic_regex` 또는 `match_results` 개체를 교환 합니다.

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>매개 변수

*E*\
일치 항목을 찾을 요소의 형식입니다.

*RXtraits*\
요소에 대한 특성 클래스입니다.

### <a name="remarks"></a>설명

템플릿 함수는 일정한 시간에 개별 인수의 내용을 교환하며 예외를 throw하지 않습니다.

### <a name="example"></a>예제

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)\
[regex_constants 클래스](../standard-library/regex-constants-class.md)\
[regex_error 클래스](../standard-library/regex-error-class.md)\
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)\
[\<regex> 작업자](../standard-library/regex-operators.md)\
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)\
[regex_traits 클래스](../standard-library/regex-traits-class.md)\
[\<regex> 정의](../standard-library/regex-typedefs.md)
