---
title: _1 개체 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _1
- std::_1
- functional/std::_1
dev_langs:
- C++
helpviewer_keywords:
- _1 object
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afb57f408c52f6884c68e93af88671d49815ef69
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="1-object"></a>_1 개체

대체 가능한 인수에 대한 자리 표시자입니다.

## <a name="syntax"></a>구문

```cpp
namespace placeholders {
    extern unspecified _1,
    _2, ... _M
 } // namespace placeholders (within std)
```

## <a name="remarks"></a>설명

개체 `_1, _2, ... _M` 자리 표시자를 지정 하는 첫 번째, 두 번째,..., Mth 인수 함수 호출을 반환 하는 개체에 각각 [바인딩할](../standard-library/functional-functions.md#bind)합니다. bind 식을 평가할 때 N번째 인수를 삽입해야 하는 위치를 지정하려면 `_N`을 사용합니다.

이 구현에서 `M`의 값은 20입니다.

## <a name="example"></a>예제

```cpp
// std__functional_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
    {
    std::cout << x << "^2 == " << x * x << std::endl;
    }

void product(double x, double y)
    {
    std::cout << x << "*" << y << " == " << x * y << std::endl;
    }

int main()
    {
    double arg[] = {1, 2, 3};

    std::for_each(&arg[0], &arg[3], square);
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(square, _1));

    return (0);
    }

```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[bind](../standard-library/functional-functions.md#bind)<br/>
[is_placeholder 클래스](../standard-library/is-placeholder-class.md)<br/>
