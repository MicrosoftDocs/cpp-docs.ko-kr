---
description: 자세한 내용은 _variant_t 추출기을 (를) 확인 하세요.
title: _variant_t Extractors
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: 55a02fdf422388b0e44a9aad77e86f7a76e80e3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161600"
---
# <a name="_variant_t-extractors"></a>_variant_t Extractors

**Microsoft 전용**

캡슐화 된 개체에서 데이터를 추출 `VARIANT` 합니다.

## <a name="syntax"></a>구문

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>설명

캡슐화 된에서 원시 데이터를 추출 `VARIANT` 합니다. 가 `VARIANT` 아직 적절 한 형식이 아닌 경우를 사용 하 여 변환을 시도 하면 오류가 발생 하면 `VariantChangeType` 오류가 생성 됩니다.

- **연산자 short ()** **`short`** 정수 값을 추출 합니다.

- **연산자 long ()** **`long`** 정수 값을 추출 합니다.

- **operator float ()** **`float`** 숫자 값을 추출 합니다.

- **operator double ()** **`double`** 정수 값을 추출 합니다.

- **연산자 CY ()** 개체를 추출 `CY` 합니다.

- **연산자 bool ()** 값을 추출 **`bool`** 합니다.

- **연산자 DECIMAL ()** 값을 추출 `DECIMAL` 합니다.

- **연산자 BYTE ()** 값을 추출 `BYTE` 합니다.

- **연산자 _bstr_t ()** 개체에 캡슐화 된 문자열을 추출 `_bstr_t` 합니다.

- **Operator IDispatch \* ()** 는 캡슐화 된에서 포인터를 추출 `VARIANT` 합니다. `AddRef` 결과 포인터에서가 호출 되므로 사용자는를 사용 하 여 사용자가 호출 하는 것이 좋습니다 `Release` .

- **연산자 IUnknown \* ()** 은 캡슐화 된에서 COM 인터페이스 포인터를 추출 `VARIANT` 합니다. `AddRef` 결과 포인터에서가 호출 되므로 사용자는를 사용 하 여 사용자가 호출 하는 것이 좋습니다 `Release` .

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
