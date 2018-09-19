---
title: _com_error::HelpContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c2a1810410194f1261da907199a3b6665e5be30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074372"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Microsoft 전용**

호출 `IErrorInfo::GetHelpContext` 함수입니다.

## <a name="syntax"></a>구문

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>반환 값

결과 반환 합니다 `IErrorInfo::GetHelpContext` 에 대 한는 `IErrorInfo` 내에 기록 된 개체는 `_com_error` 개체입니다. 없으면 `IErrorInfo` 개체는 기록, 0을 반환 합니다.

## <a name="remarks"></a>설명

호출 하는 동안 모든 오류를 `IErrorInfo::GetHelpContext` 메서드는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[_com_error 클래스](../cpp/com-error-class.md)