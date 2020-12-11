---
description: '자세한 내용은 _variant_t:: _variant_t을 (를) 확인 하세요.'
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: e49f2cf42ce1d73cb18d280d335ed267cb11df3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161366"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Microsoft 전용**

`_variant_t` 개체를 생성합니다.

## <a name="syntax"></a>구문

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>매개 변수

*varSrc*<br/>
새 `VARIANT` 개체로 복사할 `_variant_t` 개체입니다.

*pVarSrc*<br/>
`VARIANT`새 개체로 복사할 개체에 대 한 포인터 `_variant_t` 입니다.

*var_t_Src*<br/>
새 `_variant_t` 개체로 복사할 `_variant_t` 개체입니다.

*fCopy*<br/>
인 경우 **`false`** 제공 된 `VARIANT` 개체는를 사용 하 `_variant_t` 여 새 복사본을 만들지 않고 새 개체에 연결 됩니다 `VariantCopy` .

*ISrc, sSrc*<br/>
새 `_variant_t` 개체로 복사할 정수 값입니다.

*vtSrc*<br/>
`VARTYPE`새 개체에 대 한 `_variant_t` 입니다.

*fltSrc, dblSrc*<br/>
새 `_variant_t` 개체에 복사될 숫자 값입니다.

*cySrc*<br/>
새 `CY` 개체로 복사할 `_variant_t` 개체입니다.

*bstrSrc*<br/>
새 `_bstr_t` 개체로 복사할 `_variant_t` 개체입니다.

*strSrc, wstrSrc*<br/>
새 `_variant_t` 개체로 복사할 문자열입니다.

*bSrc*<br/>
**`bool`** 새 개체에 복사할 값 `_variant_t` 입니다.

*pIUknownSrc*<br/>
새 개체로 캡슐화 될 VT_UNKNOWN 개체에 대 한 COM 인터페이스 포인터 `_variant_t` 입니다.

*pDispSrc*<br/>
새 개체로 캡슐화 될 VT_DISPATCH 개체에 대 한 COM 인터페이스 포인터 `_variant_t` 입니다.

*원본 없음*<br/>
새 `DECIMAL` 개체로 복사할 `_variant_t` 값입니다.

*bSrc*<br/>
새 `BYTE` 개체로 복사할 `_variant_t` 값입니다.

*cSrc*<br/>
**`char`** 새 개체에 복사할 값 `_variant_t` 입니다.

*usSrc*<br/>
**`unsigned short`** 새 개체에 복사할 값 `_variant_t` 입니다.

*ulSrc*<br/>
**`unsigned long`** 새 개체에 복사할 값 `_variant_t` 입니다.

*iSrc*<br/>
**`int`** 새 개체로 복사할 값 `_variant_t` 입니다.

*uiSrc*<br/>
**`unsigned int`** 새 개체로 복사할 값 `_variant_t` 입니다.

*i8Src*<br/>
**`__int64`** 새 개체로 복사할 값 `_variant_t` 입니다.

*ui8Src*<br/>
새 개체에 복사할 **부호 없는 __int64** 값 `_variant_t` 입니다.

## <a name="remarks"></a>설명

- **_variant_t ()** 빈 `_variant_t` 개체를 생성 `VT_EMPTY` 합니다.

- **_variant_t (variant&** *varsrc***)** `_variant_t`개체의 복사본에서 개체를 생성 `VARIANT` 합니다.     변형 형식이 유지됩니다.

- **_variant_t (variant** <strong>\*</strong> *pvarsrc***)** 는 `_variant_t` 개체의 복사본에서 개체를 생성 `VARIANT` 합니다.     변형 형식이 유지됩니다.

- **_variant_t (_variant_t&** *var_t_Src***)** `_variant_t`다른 개체에서 개체를 생성 `_variant_t` 합니다.     변형 형식이 유지됩니다.

- **_variant_t (variant&** *varsrc* **, bool** `fCopy` **)** 는 `_variant_t` 기존 개체에서 개체를 생성 `VARIANT` 합니다.       *Fcopy* 가 인 경우 **`false`** **VARIANT** 개체는 복사를 만들지 않고 새 개체에 연결 됩니다.

