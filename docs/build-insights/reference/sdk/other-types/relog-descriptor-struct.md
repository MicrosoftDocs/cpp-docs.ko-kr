---
title: RELOG_DESCRIPTOR 구조체
description: C++ Build Insights SDK RELOG_DESCRIPTOR 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 802e51ec4246f5ee95e3d204290743ffbd03be69
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041395"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_DESCRIPTOR` 구조체는 [RelogA](../functions/relog-a.md) 및 [RelogW](../functions/relog-w.md) 함수와 함께 사용됩니다. ETW(Windows용 이벤트 추적) 추적을 다시 로그하는 방법을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `NumberOfAnalysisPasses` | 다시 로깅 세션의 분석 단계 도중 ETW 추적에 수행해야 하는 분석 패스의 수입니다. |
| `AnalysisCallbacks` | 다시 로깅 세션의 분석 단계 중에 호출할 함수를 지정하는 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 개체입니다. |
| `RelogCallbacks` | 다시 로깅 세션의 다시 로깅 단계 중에 호출할 함수를 지정하는 [RELOG_CALLBACKS](relog-callbacks-struct.md) 개체입니다. |
| `SystemEventsRetentionFlags` | 다시 로그된 추적에 유지할 시스템 ETW 이벤트를 지정하는 [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) 비트 마스크입니다. |
| `AnalysisContext` | `AnalysisCallbacks`에 지정된 모든 콜백 함수에 인수로 전달되는 사용자 제공 컨텍스트입니다. |
| `RelogContext` | `RelogCallbacks`에 지정된 모든 콜백 함수에 인수로 전달되는 사용자 제공 컨텍스트입니다. |

## <a name="remarks"></a>설명

다시 로깅 세션 중에 ETW 이벤트 다시 로깅은 `RelogCallbacks`에 지정된 콜백 함수를 통해 사용자가 제어합니다. 그러나 CPU 샘플과 같은 시스템 ETW 이벤트는 이러한 콜백 함수로 전달되지 않습니다. `SystemEventsRetentionFlags` 필드를 사용하여 시스템 ETW 이벤트 다시 로깅을 제어할 수 있습니다.

`AnalysisCallbacks` 및 `RelogCallbacks` 구조체는 비멤버 함수에 대한 포인터만 허용합니다. 이들을 개체 포인터로 설정하면 이러한 제한을 해결할 수 있습니다. 이 개체 포인터는 모든 비멤버 콜백 함수에 인수로 전달됩니다. 비멤버 콜백 함수 내에서 멤버 함수를 호출하려면 이 포인터를 사용합니다.

다시 로깅 세션의 분석 단계는 항상 다시 로깅 단계 전에 실행됩니다.

::: moniker-end
