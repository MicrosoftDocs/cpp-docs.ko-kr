---
title: 'Chaininterfaces:: Verify 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6dbc595714cbecf2ad13db13051866e31e5ebcd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581060"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify 메서드

템플릿 매개 변수에서 정의 된 각 인터페이스가 확인 *I0* 를 통해 *I9* 에서 상속 `IUnknown` 및/또는 `IInspectable`를 올바르고 *I0* 에서 상속 *I1* 를 통해 *I9*합니다.

## <a name="syntax"></a>구문

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

## <a name="remarks"></a>설명

확인 작업이 실패 하는 경우는 **static_assert** 오류를 설명 하는 오류 메시지를 내보냅니다.

템플릿 매개 변수 *I0* 하 고 *I1* 필요 및 매개 변수 *I2* 를 통해 *I9* 는 선택 사항입니다.

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[ChainInterfaces 구조체](../windows/chaininterfaces-structure.md)