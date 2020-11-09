---
title: Relog
description: C++ Build Insights SDK Relog 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 628f60042a10cf80c0b077d28387ed75466e925b
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922746"
---
# <a name="relog"></a>Relog

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`Relog` 함수는 ETW(Windows용 이벤트 추적)에서 MSVC 이벤트를 읽고 새롭게 수정된 ETW 추적에 쓰는 용도로 사용합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>매개 변수

*TAnalyzerGroupMembers*\
이 매개 변수는 항상 추론됩니다.

*TReloggerGroupMembers*\
이 매개 변수는 항상 추론됩니다.

*inputLogFile*\
이벤트를 읽을 입력 ETW 추적입니다.

*outputLogFile*\
새 이벤트를 쓸 파일입니다.

*numberOfAnalysisPasses*\
입력 추적에서 실행할 분석 패스의 수입니다. 추적은 제공된 분석기 그룹을 통해 분석 패스별로 한 번씩 전달됩니다.

*systemEventsRetentionFlags*\
다시 로깅된 추적에 유지할 시스템 ETW 이벤트를 지정하는 비트마스크입니다. 자세한 내용은 [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)를 참조하세요.

*analyzerGroup*\
다시 로깅 세션의 분석 단계에 사용하는 분석기 그룹입니다. [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)을 호출하여 분석기 그룹을 만듭니다. [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)에서 얻은 동적 분석기 그룹을 사용하려면 먼저 주소를 `MakeStaticAnalyzerGroup`으로 전달하여 정적 분석기 그룹 안에서 캡슐화해야 합니다.

*reloggerGroup*\
*outputLogFile* 에서 지정된 추적 파일에 이벤트를 다시 로깅하는 재로거 그룹입니다. [MakeStaticReloggerGroup](make-static-relogger-group.md)을 호출하여 재로거 그룹을 만드세요. [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)에서 얻은 동적 재로거 그룹을 사용하려면 먼저 해당 주소를 `MakeStaticReloggerGroup`에 전달하여 정적 재로거 그룹 안에서 캡슐화해야 합니다.

### <a name="return-value"></a>반환 값

[RESULT_CODE](../other-types/result-code-enum.md) 열거형의 결과 코드입니다.

### <a name="remark"></a>설명

입력 추적은 분석기 그룹에 *numberOfAnalysisPasses* 회 전달됩니다. 다시 로깅 패스에는 유사한 옵션이 없습니다. 추적은 모든 분석 패스가 완료된 후 재로거 그룹에 한 번만 전달됩니다.

재로거 클래스 내에서 CPU 샘플과 같은 시스템 이벤트의 다시 로깅은 지원되지 않습니다. *systemEventsRetentionFlags* 매개변수를 사용하여 출력 추적에 유지할 시스템 이벤트를 결정합니다.

::: moniker-end
