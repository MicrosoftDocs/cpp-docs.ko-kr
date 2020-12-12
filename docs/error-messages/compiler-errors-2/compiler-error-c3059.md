---
description: '자세한 정보: 컴파일러 오류 C3059'
title: 컴파일러 오류 C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: 82629fb77a0cf589f4e311d951fcf1540e0b7c8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281758"
---
# <a name="compiler-error-c3059"></a>컴파일러 오류 C3059

'var': 'threadprivate' 기호는 'clause' 절에서 사용할 수 없습니다.

[threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 기호가 절에서 사용되었습니다.

다음 샘플에서는 C3059를 생성합니다.

```cpp
// C3059.cpp
// compile with: /openmp
#include "omp.h"
int x, y;
#pragma omp threadprivate(x, y)

int main() {
   #pragma omp parallel private(x, y)   // C3059
   {
      x = y;
   }
}
```

해결 방법:

```cpp
// C3059b.cpp
// compile with: /openmp
#include "omp.h"
int x = 0, y = 0;

int main() {
   #pragma omp parallel firstprivate(y) private(x)
   {
      x = y;
   }
}
```
