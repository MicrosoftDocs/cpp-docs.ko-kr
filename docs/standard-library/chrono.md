---
title: '&lt;chrono&gt; | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
dev_langs:
- C++
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d701b290100f812f3c7845096960561cb101472
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

표준 헤더 \<chrono>를 포함하여 기간 및 시간 인스턴트를 나타내고 조작하는 클래스와 함수를 정의합니다.

Visual Studio 2015에서 구현부터 `steady_clock` 지 속성 및 단 조성에 대 한 c + + 표준 요구 사항을 충족 하도록 변경 되었습니다. 현재 `steady_clock`은 QueryPerformanceCounter()를 기반으로 하며 `high_resolution_clock`은 `steady_clock`에 대한 typedef입니다. 따라서 Visual C++에서 `steady_clock::time_point`는 현재 `chrono::time_point<steady_clock>`에 대한 typedef이나, 다른 구현에 이를 반드시 적용할 필요는 없습니다.

## <a name="syntax"></a>구문

```cpp
#include <chrono>
```

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[duration 클래스](../standard-library/duration-class.md)|시간 간격을 포함하는 유형을 설명합니다.|
|[time_point 클래스](../standard-library/time-point-class.md)|시점을 나타내는 형식을 설명합니다.|

### <a name="structs"></a>Structs

|이름|설명|
|----------|-----------------|
|[common_type 구조체](../standard-library/common-type-structure.md)|`duration` 및 `time_point`의 인스턴스화에 대한 템플릿 클래스 [common_type](../standard-library/common-type-class.md)의 특수화를 설명합니다.|
|[duration_values 구조체](../standard-library/duration-values-structure.md)|`duration` 템플릿 매개 변수 `Rep`에 대한 특정 값을 제공합니다.|
|[steady_clock 구조체](../standard-library/steady-clock-struct.md)|`steady` 클록을 나타냅니다.|
|[system_clock 구조체](../standard-library/system-clock-structure.md)|시스템의 실시간 시계를 기반으로 하는 *시계 형식*을 나타냅니다.|
|[treat_as_floating_point 구조체](../standard-library/treat-as-floating-point-structure.md)|형식이 부동 소수점 형식으로 처리될 수 있는지 여부를 지정합니다.|

### <a name="functions"></a>함수

|이름|설명|
|----------|-----------------|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|지정된 형식으로 `duration` 개체를 캐스팅합니다.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|지정된 형식으로 `time_point` 개체를 캐스팅합니다.|

### <a name="operators"></a>연산자

|이름|설명|
|----------|-----------------|
|[operator-](../standard-library/chrono-operators.md#operator-)|`duration` 및 `time_point` 개체의 빼기 또는 부정에 대한 연산자입니다.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|`duration` 또는 `time_point` 개체와 함께 사용하는 같지 않음 연산자입니다.|
|[modulo 연산자](../standard-library/chrono-operators.md#op_modulo)|`duration` 개체에 대한 모듈로 연산용 연산자입니다.|
|[operator*](../standard-library/chrono-operators.md#op_star)|`duration` 개체에 대한 곱하기 연산자입니다.|
|[operator/](../standard-library/chrono-operators.md#op_div)|`duration` 개체에 대한 나누기 연산자입니다.|
|[operator+](../standard-library/chrono-operators.md#op_add)|`duration` 및 `time_point` 개체를 추가합니다.|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|하나의 `duration` 또는 `time_point`개체가 다른 `duration` 또는 `time_point` 개체보다 작은지 여부를 확인합니다.|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|하나의 `duration` 또는 `time_point`개체가 다른 `duration` 또는 `time_point` 개체보다 작거나 같은지 여부를 확인합니다.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|두 `duration` 개체가 길이가 동일한 시간 간격을 나타내는지 여부 또는 두 `time_point` 개체가 동일한 시점을 나타내는지 여부를 확인합니다.|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|하나의 `duration` 또는 `time_point`개체가 다른 `duration` 또는 `time_point` 개체보다 큰지 여부를 확인합니다.|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|하나의 `duration` 또는 `time_point`개체가 다른 `duration` 또는 `time_point` 개체보다 크거나 같은지 여부를 확인합니다.|

### <a name="predefined-duration-types"></a>미리 정의된 기간 형식

다음 typedef에 사용되는 비율 형식에 대한 자세한 내용은 [\<ratio>](../standard-library/ratio.md)를 참조하세요.

|Typedef|설명|
|-------------|-----------------|
|`typedef duration<long long, nano> nanoseconds;`|틱 기간이 1나노초인 `duration` 형식의 동의어입니다.|
|`typedef duration<long long, micro> microseconds;`|틱 기간이 1마이크로초인 `duration` 형식의 동의어입니다.|
|`typedef duration<long long, milli> milliseconds;`|틱 기간이 1밀리초인 `duration` 형식의 동의어입니다.|
|`typedef duration<long long> seconds;`|틱 기간이 1초인 `duration` 형식의 동의어입니다.|
|`typedef duration<int, ratio<60> > minutes;`|틱 기간이 1분인 `duration` 형식의 동의어입니다.|
|`typedef duration<int, ratio<3600> > hours;`|틱 기간이 1시간인 `duration` 형식의 동의어입니다.|

### <a name="literals"></a>리터럴

**(C++11)** \<chrono> 헤더는 코드의 형식 안전성과 유지 관리 및 편의성을 위해 사용할 수 있는 다음과 같은 [사용자 정의 리터럴](../cpp/user-defined-literals-cpp.md)을 정의합니다. 이러한 리터럴은 `literals::chrono_literals` 인라인 네임스페이스에 정의되며 std::chrono가 범위 내에 있을 때 범위 안에 있습니다.

|Literal|설명|
|-------------|-----------------|
|chrono::hours 연산자 "" h(부호 없는 long long Val)|정수 계열 값으로 시간을 지정합니다.|
|chrono::\<double 비율\<3600 >> 연산자 "" h (long double Val)|부동 소수점 값으로 시간을 지정합니다.|
|chrono::minutes (연산자 "" min)(부호 없는 long long Val)|정수 계열 값으로 분을 지정합니다.|
|chrono::\<double 비율\<60 >> (연산자 "" min) (long double Val)|부동 소수점 값으로 분을 지정합니다.|
|chrono::seconds 연산자 "" s(부호 없는 long long Val)|정수 계열 값으로 분을 지정합니다.|
|chrono::duration\<double> 연산자 "" s(long double Val)|부동 소수점 값으로 초를 지정합니다.|
|chrono::milliseconds 연산자 "" ms(부호 없는 long long Val)|정수 계열 값으로 밀리초를 지정합니다.|
|chrono::duration\<double, milli> 연산자 "" ms(long double Val)|부동 소수점 값으로 밀리초를 지정합니다.|
|chrono::microseconds 연산자 "" us(부호 없는 long long Val)|정수 계열 값으로 마이크로초를 지정합니다.|
|chrono::duration\<double, micro> 연산자 "" us(long double Val)|부동 소수점 값으로 마이크로초를 지정합니다.|
|chrono::nanoseconds 연산자 "" ns(부호 없는 long long Val)|정수 계열 값으로 나노초를 지정합니다.|
|chrono::duration\<double, nano> 연산자 "" ns(long double Val)|부동 소수점 값으로 나노초를 지정합니다.|
|||

다음 예에서는 chrono 리터럴을 사용하는 방법을 보여 줍니다.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
