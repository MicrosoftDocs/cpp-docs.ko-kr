---
description: '자세한 정보: _variant_t:: SetString'
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: a36bab9189b6046325bb275469dc9dbdb495fc7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161418"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft 전용**

이 `_variant_t` 개체에 문자열을 할당합니다.

## <a name="syntax"></a>구문

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>매개 변수

*.Psrc*<br/>
문자열에 대한 포인터입니다.

## <a name="remarks"></a>설명

ANSI 문자열을 유니코드 `BSTR` 문자열로 변환하고 이 `_variant_t` 개체에 할당합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
