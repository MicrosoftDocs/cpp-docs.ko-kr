---
title: 'Asyncbase:: Oncancel 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs:
- C++
helpviewer_keywords:
- OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6297b2d9313a8bc2c7a4f90632affa054c49c662
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595269"
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel 메서드

파생된 클래스에서 재정의 되 면 비동기 작업을 취소 합니다.

## <a name="syntax"></a>구문

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="requirements"></a>요구 사항

**헤더:** async.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[AsyncBase 클래스](../windows/asyncbase-class.md)  
[AsyncBase::Cancel 메서드](../windows/asyncbase-cancel-method.md)