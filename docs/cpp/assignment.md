---
description: '자세히 알아보기: 할당'
title: 할당
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 696706202e70e8baf50dda34ac98ff9bca5dcda2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319493"
---
# <a name="assignment"></a>할당

대입 연산자 ()는 엄격 하 게 **=** 말하면 이항 연산자입니다. 할당 연산자의 선언은 다음을 제외하고 다른 모든 이항 연산자와 동일합니다.

- 비정적 멤버 함수여야 합니다. **Operator =** 를 비멤버 함수로 선언할 수 없습니다.
- 파생 클래스가 상속하지 않습니다.
- 기본 **operator =** 함수는 클래스 형식에 대해 컴파일러에서 생성 될 수 있습니다 (있는 경우).

다음 예제에서는 할당 연산자를 선언하는 방법을 보여 줍니다.

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

제공 된 인수는 식의 오른쪽입니다. 연산자는 개체를 반환하여 할당 연산자의 동작을 보존하고, 할당 연산자는 할당이 완료된 후 왼쪽의 값을 반환합니다. 이렇게 하면 다음과 같은 할당 체인이 가능 합니다.

```cpp
pt1 = pt2 = pt3;
```

복사 할당 연산자는 복사 생성자와 혼동 하지 않아야 합니다. 후자는 기존 개체에서 새 개체를 생성 하는 동안 호출 됩니다.

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> 복사 할당 연산자를 정의 하는 클래스가 복사 생성자, 소멸자 및를 사용 하 여 c + + 11, 이동 생성자 및 이동 할당 연산자를 사용 하 여 명시적으로 정의 해야 하는 [세 가지 규칙](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) 을 따르는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

- [연산자 오버로드](../cpp/operator-overloading.md)
- [복사 생성자 및 복사 할당 연산자(C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
