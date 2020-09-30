---
title: 컴파일러 오류 C3047
ms.date: 11/04/2016
f1_keywords:
- C3047
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
ms.openlocfilehash: 41312e09996e2fe007cdc13c0369b5154e720841
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506223"
---
# <a name="compiler-error-c3047"></a>컴파일러 오류 C3047

OpenMP 'sections' 영역의 구조화된 블록 앞에는 '#pragma omp section'이 있어야 합니다.

코드 블록에서 [sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) 지시문이 생성한 모든 코드는 `section` 지시문이 생성한 코드 블록 안에 있어야 합니다.

다음 샘플에서는 C3047을 생성합니다.

```cpp
// C3047.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {

         #pragma omp section
         {
            ++n3;
         }

         ++n2;   // C3047 not enclosed in #pragma omp section
      }
   }
}
```
