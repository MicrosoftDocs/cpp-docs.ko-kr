---
description: '자세한 정보: 함수 호출 (c + +)'
title: 함수 호출 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
ms.openlocfilehash: 5fc33e11dbc4c9d88cc81eb41378cb6f10e00dc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195413"
---
# <a name="function-call-c"></a>함수 호출 (C++)

괄호를 사용하여 호출된 함수 호출 연산자는 이항 연산자입니다.

## <a name="syntax"></a>구문

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>설명

이 컨텍스트에서 `primary-expression`이 첫 번째 피연산자이며, 빈 인수 목록일 수 있는 `expression-list`가 두 번째 피연산자입니다. 함수 호출 연산자는 여러 매개 변수가 필요한 연산에 사용됩니다. 이는 `expression-list`가 단일 피연산자가 아닌 목록이기 때문에 가능합니다. 함수 호출 연산자는 비정적 멤버 함수여야 합니다.

오버로드된 경우 함수 호출 연산자는 함수가 호출되는 방법을 수정하는 것이 아니라 지정된 클래스 형식의 개체에 연산자가 적용될 때 연산자가 해석되는 방법을 수정합니다. 예를 들어 다음 코드는 대개 무의미합니다.

```cpp
Point pt;
pt( 3, 2 );
```

하지만 적절하게 오버로드된 함수 호출 연산자가 제공된 경우에는 이 구문을 사용하여 `x` 좌표 3 단위 및 `y` 좌표 2 단위를 오프셋할 수 있습니다. 다음 코드에 이러한 정의가 나와 있습니다.

```cpp
// function_call.cpp
class Point
{
public:
    Point() { _x = _y = 0; }
    Point &operator()( int dx, int dy )
        { _x += dx; _y += dy; return *this; }
private:
    int _x, _y;
};

int main()
{
   Point pt;
   pt( 3, 2 );
}
```

함수 호출 연산자는 함수 이름이 아닌 개체 이름에 적용됩니다.

함수 자체를 사용하기 보다는 함수에 대한 포인터를 사용하여 함수 호출 연산자를 오버로드할 수도 있습니다.

```cpp
typedef void(*ptf)();
void func()
{
}
struct S
{
   operator ptf()
   {
      return func;
   }
};

int main()
{
   S s;
   s();//operates as s.operator ptf()()
}
```

## <a name="see-also"></a>참고 항목

[연산자 오버로드](../cpp/operator-overloading.md)
