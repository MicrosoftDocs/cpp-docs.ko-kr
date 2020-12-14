---
description: '자세한 정보: 컴파일러 경고 (수준 1 및 수준 4) C4700'
title: 컴파일러 경고(수준 1 및 수준 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: 7ba19bdd6d8e25e095f796adc8cdb60b5cc8d325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241601"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>컴파일러 경고(수준 1 및 수준 4) C4700

> 초기화 되지 않은 '*name*' 지역 변수를 사용 합니다.

지역 변수 *이름이* *사용* 되었습니다. 즉, 값이 할당 되기 전에에서 읽습니다. C 및 c + +에서 지역 변수는 기본적으로 초기화 되지 않습니다. 초기화 되지 않은 변수에는 모든 값이 포함 될 수 있으며,이로 인해 정의 되지 않은 동작이 발생 합니다. 경고 C4700 거의 항상 프로그램에서 예기치 않은 결과 또는 충돌을 일으킬 수 있는 버그를 나타냅니다.

이 문제를 해결 하기 위해 선언 될 때 지역 변수를 초기화 하거나 사용 하기 전에 값을 할당할 수 있습니다. 함수를 사용 하 여 참조 매개 변수로 전달 된 변수를 초기화 하거나 해당 주소가 포인터 매개 변수로 전달 될 때 사용할 수 있습니다.

## <a name="example"></a>예제

이 샘플은 초기화 되기 전에 변수 t, u 및 v를 사용 하 고 발생할 수 있는 가비지 값의 종류를 표시 하는 경우 C4700을 생성 합니다. 변수 x, y 및 z는를 사용 하기 전에 초기화 되기 때문에 경고를 발생 시 키 지 않습니다.

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

이 코드가 실행 될 때 t, u 및 v는 초기화 되지 않으며 s에 대 한 출력을 예측할 수 없습니다.

```Output
Value in s: 37816963
Value in w: 42
```
