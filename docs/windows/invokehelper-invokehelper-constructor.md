---
title: 'Invokehelper:: Invokehelper 생성자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11f3e82f0834863c3cdfb476443a4dbd0bdf1f6f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385081"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper 생성자

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>매개 변수

*콜백*<br/>
이벤트 처리기입니다.

## <a name="remarks"></a>설명

새 인스턴스를 초기화 합니다 **InvokeHelper** 클래스입니다.

`TCallback` 템플릿 매개 변수는 이벤트 처리기의 유형을 지정 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[InvokeHelper 구조체](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)