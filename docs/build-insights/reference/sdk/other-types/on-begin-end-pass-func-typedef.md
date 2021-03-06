---
title: OnBeginEndPassFunc 형식 정의
description: C++ Build Insights SDK OnBeginEndPassFunc 형식 정의 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a97ae792392e5cc0dc83bab00a92d05609a4815
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922495"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc 형식 정의

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`OnBeginEndPassFunc` 형식 정의는 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 및 [RELOG_CALLBACKS](relog-callbacks-struct.md) 구조체에서 사용되는 함수 서명 중 하나입니다.

## <a name="syntax"></a>구문

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `callbackContext` |  |

::: moniker-end
