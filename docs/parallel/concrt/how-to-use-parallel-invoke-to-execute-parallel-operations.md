---
title: '방법: parallel_invoke를 사용하여 병렬 작업 실행'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 62781b2915704c4104bd7e8a13e48e43d81955c6
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008344"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>방법: parallel_invoke를 사용하여 병렬 작업 실행

이 예제에서는 [동시성::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 공유 데이터 원본에 대해 여러 작업을 수행 하는 프로그램의 성능을 향상 시키는 방법을 보여 줍니다. 소스를 수정 하는 작업이 없기 때문에 간단 하 게 병렬로 실행할 수 있습니다.

## <a name="example-create-initialize-and-perform-operations-on-a-variable"></a>예: 변수에 대 한 만들기, 초기화 및 작업 수행

형식의 변수를 만들고 `MyDataType` 함수를 호출 하 여 해당 변수를 초기화 한 다음, 해당 데이터에 대해 여러 개의 긴 작업을 수행 하는 다음 코드 예제를 고려 합니다.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

`lengthy_operation1`, `lengthy_operation2` 및 함수가 변수를 수정 하지 않는 경우에는 `lengthy_operation3` `MyDataType` 추가 수정 없이 이러한 함수를 병렬로 실행할 수 있습니다.

## <a name="example-run-previous-example-in-parallel"></a>예: 이전 예제를 병렬로 실행

다음 예제에서는 이전 예제를 병렬로 실행 하도록 수정 합니다. `parallel_invoke`알고리즘은 각 작업을 병렬로 실행 하 고 모든 작업이 완료 되 면 반환 합니다.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example-perform-multiple-operations-on-a-downloaded-file"></a>예: 다운로드 한 파일에 대해 여러 작업 수행

다음 예에서는 gutenberg.org에서 *the iliad of* by Homer를 다운로드 하 고 해당 파일에 대해 여러 작업을 수행 합니다. 이 예에서는 먼저 이러한 작업을 순차적으로 수행 하 고 동일한 작업을 병렬로 수행 합니다.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

이 예제에서는 알고리즘을 사용 하 여 `parallel_invoke` 동일한 데이터 원본에 대해 작동 하는 여러 함수를 호출 합니다. 알고리즘을 사용 하면 `parallel_invoke` 동일한 데이터에 대해 작동 하는 것 뿐만 아니라 모든 함수 집합을 병렬로 호출할 수 있습니다.

알고리즘은 `parallel_invoke` 각 작업 함수를 병렬로 호출 하므로 해당 성능은 완료 하는 데 가장 긴 시간을 사용 하는 함수에 의해 제한 됩니다. 즉, 런타임이 개별 프로세서에서 각 함수를 처리 하는 경우입니다. 이 예에서는 사용 가능한 프로세서 수보다 더 많은 작업을 병렬로 수행 하는 경우 각 프로세서에서 여러 작업을 실행할 수 있습니다. 이 경우 완료 하는 데 가장 오래 걸리는 태스크 그룹에 의해 성능이 제한 됩니다.

이 예제에서는 세 가지 작업을 병렬로 수행 하므로 프로세서가 3 개 이상 있는 컴퓨터에서는 성능이 저하 되지 않습니다. 성능을 향상 시키려면 가장 오래 실행 되는 작업을 더 작은 작업으로 분할 하 고 해당 작업을 병렬로 실행할 수 있습니다.

`parallel_invoke`취소에 대 한 지원이 필요 하지 않은 경우 [concurrency:: task_group](reference/task-group-class.md) 및 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 클래스 대신 알고리즘을 사용할 수 있습니다. 알고리즘 및 작업 그룹의 사용을 비교 하는 예제는 `parallel_invoke` [방법: Parallel_invoke를 사용 하 여 병렬 정렬 루틴 작성](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)을 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-word-mining.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc/MD/DUNICODE/D_AFXDLL parallel-word-mining**

## <a name="see-also"></a>참조

[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke 함수](reference/concurrency-namespace-functions.md#parallel_invoke)
