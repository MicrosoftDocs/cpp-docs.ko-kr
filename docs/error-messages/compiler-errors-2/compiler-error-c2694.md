---
description: '자세한 정보: 컴파일러 오류 C2694'
title: 컴파일러 오류 C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4da5362a9c20a2bae10d2a201650f4312d455164
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326659"
---
# <a name="compiler-error-c2694"></a>컴파일러 오류 C2694

' override ': 재정의 가상 함수에 기본 클래스 가상 멤버 함수 ' base ' 보다 덜 제한적인 예외 사양이 있습니다.

가상 함수가 재정의 되었지만 [/za](../../build/reference/za-ze-disable-language-extensions.md)에서 재정의 하는 함수에 덜 제한적인 [예외 사양이](../../cpp/exception-specifications-throw-cpp.md)있습니다.

다음 샘플에서는 C2694를 생성 합니다.

```cpp
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```
