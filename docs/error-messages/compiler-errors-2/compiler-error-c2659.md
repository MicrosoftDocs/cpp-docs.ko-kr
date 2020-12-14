---
description: '자세한 정보: 컴파일러 오류 C 2659'
title: 컴파일러 오류 C 2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 6a0f6c84e6bc279d9db75c423fdfc0d99b5ea769
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249674"
---
# <a name="compiler-error-c2659"></a>컴파일러 오류 C 2659

'operator' : 함수를 왼쪽 피연산자로 사용했습니다.

함수가 지정된 연산자의 왼쪽에 위치되었습니다. 이 오류의 가장 일반적인 이유는 개발자가 변수로 지정하려던 연산자 왼쪽의 식별자를 컴파일러가 함수로 구문 분석했기 때문입니다. 자세한 내용은 위키백과 문서 [가장 vexing 구문 분석](https://en.wikipedia.org/wiki/Most_vexing_parse)을 참조 하세요. 이 예제에서는 혼동하기 쉬운 함수 선언과 변수 정의를 보여 줍니다.

```cpp
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

이 문제를 해결하려면 식별자가 함수 선언으로 구문 분석되지 않도록 선언을 변경합니다.

오류 C2659는 속성의 형식이 지정된 연산자 왼쪽에 있는 식에 사용할 수 없는 경우에 발생할 수 있습니다. 이 예제에서는 코드가 함수에 함수 포인터를 할당하는 경우에 C2659를 생성합니다.

```cpp
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```
