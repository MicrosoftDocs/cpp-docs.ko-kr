---
title: MatchEventStack
description: C++ Build Insights SDK MatchEventStack 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08627b6af601f6894aa228683ffb51232b015310
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922823"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MatchEventStack` 함수는 이벤트 스택을 특정 이벤트 계층 구조와 일치하는지 비교하는 데 사용됩니다. 일치하는 계층 구조는 추가 처리를 위해 처리기로 전달됩니다. 이벤트, 이벤트 스택 및 계층 구조에 대한 자세한 내용은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>매개 변수

*TEvent*\
이벤트 스택에서 일치하는지 비교할 최상위 부모의 형식입니다.

*TEvents*\
이벤트 스택에서 일치하는지 비교하려는 나머지 형식입니다.

*TCallable*\
`operator()`를 지원하는 형식입니다. 이 연산자에 전달되는 인수에 대한 자세한 내용은 *callable* 매개 변수 설명을 참조하세요.

*TExtraArgs*\
`MatchEventStack`에 전달되는 추가 인수의 형식입니다.

*eventStack*\
*TEvent* 및 *TEvents* 에 설명된 이벤트 유형 계층 구조와 일치하는지 비교할 이벤트 스택입니다.

*callable*\
`MatchEventStack`은 이벤트 스택이 *TEvent* 및 *TEvents* 에 설명된 이벤트 유형 계층 구조와 일치하면 *callable* 을 호출합니다. 이벤트 계층 구조에 있는 각 형식에 대해 하나의 r-value 인수가 *callable* 에 전달됩니다. *extraArgs* 매개 변수 팩은 *callable* 의 나머지 매개 변수에서 완벽하게 전달됩니다.

*extraArgs*\
일치하는 이벤트 유형과 함께 *callable* 로 완벽하게 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

일치가 성공하면 **`true`** 이고 그렇지 않으면 **`false`** 인 **`bool`** 값입니다.

## <a name="remarks"></a>설명

*eventStack* 의 마지막 이벤트는 항상 연결된 \[*TEvent* , *TEvents...* \] 형식 목록의 마지막 항목과 일치하는지 비교됩니다. 다른 모든 *TEvent* 및 *TEvents* 항목은 동일한 순서일 경우 마지막 항목을 제외하고 *eventStack* 의 모든 위치와 일치하는지 비교될 수 있습니다.

*TEvent* 및 *TEvents* 매개 변수에 사용할 이벤트 유형은 캡처 클래스 목록에서 선택됩니다. 일치하는지 비교하는 데 사용할 수 있는 이벤트 및 캡처 클래스의 목록은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
