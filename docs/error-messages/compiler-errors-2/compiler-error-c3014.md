---
description: '자세한 정보: 컴파일러 오류 C3014'
title: 컴파일러 오류 C3014
ms.date: 11/04/2016
f1_keywords:
- C3014
helpviewer_keywords:
- C3014
ms.assetid: af1c5b0c-dbf9-4274-b06a-c6c2cdcf2a52
ms.openlocfilehash: 1e53e7b1cfd71e2fe58d029c8b4aa6074c0e0038
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285892"
---
# <a name="compiler-error-c3014"></a>컴파일러 오류 C3014

OpenMP 'directive' 지시문 다음에 for 루프가 와야 합니다.

루프 이외의 항목에서 지시문 바로 뒤에 오는 것은 오류입니다 **`for`** `#pragma omp for` .

다음 샘플에서는 C3014를 생성합니다.

```cpp
// C3014.cpp
// compile with: /openmp
int main()
{
   int i = 0;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // OK
      {
      }
   }

   #pragma omp parallel for
   for (i = 0; i < 10; ++i)   // OK
   {
   }

   #pragma omp parallel
   {
      #pragma omp for
      {   // C3014
         for (i = 0; i < 10; ++i)
         {
         }
      }
   }

   #pragma omp parallel for
   {   // C3014
      for (i = 0; i < 10; ++i)
      {
      }
   }

   #pragma omp parallel
   {
      #pragma omp for
      i *= 2;   // C3014
      for (i = 0; i < 10; ++i)
      {
      }
   }

   #pragma omp parallel for
   i *= 2;   // C3014
   for (i = 0; i < 10; ++i)
   {
   }
}
```
