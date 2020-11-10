---
title: IAnalyzer 클래스
description: C++ Build Insights SDK IAnalyzer 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2514dd305a186d1153e9f9d1711bb774ea70cdf9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919815"
---
# <a name="ianalyzer-class"></a>IAnalyzer 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`IAnalyzer` 클래스는 ETW(Windows용 이벤트 추적)를 분석하기 위한 인터페이스를 제공합니다. 이 클래스는 [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md) 및 [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) 함수와 함께 사용합니다. `IAnalyzer`를 기본 클래스로 사용하여 분석기 또는 재로거 그룹의 일부가 될 수 있는 자체 분석기를 만드세요.

## <a name="syntax"></a>구문

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>설명

`IAnalyzer`에서 파생되는 클래스는 분석기와 재로거로 모두 사용될 수 있습니다. 재로거로 사용되는 경우 재로거 관련 함수가 해당 분석기 함수로 리디렉션됩니다. 그 역은 성립하지 않습니다. `IRelogger`에서 파생되는 클래스는 분석기로 사용될 수 없습니다. 재로거 그룹에서 분석기를 사용하는 것은 일반적인 패턴입니다. 재로거 그룹의 초기 위치에 배치된 분석기는 정보를 미리 계산하여 이후 위치에서 재로거에 제공할 수 있습니다.

재정의되지 않는 모든 함수의 기본 반환 값은 `AnalysisControl::CONTINUE`입니다. 자세한 내용은 [AnalysisControl](analysis-control-enum-class.md)을 참조하세요.

## <a name="members"></a>멤버

`IRelogger` 인터페이스의 [OnTraceInfo](irelogger-class.md#on-trace-info) 멤버 외에도 `IAnalyzer` 클래스에는 다음 멤버가 포함됩니다.

### <a name="destructor"></a>소멸자

[~IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a> ~IAnalyzer

IAnalyzer 클래스를 제거합니다.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a> OnBeginAnalysis

분석기 그룹의 분석기 부분의 경우 이 함수는 첫 번째 분석 패스가 시작되기 전에 호출됩니다. 재로거 그룹의 분석기 부분의 경우 이 함수는 다시 로깅 패스가 시작되기 전에 호출됩니다. 동일한 다시 로깅 세션의 분석기 및 재로거 그룹의 분석기 부분의 경우 이 함수는 첫 번째 분석 패스가 시작되기 전에 두 번 호출됩니다.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a> OnBeginAnalysisPass

분석기 그룹의 분석기 부분의 경우 이 함수는 모든 분석 패스 시작 시 호출됩니다. 재로거 그룹의 분석기 부분의 경우 이 함수는 재로거 패스 시작 시 호출됩니다. 동일한 다시 로깅 세션의 분석기 및 재로거 그룹의 분석기 부분의 경우 이 함수는 모든 분석 패스 시작 시와 재로거 패스 시작 시 호출됩니다.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a> OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

이 함수는 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 이 함수는 호출을 [OnBeginAnalysis](#on-begin-analysis)로 리디렉션합니다.

### <a name="return-value"></a>반환 값

[OnBeginAnalysis](#on-begin-analysis) 호출의 결과입니다.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a> OnBeginReloggingPass

이 함수는 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 이 함수는 호출을 [OnBeginAnalysisPass](#on-begin-analysis-pass)로 리디렉션합니다.

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>반환 값

[OnBeginAnalysisPass](#on-begin-analysis-pass) 호출의 결과입니다.

## <a name="onendanalysis"></a><a name="on-end-analysis"></a> OnEndAnalysis

분석기 그룹의 일부인 분석기의 경우 이 함수는 마지막 분석 패스가 끝난 후에 호출됩니다. 재로거 그룹의 일부인 분석기의 경우 이 함수는 다시 로깅 패스가 끝난 후에 호출됩니다. 동일한 다시 로깅 세션의 분석기 및 재로거 그룹의 일부인 분석기의 경우 이 함수는 다음 경우에 두 번 호출됩니다.

1. 모든 분석 패스가 끝난 후 및 다시 로깅 패스가 시작되기 전
1. 다시 로깅 패스가 끝난 후

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a> OnEndAnalysisPass

분석기 그룹의 분석기 부분의 경우 이 함수는 모든 분석 패스가 끝날 때 호출됩니다. 재로거 그룹의 분석기 부분의 경우 이 함수는 재로거 패스가 끝날 때 호출됩니다. 동일한 다시 로깅 세션의 분석기 및 재로거 그룹의 분석기 부분의 경우 이 함수는 모든 분석 패스가 끝날 때와 재로거 패스가 끝날 때 호출됩니다.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a> OnEndRelogging

이 함수는 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 이 함수는 호출을 [OnEndAnalysis](#on-end-analysis)로 리디렉션합니다.

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>반환 값

[OnEndAnalysis](#on-end-analysis) 호출의 결과입니다.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a> OnEndReloggingPass

이 함수는 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 이 함수는 호출을 [OnEndAnalysisPass](#on-end-analysis-pass)로 리디렉션합니다.

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>반환 값

[OnEndAnalysisPass](#on-end-analysis-pass) 호출의 결과입니다.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a> OnSimpleEvent

이 함수는 단순 이벤트가 처리 중일 때 호출됩니다. 이 함수의 두 번째 버전은 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 버전 2에 대한 모든 호출은 버전 1로 리디렉션됩니다.

### <a name="version-1"></a>버전 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>버전 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>매개 변수

*eventStack*\
이 단순 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [이벤트](../event-table.md)를 참조하세요.

*relogSession*\
이 매개 변수는 사용되지 않습니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onstartactivity"></a><a name="on-start-activity"></a> OnStartActivity

이 함수는 작업 시작 이벤트가 처리 중일 때 호출됩니다. 이 함수의 두 번째 버전은 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 버전 2에 대한 모든 호출은 버전 1로 리디렉션됩니다.

### <a name="version-1"></a>버전 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>버전 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>매개 변수

*eventStack*\
이 작업 시작 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [이벤트](../event-table.md)를 참조하세요.

*relogSession*\
이 매개 변수는 사용되지 않습니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a> OnStopActivity

이 함수는 작업 중지 이벤트가 처리 중일 때 호출됩니다. 이 함수의 두 번째 버전은 재정의될 수 없습니다. 분석기가 재로거 그룹의 일부인 경우 C++ Build Insights SDK가 이 함수를 호출합니다. 버전 2에 대한 모든 호출은 버전 1로 리디렉션됩니다.

### <a name="version-1"></a>버전 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>버전 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>매개 변수

*eventStack*\
이 작업 중지 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [이벤트](../event-table.md)를 참조하세요.

*relogSession*\
이 매개 변수는 사용되지 않습니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

::: moniker-end
