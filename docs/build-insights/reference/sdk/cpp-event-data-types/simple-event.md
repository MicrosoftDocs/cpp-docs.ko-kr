---
title: SimpleEvent 클래스
description: C++ Build Insights SDK SimpleEvent 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dc09a279157482089adedc660395feaa98376dae
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922999"
---
# <a name="simpleevent-class"></a>SimpleEvent 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`SimpleEvent` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 모든 단순 이벤트를 일치시켜야 합니다. `SimpleEvent` 클래스로 일치시킬 수 있는 이벤트를 모두 확인하려면 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>멤버

해당하는 [Event](event.md) 기본 클래스에서 상속된 멤버와 함께 `SimpleEvent` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructors"></a>생성자

[SimpleEvent](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a> SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
모든 단순 이벤트입니다.

::: moniker-end
