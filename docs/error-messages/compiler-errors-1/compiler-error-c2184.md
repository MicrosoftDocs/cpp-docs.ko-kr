---
description: '자세한 정보: 컴파일러 오류 C2184'
title: 컴파일러 오류 C2184
ms.date: 11/04/2016
f1_keywords:
- C2184
helpviewer_keywords:
- C2184
ms.assetid: 80fc8bff-7d76-4bde-94d2-01d84bb6824a
ms.openlocfilehash: 26513ff4162023398336eae3396e7be6abb8f8a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335148"
---
# <a name="compiler-error-c2184"></a>컴파일러 오류 C2184

'type': __except 식의 형식이 잘못되었습니다. 정수여야 합니다.

형식이 [__except](../../c-language/try-except-statement-c.md) 문에서 사용되었지만 형식이 허용되지 않습니다.

다음 샘플에서는 C2184를 생성합니다.

```cpp
// C2184.cpp
void f() {
   int * p;
   __try{}
   __except(p){};   // C2184
}
```

해결 방법:

```cpp
// C2184b.cpp
// compile with: /c
void f() {
   int i = 0;
   __try{}
   __except(i){};
}
```
