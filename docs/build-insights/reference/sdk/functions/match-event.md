---
title: MatchEvent
description: C++ Build Insights SDK MatchEvent 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1486a76aab7b9a4f3b4da209f4f163b4c65b0ac4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920101"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MatchEvent` 함수는 이벤트를 이벤트 유형 목록과 일치하는지 비교하는 데 사용됩니다. 이벤트가 목록의 형식과 일치하면 추가 처리를 위해 처리기에 전달됩니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>매개 변수

*TEvent*\
일치하는지 비교하려는 첫 번째 이벤트 유형입니다.

*TEvents*\
일치하는지 비교하려는 나머지 이벤트 유형입니다.

*TCallable*\
`operator()`를 지원하는 형식입니다. 이 연산자에 전달되는 인수에 대한 자세한 내용은 *callable* 매개 변수 설명을 참조하세요.

*TExtraArgs*\
`MatchEvent`에 전달된 추가 인수의 형식입니다.

*event*\
*TEvent* 및 *TEvents* 에 설명된 이벤트 유형과 일치하는지 비교할 이벤트입니다.

*callable*\
`MatchEvent`는 *TEvent* 및 *TEvents* 에 설명된 이벤트 유형과 이벤트가 일치하면 *callable* 을 호출합니다. *callable* 에 전달되는 첫 번째 인수는 일치하는 이벤트 유형의 r-value입니다. *extraArgs* 매개 변수 팩은 *callable* 의 나머지 매개 변수에서 완벽하게 전달됩니다.  

*extraArgs*\
일치하는 이벤트 유형과 함께 *callable* 로 완벽하게 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

일치가 성공하면 **`true`** 이고 그렇지 않으면 **`false`** 인 **`bool`** 값입니다.

## <a name="remarks"></a>설명

*TEvent* 및 *TEvents* 매개 변수에 사용할 이벤트 유형은 캡처 클래스 목록에서 선택됩니다. 일치하는지 비교하는 데 사용할 수 있는 이벤트 및 캡처 클래스의 목록은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
