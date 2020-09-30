---
title: '참조: Windows Performance Analyzer 뷰'
description: Windows Performance Analyzer에서 사용할 수 있는 C++ Build Insights 뷰에 대한 참조입니다.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a5b13ee08becd472b3bc52319212b84a9c8ffc25
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508805"
---
# <a name="reference-windows-performance-analyzer-views"></a>참조: Windows Performance Analyzer 뷰

::: moniker range="<=vs-2017"

C++ Build Insights 도구는 Visual Studio 2019에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range="vs-2019"

이 문서에서는 WPA(Windows Performance Analyzer)에서 사용할 수 있는 각 C++ Build Insights 뷰에 대한 세부 정보를 제공합니다. 이 페이지를 사용하여 다음 항목을 찾을 수 있습니다.

- 데이터 열 설명
- 각 뷰에서 사용 가능한 미리 설정(해당 용도 및 기본 설정 보기 모드 등)

WPA를 처음 사용하는 경우에는 먼저 [C++ Build Insights용 WPA의 기본 사항](../tutorials/wpa-basics.md)을 숙지하는 것이 좋습니다.

## <a name="build-explorer"></a>빌드 탐색기

빌드 탐색기 뷰는 다음 작업을 수행하는 데 사용됩니다.

- 병렬 처리 문제를 진단
- 빌드 시간이 구문 분석, 코드 생성 또는 연결에 주로 사용되는지 확인
- 병목 상태 및 비정상적으로 오래 걸린 빌드 작업을 식별

### <a name="build-explorer-view-data-columns"></a>빌드 탐색기 뷰 데이터 열

| 열 이름 | 설명 |
|-|-|
| BuildTimelineDescription | 현재 작업 또는 속성이 발생하는 타임라인에 대한 텍스트 설명입니다. |
| BuildTimelineId          | 현재 작업 또는 속성이 발생하는 타임라인에 대한 0부터 시작하는 식별자입니다. |
| 구성 요소                | 현재 이벤트가 발생했을 때 컴파일 또는 연결 중인 구성 요소입니다. 이 이벤트와 연결된 구성 요소가 없는 경우 이 열의 값은 *\<Invocation X Info\>* 입니다. X는 이벤트가 발생했을 때 실행 중인 호출의 고유한 숫자 식별자입니다. 이 식별자는 이 이벤트의 InvocationId 열에 있는 식별자와 동일합니다. |
| 개수                    | 이 데이터 행으로 표시되는 작업 또는 속성의 수입니다. 이 값은 항상 1이며 여러 행을 그룹화하는 집계 시나리오에만 유용합니다. |
| ExclusiveCPUTime         | 이 작업에 의해 사용된 CPU 시간(밀리초)입니다. 자식 활동에 사용된 시간은 이 크기에 포함되지 않습니다. |
| ExclusiveDuration        | 작업의 기간(밀리초)입니다. 자식 활동의 기간은 이 크기에 포함되지 않습니다. |
| InclusiveCPUTime         | 이 작업 및 모든 자식 작업에서 사용한 CPU 시간(밀리초)입니다. |
| InclusiveDuration        | 이 활동 및 모든 자식 활동의 기간(밀리초)입니다. |
| InvocationDescription    | 이 이벤트가 발생한 호출에 대한 텍스트 설명입니다. 설명에는 *cl.exe* 또는 *link.exe*인지 여부와 고유한 숫자 호출 식별자가 포함됩니다. 해당하는 경우 호출 중에 컴파일 또는 연결된 구성 요소의 전체 경로를 포함합니다. 구성 요소를 빌드하지 않는 호출 또는 여러 구성 요소를 빌드하는 호출의 경우 경로는 비어 있습니다. 호출 식별자는 InvocationId 열에 있는 식별자와 동일합니다. |
| InvocationId             | 이 이벤트가 발생한 호출의 고유한 숫자 식별자입니다. |
| 이름                     | 이 이벤트가 나타내는 작업 또는 속성의 이름입니다. |
| Time                     | 이벤트가 발생한 시점을 식별하는 타임스탬프입니다. |
| 도구                     | 이 이벤트가 발생했을 때 실행 중인 도구입니다. 이 열의 값은 CL 또는 링크입니다. |
| 형식                     | 현재 이벤트의 유형입니다. 이 값은 작업 또는 속성입니다. |
| 값                    | 현재 이벤트가 속성인 경우 이 열에 해당 값이 포함됩니다. 현재 이벤트가 작업인 경우 이 열은 비어 있습니다. |

### <a name="build-explorer-view-presets"></a>빌드 탐색기 뷰 미리 설정

