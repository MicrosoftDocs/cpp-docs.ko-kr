---
description: '자세한 정보: 방법: 특정 스케줄러 정책 지정'
title: '방법: 특정 Scheduler 정책 지정'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: c4aeeea04d69613ef3eb80f36863b16530e18e37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197259"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>방법: 특정 Scheduler 정책 지정

Scheduler 정책을 사용 하면 스케줄러에서 작업을 관리할 때 사용 하는 전략을 제어할 수 있습니다. 이 항목에서는 스케줄러 정책을 사용 하 여 진행률 표시기를 콘솔에 출력 하는 작업의 스레드 우선 순위를 늘리는 방법을 보여 줍니다.

비동기 에이전트와 함께 사용자 지정 스케줄러 정책을 사용 하는 예제는 [방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 두 작업을 병렬로 수행 합니다. 첫 번째 작업은 n<sup>번째</sup> 피보나치 수를 계산 합니다. 두 번째 작업은 진행률 표시기를 콘솔에 출력 합니다.

첫 번째 태스크는 재귀 분해를 사용 하 여 피보나치 수를 계산 합니다. 즉, 각 작업은 재귀적으로 하위 작업을 만들어 전체 결과를 계산 합니다. 재귀적 분해를 사용 하는 작업은 사용 가능한 모든 리소스를 사용 하 여 다른 작업을 결핍 수 있습니다. 이 예제에서 진행률 표시기를 인쇄 하는 작업은 컴퓨팅 리소스에 대 한 시기 적절 한 액세스를 수신 하지 못할 수 있습니다.

진행 메시지를 인쇄 하는 작업을 제공 하 여 컴퓨팅 리소스에 대 한 공평 한 액세스를 제공 하기 위해이 예제에서는 [방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) 에 설명 된 단계를 사용 하 여 사용자 지정 정책을 포함 하는 스케줄러 인스턴스를 만듭니다. 사용자 지정 정책은 우선 순위가 가장 높은 클래스가 되도록 스레드 우선 순위를 지정 합니다.

이 예제에서는 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 및 [concurrency:: timer](../../parallel/concrt/reference/timer-class.md) 클래스를 사용 하 여 진행률 표시기를 인쇄 합니다. 이러한 클래스에는 예약 된 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) 개체에 대 한 참조를 사용 하는 생성자 버전이 있습니다. 이 예제에서는 기본 스케줄러를 사용 하 여 피보나치 수를 계산 하는 작업을 예약 하 고 스케줄러 인스턴스를 사용 하 여 진행률 표시기를 인쇄 하는 작업을 예약 합니다.

사용자 지정 정책이 있는 스케줄러를 사용 하는 이점을 보여 주기 위해이 예에서는 전체 작업을 두 번 수행 합니다. 이 예에서는 먼저 기본 스케줄러를 사용 하 여 두 작업을 예약 합니다. 그런 다음이 예제에서는 기본 스케줄러를 사용 하 여 첫 번째 작업을 예약 하 고, 두 번째 작업을 예약 하는 사용자 지정 정책이 있는 스케줄러를 사용 합니다.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

두 작업 집합 모두 동일한 결과를 생성 하지만, 사용자 지정 정책을 사용 하는 버전은 진행률 표시기를 인쇄 하는 작업이 승격 된 우선 순위로 실행 되도록 하 여 더 반응 동작 하도록 합니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `scheduler-policy.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc scheduler-policy**

## <a name="see-also"></a>참고 항목

[스케줄러 정책](../../parallel/concrt/scheduler-policies.md)<br/>
[방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
