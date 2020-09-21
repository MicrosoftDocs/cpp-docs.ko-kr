---
title: 컴파일러 오류 C2171
ms.date: 11/04/2016
f1_keywords:
- C2171
helpviewer_keywords:
- C2171
ms.assetid: a80343b5-ab3f-4413-b6f1-3ce9d7e519e5
ms.openlocfilehash: da9e24b6b5857ca61a7eefc00a5ae455c59e8e44
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743401"
---
# <a name="compiler-error-c2171"></a>컴파일러 오류 C2171

'operator': 'type' 형식의 피연산자에는 맞지 않습니다.

단항 연산자가 잘못된 피연산자 형식과 함께 사용됩니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2171을 생성합니다.

```cpp
// C2171.cpp
int main() {
   double d, d1;
   d = ~d1;   // C2171

   // OK
   int d2 = 0, d3 = 0;
   d2 = ~d3;
}
```

다음 샘플에서는 C2171을 생성합니다.

```cpp
// C2171_b.cpp
// compile with: /c
class A {
public:
   A() { STF( &A::D ); }

   void D() {}
   void DTF() {
      (*TF)();   // C2171
      (this->*TF)();   // OK
   }

   void STF(void (A::*fnc)()) {
      TF = fnc;
   }

private:
   void (A::*TF)();
};
```
