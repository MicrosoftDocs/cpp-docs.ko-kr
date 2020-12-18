---
description: '자세한 정보: 시간 중심의 코드 성능 향상을 위한 팁'
title: 시간 중심의 코드 성능 향상을 위한 팁
ms.date: 11/04/2016
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
ms.openlocfilehash: 82963b10f623030a65b4ee8631ae30671fd23342
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277455"
---
# <a name="tips-for-improving-time-critical-code"></a>시간 중심의 코드 성능 향상을 위한 팁

코드를 빠르게 작성하려면 애플리케이션의 모든 측면과 애플리케이션이 시스템과 상호 작용하는 방법을 파악하고 있어야 합니다. 이 항목에서는 코드에서 시간이 중요한 부분이 만족스럽게 수행됨을 확신하는 데 도움이 되는 보다 명백한 일부 코딩 기술에 대한 대안을 제시합니다.

요약하자면 시간이 중요한 코드를 개선하려면 아래와 같은 내용을 알아야 합니다.

- 빨라져야 하는 프로그램의 부분

- 코드의 크기 및 속도

- 새로운 기능으로 인한 비용

- 작업을 완료하는 데 필요한 최소 작업

코드 성능에 대한 정보를 수집하는 데 성능 모니터(perfmon.exe)를 사용할 수 있습니다.

## <a name="sections-in-this-article"></a>이 문서의 섹션

