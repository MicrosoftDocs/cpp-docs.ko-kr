---
title: IRelogger 클래스
description: C++ Build Insights SDK IRelogger 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e504ece95529f7279650062145f3ac0914449c98
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922518"
---
# <a name="irelogger-class"></a>IRelogger 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`IRelogger` 클래스는 Windows용 이벤트 추적(ETW)을 다시 로깅하기 위한 인터페이스를 제공합니다. [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) 및 [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) 함수와 함께 사용합니다. `IRelogger`를 기본 클래스로 사용하여 재로거 그룹의 일부가 될 수 있는 자체 분석기를 만드세요.

## <a name="syntax"></a>구문

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>설명

재정의되지 않는 모든 함수의 기본 반환 값은 `AnalysisControl::CONTINUE`입니다. 자세한 내용은 [AnalysisControl](analysis-control-enum-class.md)을 참조하세요.

## <a name="members"></a>멤버

### <a name="destructor"></a>소멸자

[~IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a> ~IRelogger

IRelogger 클래스를 제거합니다.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a> OnBeginRelogging

이 함수는 다시 로깅 패스가 시작되기 전에 호출됩니다.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a> OnBeginReloggingPass

이 함수는 다시 로깅 패스가 시작될 때 호출됩니다.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a> OnEndRelogging

이 함수는 다시 로깅 패스가 종료된 후에 호출됩니다.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a> OnEndReloggingPass

이 함수는 다시 로깅 패스가 끝날 때 호출됩니다.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a> OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

이 함수는 단순 이벤트가 처리 중일 때 호출됩니다.

### <a name="parameters"></a>매개 변수

*eventStack*\
이 단순 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [Events](../event-table.md)를 참조하세요.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onstartactivity"></a><a name="on-start-activity"></a> OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

이 함수는 작업 시작 이벤트가 처리 중일 때 호출됩니다.

### <a name="parameters"></a>매개 변수

*eventStack*\
이 작업 시작 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [Events](../event-table.md)를 참조하세요.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a> OnStopActivity

이 함수는 작업 중지 이벤트가 처리 중일 때 호출됩니다.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>매개 변수

*eventStack*\
이 활동 중지 이벤트의 이벤트 스택입니다. 이벤트 스택에 대한 자세한 내용은 [Events](../event-table.md)를 참조하세요.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a> OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

이 함수는 모든 분석 또는 다시 로깅 패스가 시작될 때 한 번만 호출됩니다.

### <a name="parameters"></a>매개 변수

*traceInfo*\
사용 중인 추적에 대한 유용한 속성을 포함하는 [TraceInfo](../cpp-event-data-types/trace-info.md) 개체입니다.

### <a name="return-value"></a>반환 값

다음에 해야 하는 작업을 설명하는 [AnalysisControl](analysis-control-enum-class.md) 코드입니다.

::: moniker-end
