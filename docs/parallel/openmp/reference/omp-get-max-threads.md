---
title: omp_get_max_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_max_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_get_max_threads OpenMP function
ms.assetid: f47c3725-3e40-469f-8bc8-a1e47f264cc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 303e037d3fbeaf1958918c2ac78346bdcf01cf2a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695839"
---
# <a name="ompgetmaxthreads"></a>omp_get_max_threads
될 경우 병렬 영역 없이 사용할 수 있는 스레드 개수 보다 크거나 같은 정수를 반환 [num_threads](../../../parallel/openmp/reference/num-threads.md) 코드 내에서 해당 지점에서 정의 되었습니다.  
  
## <a name="syntax"></a>구문  
  
```  
int omp_get_max_threads( )  
```  
  
## <a name="remarks"></a>설명  
 자세한 내용은 참조 [3.1.3 omp_get_max_threads 함수](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)합니다.  
  
## <a name="example"></a>예제  
  
```  
// omp_get_max_threads.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_num_threads(8);  
    printf_s("%d\n", omp_get_max_threads( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
  
    #pragma omp parallel num_threads(3)  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
}  
```  
  
```Output  
8  
8  
8  
8  
8  
```  
  
## <a name="see-also"></a>참고 항목  
 [함수](../../../parallel/openmp/reference/openmp-functions.md)