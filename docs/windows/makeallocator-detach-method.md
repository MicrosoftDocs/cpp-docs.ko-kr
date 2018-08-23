---
title: 'Makeallocator:: Detach 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d609b685bb5e3d24d561e66050769b6b7728e691
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607164"
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach 메서드

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
__forceinline void Detach();
```

## <a name="remarks"></a>설명

의해 할당 된 메모리를 분리 합니다 [할당](../windows/makeallocator-allocate-method.md) 현재 메서드에서 **MakeAllocator** 개체입니다.

호출 하는 경우 **Detach()** 에서 제공한 메모리를 삭제 하는 일을 담당 하는 `Allocate` 메서드.

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[MakeAllocator 클래스](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)