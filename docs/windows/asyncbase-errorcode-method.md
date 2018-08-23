---
title: 'Asyncbase:: Errorcode 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7336824d04745440a1f6152ebacfed2afc62258e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602380"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 메서드

현재 비동기 작업에 대 한 오류 코드를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>매개 변수

*error*  
이 작업에서 현재 오류 코드를 저장 하는 위치를 위치입니다.

## <a name="remarks"></a>설명

이 작업은 스레드로부터 안전 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** async.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[AsyncBase 클래스](../windows/asyncbase-class.md)