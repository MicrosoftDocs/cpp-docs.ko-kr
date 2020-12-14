---
description: '자세한 정보: 컴파일러 오류 C3648'
title: 컴파일러 오류 C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 532c65896ae5c3707c86735c661a095698417288
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203746"
---
# <a name="compiler-error-c3648"></a>컴파일러 오류 C3648

이 명시적 재정의 구문에는/clr: oldSyntax가 필요 합니다.

최신 관리 되는 구문을 컴파일하는 경우 컴파일러에서 더 이상 지원 되지 않는 이전 버전에 대 한 명시적 재정의 구문을 발견 했습니다.

자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3648를 생성 합니다.

```cpp
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
