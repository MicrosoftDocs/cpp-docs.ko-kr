---
description: '자세한 정보: 컴파일러 오류 C2875'
title: 컴파일러 오류 C2875
ms.date: 11/04/2016
f1_keywords:
- C2875
helpviewer_keywords:
- C2875
ms.assetid: d589fc0c-08b2-4a79-bc0e-dca5eb80bdd5
ms.openlocfilehash: 8d6d4d7f985079070cde4dfe46e3619cc035126f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320514"
---
# <a name="compiler-error-c2875"></a>컴파일러 오류 C2875

using 선언을 사용 하면 ' class:: identifier ' 선언이 여러 번 사용 됩니다.

선언으로 인해 동일한 항목이 두 번 정의 됩니다.

다음 샘플에서는 C2875를 생성 합니다.

```cpp
// C2875.cpp
struct A {
   void f(int*);
};

struct B {
   void f(double*);
};

struct AB : A, B {
   using A::f;
   using A::f;   // C2875
   using B::f;
};
```
