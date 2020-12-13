---
description: 자세한 내용은 다음에 대해 자세히 알아보세요.
title: E. OpenMP C/C++에서 구현이 정의된 동작
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e8ebc8a336578a888ff8a7152552d4381a9d5add
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342480"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. OpenMP C/C++에서 구현이 정의된 동작

이 부록에는이 API의 "구현 정의"로 설명 된 동작이 요약 되어 있습니다.  각 동작은 주 사양에서 해당 설명으로 상호 참조 됩니다.

## <a name="remarks"></a>설명

이러한 경우에는 해당 동작을 정의 하 고 문서화 하는 데 구현이 필요 하지만이 목록은 불완전할 수 있습니다.

- **스레드 수:** 스레드 수를 동적으로 조정 하는 동안 병렬 지역이 발생 하 고 병렬 영역에 대해 요청 된 스레드 수가 런타임 시스템이 제공할 수 있는 수보다 많은 경우 프로그램의 동작은 구현에 정의 되어 있습니다 (9 페이지 참조).

   Visual C++에서 중첩 되지 않은 병렬 영역에 대해 64 스레드 (최대값)가 제공 됩니다.

- **프로세서 수:** 지정 된 시간에 실제로 스레드를 호스트 하는 실제 프로세서 수는 구현에 정의 되어 있습니다 (10 페이지 참조).

   Visual C++에서이 수는 일정 하지 않으며 운영 체제에 의해 제어 됩니다.

- **스레드 팀 만들기:** 중첩 된 병렬 영역을 실행 하는 팀의 스레드 수는 구현에서 정의 됩니다 (10 페이지 참조).

   Visual C++에서이 수는 운영 체제에 의해 결정 됩니다.

- **일정 (런타임):** 예약에 대 한 결정은 런타임까지 지연 됩니다. 환경 변수를 설정 하 여 런타임에 일정 유형 및 청크 크기를 선택할 수 있습니다 `OMP_SCHEDULE` . 이 환경 변수가 설정 되지 않은 경우 결과 일정은 구현 정의 됩니다 (13 페이지 참조).

   Visual C++에서 일정 유형은 `static` 청크 크기가 없는입니다.

- **기본 일정:** Schedule 절이 없는 경우 기본 일정은 구현 정의 됩니다 (13 페이지 참조).

   Visual C++에서 기본 일정 유형은 `static` 청크 크기가 없는입니다.

- **원자성:** 구현에서 모든 지시문을 고유한 이름의 지시문으로 바꿀지 여부를 구현 하 여 정의 `atomic` `critical` 합니다 (20 페이지 참조).

   Visual C++ [원자](reference/openmp-directives.md#atomic) 단위로 수정 된 데이터가 자연 스런 맞춤에 없거나 1 ~ 2 바이트인 경우 해당 속성을 충족 하는 모든 원자성 연산은 하나의 임계 영역을 사용 합니다. 그렇지 않은 경우에는 임계 영역을 사용 하지 않습니다.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** 사용자가 스레드 수를 명시적으로 설정 하지 않은 경우 기본값은 구현 정의 됩니다 (9 페이지 참조).

   Visual C++의 기본 스레드 수는 프로세서 수와 같습니다.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** 동적 스레드 조정의 기본값은 구현에서 정의 됩니다.

   Visual C++에서 기본값은 `FALSE` 입니다.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** 중첩 된 병렬 처리를 사용 하는 경우 중첩 된 병렬 영역을 실행 하는 데 사용 되는 스레드 수는 구현에서 정의 됩니다.

   Visual C++에서 스레드 수는 운영 체제에 의해 결정 됩니다.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) 환경 변수:이 환경 변수의 기본값은 구현에서 정의 됩니다.

   Visual C++에서 일정 유형은 `static` 청크 크기가 없는입니다.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) 환경 변수: 환경 변수에 대 한 값이 지정 되지 `OMP_NUM_THREADS` 않았거나, 지정 된 값이 양의 정수가 아니거나, 값이 시스템에서 지원할 수 있는 최대 스레드 수를 초과 하는 경우 사용할 스레드 수가 구현에 정의 되어 있습니다.

   Visual C++에서 지정 된 값이 0 이하인 경우 스레드 수는 프로세서 수와 같습니다.  값이 64 보다 큰 경우 스레드 수는 64입니다.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) 환경 변수: 기본값은 구현에 정의 된 값입니다.

   Visual C++에서 기본값은 `FALSE` 입니다.
