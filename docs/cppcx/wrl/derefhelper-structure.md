---
description: '자세히 알아보기: DerefHelper Structure'
title: DerefHelper 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 8605e3923d8d3099a080be22f9d8e70ee9187ef9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272918"
---
# <a name="derefhelper-structure"></a>DerefHelper 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
템플릿 매개 변수입니다.

## <a name="remarks"></a>설명

템플릿 매개 변수에 대 한 역참조 된 포인터를 나타냅니다 `T*` .

**DerefHelper** 은와 같은 식에 사용 됩니다 `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;` .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`DerefType`|역참조 된 템플릿 매개 변수의 식별자 `T*` 입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`DerefHelper`

## <a name="requirements"></a>요구 사항

**헤더:** async. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
