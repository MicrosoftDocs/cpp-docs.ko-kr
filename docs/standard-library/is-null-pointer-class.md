---
description: Is_null_pointer 클래스에 대해 자세히 알아보세요.
title: is_null_pointer 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_null_pointer
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
ms.openlocfilehash: 91a8b6a27668af72d7641ce1fe36dafc119f5aa7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230668"
---
# <a name="is_null_pointer-class"></a>is_null_pointer 클래스

형식이 std::nullptr_t인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 이면 true이 고 `std::nullptr_t` , 그렇지 않으면 false입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
