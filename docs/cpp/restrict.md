---
description: '자세히 알아보기: 제한'
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: e2900e46d3b8e452661800c1c511418f936a5b0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223713"
---
# <a name="restrict"></a>restrict

**Microsoft 전용**

포인터 형식을 반환 하는 함수 선언 또는 정의에 적용 되는 경우 **`restrict`** 함수는 *별칭이* 지정 되지 않은 개체 (즉, 다른 포인터에서 참조 됨)를 반환 한다는 것을 컴파일러에 알립니다. 이렇게 하면 컴파일러가 추가 최적화를 수행할 수 있습니다.

## <a name="syntax"></a>Syntax

> **`__declspec(restrict)`***pointer_return_type* *함수*();

## <a name="remarks"></a>설명

컴파일러가 전파 **`__declspec(restrict)`** 합니다. 예를 들어 CRT 함수에는 `malloc` **`__declspec(restrict)`** 장식이 있으므로 컴파일러는에서 메모리 위치로 초기화 된 포인터가 `malloc` 이전 기존 포인터로 별칭이 지정 되지 않은 것으로 간주 합니다.

컴파일러는 반환 된 포인터가 실제로 별칭이 지정 되지 않았는지 확인 하지 않습니다. 프로그램이 **restrict __declspec** 한정자로 표시 된 포인터에 별칭을 사용 하지 않는지 확인 하는 것은 개발자의 책임입니다.

변수에 대 한 유사한 의미 체계는 [__restrict](../cpp/extension-restrict.md)를 참조 하세요.

함수 내의 앨리어싱에 적용 되는 다른 주석은 [__declspec (noalias)](../cpp/noalias.md)를 참조 하세요.

C++ AMP의 일부인 키워드에 대 한 자세한 내용은 **`restrict`** [restrict (C++ AMP)](../cpp/restrict-cpp-amp.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는를 사용 하는 방법을 보여 줍니다 **`__declspec(restrict)`** .

**`__declspec(restrict)`** 가 포인터를 반환 하는 함수에 적용 되 면이는 반환 값이 가리키는 메모리에 별칭이 지정 되지 않음을 컴파일러에 알립니다. 이 예제에서 및 포인터는 `mempool` `memptr` 전역 이므로 컴파일러가 참조 하는 메모리에 별칭이 지정 되지 않았는지 확인할 수 없습니다. 그러나 이러한 메서드는 프로그램에서 `ma` 참조 하지 않는 메모리를 반환 하는 방식으로 및 해당 호출자 내에서 사용 됩니다 `init` . 따라서 최적화 프로그램을 지원 하기 위해 **__decslpec (restrict)** 를 사용 합니다. 이는를 `malloc` 사용 하 여 **`__declspec(restrict)`** 기존 포인터로 별칭을 지정할 수 없는 메모리를 항상 반환 한다는 것을 나타내기 위해를 사용 하는 등의 방법으로 CRT 헤더에서 할당 함수를 데코레이팅하는 방법과 비슷합니다.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec (noalias)](../cpp/noalias.md)
