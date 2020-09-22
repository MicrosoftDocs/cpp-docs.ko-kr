---
title: C++ Build Insights SDK
description: Visual Studio C++ Build Insights SDK의 개요입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f53a9b6c682a0af7d8a01f6378ed0574d8fa4ca
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041174"
---
# <a name="c-build-insights-sdk"></a>C++ Build Insights SDK

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

C++ Build Insights SDK는 C++ Build Insights 플랫폼에서 개인 설정된 도구를 만들 수 있는 API 컬렉션입니다. 이 페이지에서는 시작하는 데 도움이 되는 대략적인 개요를 제공합니다.

## <a name="obtaining-the-sdk"></a>SDK 가져오기

다음 단계를 수행하여 C++ Build Insights SDK를 NuGet 패키지로 다운로드할 수 있습니다.

1. Visual Studio 2017 이상에서 새 C++ 프로젝트를 만듭니다.
1. **솔루션 탐색기** 창에서 프로젝트를 마우스 오른쪽 단추로 클릭합니다.
1. 상황에 맞는 메뉴에서 **NuGet 패키지 관리**를 선택합니다.
1. 오른쪽 위에서 **nuget.org** 패키지 원본을 선택합니다.
1. 최신 버전의 Microsoft.Cpp.BuildInsights 패키지를 검색합니다.
1. **설치**를 선택합니다.
1. 라이선스에 동의합니다.

