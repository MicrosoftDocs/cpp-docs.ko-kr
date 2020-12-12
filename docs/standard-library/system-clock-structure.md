---
description: '다음에 대 한 자세한 정보: system_clock 구조체'
title: system_clock 구조체
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 54d15f5e5ccc75e056cbdcc1d56d05e0a343c76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183206"
---
# <a name="system_clock-structure"></a>system_clock 구조체

시스템의 실시간 시계를 기반으로 하는 *시계 형식* 을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
struct system_clock;
```

## <a name="remarks"></a>설명

*시간 형식* 은 현재 시간을 UTC로 가져오는 데 사용됩니다. 이 형식은 [duration](../standard-library/duration-class.md) 및 클래스 템플릿 [time_point](../standard-library/time-point-class.md)의 인스턴스화를 구현하고 시간을 반환하는 정적 구성원 함수 `now()`를 정의합니다.

`now()`에 대한 첫 번째 호출에서 반환되는 값이 항상 `now()`에 대한 순차적 호출에서 반환되는 값보다 작거나 같을 경우 클록은 *단조* 입니다.

클록이 *단조* 이고 클록 틱 간 시간이 지속적이면 해당 클록은 *지속* 입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`system_clock::duration`|`duration<rep, period>`의 동의어입니다.|
|`system_clock::period`|`duration`의 포함된 인스턴스화에서 틱 기간을 나타내는 데 사용되는 형식의 동의어입니다.|
|`system_clock::rep`|`duration`의 포함된 인스턴스화에서 클록 틱 수를 나타내는 데 사용되는 형식의 동의어입니다.|
|`system_clock::time_point`|`time_point<Clock, duration>`의 동의어입니다. 여기서, `Clock`은 클록 형식 자체의 동의어이거나 같은 Epoch에 기반을 두고 같은 중첩된 `duration` 형식을 포함하는 또 다른 클록 형식의 동의어입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[from_time_t](#from_time_t)|정적. 지정된 시간과 가장 가까운 근사치로 계산된 `time_point`를 반환합니다.|
|[지금은](#now)|정적. 현재 시간을 반환합니다.|
|[to_time_t](#to_time_t)|정적. 지정된 `time_point`와 가장 가까운 근사치로 계산된 `time_t` 개체를 반환합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[system_clock::is_monotonic 상수](#is_monotonic_constant)|클록 형식이 단조인지를 지정합니다.|
|[system_clock::is_steady 상수](#is_steady_constant)|클록 형식이 지속인지를 지정합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<chrono>

**네임스페이스:** std::chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a> system_clock:: from_time_t

*Tm* 에 표시 되는 시간과 가장 근접 한 [time_point](../standard-library/time-point-class.md) 를 반환 하는 정적 메서드입니다.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>매개 변수

*Tm*\
[time_t](../c-runtime-library/standard-types.md) 개체

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a> system_clock:: is_monotonic 상수

시간 형식이 단조인지를 지정하는 정적 값입니다.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>반환 값

이 구현에서는 `system_clock::is_monotonic` 항상를 반환 **`false`** 합니다.

### <a name="remarks"></a>설명

`now()`에 대한 첫 번째 호출에서 반환되는 값이 항상 `now()`에 대한 순차적 호출에서 반환되는 값보다 작거나 같을 경우 클록은 *단조* 입니다.

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a> system_clock:: is_steady 상수

시간 형식이 *지속* 인지를 지정하는 정적 값입니다.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>반환 값

이 구현에서는 `system_clock::is_steady` 항상를 반환 **`false`** 합니다.

### <a name="remarks"></a>설명

클록이 [단조](#is_monotonic_constant)이고 클록 틱 간 시간이 지속적이면 해당 클록은 *지속* 입니다.

## <a name="system_clocknow"></a><a name="now"></a> system_clock:: now

현재 시간을 반환하는 정적 메서드입니다.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>반환 값

현재 시간을 나타내는 [time_point](../standard-library/time-point-class.md) 개체입니다.

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a> system_clock:: to_time_t

*Time* 으로 표현 되는 시간과 가장 근접 한 [time_t](../c-runtime-library/standard-types.md) 를 반환 하는 정적 메서드입니다.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>매개 변수

*런타임*\
[time_point](../standard-library/time-point-class.md) 개체입니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock 구조체](../standard-library/steady-clock-struct.md)
