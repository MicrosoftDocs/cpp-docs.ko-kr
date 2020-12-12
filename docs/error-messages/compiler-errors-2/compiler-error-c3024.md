---
description: '자세한 정보: 컴파일러 오류 C3024'
title: 컴파일러 오류 C3024
ms.date: 11/04/2016
f1_keywords:
- C3024
helpviewer_keywords:
- C3024
ms.assetid: 1c031c28-ce37-4de3-aead-cfe76b261856
ms.openlocfilehash: 840cbb173e6dd9fe5f5ebe76076b75883849f934
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174301"
---
# <a name="compiler-error-c3024"></a>컴파일러 오류 C3024

'schedule(runtime)' : chunk_size 식은 허용되지 않습니다.

schedule 절의 런타임 매개 변수에 값을 전달할 수 없습니다.

다음 샘플에서는 C3024를 생성합니다.

```cpp
// C3024.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(runtime, 10)   // C3024
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(runtime)   // OK
   for (i = 0; i < 10; ++i) ;
}
```
