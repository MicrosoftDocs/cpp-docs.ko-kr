---
description: '자세한 정보: Interop에 대 한 성능 고려 사항 (c + +)'
title: Interop에 대한 성능 고려 사항(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29723f0ea5c7b745100ab4c7abb7f59abce47db6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255563"
---
# <a name="performance-considerations-for-interop-c"></a>Interop에 대한 성능 고려 사항(C++)

이 항목에서는 런타임 성능에 대 한 관리 되는/관리 되지 않는 interop 전환의 효과를 줄이기 위한 지침을 제공 합니다.

Visual C++는 Visual Basic 및 c # (P/Invoke)와 같은 다른 .NET 언어와 동일한 상호 운용성 메커니즘을 지원 하지만 Visual C++ (c + + interop)와 관련 된 interop 지원도 제공 합니다. 성능이 중요 한 응용 프로그램의 경우 각 interop 기술의 성능 영향을 이해 하는 것이 중요 합니다.

사용 된 interop 기술에 관계 없이 관리 되는 함수가 관리 되지 않는 함수를 호출 하 고 그 반대의 경우에는 썽크 라는 특수 전환 시퀀스가 필요 합니다. 이러한 썽크는 Microsoft c + + 컴파일러에 의해 자동으로 삽입 되지만, 누적 된 이러한 전환에는 성능 측면에서 비용이 많이 들 수 있습니다.

## <a name="reducing-transitions"></a>전환 줄이기

Interop 썽크의 비용을 방지 하거나 줄이는 한 가지 방법은 관리 되는/관리 되지 않는 전환을 최소화 하기 위해 관련 된 인터페이스를 리팩터링 하는 것입니다. 관리 되는/관리 되지 않는 경계를 넘어 자주 호출 하는 번잡 인터페이스를 대상으로 하 여 성능을 크게 향상 시킬 수 있습니다. 예를 들어 루프에서 관리 되지 않는 함수를 호출 하는 관리 되는 함수는 리팩터링을 위한 좋은 후보입니다. 루프 자체가 관리 되지 않는 쪽으로 이동 하거나 관리 되지 않는 호출에 대 한 관리 되는 대안이 생성 된 경우 (관리 되는 쪽에서 데이터를 큐에 대기 했다가 루프 후에 관리 되지 않는 API로 마샬링할 수 있음) 전환 횟수가 현저 하 게 줄어들 수 있습니다.

## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs c + + Interop

Visual Basic 및 c #과 같은 .NET 언어의 경우 네이티브 구성 요소와의 상호 운용을 위해 지정 된 메서드는 P/Invoke입니다. P/Invoke는 .NET Framework에서 지원 되기 때문에 Visual C++도 지원 하지만, Visual C++는 c + + Interop 라고 하는 자체 상호 운용성 지원도 제공 합니다. P/Invoke는 형식이 안전 하지 않으므로 P/Invoke 보다 c + + Interop를 선호 합니다. 결과적으로 오류는 주로 런타임에 보고 되지만 c + + Interop는 P/Invoke에 비해 성능상의 이점이 있습니다.

두 기술 모두 관리 되는 함수가 관리 되지 않는 함수를 호출할 때마다 발생 하는 몇 가지 작업이 필요 합니다.

- 함수 호출 인수는 CLR에서 네이티브 형식으로 마샬링됩니다.

- 관리 되는 관리 되지 않는 썽크를 실행 합니다.

- 관리 되지 않는 함수를 호출 합니다 (인수의 네이티브 버전 사용).

- 관리 되지 않는 썽크의 썽크를 실행 합니다.

- 반환 형식 및 "out" 또는 "in, out" 인수는 네이티브에서 CLR 형식으로 마샬링됩니다.

관리 되는/관리 되지 않는 썽크는 interop가 전혀 작동 하기 위해 필요 하지만 필요한 데이터 마샬링은 관련 된 데이터 형식, 함수 서명 및 데이터가 사용 되는 방법에 따라 달라 집니다.

C + + Interop에서 수행 하는 데이터 마샬링은 가장 간단한 형태입니다. 매개 변수는 단순히 비트 방식으로 관리 되는/관리 되지 않는 경계를 넘어 복사 됩니다. 변환이 전혀 수행 되지 않습니다. P/Invoke의 경우이는 모든 매개 변수가 단순 하 고 blittable 형식인 경우에만 적용 됩니다. 그렇지 않으면 P/Invoke는 각각의 관리 되는 매개 변수를 적절 한 네이티브 형식으로 변환 하는 매우 강력한 단계를 수행 하 고, 인수가 "out" 또는 "in"으로 표시 되는 경우 그 반대의 경우도 마찬가지입니다.

즉, c + + Interop는 가장 빠르게 가능한 데이터 마샬링 메서드를 사용 하는 반면 P/Invoke는 가장 강력한 메서드를 사용 합니다. 즉, c + +에서 일반적으로 사용 되는 방식으로 c + + Interop는 기본적으로 최적의 성능을 제공 하 고, 프로그래머는이 동작이 안전 하거나 적절 하지 않은 경우를 해결 해야 합니다.

따라서 c + + Interop를 사용 하려면 명시적으로 데이터 마샬링을 제공 해야 하지만, 프로그래머는 데이터의 특성과 사용 방법을 고려 하 여 적절 한 것을 자유롭게 결정할 수 있습니다. 또한 P/Invoke 데이터 마샬링에 대 한 동작을 사용자 지정에서 수준까지 수정할 수 있지만 c + + Interop를 사용 하면 호출을 호출 하 여 데이터 마샬링을 사용자 지정할 수 있습니다. P/Invoke에서는 이렇게 할 수 없습니다.

C + + Interop에 대 한 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
