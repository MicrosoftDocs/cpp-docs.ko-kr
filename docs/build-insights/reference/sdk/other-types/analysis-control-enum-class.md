---
title: AnalysisControl 열거형 클래스
description: C++ Build Insights SDK AnalysisControl 열거형 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0f4887d626c5e80a0afaa393e255f8ffedbd6b1f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922620"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl 열거형 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`AnalysisControl` 열거형 클래스는 분석 또는 다시 로깅 세션의 흐름을 제어하는 데 사용됩니다. [IAnalyzer](ianalyzer-class.md) 또는 [IRelogger](irelogger-class.md) 멤버 함수에서 `AnalysisControl` 코드를 반환하여 다음에 수행할 작업을 제어합니다.

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `BLOCK` | 분석기 또는 재로거 그룹에서 현재 이벤트가 더 이상 전파되지 않도록 합니다. |
| `CANCEL` | 현재 분석 또는 다시 로깅 세션을 취소합니다. |
| `CONTINUE` | 현재 분석 또는 다시 로깅 세션을 정상적으로 계속합니다. 현재 이벤트를 다음 분석기 또는 재로거 그룹 멤버로 전파합니다. |
| `FAILURE` | 현재 분석 또는 다시 로깅 세션을 취소하고 오류를 표시합니다. |

::: moniker-end
