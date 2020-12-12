---
description: '자세한 정보: _com_error:: operator ='
title: _com_error::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_error::operator=
helpviewer_keywords:
- _com_error [C++]
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
ms.openlocfilehash: 3c27fcd612fcf2fd67b09ac1217286edd69e1557
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295798"
---
# <a name="_com_erroroperator-"></a>_com_error::operator =

**Microsoft 전용**

기존 `_com_error` 개체를 다른 개체에 할당합니다.

## <a name="syntax"></a>구문

```
_com_error& operator = (
   const _com_error& that
) throw ( );
```

#### <a name="parameters"></a>매개 변수

*that*<br/>
`_com_error` 개체입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
