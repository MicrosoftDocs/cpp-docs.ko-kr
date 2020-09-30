---
title: OpenMP 함수
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 660d786148738c8ce998ad5d78645efdb444ea47
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503705"
---
# <a name="openmp-functions"></a>OpenMP 함수

OpenMP API에서 사용 되는 함수에 대 한 링크를 제공 합니다.

OpenMP 표준의 Visual C++ 구현에는 다음 함수 및 데이터 형식이 포함 됩니다.

환경 실행의 경우:

|함수|설명|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|[Num_threads](openmp-clauses.md#num-threads) 절에 의해 재정의 되지 않는 경우 예정 된 병렬 영역의 스레드 수를 설정 합니다.|
|[omp_get_num_threads](#omp-get-num-threads)|병렬 영역의 스레드 수를 반환 합니다.|
|[omp_get_max_threads](#omp-get-max-threads)|[Num_threads](openmp-clauses.md#num-threads) 없는 병렬 영역이 코드의 해당 지점에서 정의 된 경우 사용할 수 있는 스레드 수보다 크거나 같은 정수를 반환 합니다.|
|[omp_get_thread_num](#omp-get-thread-num)|스레드 팀 내에서 실행 중인 스레드의 스레드 번호를 반환 합니다.|
|[omp_get_num_procs](#omp-get-num-procs)|함수가 호출 될 때 사용할 수 있는 프로세서 수를 반환 합니다.|
|[omp_in_parallel](#omp-in-parallel)|병렬 영역 내에서 호출 된 경우 0이 아닌 값을 반환 합니다.|
|[omp_set_dynamic](#omp-set-dynamic)|런타임에 따라 예정 된 병렬 지역에서 사용할 수 있는 스레드 수를 조정할 수 있음을 나타냅니다.|
|[omp_get_dynamic](#omp-get-dynamic)|이후 병렬 지역에서 사용할 수 있는 스레드 수를 런타임에 따라 조정할 수 있는지 여부를 나타내는 값을 반환 합니다.|
|[omp_set_nested](#omp-set-nested)|중첩 된 병렬 처리를 사용 합니다.|
|[omp_get_nested](#omp-get-nested)|중첩 된 병렬 처리를 사용할 수 있는지 여부를 나타내는 값을 반환 합니다.|

잠금:

|함수|설명|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|단순 잠금을 초기화 합니다.|
|[omp_init_nest_lock](#omp-init-nest-lock)|잠금을 초기화 합니다.|
|[omp_destroy_lock](#omp-destroy-lock)|잠금 초기화 하지 않습니다.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|초기화 하지 않습니다은 a.17 중첩 가능 잠금을 해제 합니다.|
|[omp_set_lock](#omp-set-lock)|잠금을 사용할 수 있을 때까지 스레드 실행을 차단 합니다.|
|[omp_set_nest_lock](#omp-set-nest-lock)|잠금을 사용할 수 있을 때까지 스레드 실행을 차단 합니다.|
|[omp_unset_lock](#omp-unset-lock)|잠금을 해제 합니다.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|A.17 중첩 가능 잠금을 해제 합니다.|
|[omp_test_lock](#omp-test-lock)|잠금을 설정 하려고 시도 하지만 스레드 실행을 차단 하지 않습니다.|
|[omp_test_nest_lock](#omp-test-nest-lock)|A.17 중첩 가능 잠금을 설정 하려고 시도 하지만 스레드 실행을 차단 하지 않습니다.|

|데이터 형식|Description|
|---------|-----------|
|`omp_lock_t`|잠금을 사용할 수 있는지 여부 또는 스레드가 잠금을 소유 하 고 있는지 여부에 대 한 잠금 상태를 포함 하는 형식입니다.|
|`omp_nest_lock_t`|잠금 사용 가능 여부와 잠금 및 중첩 개수를 소유 하는 스레드의 id에 대 한 다음 정보 중 하나를 보유 하는 형식입니다.|

타이밍 루틴의 경우:

|함수|설명|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|특정 지점에서 경과 된 시간 (초) 값을 반환 합니다.|
|[omp_get_wtick](#omp-get-wtick)|프로세서 클록 틱 사이의 시간 (초)을 반환 합니다.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a> omp_destroy_lock

잠금 초기화 하지 않습니다.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_lock_t` [Omp_init_lock](#omp-init-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.2 omp_destroy_lock 및 omp_destroy_nest_lock 함수](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_init_lock](#omp-init-lock) 를 참조 하세요 `omp_destroy_lock` .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a> omp_destroy_nest_lock

초기화 하지 않습니다은 a.17 중첩 가능 잠금을 해제 합니다.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_nest_lock_t` [Omp_init_nest_lock](#omp-init-nest-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.2 omp_destroy_lock 및 omp_destroy_nest_lock 함수](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_init_nest_lock](#omp-init-nest-lock) 를 참조 하세요 `omp_destroy_nest_lock` .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a> omp_get_dynamic

이후 병렬 지역에서 사용할 수 있는 스레드 수를 런타임에 따라 조정할 수 있는지 여부를 나타내는 값을 반환 합니다.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>반환 값

0이 아닌 값은 스레드가 동적으로 조정 됨을 의미 합니다.

### <a name="remarks"></a>설명

스레드의 동적 조정은 [omp_set_dynamic](#omp-set-dynamic) 및 [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)를 사용 하 여 지정 됩니다.

자세한 내용은 [3.1.7 omp_set_dynamic 함수](../3-run-time-library-functions.md#317-omp_set_dynamic-function)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_set_dynamic](#omp-set-dynamic) 를 참조 하세요 `omp_get_dynamic` .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a> omp_get_max_threads

[Num_threads](openmp-clauses.md#num-threads) 없는 병렬 영역이 코드의 해당 지점에서 정의 된 경우 사용할 수 있는 스레드 수보다 크거나 같은 정수를 반환 합니다.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>설명

자세한 내용은 [3.1.3 omp_get_max_threads 함수](../3-run-time-library-functions.md#313-omp_get_max_threads-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a> omp_get_nested

중첩 된 병렬 처리를 사용할 수 있는지 여부를 나타내는 값을 반환 합니다.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>반환 값

0이 아닌 값은 중첩 된 병렬 처리를 사용 함을 의미 합니다.

### <a name="remarks"></a>설명

중첩 된 병렬 처리는 [omp_set_nested](#omp-set-nested) 및 [OMP_NESTED](openmp-environment-variables.md#omp-nested)를 사용 하 여 지정 됩니다.

자세한 내용은 [3.1.10 omp_get_nested 함수](../3-run-time-library-functions.md#3110-omp_get_nested-function)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_set_nested](#omp-set-nested) 를 참조 하세요 `omp_get_nested` .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a> omp_get_num_procs

함수가 호출 될 때 사용할 수 있는 프로세서 수를 반환 합니다.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>설명

자세한 내용은 [3.1.5 omp_get_num_procs 함수](../3-run-time-library-functions.md#315-omp_get_num_procs-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a> omp_get_num_threads

병렬 영역의 스레드 수를 반환 합니다.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>설명

자세한 내용은 [3.1.2 omp_get_num_threads 함수](../3-run-time-library-functions.md#312-omp_get_num_threads-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a> omp_get_thread_num

스레드 팀 내에서 실행 중인 스레드의 스레드 번호를 반환 합니다.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>설명

자세한 내용은 [3.1.4 omp_get_thread_num 함수](../3-run-time-library-functions.md#314-omp_get_thread_num-function)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [parallel](openmp-directives.md#parallel) 을 참조 하십시오 `omp_get_thread_num` .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a> omp_get_wtick

프로세서 클록 틱 사이의 시간 (초)을 반환 합니다.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>설명

자세한 내용은 [3.3.2 omp_get_wtick 함수](../3-run-time-library-functions.md#332-omp_get_wtick-function)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_get_wtime](#omp-get-wtime) 를 참조 하세요 `omp_get_wtick` .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a> omp_get_wtime

특정 지점에서 경과 된 시간 (초) 값을 반환 합니다.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>반환 값

는 임의의 특정 지점에서 경과 된 시간 (초)의 값을 반환 합니다.

### <a name="remarks"></a>설명

이 지점은 프로그램이 실행 되는 동안 일관 되 게 유지 되므로 향후 비교가 가능 합니다.

자세한 내용은 [3.3.1 omp_get_wtime 함수](../3-run-time-library-functions.md#331-omp_get_wtime-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a> omp_in_parallel

병렬 영역 내에서 호출 된 경우 0이 아닌 값을 반환 합니다.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>설명

자세한 내용은 [3.1.6 omp_in_parallel 함수](../3-run-time-library-functions.md#316-omp_in_parallel-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a> omp_init_lock

단순 잠금을 초기화 합니다.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_lock_t` 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.1 omp_init_lock 및 omp_init_nest_lock 함수](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a> omp_init_nest_lock

잠금을 초기화 합니다.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_nest_lock_t` 형식의 변수입니다.

### <a name="remarks"></a>설명

초기 중첩 수는 0입니다.

자세한 내용은 [3.2.1 omp_init_lock 및 omp_init_nest_lock 함수](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a> omp_set_dynamic

런타임에 따라 예정 된 병렬 지역에서 사용할 수 있는 스레드 수를 조정할 수 있음을 나타냅니다.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>매개 변수

*짧은*<br/>
런타임에 의해 예정 된 병렬 지역에서 사용할 수 있는 스레드 수를 조정할 수 있는지 여부를 나타내는 값입니다. 0이 아니면 런타임이 스레드 수를 조정할 수 있습니다 (0 인 경우). 런타임이 스레드 수를 동적으로 조정 하지 않습니다.

### <a name="remarks"></a>설명

스레드 수는 [omp_set_num_threads](#omp-set-num-threads) 또는 [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)에 의해 설정 된 값을 초과 하지 않습니다.

[Omp_get_dynamic](#omp-get-dynamic) 를 사용 하 여의 현재 설정을 표시 `omp_set_dynamic` 합니다.

의 설정은 `omp_set_dynamic` [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) 환경 변수의 설정을 재정의 합니다.

자세한 내용은 [3.1.7 omp_set_dynamic 함수](../3-run-time-library-functions.md#317-omp_set_dynamic-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a> omp_set_lock

잠금을 사용할 수 있을 때까지 스레드 실행을 차단 합니다.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_lock_t` [Omp_init_lock](#omp-init-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.3 omp_set_lock 및 omp_set_nest_lock 함수](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions)를 참조 하세요.

### <a name="examples"></a>예

을 사용 하는 예제는 [omp_init_lock](#omp-init-lock) 를 참조 하세요 `omp_set_lock` .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a> omp_set_nest_lock

잠금을 사용할 수 있을 때까지 스레드 실행을 차단 합니다.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_nest_lock_t` [Omp_init_nest_lock](#omp-init-nest-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.3 omp_set_lock 및 omp_set_nest_lock 함수](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions)를 참조 하세요.

### <a name="examples"></a>예

을 사용 하는 예제는 [omp_init_nest_lock](#omp-init-nest-lock) 를 참조 하세요 `omp_set_nest_lock` .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a> omp_set_nested

중첩 된 병렬 처리를 사용 합니다.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>매개 변수

*짧은*<br/>
0이 아닌 값은 중첩 된 병렬 처리를 사용 하 고 0은 중첩 된 병렬 처리를 비활성화 합니다

### <a name="remarks"></a>설명

OMP 중첩 된 병렬 처리는를 사용 `omp_set_nested` 하거나 [OMP_NESTED](openmp-environment-variables.md#omp-nested) 환경 변수를 설정 하 여 설정할 수 있습니다.

설정에는 `omp_set_nested` 환경 변수의 설정이 재정의 됩니다 `OMP_NESTED` .

병렬 영역을 중첩할 때 스레드 수가 급격히 향상 되기 때문에 환경 변수를 사용 하도록 설정 하면 다른 운영 프로그램이 중단 될 수 있습니다. 예를 들어 OMP 스레드 수를 4로 설정 하 여 6 번 루트로 함수는 4096 (4에서 거듭제곱) 스레드를 요구 합니다. I/o 바인딩된 응용 프로그램을 제외 하 고 프로세서 보다 많은 스레드가 있는 경우 일반적으로 응용 프로그램의 성능이 저하 됩니다.

[Omp_get_nested](#omp-get-nested) 를 사용 하 여의 현재 설정을 표시 `omp_set_nested` 합니다.

자세한 내용은 [3.1.9 omp_set_nested 함수](../3-run-time-library-functions.md#319-omp_set_nested-function)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a> omp_set_num_threads

[Num_threads](openmp-clauses.md#num-threads) 절에 의해 재정의 되지 않는 경우 예정 된 병렬 영역의 스레드 수를 설정 합니다.

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>매개 변수

*num_threads*<br/>
병렬 영역에 있는 스레드 수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.1.1 omp_set_num_threads 함수](../3-run-time-library-functions.md#311-omp_set_num_threads-function)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_get_num_threads](#omp-get-num-threads) 를 참조 하세요 `omp_set_num_threads` .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a> omp_test_lock

잠금을 설정 하려고 시도 하지만 스레드 실행을 차단 하지 않습니다.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_lock_t` [Omp_init_lock](#omp-init-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.5 omp_test_lock 및 omp_test_nest_lock 함수](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a> omp_test_nest_lock

A.17 중첩 가능 잠금을 설정 하려고 시도 하지만 스레드 실행을 차단 하지 않습니다.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_nest_lock_t` [Omp_init_nest_lock](#omp-init-nest-lock)를 사용 하 여 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.5 omp_test_lock 및 omp_test_nest_lock 함수](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a> omp_unset_lock

잠금을 해제 합니다.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_lock_t`스레드에서 소유 하 고 함수에서 실행 되는 [omp_init_lock](#omp-init-lock)로 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.4 omp_unset_lock 및 omp_unset_nest_lock 함수](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_init_lock](#omp-init-lock) 를 참조 하세요 `omp_unset_lock` .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a> omp_unset_nest_lock

A.17 중첩 가능 잠금을 해제 합니다.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>매개 변수

*lock*<br/>
`omp_nest_lock_t`스레드에서 소유 하 고 함수에서 실행 되는 [omp_init_nest_lock](#omp-init-nest-lock)로 초기화 된 형식의 변수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [3.2.4 omp_unset_lock 및 omp_unset_nest_lock 함수](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions)를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 예제는 [omp_init_nest_lock](#omp-init-nest-lock) 를 참조 하세요 `omp_unset_nest_lock` .
