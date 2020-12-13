---
description: '자세히 알아보기: OpenMP 절'
title: OpenMP 절
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 3bdcb496238b2f8acef85819c43348c095293287
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342415"
---
# <a name="openmp-clauses"></a>OpenMP 절

OpenMP API에서 사용 되는 절에 대 한 링크를 제공 합니다.

Visual C++는 다음 OpenMP 절을 지원 합니다.

일반 특성의 경우:

|절|Description|
|------|-----------|
|[if](#if-openmp)|루프를 병렬로 실행할지 또는 순차적으로 실행할지를 지정 합니다.|
|[num_threads](#num-threads)|스레드 팀의 스레드 수를 설정 합니다.|
|[설정이](#ordered-openmp-clauses)|[순서가 지정](openmp-directives.md#ordered-openmp-directives) 된 지시문을 루프에서 사용 하는 경우 parallel [for](openmp-directives.md#for-openmp) 문에 필요 합니다.|
|[일정과](#schedule)|[For](openmp-directives.md#for-openmp) 지시문에 적용 됩니다.|
|[nowait](#nowait)|지시문에서 장벽을 암시적으로 재정의 합니다.|

데이터 공유 특성의 경우:

|절|Description|
|------|-----------|
|[private](#private-openmp)|각 스레드가 변수의 고유한 인스턴스를 갖도록 지정 합니다.|
|[firstprivate](#firstprivate)|각 스레드에 변수의 고유한 인스턴스가 있어야 하 고, 변수가 병렬 구문 앞에 있기 때문에 변수의 값을 사용 하 여 초기화 되어야 함을 지정 합니다.|
|[lastprivate](#lastprivate)|바깥쪽 컨텍스트의 변수 버전이 최종 반복 (for 루프 구문) 또는 마지막 섹션 (#pragma 섹션)을 실행 하는 모든 스레드의 전용 버전과 같도록 지정 합니다.|
|[공유할](#shared-openmp)|하나 이상의 변수를 모든 스레드 간에 공유 하도록 지정 합니다.|
|[default](#default-openmp)|병렬 영역에서 범위가 지정 되지 않은 변수의 동작을 지정 합니다.|
|[적](#reduction)|각 스레드에 대해 private 인 하나 이상의 변수가 병렬 영역의 끝에서 감소 작업의 대상이 되도록 지정 합니다.|
|[copyin](#copyin)|스레드가 [threadprivate](openmp-directives.md#threadprivate) 변수에 대해 마스터 스레드의 값에 액세스할 수 있도록 허용 합니다.|
|[copyprivate](#copyprivate)|하나 이상의 변수를 모든 스레드 간에 공유 하도록 지정 합니다.|

## <a name="copyin"></a><a name="copyin"></a> copyin

스레드가 [threadprivate](openmp-directives.md#threadprivate) 변수에 대해 마스터 스레드의 값에 액세스할 수 있도록 허용 합니다.

```cpp
copyin(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
`threadprivate`병렬 구문 앞에 있는 것 처럼 마스터 스레드에서 변수 값을 사용 하 여 초기화 되는 변수입니다.

### <a name="remarks"></a>설명

`copyin` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.7.2.7 copyin](../2-directives.md#2727-copyin)을 참조 하세요.

### <a name="example"></a>예제

사용에 대 한 예제는 [threadprivate](openmp-directives.md#threadprivate) 를 참조 하세요 `copyin` .

## <a name="copyprivate"></a><a name="copyprivate"></a> copyprivate

하나 이상의 변수를 모든 스레드 간에 공유 하도록 지정 합니다.

```cpp
copyprivate(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
공유할 변수를 하나 이상입니다. 둘 이상의 변수를 지정 하는 경우 변수 이름을 쉼표로 구분 합니다.

### <a name="remarks"></a>설명

`copyprivate`[단일](openmp-directives.md#single) 지시문에 적용 됩니다.

자세한 내용은 [2.7.2.8 copyprivate](../2-directives.md#2728-copyprivate)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default"></a><a name="default-openmp"></a> 기본

병렬 영역에서 범위가 지정 되지 않은 변수의 동작을 지정 합니다.

```cpp
default(shared | none)
```

### <a name="remarks"></a>설명

`shared`는 절이 지정 되지 않은 경우에 적용 되는입니다 `default` .는 병렬 영역의 모든 변수가 [shared](#shared-openmp) 절로 지정 된 것 처럼 처리 됨을 의미 합니다. `none` 는 [private](#private-openmp), [shared](#shared-openmp), [reduction](#reduction), [firstprivate](#firstprivate)또는 [a.6 lastprivate](#lastprivate) 절로 범위가 지정 되지 않은 병렬 영역에서 사용 되는 모든 변수에 컴파일러 오류가 발생 함을 의미 합니다.

`default` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.7.2.5 default](../2-directives.md#2725-default)를 참조 하세요.

### <a name="example"></a>예제

사용에 대 한 예제는 [private](#private-openmp) 을 참조 하십시오 `default` .

## <a name="firstprivate"></a><a name="firstprivate"></a> firstprivate

각 스레드에 변수의 고유한 인스턴스가 있어야 하 고, 변수가 병렬 구문 앞에 있기 때문에 변수의 값을 사용 하 여 초기화 되어야 함을 지정 합니다.

```cpp
firstprivate(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
각 스레드에 인스턴스를 포함 하 고, 병렬 구문 앞에 있기 때문에 변수의 값으로 초기화 되는 변수입니다. 둘 이상의 변수를 지정 하는 경우 변수 이름을 쉼표로 구분 합니다.

### <a name="remarks"></a>설명

`firstprivate` 다음 지시문에 적용 됩니다.

- [for](openmp-directives.md#for-openmp)
- [평행선](openmp-directives.md#parallel)
- [섹션이](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

자세한 내용은 [2.7.2.2 firstprivate](../2-directives.md#2722-firstprivate)를 참조 하세요.

### <a name="example"></a>예제

를 사용 하는 예제는 `firstprivate` [private](#private-openmp)의 예제를 참조 하세요.

## <a name="if-openmp"></a><a name="if-openmp"></a> if (OpenMP)

루프를 병렬로 실행할지 또는 순차적으로 실행할지를 지정 합니다.

```cpp
if(expression)
```

### <a name="parameters"></a>매개 변수

*expression*<br/>
True (0이 아님)로 평가 되는 경우 병렬 영역의 코드가 병렬로 실행 되도록 하는 정수 계열 식입니다. 식이 false (0)로 계산 되 면 병렬 지역은 단일 스레드를 통해 순차적으로 실행 됩니다.

### <a name="remarks"></a>설명

`if` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.3 병렬 구문](../2-directives.md#23-parallel-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a><a name="lastprivate"></a> a.6 lastprivate

바깥쪽 컨텍스트의 변수 버전이 최종 반복 (for 루프 구문) 또는 마지막 섹션 (#pragma 섹션)을 실행 하는 모든 스레드의 전용 버전과 같도록 지정 합니다.

```cpp
lastprivate(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
모든 스레드의 전용 버전과 동일 하 게 설정 된 변수는 최종 반복 (for 루프 구문) 또는 마지막 섹션 (#pragma 섹션)을 실행 합니다.

### <a name="remarks"></a>설명

`lastprivate` 다음 지시문에 적용 됩니다.

- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.7.2.3 a.6 lastprivate](../2-directives.md#2723-lastprivate)를 참조 하세요.

### <a name="example"></a>예제

Using 절의 예는 [일정](#schedule) 을 참조 하세요 `lastprivate` .

## <a name="nowait"></a><a name="nowait"></a> nowait

지시문에서 장벽을 암시적으로 재정의 합니다.

```cpp
nowait
```

### <a name="remarks"></a>설명

`nowait` 다음 지시문에 적용 됩니다.

- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

자세한 내용은 [2.4.1](../2-directives.md#241-for-construct), [2.4.2 sections sections](../2-directives.md#242-sections-construct)및 [2.4.3 single 구문을](../2-directives.md#243-single-construct)참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num_threads"></a><a name="num-threads"></a> num_threads

스레드 팀의 스레드 수를 설정 합니다.

```cpp
num_threads(num)
```

### <a name="parameters"></a>매개 변수

*num*<br/>
스레드 수

### <a name="remarks"></a>설명

절에는 `num_threads` [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 함수와 동일한 기능이 있습니다.

`num_threads` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.3 병렬 구문](../2-directives.md#23-parallel-construct)을 참조 하세요.

### <a name="example"></a>예제

Using 절의 예는 [parallel](openmp-directives.md#parallel) 을 참조 하십시오 `num_threads` .

## <a name="ordered"></a><a name="ordered-openmp-clauses"></a> 설정이

[순서가 지정](openmp-directives.md#ordered-openmp-directives) 된 지시문을 루프에서 사용 하는 경우 parallel [for](openmp-directives.md#for-openmp) 문에 필요 합니다.

```cpp
ordered
```

### <a name="remarks"></a>설명

`ordered`[for](openmp-directives.md#for-openmp) 지시문에 적용 됩니다.

자세한 내용은 [2.4.1 for 구문](../2-directives.md#241-for-construct)을 참조 하세요.

### <a name="example"></a>예제

Using 절의 예는 [정렬](openmp-directives.md#ordered-openmp-directives) 된을 참조 하십시오 `ordered` .

## <a name="private"></a><a name="private-openmp"></a> 문자

각 스레드가 변수의 고유한 인스턴스를 갖도록 지정 합니다.

```cpp
private(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
각 스레드에 대 한 인스턴스를 포함 하는 변수입니다.

### <a name="remarks"></a>설명

`private` 다음 지시문에 적용 됩니다.

- [for](openmp-directives.md#for-openmp)
- [평행선](openmp-directives.md#parallel)
- [섹션이](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

자세한 내용은 [2.7.2.1 private](../2-directives.md#2721-private)를 참조 하세요.

### <a name="example"></a>예제

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a><a name="reduction"></a> 적

각 스레드에 대해 private 인 하나 이상의 변수가 병렬 영역의 끝에서 감소 작업의 대상이 되도록 지정 합니다.

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>매개 변수

*operation*<br/>
병렬 영역의 끝에 있는 변수 *var* 에서 수행할 작업에 대 한 연산자입니다.

*var*<br/>
스칼라 감소를 수행 하는 하나 이상의 변수입니다. 둘 이상의 변수를 지정 하는 경우 변수 이름을 쉼표로 구분 합니다.

### <a name="remarks"></a>설명

`reduction` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.7.2.6 reduction](../2-directives.md#2726-reduction)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a><a name="schedule"></a> 일정과

[For](openmp-directives.md#for-openmp) 지시문에 적용 됩니다.

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>매개 변수

*type*<br/>
일정 유형 (,, `dynamic` 또는) `guided` 입니다 `runtime` `static` .

*size*<br/>
필드 반복의 크기를 지정 합니다. *크기* 는 정수 여야 합니다. *형식이* 인 경우 유효 하지 않습니다 `runtime` .

### <a name="remarks"></a>설명

자세한 내용은 [2.4.1 for 구문](../2-directives.md#241-for-construct)을 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared"></a><a name="shared-openmp"></a> 공유할

하나 이상의 변수를 모든 스레드 간에 공유 하도록 지정 합니다.

```cpp
shared(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
공유할 변수를 하나 이상입니다. 둘 이상의 변수를 지정 하는 경우 변수 이름을 쉼표로 구분 합니다.

### <a name="remarks"></a>설명

스레드 간에 변수를 공유 하는 또 다른 방법은 [copyprivate](#copyprivate) 절을 사용 하는 것입니다.

`shared` 다음 지시문에 적용 됩니다.

- [평행선](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [섹션이](openmp-directives.md#sections-openmp)

자세한 내용은 [2.7.2.4 shared](../2-directives.md#2724-shared)를 참조 하세요.

### <a name="example"></a>예제

사용에 대 한 예제는 [private](#private-openmp) 을 참조 하십시오 `shared` .
