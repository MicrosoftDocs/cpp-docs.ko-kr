---
description: '다음에 대 한 자세한 정보: _1 개체'
title: _1 개체
ms.date: 01/15/2021
f1_keywords:
- _1
- std::_1
- functional/std::_1
- std::_2
- functional/std::_2
- std::_3
- functional/std::_3
- std::_4
- functional/std::_4
- std::_5
- functional/std::_5
- std::_6
- functional/std::_6
- std::_7
- functional/std::_7
- std::_8
- functional/std::_8
- std::_9
- functional/std::_9
- std::_10
- functional/std::_10
- std::_11
- functional/std::_11
- std::_12
- functional/std::_12
- std::_13
- functional/std::_13
- std::_14
- functional/std::_14
- std::_15
- functional/std::_15
- std::_16
- functional/std::_16
- std::_17
- functional/std::_17
- std::_18
- functional/std::_18
- std::_19
- functional/std::_19
- std::_20
- functional/std::_20
- functional/std::placeholders
- std::placeholders
helpviewer_keywords:
- _1 object
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
ms.openlocfilehash: d6c7550580b1b73485d0d3ee1bcde7497e828650
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667521"
---
# <a name="_1-object"></a>`_1` 개체

대체 가능한 인수에 대한 자리 표시자입니다.

## <a name="syntax"></a>구문

```cpp
namespace placeholders {
    extern unspecified _1, _2, ... _N
} // namespace placeholders (within std)
```

## <a name="remarks"></a>설명

개체는 `_1, _2, ... _N` 에서 반환 하는 개체에 대 한 함수 호출에서 각각 첫 번째, 두 번째, ..., n 번째 인수를 나타내는 자리 표시자입니다 [`bind`](functional-functions.md#bind) . 예를 들어를 사용 `_6` 하 여 식을 계산할 때 여섯 번째 인수를 삽입 해야 하는 위치를 지정할 수 있습니다 `bind` .

Microsoft 구현에서의 값은 `_N` 20입니다.

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
