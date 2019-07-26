---
title: is_trivially_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 6f177463b985d3e7b2f7ab7783f9c3db0dcd5722
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448008"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 클래스

지정된 인수 형식을 사용할 경우 형식이 일반적으로 생성 가능한지를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

*Args*\
*T*의 생성자에서 일치 하는 인수 형식입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 *Args*의 인수 형식을 사용 하 여 일반적으로 생성 가능 경우 true이 고, 그렇지 않으면 false입니다. 변수  정의가 `T t(std::declval<Args>()...);` 올바른 형식이 고 특수 작업을 호출 하지 않는 것으로 알려진 경우 T 형식은 일반적으로 생성 가능입니다. *T* 와 *Args* 의 모든 형식은 완전 한 형식, **void**또는 알 수 없는 바인딩된 배열 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)
