---
description: '자세히 알아보기: 병렬 진단 도구 (동시성 런타임)'
title: 병렬 진단 도구(동시성 런타임)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 44d885e8e6c7529bd15fa0aa2e7930773400361f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172429"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>병렬 진단 도구(동시성 런타임)

Visual Studio는 다중 스레드 애플리케이션 디버깅 및 프로파일링에 대한 광범위한 지원을 제공합니다.

## <a name="debugging"></a>디버깅

Visual Studio 디버거에는 병렬 **스택** 창, **병렬 작업** 창 및 **병렬 조사식** 창이 포함 되어 있습니다. 자세한 내용은 [연습: 병렬 응용 프로그램 디버깅](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) 및 [방법: 병렬 조사식 창 사용](/visualstudio/debugger/how-to-use-the-parallel-watch-window)을 참조 하세요.

## <a name="profiling"></a>프로파일링

프로파일링 도구는 다중 스레드 응용 프로그램이 자신 및 다른 프로그램과 상호 작용하는 방식에 대한 그래픽, 표 형식 및 숫자 정보를 표시하는 세 가지 데이터 뷰를 제공합니다. 뷰를 사용 하면 중요 한 영역을 신속 하 게 식별 하 고 그래픽 디스플레이의 점에서 호출 스택, 호출 사이트 및 소스 코드로 이동할 수 있습니다. 자세한 내용은 [동시성 시각화 도우미](/visualstudio/profiling/concurrency-visualizer)를 참조하세요.

## <a name="event-tracing"></a>이벤트 추적

동시성 런타임는 ETW ( [ETW(Windows용 이벤트 추적)](/windows/win32/ETW/event-tracing-portal) )를 사용 하 여 다양 한 이벤트가 발생할 때 프로파일러와 같은 계측 도구에 알립니다. 이러한 이벤트에는 스케줄러가 활성화 또는 비활성화 되는 경우, 컨텍스트가 시작, 종료, 블록, 차단 또는 생성 될 때, 병렬 알고리즘이 시작 되거나 종료 되는 경우 등이 포함 됩니다.

[동시성 시각화 도우미](/visualstudio/profiling/concurrency-visualizer) 와 같은 도구는이 기능을 사용 합니다. 따라서 일반적으로 이러한 이벤트를 직접 사용할 필요가 없습니다. 그러나 이러한 이벤트는 사용자 지정 프로파일러를 개발 하거나 [Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628)와 같은 이벤트 추적 도구를 사용 하는 경우에 유용 합니다.

동시성 런타임는 추적을 사용 하는 경우에만 이러한 이벤트를 발생 시킵니다. [Concurrency:: EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) 함수를 호출 하 여 이벤트 추적 및 [동시성::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing) 함수를 사용 하 여 추적을 사용 하지 않도록 설정 합니다.

다음 표에서는 이벤트 추적을 사용 하는 경우 런타임에서 발생 하는 이벤트에 대해 설명 합니다.

|이벤트|설명|값|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|동시성 런타임에 대 한 ETW 공급자 식별자입니다.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|컨텍스트와 관련 된 이벤트를 표시 합니다.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|[동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘에 대 한 호출로 진입 및 종료를 표시 합니다.|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|[동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘에 대 한 호출로 진입 및 종료를 표시 합니다.|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|[동시성::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘에 대 한 호출로 진입 및 종료를 표시 합니다.|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|[작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)관련 된 이벤트를 표시 합니다.|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|가상 프로세서와 관련 된 이벤트를 표시 합니다.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

동시성 런타임는 다음 이벤트를 정의 하지만 현재 발생 하지는 않습니다. 런타임에서는 나중에 사용 하기 위해 이러한 이벤트를 예약 합니다.

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) 열거형은 이벤트에서 추적할 수 있는 작업을 지정 합니다. 예를 들어 알고리즘의 입구에서 `parallel_for` 런타임은 이벤트를 발생 시키고를 `PPLParallelForEventGuid` `CONCRT_EVENT_START` 작업으로 제공 합니다. `parallel_for`알고리즘이 반환 되기 전에 런타임은 이벤트를 다시 발생 시키고를 `PPLParallelForEventGuid` `CONCRT_EVENT_END` 작업으로 제공 합니다.

다음 예제에서는에 대 한 호출에 대해 추적을 사용 하도록 설정 하는 방법을 보여 줍니다 `parallel_for` . 는 추적을 사용할 수 없기 때문에 런타임에서 첫 번째 호출을 추적 하지 않습니다 `parallel_for` . 를 호출 하면 `EnableTracing` 런타임에서에 대 한 두 번째 호출을 추적할 수 있습니다 `parallel_for` .

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

런타임은 및를 호출 하는 횟수를 추적 합니다 `EnableTracing` `DisableTracing` . 따라서를 여러 번 호출 하는 경우 `EnableTracing` `DisableTracing` 추적을 사용 하지 않도록 설정 하기 위해 동일한 횟수의 횟수를 호출 해야 합니다.

## <a name="see-also"></a>참고 항목

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)
