---
description: '자세한 정보: &lt; regex &gt; 형식 정의'
title: '&lt;regex&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 7814bd32e167d66c63c5ebf67221f461bc438c1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243798"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; 형식 정의

[cmatch](#cmatch)\
[cregex_iterator](#cregex_iterator)\
[cregex_token_iterator](#cregex_token_iterator)\
[csub_match](#csub_match)\
[regex](#regex)\
[smatch](#smatch)\
[sregex_iterator](#sregex_iterator)\
[sregex_token_iterator](#sregex_token_iterator)\
[ssub_match](#ssub_match)\
[wcmatch](#wcmatch)\
[wcregex_iterator](#wcregex_iterator)\
[wcregex_token_iterator](#wcregex_token_iterator)\
[wcsub_match](#wcsub_match)\
[wregex](#wregex)\
[wsmatch](#wsmatch)\
[wsregex_iterator](#wsregex_iterator)\
[wsregex_token_iterator](#wsregex_token_iterator)\
[wssub_match](#wssub_match)

## <a name="cmatch-typedef"></a><a name="cmatch"></a> cmatch Typedef

char match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Match_results 클래스](../standard-library/match-results-class.md) 의 특수화를 설명 합니다 `const char*` .

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a> cregex_iterator Typedef

char regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_iterator 클래스](../standard-library/regex-iterator-class.md) 의 특수화를 설명 합니다 `const char*` .

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a> cregex_token_iterator Typedef

char regex_token_iterator에 대한 형식 정의

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md) 의 특수화를 설명 합니다 `const char*` .

## <a name="csub_match-typedef"></a><a name="csub_match"></a> csub_match Typedef

char sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Sub_match 클래스](../standard-library/sub-match-class.md) 의 특수화를 설명 합니다 `const char*` .

## <a name="regex-typedef"></a><a name="regex"></a> regex Typedef

char basic_regex에 대한 형식 정의입ㄴ니다.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>설명

형식은 형식의 요소에 대 한 클래스 템플릿 [Basic_regex 클래스](../standard-library/basic-regex-class.md) 의 특수화를 설명 합니다 **`char`** .

> [!NOTE]
> 높은 비트 문자의 경우 `regex`에서 예기치 않은 결과가 반환됩니다. 0~127 범위를 벗어나는 값을 사용하는 경우 정의되지 않은 동작이 발생할 수 있습니다.

## <a name="smatch-typedef"></a><a name="smatch"></a> smatch Typedef

string match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Match_results 클래스](../standard-library/match-results-class.md) 의 특수화를 설명 합니다 `string::const_iterator` .

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a> sregex_iterator Typedef

regex_iterator 문자열에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_iterator 클래스](../standard-library/regex-iterator-class.md) 의 특수화를 설명 합니다 `string::const_iterator` .

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a> sregex_token_iterator Typedef

string regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md) 의 특수화를 설명 합니다 `string::const_iterator` .

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a> ssub_match Typedef

string sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Sub_match 클래스](../standard-library/sub-match-class.md) 의 특수화를 설명 합니다 `string::const_iterator` .

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a> wcmatch Typedef

wchar_t match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Match_results 클래스](../standard-library/match-results-class.md) 의 특수화를 설명 합니다 `const wchar_t*` .

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a> wcregex_iterator Typedef

wchar_t regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_iterator 클래스](../standard-library/regex-iterator-class.md) 의 특수화를 설명 합니다 `const wchar_t*` .

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a> wcregex_token_iterator Typedef

wchar_t regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md) 의 특수화를 설명 합니다 `const wchar_t*` .

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a> wcsub_match Typedef

wchar_t sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Sub_match 클래스](../standard-library/sub-match-class.md) 의 특수화를 설명 합니다 `const wchar_t*` .

## <a name="wregex-typedef"></a><a name="wregex"></a> wregex Typedef

wchar_t basic_regex에 대한 형식 정의입니다.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>설명

형식은 형식의 요소에 대 한 클래스 템플릿 [Basic_regex 클래스](../standard-library/basic-regex-class.md) 의 특수화를 설명 합니다 **`wchar_t`** .

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a> wsmatch Typedef

wstring match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Match_results 클래스](../standard-library/match-results-class.md) 의 특수화를 설명 합니다 `wstring::const_iterator` .

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a> wsregex_iterator Typedef

regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_iterator 클래스](../standard-library/regex-iterator-class.md) 의 특수화를 설명 합니다 `wstring::const_iterator` .

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a> wsregex_token_iterator Typedef

regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md) 의 특수화를 설명 합니다 `wstring::const_iterator` .

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a> wssub_match Typedef

wstring sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>설명

이 형식은 형식의 반복기에 대 한 클래스 템플릿 [Sub_match 클래스](../standard-library/sub-match-class.md) 의 특수화를 설명 합니다 `wstring::const_iterator` .

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)\
[regex_constants 클래스](../standard-library/regex-constants-class.md)\
[regex_error 클래스](../standard-library/regex-error-class.md)\
[\<regex> 역함수](../standard-library/regex-functions.md)\
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)\
[\<regex> 작업자](../standard-library/regex-operators.md)\
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)\
[regex_traits 클래스](../standard-library/regex-traits-class.md)
