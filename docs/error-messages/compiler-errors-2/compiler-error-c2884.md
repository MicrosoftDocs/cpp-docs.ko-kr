---
description: '자세한 정보: 컴파일러 오류 C2884'
title: 컴파일러 오류 C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: 008c72ba24bdea260fffc4a49145ecf67c610b15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332325"
---
# <a name="compiler-error-c2884"></a>컴파일러 오류 C2884

' name ': using 선언에 의해 정의 된 ' function ' 지역 함수와 충돌 합니다.

함수를 두 번 이상 정의 하려고 했습니다. 첫 번째 정의는 로컬 정의입니다. 두 번째는 선언이 포함 된 네임 스페이스에서 가져온 것입니다 **`using`** .

다음 샘플에서는 C2884를 생성 합니다.

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
