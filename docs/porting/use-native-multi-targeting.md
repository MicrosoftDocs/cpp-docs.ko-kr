---
description: '자세한 정보: Visual Studio에서 네이티브 다중 대상 지정을 사용 하 여 이전 프로젝트 빌드'
title: Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: d7f7ea617ac5f895a6fb9b04f89caebbb6130e43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331198"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드

일반적으로 최신 버전 Visual Studio를 설치할 때 프로젝트를 업데이트하는 것이 좋습니다. 대개 프로젝트 및 코드를 업데이트하는 데 필요한 비용이 새로운 IDE, 컴파일러, 라이브러리 및 도구에서 얻는 혜택보다 큽니다. 그러나 일부 프로젝트는 업데이트할 수 없습니다. 유지 관리 상의 이유로 업그레이드할 수 없는 이전 라이브러리 또는 플랫폼에 연결 된 이진 파일이 있을 수 있습니다. 더 최근 컴파일러로 이동된 경우 중단되는 비표준 언어 생성자가 코드에서 사용될 수 있습니다. 코드가 Visual C++의 특정 버전용으로 컴파일된 타사 라이브러리에 의존할 수 있습니다. 또는 Visual C++의 특정 이전 버전을 대상으로 지정해야 하는 타사용 라이브러리를 생성할 수 있습니다.

다행히도 Visual Studio 2017 및 Visual Studio 2015를 사용하여 이전 컴파일러 도구 집합 및 라이브러리를 대상으로 지정하는 프로젝트를 빌드할 수 있습니다. IDE에서 새 기능을 이용하기 위해 Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 또는 Visual Studio 2015 프로젝트를 업그레이드할 필요가 없습니다.

- 새 C++ 리팩터링 기능 및 편집기 실험 기능
- 새로운 진단 도구 디버거 창 및 오류 목록 창
- 새로운 중단점, 예외 창 및 새 PerfTips
- 새 코드 탐색 및 검색 도구
- 새 C++ 빠른 픽스 및 Productivity Power Tools 확장.

Visual Studio 2008 프로젝트를 대상으로 지정할 수도 있지만 변경이 필요합니다. 자세한 내용은 **Visual Studio 2008에 대한 지침** 섹션을 참조하세요.

최신 버전의 Visual Studio에서는 프로젝트의 네이티브 멀티 타기팅 및 라운드트립을 지원합니다. 네이티브 멀티 타기팅은 이전 버전의 Visual Studio에서 설치된 도구 집합을 사용하여 빌드되는 최신 IDE의 기능입니다. 라운드트립은 프로젝트를 변경하지 않고 이전 IDE 버전에서 만들어진 프로젝트를 로드하는 최신 IDE의 기능입니다. 기존 버전과 함께 최신 버전의 Visual Studio를 단계별로 설치할 경우 기존 버전의 컴파일러 및 도구와 함께 새 버전의 IDE를 사용하여 프로젝트를 빌드할 수 있습니다. 팀의 다른 구성원이 이전 버전의 Visual Studio에서 프로젝트를 계속 사용할 수 있습니다.

이전 도구 집합을 사용할 경우 대부분의 최신 IDE 기능을 이용할 수 있지만 C++ 컴파일러, 라이브러리 및 빌드 도구의 최신 고급 기능을 이용할 수 없습니다. 예를 들어 새 언어 규칙 향상, 새 디버깅 및 코드 분석 기능을 사용하거나 최신 도구 집합의 더 빠른 빌드 처리량을 얻을 수 없습니다. 이전 도구 집합과 호환되지 않는 몇몇 IDE 기능도 있습니다. 예를 들어 메모리 프로파일러에 형식 정보가 없을 수 있고, 리팩터링 작업 **원시 문자열 리터럴로 변환** 에서는 Visual Studio 2012 또는 이전 도구 집합을 사용할 경우 컴파일되지 않는 C++11 규격 코드를 생성합니다.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Visual Studio에서 네이티브 멀티 타기팅을 사용하는 방법

이전 버전과 함께 Visual Studio를 단계별로 설치한 후 새 버전의 Visual Studio에서 기존 프로젝트를 엽니다. 프로젝트가 로드되면 최신 C++ 컴파일러 및 라이브러리를 사용하도록 프로젝트를 업그레이드할지 묻는 메시지가 표시됩니다. 프로젝트에서 이전 컴파일러 및 라이브러리를 유지하고자 하므로 **취소** 단추를 선택합니다.

Visual Studio는 프로젝트를 지속적으로 업그레이드합니다. 프로젝트를 로드할 때마다 업그레이드 대화 상자가 표시되지 않게 하려면 프로젝트에서 다음 속성을 정의하거나 프로젝트가 가져오는 .props 또는 .targets 파일에서 정의할 수 있습니다.

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

프로젝트를 업그레이드하려면 이 속성을 제거해야 합니다.

업그레이드하지 않도록 선택하면 Visual Studio에서는 솔루션 또는 프로젝트 파일을 변경하지 않습니다. 프로젝트를 빌드할 때 생성된 이진 파일은 이전 버전의 Visual Studio를 통해 빌드한 이진 파일과 완전히 호환됩니다. 이는 Visual Studio에서는 같은 C++ 컴파일러를 사용하고 이전 IDE와 함께 제공된 같은 라이브러리를 연결하기 때문입니다. 또한 **취소** 를 선택할 경우 이전 Visual Studio 버전이 계속 설치되어 있음을 경고하는 업그레이드 대화 상자가 표시되는 이유이기도 합니다.

## <a name="instructions-for-visual-studio-2008"></a>Visual Studio 2008에 대한 지침

