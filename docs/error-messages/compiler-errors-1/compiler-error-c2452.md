---
title: 컴파일러 오류 C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 3e2d583efa2b634cf49d8588fa398bd81f24c607
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781109"
---
# <a name="compiler-error-c2452"></a>컴파일러 오류 C2452

'type': safe_cast의 형식이 잘못 된 원본

원본 유형이 [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) 올바르지 않습니다.  예를 들어, 모든 형식에는 `safe_cast` 작업에는 CLR 형식 이어야 합니다.

다음 샘플에서는 C2452 오류가 생성 됩니다.

```
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```