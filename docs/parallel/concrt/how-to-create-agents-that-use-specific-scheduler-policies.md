---
description: '자세한 정보: 방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기'
title: '방법: 특정 스케줄러 정책을 사용하는 에이전트 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 06a7ffaf18f3d7024f99755a0595154197c396f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333460"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>방법: 특정 스케줄러 정책을 사용하는 에이전트 만들기

에이전트는 다른 구성 요소와 비동기 방식으로 작동 하 여 더 큰 컴퓨팅 작업을 해결 하는 응용 프로그램 구성 요소입니다. 에이전트는 일반적으로 설정 된 수명 주기를 가지 며 상태를 유지 관리 합니다.

모든 에이전트에는 고유한 응용 프로그램 요구 사항이 있을 수 있습니다. 예를 들어 입력을 검색 하거나 출력을 표시 하는 사용자 상호 작용을 가능 하 게 하는 에이전트는 컴퓨팅 리소스에 대 한 우선 순위가 더 높은 액세스를 요구 합니다. Scheduler 정책을 사용 하면 스케줄러에서 작업을 관리할 때 사용 하는 전략을 제어할 수 있습니다. 이 항목에서는 특정 스케줄러 정책을 사용 하는 에이전트를 만드는 방법을 보여 줍니다.

비동기 메시지 블록과 함께 사용자 지정 스케줄러 정책을 사용 하는 기본 예제는 [방법: 특정 스케줄러 정책 지정을](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)참조 하세요.

이 항목에서는 에이전트, 메시지 블록 및 메시지 전달 함수와 같은 비동기 에이전트 라이브러리의 기능을 사용 하 여 작업을 수행 합니다. 비동기 에이전트 라이브러리에 대 한 자세한 내용은 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)를 참조 하십시오.

## <a name="example"></a>예제

다음 예제에서는 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md): 및에서 파생 되는 두 개의 클래스를 정의 합니다. `permutor` `printer` `permutor`클래스는 지정 된 입력 문자열의 모든 순열을 계산 합니다. `printer`클래스는 진행률 메시지를 콘솔에 출력 합니다. `permutor`클래스는 사용 가능한 모든 컴퓨팅 리소스를 사용할 수 있는 계산 집약적인 작업을 수행 합니다. 유용 하 게 사용할 수 있도록 `printer` 클래스는 각 진행률 메시지를 시기 적절 하 게 인쇄 해야 합니다.

`printer`클래스에 컴퓨팅 리소스에 대 한 공평 한 액세스를 제공 하기 위해이 예제에서는 [방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) 에 설명 된 단계를 사용 하 여 사용자 지정 정책을 포함 하는 스케줄러 인스턴스를 만듭니다. 사용자 지정 정책은 우선 순위가 가장 높은 클래스가 되도록 스레드 우선 순위를 지정 합니다.

사용자 지정 정책이 있는 스케줄러를 사용 하는 이점을 보여 주기 위해이 예에서는 전체 작업을 두 번 수행 합니다. 이 예에서는 먼저 기본 스케줄러를 사용 하 여 두 작업을 예약 합니다. 그런 다음이 예제에서는 기본 스케줄러를 사용 하 여 `permutor` 개체를 예약 하 고, 개체를 예약 하는 사용자 지정 정책이 있는 스케줄러를 사용 합니다 `printer` .

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

두 작업 집합 모두 동일한 결과를 생성 하지만, 사용자 지정 정책을 사용 하는 버전을 사용 하면 `printer` 개체가 더 반응 동작 하도록 승격 된 우선 순위로 실행 될 수 있습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `permute-strings.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc permute-strings**

## <a name="see-also"></a>참고 항목

[스케줄러 정책](../../parallel/concrt/scheduler-policies.md)<br/>
[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)
