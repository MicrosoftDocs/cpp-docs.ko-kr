---
title: 숫자, 부울 및 포인터 리터럴 (c + +)
description: 정수, 부동 소수점, 부울 및 포인터 리터럴의 c + + 표준 언어 형식입니다.
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: f817fcca35a741dac29047e214897758cdc93edb
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236714"
---
# <a name="numeric-boolean-and-pointer-literals"></a>숫자, 부울 및 포인터 리터럴

리터럴은 값을 직접 나타내는 프로그램 요소입니다. 이 문서에서는 정수, 부동 소수점, 부울 및 포인터 형식의 리터럴을 설명 합니다. 문자열 및 문자 리터럴에 대 한 자세한 내용은 [문자열 및 문자 리터럴 (c + +)](../cpp/string-and-character-literals-cpp.md)을 참조 하세요. 이러한 범주에 따라 사용자 고유의 리터럴을 정의할 수도 있습니다. 자세한 내용은 [사용자 정의 리터럴 (c + +)](../cpp/user-defined-literals-cpp.md)을 참조 하세요.

리터럴은 많은 컨텍스트에서 사용할 수 있지만 가장 일반적으로 명명된 변수를 초기화하고 인수를 함수에 전달하는 데 사용됩니다.

```cpp
const int answer = 42;      // integer literal
double d = sin(108.87);     // floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

경우에 따라 리터럴을 해석하는 방법 또는 지정할 특정 형식을 컴파일러에 알려야 합니다. 리터럴에 접두사 또는 접미사를 추가 하 여 수행 합니다. 예를 들어 접두사는 `0x` 그 뒤의 숫자를 16 진수 값으로 해석 하도록 컴파일러에 지시 합니다 (예:) `0x35` . `ULL`접미사는에서와 같이 값을 형식으로 처리 하도록 컴파일러에 지시 합니다 **`unsigned long long`** `5894345ULL` . 각 리터럴 형식에 대한 접두사 및 접미사의 전체 목록을 다음 섹션을 참조하세요.

## <a name="integer-literals"></a>정수 리터럴

정수 리터럴은 숫자로 시작하고 소수 부분이나 지수가 없습니다. 정수 리터럴은 10 진수, 이진, 8 진수 또는 16 진수 형식으로 지정할 수 있습니다. 필요에 따라 접미사를 사용 하 여 부호 없는 정수 리터럴을 long 또는 long long 형식으로 지정할 수 있습니다.

접두사 또는 접미사가 없으면 컴파일러가 정수 리터럴 값 형식 **`int`** (32 비트)을 지정 합니다. 값이 적합 하면이 고, 그렇지 않으면 형식 **`long long`** (64 비트)을 지정 합니다.

10진수 정수 계열 리터럴을 지정하려면 0이 아닌 숫자를 사용하여 지정을 시작합니다. 예를 들면 다음과 같습니다.

```cpp
int i = 157;        // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
```

8진수 정수 계열 리터럴을 지정하려면 0으로 시작하여 0부터 7까지의 숫자 시퀀스를 지정합니다. 8진수 리터럴을 지정할 때 숫자 8과 9는 오류입니다. 예를 들면 다음과 같습니다.

```cpp
int i = 0377;   // Octal literal
int j = 0397;   // Error: 9 is not an octal digit
```

16 진수 정수 리터럴을 지정 하려면 `0x` 또는 `0X` ("x"의 대/소문자 구분 안)를 사용 하 여 사양을 시작한 다음 범위에 있는 숫자의 시퀀스를 `0` 부터 `9` 및 `a` (또는 `A` )부터 `f` (또는)까지 시작 `F` 합니다. 16진수 숫자 `a`(또는 `A`)부터 `f`(또는 `F`)는 10부터 15 사이의 값을 나타냅니다. 예를 들면 다음과 같습니다.

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;   // Equal to i
```

부호 없는 형식을 지정 하려면 또는 접미사를 사용 `u` `U` 합니다. Long 형식을 지정 하려면 `l` 또는 접미사를 사용 `L` 합니다. 64비트 정수 계열 형식을 지정하려면 LL 또는 ll 접미사를 사용합니다. I64 접미사는 계속 지원 되지만 권장 하지 않습니다. Microsoft와 관련 되어 있으며, 이식할 수 없습니다. 예를 들면 다음과 같습니다.

