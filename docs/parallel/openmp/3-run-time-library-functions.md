---
description: '자세히 알아보기: 3. 런타임 라이브러리 함수'
title: 3. 런타임 라이브러리 함수
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 67eb3b25efd65dcb99cd140bdc4e93491bacd79a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342558"
---
# <a name="3-run-time-library-functions"></a>3. 런타임 라이브러리 함수

이 단원에서는 OpenMP C 및 c + + 런타임 라이브러리 함수에 대해 설명 합니다. 헤더는 **\<omp.h>** 두 가지 형식, 즉 병렬 실행 환경을 제어 하 고 쿼리 하는 데 사용할 수 있는 여러 함수 및 데이터에 대 한 액세스를 동기화 하는 데 사용할 수 있는 잠금 함수를 선언 합니다.

형식은 `omp_lock_t` 잠금을 사용할 수 있거나 스레드가 잠금을 소유 하 고 있음을 나타낼 수 있는 개체 형식입니다. 이러한 잠금을 *단순 잠금* 이라고 합니다.

형식은 `omp_nest_lock_t` 잠금을 사용할 수 있음을 나타낼 수 있는 개체 형식 이거나, 잠금을 소유 하는 스레드 id와 *중첩 된 개수* (아래 설명 참조)입니다. 이러한 잠금을 *a.17 중첩 가능 잠금* 이라고 합니다.

라이브러리 함수는 "C" 링크가 있는 외부 함수입니다.

이 장의 설명은 다음 항목으로 구성 되어 있습니다.

