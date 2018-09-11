---
title: basic_regex 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::basic_regex
dev_langs:
- C++
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 531ecc65a23e0eecd3480c397c081061cffaf9d8
ms.sourcegitcommit: 27b5712badd09a09c499d887e2e4cf2208a28603
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384945"
---
# <a name="basicregex-class"></a>basic_regex 클래스

정규식을 래핑합니다.

## <a name="syntax"></a>구문

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>매개 변수

*Elem*<br/>
일치 항목을 찾을 요소의 형식입니다.

*RXtraits*<br/>
요소에 대한 특성 클래스입니다.

## <a name="remarks"></a>설명

템플릿 클래스는 정규식을 포함하는 개체에 대해 설명합니다. 이 템플릿 클래스의 개체는 템플릿 함수는 전달할 수 있습니다 [regex_match](../standard-library/regex-functions.md#regex_match)를 [regex_search](../standard-library/regex-functions.md#regex_search), 및 [regex_replace](../standard-library/regex-functions.md#regex_replace), 적합 한 텍스트 문자열 인수와 함께 텍스트 정규식과 일치 하는 텍스트를 검색 합니다. 형식 정의 사용 하 여이 템플릿 클래스의 두 가지 특수화 [regex](../standard-library/regex-typedefs.md#regex) 형식의 요소에 대해 **char**, 및 [wregex](../standard-library/regex-typedefs.md#wregex) 형식의 요소에 대해  **wchar_t**합니다.

템플릿 인수 *RXtraits* 여러 중요 속성의 템플릿 클래스를 지 원하는 정규식 구문에 대해 설명 합니다. 이러한 정규식 특성을 지정하는 클래스는 템플릿 클래스 [regex_traits 클래스](../standard-library/regex-traits-class.md)의 개체와 외부 인터페이스가 동일해야 합니다.

일부 함수는 정규식을 정의하는 피연산자 시퀀스를 사용합니다. 그러한 피연산자 시퀀스를 여러 방법으로 지정할 수 있습니다.

`ptr` -null로 끝나는 시퀀스 (예: C 문자열에 대 한 *Elem* 형식의 **char**)부터 `ptr` (되어서는 안 됨 null 포인터)를 여기서 종료 요소는 값 `value_type()` 피연산자 시퀀스의 일부가 아니며

`ptr`, `count` -- `count`(null 포인터는 안 됨)에서 시작하는 `ptr` 요소의 시퀀스

`str` -- `basic_string` 개체 `str`에서 지정한 시퀀스

`first`, `last` -- 범위 `first`에서 반복기 `last` 및 `[first, last)`에 의해 구분된 요소의 시퀀스

`right` -- `basic_regex` 개체 `right`

이러한 멤버 함수는 인수로 걸립니다 `flags` 에서 설명 하는 것 외에도 정규식 해석 위한 다양 한 옵션을 지정 하는 *RXtraits* 형식.

### <a name="members"></a>멤버

|멤버|기본값|
|-|-|
|공용 정적 const flag_type icase|regex_constants::icase|
|공용 정적 const flag_type nosubs|regex_constants::nosubs|
|공용 정적 const flag_type 최적화|regex_constants::optimize|
|공용 정적 const flag_type collate|regex_constants::collate|
|공용 정적 const flag_type ECMAScript|regex_constants::ECMAScript|
|공용 정적 기본 const flag_type|regex_constants::basic|
|공용 정적 const flag_type 확장|regex_constants::extended|
|공용 정적 const flag_type awk|regex_constants::awk|
|공용 정적 const flag_type grep|regex_constants::grep|
|공용 정적 const flag_type egrep|regex_constants::egrep|
|개인 RXtraits 특성||

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[basic_regex](#basic_regex)|Regular Expression 개체를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[flag_type](#flag_type)|구문 옵션 플래그의 형식입니다.|
|[locale_type](#locale_type)|저장된 로캘 개체의 형식입니다.|
|[value_type](#value_type)|요소 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[assign](#assign)|정규식 개체에 값을 할당합니다.|
|[flags](#flags)|구문 옵션 플래그를 반환합니다.|
|[get_loc](#get_loc)|저장된 로캘 개체를 반환합니다.|
|[imbue](#imbue)|저장된 로캘 개체를 변경합니다.|
|[mark_count](#mark_count)|일치하는 하위 식의 수를 반환합니다.|
|[swap](#swap)|두 정규식 개체를 바꿉니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator=](#op_eq)|정규식 개체에 값을 할당합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<regex>

**네임스페이스:** std

## <a name="example"></a>예제

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="assign"></a>  basic_regex::assign

정규식 개체에 값을 할당합니다.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>매개 변수

*STtraits*<br/>
문자열 소스에 대한 특성 클래스입니다.

*STalloc*<br/>
문자열 소스에 대한 할당자 클래스입니다.

*InIt*<br/>
범위 소스에 대한 입력 반복기 형식입니다.

*right*<br/>
복사할 Regex 소스입니다.

*ptr*<br/>
복사할 시퀀스의 시작에 대한 포인터입니다.

*flags*<br/>
복사하는 동안 추가할 구문 옵션 플래그입니다.

*len/TD >*<br/>
복사할 시퀀스의 길이입니다.

*str*<br/>
복사할 문자열입니다.

*first*<br/>
복사할 시퀀스의 시작입니다.

*last*<br/>
복사할 시퀀스의 끝입니다.

*IList*<br/>
복사할 initializer_list입니다.

### <a name="remarks"></a>설명

각 멤버 함수는 `*this`에 보유된 정규식을 피연산자 시퀀스에 설명된 정규식으로 대체한 후 `*this`를 반환합니다.

## <a name="basic_regex"></a>  basic_regex::basic_regex

Regular Expression 개체를 생성합니다.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>매개 변수

*STtraits*<br/>
문자열 소스에 대한 특성 클래스입니다.

*STalloc*<br/>
문자열 소스에 대한 할당자 클래스입니다.

*InIt*<br/>
범위 소스에 대한 입력 반복기 형식입니다.

*right*<br/>
복사할 Regex 소스입니다.

*ptr*<br/>
복사할 시퀀스의 시작에 대한 포인터입니다.

*flags*<br/>
복사하는 동안 추가할 구문 옵션 플래그입니다.

*len/TD >*<br/>
복사할 시퀀스의 길이입니다.

*str*<br/>
복사할 문자열입니다.

*first*<br/>
복사할 시퀀스의 시작입니다.

*last*<br/>
복사할 시퀀스의 끝입니다.

*IList*<br/>
복사할 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자가 `RXtraits` 형식의 기본 생성된 개체를 저장합니다.

첫 번째 생성자는 빈 `basic_regex` 개체를 생성합니다. 다른 생성자는 피연산자 시퀀스에서 설명하는 정규식을 보유하는 `basic_regex` 개체를 생성합니다.

빈 `basic_regex` 개체에 전달 될 때 문자 시퀀스에 맞지 않습니다 [regex_match](../standard-library/regex-functions.md#regex_match)합니다 [regex_search](../standard-library/regex-functions.md#regex_search), 또는 [regex_replace](../standard-library/regex-functions.md#regex_replace)합니다.

## <a name="flag_type"></a>  basic_regex::flag_type

구문 옵션 플래그의 형식입니다.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>설명

이 형식은 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type)의 동의어입니다.

## <a name="flags"></a>  basic_regex::flags

구문 옵션 플래그를 반환합니다.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>설명

멤버 함수는 [basic_regex::assign](#assign) 멤버 함수 중 하나에 대한 최근 호출에 전달된 `flag_type` 인수의 값을 반환하거나, 이러한 호출이 수행되지 않은 경우 생성자에 전달된 값을 반환합니다.

## <a name="getloc"></a>  basic_regex::getloc

저장된 로캘 개체를 반환합니다.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`을 반환합니다.

## <a name="imbue"></a>  basic_regex::imbue

저장된 로캘 개체를 변경합니다.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>매개 변수

*Loc*<br/>
저장할 로캘 개체입니다.

### <a name="remarks"></a>설명

멤버 함수는 `*this`를 비우고 `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`를 반환합니다.

## <a name="locale_type"></a>  basic_regex::locale_type

저장된 로캘 개체의 형식입니다.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>설명

이 형식은 [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type)의 동의어입니다.

## <a name="mark_count"></a>  basic_regex::mark_count

일치하는 하위 식의 수를 반환합니다.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>설명

멤버 함수는 정규식의 캡처 그룹 수를 반환합니다.

## <a name="op_eq"></a>  basic_regex::operator=

정규식 개체에 값을 할당합니다.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>매개 변수

*STtraits*<br/>
문자열 소스에 대한 특성 클래스입니다.

*STalloc*<br/>
문자열 소스에 대한 할당자 클래스입니다.

*right*<br/>
복사할 Regex 소스입니다.

*str*<br/>
복사할 문자열입니다.

### <a name="remarks"></a>설명

각 연산자는 `*this` 에 보유된 정규식을 피연산자 시퀀스에 설명된 정규식으로 대체한 후 `*this`를 반환합니다.

## <a name="swap"></a>  basic_regex::swap

두 정규식 개체를 바꿉니다.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>매개 변수

*right*<br/>
바꾸려는 정규식 개체입니다.

### <a name="remarks"></a>설명

멤버 함수 간에 정규식을 바꿉니다 `*this` 하 고 *오른쪽*합니다. 일정한 시간에 이 작업을 수행하고 예외를 throw하지 않습니다.

## <a name="value_type"></a>  basic_regex::value_type

요소 형식입니다.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수에 대 한 동의어 *Elem*합니다.

## <a name="see-also"></a>참고자료

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits 클래스](../standard-library/regex-traits-class.md)<br/>
