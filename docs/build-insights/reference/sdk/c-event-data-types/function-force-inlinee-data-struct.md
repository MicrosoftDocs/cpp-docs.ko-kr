---
title: FUNCTION_FORCE_INLINEE_DATA 구조체
description: C++ Build Insights SDK FUNCTION_FORCE_INLINEE_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d64a23c603d1f30726f30ffc91c1889c51138ef6
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041707"
---
# <a name="function_force_inlinee_data-structure"></a>FUNCTION_FORCE_INLINEE_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_FORCE_INLINEE_DATA` 구조체는 강제 인라인 함수를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `Name` | UTF-8로 인코딩된 함수 이름입니다. |
| `Size` | 함수의 크기입니다(중간 명령 수). |

::: moniker-end
