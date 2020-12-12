---
description: '자세히 알아보기: _variant_t::'
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 32ce43f1d9afb388c97e5271927113c71d31bb92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116628"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft 전용**

개체의 형식을 `_variant_t` 지정 된로 변경 합니다 `VARTYPE` .

## <a name="syntax"></a>구문

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>매개 변수

*vartype*<br/>
`VARTYPE`이 개체에 대 한 `_variant_t` 입니다.

*.Psrc*<br/>
변환할 `_variant_t` 개체의 포인터입니다. 이 값이 NULL 이면 변환이 대신 수행 됩니다.

## <a name="remarks"></a>설명

이 멤버 함수는 `_variant_t` 개체를 지정 된으로 변환 `VARTYPE` 합니다. *Psrc* 가 NULL 이면 변환이 구현 된 것이 고, 그렇지 않으면이 `_variant_t` 개체가 *psrc* 에서 복사 된 후 변환 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
