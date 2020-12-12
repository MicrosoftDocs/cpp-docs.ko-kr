---
description: Is_constructible 클래스에 대해 자세히 알아보세요.
title: is_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: 66d17141693933850ce78dc15abe108664d56c8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323817"
---
# <a name="is_constructible-class"></a>is_constructible 클래스

지정된 인수 형식을 사용할 경우 형식이 생성 가능한지를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

*Args*\
*T* 의 생성자에서 일치 하는 인수 형식입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Args* 의 인수 형식을 사용 하 여 *T* 형식이 생성 가능 경우 true이 고, 그렇지 않으면 false입니다. 변수 정의가 올바른 형식이 면 *T* 형식은 생성 가능입니다 `T t(std::declval<Args>()...);` . *T* 와 *Args* 의 모든 형식은 완전 한 형식, **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
