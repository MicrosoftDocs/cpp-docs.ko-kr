---
description: '자세한 정보: _bstr_t:: Attach'
title: _bstr_t::Attach
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.openlocfilehash: 02717fad98e4d68dde70995abcfad4cb55b8c45c
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522887"
---
# `_bstr_t::Attach`

**Microsoft 전용**

`_bstr_t` 래퍼를 `BSTR`에 연결합니다.

## <a name="syntax"></a>구문

```cpp
void Attach(
   BSTR s
);
```

### <a name="parameters"></a>매개 변수

*`s`*\
`BSTR` 변수와 연결되거나 이 변수에 할당될 `_bstr_t`입니다.

## <a name="remarks"></a>설명

이전에 `_bstr_t`가 다른 `BSTR`에 연결된 경우 다른 `_bstr_t` 변수가 `BSTR`을 사용하고 있지 않으면 `_bstr_t`가 `BSTR` 리소스를 정리합니다.

## <a name="example"></a>예제

을 [`_bstr_t::Assign`](../cpp/bstr-t-assign.md) 사용 하는 예제는를 참조 하세요 **`Attach`** .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
