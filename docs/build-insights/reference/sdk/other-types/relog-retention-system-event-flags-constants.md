---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS 상수
description: C++ Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS 상수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e0144835568dab12c8593fe8fbfa820f6cde7647
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919735"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS 상수

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`RELOG_RETENTION_SYSTEM_EVENT_FLAGS` 상수는 다시 로그된 추적에 유지할 시스템 이벤트를 설명하는 데 사용됩니다. 이를 사용하여 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 구조체의 `SystemEventsRetentionFlags` 필드를 초기화합니다.

## <a name="syntax"></a>구문

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 샘플 시스템 이벤트를 다시 로그된 추적에 유지합니다. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 모든 시스템 이벤트를 다시 로그된 추적에 유지합니다. |

## <a name="remarks"></a>설명

::: moniker-end