```cpp
unsigned val_1 = 328u;                  // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**숫자 구분 기호**: 작은따옴표 (아포스트로피)를 사용 하 여 더 많은 수의 값을 구분 하 여 다른 사용자가 쉽게 읽을 수 있습니다. 구분 기호는 컴파일에 영향을 주지 않습니다.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>부동 소수점 리터럴

부동 소수점 리터럴은 소수 부분이 있어야 하는 값을 지정합니다. 이러한 값에는 소수점 ( **`.`** )이 포함 되며 지수가 포함 될 수 있습니다.

부동 소수점 리터럴에는 숫자 값  을 지정 하는 significand *(가 수 라고도 함)가* 있습니다. 숫자의 크기를 지정 하는 *지* 수를 포함 합니다. 또한 리터럴의 형식을 지정 하는 선택적 접미사가 있습니다. Significand는 숫자 시퀀스, 마침표, 숫자의 소수 부분을 나타내는 선택적 숫자 시퀀스를 차례로 지정 합니다. 예를 들면 다음과 같습니다.

```cpp
18.46
38.
```

지수는(있는 경우) 다음 예제와 같이 숫자의 크기를 10의 거듭제곱으로 지정합니다.

```cpp
18.46e0      // 18.46
18.46e1      // 184.6
```

지 수는 `e` `E` 동일한 의미를 가지 며 선택적 기호 (+ 또는-)와 숫자 시퀀스를 사용 하 여 지정할 수 있습니다.  지수가 있는 경우 `18E0`과 같은 정수에는 뒤에 오는 소수점이 필요하지 않습니다.

부동 소수점 리터럴은 기본값을 형식으로 지정 **`double`** 합니다. 접미사 또는 또는 또는 `f` `l` `F` `L` (접미사는 대/소문자를 구분 하지 않음)를 사용 하 여 리터럴을 또는로 지정할 수 있습니다 **`float`** **`long double`** .

**`long double`** 및는 **`double`** 동일한 표현을 갖지만 동일한 형식이 아닙니다. 예를 들어,와 같은 오버 로드 된 함수를 사용할 수 있습니다.

```cpp
void func( double );
```

and

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>부울 리터럴

부울 리터럴은 **`true`** 및 **`false`** 입니다.

## <a name="pointer-literal-c11"></a>포인터 리터럴(C++11)

C + +는 [`nullptr`](../cpp/nullptr.md) 0으로 초기화 된 포인터를 지정 하는 리터럴을 소개 합니다. 이식 가능한 코드에서 **`nullptr`** 는와 같이 정수 계열 형식 0 또는 매크로 대신 사용 해야 합니다 `NULL` .

## <a name="binary-literals-c14"></a>이진 리터럴(C++14)

이진 리터럴은 `0B` 또는 `0b` 접두사와 뒤에 오는 1과 0의 시퀀스를 사용하여 지정할 수 있습니다.

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>리터럴을 "매직 상수”로 사용하지 마세요.

리터럴은 식과 문에서 직접 사용할 수 있지만 항상 바람직한 프로그래밍 방법은 아닙니다.

```cpp
if (num < 100)
    return "Success";
```

이전 예제에서는 명확한 의미를 전달 하는 명명 된 상수 (예: "MAXIMUM_ERROR_THRESHOLD")를 사용 하는 것이 더 좋습니다. 또한 최종 사용자에 게 반환 값 "Success"가 표시 되는 경우 명명 된 문자열 상수를 사용 하는 것이 더 좋을 수 있습니다. 다른 언어로 지역화할 수 있는 파일의 단일 위치에 문자열 상수를 유지할 수 있습니다. 명명 된 상수를 사용 하면 자신과 다른 사용자가 코드의 의도를 이해할 수 있습니다.

## <a name="see-also"></a>참고 항목

[어휘 규칙](../cpp/lexical-conventions.md)<br/>
[C + + 문자열 리터럴](../cpp/string-and-character-literals-cpp.md)<br/>
[C + + 사용자 정의 리터럴](../cpp/user-defined-literals-cpp.md)
