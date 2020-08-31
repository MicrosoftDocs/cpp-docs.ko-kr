---
title: CompilerPass 클래스
description: C++ Build Insights SDK CompilerPass 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 054bdf75dcfca42b8c202565fb44df671f17f912
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831621"
---
# <a name="compilerpass-class"></a>CompilerPass 클래스

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용해 [BACK_END_PASS](../event-table.md#back-end-pass) 또는 [FRONT_END_PASS](../event-table.md#front-end-pass) 이벤트를 일치시킬 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>멤버

해당하는 [활동](activity.md) 기본 클래스에서 상속된 멤버와 함께 `CompilerPass` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructors"></a>생성자

[CompilerPass](#compiler-pass)

### <a name="enums"></a>열거형

#### <a name="passcode"></a>PassCode

|값|설명|
|-|-|
|FRONT_END|프런트 엔드 패스입니다.|
|BACK_END|백 엔드 패스입니다.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[PassCode](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a> CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
[BACK_END_PASS](../event-table.md#back-end-pass) 또는 [FRONT_END_PASS](../event-table.md#front-end-pass) 이벤트입니다.

## <a name="inputsourcepath"></a><a name="input-source-path"></a> InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>반환 값

이 컴파일러 패스로 처리된 입력 원본 파일의 절대 경로입니다.

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>반환 값

이 컴파일러 패스로 처리된 출력 개체 파일의 절대 경로입니다.

## <a name="passcode"></a><a name="pass-code"></a> PassCode

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>반환 값

이 CompilerPass 개체가 어떤 컴파일러 패스를 표시하는지 나타내는 코드입니다.

::: moniker-end
