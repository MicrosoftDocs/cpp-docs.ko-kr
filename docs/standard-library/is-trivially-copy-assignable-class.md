---
description: Is_trivially_copy_assignable 클래스에 대해 자세히 알아보세요.
title: is_trivially_copy_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 010e820db570f594568cb60f4edae83b91a997c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271241"
---
# <a name="is_trivially_copy_assignable-class"></a>is_trivially_copy_assignable 클래스

형식에 Trivial 복사 할당 연산자가 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 형식 *T* 가 trivial 복사 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

클래스 *t* 에 대 한 할당 생성자는 암시적으로 제공 되 고, 클래스 *t* 에 가상 함수가 없고, 클래스 t에 가상 베이스가 없고, 클래스 *t* 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 대입 연산자가 있으며, 클래스 배열 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 대입 연산자가 있는 경우 trivial입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
