---
description: '자세한 정보: _com_error:: Error'
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 25dd78caeada9e7606bc26f241126b0d0f510f4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318197"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Microsoft 전용**

생성자에 전달 된 HRESULT를 검색 합니다.

## <a name="syntax"></a>구문

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Return Value

생성자에 전달 된 원시 HRESULT 항목입니다.

## <a name="remarks"></a>설명

개체의 캡슐화 된 HRESULT 항목을 검색 `_com_error` 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
