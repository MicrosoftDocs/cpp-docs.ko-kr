---
title: 'Isbaseofstrict:: Value 상수 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65b69c974e74ff68a1af2e17ff1fc8f03e03e3af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439291"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value 상수

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
static const bool value = __is_base_of(Base, Derived);
```

## <a name="remarks"></a>설명

한 형식이 다른 형식의 기본 인지 여부를 나타냅니다.

**값** 됩니다 **true** 경우 형식 `Base` 형식의 기본 클래스인 `Derived`, 그렇지 않으면 **false**합니다.

## <a name="requirements"></a>요구 사항

**헤더:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[IsBaseOfStrict 구조체](../windows/isbaseofstrict-structure.md)<br/>
[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)