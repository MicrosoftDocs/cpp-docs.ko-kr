---
description: '자세한 정보: _bstr_t:: operator ='
title: _bstr_t::operator =
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.openlocfilehash: d021ba013190ddee262b8644e16876401be846dc
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522718"
---
# `_bstr_t::operator =`

**Microsoft 전용**

기존 `_bstr_t` 개체에 새 값을 할당합니다.

## <a name="syntax"></a>구문

```cpp
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

### <a name="parameters"></a>매개 변수

*`s1`*\
기존 `_bstr_t` 개체에 할당될 `_bstr_t` 개체입니다.

*`s2`*\
기존 `_bstr_t` 개체에 할당될 멀티바이트 문자열입니다.

*`s3`*\
기존 `_bstr_t` 개체에 할당될 유니코드 문자열입니다.

*`var`*\
기존 `_variant_t` 개체에 할당될 `_bstr_t` 개체입니다.

**Microsoft 전용 종료**

## <a name="example"></a>예제

을 [`_bstr_t::Assign`](../cpp/bstr-t-assign.md) 사용 하는 예제는를 참조 하세요 **`operator=`** .

## <a name="see-also"></a>참고 항목

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
