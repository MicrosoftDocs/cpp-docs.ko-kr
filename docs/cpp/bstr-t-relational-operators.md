---
description: '다음에 대 한 자세한 정보: _bstr_t 관계형 연산자'
title: _bstr_t 관계형 연산자
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
helpviewer_keywords:
- _bstr_t relational operators[C++]
ms.openlocfilehash: eef66f8165fc1dfbb29730507ee8d3b996800b7b
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522588"
---
# <a name="_bstr_t-relational-operators"></a>`_bstr_t` 관계형 연산자

**Microsoft 전용**

두 개의 `_bstr_t` 개체를 비교합니다.

## <a name="syntax"></a>구문

```cpp
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>설명

이러한 연산자는 두 `_bstr_t` 개체를 사전순으로 비교합니다. 연산자는 **`true`** 비교가 유지 되 면를 반환 하 고, 그렇지 않으면를 반환 **`false`** 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
