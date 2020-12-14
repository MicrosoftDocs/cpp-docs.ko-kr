---
description: '자세한 정보: 컴파일러 오류 C3650'
title: 컴파일러 오류 C3650
ms.date: 11/04/2016
f1_keywords:
- C3650
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
ms.openlocfilehash: 02230eed0f1e3448bfc91d331611f28a7b6b7531
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203733"
---
# <a name="compiler-error-c3650"></a>컴파일러 오류 C3650

' interface_method ': 명시적 재정의로 사용할 수 없습니다. 기본 클래스의 가상 멤버 함수 여야 합니다.

가상이 아닌 멤버에 대해 명시적 재정의를 수행 하려고 했습니다.

자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3650를 생성 합니다.

```cpp
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```
