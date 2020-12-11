---
description: 다음에 대해 자세히 알아보세요. `noalias`
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 56306404fc79ea851835ae5913bbdb0b297ba880
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161653"
---
# `noalias`

**Microsoft 전용**

**`noalias`** 는 함수 호출에서 표시 되는 전역 상태를 수정 하거나 참조 하지 않으며 포인터 매개 변수 (첫 번째 수준의 간접 참조)로 *직접* 가리키는 메모리를 수정 하지 않음을 의미 합니다.

함수에로 주석이 지정 된 경우 **`noalias`** 최적화 프로그램은 매개 변수 자체와 포인터 매개 변수의 첫 번째 수준 간접 참조만 함수 내에서 참조 되거나 수정 된다고 가정할 수 있습니다.

**`noalias`** 주석은 주석이 추가 된 함수의 본문 내 에서만 적용 됩니다. 함수를로 표시 하면 **`__declspec(noalias)`** 함수에서 반환 하는 포인터의 앨리어싱에 영향을 주지 않습니다.

별칭에 영향을 줄 수 있는 다른 주석은를 참조 하십시오 [`__declspec(restrict)`](../cpp/restrict.md) .

## <a name="example"></a>예제

다음 샘플에서는를 사용 하는 방법을 보여 줍니다 **`__declspec(noalias)`** .

`multiply`메모리에 액세스 하는 함수에 주석이 추가 되 면 **`__declspec(noalias)`** 이 함수는 매개 변수 목록에서 포인터를 제외 하 고 전역 상태를 수정 하지 않음을 컴파일러에 알립니다.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>참고 항목

[`__declspec`](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