Visual Studio 2008에는 **VCBuild** 라는 C++에 대한 자체 전용 빌드 시스템이 있었습니다. Visual Studio 2010부터 Visual Studio C++ 프로젝트는 **MSBuild** 를 사용하도록 변경되었습니다. 즉, 영구적으로 업그레이드 하거나 다중 대상을 지정 하는 경우 최신 버전의 Visual Studio에서 Visual Studio 2008 프로젝트를 빌드하기 위해 업데이트 단계를 진행 해야 합니다. 업데이트된 프로젝트는 Visual Studio 2008 IDE를 사용하여 만들어진 이진 파일과 완전히 호환되는 이진 파일을 생성합니다.

먼저 현재 버전의 Visual Studio 외에 Visual Studio 2010을 Visual Studio 2008과 같은 컴퓨터에 설치해야 합니다. Visual Studio 2008 프로젝트를 대상으로 지정하는 데 필요한 **MSBuild** 스크립트는 Visual Studio 2010에서만 설치합니다.

다음으로 Visual Studio 2008 솔루션 및 프로젝트를 현재 버전의 Visual Studio로 업데이트해야 합니다. 업그레이드하기 전에 프로젝트 및 솔루션 파일의 백업을 만드는 것이 좋습니다. 업그레이드 프로세스를 시작하려면 현재 버전의 Visual Studio에서 솔루션을 엽니다. 업그레이드 프롬프트가 표시되면 제공된 정보를 검토하고 **확인** 을 선택하여 업그레이드를 시작합니다. 솔루션에 두 개 이상의 프로젝트가 있는 경우 이를 업데이트해야 합니다. 마법사에서 기존 .vcproj 파일과 함께 새 .vcxproj 프로젝트 파일을 단계별로 만듭니다. 원래 .sln 파일의 복사본이 있는 경우 업그레이드가 Visual Studio 2008 프로젝트에 다른 영향을 미치지 않습니다.

> [!NOTE]
> 다음 단계는 다중 대상 지정 시나리오에만 적용 됩니다. 프로젝트를 최신 도구 집합으로 영구적으로 업그레이드 하려는 경우 다음 단계는 프로젝트를 저장 하 고 Visual Studio 2019에서 연 다음 표시 되는 빌드 문제를 해결 하는 것입니다.

업그레이드가 완료될 때 로그 보고서에 프로젝트에 대한 오류 또는 경고가 있으면 이를 주의해서 검토합니다. **VCBuild** 에서 **MSBuild** 로 변환하면 문제가 발생할 수 있습니다. 보고서에 나열된 작업 항목을 이해하고 구현해야 합니다. **VCBuild** 에서 **MSBuild** 로 변환할 때 발생할 수 있는 업그레이드 로그 보고서 및 문제에 대한 자세한 내용은 이 [C++ 네이티브 멀티 타기팅](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/) 블로그 게시물을 참조하세요.

프로젝트 업그레이드가 완료되고 로그 파일에서 문제를 수정한 경우 솔루션은 실제로 최신 도구 집합을 대상으로 지정합니다. 마지막 단계로 Visual Studio 2008 도구 집합을 사용하도록 솔루션에서 각 프로젝트에 대한 속성을 변경합니다. 솔루션이 현재 버전의 Visual Studio에 로드된 경우 솔루션의 각 프로젝트에 대해 프로젝트 **속성 페이지** 대화 상자를 엽니다. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다. **속성 페이지** 대화 상자에서 **구성** 드롭다운 값을 **모든 구성** 으로 변경합니다. **구성 속성** 에서 **일반** 을 선택하고 **플랫폼 도구 집합** 을 **Visual Studio 2008(v90)** 로 변경합니다.

이와 같이 변경한 후 Visual Studio 2008 컴파일러 및 라이브러리는 현재 버전의 Visual Studio에서 솔루션을 빌드할 때 프로젝트 이진 파일을 생성하는 데 사용됩니다.

## <a name="install-an-older-visual-studio-toolset"></a>이전 Visual Studio 도구 집합 설치

업그레이드할 수 없거나 업그레이드하지 않으려는 이전 Visual Studio C++ 프로젝트가 있지만 프로젝트와 일치하는 플랫폼 도구 집합 버전이 없을 수 있습니다. 이 경우 도구 집합을 얻으려면 필요한 버전의 무료 Visual Studio Community 또는 Express 버전을 설치합니다. Visual Studio 2008부터 Visual Studio의 모든 버전은 현재 Visual Studio에서 해당 버전을 대상으로 지정하는 데 필요한 컴파일러, 도구 및 라이브러리를 설치할 수 있습니다. Microsoft 다운로드 센터를 검색하여 특정 버전의 Visual Studio를 찾고 다운로드합니다. 설치하는 동안 C++ 설치 옵션을 선택해야 합니다. 설치가 완료되면 업데이트를 설치할 Visual Studio의 해당 버전을 실행합니다. 또한 필요한 Windows 업데이트 변경 내용이 있는지 확인합니다. 모든 업데이트를 받기 위해 이 업데이트 확인 프로세스를 두 번 이상 반복해야 할 수 있습니다.

현재 사용 가능한 다운로드는 [이전 버전의 Visual Studio 소프트웨어 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/)를 참조하세요.

이러한 제품이 설치되면 **속성 페이지** 대화 상자의 **플랫폼 도구 집합** 속성 드롭다운이 사용 가능한 도구 집합을 표시하도록 자동으로 업데이트됩니다. 이제 최신 버전의 Visual Studio를 사용하여 이전 버전의 도구 집합을 위한 프로젝트를 변환하거나 업그레이드하지 않고 빌드할 수 있습니다.

## <a name="see-also"></a>참고 항목

[이전 버전의 Visual C++에서 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)
