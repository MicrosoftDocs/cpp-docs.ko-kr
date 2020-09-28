---
title: TRACING_SESSION_STATISTICS 구조체
description: C++ Build Insights SDK TRACING_SESSION_STATISTICS 구조체 참조에 대해 알아봅니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c1db302d9e816591624f0fc63633351d32684097
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742764"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS` 구조체는 수집된 추적에 대한 통계를 설명합니다. 해당 필드는 추적 세션을 중지할 때 설정됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `MSVCEventsLost` | 삭제된 MSVC 이벤트의 수입니다. |
| `MSVCBuffersLost` | 삭제된 MSVC 이벤트 버퍼의 수입니다. |
| `SystemEventsLost` | 삭제된 시스템 이벤트의 수입니다. |
| `SystemBuffersLost` | 삭제된 시스템 이벤트 버퍼의 수입니다. |

## <a name="remarks"></a>설명

이 구조체는 다음 함수를 호출할 때 채워집니다.

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
