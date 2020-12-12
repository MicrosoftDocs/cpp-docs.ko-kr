---
description: Is_trivially_assignable 클래스에 대해 자세히 알아보세요.
title: is_trivially_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: fbbf14b83dff4bea9ed50eddf93512899f6d9fb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118552"
---
# <a name="is_trivially_assignable-class"></a>is_trivially_assignable 클래스

`From` 형식의 값을 `To` 형식에 일반적으로 할당할 수 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>매개 변수

*받는 사람*\
할당을 받는 개체의 형식입니다.

*보낸 사람*\
값을 제공하는 개체의 형식입니다.

## <a name="remarks"></a>설명

`declval<To>() = declval<From>()` 식은 올바른 형식이어야 하며 특수한 작업이 필요 없는 것으로 컴파일러에 알려져 있어야 합니다. 및 둘 다 `From` `To` 완전 한 형식, **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
