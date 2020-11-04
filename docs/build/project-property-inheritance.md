---
title: Visual Studio 프로젝트의 속성 상속 - C++
description: 원시(MSBuild) Visual Studio C++ 프로젝트에서 속성 상속이 작동하는 방식입니다.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 17b23426f70bb2d306491e538d30cffc0f202362
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919217"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Visual Studio 프로젝트의 속성 상속

Visual Studio 원시 프로젝트 시스템은 MSBuild에 기반을 두고 있습니다. MSBuild는 모든 종류의 프로젝트를 빌드하기 위한 파일 형식 및 규칙을 정의합니다. 또한 여러 구성 및 플랫폼에 대한 빌드의 복잡성을 대부분 관리합니다. MSBuild의 작동 방식을 이해하면 도움이 될 것입니다. 이러한 이해는 사용자 지정 구성을 정의하려는 경우, 또는 여러 프로젝트로 공유하고 가져올 수 있는 재사용 가능한 속성 집합을 만들려는 경우 특히 중요합니다.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.Vcxproj 파일,.props 파일 및.targets 파일

::: moniker range="msvc-140"

프로젝트 속성은 여러 파일에 저장됩니다. 일부는 *`.vcxproj`* 프로젝트 파일에 직접 저장됩니다. 다른 일부는 프로젝트 파일이 가져오고 기본값을 제공하는 다른 *`.targets`* 파일이나 *`.props`* 파일에서 옵니다. 기본 디렉터리 아래의 로캘별 폴더에 Visual Studio 2015 프로젝트 파일 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\v140`* 이 있습니다.

::: moniker-end

::: moniker range="msvc-150"

프로젝트 속성은 여러 파일에 저장됩니다. 일부는 *`.vcxproj`* 프로젝트 파일에 직접 저장됩니다. 다른 일부는 프로젝트 파일이 가져오고 기본값을 제공하는 다른 *`.targets`* 파일이나 *`.props`* 파일에서 옵니다. 기본 디렉터리 아래의 로캘별 폴더에 Visual Studio 2017 프로젝트 파일 *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* 이 있습니다.

::: moniker-end

::: moniker range=">=msvc-160"

프로젝트 속성은 여러 파일에 저장됩니다. 일부는 *`.vcxproj`* 프로젝트 파일에 직접 저장됩니다. 다른 일부는 프로젝트 파일이 가져오고 기본값을 제공하는 다른 *`.targets`* 파일이나 *`.props`* 파일에서 옵니다. 기본 디렉터리 아래의 로캘별 폴더에 Visual Studio 프로젝트 파일 *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>`* 이 있습니다. `<version>`은 Visual Studio 버전에 해당됩니다. Visual Studio 2019의 경우 *`v160`* 입니다.

::: moniker-end

속성은 사용자 고유의 프로젝트에 추가할 수 있는 모든 사용자 지정 *`.props`* 파일에도 저장됩니다. 이러한 파일은 수동으로 편집하지 ‘않는’ 것이 가장 좋습니다. MSBuild 및 *`.vcxproj`* 파일에 대한 이해가 깊지 않은 경우 모든 속성, 특히 상속에 참여하는 속성을 수정하려면 대신에 IDE에서 속성 페이지를 사용하세요.

앞에 설명한 것처럼 다른 파일에서 다른 값이 동일한 구성에 대한 동일한 속성에 할당될 수 있습니다. 프로젝트를 빌드하면 MSBuild 엔진은 올바로 정의된 순서대로(이후 설명 참조) 프로젝트 파일 및 가져온 모든 파일을 평가합니다. 각 파일을 평가하기 때문에 해당 파일에서 정의된 모든 속성 값이 기존 값을 재정의합니다. 지정되지 않은 모든 값은 이전에 평가된 파일에서 상속됩니다. 속성 페이지를 사용하여 속성을 설정할 때 설정하는 위치에도 주의해야 합니다. *`.props`* 파일에서 속성을 "X"로 설정했으나 프로젝트 파일에서 속성이 "Y"로 설정되어 있는 경우 해당 프로젝트는 속성을 "Y"로 설정하여 빌드합니다. *`.cpp`* 파일처럼 프로젝트 항목에서 동일한 속성이 "Z"로 설정되어 있는 경우 MSBuild 엔진은 "Z" 값을 사용합니다.

다음은 기본 상속 트리입니다.

1. MSBuild CPP 도구 집합의 기본 설정(기본 디렉터리의 *`Microsoft.Cpp.Default.props`* 파일로, *`.vcxproj`* 파일이 가져옴)입니다.

