---
description: '자세한 정보: 익스텐트 클래스'
title: extent 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: d3db49db99d2cb7a241ca3b69c48fa6bcf2cb490
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324388"
---
# <a name="extent-class"></a>extent 클래스

배열 차원을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

*보이지*\
쿼리에 바인딩되는 배열입니다.

## <a name="remarks"></a>설명

*Ty* 가 적어도 하나 *이상의 차원을 가진* 배열 형식인 경우 형식 쿼리는 *i* 에 지정 된 차원의 요소 수를 포함 합니다. *Ty* 가 배열 형식이 아니거나 순위가 *i* 인 경우 또는 *i* 가 0이 고 *Ty* 가 "알 수 없는 바인딩된 배열" 형식인 경우 `U` 형식 쿼리는 값 0을 보유 합니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[remove_all_extents 클래스](../standard-library/remove-all-extents-class.md)\
[remove_extent 클래스](../standard-library/remove-extent-class.md)
