---
title: omp_get_num_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_get_num_threads OpenMP function
ms.assetid: e7c3cea1-44ac-435d-866e-2b7bc477e807
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 307fe1a1769db1bdcaf862c12ffef5507dfff64f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397639"
---
# <a name="ompgetnumthreads"></a>omp_get_num_threads

병렬 영역에서 스레드 수를 반환합니다.

## <a name="syntax"></a>구문

```
int omp_get_num_threads( );
```

## <a name="remarks"></a>설명

자세한 내용은 [3.1.2 omp_get_num_threads 함수](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)합니다.

## <a name="example"></a>예제

```
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="see-also"></a>참고 항목

[함수](../../../parallel/openmp/reference/openmp-functions.md)