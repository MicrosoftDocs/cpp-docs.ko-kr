---
description: '다음에 대 한 자세한 정보: 동시성 런타임'
title: 동시성 런타임
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: 1bc161e8c70f98fe469feffa1c472ecaf6a7f161
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325786"
---
# <a name="concurrency-runtime"></a>동시성 런타임

C++용 동시성 런타임은 강력하고 확장 가능하며 응답성이 높은 병렬 애플리케이션을 작성하는 데 도움이 됩니다. 이는 동시성과 관련된 인프라 세부 정보를 관리할 필요가 없도록 추상화 수준을 높입니다. 또한 이러한 동시성 런타임을 사용하여 애플리케이션의 서비스 품질 요구 사항을 충족하는 일정 예약 정책을 지정할 수도 있습니다. 다음 리소스는 동시성 런타임 작업을 시작하는 데 도움이 됩니다.

참조 설명서 [는 참조를 참조 하세요.](../../parallel/concrt/reference/reference-concurrency-runtime.md)

> [!TIP]
> 동시성 런타임은 C++11 기능에 크게 의존하며 보다 최신 C++ 스타일을 채택합니다. 자세한 내용은  [c + +로 다시 시작](../../cpp/welcome-back-to-cpp-modern-cpp.md)을 참조 하세요.

## <a name="choosing-concurrency-runtime-features"></a>동시성 런타임 기능 선택

