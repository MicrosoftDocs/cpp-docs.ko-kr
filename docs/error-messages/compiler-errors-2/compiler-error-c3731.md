---
description: '자세한 정보: 컴파일러 오류 C3731'
title: 컴파일러 오류 C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 8a7ad836083a8c103df7becd7605a0dfd0efeea7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245085"
---
# <a name="compiler-error-c3731"></a>컴파일러 오류 C3731

호환 되지 않는 ' function1 ' 이벤트와 ' function2 ' 처리기 이벤트 원본 및 이벤트 처리기는 동일한 형식 이어야 합니다.

이벤트 소스와 이벤트 수신자는 형식이 동일해야 합니다(예:`native` 및 `com` 형식). 이 오류를 해결 하려면 이벤트 원본 및 이벤트 처리기의 형식을 일치 시킵니다.

다음 샘플에서는 C3731를 생성 합니다.

```cpp
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```
