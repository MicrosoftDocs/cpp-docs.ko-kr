---
description: '자세한 정보: 부동 소수점 마이그레이션 문제'
title: 부동 소수점 마이그레이션 문제
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: 079706570a52d164f4308941924d0a96ca5d44ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312906"
---
# <a name="floating-point-migration-issues"></a>부동 소수점 마이그레이션 문제

프로젝트를 최신 버전의 Visual Studio로 업그레이드할 때 특정 부동 소수점 연산의 결과가 변경될 수 있습니다. 일반적으로 이 문제는 두 가지 이유 즉, 사용 가능한 프로세서를 더 효율적으로 활용하는 코드 생성 변경, CRT(C 런타임 라이브러리)에서 수학 함수에 사용된 알고리즘 변경 또는 버그 수정 중 한 가지 이유로 인해 발생합니다. 일반적으로 언어 표준에 지정된 범위 내에서는 새 결과가 올바릅니다. 변경된 내용과 함수에서 이전에 얻은 것과 동일한 결과를 구하는 방법을 알아보려면 계속 읽어보세요.

## <a name="new-math-functions-and-universal-crt-changes"></a>새 수학 함수 및 유니버설 CRT 변경

대부분의 CRT 수학 함수가 수 년 동안 Visual Studio에서 사용 가능했지만, Visual Studio 2013 이상에는 ISO C99에 필요한 모든 함수가 포함되어 있습니다. 이러한 함수는 수정을 통해 성능을 균형있게 분배하도록 구현됩니다. 모든 경우에 올바르게 반올림된 결과를 생성하는 것은 막대한 비용이 들 수 있으므로 이러한 함수는 올바르게 반올림된 결과에 대한 근사치를 효율적으로 생성하도록 설계됩니다. 부정확성이 더 큰 경우도 있을 수 있지만 대부분은 생성된 결과가 올바르게 반올림된 결과의 +/-1 *ULP*(Unit of Least Precision) 내에 있습니다. 이전에는 다른 수학 라이브러리를 사용하여 이러한 함수를 가져올 경우 구현 차이로 인해 결과가 변경될 수 있었습니다.

Visual Studio 2015에서 수학 함수를 유니버설 CRT로 이동하면서 몇 가지 새로운 알고리즘을 사용하고 Visual Studio 2013에서 새롭게 발생한 여러 함수 구현 관련 버그를 수정했습니다. 이러한 변경으로 인해 해당 함수를 사용하는 부동 소수점 계산 결과가 달라질 수 있습니다. 버그 문제가 있었던 함수로는 erf, exp2, remainder, remquo, scalbln, scalbn 등과 이들의 float 및 long double variant가 있습니다.  또한 Visual Studio 2015에서는 _clear87, _clearfp, fegetenv, fesetenv 및 feholdexcept 함수의 부동 소수점 상태 단어 및 예외 상태 정보 유지 관련 문제가 해결되었습니다.

## <a name="processor-differences-and-compiler-flags"></a>프로세서 차이점 및 컴파일러 플래그

대부분의 부동 소수점 수학 라이브러리 함수에는 다양한 CPU 아키텍처에 대한 다양한 구현이 있습니다. 예를 들어 32비트 x86 CRT에는 64비트 x64 CRT와 다른 구현이 있을 수 있습니다. 또한 일부 함수에는 지정된 CPU 아키텍처에 대한 여러 구현이 있을 수 있습니다. 가장 효율적인 구현은 CPU에서 지원되는 명령 집합에 따라 런타임에 동적으로 선택됩니다. 예를 들어 32비트 x86 CRT에서 일부 함수에는 x87 구현 및 an SSE2 구현이 둘 다 있습니다. SSE2를 지원하는 CPU에서 실행될 경우 더 빠른 SSE2 구현이 사용됩니다. SSE2를 지원하지 않는 CPU에서 실행될 경우 더 느린 x87 구현이 사용됩니다. 기본 x86 컴파일러 아키텍처 옵션이 Visual Studio 2012에서 [/arch:SSE2](../build/reference/arch-x86.md)로 변경되었기 때문에 이전 코드를 마이그레이션할 때 이렇게 표시될 수 있습니다. 수학 라이브러리 함수의 구현에 따라 다른 CPU 명령 및 다른 알고리즘을 사용하여 결과를 생성할 수 있으므로 플랫폼에 따라 함수에서 다른 결과가 생성될 수 있습니다. 대부분은 결과가 올바르게 반올림된 결과의 +/-1 ulp 내에 있지만 실제 결과는 CPU에 따라 달라질 수 있습니다.

또한 Visual Studio에서 다른 부동 소수점 모드의 코드 생성 정확성이 향상되어 부동 소수점 연산 결과에 영향을 줄 수 있습니다. 이는 이전 코드와 새 코드에서 동일한 컴파일러 플래그를 사용하더라도 마찬가지입니다. 예를 들어 [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md)(기본값) 또는 `/fp:strict`를 지정할 때 Visual Studio 2010에서 생성되는 코드는 식을 통해 중간 NaN(Not-a-Number) 값을 올바르게 전파하지 못할 수 있습니다. 따라서 이전 컴파일러에서 숫자 결과를 제공하는 일부 식에서 이제 올바른 NaN 결과를 생성할 수 있습니다. `/fp:fast`에 대해 활성화된 코드 최적화에서 이제 더 많은 프로세서 기능을 이용하기 때문에 차이가 나타날 수도 있습니다. 이러한 최적화로 더 적은 명령을 사용할 수 있지만 이전에 표시된 일부 중간 연산이 제거되었기 때문에 생성되는 결과에 영향을 줄 수 있습니다.

## <a name="how-to-get-identical-results"></a>동일한 결과를 얻는 방법

대부분의 경우 최신 컴파일러 및 라이브러리의 부동 소수점 변경으로 인해 더 빠르거나 더 정확하게 동작합니다. x87 명령을 SSE2 명령으로 바꾸면 프로세서 전원 성능이 향상될 수 있습니다. 하지만 이전 컴파일러의 부동 소수점 동작을 정확하게 복제해야 하는 코드가 있는 경우 Visual Studio 네이티브 멀티 타기팅 기능을 사용하고 이전 도구 집합으로 해당 프로젝트를 빌드하는 것이 좋습니다. 자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](use-native-multi-targeting.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[이전 버전의 Visual C++에서 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[잠재적인 업그레이드 문제 개요(Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Visual C++ 변경 기록 2003 - 2015](visual-cpp-change-history-2003-2015.md)
