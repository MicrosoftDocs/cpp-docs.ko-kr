---
title: TEMPLATE_INSTANTIATION_DATA 구조체
description: C++ Build Insights SDK TEMPLATE_INSTANTIATION_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c92fbd8ee7e1fff702757d003ab3bbe0bdabd886
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923443"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA 구조체

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`TEMPLATE_INSTANTIATION_DATA` 구조체는 템플릿 인스턴스화를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `SpecializationSymbolKey` | 템플릿 특수화 유형에 대한 키입니다. 이 값은 분석 중인 추적 내에서 고유합니다. |
| `PrimaryTemplateSymbolKey` | 특수화된 기본 템플릿 유형에 대한 키입니다. 이 값은 분석 중인 추적 내에서 고유합니다. |
| `KindCode` | 템플릿 인스턴스화의 유형입니다. 자세한 내용은 [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)를 참조하세요. |

## <a name="remarks"></a>설명

`TEMPLATE_INSTANTIATION_DATA` 구조체의 키는 분석 중인 추적 내에서 고유합니다. 그러나 서로 다른 컴파일러 프런트 엔드 패스에서 들어오는 두 개의 키가 동일한 유형을 가리킬 수 있습니다. 여러 컴파일러 프런트 엔드 패스의 `TEMPLATE_INSTANTIATION_DATA` 정보를 사용하는 경우 [SYMBOL_NAME](../event-table.md#symbol-name) 이벤트를 사용하여 두 유형이 동일한지 확인합니다. 모든 템플릿 인스턴스화가 발생한 후에는 컴파일러 프런트 엔드 패스의 끝에 `SymbolName` 이벤트가 발생합니다.

::: moniker-end
