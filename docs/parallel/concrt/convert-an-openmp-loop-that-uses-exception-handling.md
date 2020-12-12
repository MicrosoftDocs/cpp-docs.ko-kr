---
description: '자세한 정보: 방법: 예외 처리를 사용 하 여 동시성 런타임를 사용 하는 OpenMP 루프 변환'
title: '방법: 동시성 런타임을 사용하기 위해 예외 처리를 사용하는 OpenMP 루프 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 8258506cfce76361eea151fe6b7f934a04f3a0aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325734"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>방법: 동시성 런타임을 사용하기 위해 예외 처리를 사용하는 OpenMP 루프 변환

이 예제에서는 동시성 런타임 예외 처리 메커니즘을 사용 하도록 예외 처리를 수행 하는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 변환 하는 방법을 보여 줍니다.

OpenMP에서는 병렬 지역에서 throw 되는 예외를 동일한 스레드에서 동일한 지역에서 catch 하 고 처리 해야 합니다. 병렬 영역을 이스케이프 하는 예외는 처리 되지 않은 예외 처리기에 의해 catch 되며 기본적으로 프로세스를 종료 합니다.

동시성 런타임에서 [concurrency:: task_group](reference/task-group-class.md) 또는 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 개체와 같은 작업 그룹에 전달 하는 작업 함수 본문에서 예외를 throw 하거나 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)와 같은 병렬 알고리즘에 전달 하는 경우 런타임은 해당 예외를 저장 하 고 작업 그룹이 나 알고리즘이 완료 되기를 기다리는 컨텍스트로 마샬링합니다. 작업 그룹의 경우 대기 컨텍스트는 [concurrency:: task_group:: wait](reference/task-group-class.md#wait), [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)또는 [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait)를 호출 하는 컨텍스트입니다. 병렬 알고리즘의 경우 대기 컨텍스트는 해당 알고리즘을 호출한 컨텍스트입니다. 또한 런타임은 자식 작업 그룹의 작업을 포함 하 여 작업 그룹에 있는 모든 활성 작업을 중지 하 고 아직 시작 되지 않은 모든 작업을 삭제 합니다.

## <a name="example"></a>예제

이 예제에서는를 호출 하 고 OpenMP 지역에서 예외를 처리 하는 방법을 보여 줍니다 `parallel` `parallel_for` . `do_work`함수는 성공 하지 않은 메모리 할당 요청을 수행 하므로 [std:: bad_alloc](../../standard-library/bad-alloc-class.md)형식의 예외를 throw 합니다. OpenMP를 사용 하는 버전에서는 예외를 throw 하는 스레드도 catch 해야 합니다. 즉, OpenMP 병렬 루프의 각 반복에서 예외를 처리 해야 합니다. 동시성 런타임를 사용 하는 버전에서 주 스레드는 다른 스레드에 의해 throw 된 예외를 catch 합니다.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

OpenMP를 사용 하는이 예제의 버전에서 예외는에서 발생 하며 각 루프 반복에서 처리 됩니다. 동시성 런타임를 사용 하는 버전에서 런타임은 예외를 저장 하 고, 모든 활성 작업을 중지 하 고, 아직 시작 되지 않은 모든 작업을 삭제 하 고,를 호출 하는 컨텍스트로 예외를 마샬링합니다 `parallel_for` .

예외가 발생 한 후에 OpenMP를 사용 하는 버전이 종료 되도록 요구 하는 경우 부울 플래그를 사용 하 여 오류가 발생 한 다른 루프 반복에 신호를 보낼 수 있습니다. [방법: 취소를 사용 하 여 동시성 런타임를 사용 하는 OpenMP 루프 변환](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)항목의 예제와 같이 플래그가 설정 된 경우 후속 루프 반복은 아무 작업도 수행 하지 않습니다. 반대로, 예외가 발생 한 후 동시성 런타임를 사용 하는 루프를 계속 사용 해야 하는 경우 병렬 루프 본문 자체에서 예외를 처리 합니다.

비동기 에이전트 및 경량 작업과 같은 동시성 런타임의 다른 구성 요소는 예외를 전송 하지 않습니다. 대신 처리 되지 않은 예외는 처리 되지 않은 예외 처리기에 의해 catch 되며이는 기본적으로 프로세스를 종료 합니다. 예외 처리에 대 한 자세한 내용은 [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)를 참조 하세요.

및 기타 병렬 알고리즘에 대 한 자세한 내용은 `parallel_for` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `concrt-omp-exceptions.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc/openmp concrt-omp-exceptions**

## <a name="see-also"></a>참고 항목

[OpenMP에서 동시성 런타임으로 마이그레이션](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)
