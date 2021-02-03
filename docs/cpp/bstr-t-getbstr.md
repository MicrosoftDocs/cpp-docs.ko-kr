---
description: '자세한 정보: _bstr_t:: GetBSTR'
title: _bstr_t::GetBSTR
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.openlocfilehash: b48dd082b21c0f3416c8b58b8ae2669c74d9d227
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522757"
---
# `_bstr_t::GetBSTR`

**Microsoft 전용**

`BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분을 가리킵니다.

## <a name="syntax"></a>구문

```cpp
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Return Value

`BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분입니다.

## <a name="remarks"></a>설명

**`GetBSTR`**`_bstr_t`는를 공유 하는 모든 개체에 영향을 줍니다 `BSTR` . 두 개 이상의은 `_bstr_t` `BSTR` 복사 생성자와을 사용 하 여를 공유할 수 있습니다 `operator=` .

## <a name="example"></a>예제

을 [`_bstr_t::Assign`](../cpp/bstr-t-assign.md) 사용 하는 예제는를 참조 하세요 **`GetBSTR`** .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)