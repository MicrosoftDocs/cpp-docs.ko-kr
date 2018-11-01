---
title: RemoveIUnknown 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 06b3ec86874bcf7968483eb4557b6b6b247ecdfe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556353"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
클래스입니다.

## <a name="remarks"></a>설명

해당 하는 형식을 만들 수는 `IUnknown`-기반, 하지만 형식은 비가상 `QueryInterface`를 `AddRef`, 및 `Release` 멤버 함수입니다.

기본적으로 COM 메서드 제공 가상 `QueryInterface`하십시오 `AddRef`, 및 `Release` 메서드. 그러나 `ComPtr` 가상 메서드의 오버 헤드가 필요 하지 않습니다. `RemoveIUnknown` 개인, 비가상 함으로써 오버 헤드를 제거 `QueryInterface`하십시오 `AddRef`, 및 `Release` 메서드.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|이름|설명|
|----------|-----------------|
|`ReturnType`|템플릿 매개 변수에 해당 하는 형식에 대 한 동의어 *T* 비가상 되었지만 `IUnknown` 멤버입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`T`

`RemoveIUnknown`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)