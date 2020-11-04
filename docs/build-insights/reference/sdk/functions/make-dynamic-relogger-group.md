---
title: MakeDynamicReloggerGroup
description: C++ Build Insights SDK MakeDynamicReloggerGroup 함수 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6bfa5bfbe8a61148f925ba185fccc035fd44d02d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920270"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`MakeDynamicReloggerGroup` 함수는 동적 재로거 그룹을 만드는 데 사용됩니다. 재로거 그룹의 멤버는 추적의 모든 이벤트가 처리될 때까지 왼쪽에서 오른쪽으로 하나씩 이벤트를 수신합니다.

## <a name="syntax"></a>구문

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>매개 변수

*reloggers*\
동적 재로거 그룹에 포함된 [IRelogger](../other-types/irelogger-class.md) 포인터의 벡터입니다. 이러한 포인터는 원시, `std::unique_ptr` 또는 `std::shared_ptr`일 수 있습니다. 상속 관계로 인해 [IAnalyzer](../other-types/ianalyzer-class.md) 포인터는 `IRelogger` 포인터로도 간주됩니다.

### <a name="return-value"></a>반환 값

동적 재로거 그룹. **`auto`** 키워드를 사용하여 반환 값을 캡처합니다.

## <a name="remarks"></a>설명

정적 재로거 그룹과 달리 동적 재로거 그룹의 멤버는 컴파일 시간에 알려지지 않아도 됩니다. 런타임에 프로그램 입력을 기반으로 재로거 그룹 멤버를 선택하거나 컴파일 시간에 알 수 없는 다른 값을 기반으로 선택할 수 있습니다. 정적 재로거 그룹과 달리 동적 재로거 그룹 내의 [`IRelogger`](../other-types/irelogger-class.md) 포인터는 다형 동작을 가지며 가상 함수 호출이 올바르게 디스패치됩니다. 이러한 유연성으로 인해 이벤트 처리 시간이 느려질 수 있습니다. 컴파일 시간에 모든 재로거 그룹 멤버가 알려지고 다형 동작이 필요하지 않은 경우에는 정적 재로거 그룹을 사용하는 것이 좋습니다. 정적 재로거 그룹을 사용하려면 대신 [`MakeStaticReloggerGroup`](make-static-relogger-group.md)을 호출합니다.

동적 재로거 그룹은 정적 재로거 그룹 내부에 캡슐화할 수 있습니다. [`MakeStaticReloggerGroup`](make-static-relogger-group.md)에 해당 주소를 전달합니다. [`Relog`](relog.md)와 같이 정적 재로거 그룹만 허용하는 함수에 동적 재로거 그룹을 전달하는 데 이 기법을 사용합니다.

::: moniker-end
