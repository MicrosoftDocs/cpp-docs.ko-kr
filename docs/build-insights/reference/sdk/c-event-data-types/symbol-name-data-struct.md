---
title: SYMBOL_NAME_DATA 구조체
description: C++ Build Insights SDK SYMBOL_NAME_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d234c6c225eff87a0eecd98fa5ff60bf92db97f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041915"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`SYMBOL_NAME_DATA` 구조체는 컴파일러 프런트 엔드 기호를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `Key` | 기호의 키입니다. 이 값은 분석 중인 추적 내에서 고유합니다. |
| `Name` | 기호의 이름입니다. |

## <a name="remarks"></a>설명

서로 다른 두 컴파일러 프런트 엔드 패스에서 들어오는 기호는 이름이 같지만 키는 다를 수 있습니다. 이 경우 기호 이름을 사용하여 두 형식이 동일한지 확인합니다.

::: moniker-end
