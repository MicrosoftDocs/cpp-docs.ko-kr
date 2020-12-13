---
description: '자세히 알아보기: 2. 지시문'
title: 2. 지시문
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 66b4ee4cdf3fec1740ed9b471c1c57cffebad6d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342571"
---
# <a name="2-directives"></a>2. 지시문

지시문은 `#pragma` c 및 c + + 표준에 정의 된 지시문을 기반으로 합니다.  OpenMP C 및 c + + API를 지 원하는 컴파일러에는 모든 OpenMP 컴파일러 지시문의 해석을 활성화 하 고 허용 하는 명령줄 옵션이 포함 됩니다.

## <a name="21-directive-format"></a>2.1 지시문 형식

OpenMP 지시문의 구문은 [부록 C](c-openmp-c-and-cpp-grammar.md)의 문법에 의해 공식적으로 지정 되며 다음과 같이 비공식적으로 지정 됩니다.

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

각 지시문은로 시작 하 여  `#pragma omp` 이름이 같은 다른 (openmp 또는 공급 업체 확장이 아닌) pragma 지시문과 충돌 가능성이 줄어듭니다. 지시문의 나머지 부분은 컴파일러 지시문에 대 한 C 및 c + + 표준의 규칙을 따릅니다. 특히 공백은의 전후에 사용할 수 있으며 `#` , 경우에 따라 지시문에서 단어를 구분 하는 데 공백을 사용 해야 합니다. 뒤에 나오는 토큰 전처리 `#pragma omp` 는 매크로 대체의 영향을 받습니다.

지시문은 대/소문자를 구분 합니다. 지시문에 절이 표시 되는 순서는 중요 하지 않습니다. 지시문의 절은 필요에 따라 반복 될 수 있으며 각 절의 설명에 나열 된 제한 사항이 적용 됩니다. *변수 목록이* 절에 표시 되는 경우 변수만 지정 해야 합니다. 지시문 마다 하나의 *지시문 이름을* 지정할 수 있습니다.  예를 들어 다음 지시문은 허용 되지 않습니다.

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 지시문은 구조화 된 블록 이어야 하는 최대 하나의 이후 문에 적용 됩니다.

## <a name="22-conditional-compilation"></a>2.2 조건부 컴파일

`_OPENMP`매크로 이름은 OpenMP 규격 구현에 의해 정의 되며,이는 승인 된 사양의 연도와 월이 될 *yyyymm* decimal 상수입니다. 이 매크로는 `#define` 또는 전처리 지시문의 제목이 아니어야 합니다 `#undef` .

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

공급 업체가 OpenMP에 대 한 확장을 정의 하는 경우 미리 정의 된 매크로를 추가로 지정할 수 있습니다.

## <a name="23-parallel-construct"></a>2.3 병렬 구문

다음 지시문은 여러 스레드에서 동시에 실행할 프로그램의 영역인 병렬 영역을 정의 합니다. 이 지시문은 병렬 실행을 시작 하는 기본 구문입니다.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*절* 은 다음 중 하나입니다.

- `if(`*스칼라 식*`)`
- `private(`*변수 목록*`)`
- `firstprivate(`*변수 목록*`)`
- `default(shared | none)`
- `shared(`*변수 목록*`)`
- `copyin(`*변수 목록*`)`
- `reduction(`*연산자* `:` *변수 목록*  `)`
- `num_threads(`*정수 식*`)`

스레드가 병렬 구문으로 이동할 때 다음 중 하나에 해당 하는 경우 스레드 팀이 생성 됩니다.

- `if`절이 없습니다.
- `if`식이 0이 아닌 값으로 계산 됩니다.

이 스레드는 스레드 번호가 0 인 팀의 마스터 스레드가 되며 마스터 스레드를 포함 하 여 팀의 모든 스레드는 영역을 병렬로 실행 합니다. 식의 값이 `if` 0 이면 지역이 serialize 됩니다.

요청 된 스레드 수를 확인 하기 위해 다음 규칙을 순서 대로 고려 합니다. 조건을 충족 하는 첫 번째 규칙이 적용 됩니다.

1. `num_threads`절이 있는 경우 정수 식의 값은 요청 된 스레드 수입니다.

1. `omp_set_num_threads`라이브러리 함수가 호출 된 경우 가장 최근에 실행 된 호출의 인수 값은 요청 된 스레드 수입니다.

1. 환경 변수가 `OMP_NUM_THREADS` 정의 되어 있는 경우이 환경 변수의 값은 요청 된 스레드 수입니다.

1. 위의 메서드가 사용 되지 않는 경우 요청 된 스레드 수는 구현에서 정의 됩니다.

`num_threads`절이 있는 경우 라이브러리 함수에 의해 요청 된 스레드 수 `omp_set_num_threads` 또는 `OMP_NUM_THREADS` 환경 변수가 적용 되는 병렬 영역에 대해서만이를 대체 합니다. 이후 병렬 지역은 영향을 받지 않습니다.

병렬 영역을 실행 하는 스레드 수는 스레드 수를 동적으로 조정 하는 기능이 사용 되는지 여부에 따라 달라 집니다. 동적 조정을 사용 하지 않도록 설정 하면 요청 된 스레드 수가 병렬 영역을 실행 하 게 됩니다. 동적 조정을 사용 하는 경우 요청 된 스레드 수가 병렬 영역을 실행할 수 있는 최대 스레드 수입니다.

스레드 수를 동적으로 조정 하는 동안 병렬 지역이 발생 하 고 병렬 영역에 대해 요청 된 스레드 수가 런타임 시스템이 제공할 수 있는 수보다 많은 경우 프로그램의 동작은 구현에 정의 되어 있습니다. 예를 들어 구현은 프로그램 실행을 중단 하거나 병렬 영역을 serialize 할 수 있습니다.

`omp_set_dynamic`라이브러리 함수 및 `OMP_DYNAMIC` 환경 변수를 사용 하 여 스레드 수를 동적으로 조정 하거나 사용 하지 않도록 설정할 수 있습니다.

지정 된 시간에 실제로 스레드를 호스트 하는 실제 프로세서 수는 구현에서 정의 됩니다. 만든 후에는 팀의 스레드 수가 해당 병렬 영역의 지속 시간 동안 일정 하 게 유지 됩니다. 사용자가 명시적으로 변경 하거나 한 병렬 지역에서 다른 병렬 지역으로 런타임 시스템에 의해 자동으로 변경 될 수 있습니다.

병렬 영역의 동적 범위 내에 포함 된 문은 각 스레드에 의해 실행 되며, 각 스레드는 다른 스레드와 다른 문의 경로를 실행할 수 있습니다. 병렬 영역의 어휘 범위 외부에서 발생 한 지시문을 분리 된 지시문 이라고 합니다.

