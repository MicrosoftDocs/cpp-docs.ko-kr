---
description: Is_copy_assignable 클래스에 대해 자세히 알아보세요.
title: is_copy_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: f13752ce74f316f180fb874572efaf15d1c06c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323800"
---
# <a name="is_copy_assignable-class"></a>is_copy_assignable 클래스

할당 시 형식을 복사할 수 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 복사 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다. Is_assignable와 동일 \<Ty&, const Ty&> 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
