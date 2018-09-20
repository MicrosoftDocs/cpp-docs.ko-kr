---
title: 'Asyncbase:: Put_id 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65d36c76ca05343084b709096d38014d802628c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439005"
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id 메서드

비동기 작업의 핸들을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>매개 변수

*ID*<br/>
0이 아닌 핸들입니다.

## <a name="return-value"></a>반환 값

성공 하면 s_ok이 고 이 고, 그렇지 E_INVALIDARG 또는 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** async.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[AsyncBase 클래스](../windows/asyncbase-class.md)