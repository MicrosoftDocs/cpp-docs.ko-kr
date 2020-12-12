---
description: '자세한 정보: 컴파일러 오류 C3023'
title: 컴파일러 오류 C3023
ms.date: 11/04/2016
f1_keywords:
- C3023
helpviewer_keywords:
- C3023
ms.assetid: 89dcce98-3cd7-4931-a50f-87df1d2ebc9b
ms.openlocfilehash: e9cd560610327afe1dabc2b6899d1e0290779ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174340"
---
# <a name="compiler-error-c3023"></a>컴파일러 오류 C3023

'value': OpenMP 'clause' 절에 대한 인수에 예기치 못한 토큰이 있습니다.

절에 전달된 값이 잘못되었습니다.

다음 샘플에서는 C3023을 생성합니다.

```cpp
// C3023.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(dynamic 10)   // C3023
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(dynamic;10)   // C3023
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(dynamic, 10)
   for (i = 0; i < 10; ++i)
   ;
}
```