- **_variant_t (short***sSrc* **, VARTYPE** `vtSrc` **= VT_I2)** 는 `_variant_t` VT_I2 형식의 개체 또는 정수 값에서 VT_BOOL를 생성 **`short`** 합니다.       다른 모든 `VARTYPE` E_INVALIDARG 오류가 발생 합니다.

- **_variant_t (long** `lSrc` **, VARTYPE** `vtSrc` **= VT_I4)** 는 `_variant_t` 정수 값에서 VT_I4, VT_BOOL 또는 VT_ERROR 형식의 개체를 생성 **`long`** 합니다.       다른 모든 `VARTYPE` E_INVALIDARG 오류가 발생 합니다.

- **_variant_t (float** `fltSrc` **)** 는 `_variant_t` 숫자 값에서 VT_R4 형식의 개체를 생성 **`float`** 합니다.    

- **_variant_t (double** `dblSrc` **, VARTYPE** `vtSrc` **= VT_R8)** 는 `_variant_t` VT_R8 형식의 개체 또는 숫자 값에서 VT_DATE를 생성 **`double`** 합니다.       다른 모든 `VARTYPE` E_INVALIDARG 오류가 발생 합니다.

- **CY&(_variant_t** `cySrc` **)** 는 `_variant_t` 개체에서 VT_CY 형식의 개체를 생성 `CY` 합니다.    

- **_variant_t (_bstr_t&** `bstrSrc` **)** 는 `_variant_t` 개체에서 VT_BSTR 형식의 개체를 생성 `_bstr_t` 합니다.     새 `BSTR`이 할당됩니다.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** 는 `_variant_t` 유니코드 문자열에서 VT_BSTR 형식의 개체를 생성 합니다. 새 `BSTR`이 할당됩니다.

- **_variant_t (char** <strong>\*</strong> `strSrc` **)** 는 `_variant_t` 문자열에서 VT_BSTR 형식의 개체를 생성 합니다.     새 `BSTR`이 할당됩니다.

- **_variant_t (bool** `bSrc` **)** `_variant_t` 값에서 VT_BOOL 형식의 개체를 생성 **`bool`** 합니다.    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **, bool** `fAddRef` **= true)** `_variant_t`COM 인터페이스 포인터에서 VT_UNKNOWN 형식의 개체를 생성 합니다.       `fAddRef`가 이면 **`true`** 제공 된 `AddRef` 인터페이스 포인터에 대해를 호출 하 여 `Release` 개체가 제거 될 때 발생 하는에 대 한 호출과 일치 시킵니다 `_variant_t` . `Release`제공 된 인터페이스 포인터에서를 호출 해야 합니다. `fAddRef`가 이면 **`false`** 이 생성자는 제공 된 인터페이스 포인터의 소유권을 갖습니다. `Release` 제공 된 인터페이스 포인터에서를 호출 하지 마세요.

- **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **, bool** `fAddRef` **= true)** `_variant_t`COM 인터페이스 포인터에서 VT_DISPATCH 형식의 개체를 생성 합니다.       `fAddRef`가 이면 **`true`** 제공 된 `AddRef` 인터페이스 포인터에 대해를 호출 하 여 `Release` 개체가 제거 될 때 발생 하는에 대 한 호출과 일치 시킵니다 `_variant_t` . `Release`제공 된 인터페이스 포인터에서를 호출 해야 합니다. `fAddRef`가 이면 **`false`** 이 생성자는 제공 된 인터페이스 포인터의 소유권을 갖습니다. `Release` 제공 된 인터페이스 포인터에서를 호출 하지 마세요.

- **_variant_t (DECIMAL&** `decSrc` **)** `_variant_t` 값에서 VT_DECIMAL 형식의 개체를 생성 `DECIMAL` 합니다.    

- **_variant_t (BYTE** `bSrc` **)** 는 `_variant_t` 값에서 형식의 개체를 생성 `VT_UI1` `BYTE` 합니다.    

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
