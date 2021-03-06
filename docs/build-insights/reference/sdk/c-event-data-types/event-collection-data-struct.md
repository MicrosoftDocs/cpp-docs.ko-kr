---
title: EVENT_COLLECTION_DATA 구조체
description: C++ Build Insights SDK EVENT_COLLECTION_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 17daaa6feb784c501d180a982cd4ad2b405ccf67
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921089"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`EVENT_COLLECTION_DATA` 구조체는 [EVENT_DATA](event-data-struct.md) 요소의 배열을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `Count` | 배열의 `EVENT_DATA` 요소 수입니다. |
| `Elements` | 배열의 첫 번째 `EVENT_DATA` 요소에 대한 포인터입니다. |

::: moniker-end
