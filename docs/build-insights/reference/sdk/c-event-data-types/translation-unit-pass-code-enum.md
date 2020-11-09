---
title: TRANSLATION_UNIT_PASS_CODE 열거형
description: C++ Build Insights SDK TRANSLATION_UNIT_PASS_CODE 열거형 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 31f3e16ce6d9aa8c3c9db6cf9c11069dc3ec22fe
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920920"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE 열거형

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`TRANSLATION_UNIT_PASS_CODE` 열거형입니다.

## <a name="members"></a>멤버

| Name | 값 | Description |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | 소스 코드를 구문 분석하고 중간 언어로 변환하는 역할을 담당하는 프런트 엔드 패스입니다. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | 중간 언어를 최적화하고 기계어 코드로 변환하는 역할을 담당하는 백엔드 패스입니다. |

## <a name="remarks"></a>설명

C SDK 함수에서 사용합니다.

::: moniker-end
