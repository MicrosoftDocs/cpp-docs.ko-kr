---
title: RuntimeClassType 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213579"
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
|`InhibitFtmBase`|`__WRL_CONFIGURATION_LEGACY__` 정의 되어 있지 않으면 `FtmBase` 지원을 사용 하지 않도록 설정 합니다.|
|`InhibitWeakReference`|약한 참조 지원을 사용 하지 않습니다.|
|`WinRt`|Windows 런타임 클래스입니다.|
|`WinRtClassicComMix`|`WinRt` 및 `ClassicCom`의 조합입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft::WRL 네임스페이스](microsoft-wrl-namespace.md)
