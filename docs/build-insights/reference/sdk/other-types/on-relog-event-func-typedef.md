---
title: OnRelogEventFunc typedef
description: C++ Build Insights SDK OnRelogEventFunc typedef 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ed639ab59b900f97d29dc69240e45b2f52f2f3b3
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919750"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typedef

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`OnRelogEventFunc` typedef는 [RELOG_CALLBACKS](relog-callbacks-struct.md) 구조체에서 사용되는 함수 서명 중 하나입니다.

## <a name="syntax"></a>구문

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>매개 변수

*eventStack*\
현재 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [이벤트](../event-table.md)를 참조하세요.

*relogSession*\
[InjectEvent](../functions/inject-event.md)를 호출할 때 사용할 다시 로깅 세션 포인터입니다.

*callbackContext*\
[RELOG_DESCRIPTOR](analysis-descriptor-struct.md)에서 이 콜백에 설정된 컨텍스트 값입니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 제어하는 [CALLBACK_CODE](callback-code-enum.md) 값입니다.

::: moniker-end
