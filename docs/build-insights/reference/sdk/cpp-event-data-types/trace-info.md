---
title: TraceInfo 클래스
description: C++ Build Insights SDK TraceInfo 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b772cc13981720c73238e56a561ca92144775cb4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922922"
---
# <a name="traceinfo-class"></a>TraceInfo 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`TraceInfo` 클래스는 분석 중이거나 다시 로깅 중인 추적에 관한 유용한 속성에 액세스하는 용도로 사용합니다.

## <a name="syntax"></a>구문

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>설명

`StopTimestamp`에서 `StartTimestamp`를 차감하여 전체 추적 중에 경과된 틱 수를 구합니다. `TickFrequency`를 사용하여 결과 값을 시간 단위로 변환합니다. [EVENT_DATA](../c-event-data-types/event-data-struct.md)에서 틱을 시간으로 변환하는 예를 확인할 수 있습니다.

틱을 직접 변환하지 않고 싶다면 `TraceInfo` 클래스에서 제공하는 추적 기간을 나노초 단위로 반환하는 멤버 함수를 사용하세요. 표준 C++ `chrono` 라이브러리를 사용하여 이 값을 다른 시간 단위로 변환해야 합니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a> Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>반환 값

작업 기간(나노초)입니다.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a> LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>반환 값

추적이 수집된 컴퓨터의 논리 프로세서 수입니다.

## <a name="starttimestamp"></a><a name="start-timestamp"></a> StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>반환 값

추적을 시작할 때 캡처한 틱 값입니다.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a> StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>반환 값

추적이 중단되었을 때 캡처한 틱 값입니다.

## <a name="tickfrequency"></a><a name="tick-frequency"></a> TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>반환 값

틱 단위로 기간을 평가할 때 사용할 초당 틱 수입니다.

## <a name="traceinfo"></a><a name="trace-info"></a> TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>매개 변수

*data*\
추적 관련 정보를 포함하는 데이터입니다.

::: moniker-end
