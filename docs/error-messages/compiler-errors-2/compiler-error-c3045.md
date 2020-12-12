---
description: '자세한 정보: 컴파일러 오류 C3045'
title: 컴파일러 오류 C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 0d39399d656a482d401eafb51f53c177c8c3bb2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269850"
---
# <a name="compiler-error-c3045"></a>컴파일러 오류 C3045

OpenMP 'sections' 지시문 다음에는 복합 문이 와야 합니다. '{'가 없습니다.

괄호로 구분된 코드 블록이 [sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) 지시문 뒤에 나와야 합니다.

다음 샘플에서는 C3045를 생성합니다.

```cpp
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```
