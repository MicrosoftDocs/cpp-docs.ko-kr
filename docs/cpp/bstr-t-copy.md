---
description: '자세한 정보: _bstr_t:: copy'
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 29ca965730dbcc22b4b725661ece68442d39aeba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229342"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 전용**

캡슐화된 `BSTR`의 복사본을 구성합니다.

## <a name="syntax"></a>구문

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>매개 변수

*fCopy*<br/>
이면 **`true`** **복사** 는 포함 된의 복사본을 반환 `BSTR` 하 고  , 그렇지 않으면 실제 BSTR을 반환 합니다.

## <a name="remarks"></a>설명

캡슐화된 `BSTR` 개체에 새로 할당된 복사본을 반환합니다.

## <a name="example"></a>예제

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_bstr_t 클래스](../cpp/bstr-t-class.md)
