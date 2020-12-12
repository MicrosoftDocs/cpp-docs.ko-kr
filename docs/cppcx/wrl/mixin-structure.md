---
description: '다음에 대 한 자세한 정보: MixIn 구조'
title: MixIn 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: a438fb6846ae6ba88aaaa968d7b94e8d6636c4aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209388"
---
# <a name="mixin-structure"></a>MixIn 구조체

런타임 클래스가 Windows 런타임 인터페이스에서 파생되었는지 확인한 다음 있는 경우 클래식 COM 인터페이스를 확인합니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>매개 변수

*파생*<br/>
[Implements](implements-structure.md) 구조체에서 파생 된 형식입니다.

*MixInType*<br/>
기본 형식입니다.

*hasImplements*<br/>
**`true`***MixInType* 가 현재 구현에서 기본 형식으로 파생 되 면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

## <a name="remarks"></a>설명

클래스가 Windows 런타임 및 클래스 COM 인터페이스에서 파생 되는 경우 클래스 선언 목록에는 먼저 Windows 런타임 인터페이스와 모든 클래식 COM 인터페이스를 나열 해야 합니다. **MixIn** 을 사용 하면 인터페이스를 올바른 순서로 지정할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`MixIn`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
