---
title: TRACING_SESSION_OPTIONS 구조체
description: C++ Build Insights SDK TRACING_SESSION_OPTIONS 구조체 참조에 대해 알아봅니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3147debbfe1ea7ab4bcb4fa3bb8a803e66163557
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922384"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`TRACING_SESSION_OPTIONS` 구조체는 [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 또는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 구조체를 초기화하는 데 사용됩니다. 추적을 수집하는 동안 캡처할 이벤트를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `SystemEventFlags` | 캡처할 시스템 이벤트를 설명하는 비트 마스크입니다. 자세한 내용은 [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md)를 참조하세요. |
| `MsvcEventFlags` | 캡처할 MSVC 이벤트를 설명하는 비트 마스크입니다. 자세한 내용은 [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md)를 참조하세요. |

::: moniker-end
