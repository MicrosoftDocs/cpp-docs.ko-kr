---
title: regex_error 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fae7d6e9e3a50ad6a0b78d2b47a732b6b5fa9fc0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853705"
---
# <a name="regexerror-class"></a>regex_error 클래스

잘못된 basic_regex 개체를 보고합니다.

## <a name="syntax"></a>구문

```cpp
class regex_error
 : public std::runtime_error {
public:
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;


};
```

## <a name="remarks"></a>설명

클래스는 `basic_regex` 개체의 사용 또는 생성 중 오류를 보고하기 위해 throw된 예외 개체를 설명합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<regex>

**네임스페이스:** std

## <a name="code"></a>  regex_error::code

오류 코드를 반환합니다.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>설명

멤버 함수는 개체의 생성자에 전달된 값을 반환합니다.

### <a name="example"></a>예제

```cpp
// std__regex__regex_error_code.cpp
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
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
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

## <a name="regex_error"></a>  regex_error::regex_error

개체를 생성합니다.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>매개 변수

`error` 오류 코드입니다.

### <a name="remarks"></a>설명

생성자는 `error`값을 보유하는 개체를 생성합니다.

### <a name="example"></a>예제

```cpp
// std__regex__regex_error_construct.cpp
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
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
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

## <a name="see-also"></a>참고자료

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 클래스](../standard-library/regex-constants-class.md)<br/>
[\<regex> 함수](../standard-library/regex-functions.md)<br/>
[regex_iterator 클래스](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 연산자](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 클래스](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 클래스](../standard-library/regex-traits-class.md)<br/>
[\<regex> 형식 정의](../standard-library/regex-typedefs.md)<br/>
