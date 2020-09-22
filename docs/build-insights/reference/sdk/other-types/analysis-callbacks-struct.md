---
title: ANALYSIS_CALLBACKS 구조체
description: C++ Build Insights SDK ANALYSIS_CALLBACKS 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a24755befdd446051ae376b49d3dca06c7bc3320
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041044"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_CALLBACKS` 구조체는 [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 또는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 개체를 초기화할 때 사용됩니다. ETW(Windows용 이벤트 추적) 추적을 분석하거나 다시 로그하는 동안 호출할 함수를 지정합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `OnStartActivity` | 작업 시작 이벤트를 처리하기 위해 호출됩니다. |
| `OnStopActivity` | 작업 중지 이벤트를 처리하기 위해 호출됩니다. |
| `OnSimpleEvent` | 간단한 이벤트를 처리하기 위해 호출됩니다. |
| `OnTraceInfo` | 분석 세션의 경우 각 분석 패스가 시작될 때 호출됩니다. 다시 로깅 세션의 경우 각 분석 패스가 시작될 때와 다시 로깅 패스가 시작될 때 호출됩니다. 이 함수는 OnBeginAnalysisPass가 호출된 후에만 호출됩니다. |
| `OnBeginAnalysis` | 분석 세션의 경우 분석 패스가 시작되기 전에 호출됩니다. 다시 로깅 세션의 경우 분석 단계가 시작되기 전에 두 번 호출됩니다. 즉, 다시 로깅 세션 시작을 알리기 위해 한 번, 분석 단계 시작을 알리기 위해 한 번 더 호출됩니다. |
| `OnEndAnalysis` | 분석 세션의 경우 이 함수는 모든 분석 패스가 종료된 후에 호출됩니다. 다시 로깅 세션의 경우 이 함수는 분석 단계의 모든 분석 패스가 종료될 때 호출됩니다. 그런 다음 다시 로깅 패스가 종료된 후 다시 호출됩니다. |
| `OnBeginAnalysisPass` | 이벤트를 처리하기 전에 분석 패스 또는 다시 로깅 패스를 시작할 때 호출됩니다. |
| `OnEndAnalysisPass` | 모든 이벤트를 처리한 후에 분석 패스 또는 다시 로깅 패스를 종료할 때 호출됩니다. |

## <a name="remarks"></a>설명

다시 로깅 세션의 분석 단계는 다시 로깅 세션의 일부로 간주되며 여러 분석 패스를 포함할 수 있습니다. 이러한 이유로 다시 로깅 세션이 시작될 때 `OnBeginAnalysis`가 한 행에서 두 번 호출됩니다. `OnEndAnalysis`는 분석 단계가 종료할 때, 다시 로깅 단계를 시작하기 전에, 그리고 다시 로깅 단계가 종료될 때 호출됩니다. 다시 로깅 단계에는 항상 단일 다시 로깅 패스가 포함됩니다.

분석기는 다시 로깅 세션의 분석 및 다시 로깅 단계 모두에 포함될 수 있습니다. 이러한 분석기는 OnBeginAnalysis 및 `OnEndAnalysis` 호출 쌍을 추적하여 현재 진행 중인 단계를 확인할 수 있습니다. `OnEndAnalysis` 호출 없이 두 번의 `OnBeginAnalysis` 호출은 분석 단계가 진행되고 있음을 의미합니다. 두 번의 `OnBeginAnalysis` 호출과 한 번의 `OnEndAnalysis` 호출은 다시 로깅 단계가 진행되고 있음을 의미합니다. 두 번의 OnBeginAnalysis 호출과 두 번의 `OnEndAnalysis` 호출은 두 단계가 모두 종료되었음을 의미합니다.

`ANALYSIS_CALLBACKS` 구조체의 모든 멤버는 유효한 함수를 가리켜야 합니다. 허용되는 함수 서명에 대한 자세한 내용은 [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md) 및 [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)을 참조하세요.

::: moniker-end
