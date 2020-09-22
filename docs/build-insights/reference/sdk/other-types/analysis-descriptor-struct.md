---
title: ANALYSIS_DESCRIPTOR 구조체
description: C++ Build Insights SDK ANALYSIS_DESCRIPTOR 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 325910f747f75f1f8d2904c248f8de69566464c7
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042006"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_DESCRIPTOR` 구조체는 [AnalyzeA](../functions/analyze-a.md) 및 [AnalyzeW](../functions/analyze-w.md) 함수와 함께 사용됩니다. ETW(Windows용 이벤트 추적) 추적을 분석하는 방법을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `NumberOfPasses` | ETW 추적에 수행해야 하는 분석 패스의 수입니다. |
| `Callbacks` | 분석 세션 중에 호출할 함수를 지정하는 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 개체입니다. |
| `Context` | `Callbacks`에 지정된 모든 콜백 함수에 인수로 전달되는 사용자 제공 컨텍스트입니다. |

## <a name="remarks"></a>설명

`Callbacks` 구조체는 비멤버 함수에 대한 포인터만 허용합니다. `Context`를 개체 포인터로 설정하면 이러한 제한을 해결할 수 있습니다. 이 개체 포인터는 모든 비멤버 콜백 함수에 인수로 전달됩니다. 비멤버 콜백 함수 내에서 멤버 함수를 호출하려면 이 포인터를 사용합니다.

::: moniker-end
