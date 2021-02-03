---
description: '자세한 정보: _bstr_t:: wchar_t *, _bstr_t:: char*'
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.openlocfilehash: b2e98ea4b62d4a2e346b552d31d66d23f301817c
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522549"
---
# <a name="_bstr_twchar_t-_bstr_tchar"></a>`_bstr_t::wchar_t*`, `_bstr_t::char*`

**Microsoft 전용**

문자를 `BSTR` 반각 또는 와이드 문자 배열로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>설명

이러한 연산자를 사용 하 여 개체에 의해 캡슐화 되는 문자 데이터를 추출할 수 있습니다 `BSTR` . 반환 된 포인터에 새 값을 할당 하면 원래 데이터가 수정 되지 않습니다 `BSTR` .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
