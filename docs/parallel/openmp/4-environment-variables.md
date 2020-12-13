---
description: '자세히 알아보기: 4. 환경 변수'
title: 4. 환경 변수
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 47c0d557497a387f89c13c88c414aae9eb9377ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342532"
---
# <a name="4-environment-variables"></a>4. 환경 변수

이 장에서는 병렬 코드의 실행을 제어 하는 OpenMP C 및 c + + API 환경 변수 (또는 이와 유사한 플랫폼 관련 메커니즘)에 대해 설명 합니다.  환경 변수의 이름은 대문자 여야 합니다. 할당 된 값은 대/소문자를 구분 하지 않으며 선행 및 후행 공백이 있을 수 있습니다.  프로그램이 시작 된 후 값에 대 한 수정 사항은 무시 됩니다.

환경 변수는 다음과 같습니다.

- [OMP_SCHEDULE](#41-omp_schedule) 런타임 일정 유형 및 청크 크기를 설정 합니다.
- [OMP_NUM_THREADS](#42-omp_num_threads) 는 실행 중에 사용할 스레드 수를 설정 합니다.
- [OMP_DYNAMIC](#43-omp_dynamic) 는 스레드 수를 동적으로 조정 하도록 설정 하거나 해제 합니다.
- [OMP_NESTED](#44-omp_nested) 중첩 된 병렬 처리를 사용 하거나 사용 하지 않도록 설정 합니다.

이 챕터의 예제에서는 이러한 변수가 csh (Unix C 셸) 환경에서 설정 되는 방법만 보여 줍니다. Korn 셸 및 DOS 환경에서 작업은 다음과 유사 합니다.

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a> 4.1 OMP_SCHEDULE

`OMP_SCHEDULE``for`일정 유형이 있는 및 지시문에만 적용 됩니다 `parallel for` `runtime` . 이러한 모든 루프의 일정 유형 및 청크 크기는 런타임에 설정할 수 있습니다. 이 환경 변수를 인식 된 일정 유형 및 선택적 *chunk_size* 로 설정 합니다.

`for`및의 `parallel for` 일정 유형을 포함 하는 지시문의 경우 `runtime` `OMP_SCHEDULE` 는 무시 됩니다. 이 환경 변수의 기본값은 구현에서 정의 됩니다. 선택적 *chunk_size* 설정 된 경우 값은 양수 여야 합니다. *Chunk_size* 설정 되지 않은 경우에는 일정이 인 경우를 제외 하 고 값 1이 가정 됩니다 `static` . 일정의 경우 `static` 기본 청크 크기는 루프 반복 공간을 루프에 적용 된 스레드 수로 나눈 값으로 설정 됩니다.

예제:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>상호 참조

- [for](2-directives.md#241-for-construct) 지시문
- [parallel for](2-directives.md#251-parallel-for-construct) 지시문

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a> 4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS`환경 변수는 실행 하는 동안 사용할 기본 스레드 수를 설정 합니다. `OMP_NUM_THREADS` 라이브러리 루틴을 호출 하 여 해당 숫자가 명시적으로 변경 되는 경우는 무시 됩니다 `omp_set_num_threads` . 지시문에 명시적 절이 있는 경우에도 무시 됩니다 `num_threads` `parallel` .

환경 변수의 값은 `OMP_NUM_THREADS` 양의 정수 여야 합니다. 이는 스레드 수를 동적으로 조정 하는 기능이 사용 되는지 여부에 따라 달라 집니다. 환경 변수와 스레드의 동적 조정 간의 상호 작용에 대 한 포괄적인 규칙 집합은 `OMP_NUM_THREADS` [섹션 2.3](2-directives.md#23-parallel-construct)을 참조 하세요.

사용할 스레드 수는 다음과 같은 경우 구현에서 정의 됩니다.

- `OMP_NUM_THREADS`환경 변수가 지정 되지 않았습니다.
- 지정 된 값이 양의 정수가 아니거나
- 값이 시스템에서 지원할 수 있는 최대 스레드 수보다 큽니다.

예제:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>상호 참조

- [num_threads](2-directives.md#23-parallel-construct) 절
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) 함수
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) 함수

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a> 4.3 OMP_DYNAMIC

`OMP_DYNAMIC`환경 변수는 병렬 영역을 실행 하는 데 사용할 수 있는 스레드 수를 동적으로 조정 하거나 사용 하지 않도록 설정 합니다. `OMP_DYNAMIC` 라이브러리 루틴을 호출 하 여 동적 조정을 명시적으로 사용 하거나 사용 하지 않도록 설정 하면가 무시 됩니다 `omp_set_dynamic` . 해당 값은 또는 여야 합니다 `TRUE` `FALSE` .

`OMP_DYNAMIC`가로 설정 되 면 `TRUE` 병렬 영역을 실행 하는 데 사용 되는 스레드 수를 런타임 환경에서 조정 하 여 시스템 리소스를 가장 효과적으로 사용할 수 있습니다.  `OMP_DYNAMIC`가로 설정 된 경우 `FALSE` 동적 조정을 사용할 수 없습니다. 기본 조건은 구현에서 정의 됩니다.

예제:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>상호 참조

- [병렬 영역](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) 함수

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a> 4.4 OMP_NESTED

`OMP_NESTED`환경 변수는 라이브러리 루틴을 호출 하 여 중첩 된 병렬 처리를 활성화 하거나 비활성화 하지 않는 한 중첩 된 병렬 처리를 사용 하거나 사용 하지 않습니다 `omp_set_nested` . `OMP_NESTED`가로 설정 된 경우 `TRUE` 중첩 된 병렬 처리를 사용할 수 있습니다. `OMP_NESTED`가로 설정 된 경우 `FALSE` 중첩 된 병렬 처리를 사용할 수 없습니다. 기본값은 `FALSE`입니다.

예제:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>상호 참조

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) 함수
