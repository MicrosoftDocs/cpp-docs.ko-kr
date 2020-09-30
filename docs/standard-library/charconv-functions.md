---
title: '&lt;charconv &gt; 함수'
description: <charconv>정수 또는 부동 소수점 값을 문자로 변환 하는 라이브러리 함수에 대해 설명 합니다.
ms.date: 08/20/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: cde2ae6b6275543ec74d859b9a953f8673da9c2b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507743"
---
# <a name="ltcharconvgt-functions"></a>&lt;charconv &gt; 함수

헤더에는 \<charconv> 다음과 같은 비 멤버 함수가 포함 되어 있습니다.

| **멤버가 아닌 함수** | **설명** |
|-|-|
|[to_chars](#to_chars) | 정수 또는 부동 소수점 값을의 시퀀스로 변환 **`char`** 합니다. |
|[from_chars](#from_chars) | 의 시퀀스를 **`char`** 정수 또는 부동 소수점 값으로 변환 합니다. |

이러한 변환 함수는 성능을 위해 조정 되며 최단 왕복 동작을 지원 합니다. 최단 왕복 동작 이란 숫자를 문자로 변환 하는 경우 해당 문자를 다시 부동 소수점으로 변환 하는 경우 원래 숫자를 복구할 수 있도록 충분 한 소수 자릿수가 기록 됨을 의미 합니다.

- Chars를 숫자로 변환 하는 경우 숫자 값을 null로 종료할 필요가 없습니다. 마찬가지로 숫자를 문자로 변환 하는 경우 결과는 null로 종료 되지 않습니다.
- 변환 함수는 메모리를 할당 하지 않습니다. 모든 경우에서 버퍼를 소유 합니다.
- 변환 함수는를 throw 하지 않습니다. 변환이 성공 했는지 여부를 확인할 수 있는 결과가 반환 됩니다.
- 변환 함수는 런타임 반올림 모드를 구분 하지 않습니다.
- 변환 함수는 로캘이 인식 되지 않습니다. `'.'`쉼표를 사용 하는 로캘에서는 항상 ', '로 소수를 인쇄 하 고 구문 분석 합니다.

## `to_chars`

정수 또는 부동 소수점 값을의 시퀀스로 변환 **`char`** 합니다.

는, `value` ) 범위를 입력 하 여 문자열로 변환 합니다 \[ `first` `last` . 여기서은 \[ `first` `last` 올바른 범위 여야 합니다.
[To_chars_result 구조체](to-chars-result-structure.md)를 반환 합니다. 에 표시 된 대로 변환이 성공적으로 수행 되 면 `to_char_result.ec` 멤버는 `ptr` 작성 된 문자에 대 한 한 번의 끝 포인터입니다. 그렇지 않은 경우에는 값이이 고 `to_char_result.ec` `errc::value_too_large` 값이 `to_char_result.ptr` 이 `last` 고 범위의 내용이 \[ `first` 로 `last` 지정 되지 않습니다.

`to_chars`불충분 large buffer를 제공 하 여 결과를 저장 하는 경우에만 실패할 수 있습니다.

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>매개 변수

*기본*\
채울 버퍼의 시작 부분을 가리킵니다.

*최신*\
채울 버퍼의 끝을 지 나 한 문자를 가리킵니다.

*기본값*\
변환할 값입니다. `value`가 음수 이면 표현은로 시작 `-` 합니다.

*하단*\
정수 변환의 경우 chars로 변환할 때 사용할 기본입니다 `value` . 2-36 (포함) 사이 여야 합니다. 앞에 0이 없습니다. 10.. 35 (포함) 범위의 숫자는 소문자 a .로 표시 됩니다. -

*bcp.fmt*\
부동 소수점 변환의 경우 과학적, fixed 또는 16 진수와 같이 사용할 변환 형식을 지정 하는 비트 마스크입니다. 자세한 내용은 [chars_format](chars-format-class.md) 를 참조 하세요.

*소수*\
부동 소수점 변환의 경우 변환 된 값의 전체 자릿수입니다.

### <a name="return-value"></a>반환 값

변환 결과를 포함 하는 [to_chars_result](to-chars-result-structure.md) 입니다.

### <a name="remarks"></a>설명

[Chars_format](chars-format-class.md) 매개 변수를 사용 하는 함수는 변환 지정자를 다음과 같이를 사용 하는 것 처럼 결정 합니다. 변환 지정자는가 이면이 고,가 이면이 고,가 이면입니다 `printf()` `'f'` `fmt` `chars_format::fixed` `'e'` `fmt` `chars_format::scientific` `'a'` `0x` `fmt` `chars_format::hex` `'g'` `fmt` `chars_format::general` . 가장 짧은 고정 표기법을 지정 하는 경우 값이 매우 크거나 매우 작은 경우 가능한 가장 짧은 표현이 될 수 있으므로 출력 시간이 길어질 수 있습니다.

다음 표에서는 `fmt` 및 매개 변수의 다양 한 조합에 지정 된 변환 동작에 대해 설명 합니다 `precision` . "최단 왕복 동작" 이란 용어는 해당 함수를 사용 하 여 표시를 구문 분석 하 여 값을 정확 하 게 복구 하는 데 필요한 최소 자릿수를 기록 하는 것을 의미 합니다 `from_chars` .

| `fmt` 및 `precision` 조합 | 출력 |
|--|--|
|  Neither | 고정 또는 과학적 표기법 중에서 더 짧은 것은 tiebreaker으로 고정을 선호 합니다.</br>이 동작은 매개 변수를 사용 하는 오버 로드에 의해 시뮬레이션 될 수 없습니다 `fmt` . |
| `fmt` | 가장 짧은 과학적 형식 등 지정 된 형식에 대 한 최단 왕복 동작입니다. |
| `fmt` 및 `precision` | `printf()`가장 짧은 왕복 동작 없이 스타일을 사용 하 여 지정 된 전체 자릿수를 사용 합니다. |

### <a name="example"></a>예제

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.

    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

의 시퀀스를 **`char`** 정수 또는 부동 소수점 값으로 변환 합니다.

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>매개 변수

*기본*\
변환할 문자 버퍼의 시작 부분을 가리킵니다.

*최신*\
변환할 문자 버퍼의 끝 요소 하나 다음을 가리킵니다.

*기본값*\
성공적으로 변환 되 면 변환 결과를 포함 합니다.

*하단*\
정수 변환의 경우 변환 하는 동안 사용할 기본입니다. 2-36 (포함) 사이 여야 합니다.

*bcp.fmt*\
부동 소수점 변환의 경우 변환 되는 문자 시퀀스의 형식입니다. 자세한 내용은 [chars_format](chars-format-class.md) 를 참조 하세요.

### <a name="remarks"></a>설명

`from_chars()`함수는 문자열를 분석 하 여 \[ `first` `last` 숫자 패턴 (여기서 \[ `first` , `last` )은 유효한 범위 여야 합니다.

문자를 구문 분석할 때 공백은 무시 되지 않습니다. 예를 들어와 달리 `strtod()` 버퍼는 유효한 숫자 표현으로 시작 해야 합니다.

[From_chars_result 구조체](from-chars-result-structure.md)를 반환 합니다.

숫자 패턴에 일치 하는 문자가 없는 경우 `value` 는 수정 되지 않으며는를 `from_chars_result.ptr` 가리키며 `first` `from_chars_result.ec` 은 `errc::invalid_argument` 입니다.

일부 문자만 숫자 패턴과 일치 하는 경우는 `from_chars_result.ptr` 패턴이 일치 하지 않는 첫 번째 문자를 가리키거나 `last` 모든 문자가 일치 하는 경우 매개 변수의 값을 갖습니다.

구문 분석 된 값이의 형식으로 표현할 수 있는 범위에 없는 경우는 `value` `value` 수정 되지 않고 `from_chars_result.ec` 가 됩니다 `errc::result_out_of_range` .

그렇지 않으면 `value` 는 반올림 후 구문 분석 된 값으로 설정 되 고 `from_chars_result.ec` 는와 같습니다 `errc{}` .

### <a name="example"></a>예제

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="requirements"></a>요구 사항

**헤더:**\<charconv>

**네임스페이스:** std

/std: c + + 17 이상이 필요 합니다.

## <a name="see-also"></a>참고 항목

[\<charconv>](charconv.md)  
[라운드트립 하는 가장 짧은 10 진수 문자열입니다](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/) 
 . [printf () 서식 지정자](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
