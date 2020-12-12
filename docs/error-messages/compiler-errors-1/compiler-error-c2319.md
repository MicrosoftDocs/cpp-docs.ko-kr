---
description: '자세한 정보: 컴파일러 오류 C2319'
title: 컴파일러 오류 C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: 54ee91245b4346837e6cfbdac2c9ab979556bfdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268238"
---
# <a name="compiler-error-c2319"></a>컴파일러 오류 C2319

'try/catch'는 복합 문이 뒤에 와야 합니다. '{'가 없습니다.

또는 **`try`** **`catch`** 문 다음에 또는 블록을 찾을 수 없습니다 **`try`** **`catch`** . 블록은 중괄호로 묶어야 합니다.

다음 샘플에서는 C2319를 생성합니다.

```cpp
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```
