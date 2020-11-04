---
title: MatchEventStackInMemberFunction
description: C++ Build Insights SDK MatchEventStackInMemberFunction 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4d416a10d5e2803cd978243a1e44625a2e696d42
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920179"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MatchEventStackInMemberFunction` 함수는 이벤트 스택을 멤버 함수의 매개 변수 목록에 설명된 특정 이벤트 계층 구조와 일치하는지 비교하는 데 사용됩니다. 일치하는 계층 구조는 추가 처리를 위해 멤버 함수로 전달됩니다. 이벤트, 이벤트 스택 및 계층 구조에 대한 자세한 내용은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>매개 변수

*TInterface*\
멤버 함수를 포함하는 형식입니다.

*TReturn*\
멤버 함수의 반환 형식입니다.

*T1* , ..., *T10*\
일치하는지 비교할 이벤트 계층 구조를 설명하는 형식입니다.

*TExtraParams*\
멤버 함수에서 허용하는 추가 매개 변수의 형식 및 이벤트 계층 구조 형식입니다.

*TExtraArgs*\
`MatchEventStackInMemberFunction`에 전달된 추가 인수의 형식입니다.

*eventStack*\
*T1* ~ *T10* 에 설명된 이벤트 유형 계층 구조와 일치하는지 비교할 이벤트 스택입니다.

*objectPtr*\
*memberFunc* 에 호출되는 개체에 대한 포인터입니다.

*memberFunc*\
일치하는지 비교할 이벤트 유형 계층 구조를 설명하는 멤버 함수입니다.

*extraArgs*\
이벤트 유형 계층 구조 매개 변수와 함께 *memberFunc* 로 완벽하게 전달되는 인수입니다.

### <a name="return-value"></a>반환 값

일치가 성공하면 **`true`** 이고 그렇지 않으면 **`false`** 인 **`bool`** 값입니다.

## <a name="remarks"></a>설명

*eventStack* 의 마지막 이벤트는 항상 일치하는지 비교할 이벤트 유형 계층 구조의 마지막 항목과 비교됩니다. 이벤트 유형 계층 구조에 있는 다른 모든 유형은 동일한 순서일 경우 마지막 항목을 제외하고 *eventStack* 의 모든 위치와 일치하는지 비교될 수 있습니다.

*T1* ~ *T10* 매개 변수에 사용할 이벤트 유형은 캡처 클래스 목록에서 선택됩니다. 일치하는지 비교하는 데 사용할 수 있는 이벤트 및 캡처 클래스의 목록은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
