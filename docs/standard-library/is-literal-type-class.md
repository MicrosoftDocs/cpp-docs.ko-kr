---
description: Is_literal_type 클래스에 대해 자세히 알아보세요.
title: is_literal_type 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 97cb609c5a42bed0be205b1b51ff901d3e366bb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323688"
---
# <a name="is_literal_type-class"></a>is_literal_type 클래스

형식을 **`constexpr`** 변수로 사용 하거나 함수에서 생성, 사용 또는 반환할 수 있는지 여부를 테스트 **`constexpr`** 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 *리터럴 형식이* 면 true이 고, 그렇지 않으면 false입니다. 리터럴 형식은 **`void`** , 스칼라 형식, 참조 형식, 리터럴 형식의 배열 또는 리터럴 클래스 형식 중 하나입니다. 리터럴 클래스 형식은 trivial 소멸자가 있는 클래스 형식 이거나, 집계 형식 이거나, 이동 하지 않는 비 복사 생성자가 하나 이상 있으며 **`constexpr`** , 모든 기본 클래스 및 비정적 데이터 멤버가 비휘발성 리터럴 형식이 기 때문입니다. 리터럴의 형식은 항상 리터럴 형식 이지만 리터럴 형식의 개념에는 컴파일러가 컴파일 타임에로 평가할 수 있는 모든 항목이 포함 됩니다 **`constexpr`** .

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
