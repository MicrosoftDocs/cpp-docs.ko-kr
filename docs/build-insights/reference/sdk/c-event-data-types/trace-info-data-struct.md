---
title: TRACE_INFO_DATA 구조체
description: C++ Build Insights SDK TRACE_INFO_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 38683ff2c5c5165b5fe2a1969ccf80fbfca3693f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040459"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA` 구조체는 분석 또는 다시 로그된 추적을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `LogicalProcessorCount` | 추적이 수집된 컴퓨터의 논리 프로세서 수입니다. |
| `TickFrequency` | 틱 단위로 기간을 평가할 때 사용할 초당 틱 수입니다. |
| `StartTimestamp` | 이 필드는 추적이 시작될 때 캡처된 틱 값으로 설정됩니다. |
| `StopTimestamp` | 이 필드는 추적이 중지될 때 캡처된 틱 값으로 설정됩니다. |

## <a name="remarks"></a>설명

`StopTimestamp`에서 `StartTimestamp`를 빼서 전체 추적 중에 경과된 틱 수를 구합니다. `TickFrequency`를 사용하여 결과 값을 시간 단위로 변환합니다. 틱을 시간 단위로 변환하는 예는 [EVENT_DATA](event-data-struct.md)를 참조하세요.

::: moniker-end
