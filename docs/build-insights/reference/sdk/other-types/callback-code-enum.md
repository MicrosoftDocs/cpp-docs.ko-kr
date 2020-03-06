---
title: CALLBACK_CODE 열거형
description: C++ BUILD Insights SDK CALLBACK_CODE 열거형 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334093"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE 열거형

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK는 Visual Studio 2017 이상 버전과 호환 됩니다. 이러한 버전에 대 한 설명서를 보려면이 문서에 대 한 Visual Studio 버전 선택기 컨트롤을 Visual Studio 2017 또는 Visual studio 2019로 설정 합니다.

::: moniker-end
::: moniker range=">=vs-2017"

`CALLBACK_CODE` 열거형은 분석 또는 다시 로깅 세션의 흐름을 제어 하는 데 사용 됩니다. [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 또는 [RELOG_CALLBACKS](relog-callbacks-struct.md) 의 함수에서 CALLBACK_CODE 값을 반환 하 여 다음에 수행 해야 하는 작업을 제어 합니다.

## <a name="members"></a>멤버

| 이름 | 값 | 설명 |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 현재 분석을 계속 하거나 세션을 다시 기록 합니다. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | 현재 분석 또는 다시 로깅 세션을 취소 하 고 오류를 알립니다. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | 현재 분석 또는 다시 로깅 세션을 취소 합니다. |

::: moniker-end
