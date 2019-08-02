---
title: regex_error 클래스
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451649"
---
# <a name="regexerror-class"></a>regex_error 클래스

잘못된 basic_regex 개체를 보고합니다.

## <a name="syntax"></a>구문

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>설명

클래스는 `basic_regex` 개체의 사용 또는 생성 중 오류를 보고하기 위해 throw된 예외 개체를 설명합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[regex_error](#regex_error)|개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[코드](#code)|오류 코드를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<regex>

**네임스페이스:** std

## <a name="example"></a>예제

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="code"></a>  regex_error::code

오류 코드를 반환합니다.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>설명

멤버 함수는 개체의 생성자에 전달된 값을 반환합니다.

## <a name="regex_error"></a>  regex_error::regex_error

개체를 생성합니다.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>매개 변수

*error*\
오류 코드입니다.

### <a name="remarks"></a>설명

생성자는 값 *오류*를 포함 하는 개체를 생성 합니다.

## <a name="see-also"></a>참고자료

[\<regex>](../standard-library/regex.md)\
[regex_constants 클래스](../standard-library/regex-constants-class.md)\
[\<regex > 함수](../standard-library/regex-functions.md)\
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)\
[\<regex > 연산자](../standard-library/regex-operators.md)\
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)\
[regex_traits 클래스](../standard-library/regex-traits-class.md)\
[\<regex> 형식 정의](../standard-library/regex-typedefs.md)
