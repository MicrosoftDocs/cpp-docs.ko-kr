---
description: '자세한 정보: 기본 제공 형식 (c + +)'
title: 기본 제공 형식 (c + +)
ms.date: 07/22/2020
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: 601bd0742002506272ec3da7af448a4bdba96065
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268745"
---
# <a name="built-in-types-c"></a>기본 제공 형식 (c + +)

기본 제공 형식 ( *기본 형식* 이 라고도 함)은 c + + 언어 표준에 의해 지정 되며 컴파일러에 기본 제공 됩니다. 기본 제공 형식은 헤더 파일에 정의 되어 있지 않습니다. 기본 제공 형식은 *정수 계열*, *부동* 소수점 및 *void* 의 세 가지 주요 범주로 구분 됩니다. 정수 계열 형식은 정수를 나타냅니다. 부동 소수점 형식은 소수 부분이 있을 수 있는 값을 지정할 수 있습니다. 대부분의 기본 제공 형식은 컴파일러에서 고유한 형식으로 처리 됩니다. 그러나 일부 형식은 *동의어* 이거나 컴파일러에서 동등한 형식으로 처리 됩니다.

## <a name="void-type"></a>void 형식

[`void`](void-cpp.md)형식은 빈 값 집합을 설명 합니다. 형식의 변수를 **`void`** 지정할 수 없습니다. **`void`** 형식은 값을 반환 하지 않는 함수를 선언 하거나 형식화 되지 않았거나 임의로 형식화 된 데이터에 대 한 제네릭 포인터를 선언 하는 데 주로 사용 됩니다. 모든 식은 형식으로 명시적으로 변환 되거나 캐스팅 될 수 있습니다 **`void`** . 그러나 이러한 식은 사용이 다음으로 제한됩니다.

- 식 문. (자세한 내용은 [식](expressions-cpp.md)을 참조 하세요.)

- 쉼표 연산자의 왼쪽 피연산자. (자세한 내용은 [쉼표 연산자](comma-operator.md)를 참조 하세요.)

- 조건 연산자의 두 번째 또는 세 번째 피연산자(`? :`)입니다. (자세한 내용은 [조건 연산자를 사용 하는 식](conditional-operator-q.md)을 참조 하세요.)

## <a name="stdnullptr_t"></a>std:: nullptr_t

키워드는 **`nullptr`** `std::nullptr_t` 원시 포인터 형식으로 변환할 수 있는 형식의 null 포인터 상수입니다. 자세한 내용은 [`nullptr`](nullptr.md)를 참조하세요.

## <a name="boolean-type"></a>부울 형식

