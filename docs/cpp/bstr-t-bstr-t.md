---
description: '자세한 내용은 _bstr_t:: _bstr_t을 (를) 확인 하세요.'
title: _bstr_t::_bstr_t
ms.date: 02/02/2021
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.openlocfilehash: 0e6913a45b1c4d542e495bc59bc5871f533a1573
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522913"
---
# `_bstr_t::_bstr_t`

**Microsoft 전용**

`_bstr_t` 개체를 생성합니다.

## <a name="syntax"></a>구문

```cpp
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

### <a name="parameters"></a>매개 변수

*`s1`*\
복사할 `_bstr_t` 개체입니다.

*`s2`*\
멀티바이트 문자열입니다.

*`s3`*\
유니코드 문자열입니다.

*`var`*\
[_Variant_t](../cpp/variant-t-class.md) 개체입니다.

*`bstr`*\
기존 `BSTR` 개체입니다.

*`fCopy`*\
이면 **`false`** 를 *`bstr`* 호출 하 여 복사를 수행 하지 않고 새 개체에 인수를 연결 합니다 `SysAllocString` .

## <a name="remarks"></a>설명

`_bstr_t`클래스는 다음과 같은 몇 가지 생성자를 제공 합니다.

`_bstr_t( )`\
`_bstr_t`Null 개체를 캡슐화 하는 기본 개체를 생성 `BSTR` 합니다.

`_bstr_t( _bstr_t& s1 )`\
`_bstr_t` 개체를 다른 개체의 복사본으로 생성합니다. 이 생성자는 *단순* 복사를 수행 `BSTR` 합니다. 이렇게 하면 새 항목을 만드는 대신 캡슐화 된 개체의 참조 횟수가 증가 합니다.

`_bstr_t( char* s2 )`\
새 `_bstr_t` 개체를 만드는 `SysAllocString`을 호출하여 `BSTR` 개체를 생성한 다음 캡슐화합니다. 이 생성자는 먼저 멀티바이트를 유니코드로 변환합니다.

`_bstr_t( wchar_t* s3 )`\
새 `_bstr_t` 개체를 만드는 `SysAllocString`을 호출하여 `BSTR` 개체를 생성한 다음 캡슐화합니다.

`_bstr_t( _variant_t& var )`\
`_bstr_t` `_variant_t` 캡슐화 된 개체에서 개체를 먼저 검색 하 여 개체에서 개체를 생성 `BSTR` `VARIANT` 합니다.

`_bstr_t( BSTR bstr, bool fCopy )`\
기존 `_bstr_t`(`BSTR` 문자열의 반대)에서 `wchar_t*` 개체를 생성합니다. *`fCopy`* 가 이면 **`false`** 제공 된가를 사용 하 `BSTR` 여 새 복사본을 만들지 않고 새 개체에 연결 됩니다 `SysAllocString` . 이 생성자는 형식 라이브러리 헤더의 래퍼 함수에서 캡슐화 하 고 `BSTR` 인터페이스 메서드에서 반환 된의 소유권을 가져오는 데 사용 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`_bstr_t` 클래스](../cpp/bstr-t-class.md)\
[`_variant_t` 클래스](../cpp/variant-t-class.md)
