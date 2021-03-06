---
title: INVOCATION_VERSION_DATA 구조체
description: C++ Build Insights SDK INVOCATION_VERSION_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ebed659ade4610b50ae06f2a32851522073a58d8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923553"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`INVOCATION_VERSION_DATA` 구조체는 버전 번호를 정수 계열 값 그룹으로 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `VersionMajor` | 버전의 주 번호입니다. |
| `VersionMinor` | 버전의 부 번호입니다. |
| `BuildNumberMajor` | 빌드의 주 번호입니다. |
| `BuildNumberMinor` | 빌드의 부 번호입니다. |

::: moniker-end
