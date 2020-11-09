---
title: 이벤트 클래스
description: C++ Build Insights SDK Event 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7dd96ffa3518c58e1b18312bb4fe2c36df26bd67
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923293"
---
# <a name="event-class"></a>이벤트 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`Event` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 모든 이벤트를 일치시켜야 합니다.

## <a name="syntax"></a>구문

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

[이벤트](#entity)

### <a name="functions"></a>Functions

[Data](#data)
[EventId](#event-id)\
[EventInstanceId](#event-instance-id)\
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a><a name="entity"></a> 이벤트

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
모든 이벤트입니다.

## <a name="data"></a><a name="data"></a> Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>반환 값

이 이벤트에 포함된 추가 데이터에 대한 포인터입니다. 이 필드를 해석하는 자세한 방법은 [EVENT_DATA](../c-event-data-types/event-data-struct.md)를 참조하세요.

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

추적 내에서 이벤트를 식별하는 번호입니다. 동일한 추적을 여러 번 분석하거나 다시 로깅하는 경우 이 값이 변경되지 않습니다. 이 값을 사용하면 동일한 추적을 통해 여러 분석 또는 재로깅 패스에서 동일한 이벤트를 식별할 수 있습니다.

## <a name="eventname"></a><a name="event-name"></a> EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>반환 값

[EventId](#event-id)식별하는 이벤트 형식의 이름을 포함하는 ANSI 문자열입니다.

## <a name="eventwidename"></a><a name="event-wide-name"></a> EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>반환 값

[EventId](#event-id)로 식별하는 이벤트의 이름을 포함하는 ANSI 문자열입니다.

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

## <a name="timestamp"></a><a name="timestamp"></a> Timestamp

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>반환 값

이벤트가 작업이면 이 함수는 작업이 시작될 때 캡처한 틱 값을 반환합니다. 단순 이벤트의 경우 이 함수는 이벤트가 발생했을 때 캡처한 틱 값을 반환합니다.

::: moniker-end
