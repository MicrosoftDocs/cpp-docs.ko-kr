---
description: '자세히 알아보기: rank 클래스'
title: rank 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::rank
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
ms.openlocfilehash: 0ec9e66b31e4dd118de3e21761bb9b2175b0c5e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337933"
---
# <a name="rank-class"></a>rank 클래스

배열 차원 수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct rank;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 쿼리는 배열 형식 *ty* 의 차원 수 값을 보유 하거나, *ty* 가 배열 형식이 아닌 경우 0을 보유 합니다.

## <a name="example"></a>예제

```cpp
// std__type_traits__rank.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "rank<int> == "
        << std::rank<int>::value << std::endl;
    std::cout << "rank<int[5]> == "
        << std::rank<int[5]>::value << std::endl;
    std::cout << "rank<int[5][10]> == "
        << std::rank<int[5][10]>::value << std::endl;

    return (0);
    }
```

```Output
rank<int> == 0
rank<int[5]> == 1
rank<int[5][10]> == 2
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[익스텐트 클래스](../standard-library/extent-class.md)
