---
title: SymbolName 클래스
description: C++ Build Insights SDK SymbolName 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a749d95b3812df8b1cc0cd7d2da037e98467cefc
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920478"
---
# <a name="symbolname-class"></a>SymbolName 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`SymbolName` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 [SYMBOL_NAME](../event-table.md#symbol-name) 이벤트를 일치시켜야 합니다.

## <a name="syntax"></a>구문

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>멤버

해당하는 [SimpleEvent](simple-event.md) 기본 클래스에서 상속된 멤버와 함께 `SymbolName` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructors"></a>생성자

[SymbolName](#symbol-name)

### <a name="functions"></a>Functions

[Key](#key)
[Name](#name)

## <a name="key"></a><a name="key"></a> Key

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>반환 값

이 기호가 나타내는 형식의 숫자 식별자입니다. 이 식별자는 컴파일러 프런트 엔드 패스 내에서 하나만 존재합니다.

## <a name="name"></a><a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>반환 값

기호가 나타내는 형식의 이름으로, UTP-8로 인코딩됩니다.

## <a name="symbolname"></a><a name="symbol-name"></a> SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
[SYMBOL_NAME](../event-table.md#symbol-name) 이벤트입니다.

::: moniker-end
