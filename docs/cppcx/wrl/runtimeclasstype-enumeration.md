---
description: '자세히 알아보기: RuntimeClassType 열거형'
title: RuntimeClassType 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 10055d79148124e886c4da50e40ffdb7d3d0fec0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135280"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 열거형

지원 되는 [RuntimeClass](runtimeclass-class.md) 인스턴스의 유형을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>멤버

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`ClassicCom`|클래식 COM 런타임 클래스입니다.|
|`Delegate`|`ClassicCom`과 동일합니다.|
|`InhibitFtmBase`|`FtmBase`가 정의 되지 않은 상태에서 지원을 사용 하지 않도록 설정 `__WRL_CONFIGURATION_LEGACY__` 합니다.|
|`InhibitWeakReference`|약한 참조 지원을 사용 하지 않습니다.|
|`WinRt`|Windows 런타임 클래스입니다.|
|`WinRtClassicComMix`|`WinRt` 및 `ClassicCom`의 조합입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