병렬 영역 끝에 묵시적 장벽이 있습니다. 팀의 마스터 스레드만 병렬 영역 끝에서 실행을 계속 합니다.

병렬 영역을 실행 하는 팀의 스레드가 다른 병렬 구문을 발견 하면 새 팀이 만들어지고 새 팀의 마스터가 됩니다. 중첩 된 병렬 영역은 기본적으로 serialize 됩니다. 결과적으로 하나의 스레드로 구성 된 팀에서 중첩 된 병렬 영역을 실행 합니다. 런타임 라이브러리 함수 또는 환경 변수를 사용 하 여 기본 동작을 변경할 수 있습니다 `omp_set_nested` `OMP_NESTED` . 그러나 중첩 된 병렬 영역을 실행 하는 팀의 스레드 수는 구현에서 정의 됩니다.

지시문에 대 한 제한 사항은 다음과 같습니다 `parallel` .

- 지시문에는 절이 한 개 이상 `if` 표시 될 수 있습니다.

- If 식 또는 식 내의 부작용이 발생 하는지 여부는 지정 되지 `num_threads` 않습니다.

- `throw`병렬 영역 내에서 실행 되는는 동일한 구조화 된 블록의 동적 범위 내에서 실행을 다시 시작 해야 하며, 예외를 throw 한 스레드와 동일한 스레드에서 catch 해야 합니다.

- `num_threads`지시문에는 단일 절만 사용할 수 있습니다. `num_threads`식은 병렬 영역의 컨텍스트 외부에서 계산 되며 양의 정수 값으로 계산 되어야 합니다.

- 및 절의 계산 순서는 `if` 지정 되지 `num_threads` 않습니다.

### <a name="cross-references"></a>상호 참조

- `private`,,,, `firstprivate` `default` `shared` `copyin` 및 `reduction` 절 ([section 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) 환경 변수
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) library 함수
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) 환경 변수
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) 함수
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) 환경 변수
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) library 함수

## <a name="24-work-sharing-constructs"></a>2.4 작업 공유 구문

작업 공유 구문은 관련 문의 실행을이를 발견 한 팀의 멤버 간에 배포 합니다. 작업 공유 지시문은 새 스레드를 시작 하지 않으며, 작업 공유 구문에 대 한 진입에는 의미가 없습니다.

발생 한 작업 공유 구문 및 지시문의 시퀀스는 `barrier` 팀의 모든 스레드에 대해 동일 해야 합니다.

OpenMP는 다음과 같은 작업 공유 구문을 정의 하며 이러한 구문은 다음에 나오는 섹션에 설명 되어 있습니다.

