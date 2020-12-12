---
description: '자세한 정보: 컴파일러 오류 C2602'
title: 컴파일러 오류 C2602
ms.date: 11/04/2016
f1_keywords:
- C2602
helpviewer_keywords:
- C2602
ms.assetid: 6c07a40e-537e-4954-b5c5-1e0e58fe1952
ms.openlocfilehash: 2922ee0d35dd5820e1df23d9bc812c0650501b35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312023"
---
# <a name="compiler-error-c2602"></a>컴파일러 오류 C2602

' class:: Identifier '는 ' class '의 기본 클래스의 멤버가 아닙니다.

`Identifier` 는 기본 클래스에서 상속 된 멤버가 아니므로 액세스할 수 없습니다.

다음 샘플에서는 C2602를 생성 합니다.

```cpp
// C2602.cpp
// compile with: /c
struct X {
   int x;
};
struct A {
   int a;
};
struct B : public A {
   X::x;   // C2602 B is not derived from X
   A::a;   // OK
};
```
