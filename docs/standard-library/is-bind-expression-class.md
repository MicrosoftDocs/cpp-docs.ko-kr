---
description: Is_bind_expression 클래스에 대해 자세히 알아보세요.
title: is_bind_expression 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: 1430beefd1c046b2910c562385f26d2788c88865
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323848"
---
# <a name="is_bind_expression-class"></a>is_bind_expression 클래스

형식이 `bind`를 호출하여 생성되었는지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template<class Ty>
struct is_bind_expression {
   static const bool value;
};
```

## <a name="remarks"></a>설명

`Ty` 형식이 `bind`를 호출하여 반환된 형식인 경우에는 상수 멤버 `value`가 true이고, 그렇지 않으면 false입니다.

## <a name="example"></a>예제

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```
