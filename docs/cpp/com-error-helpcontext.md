---
description: '자세한 정보: _com_error:: HelpContext'
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: 757fb572d9e41486af419712eb7f70cd7cfa7b14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295941"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Microsoft 전용**

`IErrorInfo::GetHelpContext`함수를 호출 합니다.

## <a name="syntax"></a>구문

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Return Value

`IErrorInfo::GetHelpContext`개체 내에 기록 된 개체에 대 한 결과를 반환 합니다 `IErrorInfo` `_com_error` . `IErrorInfo`기록 된 개체가 없으면 0이 반환 됩니다.

## <a name="remarks"></a>설명

메서드를 호출 하는 동안 발생 하는 모든 오류 `IErrorInfo::GetHelpContext` 는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
