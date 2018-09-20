---
title: RuntimeClassBaseT 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcfce810dff7862c60fca853b216eeb05d09dd0f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414903"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>매개 변수

*RuntimeClassTypeT*<br/>
플래그 중 하나 이상 지정 하는 필드 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 열거자입니다.

## <a name="remarks"></a>설명

도우미 메서드를 제공 `QueryInterface` 작업과 인터페이스 Id를 시작 합니다.

## <a name="members"></a>멤버

## <a name="inheritance-hierarchy"></a>상속 계층

`RuntimeClassBaseT`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)