형식에는 [`bool`](bool-cpp.md) 및 값이 있을 수 있습니다 [`true`](../cpp/true-cpp.md) [`false`](../cpp/false-cpp.md) . 형식의 크기는 **`bool`** 구현 별로 다릅니다. Microsoft 특정 구현 세부 정보에 대 한 [기본 제공 형식의 크기](#sizes-of-built-in-types) 를 참조 하세요.

## <a name="character-types"></a>문자 형식

**`char`** 형식은 기본 실행 문자 집합의 멤버를 효율적으로 인코딩하는 문자 표시 형식입니다. C + + 컴파일러는 **`char`** , 및 형식의 변수를 **`signed char`** **`unsigned char`** 서로 다른 형식으로 처리 합니다.

**Microsoft** 전용: **`char`** 컴파일 옵션을 사용 하지 않는 경우 형식의 변수는 **`int`** 기본적으로 형식에서와 같이로 승격 됩니다 **`signed char`** [`/J`](../build/reference/j-default-char-type-is-unsigned.md) . 이 경우 형식으로 처리 **`unsigned char`** 되 고 부호 확장 없이로 승격 됩니다 **`int`** .

형식의 변수는 **`wchar_t`** 와이드 문자 또는 멀티 바이트 문자 형식입니다. **`L`** 문자 또는 문자열 리터럴 앞에 접두사를 사용 하 여 와이드 문자 형식을 지정 합니다.

**Microsoft** 전용: 기본적으로 **`wchar_t`** 는 네이티브 형식 이지만를 사용 [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 하 여 **`wchar_t`** 에 대 한 typedef를 만들 수 있습니다 **`unsigned short`** . **`__wchar_t`** 형식은 네이티브 형식의 Microsoft 전용 동의어입니다 **`wchar_t`** .

**`char8_t`** 형식은 utf-8 문자 표현에 사용 됩니다. 와 동일한 표현을 **`unsigned char`** 갖지만 컴파일러에서 고유한 형식으로 처리 됩니다. **`char8_t`** C + + 20의 새 형식입니다. **Microsoft 전용**:을 사용 **`char8_t`**  하려면 컴파일러 옵션을 사용 해야 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 합니다.

**`char16_t`** 형식은 utf-16 문자 표현에 사용 됩니다. UTF-16 코드 단위를 나타낼 수 있을 만큼 커야 합니다. 컴파일러에서 고유한 형식으로 처리 됩니다.

**`char32_t`** 형식은 UTF-32 문자 표현에 사용 됩니다. 32 코드 단위를 나타낼 만큼 커야 합니다. 컴파일러에서 고유한 형식으로 처리 됩니다.

## <a name="floating-point-types"></a>부동 소수점 형식

부동 소수점 형식은 IEEE-754 표현을 사용 하 여 광범위 한 크고 많을에서 소수 값의 근사값을 제공 합니다. 다음 표에서는 c + +의 부동 소수점 형식 및 부동 소수점 형식 크기에 대 한 비교 제한 사항을 보여 줍니다. 이러한 제한은 c + + 표준에 따라 적용 되며 Microsoft 구현과는 독립적입니다. 기본 제공 부동 소수점 형식의 절대 크기가 표준에 지정 되어 있지 않습니다.

| 형식 | 콘텐츠 |
|--|--|
| **`float`** | 형식은 **`float`** c + +에서 가장 작은 부동 소수점 형식입니다. |
| **`double`** | 형식은 **`double`** 형식 보다 크거나 같은 부동 소수점 형식 **`float`** 이지만, 형식의 크기 보다 짧거나 같습니다 **`long double`** . |
| **`long double`** | 형식은 **`long double`** 형식 보다 크거나 같은 부동 소수점 형식입니다 **`double`** . |

**Microsoft 전용**:과의 표현은 **`long double`** **`double`** 동일 합니다. 그러나 **`long double`** 및 **`double`** 는 컴파일러에서 고유한 형식으로 처리 됩니다. Microsoft c + + 컴파일러는 4 바이트와 8 바이트 IEEE-754 부동 소수점 표현을 사용 합니다. 자세한 내용은 [IEEE 부동 소수점 표시](../build/ieee-floating-point-representation.md)를 참조 하세요.

## <a name="integer-types"></a>정수 형식

**`int`** 형식은 기본 기본 정수 형식입니다. 구현 별 범위에서 전체 숫자를 나타낼 수 있습니다.

*부호* 있는 정수 표현은 양수 및 음수 값을 모두 보유할 수 있는 정수입니다. 기본적으로 사용 되거나 **`signed`** modifier 키워드가 있는 경우 사용 됩니다. **`unsigned`** Modifier 키워드는 음수가 아닌 값만 포함할 수 있는 *부호 없는* 표현을 지정 합니다.

크기 한정자는 사용 되는 정수 표현의 너비 (비트)를 지정 합니다. 언어는 **`short`** , **`long`** 및 한정자를 지원 **`long long`** 합니다. **`short`** 형식은 16 비트 이상 이어야 합니다. **`long`** 형식은 32 비트 이상 이어야 합니다. **`long long`** 형식은 64 비트 이상 이어야 합니다. 표준은 정수 계열 형식 간의 크기 관계를 지정 합니다.

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

구현은 각 형식에 대 한 최소 크기 요구 사항과 크기 관계를 모두 유지 해야 합니다. 그러나 실제 크기는 구현에 따라 달라질 수 있습니다. Microsoft 특정 구현 세부 정보에 대 한 [기본 제공 형식의 크기](#sizes-of-built-in-types) 를 참조 하세요.

**`int`** **`signed`** , **`unsigned`** 또는 크기 한정자가 지정 된 경우 키워드를 생략할 수 있습니다. 한정자와 **`int`** 형식 (있는 경우)은 순서에 관계 없이 나타날 수 있습니다. 예를 들어 **`short unsigned`** 및는 **`unsigned int short`** 같은 형식을 참조 합니다.

### <a name="integer-type-synonyms"></a>정수 형식 동의어

다음 형식 그룹은 컴파일러에서 동의어로 간주 됩니다.

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

**Microsoft 전용** 정수 형식에는 특정 너비 **`__int8`** , **`__int16`** , **`__int32`** 및 **`__int64`** 형식이 포함 됩니다. 이러한 형식은 및 한정자를 사용할 수 있습니다 **`signed`** **`unsigned`** . **`__int8`** 데이터 형식은 **`char`** 형식과 동의어이고, **`__int16`** 은 **`short`** , **`__int32`** 는 **`int`** , **`__int64`** 는 **`long long`** 와 동의어입니다.

## <a name="sizes-of-built-in-types"></a>기본 제공 형식의 크기

대부분의 기본 제공 형식에는 구현에서 정의 된 크기가 있습니다. 다음 표에서는 Microsoft c + +의 기본 제공 형식에 필요한 저장소 크기를 나열 합니다. 특히 **`long`** 는 64 비트 운영 체제 에서도 4 바이트입니다.

| 형식 | 크기 |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1바이트 |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2바이트 |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4바이트 |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8바이트 |

각 형식의 값 범위에 대 한 요약은 [데이터 형식 범위](data-type-ranges.md) 를 참조 하세요.

형식 변환에 대 한 자세한 내용은 [표준 변환](standard-conversions.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[데이터 형식 범위](data-type-ranges.md)
