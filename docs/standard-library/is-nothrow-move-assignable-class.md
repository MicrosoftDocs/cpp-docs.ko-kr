---
description: Is_nothrow_move_assignable 클래스에 대해 자세히 알아보세요.
title: is_nothrow_move_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
ms.openlocfilehash: 77d61ff79d56ff1caee2d856ac4d947821c16946
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230759"
---
# <a name="is_nothrow_move_assignable-class"></a>is_nothrow_move_assignable 클래스

형식에 **`nothrow`** 이동 할당 연산자가 있는지 테스트 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식에 nothrow 이동 할당 연산자가 있는 경우 true이 고 그렇지 않은 경우 false입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
