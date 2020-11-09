---
title: OnTraceInfoFunc typedef
description: C++ Build Insights SDK OnTraceInfoFunc typedef 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4aaa865fd0f907a67179e7ee967f23a9827b0026
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922461"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`OnTraceInfoFunc` 형식 정의는 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 및 [RELOG_CALLBACKS](relog-callbacks-struct.md) 구조체에서 사용되는 함수 서명 중 하나입니다.

## <a name="syntax"></a>구문

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>매개 변수

*traceInfo*\
현재 분석 중이거나 다시 로깅 중인 추적 관련 정보를 포함하는 [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) 개체입니다.

*callbackContext*\
[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 또는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md)에서 이 콜백에 설정된 컨텍스트 값입니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 제어하는 [CALLBACK_CODE](callback-code-enum.md) 값입니다.

::: moniker-end
