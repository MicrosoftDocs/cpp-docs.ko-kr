---
description: '다음에 대 한 자세한 정보: `chrono` 리터럴'
title: chrono 리터럴
f1_keywords:
- chrono/std::literals::chrono_literals
- std::literals::chrono_literals
- chrono_literals
ms.date: 01/15/2021
ms.openlocfilehash: 84540d111b33738c8bb1bcb4b43966e1c50682c0
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667546"
---
# <a name="chrono-literals"></a>`chrono` 리터럴일

(C + + 14) `<chrono>` 헤더는 시간, 분, 초, 밀리초, 마이크로초 및 나노초를 나타내는 12 [개의 사용자 정의 리터럴을](../cpp/user-defined-literals-cpp.md) 정의 합니다. 각 사용자 정의 리터럴에는 정수 계열 및 부동 소수점 오버로드가 있습니다. 리터럴은 `literals::chrono_literals` `std::chrono` 가 범위 내에 있을 때 자동으로 범위로 가져오는 인라인 네임 스페이스에 정의 됩니다.

## <a name="syntax"></a>구문

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>반환 값

인수를 사용 하는 리터럴은 **`long long`** 값 또는 해당 형식을 반환 합니다. 부동 소수점 인수를 사용 하는 리터럴은 a를 반환 [`duration`](../standard-library/duration-class.md) 합니다.

## <a name="example"></a>예제

다음 예에서는 리터럴을 사용 하는 방법을 보여 줍니다 `chrono` .

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```
