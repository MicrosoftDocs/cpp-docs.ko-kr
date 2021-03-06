---
title: CALLBACK_CODE 열거형
description: C++ Build Insights SDK CALLBACK_CODE 열거형 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146d191d0b642ad538f5a314016b41fdbdf26113
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922590"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE 열거형

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`CALLBACK_CODE` 열거형은 분석 또는 다시 로깅 세션의 흐름을 제어하는 데 사용합니다. [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 또는 [RELOG_CALLBACKS](relog-callbacks-struct.md)의 함수에서 CALLBACK_CODE 값을 반환하여 다음에 해야 하는 작업을 제어합니다.

## <a name="members"></a>멤버

| Name | 값 | Description |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 현재 분석 또는 다시 로깅 세션을 정상적으로 계속합니다. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | 현재 분석 또는 다시 로깅 세션을 취소하고 오류를 표시합니다. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | 현재 분석 또는 다시 로깅 세션을 취소합니다. |

::: moniker-end
