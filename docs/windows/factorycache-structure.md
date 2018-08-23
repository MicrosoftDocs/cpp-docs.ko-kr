---
title: FactoryCache 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df2335a49d2d5daf862db7cea7eb413c01164bee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609030"
---
# <a name="factorycache-structure"></a>FactoryCache 구조체

Windows Runtime c + + 템플릿 라이브러리 인프라를 지원 하며 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>설명

클래스 팩터리와 wrt 등록을 식별 하는 값 또는 COM 클래스 개체의 위치를 포함 합니다.

## <a name="members"></a>멤버

### <a name="public-data-members"></a>공용 데이터 멤버

|이름|설명|
|----------|-----------------|
|[FactoryCache::cookie 데이터 멤버](../windows/factorycache-cookie-data-member.md)|등록된 된 Windows 런타임 또는 COM 클래스 개체를 식별 하 고 개체 등록을 취소 하려면 나중에 사용 되는 값을 포함 합니다.|
|[FactoryCache::factory 데이터 멤버](../windows/factorycache-factory-data-member.md)|Windows 런타임 또는 COM 클래스 팩터리를 가리킵니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`FactoryCache`

## <a name="requirements"></a>요구 사항

**헤더:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)