---
title: INVOCATION_DATA 구조체
description: C++ Build Insights SDK INVOCATION_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 48b4c28d3c01d61a31343894312a54ba2ab17a70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041642"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA` 구조체는 컴파일러 또는 링커 호출을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `MSVCToolCode` | 호출의 유형을 식별하는 코드입니다. 자세한 내용은 [MSVC_TOOL_CODE](msvc-tool-code-enum.md)를 참조하세요. |
| `ToolVersion` | 호출된 도구의 버전을 정수 계열 값 그룹으로 저장하는 개체입니다. |
| `ToolVersionString` | 호출된 도구의 버전을 텍스트 형식으로 설명합니다. |
| `WorkingDirectory` | 호출이 생성된 디렉터리입니다. |
| `ToolPath` | 호출된 도구의 절대 경로입니다. |

::: moniker-end
