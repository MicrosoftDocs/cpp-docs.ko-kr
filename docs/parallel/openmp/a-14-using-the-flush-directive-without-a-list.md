---
title: A.14   목록이 없는 flush 지시문 사용
ms.date: 11/04/2016
ms.assetid: 9e63141a-d0c6-43a5-ac16-b0bd7c89b871
ms.openlocfilehash: 13d50a6c0a3214297e931a7738305568596c3ae4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537594"
---
# <a name="a14---using-the-flush-directive-without-a-list"></a>A.14   목록이 없는 flush 지시문 사용

다음 예제에서는 (에 대 한 [2.6.5 섹션](../../parallel/openmp/2-6-5-flush-directive.md) 20 페이지) 영향을 받는 공유 개체를 구별를 `flush` 지시문에 영향을 받지는 공유 개체와에서 목록이 없습니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```