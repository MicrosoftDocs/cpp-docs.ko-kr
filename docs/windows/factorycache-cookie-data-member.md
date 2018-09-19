---
title: 'Factorycache:: Cookie 데이터 멤버 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs:
- C++
helpviewer_keywords:
- cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97af2db56cab99412faf35efa8cd351946ab4828
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410301"
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie 데이터 멤버

Windows Runtime c + + 템플릿 라이브러리 인프라를 지원 하며 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

## <a name="remarks"></a>설명

등록된 된 Windows 런타임 또는 COM 클래스 개체를 식별 하 고 개체 등록을 취소 하려면 나중에 사용 되는 값을 포함 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[FactoryCache 구조체](../windows/factorycache-structure.md)<br/>
[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)