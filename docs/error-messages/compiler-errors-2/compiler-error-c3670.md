---
description: '자세한 정보: 컴파일러 오류 C3670'
title: 컴파일러 오류 C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: 499ef1a8f0638da7693ccdbdc0b02c0d5c86c59b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228939"
---
# <a name="compiler-error-c3670"></a>컴파일러 오류 C3670

' override ': 액세스할 수 없는 기본 클래스 메서드 ' method '를 재정의할 수 없습니다.

재정의는 액세스 수준을 파생 형식에서 사용할 수 있도록 하는 함수 에서만 수행할 수 있습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3670를 생성 합니다.

```cpp
// C3670.cpp
// compile with: /clr /c
public ref class C {
// Uncomment the following line to resolve.
// public:
   virtual void g() { }
};

public ref class D : public C {
public:
   virtual void f() new sealed = C::g {};   // C3670
};
```
