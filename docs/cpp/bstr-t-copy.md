---
description: '자세한 정보: _bstr_t:: copy'
title: _bstr_t::copy
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.openlocfilehash: 98726e0c3100851d1496e532310ece2209d71ae0
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522861"
---
# `_bstr_t::copy`

**Microsoft 전용**

캡슐화된 `BSTR`의 복사본을 구성합니다.

## <a name="syntax"></a>구문

```cpp
BSTR copy( bool fCopy = true ) const;
```

### <a name="parameters"></a>매개 변수

*`fCopy`*\
인 **`true`** 경우 **`copy`** 포함 된의 복사본을 반환 `BSTR` 하 고, 그렇지 않으면 **`copy`** 실제를 반환 합니다 `BSTR` .

## <a name="remarks"></a>설명

매개 변수에 따라 캡슐화 된 개체 또는 캡슐화 된 개체의 새로 할당 된 복사본을 반환 합니다 `BSTR` .

## <a name="example"></a>예제

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