| 미리 설정 이름           | 기본 설정 뷰 모드 | 사용 방법 |
|-----------------------|---------------------|------------|
| 활동 통계   | 그래프/테이블       | 이 미리 설정을 사용하여 모든 빌드 탐색기 작업에 대한 집계된 통계를 볼 수 있습니다. 테이블 모드에서는 빌드가 구문 분석, 코드 생성 또는 링커에 주로 사용되는지 여부를 한눈에 파악할 수 있습니다. 각 작업에 대한 집계 기간은 내림차순으로 정렬됩니다. 최상위 노드를 확장하여 이러한 최상위 활동에 가장 많은 시간을 사용하는 호출을 쉽게 찾을 수 있습니다. 원하는 경우에는 WPA 설정을 조정하여 평균 또는 다른 유형의 집계를 표시할 수 있습니다. 그래프 모드에서는 빌드하는 동안 각 활동이 활성화된 시기를 확인할 수 있습니다. |
| 호출           | Graph               | 그래프 뷰에서 시작 시간으로 정렬된 호출 목록을 아래로 스크롤합니다. CPU(샘플링) 뷰와 함께 사용하여 CPU 사용률이 낮은 호출을 찾을 수 있습니다. 병렬 처리 문제를 검색합니다. |
| 호출 속성 | 표               | 지정된 컴파일러 또는 링커 호출에 대한 주요 정보를 빠르게 찾습니다. 해당 버전, 작업 디렉터리 또는 호출에 사용된 전체 명령줄을 확인합니다. |
| 타임라인             | Graph               | 빌드가 병렬 처리된 방식을 막대 그래프로 확인합니다. 병렬 처리 문제 및 병목 상태를 한눈에 파악합니다. 필요에 따라 막대에 다른 의미를 할당하도록 WPA를 구성합니다. 모든 호출을 색으로 구분된 막대 그래프로 보려면 호출 설명을 마지막 그룹화된 열로 선택합니다. 이는 시간이 많이 걸리는 원인을 신속하게 식별하는 데 도움이 됩니다. 그런 다음 확대하여 작업 이름을 마지막 그룹화된 열로 선택하고 가장 오래 걸린 부분을 확인합니다. |

## <a name="files"></a>파일

파일 뷰는 다음 작업을 수행하는 데 사용됩니다.

- 가장 자주 포함되는 헤더를 확인
- PCH(미리 컴파일된 헤더)에 포함할 항목을 결정

### <a name="files-view-data-columns"></a>파일 뷰 데이터 열

| 열 이름              | 설명 |
|--------------------------|-------------|
| ActivityName             | 이 파일 이벤트가 발생했을 때 진행 중인 작업입니다. 현재 이 값은 항상 *Parsing*입니다. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 구성 요소                | * |
| 개수                    | * |
| 깊이                    | 포함 트리에서 이 파일이 발견된 0부터 시작하는 위치입니다. 계산은 포함 트리의 루트에서 시작합니다. 값 0은 일반적으로 .c/.cpp 파일에 해당합니다. |
| ExclusiveDuration        | * |
| IncludedBy               | 현재 파일이 포함된 파일의 전체 경로입니다. |
| IncludedPath             | 현재 파일의 전체 경로입니다. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | 현재 파일 이벤트가 발생한 시간을 나타내는 타임스탬프입니다. |
| 도구                     | * |

\* 이 열의 값은 [빌드 탐색기](#build-explorer-view-data-columns) 뷰의 값과 동일합니다.

### <a name="files-view-presets"></a>파일 뷰 미리 설정

| 미리 설정 이름 | 기본 설정 뷰 모드 | 사용 방법 |
|-------------|---------------------|------------|
| 통계  | 표               | 목록을 내림차순으로 살펴보면서 집계된 구문 분석 시간이 가장 긴 파일을 확인합니다. 이 정보를 사용하여 헤더를 재구성하거나 PCH에 포함할 항목을 결정합니다. |

## <a name="functions"></a>함수

함수 뷰는 코드 생성 시간이 과도하게 긴 함수를 식별하는 데 사용됩니다.

### <a name="functions-view-data-columns"></a>함수 뷰 데이터 열

| 열 이름              | 설명 |
|--------------------------|-------------|
| ActivityName             | 이 함수 이벤트가 발생했을 때 진행 중인 작업입니다. 현재 이 값은 항상 *CodeGeneration*입니다. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 구성 요소                | * |
| 개수                    | * |
| 기간                 | 이 함수의 코드 생성 활동 기간입니다. |
| FunctionName             | 코드가 생성되는 함수의 이름입니다. |
| InvocationId             | * |
| StartTime                | 현재 함수 이벤트가 발생한 시간을 나타내는 타임스탬프입니다. |
| 도구                     | * |

\* 이 열의 값은 [빌드 탐색기](#build-explorer-view-data-columns) 뷰의 값과 동일합니다.

### <a name="functions-view-presets"></a>함수 뷰 미리 설정

| 미리 설정 이름 | 기본 설정 뷰 모드 | 사용 방법 |
|-------------|---------------------|------------|
| 통계  | 표               | 목록을 내림차순으로 살펴보면서 집계된 코드 생성 시간이 가장 긴 함수를 확인합니다. 코드에서 **`__forceinline`** 키워드를 과도하게 사용했는지 또는 일부 함수가 지나치게 큰지에 대한 힌트를 얻을 수 있습니다. |
| 타임라인   | Graph               | 이 막대 그래프를 살펴보면서 생성 시간이 가장 오래 걸리는 함수의 위치 및 기간을 확인합니다. 해당 함수가 빌드 탐색기 뷰의 병목 상태와 일치하는지 확인합니다. 일치할 경우 적절한 조치를 취해 코드 생성 시간을 줄이고 빌드 시간을 효율적으로 활용합니다. |

## <a name="see-also"></a>참조

[C++ Build Insights 활용 시작](../get-started-with-cpp-build-insights.md)\
[참조: vcperf 명령](vcperf-commands.md)\
[자습서: Windows Performance Analyzer 기본 사항](../tutorials/wpa-basics.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
