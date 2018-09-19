---
title: 컴파일러 오류 C3175 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3175
dev_langs:
- C++
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b4ba372dd542bfb2c38435b6084b55d95b1bdf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043276"
---
# <a name="compiler-error-c3175"></a>컴파일러 오류 C3175

'function1': 관리 되지 않는 함수 'function2'에서 관리 되는 형식의 메서드를 호출할 수 없습니다

관리 되지 않는 함수는 관리 되는 클래스의 멤버 함수를 호출할 수 없습니다.

다음 샘플에서는 C3175를 생성합니다.

```
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
