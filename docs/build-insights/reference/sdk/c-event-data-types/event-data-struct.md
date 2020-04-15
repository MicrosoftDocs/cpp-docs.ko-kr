---
title: EVENT_DATA 구조
description: C++ 빌드 인사이트 SDK EVENT_DATA 구조 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325603"
---
# <a name="event_data-structure"></a>EVENT_DATA 구조

::: moniker range="<=vs-2015"

C++ 빌드 인사이트 SDK는 Visual Studio 2017 이상과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정합니다. 이 페이지의 목조 테이블 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

구조는 `EVENT_DATA` 분석 또는 리로깅 세션에서 받은 이벤트를 설명합니다. 이러한 세션은 [분석,](../functions/analyze.md) [AnalyzeA,](../functions/analyze-a.md) [AnalyzeW,](../functions/analyze-w.md) [RelogA, RelogA](../functions/relog-a.md)또는 [RelogW](../functions/relog-w.md) 함수를 호출하여 시작됩니다. [Relog](../functions/relog.md)

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

|  |  |
|--|--|
| `EventId` | 이벤트를 식별하는 숫자입니다. 이벤트 식별자 목록은 [EVENT_ID](event-id-enum.md)를 참조하십시오. |
| `EventInstanceId` | 추적 내부의 현재 이벤트를 고유하게 식별하는 숫자입니다. 이 값은 동일한 추적을 여러 번 분석하거나 다시 작업할 때 변경되지 않습니다. 이 필드를 사용하여 여러 분석에서 동일한 이벤트를 식별하거나 동일한 추적을 통해 다시 기록하면 됩니다. |
| `TickFrequency` | 틱으로 측정된 기간을 평가할 때 사용할 초당 틱 수입니다. |
| `StartTimestamp` | 이벤트가 *활동인*경우 이 필드는 활동이 시작된 시점에 캡처된 눈금 값으로 설정됩니다. 이 이벤트가 *단순 이벤트인*경우 이 필드는 이벤트가 발생했을 때 캡처된 눈금 값으로 설정됩니다. |
| `StopTimestamp` | 이벤트가 *활동인*경우 이 필드는 활동이 중지된 시점에 캡처된 눈금 값으로 설정됩니다. 이 활동에 대해 중지 이벤트가 아직 수신되지 않은 경우 이 필드는 0으로 설정됩니다. 이 이벤트가 *단순 이벤트인*경우 이 필드는 0으로 설정됩니다. |
| `ExclusiveDurationTicks` | 이 이벤트가 *활동인*경우 이 필드는 이 활동에서 직접 발생한 틱 수로 설정됩니다. 하위 활동에서 발생한 틱 수는 제외됩니다. 이 필드는 *단순 이벤트에*대해 0으로 설정됩니다. |
| `CPUTicks` | 이 이벤트가 *활동인*경우 이 필드는 이 활동 중에 발생한 CPU 틱 수로 설정됩니다. CPU 틱은 일반 틱과 다릅니다. CPU 틱은 CPU가 활동에서 코드를 실행하는 경우에만 계산됩니다. 활동과 연결된 스레드가 절전 모드일 때 CPU 체크는 계산되지 않습니다. 이 필드는 *단순 이벤트에*대해 0으로 설정됩니다. |
| `ExclusiveCPUTicks` | 이 필드는 자식 `CPUTicks`활동에서 발생한 CPU 체크를 포함하지 않는다는 점을 제외하면 과 같은 의미를 가립니다. 이 필드는 *단순 이벤트에*대해 0으로 설정됩니다. |
| `WallClockTimeResponsibilityTicks` | 이 이벤트가 *활동인*경우 이 필드는 전체 월 시계 시간에 대한 이 활동의 기여도를 나타내는 눈금 수로 설정됩니다. 벽 시계 시간 책임 진드기는 일반 진드기와 다릅니다. 월 시계 시간 책임 틱은 활동 간의 병렬성을 고려합니다. 예를 들어 두 개의 병렬 활동은 50틱의 지속 시간과 동일한 시작 및 중지 시간을 가질 수 있습니다. 이 경우 둘 다 25틱의 월 클럭 시간 책임이 할당됩니다. 이 필드는 *단순 이벤트에*대해 0으로 설정됩니다. |
| `ExclusiveWallClockTimeResponsibilityTicks` | 이 필드는 어린이 활동의 `WallClockTimeResponsibilityTicks`월 시계 시간 책임 체크를 포함하지 않는다는 점을 제외하면 과 같은 의미를 가집니다. 이 필드는 *단순 이벤트에*대해 0으로 설정됩니다. |
| `Data` | 이벤트에 저장된 추가 데이터를 가리킵니다. `EventId` 가리키는 데이터 유형은 필드에 따라 다릅니다. |
| `ProcessId` | 이벤트가 발생한 프로세스의 식별자입니다. |
| `ThreadId` | 이벤트가 발생한 스레드의 식별자입니다. |
| `ProcessorIndex` | 이벤트가 발생한 0인덱싱된 CPU 번호입니다. |
| `EventName` | `EventId`에서 식별된 엔터티의 이름을 포함하는 ANSI 문자열입니다. |
| `EventWideName` | `EventId`에서 식별된 엔터티의 이름을 포함하는 넓은 문자열입니다. |

## <a name="remarks"></a>설명

많은 `EVENT_DATA` 필드에는 틱 수가 포함됩니다. C++ 빌드 인사이트는 윈도우의 성능 카운터를 눈금의 소스로 사용합니다. 필드와 함께 `TickFrequency` 눈금 수를 사용하여 초와 같은 적절한 시간 단위로 변환해야 합니다. 이 변환을 수행하려면 아래 예제를 참조하세요. `EVENT_DATA`활동의 일반 틱 수에 대한 필드가 포함되어 있지 않습니다. 이 값을 얻으려면 에서 `StartTimestamp` `StopTimestamp`뺍니다. `EVENT_DATA`는 C API 사용자가 사용할 수 있는 구조입니다. C++ API 사용자의 경우 [이벤트와](../cpp-event-data-types/event.md) 같은 클래스는 시간 변환을 자동으로 수행합니다.

필드의 값은 `EVENT_DATA` 해당 `EventId` 필드의 값에 따라 다릅니다. `Data` 의 `Data` 값은 아래 표에 설명되어 있습니다. 아래 표에서 일부 엔터티 식별자가 누락되었을 수 있습니다. 이 경우 `Data` 필드는 0으로 `nullptr` 설정됩니다.

| `EventId` 값 | 에 의해 가리키는 유형`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
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
