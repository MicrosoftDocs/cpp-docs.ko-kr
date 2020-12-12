---
description: '자세한 정보: _com_error:: WCodeToHRESULT'
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: 9925c34f14f0685cb563e37a8cae0970911f009c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295720"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 전용**

16 비트 *Wcode* 를 32 비트 HRESULT에 매핑합니다.

## <a name="syntax"></a>구문

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>매개 변수

*wCode*<br/>
32 비트 HRESULT에 매핑할 16 비트 *Wcode* 입니다.

## <a name="return-value"></a>반환 값

16 비트 *Wcode* 에서 매핑된 32 비트 HRESULT입니다.

## <a name="remarks"></a>설명

[Wcode](../cpp/com-error-wcode.md) 멤버 함수를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error 클래스](../cpp/com-error-class.md)
