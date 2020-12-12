---
description: '다음에 대 한 자세한 정보: _bstr_t 관계형 연산자'
title: _bstr_t 관계형 연산자
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: 3d34c83d9547bb9d52e43174cac2acd259717e76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308694"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t 관계형 연산자

**Microsoft 전용**

두 개의 `_bstr_t` 개체를 비교합니다.

## <a name="syntax"></a>구문

```
bool operator!( ) const throw( );
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

[_bstr_t 클래스](../cpp/bstr-t-class.md)
