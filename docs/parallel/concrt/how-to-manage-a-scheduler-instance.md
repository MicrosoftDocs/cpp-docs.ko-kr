---
description: '자세한 정보: 방법: 스케줄러 인스턴스 관리'
title: '방법: 스케줄러 인스턴스 관리'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: 53d3e1af2a7d0dd434882e0a7ce9e5a36516834c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197402"
---
# <a name="how-to-manage-a-scheduler-instance"></a>방법: 스케줄러 인스턴스 관리

스케줄러 인스턴스를 사용 하면 다양 한 종류의 작업에 특정 일정 예약 정책을 연결할 수 있습니다. 이 항목에는 스케줄러 인스턴스를 만들고 관리 하는 방법을 보여 주는 두 가지 기본 예가 포함 되어 있습니다.

이 예제에서는 기본 스케줄러 정책을 사용 하는 스케줄러를 만듭니다. 사용자 지정 정책을 사용 하는 스케줄러를 만드는 예제는 [방법: 특정 스케줄러 정책 지정을](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)참조 하세요.

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>응용 프로그램에서 scheduler 인스턴스를 관리 하려면

1. 사용할 스케줄러에 대 한 정책 값이 포함 된 [concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 개체를 만듭니다.

1. Concurrency: [: CurrentScheduler:: create](reference/currentscheduler-class.md#create) 메서드 또는 [Concurrency:: Scheduler:: create](reference/scheduler-class.md#create) 메서드를 호출 하 여 스케줄러 인스턴스를 만듭니다.

   메서드를 사용 하는 경우 `Scheduler::Create` 스케줄러와 현재 컨텍스트를 연결 해야 하는 경우 [concurrency:: scheduler:: Attach](reference/scheduler-class.md#attach) 메서드를 호출 합니다.

1. [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) 함수를 호출 하 여 신호를 받지 않는 자동 다시 설정 이벤트 개체에 대 한 핸들을 만듭니다.

1. 방금 만든 이벤트 개체에 대해 [concurrency:: CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) 메서드 또는 [Concurrency:: Scheduler:: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) 메서드에 핸들을 전달 합니다. 그러면 스케줄러가 제거 될 때 설정 되는 이벤트를 등록 합니다.

1. 현재 스케줄러에서 예약 하려는 작업을 수행 합니다.

1. [Concurrency:: currentscheduler::D etach](reference/currentscheduler-class.md#detach) 메서드를 호출 하 여 현재 스케줄러를 분리 하 고 이전 스케줄러를 현재 스케줄러로 복원 합니다.

   메서드를 사용 하는 경우 `Scheduler::Create` [concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) 메서드를 호출 하 여 개체의 참조 횟수를 감소 시킵니다. `Scheduler`

1. 이벤트에 대 한 핸들을 [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) 함수에 전달 하 여 스케줄러가 종료 될 때까지 기다립니다.

1. [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) 함수를 호출 하 여 이벤트 개체에 대 한 핸들을 닫습니다.

## <a name="example"></a>예제

다음 코드에서는 스케줄러 인스턴스를 관리 하는 두 가지 방법을 보여 줍니다. 각 예제에서는 먼저 기본 스케줄러를 사용 하 여 현재 스케줄러의 고유 식별자를 출력 하는 작업을 수행 합니다. 그런 다음 각 예제에서는 스케줄러 인스턴스를 사용 하 여 동일한 작업을 다시 수행 합니다. 마지막으로, 각 예제에서는 기본 스케줄러를 현재 스케줄러로 복원 하 고 작업을 한 번 더 수행 합니다.

첫 번째 예제에서는 [concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md) 클래스를 사용 하 여 스케줄러 인스턴스를 만들고이를 현재 컨텍스트와 연결 합니다. 두 번째 예제에서는 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) 클래스를 사용 하 여 동일한 작업을 수행 합니다. 일반적으로 `CurrentScheduler` 클래스는 현재 스케줄러에서 작업 하는 데 사용 됩니다. 클래스를 사용 하는 두 번째 예제는 `Scheduler` 스케줄러가 현재 컨텍스트와 연결 된 시기 또는 특정 스케줄러를 특정 작업과 연결 하려는 경우에 유용 합니다.

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `scheduler-instance.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc scheduler-instance**

## <a name="see-also"></a>참고 항목

[Scheduler 인스턴스](../../parallel/concrt/scheduler-instances.md)<br/>
[방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
