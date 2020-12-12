---
description: '자세한 정보: _bstr_t:: operator ='
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 78447048a45567df603acf3af0bc51cefbdb187d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308785"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Microsoft 전용**

기존 `_bstr_t` 개체에 새 값을 할당합니다.

## <a name="syntax"></a>구문

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>매개 변수

*s1*<br/>
기존 `_bstr_t` 개체에 할당될 `_bstr_t` 개체입니다.

*s2'*<br/>
기존 `_bstr_t` 개체에 할당될 멀티바이트 문자열입니다.

*s3*<br/>
기존 `_bstr_t` 개체에 할당될 유니코드 문자열입니다.

*var*<br/>
기존 `_variant_t` 개체에 할당될 `_bstr_t` 개체입니다.

**Microsoft 전용 종료**

## <a name="example"></a>예제

**Operator =** 를 사용 하는 예제는 [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) 을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[_bstr_t 클래스](../cpp/bstr-t-class.md)