- [실행 환경 함수](#31-execution-environment-functions)
- [Lock 함수](#32-lock-functions)
- [타이밍 루틴](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 실행 환경 함수

이 섹션에서 설명 하는 함수는 스레드, 프로세서 및 병렬 환경에 영향을 주고 모니터링 합니다.

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a> 3.1.1 omp_set_num_threads 함수

`omp_set_num_threads`함수는 절을 지정 하지 않는 이후 병렬 영역에 사용할 기본 스레드 수를 설정 합니다 `num_threads` . 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

*Num_threads* 매개 변수의 값은 양의 정수 여야 합니다. 이는 스레드 수를 동적으로 조정 하는 기능이 사용 되는지 여부에 따라 달라 집니다. 함수와 스레드 동적 조정 간의 상호 작용에 대 한 포괄적인 규칙 집합은 `omp_set_num_threads` [섹션 2.3](2-directives.md#23-parallel-construct)을 참조 하세요.

이 함수는 함수에서 0을 반환 하는 프로그램의 일부에서 호출 될 때 위에서 설명한 효과를 가집니다 `omp_in_parallel` . 함수가 0이 아닌 값을 반환 하는 프로그램의 일부에서 호출 되는 경우 `omp_in_parallel` 이 함수의 동작이 정의 되지 않습니다.

이 호출은 환경 변수 보다 우선 `OMP_NUM_THREADS` 합니다. 을 호출 하 여 설정 하거나 환경 변수를 설정 하 여 설정할 수 있는 스레드 수의 기본값은 `omp_set_num_threads` `OMP_NUM_THREADS` 절을 지정 하 여 단일 지시문에서 명시적으로 재정의 될 수 있습니다 `parallel` `num_threads` .

자세한 내용은 [omp_set_dynamic](#317-omp_set_dynamic-function)를 참조 하세요.

#### <a name="cross-references"></a>상호 참조

- [omp_set_dynamic](#317-omp_set_dynamic-function) 함수
- [omp_get_dynamic](#318-omp_get_dynamic-function) 함수
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) 환경 변수
- [num_threads](2-directives.md#23-parallel-construct) 절

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a> 3.1.2 omp_get_num_threads 함수

`omp_get_num_threads`함수는 현재 팀에서 호출 된 병렬 영역을 실행 중인 스레드의 수를 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads`절, `omp_set_num_threads` 함수 및 `OMP_NUM_THREADS` 환경 변수는 팀의 스레드 수를 제어 합니다.

사용자가 스레드 수를 명시적으로 설정 하지 않은 경우 기본값은 구현에서 정의 됩니다. 이 함수는 가장 가까운 바깥쪽 지시문에 바인딩합니다 `parallel` . 프로그램의 일련 부분에서 또는 serialize 된 중첩 된 병렬 영역에서 호출 하는 경우이 함수는 1을 반환 합니다.

자세한 내용은 [omp_set_dynamic](#317-omp_set_dynamic-function)를 참조 하세요.

#### <a name="cross-references"></a>상호 참조

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [평행선](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a> 3.1.3 omp_get_max_threads 함수

`omp_get_max_threads`함수는 절이 없는 병렬 영역이 `num_threads` 코드의 해당 지점에서 표시 되는 경우 팀을 구성 하는 데 사용 되는 스레드 수 만큼 이상으로 보장 되는 정수를 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

다음은 값의 하 한을 나타냅니다 `omp_get_max_threads` .

> *스레드 사용-다음-팀* <= `omp_get_max_threads`

다른 병렬 지역이 절을 사용 하 여 `num_threads` 특정 개수의 스레드를 요청 하는 경우의 결과에 대 한 하한값은 `omp_get_max_threads` 더 이상 유지 되지 않습니다.

`omp_get_max_threads`함수의 반환 값을 사용 하 여 다음 병렬 지역에서 형성 된 팀의 모든 스레드에 대해 충분 한 저장소를 동적으로 할당할 수 있습니다.

#### <a name="cross-references"></a>상호 참조

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a> 3.1.4 omp_get_thread_num 함수

`omp_get_thread_num`함수는 해당 팀 내에서 함수를 실행 하는 스레드의 스레드 번호를 반환 합니다. 스레드 번호는 0 `omp_get_num_threads()` 에서-1 (포함) 사이입니다. 팀의 마스터 스레드는 스레드 0입니다.

형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

직렬 지역에서 호출 되는 경우 `omp_get_thread_num` 0을 반환 합니다. Serialize 된 중첩 된 병렬 영역 내에서 호출 되는 경우이 함수는 0을 반환 합니다.

#### <a name="cross-references"></a>상호 참조

- [omp_get_num_threads](#312-omp_get_num_threads-function) 함수

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a> 3.1.5 omp_get_num_procs 함수

`omp_get_num_procs`함수는 함수가 호출 될 때 프로그램에 사용할 수 있는 프로세서 수를 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a> 3.1.6 omp_in_parallel 함수

`omp_in_parallel`병렬로 실행 되는 병렬 영역의 동적 범위 내에서 호출 되는 경우이 함수는 0이 아닌 값을 반환 하 고 그렇지 않으면 0을 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

이 함수는 serialize 된 중첩 된 영역을 포함 하 여 병렬로 실행 되는 지역 내에서 호출 될 때 0이 아닌 값을 반환 합니다.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a> 3.1.7 omp_set_dynamic 함수

`omp_set_dynamic`함수는 병렬 영역 실행에 사용할 수 있는 스레드 수를 동적으로 조정 하거나 사용 하지 않도록 설정 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

0이 아닌 값으로 계산 되는 *dynamic_threads* 경우에는 런타임 환경에서 사용 하는 스레드 수를 자동으로 조정 하 여 시스템 리소스를 가장 효과적으로 사용할 수 있습니다. 결과적으로 사용자가 지정한 스레드 수는 최대 스레드 수입니다. 병렬 영역을 실행 하는 팀의 스레드 수는 해당 병렬 영역의 지속 시간 동안 고정 된 상태로 유지 되며 함수에서 보고 됩니다 `omp_get_num_threads` .

*Dynamic_threads* 0으로 계산 되 면 동적 조정을 사용할 수 없습니다.

이 함수는 함수에서 0을 반환 하는 프로그램의 일부에서 호출 될 때 위에서 설명한 효과를 가집니다 `omp_in_parallel` . 함수가 0이 아닌 값을 반환 하는 프로그램의 일부에서 호출 되는 경우 `omp_in_parallel` 이 함수의 동작이 정의 되지 않습니다.

에 대 한 호출은 `omp_set_dynamic` `OMP_DYNAMIC` 환경 변수 보다 우선 합니다.

스레드의 동적 조정에 대 한 기본값은 구현에서 정의 됩니다. 따라서 올바른 실행을 위해 특정 개수의 스레드에 종속 된 사용자 코드는 동적 스레드를 명시적으로 사용 하지 않도록 설정 해야 합니다. 스레드 수를 동적으로 조정 하는 기능을 제공 하기 위해 구현 해야 하는 것은 아니지만, 모든 플랫폼에서 이식성을 지원 하기 위해 인터페이스를 제공 해야 합니다.

#### <a name="microsoft-specific"></a>Microsoft 전용

및의 현재 지원은 다음과 같습니다 `omp_get_dynamic` `omp_set_dynamic` .

에 대 한 입력 매개 변수는 스레딩 정책에 영향을 주지 않으며 `omp_set_dynamic` 스레드 수를 변경 하지 않습니다. `omp_get_num_threads` 는 항상 사용자 정의 번호 (설정 된 경우) 또는 기본 스레드 번호를 반환 합니다. 현재 Microsoft 구현에서는 `omp_set_dynamic(0)` 기존 스레드 집합을 다음 병렬 영역에 다시 사용할 수 있도록 동적 스레딩을 끕니다. `omp_set_dynamic(1)` 기존 스레드 집합을 삭제 하 고 예정 된 병렬 영역에 대 한 새 집합을 만들어 동적 스레딩을 설정 합니다. 새 집합의 스레드 수는 이전 집합과 같으며의 반환 값을 기반으로 `omp_get_num_threads` 합니다. 따라서 최상의 성능을 위해를 사용 `omp_set_dynamic(0)` 하 여 기존 스레드를 다시 사용 합니다.

#### <a name="cross-references"></a>상호 참조

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a> 3.1.8 omp_get_dynamic 함수

`omp_get_dynamic`이 함수는 스레드를 동적으로 조정할 수 있는 경우 0이 아닌 값을 반환 하 고, 그렇지 않으면 0을 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

구현에서 스레드 수의 동적 조정을 구현 하지 않는 경우이 함수는 항상 0을 반환 합니다. 자세한 내용은 [omp_set_dynamic](#317-omp_set_dynamic-function)를 참조 하세요.

#### <a name="cross-references"></a>상호 참조

- 동적 스레드 조정에 대 한 자세한 내용은 [omp_set_dynamic](#317-omp_set_dynamic-function)를 참조 하세요.

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a> 3.1.9 omp_set_nested 함수

`omp_set_nested`함수는 중첩 된 병렬 처리를 사용 하거나 사용 하지 않도록 설정 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

*Nested* 가 0으로 계산 되 면 중첩 된 병렬 처리를 사용할 수 없으며,이는 기본값이 고, 중첩 된 병렬 영역은 현재 스레드에 의해 serialize 되 고 실행 됩니다. 그렇지 않으면 중첩 된 병렬 처리를 사용할 수 있고 중첩 된 병렬 영역은 중첩 된 팀을 형성 하는 추가 스레드를 배포할 수 있습니다.

이 함수는 함수에서 0을 반환 하는 프로그램의 일부에서 호출 될 때 위에서 설명한 효과를 가집니다 `omp_in_parallel` . 함수가 0이 아닌 값을 반환 하는 프로그램의 일부에서 호출 되는 경우 `omp_in_parallel` 이 함수의 동작이 정의 되지 않습니다.

이 호출은 환경 변수 보다 우선 `OMP_NESTED` 합니다.

중첩 된 병렬 처리를 사용 하는 경우 중첩 된 병렬 영역을 실행 하는 데 사용 되는 스레드 수는 구현에서 정의 됩니다. 따라서 중첩 된 병렬 처리를 사용 하도록 설정한 경우에도 OpenMP 규격 구현은 중첩 된 병렬 영역을 serialize 할 수 있습니다.

#### <a name="cross-references"></a>상호 참조

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a> 3.1.10 omp_get_nested 함수

`omp_get_nested`중첩 된 병렬 처리를 사용 하는 경우 함수는 0이 아닌 값을 반환 하 고, 비활성화 된 경우 0을 반환 합니다. 중첩 된 병렬 처리에 대 한 자세한 내용은 [omp_set_nested](#319-omp_set_nested-function)를 참조 하세요. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_get_nested(void);
```

구현에서 중첩 된 병렬 처리를 구현 하지 않는 경우이 함수는 항상 0을 반환 합니다.

## <a name="32-lock-functions"></a>3.2 잠금 함수

이 섹션에서 설명 하는 함수는 동기화에 사용 되는 잠금을 조작 합니다.

다음 함수의 경우 lock 변수에는 형식이 있어야 합니다 `omp_lock_t` . 이 변수는 이러한 함수를 통해서만 액세스 해야 합니다. 모든 잠금 함수에는 형식에 대 한 포인터를 포함 하는 인수가 필요 `omp_lock_t` 합니다.

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) 함수는 단순 잠금을 초기화 합니다.
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) 함수는 단순 잠금을 제거 합니다.
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) 함수는 단순 잠금을 사용할 수 있을 때까지 대기 합니다.
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) 함수는 단순 잠금을 해제 합니다.
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) 함수는 간단한 잠금을 테스트 합니다.

다음 함수의 경우 lock 변수에는 형식이 있어야 합니다 `omp_nest_lock_t` .  이 변수는 이러한 함수를 통해서만 액세스 해야 합니다. 모든 a.17 중첩 가능 잠금 함수에는 형식에 대 한 포인터를 포함 하는 인수가 필요 `omp_nest_lock_t` 합니다.

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) 함수는 a.17 중첩 가능 잠금을 초기화 합니다.
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) 함수는 a.17 중첩 가능 잠금을 제거 합니다.
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) 함수는 a.17 중첩 가능 잠금을 사용할 수 있을 때까지 대기 합니다.
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) 함수는 a.17 중첩 가능 잠금을 해제 합니다.
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) 함수는 a.17 중첩 가능 잠금을 테스트 합니다.

