---
description: '자세히 알아보기: F. 버전 2.0의 새로운 기능 및 설명'
title: F. Version 2.0에서 새 기능 및 설명
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 77a27ed6d15986f787297b37a904d4625d649ced
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342467"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Version 2.0에서 새 기능 및 설명

이 부록에서는 버전 1.0에서 버전 2.0로 이동 하는 OpenMP C/c + + 사양에 대 한 주요 변경 내용을 요약 합니다. 다음 항목은 사양에 추가 된 새로운 기능입니다.

- OpenMP [지시문](2-directives.md#21-directive-format)에는 쉼표를 사용할 수 있습니다.

- `num_threads`절 추가. 이 절을 사용 하면 사용자가 [병렬 구문](2-directives.md#23-parallel-construct)에 대해 특정 개수의 스레드를 요청할 수 있습니다.

- [Threadprivate](2-directives.md#271-threadprivate-directive) 지시문이 정적 블록 범위 변수를 허용 하도록 확장 되었습니다.

- C99 가변 길이 배열은 전체 형식이 며, 및 절 목록에서와 같이 전체 형식이 허용 되는 위치에 지정할 수 `private` 있습니다 `firstprivate` `lastprivate` ( [2.7.2 섹션](2-directives.md#272-data-sharing-attribute-clauses)참조).

- 병렬 영역의 private 변수는 중첩 지시문에서 다시 [비공개로](2-directives.md#2721-private) 표시 될 수 있습니다.

- `copyprivate`절이 추가 되었습니다. Private 변수를 사용 하 여 팀의 한 멤버에서 다른 멤버로 값을 브로드캐스트하는 메커니즘을 제공 합니다. 이러한 공유 변수를 제공할 때 값에 공유 변수를 사용 하는 대신 사용 하는 것이 더 어려울 수 있습니다. 예를 들어 각 수준에서 다른 변수를 요구 하는 재귀가 발생할 수 있습니다. [Copyprivate](2-directives.md#2728-copyprivate) 절은 지시문에만 나타날 수 있습니다 `single` .

- [Omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) 및 [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) 에 대 한 타이밍 루틴 추가는 MPI 루틴과 비슷합니다. 이러한 함수는 벽면 클록 타이밍을 수행 하는 데 필요 합니다.

- OpenMP C/c + +의 [구현 정의 동작](e-implementation-defined-behaviors-in-openmp-c-cpp.md) 목록이 포함 된 부록이 추가 되었습니다. 이러한 경우에는 해당 동작을 정의 하 고 문서화 하는 데 구현이 필요 합니다.

- C/c + +에 대 한 이전 OpenMP API 사양의 기능을 명확 하 게 하거나 수정 하려면 다음과 같이 변경 해야 합니다.

  - 0이 아닌 값을 반환 하는 경우 [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) 및 [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) 의 동작이 `omp_in_parallel` 정의 되지 않았습니다.

  - 중첩 된 parallel을 사용할 때 [지시문 중첩](2-directives.md#29-directive-nesting) 이 설명 되었습니다.

  - 병렬 영역에서 [잠금 초기화](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) 및 [잠금 소멸](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) 함수를 호출할 수 있습니다.

  - 새로운 예제가 [부록 a](a-examples.md)에 추가 되었습니다.