- [for](#241-for-construct) 지시문
- [sections](#242-sections-construct) 지시문
- [단일](#243-single-construct) 지시문

### <a name="241-for-construct"></a>구문에 대 한 2.4.1

`for`지시문은 연결 된 루프의 반복이 병렬로 실행 되도록 지정 하는 반복적인 작업 공유 구문을 식별 합니다. 루프의 반복은 `for` 자신이 바인딩하는 병렬 구문을 실행 하는 팀에 이미 있는 스레드 간에 배포 됩니다. 구문 구문은 다음과 같습니다 `for` .

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

절은 다음 중 하나입니다.

- `private(`*변수 목록*`)`
- `firstprivate(`*변수 목록*`)`
- `lastprivate(`*변수 목록*`)`
- `reduction(`*연산자* `:` *변수 목록*`)`
- `ordered`
- `schedule(`*kind* [ `,` *chunk_size*]`)`
- `nowait`

`for`지시문은 해당 루프의 구조에 제한을 둡니다 `for` . 특히 해당 루프는 `for` 정식 셰이프 여야 합니다.

`for (`*init-expr* `;` *var 논리적 op b* `;` *incr*`)`

*init-expr*<br/>
다음 중 하나

- *var*  =  *lb*
- *정수 형식 var*  =  *lb*

*incr*<br/>
다음 중 하나

- `++`*var*
- *var*`++`
- `--`*var*
- *var*`--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
부호 있는 정수 변수입니다. 다른 방법으로이 변수를 공유 하는 경우에는 해당 기간 동안 암시적으로 전용으로 설정 됩니다 `for` . 문의 본문 내에서이 변수를 수정 하지 마십시오 `for` . 변수를 지정 하지 않으면 `lastprivate` 루프 뒤의 값이 결정 되지 않습니다.

*논리적 op*<br/>
다음 중 하나

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b* 및 *incr*<br>
루프 고정 정수 식입니다. 이러한 식을 평가 하는 동안에는 동기화가 수행 되지 않으므로 계산 된 부작용은 확정 되지 않은 결과를 생성 합니다.

정규 폼을 사용 하면 루프의 진입에서 루프 반복 횟수를 계산할 수 있습니다. 이 계산은 정수 계열 프로 모션 후에 *var* 형식의 값을 사용 하 여 생성 됩니다. 특히, *b* `-` *lb* `+` *incr* 의 값을 해당 형식으로 표현할 수 없는 경우 결과는 결정 되지 않습니다. 또한 *논리적 op* 가 또는 인 경우 `<` `<=` *incr* 은 루프가 반복 될 때마다 *var* 이 증가 하도록 해야 합니다.   *논리적 op* 가 또는 인 `>` 경우 `>=` *incr* 은 루프가 반복 될 때마다 *var* 이 더 작아 져 야 합니다.

`schedule`절은 루프의 반복 `for` 이 팀의 스레드 간에 나뉘는 방법을 지정 합니다. 프로그램의 정확성은 특정 반복을 실행 하는 스레드에 종속 되지 않아야 합니다. *Chunk_size* 값 (지정 된 경우)은 양의 값을 포함 하는 루프 고정 정수 식 이어야 합니다. 이 식을 평가 하는 동안에는 동기화가 수행 되지 않으므로 계산 된 부작용은 확정 되지 않은 결과를 생성 합니다. 일정 *종류* 는 다음 값 중 하나일 수 있습니다.

표 2-1: `schedule` 절 *종류* 값

|값|설명|
|-|-|
|static|`schedule(static,` *Chunk_size* `)` 지정 된 경우 반복은 *chunk_size* 에 지정 된 크기의 청크로 분할 됩니다. 청크는 스레드 번호의 순서에 따라 라운드 로빈 방식으로 팀의 스레드에 정적으로 할당 됩니다. *Chunk_size* 지정 하지 않으면 반복 공간은 각 스레드에 할당 된 하나의 청크를 사용 하 여 크기가 거의 같은 청크로 분할 됩니다.|
|동적|`schedule(dynamic,` *Chunk_size* `)` 지정 된 경우 반복은 각각 *chunk_size* 반복을 포함 하는 일련의 청크로 나뉩니다. 각 청크는 할당을 기다리는 스레드에 할당 됩니다. 스레드는 반복의 청크를 실행 한 후에는 청크를 할당할 수 없을 때까지 다음 할당을 기다립니다. 할당할 마지막 청크에는 더 적은 수의 반복이 있을 수 있습니다. *Chunk_size* 지정 하지 않으면 기본값은 1입니다.|
|처리|`schedule(guided,` *Chunk_size* `)` 지정 된 경우 반복은 크기가 감소 된 청크로 스레드에 할당 됩니다. 스레드가 할당 된 반복 청크를 완료 하는 경우에는 아무것도 남아 있지 않을 때까지 다른 청크를 동적으로 할당 합니다. *Chunk_size* 1의 경우 각 청크의 크기는 대략 스레드 수로 나눈 할당 되지 않은 반복의 수입니다. 이러한 크기는 거의 수만로 줄어듭니다. 값 *k* 가 1 보다 큰 *chunk_size* 의 경우, 마지막 청크가 *k* 회 반복 보다 적을 수 있다는 점을 제외 하 고 크기는 *거의 수만* 로 줄어듭니다. *Chunk_size* 지정 하지 않으면 기본값은 1입니다.|
|런타임|`schedule(runtime)`을 지정 하면 일정에 대 한 결정은 런타임까지 지연 됩니다. 런타임에 환경 변수를 설정 하 여 일정 *종류* 와 청크 크기를 선택할 수 있습니다 `OMP_SCHEDULE` . 이 환경 변수가 설정 되지 않은 경우 결과 일정은 구현에서 정의 됩니다. `schedule(runtime)`을 지정 하면 *chunk_size* 를 지정 하지 않아야 합니다.|

명시적으로 정의 된 `schedule` 절이 없으면 기본값은 `schedule` 구현 시 정의 됩니다.

OpenMP 규격 프로그램은 특정 일정에 따라 올바른 실행을 사용 하지 않아야 합니다. 프로그램은 다른 컴파일러에서 동일한 일정 *종류* 의 구현에 차이가 있을 수 있으므로 위에 지정 된 설명과 정확히 일치 하는 일정 *종류* 를 사용 하면 안 됩니다. 설명을 사용 하 여 특정 상황에 적합 한 일정을 선택할 수 있습니다.

`ordered` `ordered` 지시문은 지시문이 구문에 바인딩될 때 있어야 합니다 `for` .

`for`절이 지정 되지 않은 경우 구문의 끝에 암시적 장벽이 있습니다 `nowait` .

지시문에 대 한 제한 사항은 다음과 같습니다 `for` .

- 루프는 구조화 된 블록 이어야 하 `for` 고, 문으로 실행을 종료 하면 안 됩니다 **`break`** .

- 지시문과 연결 된 루프의 루프 제어 식 값은 `for` `for` 팀의 모든 스레드에 대해 동일 해야 합니다.

- `for`루프 반복 변수는 부호 있는 정수 형식 이어야 합니다.

- `schedule`지시문에는 단일 절만 사용할 수 있습니다 `for` .

- `ordered`지시문에는 단일 절만 사용할 수 있습니다 `for` .

- `nowait`지시문에는 단일 절만 사용할 수 있습니다 `for` .

- *Chunk_size*, *lb*, *b* 또는 *incr* 식 내에서 부작용이 발생 하는 경우 또는 빈도를 지정 하지 않습니다.

- *Chunk_size* 식의 값은 팀의 모든 스레드에 대해 동일 해야 합니다.

#### <a name="cross-references"></a>상호 참조

- `private`, `firstprivate` , `lastprivate` 및 `reduction` 절 ([section 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) 환경 변수
- [순서가 지정](#266-ordered-construct) 된 구문
- [schedule](d-using-the-schedule-clause.md) 절

### <a name="242-sections-construct"></a>2.4.2 sections sections 구문

`sections`지시문은 팀의 여러 스레드 간에 나눌 구문 집합을 지정 하는 비 반복적인 작업 공유 구문을 식별 합니다. 각 섹션은 팀의 스레드에 의해 한 번 실행 됩니다. 지시문의 구문은 다음과 같습니다 `sections` .

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

절은 다음 중 하나입니다.

- `private(`*변수 목록*`)`
- `firstprivate(`*변수 목록*`)`
- `lastprivate(`*변수 목록*`)`
- `reduction(`*연산자* `:` *변수 목록*  `)`
- `nowait`

`section`첫 번째 섹션에서 지시문은 선택 사항 이지만 각 섹션 앞에는 지시문이 `section` 있습니다. 지시문은 `section` 지시문의 어휘 범위 내에 표시 되어야 합니다 `sections` . `sections`가 지정 되지 않은 경우 생성자의 끝에 암시적 장벽이 있습니다 `nowait` .

지시문에 대 한 제한 사항은 다음과 같습니다 `sections` .

- 지시문은 `section` 지시문의 어휘 범위 밖에 서 나타나지 않아야 합니다 `sections` .

- `nowait`지시문에는 단일 절만 사용할 수 있습니다 `sections` .

#### <a name="cross-references"></a>상호 참조

- `private`, `firstprivate` , `lastprivate` 및 `reduction` 절 ([section 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 단일 구문

`single`지시문은 연결 된 구조적 블록이 팀의 한 스레드에서만 실행 되도록 지정 하는 생성자를 식별 합니다 (마스터 스레드 일 필요는 없음). 지시문의 구문은 다음과 같습니다 `single` .

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

절은 다음 중 하나입니다.

- `private(`*변수 목록*`)`
- `firstprivate(`*변수 목록*`)`
- `copyprivate(`*변수 목록*`)`
- `nowait`

`single`절이 지정 되지 않은 경우 구문 뒤에는 암시적 장벽이 있습니다 `nowait` .

지시문에 대 한 제한 사항은 다음과 같습니다 `single` .

- `nowait`지시문에는 단일 절만 사용할 수 있습니다 `single` .
- 절은 절 `copyprivate` 과 함께 사용 하지 않아야 합니다 `nowait` .

#### <a name="cross-references"></a>상호 참조

- `private`, `firstprivate` 및 `copyprivate` 절 ([section 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 결합 된 병렬 작업 공유 구문

결합 된 병렬 작업 공유 구문은 작업 공유 구문이 하나만 있는 병렬 영역을 지정 하기 위한 바로 가기입니다. 이러한 지시문의 의미 체계는 지시문을 명시적으로 지정 하 고 `parallel` 그 다음에 단일 작업 공유 생성자를 사용 하는 것과 같습니다.

다음 섹션에서는 결합 된 병렬 작업 공유 구문에 대해 설명 합니다.

- [parallel for](#251-parallel-for-construct) 지시문
- [parallel sections](#252-parallel-sections-construct) 지시문

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for 구문

`parallel for`지시어는 `parallel` 단일 지시문만 포함 된 영역에 대 한 바로 가기입니다 `for` . 지시문의 구문은 다음과 같습니다 `parallel for` .

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

이 지시문을 사용 하면 절을 제외 하 고 지시문 및 지시문의 모든 절을 사용 하 여 `parallel` `for` `nowait` 의미와 제한 사항이 동일 합니다. 의미 체계는 지시문이 바로 뒤에 오는 지시문을 명시적으로 지정 하는 것과 같습니다 `parallel` `for` .

#### <a name="cross-references"></a>상호 참조

- [parallel](#23-parallel-construct) 지시문
- [for](#241-for-construct) 지시문
- [데이터 특성 절](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections 구문

`parallel sections`지시문은 `parallel` 단일 지시문만 있는 영역을 지정 하기 위한 바로 가기 폼을 제공 합니다 `sections` . 의미 체계는 지시문이 바로 뒤에 오는 지시문을 명시적으로 지정 하는 것과 같습니다 `parallel` `sections` . 지시문의 구문은 다음과 같습니다 `parallel sections` .

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

절 *은* `parallel` 절을 제외 하 고 및 지시문에서 허용 하는 절 중 하나일 수 있습니다 `sections` `nowait` .

#### <a name="cross-references"></a>상호 참조

- [parallel](#23-parallel-construct) 지시문
- [sections](#242-sections-construct) 지시문

## <a name="26-master-and-synchronization-directives"></a>2.6 Master 및 synchronization 지시문

다음 섹션에서 설명 합니다.

- [마스터](#261-master-construct) 구문
- [중요](#262-critical-construct) 구문
- [장벽](#263-barrier-directive) 지시문
- [atomic](#264-atomic-construct) 구문
- [flush](#265-flush-directive) 지시문
- [순서가 지정](#266-ordered-construct) 된 구문

### <a name="261-master-construct"></a>2.6.1 master 구문

`master`지시문은 팀의 마스터 스레드에서 실행 되는 구조화 된 블록을 지정 하는 구문을 식별 합니다. 지시문의 구문은 다음과 같습니다 `master` .

```cpp
#pragma omp master new-linestructured-block
```

팀의 다른 스레드에서는 연결 된 구조적 블록을 실행 하지 않습니다. 마스터 구문에서 항목을 입력 하거나 종료 하는 경우에는 묵시적 장벽이 없습니다.

### <a name="262-critical-construct"></a>2.6.2 critical 중요 구문

지시문은 한 `critical` 번에 하나의 스레드로 연결 된 구조적 블록의 실행을 제한 하는 구문을 식별 합니다. 지시문의 구문은 다음과 같습니다 `critical` .

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

선택적 *이름은* 중요 한 영역을 식별 하는 데 사용할 수 있습니다. 중요 한 영역을 식별 하는 데 사용 되는 식별자에는 외부 링크가 있으며 레이블, 태그, 멤버 및 일반 식별자에 사용 되는 이름 공백과는 별개의 이름 공간에 있습니다.

스레드는 다른 스레드가 동일한 이름을 사용 하 여 중요 한 영역 (프로그램의 어디에 있는)을 실행 하 고 있지 않을 때까지 위험 영역 시작 시 대기 합니다. 명명 되지 않은 `critical` 지시문은 모두 동일한 지정 되지 않은 이름에 매핑됩니다.

### <a name="263-barrier-directive"></a>2.6.3 장벽 지시문

`barrier`지시문은 팀의 모든 스레드를 동기화 합니다. 발생 한 경우 팀의 각 스레드는 다른 모든 스레드가이 지점에 도달할 때까지 대기 합니다. 지시문의 구문은 다음과 같습니다 `barrier` .

```cpp
#pragma omp barrier new-line
```

팀의 모든 스레드가 장벽을 발견 한 후에는 팀의 각 스레드가 장벽 지시문 후에 문을 병렬로 실행 하기 시작 합니다. 지시문에는 `barrier` 해당 구문의 일부로 C 언어 문이 없으므로 프로그램 내에서의 배치에 몇 가지 제한 사항이 있습니다. 정식 문법에 대 한 자세한 내용은 [부록 C](c-openmp-c-and-cpp-grammar.md)를 참조 하세요. 아래 예제에서는 이러한 제한 사항을 보여 줍니다.

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 atomic 구문

`atomic`지시문을 사용 하면 동시에 여러 스레드를 쓸 수 있는 가능성에 노출 하는 대신 특정 메모리 위치가 원자 단위로 업데이트 됩니다. 지시문의 구문은 다음과 같습니다 `atomic` .

```cpp
#pragma omp atomic new-lineexpression-stmt
```

식 문에는 다음 형식 중 하나가 있어야 합니다.

- *x binop* `=` *expr*
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

위의 식에서 다음을 수행 합니다.

- *x* 는 스칼라 형식의 lvalue 식입니다.

- *expr* 은 스칼라 형식의 식이 며 *x* 로 지정 된 개체를 참조 하지 않습니다.

- *binop* 는 오버 로드 된 연산자가 아니며,,,,,,, 또는 중 하나입니다 `+` `*` `-` `/` `&` `^` `|` `<<` `>>` .

구현에서 모든 `atomic` 지시문을 동일한 고유 이름을 가진 지시문으로 바꿀지 여부를 구현 정의 하지만 `critical` 지시문은  `atomic` 더 나은 최적화를 허용 합니다. 최소한의 오버 헤드로 원자성 업데이트를 수행할 수 있는 하드웨어 지침이 종종 있습니다.

*X* 로 지정 된 개체의 로드와 저장소만 원자성입니다. *expr* 계산은 원자성이 아닙니다. 경합 상태를 방지 하려면 경합 상태가 아닌 `atomic` 것으로 알려진 상태를 제외 하 고 모든 위치의 업데이트를 병렬로 보호 해야 합니다.

지시문에 대 한 제한 사항은 다음과 같습니다 `atomic` .

- 프로그램 전체의 저장소 위치 x에 대 한 모든 원자성 참조에는 호환 되는 형식이 있어야 합니다.

#### <a name="examples"></a>예제

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 flush 지시문

`flush`지시문은 명시적 또는 묵시적 인지 여부에 관계 없이, 팀의 모든 스레드가 메모리의 특정 개체 (아래 지정 된)를 일관 되 게 볼 수 있도록 하기 위해 구현이 필요한 "크로스 스레드" 시퀀스 위치를 지정 합니다. 즉, 이러한 개체를 참조 하는 식의 이전 평가가 완료 되 고 후속 평가가 아직 시작 되지 않은 것입니다. 예를 들어 컴파일러는 레지스터에서 개체의 값을 메모리에 복원 해야 하며, 하드웨어에서 쓰기 버퍼를 메모리로 플러시하고 메모리에서 개체의 값을 다시 로드 해야 할 수 있습니다.

지시문의 구문은 다음과 같습니다 `flush` .

```cpp
#pragma omp flush [(variable-list)]  new-line
```

동기화 해야 하는 개체를 모두 변수로 지정할 수 있는 경우 해당 변수를 선택적 *변수 목록* 에 지정할 수 있습니다. *변수가 목록* 에 있는 경우 포인터가 참조 하는 개체가 아니라 포인터 자체가 플러시됩니다.

`flush` *변수 목록이* 없는 지시어는 액세스할 수 없는 개체를 제외한 모든 공유 개체를 자동 저장 기간으로 동기화 합니다. 이는 `flush` *변수 목록을* 사용 하는 것 보다 더 많은 오버 헤드가 있을 수 있습니다. `flush` *변수 목록이* 없는 지시문은 다음 지시문에 대해 암시 됩니다.

- `barrier`
- 에서 시작 하 여 종료 `critical`
- 에서 시작 하 여 종료 `ordered`
- 에서 시작 하 여 종료 `parallel`
- 종료 시 `for`
- 종료 시 `sections`
- 종료 시 `single`
- 에서 시작 하 여 종료 `parallel for`
- 에서 시작 하 여 종료 `parallel sections`

절이 있는 경우에는 지시문이 포함 되지 않습니다 `nowait` . `flush`지시문은 다음에 대해 암시 되지 않습니다.

- 입력 시 `for`
- 에서 시작 또는 종료 `master`
- 입력 시 `sections`
- 입력 시 `single`

Volatile 정규화 형식을 사용 하 여 개체의 값에 액세스 하는 참조는 `flush` 이전 시퀀스 위치에서 해당 개체를 지정 하는 지시문이 있는 것 처럼 동작 합니다. Volatile 정규화 된 형식으로 개체의 값을 수정 하는 참조는 `flush` 후속 시퀀스 위치에서 해당 개체를 지정 하는 지시문이 있는 것 처럼 동작 합니다.

지시문에는 `flush` 해당 구문의 일부로 C 언어 문이 없으므로 프로그램 내에서의 배치에 몇 가지 제한 사항이 있습니다. 정식 문법에 대 한 자세한 내용은 [부록 C](c-openmp-c-and-cpp-grammar.md)를 참조 하세요. 아래 예제에서는 이러한 제한 사항을 보여 줍니다.

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

지시문에 대 한 제한 사항은 다음과 같습니다 `flush` .

- 지시문에 지정 된 변수는 `flush` 참조 형식이 아니어야 합니다.

### <a name="266-ordered-construct"></a>2.6.6 정렬 된 구문

지시문 뒤에 나오는 구조화 된 블록은 `ordered` 반복이 순차 루프에서 실행 되는 순서 대로 실행 됩니다. 지시문의 구문은 다음과 같습니다 `ordered` .

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered`지시문은 또는 구문의 동적 범위 내에 있어야 합니다 `for` `parallel for` . `for`구문이 바인딩하는 또는 지시문에는 `parallel for` `ordered` `ordered` [2.4.1 섹션](#241-for-construct)에 설명 된 대로 지정 된 절이 있어야 합니다. 절을 사용 하 여 `for` 또는 생성자를 실행 하는 경우 `parallel for` `ordered` `ordered` 구문은 루프의 순차적 실행에서 실행 되는 순서 대로 엄격 하 게 실행 됩니다.

지시문에 대 한 제한 사항은 다음과 같습니다 `ordered` .

- 구문이 있는 루프의 반복은 `for` 순서가 동일한 동일한 지시문을 두 번 이상 실행 해서는 안 되며 지시문을 두 개 이상 실행 해서는 안 `ordered` 됩니다.

## <a name="27-data-environment"></a>2.7 데이터 환경

이 섹션에서는 다음과 같이 병렬 영역을 실행 하는 동안 데이터 환경을 제어 하기 위한 지시문과 여러 절을 제공 합니다.

- [Threadprivate](#271-threadprivate-directive) 지시문을 제공 하 여 파일 범위, 네임 스페이스 범위 또는 정적 블록 범위 변수를 스레드에 로컬로 만듭니다.

- 병렬 또는 작업 공유 구문 동안 변수의 공유 특성을 제어 하기 위해 지시문에 지정할 수 있는 절은 [2.7.2 섹션](#272-data-sharing-attribute-clauses)에 설명 되어 있습니다.

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 지시문

`threadprivate`지시문을 사용 하면 *변수 목록* 에 지정 된 명명 된 파일 범위, 네임 스페이스 범위 또는 정적 블록 범위 변수가 스레드에 대해 전용으로 설정 됩니다. *변수 목록* 은 불완전 한 형식이 없는 변수를 쉼표로 구분한 목록입니다. 지시문의 구문은 다음과 같습니다 `threadprivate` .

```cpp
#pragma omp threadprivate(variable-list) new-line
```

변수의 각 복사본 `threadprivate` 은 해당 복사본에 대 한 첫 번째 참조 전에 프로그램의 지정 되지 않은 지점에서 한 번 초기화 되며, 일반적인 방식 (예: 프로그램의 직렬 실행에서 마스터 복사본이 초기화 됨)에 의해 초기화 됩니다. 변수의 명시적 이니셜라이저에서 개체가 참조 되 `threadprivate` 고 개체의 값이 변수 복사본에 대 한 첫 번째 참조 이전에 수정 된 경우에는 동작이 지정 되지 않습니다.

모든 private 변수와 마찬가지로 스레드는 다른 스레드의 개체 복사본을 참조 하지 않아야 합니다 `threadprivate` . 프로그램의 직렬 지역 및 마스터 영역 중에 참조는 개체의 마스터 스레드의 복사본에 대 한 참조입니다.

첫 번째 병렬 지역이 실행 된 후에는 `threadprivate` 동적 스레드 메커니즘이 사용 하지 않도록 설정 되어 있고 스레드 수가 모든 병렬 영역에 대해 변경 되지 않은 경우에만 개체의 데이터가 유지 되도록 보장 됩니다.

지시문에 대 한 제한 사항은 다음과 같습니다 `threadprivate` .

- `threadprivate`파일 범위 또는 네임 스페이스 범위 변수에 대 한 지시문은 모든 정의 또는 선언 외부에 표시 되어야 하며, 목록에 있는 모든 변수에 대 한 모든 참조의 앞에와 야 합니다.

- 파일 또는 네임 스페이스 범위에서 지시문의 *변수 목록* 에 있는 각 변수는 `threadprivate` 어휘 앞에 있는 파일 또는 네임 스페이스 범위에서 변수 선언을 참조 해야 합니다.

- `threadprivate`정적 블록 범위 변수에 대 한 지시문은 중첩 된 범위가 아니라 변수의 범위에 나타나야 합니다. 지시문은 목록에 있는 모든 변수에 대 한 모든 참조를 어휘 적으로 붙여야 합니다.

- 블록 범위에서 지시문의 *변수 목록* 에 있는 각 변수는 `threadprivate` 어휘 앞에 있는 것과 동일한 범위에서 변수 선언을 참조 해야 합니다. 변수 선언에는 정적 저장소 클래스 지정자를 사용 해야 합니다.

- 변수가 `threadprivate` 하나의 변환 단위에서 지시문에 지정 된 경우 `threadprivate` 선언 된 모든 변환 단위에서 지시문에 지정 해야 합니다.

- `threadprivate`변수는 `copyin` ,, `copyprivate` `schedule` , `num_threads` 또는 `if` 절을 제외한 모든 절에 표시 되지 않아야 합니다.

- `threadprivate`변수 주소가 주소 상수가 아닙니다.

- `threadprivate`변수에 불완전 한 형식 또는 참조 형식이 없어야 합니다.

- `threadprivate`비 POD 클래스 형식의 변수에는 명시적 이니셜라이저로 선언 된 경우 액세스할 수 있고 모호 하지 않은 복사 생성자가 있어야 합니다.

다음 예제에서는 이니셜라이저에 표시 되는 변수를 수정 하 여 지정 되지 않은 동작을 유발할 수 있는 방법 및 보조 개체와 복사 생성자를 사용 하 여이 문제를 방지 하는 방법을 보여 줍니다.

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>상호 참조

- [동적 스레드](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) 환경 변수

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 데이터 공유 특성 절

사용자가 지역 기간 동안 변수의 공유 특성을 제어할 수 있도록 하는 절을 허용 하는 절이 여러 개 있습니다. 특성 절 공유는 절이 표시 되는 지시문의 어휘 익스텐트의 변수에만 적용 됩니다. 모든 지시문에서 다음 절은 모두 허용 되지 않습니다. 특정 지시문에 유효한 절 목록은 지시문을 사용 하 여 설명 합니다.

병렬 또는 작업 공유 구문이 나타날 때 변수가 표시 되 고 공유 특성 절 또는 지시문에 변수가 지정 되지 않은 경우 `threadprivate` 변수가 공유 됩니다. 병렬 영역의 동적 범위 내에서 선언 된 정적 변수는 공유 됩니다. 힙에 할당 된 메모리 (예: `malloc()` c 또는 c + +에서 사용 또는 **`new`** c + +의 경우)는 공유 됩니다. 그러나이 메모리에 대 한 포인터는 개인 또는 공유 일 수 있습니다. 병렬 영역의 동적 범위 내에서 선언 된 자동 저장 기간이 있는 변수는 전용입니다.

대부분의 절은 표시 되는 쉼표로 구분 된 변수 목록 인 *변수 목록* 인수를 허용 합니다. 데이터 공유 특성 절에서 참조 되는 변수가 템플릿에서 파생 된 형식을 가지 며 프로그램에 해당 변수에 대 한 다른 참조가 없는 경우 동작은 정의 되지 않습니다.

지시문 절 내에 표시 되는 모든 변수는 표시 되어야 합니다. 필요에 따라 절이 반복 될 수 있지만 둘 이상의 절에는 변수를 지정할 수 없습니다. 단,와 절 모두에서 변수를 지정할 수 있습니다 `firstprivate` `lastprivate` .

다음 섹션에서는 데이터 공유 특성 절에 대해 설명 합니다.

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [공유할](#2724-shared)
- [default](#2725-default)
- [적](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private`절은 변수 목록의 변수를 팀의 각 스레드에 대해 private으로 선언 합니다. 절의 구문은 다음과 같습니다 `private` .

```cpp
private(variable-list)
```

절에 지정 된 변수의 동작은 다음과 같습니다 `private` . 자동 저장 기간이 있는 새 개체가 구문에 할당 됩니다. 새 개체의 크기와 맞춤은 변수의 유형에 따라 결정 됩니다. 이 할당은 팀의 각 스레드에 대해 한 번 발생 하며 필요한 경우 클래스 개체에 대해 기본 생성자가 호출 됩니다. 그렇지 않으면 초기 값이 결정 되지 않습니다.  변수에 의해 참조 되는 원래 개체는 구문에 대 한 엔트리에서 결정 되지 않은 값을 가지 며, 구문의 동적 범위 내에서 수정 되지 않아야 하 고, 구문 종료 시 결정 되지 않은 값이 있습니다.

지시문 구문의 어휘 범위에서 변수는 스레드에 의해 할당 된 새 private 개체를 참조 합니다.

절에 대 한 제한 사항은 다음과 같습니다 `private` .

- 절에 지정 된 클래스 형식의 변수에는 `private` 액세스 가능 하 고 명확한 기본 생성자가 있어야 합니다.

- 절에 지정 된 변수는 `private` **`const`** 멤버가 있는 클래스 형식이 없는 경우 정규화 된 형식이 아니어야 합니다 `mutable` .

- 절에 지정 된 변수는 `private` 불완전 한 형식 또는 참조 형식 이어야 합니다.

- 지시문의 절에 나타나는 변수는 `reduction` `parallel` `private` 병렬 구문에 바인딩하는 작업 공유 지시문의 절에 지정할 수 없습니다.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate`절은 절에서 제공 하는 기능의 상위 집합을 제공 합니다 `private` . 절의 구문은 다음과 같습니다 `firstprivate` .

```cpp
firstprivate(variable-list)
```

*변수 목록* 에 지정 된 변수에는 `private` [2.7.2.1 섹션](#2721-private)에 설명 된 대로 절 의미 체계가 있습니다. 초기화 또는 생성은 스레드의 생성자 실행 전에 스레드 당 한 번 수행 된 것 처럼 수행 됩니다. `firstprivate`병렬 구문의 경우 새 private 개체의 초기 값은이를 발견 하는 스레드에 대 한 병렬 구문 바로 앞에 존재 하는 원래 개체의 값입니다. `firstprivate`작업 공유 구문에 대 한 절의 초기 값은 작업 공유 구문을 실행 하는 각 스레드에 대 한 새 private 개체의 초기 값입니다 .이 값은 동일한 스레드가 작업 공유 구문을 발견 하는 시점 이전에 존재 하는 원래 개체의 값입니다. 또한 c + + 개체의 경우 각 스레드에 대 한 새 private 개체는 원래 개체에서 복사 생성 됩니다.

절에 대 한 제한 사항은 다음과 같습니다 `firstprivate` .

- 절에 지정 된 변수는 `firstprivate` 불완전 한 형식 또는 참조 형식 이어야 합니다.

- 로 지정 된 클래스 형식의 변수에는 `firstprivate` 액세스 가능 하 고 명확한 복사 생성자가 있어야 합니다.

- 병렬 지역 내에서 전용 이거나 지시문의 절에 나타나는 변수는 `reduction` `parallel` `firstprivate` 병렬 구문에 바인딩하는 작업 공유 지시문의 절에 지정할 수 없습니다.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`절은 절에서 제공 하는 기능의 상위 집합을 제공 합니다 `private` . 절의 구문은 다음과 같습니다 `lastprivate` .

```cpp
lastprivate(variable-list)
```

*변수 목록* 에 지정 된 변수에는 `private` 절 의미 체계가 있습니다. `lastprivate`작업 공유 구문을 식별 하는 지시문에 절이 표시 되 면 `lastprivate` 연결 된 루프의 순차적 마지막 반복에서 각 변수의 값 또는 어휘 적 last section 지시어가 변수의 원래 개체에 할당 됩니다. 또는 지시문의 마지막 반복 또는 또는 지시문의 어휘 마지막 섹션에 의해 값이 할당 되지 않은 변수는 `for` `parallel for` `sections` `parallel sections` 구문 다음에 비활성화 된 값을 갖습니다. 또한 할당 되지 않은 하위 개체가 구문 뒤에 확정 되지 않은 값을 갖습니다.

절에 대 한 제한 사항은 다음과 같습니다 `lastprivate` .

- 에 대 한 모든 제한이 `private` 적용 됩니다.

- 로 지정 된 클래스 형식의 변수에는 `lastprivate` 액세스 가능 하 고 명확한 복사 할당 연산자가 있어야 합니다.

- 병렬 지역 내에서 전용 이거나 지시문의 절에 나타나는 변수는 `reduction` `parallel` `lastprivate` 병렬 구문에 바인딩하는 작업 공유 지시문의 절에 지정할 수 없습니다.

#### <a name="2724-shared"></a>2.7.2.4 공유됨

이 절은 팀의 모든 스레드 간에 *변수 목록* 에 표시 되는 변수를 공유 합니다. 팀의 모든 스레드는 변수의 동일한 저장소 영역에 액세스 `shared` 합니다.

절의 구문은 다음과 같습니다 `shared` .

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 기본값

`default`절을 사용 하면 사용자가 변수의 데이터 공유 특성에 영향을 줄 수 있습니다. 절의 구문은 다음과 같습니다 `default` .

```cpp
default(shared | none)
```

를 지정 `default(shared)` 하는 것은 `shared` 또는 정규화 되지 않은 경우 절에 현재 표시 되는 각 변수를 명시적으로 나열 하는 것과 같습니다 `threadprivate` **`const`** . 명시적 `default` 절이 없으면 기본 동작은가 지정 된 것과 동일 합니다 `default(shared)` .

를 지정 `default(none)` 하려면 병렬 구문의 어휘 범위에서 변수에 대 한 모든 참조에 대해 다음 중 하나 이상을 충족 해야 합니다.

- 변수는 참조를 포함 하는 구문의 데이터 공유 특성 절에 명시적으로 나열 됩니다.

- 변수는 병렬 구문 내에서 선언 됩니다.

- `threadprivate`변수가 인 경우

- 변수에는 정규화 된 **`const`** 형식이 있습니다.

- 변수는 또는 지시문 바로 다음에 오는 루프 제어 변수 이며 `for` `for` `parallel for` 루프 내에 변수 참조가 나타납니다.

`firstprivate`포함 된 지시문의, 또는 절에 변수를 지정 `lastprivate` `reduction` 하면 바깥쪽 컨텍스트의 변수에 대 한 암시적 참조가 발생 합니다. 이러한 암시적 참조에는 위에 나열 된 요구 사항도 적용 됩니다.

`default`지시문에는 단일 절만 지정할 수 있습니다 `parallel` .

`private` `firstprivate` `lastprivate` `reduction` `shared` 다음 예제에서 보여 주는 것 처럼,,, 및 절을 사용 하 여 변수의 기본 데이터 공유 특성을 재정의할 수 있습니다.

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

이 절은 *op* 연산자를 사용 하 여 *변수 목록* 에 나타나는 스칼라 변수를 축소 합니다. 절의 구문은 다음과 같습니다 `reduction` .

`reduction(`*op* `:` *변수 목록*`)`

일반적으로 다음 형식 중 하나를 사용 하 여 문에 대해 감소를 지정 합니다.

- *x* `=` *x* *op* *식*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x*  (빼기 제외)
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

여기서

*x*<br/>
목록에 지정 된 감소 변수 중 하나입니다.

*변수 목록*<br/>
스칼라 환산 변수의 쉼표로 구분 된 목록입니다.

*expr*<br/>
*X* 를 참조 하지 않는 스칼라 형식의 식입니다.

*op*<br/>
오버 로드 된 연산자가 아닌,,,,,, 또는 중 하나 `+` `*` `-` `&` `^` `|` `&&` `||` 입니다.

*binop*<br/>
오버 로드 된 연산자가 아닌,,,, 또는 중 하나 `+` `*` `-` `&` `^` `|` 입니다.

다음은 절의 예입니다 `reduction` .

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

예제에 표시 된 것 처럼 함수 호출 내에서 연산자를 숨길 수 있습니다. 사용자는 절에 지정 된 연산자가 감소 작업과 일치 하는지 주의 해야 합니다 `reduction` .

이 예제에서는 연산자의 오른쪽 피연산자에 `||` 부작용이 없지만이 연산자는 허용 되지만 주의 해 서 사용 해야 합니다. 이 컨텍스트에서 루프를 순차적으로 실행 하는 동안 발생 하지 않는 부작용은 병렬 실행 중에 발생할 수 있습니다. 이러한 차이는 반복의 실행 순서가 결정 되지 않기 때문에 발생할 수 있습니다.

연산자는 축소를 위해 컴파일러에서 사용 하는 모든 전용 변수의 초기 값을 확인 하 고 종료 연산자를 결정 하는 데 사용 됩니다. 연산자를 명시적으로 지정 하면 reduction 문이 구문의 어휘 범위를 벗어날 수 있습니다. 지시문에는 개수에 관계 없이 `reduction` 절을 지정할 수 있지만 `reduction` 해당 지시문에 대해 최대 하나의 절에 변수가 표시 될 수 있습니다.

절이 사용 된 것 처럼 각 스레드에 대해 하나씩, *변수 목록* 에 있는 각 변수의 전용 복사본이 생성 됩니다 `private` . 전용 복사본은 연산자에 따라 초기화 됩니다 (다음 표 참조).

절이 지정 된 영역의 끝에서 원래 `reduction` 값을 지정 된 연산자를 사용 하 여 각 개인 복사본의 최종 값과 결합 한 결과를 반영 하도록 원래 개체가 업데이트 됩니다. 감소 연산자는 모두 연관 (빼기 제외) 이며 컴파일러는 최종 값의 계산을 자유롭게 다시 연결할 수 있습니다. (빼기 감소의 일부 결과는 최종 값을 구성 하기 위해 추가 됩니다.)

첫 번째 스레드가 포함 하는 절에 도달 하 고 감소 계산이 완료 될 때까지 유지 되는 경우에는 원래 개체의 값이 결정 되지 않습니다.  일반적으로 계산은 구문이 끝날 때 완료 됩니다. 그러나 `reduction` 이 절이 적용 되는 구문에서 사용 되는 경우에는 `nowait` 모든 스레드가 절을 완료할 수 있도록 장벽 동기화가 수행 될 때까지 원래 개체의 값은 확정 되지 않은 상태로 유지 됩니다 `reduction` .

다음 표에서는 유효한 연산자와 해당 정식 초기화 값을 보여 줍니다. 실제 초기화 값은 감소 변수의 데이터 형식과 일치 해야 합니다.

|연산자|초기화|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

절에 대 한 제한 사항은 다음과 같습니다 `reduction` .

- `reduction`포인터 형식 및 참조 형식이 허용 되지 않는다는 점을 제외 하 고 절의 변수 형식은 reduction 연산자에 대해 유효 해야 합니다.

- 절에 지정 된 변수는 `reduction` 한정 되지 않아야 합니다 **`const`** .

- 병렬 지역 내에서 전용 이거나 지시문의 절에 나타나는 변수는 `reduction` `parallel` `reduction` 병렬 구문에 바인딩하는 작업 공유 지시문의 절에 지정할 수 없습니다.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

`copyin`절은 `threadprivate` 병렬 영역을 실행 하는 팀의 각 스레드에 대해 동일한 값을 변수에 할당 하는 메커니즘을 제공 합니다. 절에 지정 된 각 변수에 대해 `copyin` 팀의 마스터 스레드에 있는 변수의 값은 할당에 따라 병렬 영역의 시작 부분에 있는 스레드 전용 복사본에 복사 됩니다. 절의 구문은 다음과 같습니다 `copyin` .

```cpp

copyin(
variable-list
)
```

절에 대 한 제한 사항은 다음과 같습니다 `copyin` .

- 절에 지정 된 변수에는 `copyin` 액세스 가능 하 고 명확한 복사 할당 연산자가 있어야 합니다.

- 절에 지정 된 변수는 변수 여야 합니다 `copyin` `threadprivate` .

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate`절은 개인 변수를 사용 하 여 팀의 한 멤버에서 다른 멤버로 값을 브로드캐스트하는 메커니즘을 제공 합니다. 이러한 공유 변수를 제공할 때 값에 공유 변수를 사용 하는 대신 사용 하는 것이 더 어려울 수 있습니다. 예를 들어 각 수준에서 다른 변수를 요구 하는 재귀가 발생할 수 있습니다. `copyprivate`절은 지시어에만 나타날 수 있습니다 `single` .

절의 구문은 다음과 같습니다 `copyprivate` .

```cpp

copyprivate(
variable-list
)
```

`copyprivate`변수 목록의 변수에 대 한 절 효과는 구문에 연결 된 구조적 블록을 실행 한 후 `single` , 그리고 팀의 스레드가 구문의 끝에서 장벽을 떠난 후에 발생 합니다. 그런 다음 팀의 다른 모든 스레드에서 *변수 목록* 에 있는 각 변수에 대해 해당 변수는 구문의 구조화 된 블록을 실행 한 스레드의 해당 변수 값을 사용 하 여 할당 된 것으로 정의 됩니다.

절에 대 한 제한 사항은 다음과 같습니다 `copyprivate` .

- 절에 지정 된 변수는 `copyprivate` `private` `firstprivate` 동일한 지시문의 or 절에 표시 되지 않아야 합니다 `single` .

- `single` `copyprivate` 병렬 영역의 동적 범위에서 절이 있는 지시문이 발견 된 경우 절에 지정 된 모든 변수는 `copyprivate` 바깥쪽 컨텍스트에서 private 이어야 합니다.

- 절에 지정 된 변수에는 `copyprivate` 액세스 가능한 명확한 복사 할당 연산자가 있어야 합니다.

## <a name="28-directive-binding"></a>2.8 지시문 바인딩

지시문의 동적 바인딩은 다음 규칙을 따라야 합니다.

- `for`,, `sections` `single` , `master` 및 지시문은 `barrier` `parallel` 해당 지시문에 있을 수 있는 모든 절의 값에 관계 없이 동적으로 바깥쪽 (있는 경우)에 바인딩됩니다 `if` . 병렬 영역을 현재 실행 하 고 있지 않은 경우에는 마스터 스레드만 구성 된 팀에서 지시문을 실행 합니다.

- `ordered`지시문은 동적 바깥쪽에 바인딩됩니다 `for` .

- `atomic`지시문은 `atomic` 현재 팀 뿐만 아니라 모든 스레드의 지시문에 대해 단독 액세스를 적용 합니다.

- `critical`지시문은 `critical` 현재 팀 뿐만 아니라 모든 스레드의 지시문에 대해 단독 액세스를 적용 합니다.

- 지시문은 동적으로 가장 가까운 바깥쪽 바깥쪽의 지시문에 바인딩할 수 없습니다 `parallel` .

## <a name="29-directive-nesting"></a>2.9 지시문 중첩

지시문의 동적 중첩은 다음 규칙을 따라야 합니다.

- `parallel` `parallel` 중첩 된 병렬 처리를 사용 하도록 설정 하지 않는 한, 다른 내부에 있는 지시문은 현재 스레드만 구성 된 새 팀을 논리적으로 설정 합니다.

- `for``sections` `single` 동일한에 바인딩하는, 및 지시문은 서로 `parallel` 중첩 될 수 없습니다.

- `critical` 이름이 같은 지시문은 서로 중첩 될 수 없습니다. 이 제한은 교착 상태를 방지 하는 데 충분 하지 않습니다.

- `for``sections` `single` 지시문이 영역과 동일한에 바인딩하는 경우, 및 지시문 `critical` `ordered` 은, 및 `master` 지역의 동적 범위에서 허용 되지 않습니다 `parallel` .

- `barrier` 지시문이 영역과 동일한에 바인딩하는 경우에는,,,, 및 영역의 동적 범위에서 지시문을 사용할 수 `for` `ordered` `sections` `single` `master` `critical` `parallel` 없습니다.

- `master` 지시문이 `for` `sections` `single` `master` `parallel` 작업 공유 지시문과 동일한에 바인딩하는 경우 지시문은, 및 지시문의 동적 범위에서 허용 되지 않습니다.

- `ordered` 지시문이 영역과 동일한에 바인딩하는 경우 영역의 동적 범위에는 지시문을 사용할 수 `critical` `parallel` 없습니다.

- 병렬 영역 내부에서 실행 될 때 허용 되는 지시문은 병렬 영역 외부에서 실행 되는 경우에도 허용 됩니다. 사용자 지정 병렬 영역 외부에서 동적으로 실행 되는 경우에는 마스터 스레드만 구성 된 팀에서 지시문을 실행 합니다.
