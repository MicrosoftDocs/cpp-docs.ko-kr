---
description: '자세한 정보: 컴파일러 오류 C2792'
title: 컴파일러 오류 C2792
ms.date: 11/04/2016
f1_keywords:
- C2792
helpviewer_keywords:
- C2792
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
ms.openlocfilehash: 5699f734574aaadd01aa6ddabac09facc249fb1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297761"
---
# <a name="compiler-error-c2792"></a>컴파일러 오류 C2792

' super ':이 키워드 다음에는 ':: '이와 야 합니다.

키워드 뒤에 올 수 있는 유일한 토큰 **`__super`** 은 `::` 입니다.

다음 샘플에서는 C2792를 생성 합니다.

```cpp
// C2792.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super.();   // C2792

      // try the following line instead
      // __super::mf();
   }
};
```
