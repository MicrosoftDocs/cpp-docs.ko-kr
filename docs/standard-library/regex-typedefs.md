---
title: '&lt;regex&gt; 형식 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe7108c2eb370739494a2c6b8bc95fbdc1001840
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; 형식 정의

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>  cmatch 형식 정의

char match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>설명

이 형식은 `const char*` 형식의 반복기에 대한 템플릿 클래스 [match_results 클래스](../standard-library/match-results-class.md)의 특수화를 설명합니다.

## <a name="cregex_iterator"></a>  cregex_iterator 형식 정의

char regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `const char*` 형식의 반복기에 대한 템플릿 클래스 [regex_iterator 클래스](../standard-library/regex-iterator-class.md)의 특수화를 설명합니다.

## <a name="cregex_token_iterator"></a>  cregex_token_iterator 형식 정의

char regex_token_iterator에 대한 형식 정의

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `const char*` 형식의 반복기에 대한 템플릿 클래스 [regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)의 특수화를 설명합니다.

## <a name="csub_match"></a>  csub_match 형식 정의

char sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>설명

이 형식은 `const char*` 형식의 반복기에 대한 템플릿 클래스 [sub_match 클래스](../standard-library/sub-match-class.md)의 특수화를 설명합니다.

## <a name="regex"></a>  regex 형식 정의

char basic_regex에 대한 형식 정의입ㄴ니다.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>설명

이 형식은 `char` 형식의 반복기에 대한 템플릿 클래스 [basic_regex 클래스](../standard-library/basic-regex-class.md)의 특수화를 설명합니다.

> [!NOTE]
> 높은 비트 문자의 경우 `regex`에서 예기치 않은 결과가 반환됩니다. 0~127 범위를 벗어나는 값을 사용하는 경우 정의되지 않은 동작이 발생할 수 있습니다.

## <a name="smatch"></a>  smatch 형식 정의

string match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>설명

이 형식은 `string::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [match_results 클래스](../standard-library/match-results-class.md)의 특수화를 설명합니다.

## <a name="sregex_iterator"></a>  sregex_iterator 형식 정의

regex_iterator 문자열에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `string::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [regex_iterator 클래스](../standard-library/regex-iterator-class.md)의 특수화를 설명합니다.

## <a name="sregex_token_iterator"></a>  sregex_token_iterator 형식 정의

string regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `string::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)의 특수화를 설명합니다.

## <a name="ssub_match"></a>  ssub_match 형식 정의

string sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>설명

이 형식은 `string::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [sub_match 클래스](../standard-library/sub-match-class.md)의 특수화를 설명합니다.

## <a name="wcmatch"></a>  wcmatch 형식 정의

wchar_t match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>설명

이 형식은 `const wchar_t*` 형식의 반복기에 대한 템플릿 클래스 [match_results 클래스](../standard-library/match-results-class.md)의 특수화를 설명합니다.

## <a name="wcregex_iterator"></a>  wcregex_iterator 형식 정의

wchar_t regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `const wchar_t*` 형식의 반복기에 대한 템플릿 클래스 [regex_iterator 클래스](../standard-library/regex-iterator-class.md)의 특수화를 설명합니다.

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator 형식 정의

wchar_t regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `const wchar_t*` 형식의 반복기에 대한 템플릿 클래스 [regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)의 특수화를 설명합니다.

## <a name="wcsub_match"></a>  wcsub_match 형식 정의

wchar_t sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>설명

이 형식은 `const wchar_t*` 형식의 반복기에 대한 템플릿 클래스 [sub_match 클래스](../standard-library/sub-match-class.md)의 특수화를 설명합니다.

## <a name="wregex"></a>  wregex 형식 정의

wchar_t basic_regex에 대한 형식 정의입니다.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>설명

이 형식은 `wchar_t` 형식의 반복기에 대한 템플릿 클래스 [basic_regex 클래스](../standard-library/basic-regex-class.md)의 특수화를 설명합니다.

## <a name="wsmatch"></a>  wsmatch 형식 정의

wstring match_results에 대한 형식 정의입니다.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>설명

이 형식은 `wstring::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [match_results 클래스](../standard-library/match-results-class.md)의 특수화를 설명합니다.

## <a name="wsregex_iterator"></a>  wsregex_iterator 형식 정의

regex_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `wstring::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [regex_iterator 클래스](../standard-library/regex-iterator-class.md)의 특수화를 설명합니다.

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator 형식 정의

regex_token_iterator에 대한 형식 정의입니다.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>설명

이 형식은 `wstring::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)의 특수화를 설명합니다.

## <a name="wssub_match"></a>  wssub_match 형식 정의

wstring sub_match에 대한 형식 정의입니다.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>설명

이 형식은 `wstring::const_iterator` 형식의 반복기에 대한 템플릿 클래스 [sub_match 클래스](../standard-library/sub-match-class.md)의 특수화를 설명합니다.

## <a name="see-also"></a>참고자료

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 클래스](../standard-library/regex-constants-class.md)<br/>
[regex_error 클래스](../standard-library/regex-error-class.md)<br/>
[\<regex> 함수](../standard-library/regex-functions.md)<br/>
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 연산자](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 클래스](../standard-library/regex-traits-class.md)<br/>
