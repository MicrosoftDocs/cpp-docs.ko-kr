---
description: Is_nothrow_copy_constructible 클래스에 대해 자세히 알아보세요.
title: is_nothrow_copy_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
ms.openlocfilehash: b238b86a5780d12dd6c1e62e0b2d79b9fbc139dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323605"
---
# <a name="is_nothrow_copy_constructible-class"></a>is_nothrow_copy_constructible 클래스

형식에 복사 생성자가 있는지 테스트 **`nothrow`** 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식에 nothrow 복사 생성자가 있는 경우 true이 고 그렇지 않은 경우 false입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
