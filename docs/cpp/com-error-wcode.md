---
description: '자세한 내용은 _com_error:: WCode를 확인 하세요.'
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: e3a19e5ae6c98cb38445e5eaa822474b2a852135
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295733"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Microsoft 전용**

캡슐화 된 HRESULT에 매핑된 16 비트 오류 코드를 검색 합니다.

## <a name="syntax"></a>구문

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Return Value

HRESULT가 0x80040200 범위 내에 있는 경우 메서드는 HRESULT를 `WCode` 빼기 0x80040200로 반환 하 고 그렇지 않으면 0을 반환 합니다.

## <a name="remarks"></a>설명

`WCode`메서드는 COM 지원 코드에서 발생 하는 매핑을 실행 취소 하는 데 사용 됩니다. 속성 또는 메서드에 대 한 래퍼는 `dispinterface` 인수를 패키지 하 고를 호출 하는 지원 루틴을 호출 `IDispatch::Invoke` 합니다. 반환 시의 오류 HRESULT `DISP_E_EXCEPTION` 가 반환 되 면에 전달 된 구조체에서 오류 정보가 검색 됩니다 `EXCEPINFO` `IDispatch::Invoke` . 오류 코드는 구조체의 멤버에 저장 된 16 비트 값 `wCode` `EXCEPINFO` 이거나 `scode` 구조체의 멤버에 있는 전체 32 비트 값일 수 있습니다 `EXCEPINFO` . 16 비트를 반환 하는 경우 `wCode` 먼저 32 비트 오류 HRESULT에 매핑해야 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 클래스](../cpp/com-error-class.md)
