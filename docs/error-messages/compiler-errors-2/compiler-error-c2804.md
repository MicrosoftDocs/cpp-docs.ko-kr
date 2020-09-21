---
title: 컴파일러 오류 C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: bdd1b4155d30dd2513d87ac217ca20ca7baabd8a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743167"
---
# <a name="compiler-error-c2804"></a>컴파일러 오류 C2804

이항 'operator operator'에 매개 변수가 너무 많습니다.

오버로드된 이항 연산자 멤버 함수는 둘 이상의 매개 변수를 사용하여 선언됩니다. 형식이 연산자의 바깥쪽 형식인 이항 연산자 멤버 함수의 첫 번째 피연산자 매개 변수가 적용됩니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2804 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

다음 샘플에서는 C2804 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```