1. 속성 시트

1. *`.vcxproj`* 파일. 이 파일은 기본 및 속성 시트 설정을 재정의할 수 있습니다.

1. 항목 메타데이터

> [!TIP]
> 속성 페이지에는 **굵게** 표시된 속성이 현재 컨텍스트에 정의됩니다. 일반 글꼴의 속성이 상속됩니다.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>가져온 모든 값으로 확장된 프로젝트 파일 보기

확장된 파일을 보고 지정된 속성 값의 상속 방법을 결정하는 것이 유용한 경우도 있습니다. 확장 버전을 보려면 Visual Studio 명령 프롬프트에서 다음 명령을 입력합니다. 자리 표시자 파일 이름을 사용할 이름으로 변경합니다.

> **msbuild /pp:** _temp_ **.txt** _myapp_ **.vcxproj**

확장된 프로젝트 파일은 클 수 있으며 MSBuild를 잘 알고 있지 않은 한 이해하기 어렵습니다. 프로젝트 파일의 기본 구조는 다음과 같음:

1. IDE에 노출되지 않는 기본 프로젝트 속성입니다.

1. 일부 기본 toolset-independent 속성을 정의하는 *`Microsoft.cpp.default.props`* 를 가져옵니다.

1. **구성 일반** 페이지에서 **PlatformToolset** 및 **프로젝트** 기본 속성으로 노출된 전역 구성 속성입니다. 이러한 속성은 다음 단계에서 어떤 도구 집합 및 내장 속성 시트를 *`Microsoft.cpp.props`* 로 가져올지 결정합니다.

1. 대부분의 프로젝트 기본값을 설정하는 *`Microsoft.cpp.props`* 를 가져옵니다.

1. *`.user`* 파일을 포함하여 모든 속성 시트를 가져옵니다. 등록 정보 시트는 **PlatformToolset** 및 **프로젝트** 기본 속성을 제외한 모든 항목을 재정의할 수 있습니다.

1. 나머지 프로젝트 구성 속성입니다. 이러한 값은 속성 시트에서 설정된 것을 재정의할 수 있습니다.

1. 메타데이터와 함께 있는 항목(파일)입니다. 이러한 항목은 다른 속성과 가져오기 앞에 있더라도 항상 MSBuild 평가 규칙의 마지막 단어입니다.

자세한 내용은 [MSBuild 속성](/visualstudio/msbuild/msbuild-properties)을 참조하세요.

## <a name="build-configurations"></a>빌드 구성

구성은 이름이 지정된 속성의 임의의 그룹입니다. Visual Studio는 디버그 및 릴리스 구성을 제공합니다. 각 구성은 디버그 빌드 또는 릴리스 빌드에 대해 다양한 속성을 적절히 설정합니다. **구성 관리자** 를 사용하여 사용자 지정 구성을 정의할 수 있습니다. 이를 통해 빌드의 특정 버전에 대한 속성을 편리하게 그룹화할 수 있습니다.

빌드 구성에 대해 더 잘 이해하려면 **속성 관리자** 를 엽니다. 설정에 따라 **보기 > 속성 관리자** 또는 **보기 > 다른 Windows > 속성 관리자** 를 선택하여 열 수 있습니다. **속성 관리자** 는 프로젝트에 각 구성 및 플랫폼 쌍에 대한 노드가 있습니다. 이러한 노드 각각에 해당 구성에 대한 일부 특정 속성을 설정하는 속성 시트( *`.props`* 파일)에 대한 노드가 있습니다.

![속성 관리자](media/property-manager.png "속성 관리자")

예를 들어 속성 페이지에서 일반 창으로 이동할 수 있습니다. 문자 집합 속성을 "유니코드 사용" 대신 "설정되지 않음"으로 변경한 다음, **확인** 을 클릭합니다. 이제 속성 관리자는 **유니코드 지원** 속성 시트를 표시하지 않습니다. 현재 구성에 대해서는 제거되지만 다른 구성에 대해서는 여전히 남아 있습니다.

속성 관리자 및 속성 시트에 대한 자세한 정보는 [Visual Studio C++ 프로젝트 설정 공유 또는 다시 사용](create-reusable-property-configurations.md)을 참조하세요.

> [!TIP]
> *`.user`* 파일은 레거시 기능입니다. 구성 및 플랫폼에 따라 속성을 올바르게 그룹화된 상태로 유지하기 위해 이 파일을 삭제하는 것이 좋습니다.
