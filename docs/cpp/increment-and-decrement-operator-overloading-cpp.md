---
description: '자세한 정보: 증가 및 감소 연산자 오버 로드 (c + +)'
title: 증가 및 감소 연산자 오버로드(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: f2704a1c10375bf8422324d90f41c6e3ac245505
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113924"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>증가 및 감소 연산자 오버로드(C++)

증가 및 감소 연산자의 경우 각각 두 가지 변형이 있으므로 특수 범주에 속합니다.

- 사전 증가 및 사후 증가

- 사전 감소 및 사후 감소

오버로드된 연산자 함수를 작성하는 경우 이러한 연산자의 전위 버전과 후위 버전에 대해 별도의 버전을 구현하는 것이 유용할 수 있습니다. 두 가지를 구분 하기 위해 연산자의 전위 형식은 다른 단항 연산자와 정확히 같은 방식으로 선언 됩니다. 후 위 폼은 형식의 추가 인수를 허용 합니다 **`int`** .

> [!NOTE]
> 증가 또는 감소 연산자의 후 위 형식에 대해 오버 로드 된 연산자를 지정 하는 경우 추가 인수는 형식 이어야 하 **`int`** 고 다른 형식을 지정 하면 오류가 생성 됩니다.

다음 예제에서는 `Point` 클래스에 대해 전위 및 후위 증가 연산자와 감소 연산자를 정의하는 방법을 보여 줍니다.

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

다음 함수 헤드를 사용하여 파일 범위에서 전역으로 동일한 연산자를 정의할 수 있습니다.

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

**`int`** 증가 또는 감소 연산자의 후 위 형식을 나타내는 형식의 인수는 인수를 전달 하는 데 일반적으로 사용 되지 않습니다. 일반적으로 0 값을 포함합니다. 그러나 이 인수는 다음과 같이 사용할 수 있습니다.

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

위의 코드에 나와 있는 것처럼 명시적 호출 외에 이러한 값을 전달하기 위해 증가 또는 감소 연산자를 사용하는 구문은 없습니다. 이 기능을 구현 하는 보다 간단한 방법은 더하기/할당 연산자 ()를 오버 로드 하는 것입니다 **+=** .

## <a name="see-also"></a>참고 항목

[연산자 오버로드](../cpp/operator-overloading.md)
