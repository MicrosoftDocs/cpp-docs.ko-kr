---
description: '자세한 정보: _com_error:: HRESULTToWCode'
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 1bbf62be42d4e34a2ef73493f0449c2ffbaf0646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295836"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 전용**

32 비트 HRESULT를 16 비트에 매핑합니다 `wCode` .

## <a name="syntax"></a>구문

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>매개 변수

*시간*<br/>
16 비트에 매핑할 32 비트 HRESULT `wCode` 입니다.

## <a name="return-value"></a>반환 값

`wCode`32 비트 HRESULT에서 매핑된 16 비트입니다.

## <a name="remarks"></a>설명

자세한 내용은 [_com_error:: WCode](../cpp/com-error-wcode.md) 를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 클래스](../cpp/com-error-class.md)
