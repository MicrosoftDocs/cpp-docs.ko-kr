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
ms.openlocfilehash: ec54c560dd408dc3beecbc20eaac69d389c7ec37
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041561"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

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
