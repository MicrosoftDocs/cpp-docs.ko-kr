---
title: 'Semaphoretraits:: Unlock 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e993c58ea6fc84e0b4001b488632858e5251d67b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583973"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock 메서드

공유 리소스의 릴리스 컨트롤입니다.

## <a name="syntax"></a>구문

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>매개 변수

*h*  
에 대 한 핸들을 **세마포** 개체입니다.

## <a name="remarks"></a>설명

잠금 해제 작업이 성공적 이면 **Unlock()** 실패의 원인을 나타내는 오류를 생성 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>참고 항목

[SemaphoreTraits 구조체](../windows/semaphoretraits-structure.md)