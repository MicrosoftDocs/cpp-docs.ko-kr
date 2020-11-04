---
title: EVENT_DATA 구조체
description: C++ Build Insights SDK EVENT_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 617a82055f406c130d74a2823c2cf00aa1beef36
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923610"
---
# <a name="event_data-structure"></a>EVENT_DATA 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`EVENT_DATA` 구조체는 분석 또는 재로깅 세션에서 수신되는 이벤트를 설명합니다. 이러한 세션은 [Analyze](../functions/analyze.md), [AnalyzeA](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [Relog](../functions/relog.md), [RelogA](../functions/relog-a.md) 또는 [RelogW](../functions/relog-w.md) 함수를 호출하여 시작됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `EventId` | 이벤트를 식별하는 번호입니다. 이벤트 식별자 목록은 [EVENT_ID](event-id-enum.md)를 참조하세요. |
| `EventInstanceId` | 추적 내에서 현재 이벤트를 고유하게 식별하는 번호입니다. 동일한 추적을 여러 번 분석하거나 다시 로깅하는 경우 이 값이 변경되지 않습니다. 이 필드를 사용하여 동일한 추적을 통해 여러 분석 또는 재로깅 패스에서 동일한 이벤트를 식별할 수 있습니다. |
| `TickFrequency` | 틱 단위로 기간을 평가할 때 사용할 초당 틱 수입니다. |
| `StartTimestamp` | 이벤트가 작업이면 이 필드는 작업이 시작될 때 캡처된 틱 값으로 설정됩니다. 이 이벤트가 단순 이벤트인 경우 이 필드는 이벤트가 발생했을 때 캡처된 틱 값으로 설정됩니다. |
| `StopTimestamp` | 이벤트가 작업이면 이 필드는 작업이 중지될 때 캡처된 틱 값으로 설정됩니다. 이 작업에 대한 중지 이벤트가 아직 수신되지 않은 경우 이 필드는 0으로 설정됩니다. 이 이벤트가 단순 이벤트이면 이 필드는 0으로 설정됩니다. |
| `ExclusiveDurationTicks` | 이 이벤트가 작업이면 이 필드는 이 작업에서 직접 발생한 틱 수로 설정됩니다. 자식 활동에서 발생한 틱 수는 제외됩니다. 이 필드는 단순 이벤트에 대해 0으로 설정됩니다. |
| `CPUTicks` | 이 이벤트가 작업이면 이 필드는 이 작업에서 발생한 CPU 틱 수로 설정됩니다. CPU 틱은 일반 틱과 다릅니다. CPU 틱은 작업에서 CPU가 코드를 실행하는 경우에만 계산됩니다. 작업과 연결된 스레드가 절전 모드이면 CPU 틱이 계산되지 않습니다. 이 필드는 단순 이벤트에 대해 0으로 설정됩니다. |
| `ExclusiveCPUTicks` | 이 필드는 자식 활동에서 발생한 CPU 틱을 포함하지 않는다는 점을 제외하고 `CPUTicks`와 동일한 의미를 갖습니다. 이 필드는 단순 이벤트에 대해 0으로 설정됩니다. |
| `WallClockTimeResponsibilityTicks` | 이 이벤트가 작업인 경우 이 필드는 전체 벽시계 시간에 대한 이 활동의 기여를 나타내는 틱 수로 설정됩니다. 벽시계 시간 책임 틱은 일반 틱과 다릅니다. 벽시계 시간 책임 틱은 작업 간의 병렬 처리를 고려합니다. 예를 들어 두 병렬 작업에서 기간이 50이고 시작 및 중지 시간이 동일할 수 있습니다. 이 경우 두 작업 모두 벽시계 시간 책임이 25틱으로 할당됩니다. 이 필드는 단순 이벤트에 대해 0으로 설정됩니다. |
| `ExclusiveWallClockTimeResponsibilityTicks` | 이 필드는 자식 활동의 벽시계 시간 책임이 포함되지 않는다는 점을 제외하고 `WallClockTimeResponsibilityTicks`와 동일한 의미를 갖습니다. 이 필드는 단순 이벤트에 대해 0으로 설정됩니다. |
| `Data` | 이벤트에 저장된 추가 데이터를 가리킵니다. `EventId` 필드에 따라 가리키는 데이터 형식이 다릅니다. |
| `ProcessId` | 이벤트가 발생한 프로세스의 식별자입니다. |
| `ThreadId` | 이벤트가 발생한 스레드의 식별자입니다. |
| `ProcessorIndex` | 이벤트가 발생한 0으로 인덱싱된 CPU 번호입니다. |
| `EventName` | `EventId`로 식별되는 엔터티의 이름을 포함하는 ANSI 문자열입니다. |
| `EventWideName` | `EventId`로 식별되는 엔터티의 이름을 포함하는 와이드 문자열입니다. |

## <a name="remarks"></a>설명

`EVENT_DATA`에서는 많은 필드에 틱 수가 포함됩니다. C++ Build Insights는 Windows의 성능 카운터를 틱의 소스로 사용합니다. 틱 수는 `TickFrequency` 필드와 함께 사용하여 초와 같은 적절한 시간 단위로 변환해야 합니다. 이 변환을 수행하려면 아래 예제를 참조하세요. `EVENT_DATA`에는 작업의 일반 틱 수에 대한 필드가 포함되지 않습니다. 이 값을 얻으려면 `StopTimestamp`에서 `StartTimestamp`을 차감합니다. `EVENT_DATA`는 C API 사용자가 사용하기 위한 구조체입니다. C++ API 사용자의 경우 [이벤트](../cpp-event-data-types/event.md) 같은 클래스가 자동으로 시간 변환을 수행합니다.

`EVENT_DATA` `Data` 필드의 값은 `EventId` 필드의 값에 따라 달라집니다. `Data`의 값은 아래 표에 설명되어 있습니다. 아래 테이블에 일부 엔터티 식별자가 없을 수 있습니다. 이 경우 `Data` 필드는 **`nullptr`** 또는 0으로 설정됩니다.

| `EventId` 값 | `Data`가 가리키는 형식 |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>틱 변환 예제

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
