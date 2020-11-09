---
title: InjectEvent
description: C++ Build Insights SDK InjectEvent 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4d85f17a6d553d9dffa727824e6d4de94518645
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922844"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`InjectEvent` 함수는 [IRelogger](../other-types/irelogger-class.md) 인터페이스를 구현하는 재로거 내에서 호출됩니다. 다시 로깅 세션의 출력 추적 파일에 ETW(Windows용 이벤트 추적)를 쓰는 용도로 사용합니다.

## <a name="syntax"></a>구문

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>매개 변수

*relogSession*\
다시 로깅 세션에 대한 포인터입니다. 다시 로깅 세션은 `IRelogger` 인터페이스를 구현하는 재로거에 제공됩니다. 자세한 내용은 [IRelogger](../other-types/irelogger-class.md)를 참조하세요.

*providerId*\
ETW(Windows용 이벤트 추적) 이벤트가 다시 로깅되는 ETW 공급자 GUID입니다.

*eventDescriptor*\
다시 로깅된 ETW 이벤트의 ETW 이벤트 설명자입니다.

*processId*\
다시 로깅된 ETW 이벤트의 PID(프로세스 식별자)입니다.

*threadId*\
다시 로깅된 ETW 이벤트의 TID(스레드 식별자)입니다.

*processorIndex*\
다시 로깅된 ETW 이벤트의 프로세서 인덱스입니다.

*timestamp*\
다시 로깅된 ETW 이벤트의 타임스탬프입니다.

*data*\
다시 로깅된 ETW 이벤트에 포함되어야 하는 데이터에 대한 포인터입니다.

*byteCount*\
*data* 로 가리키는 데이터의 크기(바이트)입니다.

## <a name="remarks"></a>설명

공급자 GUID와 이벤트 설명자 같은 ETW 개념에 관한 자세한 내용은 [ETW 설명서](/windows/win32/etw/about-event-tracing)를 참조하세요. C++ Build Insights SDK로 다시 로깅 세션을 시작하는 자세한 방법은 [Relog](relog.md)를 참조하세요.

::: moniker-end
