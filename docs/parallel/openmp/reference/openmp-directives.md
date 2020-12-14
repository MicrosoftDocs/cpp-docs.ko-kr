---
description: '자세히 알아보기: OpenMP 지시문'
title: OpenMP 지시문
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 03730b1f5cda0972dbf86b345c6e44bdad4e949b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342402"
---
# <a name="openmp-directives"></a>OpenMP 지시문

OpenMP API에서 사용 되는 지시문에 대 한 링크를 제공 합니다.

Visual C++는 다음 OpenMP 지시문을 지원 합니다.

병렬 작업 공유:

|지시문|설명|
|---------|-----------|
|[평행선](#parallel)|여러 스레드에서 동시에 실행 되는 코드 인 병렬 영역을 정의 합니다.|
|[for](#for-openmp)|`for`병렬 영역 내의 루프에서 수행 되는 작업을 스레드 간에 분할할 수 있습니다.|
|[섹션이](#sections-openmp)|모든 스레드 간에 나눌 코드 섹션을 식별 합니다.|
|[single](#single)|코드의 섹션이 마스터 스레드가 아닌 단일 스레드에서 실행 되도록 지정할 수 있습니다.|

Master 및 synchronization의 경우:

|지시문|설명|
|---------|-----------|
|[master](#master)|마스터 스레드만 프로그램의 특정 섹션을 실행 하도록 지정 합니다.|
|[업무용](#critical)|코드를 한 번에 하나의 스레드에서만 실행 하도록 지정 합니다.|
|[장벽](#barrier)|팀의 모든 스레드를 동기화 합니다. 모든 스레드는 모든 스레드가 장벽을 실행할 때까지 장벽에서 일시 중지 됩니다.|
|[원자적](#atomic)|원자 단위로 업데이트 되는 메모리 위치를 지정 합니다.|
|[플러시가](#flush-openmp)|모든 스레드가 모든 공유 개체에 대해 동일한 메모리 뷰를 갖도록 지정 합니다.|
|[설정이](#ordered-openmp-directives)|병렬화 된 루프의 코드를 `for` 순차 루프 처럼 실행 하도록 지정 합니다.|

데이터 환경:

|지시문|설명|
|---------|-----------|
|[threadprivate](#threadprivate)|변수가 스레드에 전용 임을 지정 합니다.|

## <a name="atomic"></a><a name="atomic"></a> 원자적

원자 단위로 업데이트 되는 메모리 위치를 지정 합니다.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>매개 변수

*expression*<br/>
하나 이상의 쓰기 로부터 보호 하려는 메모리 위치를 포함 하는 *lvalue* 를 포함 하는 문입니다.

### <a name="remarks"></a>설명

`atomic`지시문은 절을 지원 하지 않습니다.

자세한 내용은 [2.6.4 atomic 구문](../2-directives.md#264-atomic-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a> 장벽

팀의 모든 스레드를 동기화 합니다. 모든 스레드는 모든 스레드가 장벽을 실행할 때까지 장벽에서 일시 중지 됩니다.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>설명

`barrier`지시문은 절을 지원 하지 않습니다.

자세한 내용은 [2.6.3 장벽 지시어](../2-directives.md#263-barrier-directive)를 참조 하세요.

### <a name="example"></a>예제

를 사용 하는 방법에 대 한 샘플은 `barrier` [master](#master)를 참조 하세요.

## <a name="critical"></a><a name="critical"></a> 업무용

코드를 한 번에 하나의 스레드에서만 실행 하도록 지정 합니다.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*name*<br/>
필드 중요 한 코드를 식별 하는 이름입니다. 이름은 괄호로 묶어야 합니다.

### <a name="remarks"></a>설명

`critical`지시문은 절을 지원 하지 않습니다.

자세한 내용은 [2.6.2 critical critical 구문](../2-directives.md#262-critical-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a> 플러시가

모든 스레드가 모든 공유 개체에 대해 동일한 메모리 뷰를 갖도록 지정 합니다.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>매개 변수

*var*<br/>
필드 동기화 할 개체를 나타내는 쉼표로 구분 된 변수 목록입니다. *Var* 을 지정 하지 않으면 모든 메모리가 플러시됩니다.

### <a name="remarks"></a>설명

`flush`지시문은 절을 지원 하지 않습니다.

자세한 내용은 [2.6.5 flush 지시문](../2-directives.md#265-flush-directive)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a> 에 대 한

`for`병렬 영역 내의 루프에서 수행 되는 작업을 스레드 간에 분할할 수 있습니다.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>매개 변수

*절*<br/>
필드 절이 0 개 이상 있습니다. **설명** 부분을 참조 하십시오.

*for_statement*<br/>
`for`루프입니다. 루프의 사용자 코드가 `for` 인덱스 변수를 변경 하면 정의 되지 않은 동작이 발생 합니다.

### <a name="remarks"></a>설명

`for`지시문은 다음 절을 지원 합니다.

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [적](openmp-clauses.md#reduction)
- [설정이](openmp-clauses.md#ordered-openmp-clauses)
- [일정과](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

도 지정 된 경우를 제외 하 고는 `parallel` `clauses` 또는 지시문에서 허용 하는 모든 절이 될 수 있습니다 `parallel` `for` `nowait` .

자세한 내용은 [2.4.1 for 구문](../2-directives.md#241-for-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a> 마스터나

마스터 스레드만 프로그램의 특정 섹션을 실행 하도록 지정 합니다.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>설명

`master`지시문은 절을 지원 하지 않습니다.

[단일](#single) 지시문을 사용 하면 코드 섹션을 마스터 스레드가 아닌 단일 스레드에서 실행 하도록 지정할 수 있습니다.

자세한 내용은 [2.6.1 master 구문을](../2-directives.md#261-master-construct)참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a> 설정이

병렬화 된 루프의 코드를 `for` 순차 루프 처럼 실행 하도록 지정 합니다.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>설명

`ordered`지시문은 절을 사용 하 여 [에 대 한](#for-openmp) 의 동적 범위 내에 있어야 합니다 `parallel for` `ordered` .

`ordered`지시문은 절을 지원 하지 않습니다.

자세한 내용은 [2.6.6 정렬 된 구문](../2-directives.md#266-ordered-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a> 평행선

여러 스레드에서 동시에 실행 되는 코드 인 병렬 영역을 정의 합니다.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
필드 절이 0 개 이상 있습니다. **설명** 부분을 참조 하십시오.

### <a name="remarks"></a>설명

`parallel`지시문은 다음 절을 지원 합니다.

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [공유할](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [적](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`[for](#for-openmp) 및 [sections](#sections-openmp) 지시문과 함께 사용할 수도 있습니다.

자세한 내용은 [2.3 병렬 구문](../2-directives.md#23-parallel-construct)을 참조 하세요.

### <a name="example"></a>예제

다음 샘플에서는 스레드 수를 설정 하 고 병렬 영역을 정의 하는 방법을 보여 줍니다. 스레드 수는 기본적으로 컴퓨터의 논리적 프로세서 수와 동일 합니다. 예를 들어 하이퍼스레딩을 사용 하도록 설정 된 하나의 실제 프로세서를 포함 하는 컴퓨터가 있는 경우 두 개의 논리적 프로세서와 두 개의 스레드가 포함 됩니다. 출력 순서는 컴퓨터 마다 다를 수 있습니다.

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a> 섹션이

모든 스레드 간에 나눌 코드 섹션을 식별 합니다.

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
필드 절이 0 개 이상 있습니다. **설명** 부분을 참조 하십시오.

### <a name="remarks"></a>설명

`sections`지시문은 0 개 이상의 지시문을 포함할 수 있습니다 `section` .

`sections`지시문은 다음 절을 지원 합니다.

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [적](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

도 지정 된 경우를 제외 하 고는 `parallel` `clauses` 또는 지시문에서 허용 하는 모든 절이 될 수 있습니다 `parallel` `sections` `nowait` .

자세한 내용은 [2.4.2 sections sections 구문](../2-directives.md#242-sections-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a> 단

코드의 섹션이 마스터 스레드가 아닌 단일 스레드에서 실행 되도록 지정할 수 있습니다.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
필드 절이 0 개 이상 있습니다. **설명** 부분을 참조 하십시오.

### <a name="remarks"></a>설명

`single`지시문은 다음 절을 지원 합니다.

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[Master](#master) 지시어를 사용 하면 코드 섹션을 마스터 스레드에서만 실행 하도록 지정할 수 있습니다.

자세한 내용은 [2.4.3 single 구문](../2-directives.md#243-single-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a> threadprivate

변수가 스레드에 전용 임을 지정 합니다.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
스레드에 전용으로 지정할 변수를 쉼표로 구분한 목록입니다. *var* 은 전역 또는 네임 스페이스 범위 변수 또는 로컬 정적 변수 여야 합니다.

### <a name="remarks"></a>설명

`threadprivate`지시문은 절을 지원 하지 않습니다.

`threadprivate` 지시어는 [__declspec](../../../cpp/declspec.md) 키워드를 사용하는 [thread](../../../cpp/thread.md) 특성을 기반으로 합니다 .`__declspec(thread)`에 대한 제한은 `threadprivate`에 적용됩니다. 예를 들어, `threadprivate` 병렬 지역에서 생성 된 스레드 팀의 일부인 스레드만이 아니라 프로세스에서 시작 된 모든 스레드에 변수가 존재 합니다. 이 구현에 대해 자세히 알고 있어야 합니다. 사용자 정의 형식에 대 한 생성자가 `threadprivate` 예상 보다 더 자주 호출 될 수 있습니다.

프로세스를 시작할 때 정적으로 로드 되는 DLL에서는를 사용할 수 있지만/DELAYLOAD를 사용 하 여 로드 되는 dll `threadprivate` `threadprivate` (예: [로드 지연 가져오기)](../../../build/reference/delayload-delay-load-import.md)과 같은 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 를 통해 로드 되는 dll에서는를 사용할 수 없습니다 `LoadLibrary` .

`threadprivate` *소멸 가능한* 형식의 변수는 해당 소멸자를 호출 하는 것이 보장 되지 않습니다. 예를 들어:

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

사용자는 병렬 지역이 백업을 위해 스레드가 종료 될 때를 제어 하지 않습니다. 프로세스가 종료 될 때 이러한 스레드가 있으면 스레드에 프로세스가 종료 되었다는 알림이 표시 되지 않고 `threaded_var` 종료 된 스레드 (여기서는 주 스레드)를 제외한 모든 스레드에서 소멸자가 호출 되지 않습니다. 따라서 코드를 적절 하 게 소멸 시 코드를 계산 해서는 안 `threadprivate` 됩니다.

자세한 내용은 [2.7.1 threadprivate 지시문](../2-directives.md#271-threadprivate-directive)을 참조 하세요.

### <a name="example"></a>예제

사용에 대 한 샘플은 `threadprivate` [private](openmp-clauses.md#private-openmp)를 참조 하세요.
