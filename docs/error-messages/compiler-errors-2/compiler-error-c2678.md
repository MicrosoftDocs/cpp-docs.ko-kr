---
description: '자세한 정보: 컴파일러 오류 C 2678'
title: 컴파일러 오류 C 2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 9314d3d0201e38c2ce13b48f59356e04e0925a3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220866"
---
# <a name="compiler-error-c2678"></a>컴파일러 오류 C 2678

이항 'operator': 왼쪽 피연산자로 'type' 형식을 사용하는 연산자가 없거나 허용되는 변환이 없습니다.

연산자를 사용하려면 지정된 형식에 대해 오버로드하거나 연산자가 정의된 형식으로의 변환을 정의해야 합니다.

C2678은 왼쪽 피연산자가 const로 한정되었지만 연산자가 비const 인수를 사용하도록 정의된 경우 발생할 수 있습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2678을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

C2678은 멤버 함수를 호출하기 전에 네이티브 멤버를 고정하지 않은 경우에도 발생합니다.

다음 샘플에서는 C2678을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
