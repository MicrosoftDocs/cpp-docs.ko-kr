---
description: '자세한 정보: 컴파일러 오류 C3175'
title: 컴파일러 오류 C3175
ms.date: 11/04/2016
f1_keywords:
- C3175
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
ms.openlocfilehash: 278d8de3d18aaa3437f4d2c0b1d8c9e3306630a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242082"
---
# <a name="compiler-error-c3175"></a>컴파일러 오류 C3175

' function1 ': 관리 되는 형식의 메서드를 관리 되지 않는 함수 ' function2 '에서 호출할 수 없습니다.

관리 되지 않는 함수는 관리 되는 클래스의 멤버 함수를 호출할 수 없습니다.

다음 샘플에서는 C3175를 생성 합니다.

```cpp
// C3175_2.cpp
// compile with: /clr

ref struct A {
   static void func() {
   }
};

#pragma unmanaged   // remove this line to resolve

void func2() {
   A::func();   // C3175
}

#pragma managed

int main() {
   A ^a = gcnew A;
   func2();
}
```
