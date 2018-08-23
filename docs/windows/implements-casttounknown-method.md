---
title: 'Implements:: casttounknown 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586360"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown 메서드

기본 포인터를 가져옵니다 `IUnknown` 인터페이스입니다.

## <a name="syntax"></a>구문

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>반환 값

이 작업에서 항상 성공 하 고 반환 된 `IUnknown` 포인터입니다.

## <a name="remarks"></a>설명

내부 도우미 함수입니다.

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Implements 구조체](../windows/implements-structure.md)