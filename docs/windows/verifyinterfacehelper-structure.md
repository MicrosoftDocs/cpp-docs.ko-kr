---
title: VerifyInterfaceHelper 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInterfaceHelper structure
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62914b6e46b1fe98c95fba3ab96821c961888db8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413655"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 구조체

Windows Runtime c + + 템플릿 라이브러리 인프라를 지원 하며 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <
   bool isWinRTInterface,
   typename I
>
struct VerifyInterfaceHelper;

template <
   typename I
>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>매개 변수

*I*<br/>
확인 하는 인터페이스입니다.

*isWinRTInterface*

## <a name="remarks"></a>설명

템플릿 매개 변수로 지정 된 인터페이스에 특정 요구 사항을 충족 하는지 확인 합니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[VerifyInterfaceHelper::Verify 메서드](../windows/verifyinterfacehelper-verify-method.md)||

## <a name="inheritance-hierarchy"></a>상속 계층

`VerifyInterfaceHelper`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)