|아티클|설명|
|-|-|
|[개요](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|동시성 런타임이 중요한 이유와 해당 핵심 기능을 설명합니다.|
|[기타 동시성 모델과 비교](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|애플리케이션 요구 사항에 가장 잘 맞는 동시성 모델을 사용할 수 있도록 동시성 런타임과 Windows 스레드 풀, OpenMP 등의 기타 동시성 모델을 비교하는 방법을 보여 줍니다.|
|[OpenMP에서 동시성 런타임으로 마이그레이션](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|OpenMP와 동시성 런타임을 비교하고 기존 OpenMP 코드를 동시성 런타임을 사용하도록 마이그레이션하는 방법에 대한 예제를 제공합니다.|
|[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)|병렬 루프, 작업 및 병렬 컨테이너를 제공하는 PPL을 소개합니다.|
|[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)|비동기 에이전트 및 메시지 전달을 사용하여 데이터 흐름 및 파이프라이닝 작업을 애플리케이션에 쉽게 통합하는 방법을 소개합니다.|
|[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|동시성 런타임을 사용하는 데스크톱 앱의 성능을 미세 조정할 수 있게 해주는 작업 스케줄러를 소개합니다.|

## <a name="task-parallelism-in-the-ppl"></a>PPL에서 작업 병렬 처리

|아티클|설명|
|-|-|
|[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [방법: parallel_invoke를 사용 하 여 병렬 정렬 루틴 작성](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [방법: parallel_invoke를 사용 하 여 병렬 작업 실행](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [방법: 지연 후 완료 되는 작업 만들기](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|비동기 코드를 작성하고 병렬 작업을 더 작은 부분으로 분해하는 데 도움이 되는 작업 및 작업 그룹을 설명합니다.|
|[연습: 미래 구현](../../parallel/concrt/walkthrough-implementing-futures.md)|동시성 런타임 기능을 결합하여 더 많은 작업을 수행하는 방법을 보여 줍니다.|
|[연습: User-Interface 스레드에서 작업 제거](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|MFC 애플리케이션의 UI 스레드에서 수행하는 작업을 작업자 스레드로 이동하는 방법을 보여 줍니다.|
|[병렬 패턴 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [동시성 런타임의 일반적인 모범 사례](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|PPL 사용에 대한 팁과 유용한 정보를 제공합니다.|

## <a name="data-parallelism-in-the-ppl"></a>PPL에서 데이터 병렬 처리

|아티클|설명|
|-|-|
|[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [방법: parallel_for 루프 작성](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [방법: parallel_for_each 루프 작성](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [방법: 매핑 수행 및 병렬 작업 줄이기](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|`parallel_for`, `parallel_for_each`, `parallel_invoke`및 기타 병렬 알고리즘을 설명합니다. 데이터 컬렉션이 관련된 *데이터 병렬* 문제를 해결하려면 병렬 알고리즘을 사용합니다.|
|[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [방법: 병렬 컨테이너를 사용 하 여 효율성 향상](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [방법: 결합을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [방법: 조합 하 여 집합 결합](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|`combinable` 클래스와 `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`및 기타 병렬 컨테이너를 설명합니다. 해당 요소에 스레드로부터 안전한 액세스를 제공하는 컨테이너가 필요한 경우 병렬 컨테이너 및 개체를 사용합니다.|
|[병렬 패턴 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [동시성 런타임의 일반적인 모범 사례](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|PPL 사용에 대한 팁과 유용한 정보를 제공합니다.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>작업 및 병렬 알고리즘 취소

|아티클|설명|
|-|-|
|[PPL에서의 취소](cancellation-in-the-ppl.md)|취소 요청을 시작하고 취소 요청에 응답하는 방법을 비롯한 PPL에서의 취소 역할을 설명합니다.|
|[방법: 취소를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [방법: 예외 처리를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|데이터 병렬 작업을 취소하는 두 가지 방법을 보여 줍니다.|

## <a name="universal-windows-platform-apps"></a>유니버설 Windows 플랫폼 앱

|아티클|설명|
|-|-|
|[UWP 앱 용 c + +로 비동기 작업 만들기](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|동시성 런타임를 사용 하 여 UWP 앱에서 비동기 작업을 생성할 때 염두에 두어야 하는 몇 가지 주요 사항에 대해 설명 합니다.|
|[연습: 작업 및 XML HTTP 요청을 사용 하 여 연결](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|PPL 작업을 및 인터페이스와 결합 하 `IXMLHTTPRequest2` 여 `IXMLHTTPRequest2Callback` UWP 앱의 웹 서비스에 HTTP GET 및 POST 요청을 보내는 방법을 보여 줍니다.|
|[Windows 런타임 앱 샘플](/samples/browse/?languages=cpp&expanded=windows&products=windows-uwp)|Windows 런타임에 대 한 다운로드 가능한 코드 샘플 및 데모 앱이 포함 되어 있습니다.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>비동기 에이전트 라이브러리의 데이터 흐름 프로그래밍

|아티클|설명|
|-|-|
|[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)<br /><br /> [방법: 다양 한 Producer-Consumer 패턴 구현](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [방법: 호출 및 변환기 클래스에 작업 함수 제공](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [방법: 데이터 파이프라인에서 변환기 사용](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [방법: 완료 된 작업 중에서 선택](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [방법: 정기적으로 메시지 보내기](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md)|동시성 런타임에서 데이터 흐름 작업을 수행하기 위한 구성 요소인 비동기 에이전트, 메시지 블록 및 메시지 전달 함수를 설명합니다.|
|[연습: Agent-Based 응용 프로그램 만들기](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|기본 에이전트 기반 애플리케이션을 만드는 방법을 보여 줍니다.|
|[연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|이미지 처리를 수행하는 비동기 메시지 블록의 네트워크를 만드는 방법을 보여 줍니다.|
|[연습: join을 사용 하 여 교착 상태 방지](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|동시성 런타임을 사용하여 애플리케이션의 교착 상태를 방지하는 방법을 보여 주기 위해 철학자들의 만찬 문제(Dining Philosophers Problem)를 활용합니다.|
|[연습: 사용자 지정 메시지 블록 만들기](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|들어오는 메시지를 우선 순위별로 정렬하는 사용자 지정 메시지 블록 형식을 만드는 방법을 보여 줍니다.|
|[비동기 에이전트 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [동시성 런타임의 일반적인 모범 사례](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|에이전트 사용에 대한 팁과 유용한 정보를 제공합니다.|

## <a name="exception-handling-and-debugging"></a>예외 처리 및 디버깅

|아티클|설명|
|-|-|
|[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|동시성 런타임에서 예외를 사용하는 방법을 설명합니다.|
|[병렬 진단 도구](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|애플리케이션을 미세 조정하고 동시성 런타임을 가장 효과적으로 사용하는 방법을 보여 줍니다.|

## <a name="tuning-performance"></a>성능 조정

|아티클|설명|
|-|-|
|[병렬 진단 도구](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|애플리케이션을 미세 조정하고 동시성 런타임을 가장 효과적으로 사용하는 방법을 보여 줍니다.|
|[Scheduler 인스턴스](../../parallel/concrt/scheduler-instances.md)<br /><br /> [방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [스케줄러 정책](../../parallel/concrt/scheduler-policies.md)<br /><br /> [방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|스케줄러 인스턴스 및 스케줄러 정책을 관리하는 방법을 보여 줍니다. 데스크톱 앱의 경우 스케줄러 정책을 사용하면 특정 유형의 작업을 특정 규칙과 연결할 수 있습니다. 예를 들어 높은 스레드 우선 순위로 일부 작업을 실행하기 위한 스케줄러 인스턴스를 하나 만들고, 기본 스케줄러를 사용하여 보통 스레드 우선 순위로 다른 작업을 실행할 수 있습니다.|
|[일정 그룹](../../parallel/concrt/schedule-groups.md)<br /><br /> [방법: 일정 그룹을 사용 하 여 실행 순서에 영향을 줍니다.](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|일정 그룹을 사용하여 관련 작업을 함께 선호도를 설정하거나 그룹화하는 방법을 보여 줍니다. 예를 들어 동일한 프로세서 노드에서 관련 작업을 실행하는 이점이 있는 경우 해당 작업 간에 높은 수준의 국부성이 필요할 수 있습니다.|
|[간단한 작업](../../parallel/concrt/lightweight-tasks.md)|간단한 작업이 어떻게 부하 분산 또는 취소가 불필요한 작업을 만드는 데 유용한지 그리고 동시성 런타임과 함께 사용하는 데 적절하도록 기존 코드를 변경하는 데 유용한지를 설명합니다.|
|[컨텍스트](../../parallel/concrt/contexts.md)<br /><br /> [방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|동시성 런타임에서 관리하는 스레드의 동작을 제어하는 방법을 설명합니다.|
|[메모리 관리 함수](../../parallel/concrt/memory-management-functions.md)<br /><br /> [방법: Alloc 및 Free를 사용 하 여 메모리 성능 개선](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|동시성 런타임에서 메모리 할당과 해제를 동시에 수행할 수 있도록 제공하는 메모리 관리 함수를 설명합니다.|

## <a name="additional-resources"></a>추가 리소스

|아티클|설명|
|-|-|
|[Hilo의 비동기 프로그래밍 패턴 및 팁(C++ 및 XAML을 사용하는 Windows 스토어 앱)](/previous-versions/windows/apps/jj160321(v=win.10))|동시성 런타임를 사용 하 여 c + + 및 XAML을 사용 하는 Windows 런타임 앱 인 Hilo에서 비동기 작업을 구현 하는 방법을 알아봅니다.|
|[네이티브 코드 블로그의 병렬 프로그래밍](/archive/blogs/nativeconcurrency)|동시성 런타임의 병렬 프로그래밍에 대한 자세한 추가 블로그 기사를 제공합니다.|
|[C++ 및 네이티브 코드 포럼에서 병렬 컴퓨팅](https://go.microsoft.com/fwlink/p/?linkid=183874)|동시성 런타임에 대한 커뮤니티 토론에 참여할 수 있습니다.|
|[병렬 프로그래밍](/dotnet/standard/parallel-programming/index)|.NET Framework에서 사용할 수 있는 병렬 프로그래밍 모델에 대해 알려줍니다.|

## <a name="see-also"></a>참고 항목

[참조](../../parallel/concrt/reference/reference-concurrency-runtime.md)
