---
title: 'Issame:: Value 상수 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1f67769f7bab517c6a5010788c3627529f14db2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373524"
---
# <a name="issamevalue-constant"></a>IsSame::value 상수

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

## <a name="remarks"></a>설명

한 형식이 다른 동일한 인지 여부를 나타냅니다.

**값** 됩니다 **true** 같으면 템플릿 매개 변수, 및 **false** 템플릿 매개 변수는 서로 다른 경우.

## <a name="requirements"></a>요구 사항

**헤더:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[IsSame 구조체](../windows/issame-structure.md)<br/>
[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)