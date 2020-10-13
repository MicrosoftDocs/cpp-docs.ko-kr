---
title: '방법: 예외 처리를 사용하여 병렬 루프 중단'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: f6842e3093a577289c0c4432d96298e3c7b2bb92
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008505"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>방법: 예외 처리를 사용하여 병렬 루프 중단

이 항목에서는 기본 트리 구조에 대 한 검색 알고리즘을 작성 하는 방법을 보여 줍니다.

항목 [취소](cancellation-in-the-ppl.md) 에서는 병렬 패턴 라이브러리에서 취소의 역할에 대해 설명 합니다. 예외 처리를 사용 하는 것은 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 및 [concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드를 사용 하는 것 보다 병렬 작업을 취소 하는 보다 효율적인 방법입니다. 그러나 작업을 취소 하는 예외 처리를 사용 하는 한 가지 시나리오는 작업 또는 병렬 알고리즘을 사용 하지만 `task_group` 취소할 또는 개체를 제공 하지 않는 타사 라이브러리를 호출 하는 경우입니다 `structured_task_group` .

## <a name="example-basic-tree-type"></a>예: 기본 트리 형식

다음 예에서는 `tree` 데이터 요소와 자식 노드 목록을 포함 하는 기본 형식을 보여 줍니다. 다음 섹션에서는 `for_all` 각 자식 노드에서 작업 함수를 재귀적으로 수행 하는 메서드의 본문을 보여 줍니다.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example-perform-work-in-parallel"></a>예: 병렬로 작업 수행

다음 예제에서는 메서드를 보여 줍니다 `for_all` . [동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 트리의 각 노드에 대해 작업 기능을 병렬로 수행 합니다.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example--search-the-tree-for-a-value"></a>예: 트리에서 값을 검색 합니다.

다음 예제에서는 제공된 `tree` 개체에서 값을 검색하는 `search_for_value` 함수를 보여 줍니다. 이 함수는 제공 된 `for_all` 값을 포함 하는 트리 노드를 찾을 때를 throw 하는 작업 함수를 메서드에 전달 합니다.

`tree`타사 라이브러리에서 클래스를 제공 하 고이를 수정할 수 없다고 가정 합니다. 이 경우 `for_all` 메서드는 `task_group` 호출자에 대해 또는 개체를 제공 하지 않기 때문에 예외 처리를 사용 하는 것이 적절 합니다 `structured_task_group` . 따라서 작업 함수는 부모 작업 그룹을 직접 취소할 수 없습니다.

작업 그룹에 제공 하는 작업 함수가 예외를 throw 하는 경우 런타임은 작업 그룹에 있는 모든 태스크 (자식 작업 그룹 포함)를 중지 하 고 아직 시작 되지 않은 모든 작업을 삭제 합니다. `search_for_value`함수는 블록을 사용 하 여 **`try`** - **`catch`** 예외를 캡처하고 결과를 콘솔에 출력 합니다.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example-create-and-search-a-tree-in-parallel"></a>예: 트리를 병렬로 만들고 검색

다음 예제에서는 개체를 만들고 `tree` 여러 값을 병렬로 검색 합니다. `build_tree`함수는이 항목의 뒷부분에 나와 있습니다.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

이 예제에서는 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 값을 병렬로 검색 합니다. 이 알고리즘에 대 한 자세한 내용은 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="example-finished-exception-handling-code-sample"></a>예: 완료 된 예외 처리 코드 샘플

다음 전체 예제에서는 예외 처리를 사용 하 여 기본 트리 구조에서 값을 검색 합니다.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `task-tree-search.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc task-tree-search**

## <a name="see-also"></a>참조

[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group 클래스](reference/task-group-class.md)<br/>
[structured_task_group 클래스](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each 함수](reference/concurrency-namespace-functions.md#parallel_for_each)
