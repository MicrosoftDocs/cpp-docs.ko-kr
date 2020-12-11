---
description: '자세한 정보: _variant_t:: operator ='
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: a304f0904f697ade7d04c6d12f375571a156e989
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161470"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Microsoft 전용**

## <a name="syntax"></a>구문

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>설명

다음 연산자는 `_variant_t` 개체에 새 값을 할당합니다.

- **operator = (**  *varsrc*  **)** `VARIANT` 개체에 기존을 할당 `_variant_t` 합니다.

- **operator = (**  *pvarsrc*  **)** `VARIANT` 개체에 기존을 할당 `_variant_t` 합니다.

- **연산자 = (**  *var_t_Src*  **)** 기존 `_variant_t` 개체를 개체에 할당 `_variant_t` 합니다.

- **연산자 = (**  *sSrc*  **)** **`short`** 개체에 정수 값을 할당 `_variant_t` 합니다.

- **operator = (** `lSrc` **)** **`long`** 개체에 정수 값을 할당 `_variant_t` 합니다.    

- **연산자 = (**  *fltSrc*  **)** **`float`** 개체에 숫자 값을 할당 `_variant_t` 합니다.

- **연산자 = (**  *dblSrc*  **)** **`double`** 개체에 숫자 값을 할당 `_variant_t` 합니다.

- **operator = (**  *cysrc*  **)** 개체 `CY` 에 개체를 할당 `_variant_t` 합니다.

- **연산자 = (**  *bstrSrc*  **)** 개체 `BSTR` 에 개체를 할당 `_variant_t` 합니다.

- **연산자 = (**  *wstrSrc*  **)** 개체에 유니코드 문자열을 할당 `_variant_t` 합니다.

- **operator = (** `strSrc` **)** 개체에 멀티 바이트 문자열을 할당 `_variant_t` 합니다.    

- **operator = (** `bSrc` **)** **`bool`** 개체에 값을 할당 `_variant_t` 합니다.  

- **연산자 = (**  *pDispSrc*  **)** 개체 `VT_DISPATCH` 에 개체를 할당 `_variant_t` 합니다.

- **연산자 = (**  *pIUnknownSrc*  **)** 개체 `VT_UNKNOWN` 에 개체를 할당 `_variant_t` 합니다.

- **operator = (**  *src*  **)** `DECIMAL` 개체에 값을 할당 `_variant_t` 합니다.

- **operator = (** `bSrc` **)** `BYTE` 개체에 값을 할당 `_variant_t` 합니다.  

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
