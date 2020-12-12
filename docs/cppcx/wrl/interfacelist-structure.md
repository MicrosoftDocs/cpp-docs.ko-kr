---
description: '자세한 정보: 인터페이스 목록 구조'
title: InterfaceList 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 660ae5137b7ff41129ce3866f0d289045f7dee9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124581"
---
# <a name="interfacelist-structure"></a>InterfaceList 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
인터페이스 이름입니다. 재귀 목록의 첫 번째 인터페이스입니다.

*U*<br/>
인터페이스 이름입니다. 재귀 목록의 나머지 인터페이스입니다.

## <a name="remarks"></a>설명

재귀 인터페이스 목록을 만드는 데 사용 됩니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`FirstT`|템플릿 매개 변수 *T* 의 동의어입니다.|
|`RestT`|템플릿 매개 변수 *U* 의 동의어입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`InterfaceList`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
