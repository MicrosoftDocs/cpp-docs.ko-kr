---
description: '자세한 정보: 컴파일러 오류 C3046'
title: 컴파일러 오류 C3046
ms.date: 11/04/2016
f1_keywords:
- C3046
helpviewer_keywords:
- C3046
ms.assetid: 2e53d835-faa1-4ec0-9807-41f3dc552635
ms.openlocfilehash: aee37f1f1921c62614dc5e40de4514403b92c91a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269811"
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