OpenMP 잠금 함수는 잠금 변수의 최신 값을 항상 읽고 업데이트 하는 방식으로 lock 변수에 액세스 합니다. 따라서 OpenMP 프로그램에 명시적 지시문을 포함 하 여 `flush` 잠금 변수의 값이 서로 다른 스레드 간에 일치 하는지 확인 하는 것은 필요 하지 않습니다. ( `flush` 지시문이 다른 변수의 값을 일관성 있게 만들어야 할 수도 있습니다.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a> 3.2.1 omp_init_lock 및 omp_init_nest_lock 함수

이러한 함수는 잠금을 초기화 하는 유일한 수단을 제공 합니다. 각 함수는 예정 된 호출에서 사용할 매개 변수 *잠금과* 연결 된 잠금을 초기화 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

초기 상태는 잠금 해제 됩니다. 즉, 잠금을 소유 하는 스레드는 없습니다. A.17 중첩 가능 잠금의 경우 초기 중첩 수는 0입니다. 이미 초기화 된 잠금 변수를 사용 하 여 이러한 루틴 중 하나를 호출 하는 것은 호환 되지 않습니다.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a> 3.2.2 omp_destroy_lock 및 omp_destroy_nest_lock 함수

이러한 함수는 가리키는 lock lock 변수 *잠금이* 초기화 되지 않았는지 확인 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

초기화 되지 않았거나 잠금이 해제 된 잠금 변수를 사용 하 여 이러한 루틴 중 하나를 호출 하는 것은 호환 되지 않습니다.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a> 3.2.3 omp_set_lock 및 omp_set_nest_lock 함수

이러한 각 함수는 지정 된 잠금을 사용할 수 있을 때까지 함수를 실행 하는 스레드를 차단 하 고 잠금을 설정 합니다. 잠금이 해제 된 경우에는 간단한 잠금을 사용할 수 있습니다. A.17 중첩 가능 잠금은 잠금이 해제 된 경우 또는 함수를 실행 하는 스레드가 이미 소유 하 고 있는 경우 사용할 수 있습니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

간단한 잠금의 경우 함수에 대 한 인수는 `omp_set_lock` 초기화 된 잠금 변수를 가리켜야 합니다. 잠금 소유권은 함수를 실행 하는 스레드에 부여 됩니다.

A.17 중첩 가능 잠금의 경우 함수에 대 한 인수는 `omp_set_nest_lock` 초기화 된 잠금 변수를 가리켜야 합니다. 중첩 횟수가 증가 하 고 스레드가 잠금 소유권을 부여 받거나 유지 합니다.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a> 3.2.4 omp_unset_lock 및 omp_unset_nest_lock 함수

이러한 함수는 잠금의 소유권을 해제 하는 방법을 제공 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

이러한 각 함수에 대 한 인수는 함수를 실행 하는 스레드가 소유 하는 초기화 된 잠금 변수를 가리켜야 합니다. 스레드가 해당 잠금을 소유 하지 않는 경우에는 동작이 정의 되지 않습니다.

간단한 잠금의 경우 `omp_unset_lock` 함수는 잠금 소유권에서 함수를 실행 하는 스레드를 해제 합니다.

A.17 중첩 가능 잠금의 경우 `omp_unset_nest_lock` 함수는 중첩 개수를 감소 시키고, 결과 횟수가 0 인 경우 잠금 소유권에서 함수를 실행 하는 스레드를 해제 합니다.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a> 3.2.5 omp_test_lock 및 omp_test_nest_lock 함수

이러한 함수는 잠금을 설정 하려고 하지만 스레드의 실행을 차단 하지는 않습니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

인수는 초기화 된 잠금 변수를 가리켜야 합니다. 이러한 함수는 `omp_set_lock` 스레드의 실행을 차단 하지 않는다는 점을 제외 하 고 및와 동일한 방식으로 잠금을 설정 하려고 시도 `omp_set_nest_lock` 합니다.

간단한 잠금의 `omp_test_lock` 경우 잠금이 성공적으로 설정 된 경우 함수는 0이 아닌 값을 반환 하 고 그렇지 않으면 0을 반환 합니다.

A.17 중첩 가능 잠금의 `omp_test_nest_lock` 경우 함수는 잠금이 성공적으로 설정 된 경우 새 중첩 개수를 반환 하 고 그렇지 않으면 0을 반환 합니다.

## <a name="33-timing-routines"></a>3.3 타이밍 루틴

이 섹션에서 설명 하는 함수는 휴대용 벽 시계 타이머를 지원 합니다.

- [Omp_get_wtime](#331-omp_get_wtime-function) 함수는 경과 된 벽 시계 시간을 반환 합니다.
- [Omp_get_wtick](#332-omp_get_wtick-function) 함수는 연속 클록 틱 사이에 초를 반환 합니다.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a> 3.3.1 omp_get_wtime 함수

`omp_get_wtime`함수는 "과거 시간" 이후 경과 된 벽 시계 시간 (초)에 해당 하는 배정밀도 부동 소수점 값을 초 단위로 반환 합니다.  실제 "과거 시간"은 임의의 것 이지만 응용 프로그램을 실행 하는 동안 변경 되지 않는 것이 보장 됩니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

함수는 다음 예제와 같이 경과 된 시간을 측정 하는 데 사용 될 것으로 예상 됩니다.

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

반환 된 시간은 응용 프로그램에 참여 하는 모든 스레드에서 전역적으로 일치 하지 않아도 되는 "스레드별 시간"입니다.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a> 3.3.2 omp_get_wtick 함수

`omp_get_wtick`함수는 연속 클록 틱 사이의 시간 (초)과 동일한 배정밀도 부동 소수점 값을 반환 합니다. 형식은 다음과 같습니다.

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
