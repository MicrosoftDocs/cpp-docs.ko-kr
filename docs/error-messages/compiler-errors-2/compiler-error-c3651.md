---
description: '자세한 정보: 컴파일러 오류 C3651'
title: 컴파일러 오류 C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 03845059c1c99db7a228d2678148f768cb2e2c1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203720"
---
# <a name="compiler-error-c3651"></a>컴파일러 오류 C3651

' member ': 명시적 재정의로 사용할 수 없습니다. 기본 클래스의 멤버 여야 합니다.

명시적 재정의가 지정 되었지만 재정의 되는 함수가 기본 형식이 아닌 형식에 있습니다.

자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3651를 생성 합니다.

```cpp
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```
