---
description: '자세한 정보: _variant_t:: Attach'
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: de13b1e8138eb24971e52165ee84fc92d97ca3d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116654"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft 전용**

개체를 `VARIANT` **_variant_t** 개체에 연결 합니다.

## <a name="syntax"></a>구문

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>매개 변수

*varSrc*<br/>
`VARIANT`이 **_variant_t** 개체에 연결할 개체입니다.

## <a name="remarks"></a>설명

를 캡슐화 하 여의 소유권을 가져옵니다 `VARIANT` . 이 멤버 함수는 캡슐화 된 모든 기존를 해제 `VARIANT` 한 다음 제공 된를 복사 하 `VARIANT` 고를 VT_EMPTY 설정 하 여 `VARTYPE` **_variant_t** 소멸자만 리소스를 해제할 수 있도록 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
