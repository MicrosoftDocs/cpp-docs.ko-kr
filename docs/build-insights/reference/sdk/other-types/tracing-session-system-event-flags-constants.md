---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS 상수
description: C++ Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS 상수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 346c955355ffbc6c062a34bf928f16ccd3940154
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922375"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS 상수

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`TRACING_SESSION_SYSTEM_EVENT_FLAGS` 상수는 추적 과정에서 수집할 시스템 이벤트를 설명하는 용도로 사용합니다. 이 상수를 사용하여 [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) 구조체의 `SystemEventFlags` 필드를 초기화하세요.

## <a name="syntax"></a>구문

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>멤버

| Name | 이 플래그를 이용해 설정한 이벤트 |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | 이 플래그는 명시적으로 지정하지 않더라도 기본적으로 C++ Build Insights SDK에 의해 활성화됩니다. C++ Build Insights가 정상적으로 작동하려면 필요한 기본 시스템 이벤트를 활성화합니다. 이 플래그로 활성화한 이벤트는 프로세스, 스레드, 이미지 로딩 관련 정보를 제공합니다. 이러한 이벤트를 비활성화할 수 없습니다. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 샘플 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | 이 플래그는 모든 시스템 이벤트를 설정합니다. |

::: moniker-end
