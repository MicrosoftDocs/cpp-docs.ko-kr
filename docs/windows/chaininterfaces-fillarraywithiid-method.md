---
title: 'Chaininterfaces:: Fillarraywithiid 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f1ce699c-dfb6-40a9-9ea0-e6703d3cf971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09e0dc3b9caf059bb8ecdce0468dfc118ce9ebfa
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594946"
---
# <a name="chaininterfacesfillarraywithiid-method"></a>ChainInterfaces::FillArrayWithIid 메서드

인터페이스 ID가 정의한 저장소 합니다 *I0* 인터페이스 Id의 지정된 된 배열에 지정된 된 위치에 템플릿 매개 변수입니다.

## <a name="syntax"></a>구문

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>매개 변수

*index*  
에 인덱스 값에 대 한 포인터를 *iid* 배열입니다.

*iid*  
인터페이스 Id의 배열입니다.

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[ChainInterfaces 구조체](../windows/chaininterfaces-structure.md)