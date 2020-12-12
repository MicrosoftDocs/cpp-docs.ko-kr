---
description: Is_nothrow_default_constructible 클래스에 대해 자세히 알아보세요.
title: is_nothrow_default_constructible 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: bbfadf10048175472c10f264856cdb519896b65f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230798"
---
# <a name="is_nothrow_default_constructible-class"></a>is_nothrow_default_constructible 클래스

형식에 throw되지 않는 기본 생성자가 있는지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식에 nothrow 기본 생성자가 있으면 true이 고, 그렇지 않으면 false입니다. 형식 조건자의 인스턴스는 `is_nothrow_constructible<Ty>`와 같습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
