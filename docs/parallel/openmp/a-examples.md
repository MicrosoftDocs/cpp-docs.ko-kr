---
description: '다음에 대 한 자세한 정보: A. 예'
title: A. 예제
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: d52b59f9f83cf791c03fb49ca726273a2c977e58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342545"
---
# <a name="a-examples"></a>A. 예제

다음은이 문서에 정의 된 구문의 예입니다. 지시문 뒤에 오는 문은 필요한 경우에만 복합 이며 복합 문이 앞의 지시문에서 들여쓰기 됩니다.

## <a name="a1-a-simple-loop-in-parallel"></a>1.1은 간단한 루프를 병렬로 실행 합니다.

다음 예에서는 [parallel for](2-directives.md#251-parallel-for-construct) 지시문을 사용 하 여 루프를 병렬화 하는 방법을 보여 줍니다. 루프 반복 변수는 기본적으로 private 이므로 private 절에서 명시적으로 지정할 필요가 없습니다.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>1.2 조건부 컴파일

다음 예에서는 [_OPENMP](2-directives.md#22-conditional-compilation)OpenMP 매크로를 사용 하 여 조건부 컴파일을 사용 하는 방법을 보여 줍니다. OpenMP 컴파일을 사용 하면 `_OPENMP` 매크로가 정의 됩니다.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

정의 된 전처리기 연산자를 사용 하면 단일 지시문에서 둘 이상의 매크로를 테스트할 수 있습니다.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>3.3 병렬 지역

[병렬](2-directives.md#23-parallel-construct) 지시문은 정교 하지 않은 병렬 프로그램에서 사용할 수 있습니다. 다음 예제에서 병렬 영역의 각 스레드는 `x` 스레드 번호에 따라 작업할 전역 배열의 일부를 결정 합니다.

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>Nowait 절

병렬 지역 내에 독립적인 루프가 많은 경우 다음과 같이 [nowait](2-directives.md#241-for-construct) 절을 사용 하 여 지시문의 끝에 묵시적 장벽을 피할 수 있습니다 `for` .

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A. 5 임계 지시문

다음 예제에는 몇 가지 [중요 한](2-directives.md#262-critical-construct) 지시문이 포함 되어 있습니다. 이 예에서는 태스크가 큐에서 제거 되 고 작동 하는 큐 모델을 보여 줍니다. 동일한 작업을 큐에서 해제 하는 많은 스레드를 보호 하려면 큐에서 제거할 작업이 섹션에 있어야 합니다 `critical` . 이 예제의 두 큐는 독립적 이기 때문에 `critical` 다른 이름, *x 축* 및 *yaxis* 를 사용 하는 지시문에 의해 보호 됩니다.

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>6. a.6 lastprivate 절

올바른 실행은 루프의 마지막 반복이 변수에 할당 하는 값에 따라 달라질 수 있습니다. 이러한 프로그램은 루프를 순차적으로 실행 하는 경우와 같은 변수 값이 되도록 [a.6 lastprivate](2-directives.md#2723-lastprivate) 절의 인수로 이러한 변수를 모두 나열 해야 합니다.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

위의 예제에서 병렬 영역의 끝에 있는 값은 `i` `n-1` 순차적 사례에서와 같이 동일 하 게 됩니다.

## <a name="a7-the-reduction-clause"></a>.7 reduction 절

다음 예에서는 [reduction](2-directives.md#2726-reduction) 절을 보여 줍니다.

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>8 개의 병렬 섹션

다음 예에서는 ( [섹션 2.4.2 sections](2-directives.md#242-sections-construct))에서 함수 *x 축*, *yaxis* 및 *zaxis* 를 동시에 실행할 수 있습니다. 첫 번째 `section` 지시문은 선택 사항입니다.  모든 `section` 지시문이 구문의 어휘 범위에 표시 되어야 `parallel sections` 합니다.

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A. 9 단일 지시문

다음 예에서는 [단일](2-directives.md#243-single-construct) 지시문을 보여 줍니다. 이 예제에서는 하나의 스레드 (일반적으로 지시문을 발견 하는 첫 번째 스레드 `single` )만 진행률 메시지를 인쇄 합니다. 사용자는 섹션을 실행 하는 스레드에 대 한 가정을 하지 않아야 합니다 `single` . 다른 모든 스레드는 섹션을 건너뛰고 `single` 구문 끝의 장벽에서 중지 합니다 `single` . 섹션을 실행 하는 스레드를 기다리지 않고 다른 스레드를 계속 진행할 수 있는 경우 `single` `nowait` 지시문에 절을 지정할 수 있습니다 `single` .

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>10 개의 순차적 순서 지정

[순서가 지정 된 섹션](2-directives.md#266-ordered-construct) 은 병렬로 수행 된 작업의 출력 순서를 순차적으로 지정 하는 데 유용 합니다. 다음 프로그램은 인덱스를 순차적인 순서로 출력 합니다.

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>11.11 스레드의 고정 된 수

일부 프로그램은 올바르게 실행 하기 위해 고정 된 미리 지정 된 수의 스레드를 사용 합니다.  스레드 수를 동적으로 조정 하는 기본 설정은 구현에 정의 되어 있기 때문에 이러한 프로그램은 동적 스레드 기능을 해제 하 고 스레드 수를 명시적으로 설정 하 여 이식성을 유지 하도록 선택할 수 있습니다. 다음 예제에서는 [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)및 [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)를 사용 하 여이 작업을 수행 하는 방법을 보여 줍니다.

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

이 예제에서 프로그램은 16 개 스레드로 실행 되는 경우에만 올바르게 실행 됩니다. 구현에서 16 개의 스레드를 지원할 수 없는 경우이 예제의 동작은 구현에 정의 되어 있습니다.

병렬 영역을 실행 하는 스레드 수는 동적 스레드 설정에 관계 없이 병렬 영역 중에 일정 하 게 유지 됩니다. 동적 스레드 메커니즘은 병렬 영역 시작 시 사용할 스레드 수를 결정 하 고 영역 지속 시간에 대해 상수를 유지 합니다.

## <a name="a12-the-atomic-directive"></a>12. 원자성 지시문

다음 예제에서는 [atomic](2-directives.md#264-atomic-construct) 지시어를 사용 하 여 경합 상태 (여러 스레드를 통해 *x* 의 요소를 동시에 업데이트)를 방지 합니다.

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

`atomic`이 예제에서 지시문을 사용 하면 x의 서로 다른 두 요소에 대 한 업데이트가 병렬로 수행 될 수 있다는 장점이 있습니다. [임계](2-directives.md#262-critical-construct) 지시문을 대신 사용 하면 *x* 의 요소에 대 한 모든 업데이트가 순차적으로 실행 됩니다 (보장 된 순서는 아님).

`atomic`지시문은 바로 뒤에 오는 c 또는 c + + 문에만 적용 됩니다.  따라서이 예제에서는 *y* 의 요소가 원자 단위로 업데이트 되지 않습니다.

## <a name="a13-a-flush-directive-with-a-list"></a>A. 13-목록이 있는 flush 지시문

다음 예에서는 `flush` 스레드 쌍 간에 특정 개체의 지점 간 동기화에 대 한 지시문을 사용 합니다.

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A. 14 목록 없이 플러시 지시문

다음 예제 ( [2.6.5 섹션](2-directives.md#265-flush-directive))는 지시문에 의해 영향을 받지 `flush` 않는 공유 개체의 목록이 없는 공유 개체를 구분 합니다.

```cpp
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

## <a name="a15-the-number-of-threads-used"></a>5.15 사용 된 스레드 수

다음과 같은 잘못 된 예를 고려해 보세요 ( [3.1.2 섹션](3-run-time-library-functions.md#312-omp_get_num_threads-function)).

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`이 호출은 코드의 일련 섹션에서 1을 반환 하므로 앞의 예제에서 *np* 는 항상 1과 같습니다. 병렬 영역에 대해 배포할 스레드 수를 결정 하려면 호출이 병렬 영역 내에 있어야 합니다.

다음 예제에서는 스레드 수에 대 한 쿼리를 포함 하지 않고이 프로그램을 다시 작성 하는 방법을 보여 줍니다.

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>16 잠금

다음 예제에서 ( [3.2 섹션](3-run-time-library-functions.md#32-lock-functions)) lock 함수에 대 한 인수는 형식 이어야 `omp_lock_t` 하며 플러시할 필요가 없습니다.  잠금 함수를 사용 하면 첫 번째 임계 영역에 대 한 항목을 기다리는 동안 스레드가 유휴 상태가 되 고, 두 번째 임계 항목에 대 한 항목을 기다리는 동안 다른 작업을 수행할 수 있습니다.  `omp_set_lock`함수는를 차단 하지만 `omp_test_lock` 함수는의 작업을 수행할 수 있도록 합니다 `skip()` .

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>17ne안정 잠금

다음 예제 ( [3.2 섹션](3-run-time-library-functions.md#32-lock-functions))에서는 a.17 중첩 가능 잠금을 사용 하 여 전체 구조와 해당 멤버 중 하나에 업데이트를 동기화 할 수 있는 방법을 보여 줍니다.

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>.18 개의 중첩 된 지시문

다음 `for` [지시문 중첩](2-directives.md#29-directive-nesting) 예제는 내부 및 외부 `for` 지시문이 서로 다른 병렬 영역에 바인딩되도록 하므로 호환 됩니다.

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

위의 예제에서 다음과 같은 변형도 준수 합니다.

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A. 작업 공유 지시문의 잘못 된 중첩을 보여 주는 19 개의 예제

이 단원의 예제에서는 [지시문 중첩](2-directives.md#29-directive-nesting) 규칙을 보여 줍니다.

다음 예제는 내부 및 외부 지시문이 중첩 되어 `for` 동일한 지시문에 바인딩되어 있기 때문에 호환 되지 않습니다 `parallel` .

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

이전 예제의 다음 동적 중첩 버전은 비준수 이기도 합니다.

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

다음 예제는 `for` 및 지시문이 중첩 되어 있고 `single` 동일한 병렬 영역에 바인딩 되었으므로 호환 되지 않습니다.

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

다음 예제는의 `barrier` 지시문이 `for` 교착 상태를 발생 시킬 수 있기 때문에 비규격입니다.

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

다음 예제는 한 `barrier` 번에 하나의 스레드만 임계 영역에 들어갈 수 있으므로 교착 상태가 발생 하기 때문에 호환 되지 않습니다.

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

다음 예제는 `barrier` 하나의 스레드만 섹션을 실행 한다는 사실 때문에 교착 상태가 발생 하기 때문에 비준수입니다 `single` .

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>20 개의 바인드 장벽 지시문

지시문 바인딩 규칙은 지시문을 호출 `barrier` 하 여 가장 가까운 바깥쪽 지시문에 바인딩합니다 `parallel` . 지시문 바인딩에 대 한 자세한 내용은 [섹션 2.8](2-directives.md#28-directive-binding)을 참조 하세요.

다음 예제에서는  (  `barrier` *sub3*)가 *sub2* 의 병렬 영역에 바인딩되기 때문에 main에서 sub2으로의 호출은 규격입니다. 가  서브루틴  `barrier` *sub2* 의 병렬 영역에 바인딩되기 때문에 main에서 sub1으로의 호출은 규격을 준수 합니다.  가 병렬 영역에 바인딩하지 않고 무시 되므로 *main* 에서 *sub3* 으로의 호출은 규격입니다 `barrier` . 또한은 (는)는 `barrier` 바깥쪽 병렬 지역의 스레드 팀만 동기화 하 고 *sub1* 에 생성 된 모든 스레드는 동기화 하지 않습니다.

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>.21 범위 변수 (private 절 포함)

`i`다음 예제에서 및의 값은 `j` 병렬 지역에서 종료 될 때 정의 되지 않습니다.

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

절에 대 한 자세한 내용은 `private` [2.7.2.1 섹션](2-directives.md#2721-private)을 참조 하세요.

## <a name="a22-the-defaultnone-clause"></a>A. 22 기본 (none) 절

다음 예에서는 절에 의해 영향을 받는 변수를 `default(none)` 이 아닌 변수를 구분 합니다.

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

절에 대 한 자세한 내용은 `default` [2.7.2.5 섹션](2-directives.md#2725-default)을 참조 하세요.

## <a name="a23-examples-of-the-ordered-directive"></a>A. 23의 정렬 된 지시문 예제

절을 사용 하 여 지정 된 여러 개의 정렬 된 섹션이 있을 수 있습니다 `for` `ordered` . API가 다음 규칙을 지정 하기 때문에 첫 번째 예제는 비준수입니다.

"구문을 사용한 루프의 반복은 `for` 동일한 지시문을 두 번 이상 실행 해서는 안 `ordered` 되며 둘 이상의 지시문을 실행 해서는 안 `ordered` 됩니다." [2.6.6 섹션](2-directives.md#266-ordered-construct)을 참조 하세요.

이 비규격 예제에서는 모든 반복이 두 개의 정렬 된 섹션을 실행 합니다.

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

다음 호환 예제에서는 두 개 `for` 이상의 정렬 된 섹션이 있는을 보여 줍니다.

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>Private 절의 24 가지 예

병렬 영역의 [private](2-directives.md#2721-private) 절은 영역의 동적 범위가 아니라 영역의 어휘 범위에만 적용 됩니다.  따라서 다음 예제에서는 루틴 f의 루프 내에서 변수 *a* 를 사용 하는 경우 `for` 의 전용 복사본  을 참조 하 고, 루틴 *g* 의 사용량은 전역 *a* 를 참조 합니다. 

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>Copyprivate data attribute 절의 25 가지 예

**예 1:** [Copyprivate](2-directives.md#2728-copyprivate) 절을 사용 하 여 단일 스레드에서 획득 한 값을 다른 스레드에서 전용 변수의 모든 인스턴스에 직접 브로드캐스트할 수 있습니다.

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

순차 지역에서 루틴 *init* 를 호출 하는 경우에는 해당 동작이 지시문의 존재에 영향을 받지 않습니다. 한 스레드에서 *get_values* 루틴에 대 한 호출을 실행 한 후에 *는* 모든 스레드에서 a, *b*, *x* 및 *y* 로 지정 된 개인 개체가 읽은 값으로 정의 될 때까지 스레드가 생성을 벗어납니다.

**예 2:** 이전 예제와는 달리, 특정 스레드에서 읽기를 수행 해야 한다고 가정 합니다 (마스터 스레드). 이 경우에는 `copyprivate` 절을 사용 하 여 브로드캐스트를 직접 수행할 수 없지만 임시 공유 개체에 대 한 액세스를 제공 하는 데 사용할 수 있습니다.

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**예 3:** 병렬 영역 내에 필요한 잠금 개체 수를 입력 하기 전에 쉽게 확인할 수 없다고 가정 합니다. `copyprivate`절을 사용 하 여 해당 병렬 영역 내에 할당 된 공유 잠금 개체에 대 한 액세스를 제공할 수 있습니다.

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>Threadprivate 지시문

다음 예제에서는 [threadprivate](2-directives.md#271-threadprivate-directive) 지시문을 사용 하 여 각 스레드에 별도의 카운터를 제공 하는 방법을 보여 줍니다.

### <a name="example-1"></a>예제 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>예 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A. 27 C99 가변 길이 배열

다음 예제에서는 [firstprivate](2-directives.md#2722-firstprivate) 지시문에서 Vla (C99 가변 길이 배열)를 사용 하는 방법을 보여 줍니다.

> [!NOTE]
> 가변 길이 배열은 현재 Visual C++에서 지원 되지 않습니다.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-num_threads-clause"></a>.28 num_threads 절

다음 예에서는 [num_threads](2-directives.md#23-parallel-construct) 절을 보여 줍니다. 병렬 지역은 최대 10 개 스레드를 사용 하 여 실행 됩니다.

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>.29 개의 작업 공유 구문은 중요 한 구문 내에 있습니다.

다음 예제에서는 구문 내에서 작업 공유 구문을 사용 하는 방법을 보여 줍니다 `critical` . 이 예제는 작업 공유 구문과 `critical` 구문이 동일한 병렬 영역에 바인딩되지 않기 때문에 호환 됩니다.

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>30 Reprivatization

다음 예에서는 변수의 reprivatization를 보여 줍니다. Private 변수 `private` 는 중첩 된 지시문에서 다시 표시할 수 있습니다. 바깥쪽 병렬 지역에서는 이러한 변수를 공유할 필요가 없습니다.

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>31 스레드로부터 안전한 lock 함수

다음 c + + 예제에서는 [omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)사용 하 여 병렬 영역에서 잠금 배열을 초기화 하는 방법을 보여 줍니다.

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
