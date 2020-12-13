---
description: '자세한 정보: 컴파일러 오류 C3026'
title: 컴파일러 오류 C3026
ms.date: 11/04/2016
f1_keywords:
- C3026
helpviewer_keywords:
- C3026
ms.assetid: 3297060e-cc5b-4600-a2db-09bfc4ffa21f
ms.openlocfilehash: e388fbaca270ab889b7873677ab2b2e8252780a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335070"
---
# <a name="compiler-error-c3026"></a>컴파일러 오류 C3026

'clause': 상수 식이 양수여야 합니다.

절에 정수 값을 전달했지만 값이 양수가 아닙니다. 숫자가 양수여야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3026을 생성합니다.

```cpp
// C3026.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main()
{
    int i;
    const int i1 = 0;

    #pragma omp parallel for num_threads(i1)   // C3026
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);

    #pragma omp parallel for num_threads(i1 + 1)   // OK
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);
}
```
