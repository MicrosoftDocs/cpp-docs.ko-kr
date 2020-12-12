---
description: '자세한 정보: 컴파일러 오류 C3022'
title: 컴파일러 오류 C3022
ms.date: 11/04/2016
f1_keywords:
- C3022
helpviewer_keywords:
- C3022
ms.assetid: 9f1d444c-6c6e-48d9-9346-69128390aa33
ms.openlocfilehash: 66d9fa5e4eec93a1fcb4182c8c4e8672c586aa76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174366"
---
# <a name="compiler-error-c3022"></a>컴파일러 오류 C3022

'clause': OpenMP 'directive' 지시문에서 'value'의 예약 종류가 잘못되었습니다.

지원되지 않는 값이 절에 전달되었습니다.

다음 샘플에서는 C3022를 생성합니다.

```cpp
// C3022.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(10)   // C3022
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(x)   // C3022
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(runtime)
   for (i = 0; i < 10; ++i)
   ;
}
```
