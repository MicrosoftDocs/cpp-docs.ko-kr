---
description: Is_lvalue_reference 클래스에 대해 자세히 알아보세요.
title: is_lvalue_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 624849bce456048f4454542db8a03f37771a46d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230903"
---
# <a name="is_lvalue_reference-class"></a>is_lvalue_reference 클래스

형식이 lvalue 참조인지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

이 형식 조건자의 인스턴스는 *Ty* 형식이 개체나 함수에 대 한 참조 인 경우 true이 고 그렇지 않은 경우 false입니다. *Ty* 는 rvalue 참조일 수 없습니다. rvalue에 대한 자세한 내용은 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues 및 Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)
