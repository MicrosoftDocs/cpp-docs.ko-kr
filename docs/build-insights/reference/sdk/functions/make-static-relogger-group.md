---
title: MakeStaticReloggerGroup
description: C++ Build Insights SDK MakeStaticReloggerGroup 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1d49f15a14675f265e1f63ef8795f442f49ad5d4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920205"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MakeStaticReloggerGroup` 함수는 [Relog](relog.md)와 같은 함수에 전달할 수 있는 정적 재로거 그룹을 만드는 데 사용됩니다. 재로거 그룹의 멤버는 추적의 모든 이벤트가 처리될 때까지 왼쪽에서 오른쪽으로 하나씩 이벤트를 수신합니다.

## <a name="syntax"></a>구문

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>매개 변수

*TReloggerPtrs*\
이 매개 변수는 항상 추론됩니다.

*reloggers*\
정적 재로거 그룹에 포함된 [`IRelogger`](../other-types/irelogger-class.md) 포인터의 매개 변수 팩입니다. 이러한 포인터는 원시, `std::unique_ptr` 또는 `std::shared_ptr`일 수 있습니다. 상속 관계로 인해 [`IAnalyzer`](../other-types/ianalyzer-class.md) 포인터는 `IRelogger` 포인터로도 간주됩니다.

### <a name="return-value"></a>반환 값

정적 재로거 그룹입니다. **`auto`** 키워드를 사용하여 반환 값을 캡처합니다.

## <a name="remarks"></a>설명

동적 재로거 그룹과 달리 정적 재로거 그룹의 멤버는 컴파일 시간에 알 수 있어야 합니다. 또한 정적 재로거 그룹에는 다형 동작이 없는 [`IRelogger`](../other-types/irelogger-class.md) 포인터가 포함됩니다. 정적 재로거 그룹을 사용하여 ETW(Windows용 이벤트 추적) 추적을 분석하는 경우 `IRelogger` 인터페이스를 호출하면 항상 재로거 그룹 멤버가 직접 가리키는 개체로 확인됩니다. 이러한 유연성 손실로 이벤트 처리 시간이 빨라질 수 있습니다. 컴파일 시간에 재로거 그룹의 멤버를 알 수 없거나 `IRelogger` 포인터에 다형 동작이 필요한 경우에는 동적 재로거 그룹을 사용하는 것이 좋습니다. 대신 [`MakeDynamicReloggerGroup`](make-dynamic-relogger-group.md)을 호출하여 동적 재로거 그룹을 사용할 수 있습니다.

::: moniker-end
