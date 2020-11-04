---
title: RELOG_CALLBACKS 구조체
description: C++ Build Insights SDK RELOG_CALLBACKS 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b3beb656aa72ce4c8519c56c4c8bf6ca6577cf4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919801"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`RELOG_CALLBACKS` 구조체는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 개체를 초기화할 때 사용됩니다. ETW(Windows용 이벤트 추적) 추적을 다시 로그하는 동안 호출할 함수를 지정합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `OnStartActivity` | 작업 시작 이벤트를 처리하기 위해 호출됩니다. |
| `OnStopActivity` | 작업 중지 이벤트를 처리하기 위해 호출됩니다. |
| `OnSimpleEvent` | 간단한 이벤트를 처리하기 위해 호출됩니다. |
| `OnTraceInfo` | `OnBeginReloggingPass`가 호출된 후에 다시 로깅 패스가 시작될 때 한 번 호출됩니다. |
| `OnBeginRelogging` | 다시 로깅 세션을 시작할 때 다시 로깅 패스가 시작되기 전에 호출됩니다. |
| `OnEndRelogging` | 다시 로깅 패스가 종료된 후 다시 로깅 세션을 종료할 때 호출됩니다. |
| `OnBeginReloggingPass` | 다시 로깅 패스를 시작할 때 이벤트를 처리하기 전에 호출됩니다. |
| `OnEndReloggingPass` | 모든 이벤트를 처리한 후 다시 로깅 패스를 종료할 때 호출됩니다. |

## <a name="remarks"></a>설명

`RELOG_CALLBACKS` 구조체의 모든 멤버는 유효한 함수를 가리켜야 합니다. 허용되는 함수 서명에 대한 자세한 내용은 [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md) 및 [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)을 참조하세요.

::: moniker-end
