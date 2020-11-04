---
title: MatchEventInMemberFunction
description: C++ Build Insights SDK MatchEventInMemberFunction 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62a7bf6bde62dee7fdf5b1d2ce9044491a123f94
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920192"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MatchEventInMemberFunction` 함수를 사용하여 이벤트를 멤버 함수의 첫 번째 매개 변수에 설명된 유형과 일치하는지 비교할 수 있습니다. 일치하는 이벤트는 추가 처리를 위해 멤버 함수로 전달됩니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>매개 변수

*TInterface*\
멤버 함수를 포함하는 형식입니다.

*TReturn*\
멤버 함수의 반환 형식입니다.

*TEvent*\
일치하는지 비교할 이벤트의 유형입니다.

*TExtraParams*\
일치하는지 비교할 이벤트 유형과 함께 멤버 함수에서 허용하는 추가 매개 변수의 형식입니다.

*TExtraArgs*\
`MatchEventInMemberFunction`에 전달된 추가 인수의 형식입니다.

*event*\
*TEvent* 에 설명된 이벤트 유형과 일치하는지 비교할 이벤트입니다.

*objectPtr*\
*memberFunc* 가 호출되는 개체에 대한 포인터입니다.

*memberFunc*\
일치하는지 비교할 이벤트 유형을 설명하는 멤버 함수입니다.

*extraArgs*\
이벤트 유형 매개 변수와 함께 *memberFunc* 로 완벽하게 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

일치가 성공하면 **`true`** 이고 그렇지 않으면 **`false`** 인 **`bool`** 값입니다.

## <a name="remarks"></a>설명

*TEvent* 매개 변수에 사용할 이벤트 유형은 캡처 클래스 목록에서 선택할 수 있습니다. 일치하는지 비교하는 데 사용할 수 있는 이벤트 및 캡처 클래스의 목록은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
