---
description: '자세한 정보: 컴파일러 오류 C2064 오류가 발생'
title: 컴파일러 오류 C2064 오류가 발생
ms.date: 11/04/2016
f1_keywords:
- C2064
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
ms.openlocfilehash: dd9f0386267a81d4f92d6dd0474cd9a3292e7345
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328570"
---
# <a name="compiler-error-c2064"></a>컴파일러 오류 C2064 오류가 발생

항은 N개의 인수를 받아들이는 함수로 계산되지 않습니다.

식을 통해 함수가 호출됩니다. 식은 지정된 수의 인수를 사용하는 함수에 대한 포인터로 계산되지 않습니다.

이 예제에서는 코드가 비함수를 함수로 호출하려고 합니다. 다음 샘플에서는 C2064 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2064.cpp
int i, j;
char* p;
void func() {
   j = i();    // C2064, i is not a function
   p();        // C2064, p doesn't point to a function
}
```

개체 인스턴스의 컨텍스트에서 비정적 멤버 함수에 대한 포인터를 호출해야 합니다. 다음 샘플에서는 C2064 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2064b.cpp
struct C {
   void func1(){}
   void func2(){}
};

typedef void (C::*pFunc)();

int main() {
   C c;
   pFunc funcArray[2] = {&C::func1, &C::func2};
   (funcArray[0])();    // C2064
   (c.*funcArray[0])(); // OK - function called in instance context
}
```

클래스 내에서 멤버 함수 포인터도 호출 개체 컨텍스트를 나타내야 합니다. 다음 샘플에서는 C2064 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2064d.cpp
// Compile by using: cl /c /W4 C2064d.cpp
struct C {
   typedef void (C::*pFunc)();
   pFunc funcArray[2];
   void func1(){}
   void func2(){}
   C() {
      funcArray[0] = &C::func1;
      funcArray[1] = &C::func2;
   }
   void func3() {
      (funcArray[0])();   // C2064
      (this->*funcArray[0])(); // OK - called in this instance context
   }
};
```
