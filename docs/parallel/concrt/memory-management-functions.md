---
description: '자세히 알아보기: 메모리 관리 함수'
title: 메모리 관리 함수
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: d75778f99294c1a177ac204bb0fb96c3ee84422c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205540"
---
# <a name="memory-management-functions"></a>메모리 관리 함수

이 문서에서는 동시에 메모리를 할당 하 고 해제 하는 데 도움이 되는 동시성 런타임에서 제공 하는 메모리 관리 함수에 대해 설명 합니다.

> [!TIP]
> 동시성 런타임은 기본 스케줄러를 제공하므로 애플리케이션에서 스케줄러를 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

동시성 런타임는 동시에 메모리 블록을 할당 하 고 해제 하는 데 최적화 된 두 개의 메모리 관리 함수를 제공 합니다. [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) 함수는 지정 된 크기를 사용 하 여 메모리 블록을 할당 합니다. [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) 함수는에 의해 할당 된 메모리를 해제 합니다 `Alloc` .

> [!NOTE]
> `Alloc`및 `Free` 함수는 서로를 사용 합니다. 함수는 `Free` 함수를 사용 하 여 할당 하는 메모리를 해제 하는 데만 사용 `Alloc` 합니다. 또한 함수를 사용 하 여 메모리를 할당 하는 경우 함수를 사용 하 여 `Alloc` `Free` 해당 메모리를 해제 합니다.

`Alloc` `Free` 다른 스레드나 작업에서 고정 된 할당 크기 집합을 할당 하 고 해제할 때 및 함수를 사용 합니다. 동시성 런타임는 C 런타임 힙에서 할당 하는 메모리를 캐시 합니다. 동시성 런타임는 실행 중인 각 스레드에 대해 별도의 메모리 캐시를 보유 합니다. 따라서 런타임은 잠금이나 메모리 장벽을 사용 하지 않고 메모리를 관리 합니다. 응용 프로그램은 `Alloc` `Free` 메모리 캐시가 더 자주 액세스 될 때 및 함수에서 더 많은 혜택을 제공 합니다. 예를 들어 및를 자주 호출 하는 스레드는 `Alloc` `Free` 주로 또는를 호출 하는 스레드 보다 더 많은 혜택을 제공 합니다 `Alloc` `Free` .

> [!NOTE]
> 이러한 메모리 관리 함수를 사용 하 고 응용 프로그램에서 많은 메모리를 사용 하는 경우 응용 프로그램은 원하는 것 보다 더 빠른 메모리 부족 상태를 입력할 수 있습니다. 한 스레드에 의해 캐시 되는 메모리 블록을 다른 스레드에서 사용할 수 없으므로 한 스레드에 많은 메모리가 있는 경우 해당 메모리를 사용할 수 없습니다.

## <a name="example"></a>예제

및 함수를 사용 하 여 `Alloc` `Free` 메모리 성능을 향상 시키는 예제는 [방법: Alloc 및 Free를 사용 하 여 메모리 성능 향상](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[방법: Alloc 및 Free를 사용 하 여 메모리 성능 개선](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
