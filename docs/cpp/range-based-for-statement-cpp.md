---
description: '자세히 알아보기: 범위 기반 for 문 (c + +)'
title: 범위 기반 for 문(C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 0d32086009190fe69333a2f36ff03bb551396d98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319393"
---
# <a name="range-based-for-statement-c"></a>범위 기반 for 문(C++)

`statement`의 각 요소에 대해 `expression`를 반복적 및 순차적으로 실행합니다.

## <a name="syntax"></a>Syntax

> **`for (`***-범위 선언* **`:`** *식***`)`**\
&emsp;*문*

## <a name="remarks"></a>설명

범위 기반 문을 사용 하 여 범위를 **`for`** 통해 실행 되어야 하는 루프 를 생성 합니다. 범위는에서 반복할 수 있는 것으로 정의 됩니다. 예를 들어, `std::vector` 및가 정의 하는 다른 c + + 표준 라이브러리 시퀀스를 사용할 수 있습니다 `begin()` `end()` . 부분에 선언 된 이름은 문에 대해 `for-range-declaration` 로컬 이며 **`for`** 또는에서 다시 선언할 수 없습니다 `expression` `statement` . [`auto`](../cpp/auto-cpp.md)문의 부분에서 키워드를 선호 합니다 `for-range-declaration` .

**Visual Studio 2017의 새로운 작업:**  범위 기반 **`for`** 루프에서는 더 이상를 사용 하지 않아도 되 `begin()` 고 `end()` 동일한 형식의 개체가 반환 됩니다. 이렇게 하면 `end()` 범위-V3 제안에 정의 된 대로 범위에서 사용 되는 것과 같은 센티널 개체를 반환할 수 있습니다. 자세한 내용은 [Range-Based `For` 루프 일반화](https://wg21.link/p0184r0) 및 [GitHub의 범위 v3 라이브러리](https://github.com/ericniebler/range-v3)를 참조 하세요.

이 코드는 범위 기반 루프를 사용 하 여 배열 및 벡터를 반복 하는 방법을 보여 줍니다 **`for`** .

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

출력은 다음과 같습니다.

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

범위 기반 루프는 **`for`** `statement` 범위 기반 루프 외부에 있는 [`break`](../cpp/break-statement-cpp.md) [`return`](../cpp/return-statement-cpp.md) [`goto`](../cpp/goto-statement-cpp.md) 레이블이 지정 된 문의, 또는 **`for`** 중 하나가 실행 될 때 종료 됩니다. [`continue`](../cpp/continue-statement-cpp.md)범위 기반 루프의 문은 **`for`** 현재 반복만 종료 합니다.

범위 기반에 대 한 다음 사항에 유의 하세요 **`for`** .

- 배열을 자동으로 인식합니다.

- `.begin()` 및 `.end()`가 포함된 컨테이너를 인식합니다.

- 기타 항목에 대해 `begin()` 및 `end()` 인수 종속성 조회를 사용합니다.

## <a name="see-also"></a>참고 항목

[`auto`](../cpp/auto-cpp.md)<br/>
[반복 문](../cpp/iteration-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[`while` Statement (C++)](../cpp/while-statement-cpp.md)<br/>
[`do-while` Statement (C++)](../cpp/do-while-statement-cpp.md)<br/>
[`for` Statement (C++)](../cpp/for-statement-cpp.md)
