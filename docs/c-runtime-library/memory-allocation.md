---
title: 메모리 할당
ms.date: 11/18/2020
description: 메모리를 할당, 해제 및 다시 할당 하는 데 사용 되는 Microsoft C 런타임 함수 목록입니다.
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.openlocfilehash: 39be48a4ebdf8ee917395d7b743846196200878d
ms.sourcegitcommit: e82e13b80150fcb27a1387018aafb00d99a3827a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94920744"
---
# <a name="memory-allocation"></a>메모리 할당

이러한 루틴은 메모리를 할당, 해제 및 다시 할당 합니다.

## <a name="memory-allocation-routines"></a>메모리 할당 루틴

|루틴에서 반환된 값|용도|
|-------------|---------|
|[`_alloca`](../c-runtime-library/reference/alloca.md), [`_malloca`](../c-runtime-library/reference/malloca.md)|스택에서 메모리를 할당 합니다.|
|[`calloc`](../c-runtime-library/reference/calloc.md)|배열을 할당 하 고 해당 요소를 0 (영)으로 초기화 합니다.|
|[`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md)|의 디버그 버전입니다 **`calloc`** . 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`operator delete`, `operator delete[]`](../c-runtime-library/delete-operator-crt.md)|힙에 할당 된 사용 가능한 메모리 |
|[`_expand`](../c-runtime-library/reference/expand.md)|이동 하지 않고 메모리 블록을 확장 하거나 축소 합니다.|
|[`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md)|의 디버그 버전입니다 **`_expand`** . 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`free`](../c-runtime-library/reference/free.md)|힙에 할당 된 사용 가능한 메모리|
|[`_free_dbg`](../c-runtime-library/reference/free-dbg.md)|의 디버그 버전입니다 **`free`** . 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`_freea`](../c-runtime-library/reference/freea.md)|스택에 할당 된 사용 가능한 메모리|
|[`_get_heap_handle`](../c-runtime-library/reference/get-heap-handle.md)|`HANDLE`CRT (C 런타임) 힙으로 Win32를 가져옵니다.|
|[`_heapadd`](../c-runtime-library/heapadd.md)|힙에 메모리 추가|
|[`_heapchk`](../c-runtime-library/reference/heapchk.md)|일관성을 위해 힙 확인|
|[`_heapmin`](../c-runtime-library/reference/heapmin.md)|힙에서 사용 하지 않는 메모리 해제|
|[`_heapset`](../c-runtime-library/heapset.md)|값을 사용 하 여 빈 힙 항목 채우기|
|[`_heapwalk`](../c-runtime-library/reference/heapwalk.md)|힙의 각 항목에 대 한 정보를 가져옵니다.|
|[`malloc`](../c-runtime-library/reference/malloc.md)|힙에서 메모리 할당|
|[`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md)|의 디버그 버전 **`malloc`** , 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`_msize`](../c-runtime-library/reference/msize.md)|할당 된 메모리 블록의 크기를 반환 합니다.|
|[`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md)|의 디버그 버전 **`_msize`** , 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`new`, `new[]`](../c-runtime-library/new-operator-crt.md)|힙에서 메모리 블록을 할당 합니다.|
|[`_query_new_handler`](../c-runtime-library/reference/query-new-handler.md)|로 설정 된 현재 새 처리기 루틴의 주소를 가져옵니다. **`_set_new_handler`**|
|[`_query_new_mode`](../c-runtime-library/reference/query-new-mode.md)|에 대해로 설정 된 새 처리기 모드 가져오기 **`_set_new_mode`****`malloc`**|
|[`realloc`](../c-runtime-library/reference/realloc.md)|새 크기로 블록 다시 할당|
|[`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md)|의 디버그 버전 **`realloc`** , 런타임 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.|
|[`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md)|**`new`** 연산자가 메모리 할당에 실패 하 고 c + + 표준 라이브러리의 컴파일을 사용 하도록 설정 하는 경우 오류 처리 메커니즘을 사용 합니다.|
|[`_set_new_mode`](../c-runtime-library/reference/set-new-mode.md)|에 대 한 새 처리기 모드 설정 **`malloc`**|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)