- [캐시 누락 및 페이지 폴트](#_core_cache_hits_and_page_faults)

- [정렬 및 검색](#_core_sorting_and_searching)

- [MFC 및 클래스 라이브러리](#_core_mfc_and_class_libraries)

- [공유 라이브러리](#vcovrsharedlibraries)

- [힙](#_core_heaps)

- [스레드](#_core_threads)

- [소규모 작업 집합](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a> 캐시 누락 및 페이지 폴트

페이지 폴트(프로그램 지침 및 데이터를 위한 보조 스토리지로 이동)와 외부 및 내부 캐시 모두에서, 누락된 캐시 적중은 프로그램 성능을 저하시킵니다.

CPU 캐시 적중은 프로그램에 10-20 클록 주기를 일으킬 수 있습니다. 외부 캐시 적중은 20–40 클록 주기를 일으킬 수 있습니다. 페이지 폴트는 백만 클록 주기를 일으킬 수 있습니다(프로세서가 하나의 페이지 폴트를 500MIPS(초당 명령 100만 개) 및 2밀리초 시간으로 처리한다고 가정). 따라서 프로그램 실행 시 누락된 캐시 적중 및 페이지 폴트 수를 줄이는 코드를 작성하는 것이 가장 중요합니다.

프로그램 성능 저하의 한 가지 원인은 프로그램이 필요 이상으로 많은 페이지 폴트를 반환하거나 캐시를 누락하는 것입니다. 이러한 문제를 피하기 위해 참조 집약성이 좋은 데이터 구조를 사용해야 합니다. 즉, 관련 항목을 함께 보관해야 합니다. 경우에 따라서는 참조 집약성이 떨어져 뛰어난 것처럼 보이는 데이터 구조가 끔찍하게 변하는 경우가 있고 또 그 반대의 경우도 있습니다. 다음 두 가지 예제를 살펴보세요.

- 항목을 검색하는 경우 또는 목록을 끝으로 트래버스하는 경우 건너 뛴 각 링크가 캐시를 누락하거나 페이지 폴트를 일으킬 수 있으므로 동적으로 할당되어 연결된 목록은 프로그램 성능을 줄일 수 있습니다. 단순 배열을 기반으로 하는 목록 구현은 향상된 캐싱과 줄어든 페이지 폴트로 인해 실제로 훨씬 더 빨라질 수 있습니다. 따라서 배열이 커지기 힘들어 계속해서 더 빨라질 수 있습니다.

- 동적으로 할당되어 연결된 목록을 사용하는 해시 테이블은 성능을 저하시킬 수 있습니다. 더 나아가 동적으로 할당되어 연결된 목록을 사용하여 내용을 저장하는 해시 테이블은 성능을 크게 저하시킬 수 있습니다. 실제로 최종 분석에서는 상황에 따라 배열을 통한 간단한 선형 검색이 더 빠를 수도 있습니다. 배열 기반 해시 테이블("closed hashing")은 뛰어난 성능을 자주 보여줌에도 불구하고 종종 간과되는 구현입니다.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a> 정렬 및 검색

정렬은 대다수의 일반 작업에 비해 본래 시간이 많이 소요됩니다. 불필요한 속도 저하를 피하려면 중요한 시간에는 정렬 작업을 피합니다. 다음과 같이 할 수 있습니다.

- 정렬을 비 성능 결정적 시간까지 지연합니다.

- 데이터를 초기의 비 성능 결정적 시간에 정렬합니다.

- 정말 정렬이 필요한 데이터의 부분만 정렬합니다.

경우에 따라 정렬된 순서로 목록을 작성할 수 있습니다. 정렬된 순서대로 데이터를 삽입해야 하는 경우 참조 집약성이 안 좋은, 더 복잡한 데이터 구조가 필요할 수 있으므로 주의합니다. 이는 캐시 누락 및 페이지 폴트로 이어질 수 있습니다. 모든 경우에 적용할 수 있는 접근 방식은 없습니다. 여러 접근 방식을 시도해 보고 차이점을 확인해 보세요.

다음은 정렬을 위한 몇 가지 일반적인 팁입니다.

- 버그를 최소화하려면 스톡 정렬을 사용합니다.

- 정렬의 복잡성을 줄이기 위해 사전에 수행할 수 있는 모든 작업을 수행합니다. 데이터를 한 번 무시하여 비교가 간소화되고 O(n log n)에서 O(n)로 정렬이 줄어들면 거의 확실히 상황이 개선됩니다.

- 정렬의 참조 집약성 알고리즘과 이러한 알고리즘이 실행될 것으로 예상되는 데이터에 대해 생각해 보세요.

검색에 대한 대안은 정렬에 대한 대안보다 적습니다. 검색이 시간 결정적이라면 이진 검색 또는 해시 테이블 조회는 거의 항상 최고의 성능을 보이지만 정렬과 마찬가지로 집약성을 염두에 둬야 합니다. 작은 배열을 통한 선형 검색은 페이지 폴트 또는 캐시 누락을 일으키는 포인터가 많이 포함된 데이터 구조를 통한 이진 검색보다 빠를 수 있습니다.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a> MFC 및 클래스 라이브러리

MFC(Microsoft Foundation Classes)는 코드 작성을 크게 간소화할 수 있습니다. 시간 결정적인 코드를 작성할 때 일부 클래스에서 본질적으로 발생하는 오버헤드를 염두에 둬야 합니다. 시간 결정적 코드가 성능 요구 사항을 충족하는지 확인하려면 시간 결정적 코드가 사용하는 MFC 코드를 확인합니다. 다음 목록에서는 파악하고 있어야 하는 MFC 클래스 및 함수를 식별합니다.

- `CString` MFC는 C 런타임 라이브러리를 호출하여 [CString](../atl-mfc-shared/reference/cstringt-class.md)을 위한 메모리를 동적으로 할당합니다. 일반적으로 `CString`은 동적으로 할당된 다른 문자열처럼 효율적입니다. 동적으로 할당된 모든 문자열처럼 동적 할당 및 릴리스에 대한 오버헤드가 있습니다. 일반적으로 스택에 대한 단순 **`char`** 배열은 동일한 용도를 제공하면서 더 빠릅니다. 상수 문자열을 저장하는 데 `CString`을 사용하지 마세요. 대신 `const char *`를 사용하세요. `CString` 개체를 사용하여 수행하는 모든 작업에는 약간의 오버헤드가 있습니다. 런타임 라이브러리 [문자열 함수](../c-runtime-library/string-manipulation-crt.md)를 사용하면 더 빠를 수 있습니다.

- `CArray` [CArray](../mfc/reference/carray-class.md)는 일반 배열에는 없는 유연성을 제공하지만 프로그램에는 이러한 유연성이 필요하지 않을 수 있습니다. 배열의 특정 한계를 알면 대신 고정된 전역 배열을 사용할 수 있습니다. `CArray`를 사용하면 `CArray::SetSize`를 사용하여 크기를 설정하고 다시 할당이 필요한 경우 커지게 하는 요소 수를 지정합니다. 그렇지 않은 경우 요소를 추가하면 배열이 자주 다시 할당되고 복사될 수 있습니다. 이는 비효율적이며 메모리를 조각화할 수 있습니다. 또한 배열에 항목을 삽입하면 `CArray`가 메모리의 후속 항목을 이동하므로 배열이 커져야 할 수 있음에 주의합니다. 이러한 작업은 캐시 누락 및 페이지 폴트를 일으킬 수 있습니다. MFC에서 사용하는 코드를 살펴보면 성능 개선을 위해 자신의 시나리오에 더 잘 맞는 코드를 작성할 수 있다는 점을 알 수 있습니다. `CArray`는 템플릿입니다. 예를 들어 특정 형식에 대해 `CArray` 특수화를 제공할 수 있습니다.

- `CList` [CList](../mfc/reference/clist-class.md)는 이중 연결 목록이므로 목록의 처음, 끝 및 알려진 위치(`POSITION`)에서 요소가 빨리 삽입됩니다. 값 또는 인덱스별로 요소 조회에는 순차 검색이 필요하지만 목록이 길 경우 속도가 저하될 수 있습니다. 코드에 이중 연결 목록이 필요 없는 경우에는 `CList` 사용을 다시 고려할 수 있습니다. 단일 연결 목록을 사용하면 모든 작업에 필요한 추가 포인터 업데이트를 위한 오버헤드와 해당 포인터에 필요한 메모리가 절약됩니다. 추가 메모리는 크지 않지만 캐시 누락 또는 페이지 폴트가 발생할 수 있는 또 다른 기회가 될 수 있습니다.

- `IsKindOf` 이 함수는 여러 호출을 생성하고 여러 데이터 영역에서 많은 메모리에 액세스할 수 있어 참조 집약성이 떨어집니다. 이 함수는 디버그 빌드(예: ASSERT 호출)에 유용하지만 릴리스 빌드에는 사용하지 않도록 하세요.

- `PreTranslateMessage` 창의 특정 트리에 다른 키보드 액셀러레이터가 필요하거나 메시지 펌프에 메시지 처리를 삽입해야 하는 경우 `PreTranslateMessage`를 사용합니다. `PreTranslateMessage`는 MFC 디스패치 메시지를 변경합니다. `PreTranslateMessage`를 재정의하는 경우 필요한 수준에서만 재정의합니다. 예를 들어 특정 뷰의 자식으로 이동하는 메시지에만 관심이 있는 경우에는 `CMainFrame::PreTranslateMessage`를 재정의할 필요가 없습니다. 대신 뷰 클래스의 `PreTranslateMessage`를 재정의합니다.

   아무 창으로나 전송된 메시지를 처리하려고 `PreTranslateMessage`를 사용하여 일반 디스패치 경로를 피하지 마세요. 이러한 용도로는 [창 프로시저](../mfc/registering-window-classes.md) 및 MFC 메시지 맵을 사용합니다.

- `OnIdle` 유휴 상태 이벤트는 `WM_KEYDOWN` 이벤트와 `WM_KEYUP` 이벤트 사이에서 발생하듯 예기치 못하게 발생할 수 있습니다. 타이머가 코드를 트리거할 보다 효율적인 방법일 수 있습니다. false 메시지를 생성하거나 `OnIdle`의 재정의에서 항상 `TRUE`를 반환하여 `OnIdle`을 강제로 반복적으로 호출하지 마세요. 그러면 스레드 대기를 허용할 수 없습니다. 다시 한 번 말하지만 타이머 또는 개별 스레드가 더욱 적절할 수 있습니다.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a> 공유 라이브러리

코드 다시 사용이 필요합니다. 그러나 다른 사람의 코드를 사용하려고 하면 성능이 중요한 경우 해당 코드가 무엇을 수행하는지 정확하게 파악해야 합니다. 이를 파악하는 가장 좋은 방법은 소스 코드를 꼼꼼하게 살펴보거나 PView 또는 성능 모니터와 같은 도구를 사용하여 측정하는 것입니다.

## <a name="heaps"></a><a name="_core_heaps"></a> 힙

다중 힙은 신중하게 사용합니다. `HeapCreate` 및 `HeapAlloc`으로 만든 추가 힙을 사용하면 관련 할당 집합을 관리한 다음 삭제할 수 있습니다. 메모리를 너무 많이 커밋하지 마세요. 다중 힙을 사용하는 경우 초기에 커밋된 메모리 양에 특히 주의를 기울이세요.

다중 힙 대신 도우미 함수를 사용하여 코드와 기본 힙 간에 상호 작용할 수 있습니다. 도우미 함수는 애플리케이션의 성능을 개선할 수 있는 사용자 지정 할당 전략의 구현을 용이하게 합니다. 예를 들어 소규모 할당을 자주 수행하는 경우 이러한 할당을 기본 힙의 한 부분으로 지역화하려 할 수 있습니다. 메모리의 큰 블록을 할당한 다음 도우미 함수를 사용하여 이 블록에서 하위 할당할 수 있습니다. 이렇게 하면 할당이 기본 힙에서 나오므로 사용되지 않는 메모리가 있는 추가 힙은 없습니다.

그러나 기본 힙을 사용하면 참조의 집약성이 떨어지는 경우도 있습니다. Process Viewer, Spy++ 또는 성능 모니터를 사용하면 힙 간에 개체 이동의 영향을 측정할 수 있습니다.

힙을 측정하면 힙에서의 모든 할당을 처리할 수 있습니다. 검사점에 C 런타임 [디버그 힙 루틴](/visualstudio/debugger/crt-debug-heap-details)을 사용하고 힙을 덤프합니다. Microsoft Excel과 같은 스프레드시트 프로그램으로 출력을 읽고 피벗 테이블을 사용하여 결과를 볼 수 있습니다. 할당의 총 수, 크기 및 분포를 확인합니다. 이러한 정보를 작업 집합의 크기와 비교합니다. 또한 관련 크기의 개체 클러스터링을 살펴봅니다.

성능 카운터를 사용하여 메모리 사용을 모니터링할 수도 있습니다.

## <a name="threads"></a><a name="_core_threads"></a> 스레드

백그라운드 작업의 경우 이벤트의 효과적인 유휴 상태 처리가 스레드 사용보다 빠를 수 있습니다. 단일 스레드 프로그램에서 참조의 집약성을 파악하는 것이 더 쉽습니다.

가장 좋은 방법은 차단한 운영 체제 알림이 백그라운드 작업의 루트에 있는 경우에만 스레드를 사용하는 것입니다. 이벤트에 대한 주 스레드를 차단하는 것은 비현실적이므로 스레드를 사용하는 것이 가장 좋습니다.

스레드는 통신 문제도 일으킵니다. 메시지 목록을 통해서 또는 공유 메모리를 할당하고 사용하여 스레드 간의 통신 링크를 관리해야 합니다. 경합 상태 및 교착 상태 문제를 피하려면 통신 링크 관리에는 일반적으로 동기화가 필요합니다. 이러한 복잡성은 쉽게 버그 및 성능 문제로 돌변할 수 있습니다.

자세한 내용은 [유휴 상태 루프 처리](../mfc/idle-loop-processing.md) 및 [다중 스레딩](../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조하세요.

## <a name="small-working-set"></a><a name="_core_small_working_set"></a> 소규모 작업 집합

작업 집합이 더 작을수록 참조 집약성은 향상되고 페이지 폴트는 줄어들며 캐시 적중률은 더 커집니다. 프로세스 작업 집합은 운영 체제에서 직접 제공하는, 참조 집약성 측정에 가장 적합한 메트릭입니다.

- 작업 집합의 상한 및 하한을 설정하려면 [SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize)를 사용합니다.

- 작업 집합의 상한 및 하한을 가져오려면 [GetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize)를 사용합니다.

- 작업 집합의 크기를 보려면 Spy++를 사용합니다.

## <a name="see-also"></a>참조

[코드 최적화](optimizing-your-code.md)
