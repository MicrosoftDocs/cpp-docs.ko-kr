---
description: '자세한 정보: _com_error:: GUID'
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 32f88728d5c0f93094413aaeae8fb3c116b415c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295967"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Microsoft 전용**

`IErrorInfo::GetGUID`함수를 호출 합니다.

## <a name="syntax"></a>구문

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Return Value

`IErrorInfo::GetGUID`개체 내에 기록 된 개체에 대 한 결과를 반환 합니다 `IErrorInfo` `_com_error` . `IErrorInfo`기록 된 개체가 없으면을 반환 `GUID_NULL` 합니다.

## <a name="remarks"></a>설명

메서드를 호출 하는 동안 발생 하는 모든 오류 `IErrorInfo::GetGUID` 는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
