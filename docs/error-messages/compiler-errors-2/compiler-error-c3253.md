---
description: '자세한 정보: 컴파일러 오류 C3253'
title: 컴파일러 오류 C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: 492530dfdfbd5b4b219dcee920fd4f4940393b3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194295"
---
# <a name="compiler-error-c3253"></a>컴파일러 오류 C3253

' function ': 명시적 재정의에 오류가 있습니다.

명시적 재정의가 잘못 지정 되었습니다. 예를 들어 순수로 지정 하는 재정의에 대 한 구현을 지정할 수 없습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3253를 생성 합니다.

```cpp
// C3253.cpp
// compile with: /clr
public interface struct I {
   void a();
   void b();
   void c();
};

public ref struct R : I {
   virtual void a() = 0, I::a {}   // C3253
   virtual void b() = I::a {}   // OK
   virtual void c() = 0;   // OK
};
```
