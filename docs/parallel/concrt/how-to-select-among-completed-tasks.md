---
description: '자세히 알아보기: 방법: 완료 된 작업 중에서 선택'
title: '방법: 완료된 작업 중에서 선택'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: a23092e4572188898f5e544f25406febc63d0c06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197338"
---
# <a name="how-to-select-among-completed-tasks"></a>방법: 완료된 작업 중에서 선택

이 예제에서는 [concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 및 [concurrency:: join](../../parallel/concrt/reference/join-class.md) 클래스를 사용 하 여 검색 알고리즘을 완료 하는 첫 번째 작업을 선택 하는 방법을 보여 줍니다.

## <a name="example"></a>예제

다음 예에서는 두 개의 검색 알고리즘을 병렬로 수행 하 고 완료할 첫 번째 알고리즘을 선택 합니다. 이 예제에서는 `employee` 숫자 식별자와 직원의 급여를 포함 하는 형식을 정의 합니다. `find_employee`함수는 제공 된 식별자 또는 제공 된 급여를 가진 첫 번째 직원을 찾습니다. `find_employee`또한 함수는 제공 된 식별자 나 급여를 포함 하는 직원이 없는 경우를 처리 합니다. `wmain`함수는 개체의 배열을 만들고 `employee` 여러 식별자 및 급여 값을 검색 합니다.

이 예제에서는 개체를 사용 하 여 `choice` 다음과 같은 경우를 선택 합니다.

1. 제공 된 식별자가 있는 직원이 있습니다.

1. 제공 된 급여를 가진 직원이 있습니다.

1. 제공 된 식별자 나 급여를 가진 직원은 없습니다.

처음 두 경우에 대 한 예제에서는 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 개체를 사용 하 여 해당 식별자와 급여를 포함 하는 다른 개체를 저장 합니다. `single_assignment` 이 예제에서는 `join` 세 번째 경우에 개체를 사용 합니다. `join`개체는 두 개의 추가 개체로 구성 됩니다 `single_assignment` . 하나는 제공 된 식별자가 있는 직원을 포함 하지 않는 경우이 고 다른 하나는 제공 된 급여를 가진 직원이 없는 경우입니다. `join`개체는 각 멤버가 메시지를 받을 때 메시지를 보냅니다. 이 예제에서 개체는 `join` 제공 된 식별자 나 급여를 가진 직원이 없을 때 메시지를 보냅니다.

이 예제에서는 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 개체를 사용 하 여 두 검색 알고리즘을 병렬로 실행 합니다. 각 검색 작업은 개체 중 하나에 기록 `single_assignment` 하 여 지정 된 직원이 있는지 여부를 나타냅니다. 이 예제에서는 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수를 사용 하 여 메시지를 포함 하는 첫 번째 버퍼의 인덱스와 **`switch`** 결과를 인쇄 하는 블록을 가져옵니다.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

이 예제에서는 [concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) 도우미 함수를 사용 하 여 개체를 만들고 `choice` [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) 도우미 함수를 사용 하 여 개체를 만듭니다 `join` .

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `find-employee.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc find-employee**

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 클래스](../../parallel/concrt/reference/choice-class.md)<br/>
[join 클래스](../../parallel/concrt/reference/join-class.md)
