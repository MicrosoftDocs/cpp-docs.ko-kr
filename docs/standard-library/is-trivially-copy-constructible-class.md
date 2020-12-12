---
description: Is_trivially_copy_constructible 클래스에 대해 자세히 알아보세요.
title: is_trivially_copy_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: c247e81f52ad98e546a840bb38938fe15bc9b302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118526"
---
# <a name="is_trivially_copy_constructible-class"></a>is_trivially_copy_constructible 클래스

형식에 trivial 복사 생성자가 있는지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 형식 *T* 가 trivial 복사 생성자가 있는 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

클래스 *t* 에 대 한 복사 생성자는 암시적으로 선언 되 고, *t* 클래스에 가상 함수나 가상 베이스가 없고, 클래스 *t* 의 모든 직접 기본에 trivial 복사 생성자가 있고, 클래스 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 복사 생성자가 있으며, 클래스 배열 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 복사 생성자가 있는 경우 trivial입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
