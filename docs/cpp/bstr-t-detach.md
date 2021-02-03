---
description: _Bstr_t::D etach에 대해 자세히 알아보세요.
title: _bstr_t::Detach
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.openlocfilehash: bc269f46d3a393485e95a62df23692c60070d75a
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522848"
---
# `_bstr_t::Detach`

**Microsoft 전용**

`BSTR`로 래핑된 `_bstr_t`을 반환하고 `BSTR`을 `_bstr_t`에서 분리합니다.

## <a name="syntax"></a>구문

```cpp
BSTR Detach( ) throw;
```

## <a name="return-value"></a>Return Value

에 의해 캡슐화 된을 반환 합니다 `BSTR` `_bstr_t` .

## <a name="example"></a>예제

을 [`_bstr_t::Assign`](../cpp/bstr-t-assign.md) 사용 하는 예제는를 참조 하세요 **`Detach`** .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
