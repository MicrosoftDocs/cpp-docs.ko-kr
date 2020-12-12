---
description: '자세한 정보: _com_error:: ErrorInfo'
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 36092ae9287352d421bf502ad24c054cf3b7a907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296045"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 전용**

`IErrorInfo`생성자에 전달 된 개체를 검색 합니다.

## <a name="syntax"></a>구문

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Return Value

생성자에 전달된 원시 `IErrorInfo` 항목입니다.

## <a name="remarks"></a>설명

`IErrorInfo`개체에서 캡슐화 된 항목 `_com_error` 을 검색 하거나, 기록 된 항목이 없으면 NULL을 반환 합니다 `IErrorInfo` . 호출자는 반환 된 `Release` 개체의 사용을 마치면 반환 된 개체에서를 호출 해야 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
