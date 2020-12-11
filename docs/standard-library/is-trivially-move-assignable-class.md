---
description: Is_trivially_move_assignable 클래스에 대해 자세히 알아보세요.
title: is_trivially_move_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 3f852bd2b1ccf3647a4aa05bb5996f015341b342
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154333"
---
# <a name="is_trivially_move_assignable-class"></a>is_trivially_move_assignable 클래스

형식에 trivial 이동 할당 연산자가 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 trivial 이동 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

클래스에 대 한 이동 할당 연산자 *는 다음과* 같은 경우 trivial입니다.

- 암시적으로 제공된 경우
- *Ty* 클래스에 가상 함수가 없습니다.
- *Ty* 클래스에 가상 기본이 없습니다.
- 클래스 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 이동 할당 연산자가 있는 경우
- 클래스 형식 배열의 모든 비정적 데이터 멤버의 클래스에 trivial 이동 할당 연산자가 있는 경우

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
