---
title: 컴파일러 오류 C3046
ms.date: 11/04/2016
f1_keywords:
- C3046
helpviewer_keywords:
- C3046
ms.assetid: 2e53d835-faa1-4ec0-9807-41f3dc552635
ms.openlocfilehash: cd7c934babe37def934b644ff4657ad63eb7676d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506225"
---
# <a name="compiler-error-c3046"></a>컴파일러 오류 C3046

OpenMP '#pragma omp sections' 영역에 구조화된 블록이 없습니다.

[섹션](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) 지시문에 빈 코드 블록이 있습니다.

다음 샘플에서는 C3046을 생성합니다.

```cpp
// C3046.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
/*
         ++n2;

         #pragma omp section
         {
            ++n3;
         }
*/
       }   // C3046 uncomment code to resolve this C3046
   }
}
```
