---
title: '&lt;regex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 109d7ee960b6788468c473e88321a00a38fb4379
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="ltregexgt"></a>&lt;regex&gt;

[정규식(C++)](../standard-library/regular-expressions-cpp.md)을 구문 분석하는 템플릿 클래스와 텍스트에서 정규식 개체와 일치하는 항목을 검색하는 여러 템플릿 클래스 및 함수를 정의합니다.

## <a name="syntax"></a>구문

```cpp
#include <regex>
```

## <a name="remarks"></a>설명

정규식 개체를 만들려면 템플릿 클래스 [basic_regex 클래스](../standard-library/basic-regex-class.md) 또는 해당 특수화 [regex](../standard-library/regex-typedefs.md#regex) 및 [wregex](../standard-library/regex-typedefs.md#wregex) 중 하나를 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 형식의 구문 플래그와 함께 사용합니다.

정규식 개체에 일치 하는 항목에 대 한 텍스트를 검색 하려면 템플릿 함수를 사용 하 여 [regex_match](../standard-library/regex-functions.md#regex_match) 및 [regex_search](../standard-library/regex-functions.md#regex_search)형식의 일치 플래그와 함께 [regex_constants::match_ flag_type](../standard-library/regex-constants-class.md#match_flag_type)합니다. 이러한 함수는 템플릿 클래스 [match_results 클래스](../standard-library/match-results-class.md)와 해당 특수화 [cmatch](../standard-library/regex-typedefs.md#cmatch), [wcmatch](../standard-library/regex-typedefs.md#wcmatch), [smatch](../standard-library/regex-typedefs.md#smatch) 및 [wsmatch](../standard-library/regex-typedefs.md#wsmatch)를 템플릿 클래스 [sub_match 클래스](../standard-library/sub-match-class.md)와 해당 특수화 [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match) 및 [wssub_match](../standard-library/regex-typedefs.md#wssub_match)와 함께 사용하여 결과를 반환합니다.

정규식 개체와 일치 하는 텍스트를 바꾸려면 템플릿 함수를 사용 하 여 [regex_replace](../standard-library/regex-functions.md#regex_replace)형식의 일치 플래그와 함께 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type)합니다.

정규식 개체의 여러 일치 항목을 반복하려면 템플릿 클래스 [regex_iterator 클래스](../standard-library/regex-iterator-class.md) 및 [regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md) 또는 해당 특수화 [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator), 또는 [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator) 중 하나를 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type) 형식의 일치 플래그와 함께 사용합니다.

정규식의 문법에 대한 세부 정보를 수정하려면 정규식 특성을 구현하는 클래스를 작성합니다.

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|정규식을 래핑합니다.|
|[match_results](../standard-library/match-results-class.md)|부분 일치 시퀀스를 보유합니다.|
|[regex_constants](../standard-library/regex-constants-class.md)|분류된 상수를 보유합니다.|
|[regex_error](../standard-library/regex-error-class.md)|잘못된 정규식을 보고합니다.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|일치 결과를 반복합니다.|
|[regex_traits](../standard-library/regex-traits-class.md)|일치를 위해 요소의 특징을 설명합니다.|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|일치를 위해 `char`의 특징을 설명합니다.|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|일치를 위해 `wchar_t`의 특징을 설명합니다.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|부분 일치를 반복합니다.|
|[sub_match](../standard-library/sub-match-class.md)|부분 일치를 설명합니다.|

### <a name="type-definitions"></a>형식 정의

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|`char` `match_results`에 대한 형식 정의입니다.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|`char` `regex_iterator`에 대한 형식 정의입니다.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|`char` `regex_token_iterator`에 대한 형식 정의입니다.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|`char` `sub_match`에 대한 형식 정의입니다.|
|[regex](../standard-library/regex-typedefs.md#regex)|`char` `basic_regex`에 대한 형식 정의입니다.|
|[smatch](../standard-library/regex-typedefs.md#smatch)|`string` `match_results`에 대한 형식 정의입니다.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|`string` `regex_iterator`에 대한 형식 정의입니다.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|`string` `regex_token_iterator`에 대한 형식 정의입니다.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|`string` `sub_match`에 대한 형식 정의입니다.|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|`wchar_t` `match_results`에 대한 형식 정의입니다.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|`wchar_t` `regex_iterator`에 대한 형식 정의입니다.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|`wchar_t` `regex_token_iterator`에 대한 형식 정의입니다.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|`wchar_t` `sub_match`에 대한 형식 정의입니다.|
|[wregex](../standard-library/regex-typedefs.md#wregex)|`wchar_t` `basic_regex`에 대한 형식 정의입니다.|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|`wstring` `match_results`에 대한 형식 정의입니다.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|`wstring` `regex_iterator`에 대한 형식 정의입니다.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|`wstring` `regex_token_iterator`에 대한 형식 정의입니다.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|`wstring` `sub_match`에 대한 형식 정의입니다.|

### <a name="functions"></a>함수

|함수|설명|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|정규식과 정확히 일치합니다.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|일치하는 정규식을 바꿉니다.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|정규식 일치 항목을 검색합니다.|
|[swap](../standard-library/regex-functions.md#swap)|`basic_regex` 또는 `match_results` 개체를 교환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|다양한 개체가 같은지 비교합니다.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|다양한 개체가 같지 않은지 비교합니다.|
|[operator<](../standard-library/regex-operators.md#op_lt)|다양한 개체가 보다 작은지 비교합니다.|
|[operator\<=](../standard-library/regex-operators.md#op_gt_eq)|다양한 개체가 보다 작거나 같은지 비교합니다.|
|[operator>](../standard-library/regex-operators.md#op_gt)|다양한 개체가 보다 큰지 비교합니다.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|다양한 개체가 보다 크거나 같은지 비교합니다.|
|[operator<<](../standard-library/regex-operators.md#op_lt_lt)|스트림에 `sub_match`를 삽입합니다.|

## <a name="see-also"></a>참고자료

[정규식(C++)](../standard-library/regular-expressions-cpp.md)<br/>
[regex_constants 클래스](../standard-library/regex-constants-class.md)<br/>
[regex_error 클래스](../standard-library/regex-error-class.md)<br/>
[\<regex> 함수](../standard-library/regex-functions.md)<br/>
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 연산자](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 클래스](../standard-library/regex-traits-class.md)<br/>
[\<regex> 형식 정의](../standard-library/regex-typedefs.md)<br/>
