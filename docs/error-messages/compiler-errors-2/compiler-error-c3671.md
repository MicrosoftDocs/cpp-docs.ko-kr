---
description: '자세한 정보: 컴파일러 오류 C3671'
title: 컴파일러 오류 C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: a8fba0ccec84789b7fe5e45cd72b18abc3fe63b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228874"
---
# <a name="compiler-error-c3671"></a>컴파일러 오류 C3671

' function_1 ': 함수가 ' function_2 '을 (를) 재정의 하지 않습니다.

명시적 재정의 구문을 사용할 때 함수가 재정의 되지 않으면 컴파일러에서 오류를 생성 합니다.  자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3671를 생성 합니다.

```cpp
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```
