---
description: '자세한 정보: 컴파일러 오류 C3243'
title: 컴파일러 오류 C3243
ms.date: 11/04/2016
f1_keywords:
- C3243
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
ms.openlocfilehash: 068987c8e15cc4904d782a5288dff4f7f69acace
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307213"
---
# <a name="compiler-error-c3243"></a>컴파일러 오류 C3243

오버로드 함수가 'interface'에 의해 하나도 정의되지 않았습니다.

지정된 인터페이스에 없는 멤버를 [명시적으로 재정의](../../cpp/explicit-overrides-cpp.md) 하려고 했습니다.

다음 샘플에서는 C3243을 생성합니다.

```cpp
// C3243.cpp
#pragma warning(disable:4199)
__interface IX14A {
   void g();
};

__interface IX14B {
   void f();
   void f(int);
};

class CX14 : public IX14A, public IX14B {
public:
   void IX14A::g();
   void IX14B::f();
   void IX14B::f(int);
};

void CX14::IX14A::f()   // C3243 occurs here
{
}
```
