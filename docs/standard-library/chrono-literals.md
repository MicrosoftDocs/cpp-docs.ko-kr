---
description: '자세히 알아보기: chrono 리터럴'
title: chrono 리터럴
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: 497094d920a25635496fb0aa30295d378571418c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325157"
---
# <a name="chrono-literals"></a>chrono 리터럴

(C + + 14) \<chrono> 헤더는 12 [개의 사용자 정의 리터럴을](../cpp/user-defined-literals-cpp.md) 정의 하 여 시간, 분, 초, 밀리초, 마이크로초 및 나노초를 나타내는 리터럴을 쉽게 사용할 수 있도록 합니다. 각 사용자 정의 리터럴에는 정수 계열 및 부동 소수점 오버로드가 있습니다. 리터럴은 std::chrono가 범위에 있을 때 자동으로 범위로 가져오는 literals::chrono_literals 인라인 네임스페이스에서 정의됩니다.

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

## <a name="return-value"></a>Return Value

인수를 사용 하는 리터럴은 **`long long`** 값 또는 해당 형식을 반환 합니다. 부동 소수점 인수를 사용하는 리터럴은 [duration](../standard-library/duration-class.md)을 반환합니다.

## <a name="example"></a>예제

다음 예에서는 chrono 리터럴을 사용하는 방법을 보여 줍니다.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```
