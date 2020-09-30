---
title: 컴파일러 오류 C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 8cd27f492a72277c383afa5ca335a073b1a0519c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506392"
---
# <a name="compiler-error-c3042"></a>컴파일러 오류 C3042

OpenMP 'directive' 절에 'copyprivate'와 'nowait' 절을 함께 사용할 수 없습니다.

[copyprivate](../../parallel/openmp/reference/openmp-clauses.md#copyprivate) 및 [nowait](../../parallel/openmp/reference/openmp-clauses.md#nowait) 절은 지정된 지시문에서 함께 사용할 수 없습니다. 이 오류를 해결하려면 `copyprivate` 또는 `nowait` 절 중 하나 또는 둘 다를 제거합니다.

다음 샘플에서는 C3042를 생성합니다.

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
