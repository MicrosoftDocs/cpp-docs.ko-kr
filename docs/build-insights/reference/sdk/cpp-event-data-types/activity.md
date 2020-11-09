---
title: 작업 클래스
description: C++ Build Insights SDK Activity 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce7e4083411f1654064ca4628d10a767c7be1b7f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923404"
---
# <a name="activity-class"></a>작업 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`Activity` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 모든 작업 이벤트를 일치시켜야 합니다. `Activity` 클래스로 일치시킬 수 있는 이벤트를 모두 확인하려면 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>설명

`Activity` 클래스의 여러 멤버 함수는 틱 수를 반환합니다. C++ Build Insights는 Windows의 성능 카운터를 틱의 소스로 사용합니다. 틱 수를 시간 단위(예: 초)로 변환하려면 틱 빈도와 함께 사용해야 합니다. [Event](event.md)기본 클래스에서 사용할 수 있는 `TickFrequency` 멤버 함수를 호출하면 틱 빈도를 얻을 수 있습니다. [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) 페이지에서 틱을 시간 단위로 변환하는 예를 확인할 수 있습니다.

틱을 시간 단위로 직접 변환하지 않고 싶다면 `Activity` 클래스에서 제공하는 시간 값을 나노초 단위로 반환하는 멤버 함수를 사용하세요. 표준 C++ `chrono` 라이브러리를 사용하여 다른 시간 단위로 변환해야 합니다.

## <a name="members"></a>멤버

해당하는 [Event](event.md) 기본 클래스에서 상속된 멤버와 함께 `Activity` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructor"></a>생성자

[활동](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Duration](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a> 작업

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
모든 작업 이벤트입니다.

## <a name="cputicks"></a><a name="cpu-ticks"></a> CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>반환 값

이 작업에서 발생한 CPU틱 수입니다. CPU 틱은 일반 틱과 다릅니다. CPU 틱은 작업에서 CPU가 코드를 실행하는 경우에만 계산됩니다. 작업과 연결된 스레드가 절전 모드이면 CPU 틱이 계산되지 않습니다.

## <a name="cputime"></a><a name="cpu-time"></a> CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>반환 값

이 작업에서 CPU가 코드를 실행한 시간입니다. 자식 작업이 별도의 스레드에서 실행된다면 이 값이 작업 기간보다 클 수 있습니다. 값은 나노초 단위로 반환됩니다.

## <a name="duration"></a><a name="duration"></a> Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>반환 값

작업 기간(나노초)입니다.

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a> ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>반환 값

[CPUTicks](#cpu-ticks)와 동일하지만 자식 작업에서 발생한 CPU 틱은 포함하지 않습니다.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a> ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>반환 값

[CPUTime](#cpu-time)과 동일하지만 자식 작업의 CPU 시간이 포함되지 않습니다.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a> ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>반환 값

작업 기간(나노초)으로, 자식 작업에서 소비한 시간은 포함하지 않습니다.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a> ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>반환 값

이 작업에서 발생한 틱 수로, 자식 작업에서 발생한 틱 수는 제외됩니다.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a> ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>반환 값

[WallClockTimeResponsibility](#wall-clock-time-responsibility)와 동일하지만 자식 작업의 벽시계 시간 책임은 제외됩니다.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a> ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>반환 값

[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)와 동일하지만 자식 작업의 벽시계 시간 책임 틱은 제외됩니다.

## <a name="starttimestamp"></a><a name="start-timestamp"></a> StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>반환 값

작업을 시작했을 때 캡처한 틱 값입니다.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a> StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>반환 값

작업이 중단되었을 때 캡처한 틱 값입니다.

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a> WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>반환 값

이 작업의 벽시계 시간 책임(나노초)입니다. 벽시계 시간 책임에 대한 자세한 내용은 [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)를 참조하세요.

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a> WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>반환 값

전체 벽시계 시간에 대한 이 작업의 기여를 나타내는 틱 수입니다. 벽시계 시간 책임 틱은 일반 틱과 다릅니다. 벽시계 시간 책임 틱은 작업 간의 병렬 처리를 고려합니다. 두 병렬 작업의 기간이 50틱이고 시작 및 중지 시간이 동일할 수 있습니다. 이 경우 두 작업 모두 벽시계 시간 책임이 25틱으로 할당됩니다.

::: moniker-end
