---
description: '자세한 정보: OpenMP 환경 변수'
title: OpenMP 환경 변수
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: 58ca563033906f4e5e7e9d59089dc463396aa91c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342389"
---
# <a name="openmp-environment-variables"></a>OpenMP 환경 변수

OpenMP API에서 사용 되는 환경 변수에 대 한 링크를 제공 합니다.

OpenMP 표준의 Visual C++ 구현에는 다음과 같은 환경 변수가 포함 됩니다. 이러한 환경 변수는 프로그램 시작 시에 읽을 수 있으며 해당 값에 대 한 수정 내용은 런타임에 무시 됩니다 (예: [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)사용).

|환경 변수|Description|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|[](openmp-clauses.md#schedule) `schedule(runtime)` 가 또는 지시문에 지정 된 경우 schedule 절의 동작을 수정 `for` 합니다 `parallel for` .|
|[OMP_NUM_THREADS](#omp-num-threads)|[Omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 또는 [num_threads](openmp-clauses.md#num-threads)에 의해 재정의 되지 않는 한 병렬 영역에 있는 최대 스레드 수를 설정 합니다.|
|[OMP_DYNAMIC](#omp-dynamic)|OpenMP 런타임에서 병렬 영역의 스레드 수를 조정할 수 있는지 여부를 지정 합니다.|
|[OMP_NESTED](#omp-nested)|중첩 된 병렬 처리를 사용 하거나 사용 하지 않도록 설정 하지 않는 한 중첩 된 병렬 처리를 사용할지 여부를 지정 합니다 `omp_set_nested` .|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a> OMP_DYNAMIC

OpenMP 런타임에서 병렬 영역의 스레드 수를 조정할 수 있는지 여부를 지정 합니다.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>설명

`OMP_DYNAMIC`환경 변수는 [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) 함수를 통해 재정의할 수 있습니다.

OpenMP 표준의 Visual C++ 구현에서 기본값은 `OMP_DYNAMIC=FALSE` 입니다.

자세한 내용은 [4.3 OMP_DYNAMIC](../4-environment-variables.md#43-omp_dynamic)를 참조 하세요.

### <a name="example"></a>예제

다음 명령은 `OMP_DYNAMIC` 환경 변수를 TRUE로 설정 합니다.

```cmd
set OMP_DYNAMIC=TRUE
```

다음 명령은 환경 변수의 현재 설정을 표시 합니다 `OMP_DYNAMIC` .

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a> OMP_NESTED

중첩 된 병렬 처리를 사용 하거나 사용 하지 않도록 설정 하지 않는 한 중첩 된 병렬 처리를 사용할지 여부를 지정 합니다 `omp_set_nested` .

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>설명

`OMP_NESTED`환경 변수는 [omp_set_nested](openmp-functions.md#omp-set-nested) 함수를 통해 재정의할 수 있습니다.

OpenMP 표준의 Visual C++ 구현에서 기본값은 `OMP_DYNAMIC=FALSE` 입니다.

자세한 내용은 [4.4 OMP_NESTED](../4-environment-variables.md#44-omp_nested)를 참조 하세요.

### <a name="example"></a>예제

다음 명령은 `OMP_NESTED` 환경 변수를 TRUE로 설정 합니다.

```cmd
set OMP_NESTED=TRUE
```

다음 명령은 환경 변수의 현재 설정을 표시 합니다 `OMP_NESTED` .

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a> OMP_NUM_THREADS

[Omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 또는 [num_threads](openmp-clauses.md#num-threads)에 의해 재정의 되지 않는 한 병렬 영역에 있는 최대 스레드 수를 설정 합니다.

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>매개 변수

*num*<br/>
병렬 영역에 있는 최대 스레드 수는 Visual C++ 구현의 최대 64입니다.

### <a name="remarks"></a>설명

`OMP_NUM_THREADS`환경 변수는 [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 함수 또는 [num_threads](openmp-clauses.md#num-threads)에 의해 재정의 될 수 있습니다.

`num`OpenMP 표준의 Visual C++ 구현에서의 기본값은 하이퍼스레딩을 cpu를 포함 하는 가상 프로세서의 수입니다.

자세한 내용은 [4.2 OMP_NUM_THREADS](../4-environment-variables.md#42-omp_num_threads)를 참조 하세요.

### <a name="example"></a>예제

다음 명령은 `OMP_NUM_THREADS` 환경 변수를로 설정 합니다 `16` .

```cmd
set OMP_NUM_THREADS=16
```

다음 명령은 환경 변수의 현재 설정을 표시 합니다 `OMP_NUM_THREADS` .

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a> OMP_SCHEDULE

[](openmp-clauses.md#schedule) `schedule(runtime)` 가 또는 지시문에 지정 된 경우 schedule 절의 동작을 수정 `for` 합니다 `parallel for` .

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>매개 변수

*size*<br/>
필드 반복의 크기를 지정 합니다. *크기* 는 양의 정수 여야 합니다. 기본값은 `1` *형식이* static 인 경우를 제외 하 고입니다. *형식이* 인 경우 유효 하지 않습니다 `runtime` .

*type*<br/>
일정 유형 (,, `dynamic` 또는) `guided` 입니다 `runtime` `static` .

### <a name="remarks"></a>설명

OpenMP 표준의 Visual C++ 구현에서 기본값은 `OMP_SCHEDULE=static,0` 입니다.

자세한 내용은 [4.1 OMP_SCHEDULE](../4-environment-variables.md#41-omp_schedule)를 참조 하세요.

### <a name="example"></a>예제

다음 명령은 환경 변수를 설정 합니다 `OMP_SCHEDULE` .

```cmd
set OMP_SCHEDULE="guided,2"
```

다음 명령은 환경 변수의 현재 설정을 표시 합니다 `OMP_SCHEDULE` .

```cmd
set OMP_SCHEDULE
```
