---
title: StopTracingSessionA
description: C++ Build Insights SDK StopTracingSessionA 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 211538c1756d41b91dab6d43f33f4b4a41ceb70c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922643"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`StopTracingSessionA` 함수는 진행 중인 추적 세션을 중지하고 원시 추적 파일을 생성합니다. 원시 추적 파일을 [Analyze](analyze.md), [AnalzeA](analyze-a.md), [AnalyzeW](analyze-w.md) 함수에 전달하여 분석 세션을 시작할 수 있습니다. 원시 추적 파일을 [Relog](relog.md), [RelogA](relog-a.md), [RelogW](relog-w.md) 함수에 전달하여 다시 로깅 세션을 시작할 수도 있습니다. `StopTracingSessionA`를 호출하는 실행 파일에는 관리자 권한이 있어야 합니다.

## <a name="syntax"></a>구문

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>매개 변수

*sessionName*\
중지할 추적 세션의 이름입니다. [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) 또는 [StartTracingSessionW](start-tracing-session-w.md)에 전달된 것과 동일한 세션 이름을 사용해야 합니다.

*outputLogFile*\
원시 추적을 저장해야 하는 최종 출력 로그 파일의 경로입니다.

*statistics*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) 개체에 대한 포인터입니다. `StopTracingSessionA`는 반환하기 전에 이 개체에 추적 컬렉션 통계를 씁니다.

### <a name="return-value"></a>반환 값

[RESULT_CODE](../other-types/result-code-enum.md) 열거형의 결과 코드입니다.

::: moniker-end
