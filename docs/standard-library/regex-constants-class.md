---
description: Regex_constants 네임 스페이스에 대해 자세히 알아보세요.
title: regex_constants 클래스
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: d33f9d45023453281714e5585ab6ab33ee1f7857
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250519"
---
# <a name="regex_constants-namespace"></a>regex_constants 네임스페이스

정규식 플래그에 대한 네임스페이스입니다.

## <a name="syntax"></a>구문

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>설명

네임스페이스 `regex_constants`는 여러 플래그 형식과 관련 플래그 값을 캡슐화합니다.

|Name|설명|
|-|-|
|[error_type](#error_type)|정규식 구문 오류 보고에 대한 플래그입니다.|
|[match_flag_type](#match_flag_type)|정규식 일치 옵션에 대한 플래그입니다.|
|[syntax_option_type](#syntax_option_type)|구문 옵션을 선택하기 위한 플래그입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<regex>

**네임스페이스:** std

## <a name="regex_constantserror_type"></a><a name="error_type"></a> regex_constants:: error_type

정규식 구문 오류 보고에 대한 플래그입니다.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>설명

형식은 오류 플래그를 저장할 수 있는 개체를 설명하는 열거 형식입니다. 고유 플래그 값은 다음과 같습니다.

`error_backref` -- 식에 잘못된 역참조가 포함되었습니다.

`error_badbrace` 식에 잘못된 개수의 { } 식이 포함되었습니다.

`error_badrepeat` -- 반복 실행 식(대부분의 컨텍스트에서 '*', '?', '+', '{' 중 하나)이 식 뒤에 오지 않았습니다.

`error_brace` -- 식에 일치하지 않는 '(' 또는 ')'가 포함되었습니다.

`error_brack` -- 식에 일치하지 않는 '(' 또는 ')'가 포함되었습니다.

`error_collate` -- 식에 잘못된 데이터 정렬 요소 이름이 포함되었습니다.

`error_complexity` -- 시도된 일치가 너무 복잡하여 실패했습니다.

`error_ctype` -- 식에 잘못된 문자 클래스 이름이 포함되었습니다.

`error_escape` -- 식에 잘못된 이스케이프 시퀀스가 포함되었습니다.

`error_paren` -- 식에 일치하지 않는 '(' 또는 ')'가 포함되었습니다.

`error_parse` - 식을 구문 분석하지 못했습니다.

`error_range` -- 식에 잘못된 문자 범위 지정자가 포함되었습니다.

`error_space` -- 사용 가능한 리소스가 부족하여 정규식을 구문 분석하지 못했습니다.

`error_stack` -- 사용 가능한 메모리가 부족하여 시도된 일치가 실패했습니다.

`error_syntax` -- 구문 오류를 구문 분석하지 못했습니다.

`error_backref` -- 식에 잘못된 역참조가 포함되었습니다.

## <a name="regex_constantsmatch_flag_type"></a><a name="match_flag_type"></a> regex_constants:: match_flag_type

정규식 일치 옵션에 대한 플래그입니다.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>설명

형식은 정규식에 대해 텍스트 시퀀스를 일치시킬 때 사용할 옵션 및 텍스트를 대체할 때 사용할 형식 플래그에 대해 설명하는 비트 마스크 형식입니다. 옵션은 `|`와 함께 사용할 수 있습니다.

일치 옵션은 다음과 같습니다.

`match_default`

`match_not_bol` -- 대상 시퀀스의 첫 번째 위치를 줄의 시작으로 처리하지 않습니다.

`match_not_eol` -- 대상 시퀀스의 끝을 지난 위치를 줄의 끝으로 처리하지 않습니다.

`match_not_bow` -- 대상 시퀀스의 첫 번째 위치를 단어의 시작으로 처리하지 않습니다.

`match_not_eow` -- 대상 시퀀스의 끝을 지난 위치를 단어의 끝으로 처리하지 않습니다.

`match_any` -- 둘 이상의 일치 항목이 가능한 경우 임의 일치 항목이 허용됩니다.

`match_not_null` -- 빈 시퀀스를 일치 항목으로 처리하지 않습니다.

`match_continuous` -- 대상 시퀀스의 시작 부분이 아닌 다른 위치에서 일치 항목을 검색하지 않습니다.

`match_prev_avail` -- `--first`는 유효한 반복기이며, 설정된 경우 `match_not_bol` 및 `match_not_bow`를 무시합니다.

형식 플래그는 다음과 같습니다.

`format_default` -- ECMAScript 형식 규칙을 사용합니다.

`format_sed` -- sed 형식 규칙을 사용합니다.

`format_no_copy` -- 정규식과 일치하지 않는 텍스트를 복사하지 않습니다.

`format_first_only` -- 첫 번째 일치 항목 뒤에서 일치 항목을 검색하지 않습니다.

## <a name="regex_constantssyntax_option_type"></a><a name="syntax_option_type"></a> regex_constants:: syntax_option_type

구문 옵션을 선택하기 위한 플래그입니다.

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>설명

형식은 정규식을 컴파일할 때 사용할 언어 지정자 및 구문 한정자를 설명하는 비트 마스크 형식입니다. 옵션은 `|`와 함께 사용할 수 있습니다. 한 번에 둘 이상의 언어 지정자를 사용할 수 없습니다.

언어 지정자는 다음과 같습니다.

`ECMAScript` -- ECMAScript로 컴파일

`basic` -- BRE로 컴파일

`extended` -- ERE로 컴파일

`awk` -- awk로 컴파일

`grep` -- grep로 컴파일

`egrep` -- egrep로 컴파일

구문 한정자는 다음과 같습니다.

`icase` -- 일치 항목이 대/소문자를 구분하지 않도록 함

`nosubs` -- 구현에서 캡처 그룹의 내용을 추적하지 않아도 됨

`optimize` -- 구현에서 정규식 컴파일 속도가 아닌 일치 속도를 강조해야 함

`collate` -- 일치 항목이 로캘을 구분하도록 함

## <a name="see-also"></a>참고 항목

[\<regex>](../standard-library/regex.md)\
[regex_error 클래스](../standard-library/regex-error-class.md)\
[\<regex> 역함수](../standard-library/regex-functions.md)\
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)\
[\<regex> 작업자](../standard-library/regex-operators.md)\
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)\
[regex_traits 클래스](../standard-library/regex-traits-class.md)\
[\<regex> 정의](../standard-library/regex-typedefs.md)
