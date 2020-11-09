---
title: StopAndRelogTracingSessionA
description: C++ Build Insights SDK StopAndRelogTracingSessionA 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de69ca379c6f0ef46e23d2b4a78c72518e997572
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919971"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`StopAndRelogTracingSessionA` 함수는 진행 중인 추적 세션을 중지하고 결과 추적을 임시 파일에 저장합니다. 그러면 다시 로깅 세션이 임시 파일을 입력으로 사용하여 즉시 시작됩니다. 다시 로깅 세션에 의해 생성된 다시 로깅된 최종 추적은 호출자가 지정한 파일에 저장됩니다. 이 함수를 호출하는 실행 파일에는 관리자 권한이 있어야 합니다.

## <a name="syntax"></a>구문

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>매개 변수

*sessionName*\
중지할 추적 세션의 이름입니다. [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) 또는 [StartTracingSessionW](start-tracing-session-w.md)에 전달된 것과 동일한 세션 이름을 사용해야 합니다.

*outputLogFile*\
다시 로깅 세션에서 생성한 다시 로깅된 추적을 쓸 파일입니다.

*statistics*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) 개체에 대한 포인터입니다. `StopAndRelogTracingSessionA`는 반환하기 전에 이 개체에 추적 컬렉션 통계를 씁니다.

*analysisDescriptor*\
[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) 개체에 대한 포인터입니다. 이 개체를 사용하여 `StopAndRelogTracingSessionA`로 시작되는 다시 로깅 세션을 구성해야 합니다.

### <a name="return-value"></a>반환 값

[RESULT_CODE](../other-types/result-code-enum.md) 열거형의 결과 코드입니다.

::: moniker-end
