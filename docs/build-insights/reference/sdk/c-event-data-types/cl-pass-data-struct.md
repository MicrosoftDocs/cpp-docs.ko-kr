---
title: CL_PASS_DATA 구조체
description: C++ Build Insights SDK CL_PASS_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 52ee5fdaae12784c2f59d2c47ac9a2fd80649f27
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040537"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`CL_PASS_DATA` 구조체는 컴파일 패스를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `TranslationUnitPassCode` | 실행되는 컴파일 패스를 식별하는 코드입니다. 자세한 내용은 [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md)를 참조하세요. |
| `InputSourcePath` | 이 컴파일 패스가 실행되는 C 또는 C++ 소스 파일입니다. |
| `OutputObjectPath` | 컴파일러에서 생성되는 개체 파일입니다. |

::: moniker-end
