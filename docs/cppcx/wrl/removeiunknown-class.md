---
description: '자세한 정보: RemoveIUnknown 클래스'
title: RemoveIUnknown 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 0ef00ee9859a27252550aaeec6fb9b4f9ef2d5b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278729"
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

는 `IUnknown` 기반 형식과 동일 하지만 비가상 `QueryInterface` , `AddRef` 및 `Release` 멤버 함수를 포함 하는 형식을 만듭니다.

기본적으로 COM 메서드는 가상 `QueryInterface` , `AddRef` 및 메서드를 제공 `Release` 합니다. 그러나에는 `ComPtr` 가상 메서드의 오버 헤드가 필요 하지 않습니다. `RemoveIUnknown` private, 비가상, 및 메서드를 제공 하 여 오버 헤드를 제거 `QueryInterface` `AddRef` `Release` 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`ReturnType`|템플릿 매개 변수 *T* 와 동일 하지만 비가상 멤버가 있는 형식의 동의어입니다 `IUnknown` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`T`

`RemoveIUnknown`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
