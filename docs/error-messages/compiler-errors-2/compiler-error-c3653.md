---
description: '자세한 정보: 컴파일러 오류 C3653'
title: 컴파일러 오류 C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: 6f41d52416d2fee05873197efa60e4b888cf29f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320107"
---
# <a name="compiler-error-c3653"></a>컴파일러 오류 C3653

' function ': 명명 된 재정의로 사용할 수 없습니다. 재정의 되는 함수를 찾을 수 없습니다. :: 연산자를 사용 하 여 함수 이름을 명시적으로 지정할 수 있나요?

명시적 재정의에서 인터페이스에 없는 함수를 지정 했습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3653를 생성 합니다.

```cpp
// C3653.cpp
// compile with: /clr
public interface struct I {
   void h();
};

public ref struct X : public I {
   virtual void f() new sealed = J {};   // C3653 no J in scope
   virtual void g() {}   // OK
   virtual void h() new sealed = I::h {};   // OK
};
```
