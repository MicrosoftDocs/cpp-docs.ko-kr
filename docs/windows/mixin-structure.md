---
title: MixIn 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ccea9a053f47ae206cbe5c8412c387f07bd5b52
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603429"
---
# <a name="mixin-structure"></a>MixIn 구조체

런타임 클래스가 Windows 런타임 인터페이스에서 파생되었는지 확인한 다음 있는 경우 클래식 COM 인터페이스를 확인합니다.

## <a name="syntax"></a>구문

```cpp
template<
   typename Derived,
   typename MixInType,
   bool hasImplements = __is_base_of(Details::ImplementsBase,
   MixInType)  
>
struct MixIn;
```

### <a name="parameters"></a>매개 변수

*파생 된*  
형식에서 파생 된 [구현](../windows/implements-structure.md) 구조입니다.

*MixInType*  
기본 형식입니다.

*hasImplements*  
**true** 하는 경우 *MixInType* 는 현재 구현에서 파생 된 기본 형식입니다. **false** 그렇지 않은 경우.

## <a name="remarks"></a>설명

Windows 런타임 및 COM 클래스 인터페이스에서 파생 된 클래스는, 클래스 선언 목록에는 모든 Windows 런타임 인터페이스 먼저 나열 해야 합니다 하 고 모든 클래식 COM 인터페이스입니다. **MixIn** 인터페이스가 올바른 순서로 지정 되어 있는지 확인 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`MixIn`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft::WRL 네임스페이스](../windows/microsoft-wrl-namespace.md)