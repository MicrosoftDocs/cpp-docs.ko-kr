---
description: '자세한 정보: _bstr_t:: GetAddress'
title: _bstr_t::GetAddress
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.openlocfilehash: 23013a6666b8e268a6437532b69050933ffe6b42
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522835"
---
# `_bstr_t::GetAddress`

**Microsoft 전용**

기존 문자열을 해제하고 새로 할당된 문자열의 주소를 반환합니다.

## <a name="syntax"></a>구문

```cpp
BSTR* GetAddress( );
```

## <a name="return-value"></a>Return Value

`BSTR`로 래핑되는 `_bstr_t`에 대한 포인터입니다.

## <a name="remarks"></a>설명

**`GetAddress`**`_bstr_t`는를 공유 하는 모든 개체에 영향을 줍니다 `BSTR` . 두 개 이상의은 `_bstr_t` `BSTR` 복사 생성자와을 사용 하 여를 공유할 수 있습니다 **`operator=`** .

## <a name="example"></a>예제

을 [`_bstr_t::Assign`](../cpp/bstr-t-assign.md) 사용 하는 예제는를 참조 하세요 **`GetAddress`** .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)