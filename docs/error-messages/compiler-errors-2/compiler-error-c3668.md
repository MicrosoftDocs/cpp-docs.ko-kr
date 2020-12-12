---
description: '자세한 정보: 컴파일러 오류 C3668'
title: 컴파일러 오류 C3668
ms.date: 11/04/2016
f1_keywords:
- C3668
helpviewer_keywords:
- C3668
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
ms.openlocfilehash: a13de2f8ea1ca9c8bf6d66483c777d74675fef9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269499"
---
# <a name="compiler-error-c3668"></a>컴파일러 오류 C3668

' method ': 재정의 지정자 ' override '가 있는 메서드가 기본 클래스 메서드를 재정의 하지 않았습니다.

함수가 존재 하지 않는 함수를 재정의 하려고 했습니다.

자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3668를 생성 합니다.

```cpp
// C3668.cpp
// compile with: /c
__interface I {
   void f(int);   // virtual by default
};

class J {
public:
   void g(int);
   virtual void h(int);
};

struct R : I,J {
   virtual void f() override {}   // C3668
   virtual void f(int) override {}   // OK

   virtual void g(int) override {}   // C3668
   virtual void h(int) override {}   // OK
};
```
