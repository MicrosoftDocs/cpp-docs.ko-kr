---
title: RawEvent 클래스
description: C++ Build Insights SDK RawEvent 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1cf96e1b8eadaf1de9fe2cf565a993f3bcafe358
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920465"
---
# <a name="rawevent-class"></a>RawEvent 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`RawEvent` 클래스는 [EventStack](event-stack.md)에 있는 일반 이벤트를 나타내는 용도로 사용합니다.

## <a name="syntax"></a>구문

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>설명

`RawEvent` 클래스의 여러 멤버 함수는 틱 수를 반환합니다. C++ Build Insights는 Windows의 성능 카운터를 틱의 소스로 사용합니다. 틱 수를 시간 단위(예: 초)로 변환하려면 틱 빈도와 함께 사용해야 합니다. 빈 빈도를 가져오려면 `TickFrequency` 멤버 함수를 호출해야 할 수 있습니다. [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) 페이지에 틱을 시간 단위로 변환하는 예제가 나와 있습니다.

틱을 직접 변환하지 않고 싶다면 `RawEvent` 클래스에서 제공하는 시간 값을 나노초 단위로 반환하는 멤버 함수를 사용하세요. 표준 C++ `chrono` 라이브러리를 사용하여 나노초를 다른 시간 단위로 변환해야 합니다.

## <a name="members"></a>멤버

### <a name="constructor"></a>생성자

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[데이터](#data)\
[Duration](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a> RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>매개 변수

*event*\
이벤트 데이터입니다.

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

## <a name="data"></a><a name="data"></a> Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>반환 값

이 이벤트에 포함된 추가 데이터에 대한 포인터입니다. 이 필드를 해석하는 자세한 방법은 [EVENT_DATA](../c-event-data-types/event-data-struct.md)를 참조하세요.

## <a name="duration"></a><a name="duration"></a> Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>반환 값

작업 기간(나노초)입니다.

## <a name="eventid"></a><a name="event-id"></a> EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>반환 값

이벤트 형식을 식별하는 번호입니다. 이벤트 식별자 목록은 [EVENT_ID](../c-event-data-types/event-id-enum.md)를 참조하세요.

## <a name="eventinstanceid"></a><a name="event-instance-id"></a> EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>반환 값

추적 내에서 이벤트를 식별하는 번호입니다. 동일한 추적을 여러 번 분석하거나 다시 로깅하는 경우 이 값이 변경되지 않습니다. 이 값을 사용하면 동일한 추적을 통해 여러 분석 또는 다시 로깅 패스에서 동일한 이벤트를 식별할 수 있습니다.

## <a name="eventname"></a><a name="event-name"></a> EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>반환 값

[EventId](#event-id)로 식별하는 이벤트 형식의 이름을 포함하는 ANSI 문자열입니다.

## <a name="eventwidename"></a><a name="event-wide-name"></a> EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>반환 값

[EventId](#event-id)로 식별하는 이벤트 형식의 이름을 포함하는 와이드 문자열입니다.

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

## <a name="processid"></a><a name="process-id"></a> ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>반환 값

이벤트가 발생한 프로세스의 식별자입니다.

## <a name="processorindex"></a><a name="processor-index"></a> ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>반환 값

이벤트가 발생한 논리 프로세서의 인덱스(0부터 시작)입니다.

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

## <a name="threadid"></a><a name="thread-id"></a> ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>반환 값

이벤트가 발생한 스레드의 식별자입니다.

## <a name="tickfrequency"></a><a name="tick-frequency"></a> TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>반환 값

이 이벤트에서 틱 단위로 기간을 평가할 때 사용할 초당 틱 수입니다.

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

전체 벽시계 시간에 대한 이 작업의 기여를 나타내는 틱 수입니다. 벽시계 시간 책임 틱은 일반 틱과 다릅니다. 벽시계 시간 책임 틱은 작업 간의 병렬 처리를 고려합니다. 두 병렬 작업의 기간이 50 틱이고 시작 및 중지 시간이 동일할 수 있습니다. 이 경우 두 작업 모두 벽시계 시간 책임이 25틱으로 할당됩니다.

::: moniker-end
