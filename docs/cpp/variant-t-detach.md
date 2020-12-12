---
description: _Variant_t::D etach에 대해 자세히 알아보세요.
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 502903f73f9b149a5f85a6eb1be44687aab20664
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204695"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 전용**

캡슐화 된 `VARIANT` 개체를이 개체에서 분리 `_variant_t` 합니다.

## <a name="syntax"></a>구문

```
VARIANT Detach( );
```

## <a name="return-value"></a>Return Value

캡슐화 된 `VARIANT` 입니다.

## <a name="remarks"></a>설명

캡슐화 된를 추출 하 여 반환한 `VARIANT` 다음이 `_variant_t` 개체를 삭제 하지 않고 지웁니다. 이 멤버 함수는 `VARIANT` 캡슐화에서을 제거 하 고 `VARTYPE` 이 개체의를 VT_EMPTY 설정 합니다 `_variant_t` . VariantClear 함수를 호출 하 여 반환 된를 해제할 수 있습니다 `VARIANT` . [](/windows/win32/api/oleauto/nf-oleauto-variantclear)

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
