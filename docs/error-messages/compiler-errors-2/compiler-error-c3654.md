---
description: '자세한 정보: 컴파일러 오류 C3654'
title: 컴파일러 오류 C3654
ms.date: 11/04/2016
f1_keywords:
- C3654
helpviewer_keywords:
- C3654
ms.assetid: 57d96e3f-6bbb-4eaa-934b-26c23b4ceb2e
ms.openlocfilehash: e3f5aee0031e398493b97e403159da64e891d2b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198286"
---
# <a name="compiler-error-c3654"></a>컴파일러 오류 C3654

' text ': 명시적 재정의에 구문 오류가 있습니다.

예기치 않은 문자열이 명시적으로 재정의 되었습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3654를 생성 합니다.

```cpp
// C3654.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f() = 0;
   virtual void g() = 0;
   virtual void h() = 0;
};

public ref struct Q : B {
   virtual void f() = B::f, 3 {}   // C3654
   // try the following line instead
   // virtual void g() = B::g, B::h {}
};
```
