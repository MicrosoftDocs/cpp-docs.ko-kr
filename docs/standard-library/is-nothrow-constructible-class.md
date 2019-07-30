---
title: is_nothrow_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 7ec4fc3ef5d9a799d5d77124870fbb337061c94c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455999"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 클래스

지정된 인수 형식을 사용할 경우 형식이 생성 가능한지와 throw되지 않는 것으로 알려져 있는지를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

*Args*\
*T*의 생성자에서 일치 하는 인수 형식입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Args*의 인수 형식을 사용 하 여 형식이 *T* 인 경우 true이 고, 생성자는 throw 되지 않는 컴파일러에 의해 생성 가능 됩니다. 그렇지 않으면 false입니다. 변수  정의가 `T t(std::declval<Args>()...);` 올바른 형식이 면 T 형식은 생성 가능입니다. *T* 와 *Args* 의 모든 형식은 완전 한 형식, **void**또는 알 수 없는 바인딩된 배열 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)