SDK와 관련된 일반 개념을 자세히 알아보려면 계속 읽으세요. 공식 [C++ Build Insights 샘플 GitHub 리포지토리](https://github.com/microsoft/cpp-build-insights-samples)에 액세스하여 SDK를 사용하는 실제 C++ 애플리케이션의 예제를 볼 수도 있습니다.

## <a name="collecting-a-trace"></a>추적 수집

C++ Build Insights SDK를 사용하여 MSVC 도구 체인에서 오는 이벤트를 분석하려면 먼저 추적을 수집해야 합니다. SDK는 기본 추적 기술로 ETW(Windows용 이벤트 추적)를 사용합니다. 추적 수집은 다음 두 가지 방법으로 수행할 수 있습니다.

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>방법 1: Visual Studio 2019 이상에서 vcperf를 사용

1. 관리자 권한으로 VS 2019용 x64 Native Tools 명령 프롬프트를 엽니다.
1. 다음 명령을 실행합니다. `vcperf /start MySessionName`
1. 프로젝트를 빌드합니다.
1. 다음 명령을 실행합니다. `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > vcperf를 사용하는 추적을 중지할 때 `/stopnoanalyze` 명령을 사용합니다. C++ Build Insights SDK를 사용하여 일반 `/stop` 명령으로 중지된 추적을 분석할 수는 없습니다.

### <a name="method-2-programmatically"></a>방법 2: 프로그래밍 방식을 사용

다음과 같은 C++ Build Insights SDK 추적 수집 함수를 사용하여 프로그래밍 방식으로 추적을 시작하고 중지할 수 있습니다. **이러한 함수 호출을 실행하는 프로그램에는 관리자 권한이 있어야 합니다.** 추적 시작 및 중지 함수만 관리자 권한이 필요합니다. C++ Build Insights SDK의 다른 모든 함수는 관리자 권한 없이 실행할 수 있습니다.

### <a name="sdk-functions-related-to-trace-collection"></a>추적 수집과 관련된 SDK 함수

| 기능 | C++ API | C API |
|--|--|--|
| 추적 시작 | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| 추적 중지 | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| 추적 중지 후<br />즉시 결과 분석 | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| 추적 중지 후<br />즉시 결과를 다시 로깅 | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

다음 섹션에서는 분석 또는 다시 로깅 세션을 구성하는 방법을 보여 줍니다. 이는 [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md)와 같은 결합된 기능 함수에 필요합니다.

## <a name="consuming-a-trace"></a>추적 사용

ETW 추적이 있으면 C++ Build Insights SDK를 사용하여 압축을 풉니다. SDK는 도구를 신속하게 개발할 수 있는 형식으로 이벤트를 제공합니다. SDK를 사용하지 않고 원시 ETW 추적을 사용하지 않는 것이 좋습니다. MSVC에서 사용하는 이벤트 형식은 설명서가 제공되지 않으며, 대규모 빌드로 확장하도록 최적화되어 있고 이해하기 어렵습니다. 또한 C++ Build Insights SDK API는 안정적이지만 원시 ETW 추적 형식은 예고 없이 변경될 수 있습니다.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>추적 사용과 관련된 SDK 유형 및 함수

| 기능 | C++ API | C API | 참고 |
|--|--|--|--|
| 이벤트 콜백 설정 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++ Build Insights SDK는 콜백 함수를 통해 이벤트를 제공합니다. C++에서는 IAnalyzer 또는 IRelogger 인터페이스를 상속하는 분석기 또는 재로거 클래스를 만들어 콜백 함수를 구현합니다. C에서는 전역 함수에서 콜백을 구현하고 ANALYSIS_CALLBACKS 또는 RELOG_CALLBACKS 구조체에서 이에 대한 포인터를 제공합니다. |
| 그룹 빌드 | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | C++ API는 여러 분석기 및 재로거 개체를 그룹화하기 위한 도우미 함수와 형식을 제공합니다. 그룹은 복잡한 분석을 간단한 단계로 나눌 수 있는 간편한 방법입니다. [vcperf](https://github.com/microsoft/vcperf)는 이러한 방식으로 구성됩니다. |
| 분석 또는 다시 로깅 | [분석](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>분석 및 다시 로깅

분석 세션 또는 다시 로깅 세션을 통해 추적을 사용합니다.

대부분의 시나리오에서는 일반 분석을 사용하는 것이 적합합니다. 이 방법을 사용하면 `printf` 텍스트, xml, JSON, 데이터베이스, REST 호출 등 출력 형식을 유연하게 선택할 수 있습니다.

다시 로깅은 ETW 출력 파일을 생성해야 하는 특별한 용도의 분석에 사용할 수 있습니다. 다시 로깅을 사용하여 C++ Build Insights 이벤트를 고유한 ETW 이벤트 형식으로 변환할 수 있습니다. 다시 로깅을 사용하는 적절한 방법은 기존 ETW 도구 및 인프라에 C++ Insights 데이터를 연결하는 것입니다. 예를 들어 [vcperf](https://github.com/microsoft/vcperf)는 다시 로깅 인터페이스를 사용합니다. ETW 도구인 Windows 성능 분석기에서 이해할 수 있는 데이터를 생성해야 하기 때문입니다. 다시 로깅 인터페이스를 사용하려는 경우 ETW 작동 방식에 대한 몇 가지 사전 지식이 필요합니다.

### <a name="creating-analyzer-groups"></a>분석기 그룹 만들기

그룹을 만드는 방법을 알고 있어야 합니다. 활동 시작 이벤트를 수신할 때마다 *Hello, world!* 를 출력하는 방법을 보여 주는 예제는 다음과 같습니다.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>이벤트 사용

### <a name="sdk-types-and-functions-related-to-events"></a>이벤트와 관련된 SDK 유형 및 함수

| 기능 | C++ API | C API | 참고 |
|--|--|--|--|
| 이벤트 일치 및 필터링 | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | C++ API는 추적에서 관심 있는 이벤트를 쉽게 추출할 수 있는 함수를 제공합니다. C API를 사용하는 경우 이 필터링을 직접 수행해야 합니다. |
| 이벤트 데이터 형식 | [작업](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[컴파일러](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[이벤트](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[함수](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[호출](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[링커](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[스레드](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>작업 및 단순 이벤트

이벤트는 작업 및 단순 이벤트 두 가지 범주로 구분됩니다. 작업은 시작 및 종료 시간이 있는 지속적인 프로세스입니다. 단순 이벤트는 정확한 시간에 발생하며 기간이 없습니다. C++ Build Insights SDK를 사용하여 MSVC 추적을 분석하는 경우 작업이 시작 및 중지될 때 별도의 이벤트를 받게 됩니다. 단순 이벤트가 발생하는 경우에는 이벤트를 하나만 받습니다.

### <a name="parent-child-relationships"></a>부모-자식 관계

작업 및 단순 이벤트는 부모-자식 관계를 통해 서로 관련됩니다. 작업 또는 단순 이벤트의 부모는 이벤트가 발생하는 포괄 작업입니다. 예를 들어, 소스 파일을 컴파일할 때 컴파일러는 파일을 구문 분석한 다음 코드를 생성해야 합니다. 구문 분석 및 코드 생성 작업은 모두 컴파일러 작업의 자식입니다.

단순 이벤트에는 기간이 없으므로 그 안에 발생하는 다른 작업이 없습니다. 따라서 자식이 없습니다.

각 작업 및 단순 이벤트의 부모-자식 관계는 [이벤트 테이블](event-table.md)에 표시됩니다. C++ Build Insights 이벤트를 사용할 때 이러한 관계를 파악하는 것이 중요합니다. 이벤트의 전체 컨텍스트를 이해하려면 이러한 관계를 사용해야 하는 경우가 많습니다.

### <a name="properties"></a>속성

모든 이벤트에는 다음과 같은 속성이 있습니다.

| 속성 | Description |
|--|--|
| 유형 식별자 | 이벤트 유형을 고유하게 식별하는 번호입니다. |
| 인스턴스 식별자 | 추적 내에서 이벤트를 고유하게 식별하는 번호입니다. 추적에서 두 개의 동일한 유형의 이벤트가 발생하는 경우에는 둘 다 고유한 인스턴스 식별자가 부여됩니다. |
| 시작 시간 | 작업이 시작된 시간 또는 단순 이벤트가 발생한 시간입니다. |
| 프로세스 식별자 | 이벤트가 발생한 프로세스를 식별하는 번호입니다. |
| 스레드 식별자 | 이벤트가 발생한 스레드를 식별하는 번호입니다. |
| 프로세서 인덱스 | 이벤트를 내보낸 논리 프로세서를 나타내는 0부터 시작하는 인덱스입니다. |
| 이벤트 이름 | 이벤트 유형을 설명하는 문자열입니다. |

단순 이벤트 이외의 모든 작업에는 다음과 같은 속성도 있습니다.

| 속성 | Description |
|--|--|
| 중지 시간 | 작업이 중지된 시간입니다. |
| 전용 기간 | 자식 작업에 소요된 시간을 제외하고 작업에 소요된 시간입니다. |
| CPU 시간 | CPU가 작업에 연결된 스레드의 코드를 실행하는 데 걸린 시간입니다. 작업에 연결된 스레드가 중지된 시간은 포함하지 않습니다. |
| 전용 CPU 시간 | CPU 시간과 동일하지만 자식 작업에 소요된 CPU 시간은 제외됩니다. |
| 벽시계 시간 책임 | 전체 벽시계 시간에 대한 작업의 기여도입니다. 벽시계 시간 책임은 작업 간의 병렬 처리를 고려합니다. 예를 들어 관련이 없는 두 작업이 병렬로 실행된다고 가정하겠습니다. 두 작업은 모두 기간이 10초이며 시작 및 중지 시간이 정확히 동일합니다. 이 경우 Build Insights는 두 작업에 각각 5초의 벽시계 시간 책임을 할당합니다. 반면, 이러한 작업이 겹치지 않고 순서대로 실행되는 경우 각각 10초의 벽시계 시간 책임이 할당됩니다. |
| 전용 벽시계 시간 책임 | 벽시계 시간 책임과 동일하지만 자식 작업의 벽시계 시간 책임은 제외됩니다. |

일부 이벤트에는 언급한 속성 이외의 자체 속성이 있습니다. 이 경우 [이벤트 테이블](event-table.md)에 이러한 추가 속성이 나열됩니다.

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>C++ Build Insights SDK에서 제공하는 이벤트 사용

#### <a name="the-event-stack"></a>이벤트 스택

C++ Build Insights SDK는 이벤트를 항상 스택 형태로 제공합니다. 스택의 마지막 항목은 현재 이벤트이고, 그 이전 항목은 해당 부모 계층 구조입니다. 예를 들어 [LTCG](event-table.md#ltcg) 시작 및 중지 이벤트는 링커의 패스 1 도중에 발생합니다. 이 경우 수신하는 스택에는 다음이 포함됩니다. \[[LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. 부모 계층 구조는 이벤트를 루트로 다시 추적할 수 있으므로 편리합니다. 위에서 언급한 LTCG 작업이 느려지는 경우 관련된 링커 호출을 즉시 알아볼 수 있습니다.

#### <a name="matching-events-and-event-stacks"></a>이벤트 및 이벤트 스택 일치

C++ Build Insights SDK는 추적의 모든 이벤트를 제공하지만 하위 집합에만 관심이 있는 경우가 대부분입니다. 이벤트 스택의 하위 집합만 고려해야 하는 경우도 있습니다. SDK는 필요한 이벤트 또는 이벤트 스택을 신속하게 추출하고 그렇지 않은 이벤트를 거부하는 기능을 제공합니다. 이를 위해 다음과 같은 일치 함수가 사용됩니다.

| 기능 | Description |
|--|--|
| [MatchEvent](functions/match-event.md) | 이벤트가 지정된 유형 중 하나와 일치하면 이벤트를 유지합니다. 일치하는 이벤트를 람다 또는 다른 호출 가능 형식으로 전달합니다. 이 함수는 이벤트의 부모 계층 구조를 고려하지 않습니다. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | 이벤트가 멤버 함수의 매개 변수에 지정된 유형과 일치하면 이벤트를 유지합니다. 일치하는 이벤트를 멤버 함수로 전달합니다. 이 함수는 이벤트의 부모 계층 구조를 고려하지 않습니다. |
| [MatchEventStack](functions/match-event-stack.md) | 이벤트와 해당 부모 계층 구조가 모두 지정된 유형과 일치하면 이벤트를 유지합니다. 이벤트 및 일치하는 부모 계층 구조 이벤트를 람다 또는 다른 호출 가능 형식으로 전달합니다. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | 이벤트와 해당 부모 계층 구조가 모두 멤버 함수의 매개 변수 목록에 지정된 형식과 일치하면 이벤트를 유지합니다. 이벤트 및 일치하는 부모 계층 구조 이벤트를 멤버 함수로 전달합니다. |

`MatchEventStack`과 같은 이벤트 스택 일치 함수는 일치시킬 부모 계층 구조를 설명할 때 간격을 허용합니다. 예를 들어 \[[LINKER](event-table.md#linker), [LTCG](event-table.md#ltcg)\] 스택에 관심이 있다고 할 수 있습니다. 그러면 \[LINKER, [PASS1](event-table.md#pass1), LTCG\] 스택도 일치시킵니다. 지정된 마지막 유형은 일치시킬 이벤트 유형이어야 하며 부모 계층 구조의 일부가 아닙니다.

#### <a name="capture-classes"></a>캡처 클래스

`Match*` 함수를 사용하려면 일치시킬 유형을 지정해야 합니다. 이러한 유형은 캡처 클래스 목록에서 선택됩니다. 캡처 클래스는 아래에 설명된 여러 범주로 제공됩니다.

| 범주 | Description |
|--|--|
| Exact | 이러한 캡처 클래스는 특정 이벤트 유형을 일치시키는 데 사용됩니다. 예를 들어 [COMPILER](event-table.md#compiler) 이벤트를 일치시키는 [컴파일러](cpp-event-data-types/compiler.md) 클래스가 있습니다. |
| 와일드카드 | 이러한 캡처 클래스를 사용하여 지원되는 이벤트 목록의 모든 이벤트를 일치시킬 수 있습니다. 예를 들어 [작업](cpp-event-data-types/activity.md) 와일드카드는 모든 작업 이벤트를 일치시킵니다. 또 다른 예는 [FRONT_END_PASS](event-table.md#front-end-pass) 또는 [BACK_END_PASS](event-table.md#back-end-pass) 이벤트를 일치시키는 [CompilerPass](cpp-event-data-types/compiler-pass.md) 와일드카드입니다. |
| 그룹 | 그룹 캡처 클래스의 이름은 *Group*으로 끝납니다. 이러한 클래스는 간격을 무시하고 한 행에 있는 동일한 형식의 여러 이벤트를 일치시키는 데 사용됩니다. 이벤트 스택에 있는 이벤트 수를 알 수 없으므로 재귀 이벤트를 일치시킬 때만 의미가 있습니다. 예를 들어 [FRONT_END_FILE](event-table.md#front-end-file) 작업은 컴파일러가 파일을 구문 분석할 때마다 발생합니다. 컴파일러가 파일을 구문 분석하는 동안 include 지시문을 찾을 수 있기 때문에 이 작업은 재귀적입니다. [FrontEndFile](cpp-event-data-types/front-end-file.md) 클래스는 스택에서 하나의 FRONT_END_FILE 이벤트만 일치시킵니다. 전체 include 계층 구조를 일치시키려면 [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) 클래스를 사용합니다. |
| 와일드카드 그룹 | 와일드카드 그룹은 와일드카드 및 그룹의 속성이 결합되어 있습니다. 이 범주의 유일한 클래스는 단일 이벤트 스택의 모든 [LINKER](event-table.md#linker) 및 [COMPILER](event-table.md#compiler) 이벤트를 일치시키고 캡처하는 [InvocationGroup](cpp-event-data-types/invocation-group.md)입니다. |

각 이벤트를 일치시키는 데 사용할 수 있는 캡처 클래스는 [이벤트 테이블](event-table.md)을 참조하세요.

#### <a name="after-matching-using-captured-events"></a>일치 후: 캡처한 이벤트 사용

일치가 성공적으로 완료되면 `Match*` 함수는 캡처 클래스 개체를 생성하여 지정된 함수에 전달합니다. 이러한 캡처 클래스 개체를 사용하여 이벤트의 속성에 액세스합니다.

#### <a name="example"></a>예제

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
