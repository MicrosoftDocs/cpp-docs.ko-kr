---
title: 컴파일러 오류 C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: f3ef949b2651631f30a9c614a0d21b2668b7239f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653767"
---
# <a name="compiler-error-c3648"></a>컴파일러 오류 C3648

이 명시적 재정의 구문은 /clr: oldsyntax 필요

최신 관리 되는 구문에 대 한를 컴파일할 때 컴파일러에서 명시적 검색에 더 이상 지원 되지 않는 이전 버전에 대 한 구문을 재정의 합니다.

자세한 내용은 [명시적으로 재정의](../../windows/explicit-overrides-cpp-component-extensions.md)합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3648 오류가 생성 됩니다.

```
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```