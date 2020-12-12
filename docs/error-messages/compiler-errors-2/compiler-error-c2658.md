---
description: '자세한 정보: 컴파일러 오류 C2658'
title: 컴파일러 오류 C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 6f86bb2147d13a0192cb7272e3ac2f3f580b1493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286048"
---
# <a name="compiler-error-c2658"></a>컴파일러 오류 C2658

' member ': 익명 구조체/공용 구조체에서 재정의 합니다.

두 익명 구조체 또는 공용 구조체에 동일한 식별자를 사용 하지만 형식이 다른 멤버 선언이 포함 되어 있습니다. [/Za](../../build/reference/za-ze-disable-language-extensions.md)에서 식별자와 형식이 같은 멤버에 대해서도이 오류가 발생 합니다.

다음 샘플에서는 C2658를 생성 합니다.

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```
