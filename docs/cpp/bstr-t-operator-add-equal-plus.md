---
description: '자세한 정보: _bstr_t:: operator + =, _bstr_t:: operator +'
title: '_bstr_t:: operator + =, _bstr_t:: operator +'
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.openlocfilehash: 44a525891ee072ea797026bd022ecae7b62fd6d1
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522523"
---
# <a name="_bstr_toperator--_bstr_toperator-"></a>`_bstr_t::operator +=`, `_bstr_t::operator +`

**Microsoft 전용**

개체의 끝에 문자를 추가 `_bstr_t` 하거나 두 문자열을 연결 합니다.

## <a name="syntax"></a>구문

```cpp
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

### <a name="parameters"></a>매개 변수

*`s1`*\
`_bstr_t` 개체입니다.

*`s2`*\
멀티바이트 문자열입니다.

*`s3`*\
유니코드 문자열입니다.

## <a name="remarks"></a>설명

이러한 연산자는 다음과 같이 문자열 연결을 수행합니다.

- `operator+=( s1 )` 의 캡슐화 된의 문자를 `BSTR` *`s1`* 이 개체의 캡슐화 된 끝에 추가 합니다 `BSTR` .

- `operator+( s1 )``_bstr_t`이 개체의 및의 개체를 연결 하 여 구성 된 새을 반환 합니다 `BSTR` *`s1`* .

- `operator+( s2, s1 )``_bstr_t`유니코드로 변환 된 멀티 바이트 문자열을 연결 하 여 구성 된 새을 반환 하 *`s2`* 고 `BSTR` 에서 캡슐화 합니다 *`s1`* .

- `operator+( s3, s1 )``_bstr_t`유니코드 문자열과 *`s3`* 에 캡슐화 된를 연결 하 여 형성 된 새를 반환 합니다 `BSTR` *`s1`* .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)
