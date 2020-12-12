---
description: Is_standard_layout 클래스에 대해 자세히 알아보세요.
title: is_standard_layout 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 8f1f24fcb29e862dff10c2a51d1c9d0b2b28541f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271254"
---
# <a name="is_standard_layout-class"></a>is_standard_layout 클래스

형식이 표준 레이아웃인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>매개 변수

*Ty*\
쿼리할 형식입니다.

## <a name="remarks"></a>설명

이 형식 조건자의 인스턴스는 *Ty* 형식이 메모리에서 멤버 개체의 표준 레이아웃을 포함 하는 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
