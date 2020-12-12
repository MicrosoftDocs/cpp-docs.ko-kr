---
description: Is_trivially_default_constructible 클래스에 대해 자세히 알아보세요.
title: is_trivially_default_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 3686dab86b8bf04fe7629b53651988d7ccef161e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118409"
---
# <a name="is_trivially_default_constructible-class"></a>is_trivially_default_constructible 클래스

형식에 Trivial 기본 생성자가 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 trivial 생성자가 있는 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

*클래스의 기본 생성자는 다음과* 같은 경우 trivial입니다.

- 암시적으로 선언된 기본 생성자인 경우

- *Ty* 클래스에 가상 함수가 없습니다.

- *Ty* 클래스에 가상 기본이 없습니다.

- 클래스의 모든 직접 *기본에 trivial* 생성자가 있습니다.

- 클래스 형식의 모든 비정적 데이터 멤버의 클래스에 Trivial 생성자가 있는 경우

- 클래스 배열 형식의 모든 비정적 데이터 멤버의 클래스에 Trivial 생성자가 있는 경우

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
