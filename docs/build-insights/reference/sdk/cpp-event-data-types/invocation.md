---
title: Invocation 클래스
description: C++ Build Insights SDK Invocation 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dfd463c7b9ca72dc14ad74b3759fdd1e3730d5a9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923146"
---
# <a name="invocation-class"></a>Invocation 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`Invocation` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 [COMPILER](../event-table.md#compiler) or [LINKER](../event-table.md#linker) 이벤트를 일치시켜야 합니다.

## <a name="syntax"></a>구문

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>멤버

해당하는 [활동](activity.md) 기본 클래스에서 상속된 멤버와 함께 `Invocation` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructors"></a>생성자

[호출](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a> Invocation

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
[COMPILER](../event-table.md#compiler) 또는 [LINKER](../event-table.md#linker) 이벤트입니다.

## <a name="toolpath"></a><a name="tool-path"></a> ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>반환 값

호출된 도구의 절대 경로입니다.

## <a name="toolversion"></a><a name="tool-version"></a> ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>반환 값

호출된 도구의 버전([INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) 참조)입니다.

## <a name="toolversionstring"></a><a name="tool-version-string"></a> ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>반환 값

호출된 도구의 버전(ANSI 문자열)입니다.

## <a name="type"></a><a name="type"></a> 형식

```cpp
Type Type() const;
```

### <a name="return-value"></a>반환 값

호출된 도구를 나타내는 코드입니다.

## <a name="workingdirectory"></a><a name="working-directory"></a> WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>반환 값

도구가 호출된 디렉터리의 절대 경로입니다.

::: moniker-end
