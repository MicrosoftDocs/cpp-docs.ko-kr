---
description: Is_final 클래스에 대해 자세히 알아보세요.
title: is_final 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: 04660309205689e14200cb5d214ce5dc80efb88f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323743"
---
# <a name="is_final-class"></a>is_final 클래스

형식이 `final`로 표시된 클래스 종류인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이로 표시 된 클래스 형식인 경우 true `final` 이 고, 그렇지 않으면 false입니다. *T* 가 클래스 형식이 면 완전 한 형식 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[final 지정자](../cpp/final-specifier.md)
