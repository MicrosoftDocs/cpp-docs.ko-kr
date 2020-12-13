---
description: Is_rvalue_reference 클래스에 대해 자세히 알아보세요.
title: is_rvalue_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: 1fb3de556f3a8b1b9aa70034a23e5e487336cd56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339028"
---
# <a name="is_rvalue_reference-class"></a>is_rvalue_reference 클래스

형식이 rvalue 참조인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

이 형식 조건자의 인스턴스는 *Ty* 형식이 [rvalue 참조](../cpp/rvalue-reference-declarator-amp-amp.md)인 경우 true입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues 및 Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)
