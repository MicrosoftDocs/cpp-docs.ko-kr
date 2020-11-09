---
title: 분석
description: C++ Build Insights SDK Analyze 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5e593b690231adf6f04161f9c3ff6aef3217f9ef
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920322"
---
# <a name="analyze"></a>분석

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`Analyze` 함수는 C++ Build를 추적하는 동안 MSVC에서 얻은 ETW(Windows용 이벤트 추적)를 분석하는 용도로 사용합니다. ETW 추적의 이벤트는 호출자가 제공한 분석기 그룹에 순차적으로 전달됩니다. 이 함수는 이벤트 스트림을 분석기 그룹에 연속으로 수 차례 전달할 수 있는 멀티 패스 분석을 지원합니다.

## <a name="syntax"></a>구문

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>매개 변수

*TAnalyzerGroupMembers*\
이 매개 변수는 항상 추론됩니다.

*inputLogFile*\
이벤트를 읽을 입력 ETW 추적입니다.

*numberOfPasses*\
입력 추적에서 실행할 분석 패스의 수입니다. 추적은 제공된 분석기 그룹을 통해 분석 패스별로 한 번씩 전달됩니다.

*analyzerGroup*\
분석에 사용하는 분석기 그룹입니다. [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)을 호출하여 분석기 그룹을 만듭니다. [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)에서 얻은 동적 분석기 그룹을 사용하려면 먼저 주소를 `MakeStaticAnalyzerGroup`으로 전달하여 정적 분석기 그룹 안에서 캡슐화해야 합니다.

### <a name="return-value"></a>반환 값

[RESULT_CODE](../other-types/result-code-enum.md) 열거형의 결과 코드입니다.

::: moniker-end
