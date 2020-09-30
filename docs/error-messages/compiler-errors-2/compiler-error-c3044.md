---
title: 컴파일러 오류 C3044
ms.date: 11/04/2016
f1_keywords:
- C3044
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
ms.openlocfilehash: 0ac2a6a86ffd719dbb5f39fc085d3f5cbca0567d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506360"
---
# <a name="compiler-error-c3044"></a>컴파일러 오류 C3044

'section' : OpenMP 'sections' 지시문 내부에 직접 중첩되어야 합니다.

컴파일러에서 `section` 지시문이 잘못 사용된 것을 발견했습니다. 자세한 내용은 [섹션](../../parallel/openmp/reference/openmp-directives.md#sections-openmp)을 참조하세요.

다음 샘플에서는 C3044를 생성합니다.

```cpp
// C3044.cpp
// compile with: /openmp /c
#include "omp.h"
int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         ++n2;
      }

      #pragma omp section   // C3044
      {
         ++n3;
      }
   }

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         #pragma omp section   // OK
         {
            ++n3;
         }
      }
   }
}
```
