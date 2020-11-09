---
title: FrontEndFile 클래스
description: C++ Build Insights SDK FrontEndFile 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7715a153df538eab94b8de5281a91d4f6b439ff9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920660"
---
# <a name="frontendfile-class"></a>FrontEndFile 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`FrontEndFile` 클래스는 [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) 및 [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 함수와 함께 사용 됩니다. 이를 사용하여 [FRONT_END_FILE](../event-table.md#front-end-file) 이벤트를 일치시켜야 합니다.

## <a name="syntax"></a>구문

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>멤버

해당하는 [활동](activity.md) 기본 클래스에서 상속된 멤버와 함께 `FrontEndFile` 클래스에는 다음 멤버가 포함됩니다.

### <a name="constructors"></a>생성자

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Functions

[Path](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a> FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>매개 변수

*event*\
[FRONT_END_FILE_DATA](../event-table.md#front-end-file) 이벤트입니다.

## <a name="path"></a><a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>반환 값

UTF-8로 인코딩된 파일의 절대 경로입니다.

::: moniker-end
