---
description: Is_move_assignable 클래스에 대해 자세히 알아보세요.
title: is_move_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: ccca3eb1da646bad9e55222a23b5ae8d511d3bb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230863"
---
# <a name="is_move_assignable-class"></a>is_move_assignable 클래스

형식을 이동 할당할 수 있는지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식에 대한 rvalue 참조를 형식에 대한 참조에 할당할 수 있는 경우 형식은 이동 할당할 수 있습니다. 형식 조건자는 `is_assignable<T&, T&&>`와 같습니다. 이동 할당 가능한 형식에는 컴파일러에서 생성되었거나 사용자가 정의한 이동 할당 연산자를 포함하는 참조 가능한 스칼라 형식과 클래스 형식이 포함됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
