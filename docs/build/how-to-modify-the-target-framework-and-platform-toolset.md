---
description: '자세한 정보: 방법: 대상 프레임워크 및 플랫폼 도구 집합 수정'
title: '방법: 대상 프레임워크 및 플랫폼 도구 집합 수정'
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 8b3de299652efcdd8fd94622b890b6cec7b059e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156257"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>방법: 대상 프레임워크 및 플랫폼 도구 집합 수정

Visual Studio C++ 프로젝트 파일을 편집하여 C++ 플랫폼 도구 집합, Windows SDK 및 .NET Framework의 다른 버전을 대상으로 지정할 수 있습니다(C++/CLI 프로젝트에만 해당). 기본적으로 프로젝트 시스템에는 프로젝트를 만드는 데 사용하는 Visual Studio 버전에 해당하는 .NET Framework 버전 및 도구 집합 버전이 사용됩니다. .vcxproj 파일에서 관련 모든 값을 수정하여 모든 컴파일 대상에 동일한 코드베이스를 사용할 수 있습니다.

## <a name="platform-toolset"></a>플랫폼 도구 집합

플랫폼 도구 집합은 C/C++ 표준 라이브러리와 함께 C++ 컴파일러(cl.exe) 및 링커(link.exe)로 구성됩니다. Visual Studio 2015부터 도구 집합의 주 버전은 14로 유지됩니다. 즉, Visual studio 2019 또는 Visual Studio 2017로 컴파일된 프로젝트는 Visual Studio 2015로 컴파일된 프로젝트와 ABI 이전 버전과 호환됩니다. 부 버전은 Visual Studio 2015 이후 버전마다 1씩 업데이트되었습니다.

- Visual Studio 2015: v140
- Visual Studio 2017: v141
- Visual Studio 2019: v142

관련 도구 집합은 .NET Framework 4.5 이상 버전을 지원합니다.

Visual Studio는 C++ 프로젝트의 다중 대상 지정도 지원합니다. 이전 버전의 Visual Studio로 만든 프로젝트를 Visual Studio IDE를 사용하여 편집하고 빌드하면 업그레이드하지 않고도 새 버전의 도구 집합을 사용할 수 있습니다. 이전 도구 집합이 컴퓨터에 설치되어 있어야 합니다. 자세한 내용은 [Visual Studio에서 네이티브 멀티 타기팅을 사용하는 방법](../porting/use-native-multi-targeting.md)을 참조하세요. 예를 들어 Visual Studio 2015에서 .NET Framework 2.0을 ‘대상’으로 지정할 수 있지만 이를 지원하는 이전 도구 집합을 사용해야 합니다. 

## <a name="target-framework-ccli-project-only"></a>대상 프레임워크(C++/CLI 프로젝트에만 해당)

대상 프레임워크를 변경하는 경우 플랫폼 도구 집합도 해당 프레임워크를 지원하는 버전으로 변경합니다. 예를 들어 .NET Framework 4.5를 대상으로 하려면 Visual Studio 2015(v140), Visual Studio 2013(v120) 또는 Visual Studio 2012(v110)와 같은 호환되는 플랫폼 도구 집합을 사용해야 합니다. .NET Framework 2.0, 3.0, 3.5, 4 및 x86/x64 플랫폼을 대상으로 하는 [Windows 7.1 SDK](https://www.microsoft.com/download/details.aspx?id=8279) 플랫폼 도구 집합을 사용할 수 있습니다.

사용자 지정 플랫폼 도구 집합을 만들어 대상 플랫폼을 추가로 확장할 수 있습니다. 자세한 내용은 Visual C++ 블로그의 [C++ Native Multi-Targeting](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/) 을 참조하세요.

### <a name="to-change-the-target-framework"></a>대상 프레임워크를 변경하려면

1. Visual Studio의 **솔루션 탐색기** 에서 프로젝트를 선택합니다. 메뉴 모음에서 **프로젝트** 메뉴를 열고 **프로젝트 언로드** 를 선택합니다. 프로젝트에 대한 프로젝트 파일(.vcxproj)을 언로드합니다.

   > [!NOTE]
   >  Visual Studio에서 프로젝트 파일을 수정하는 동안에는 C++ 프로젝트를 로드할 수 없습니다. 그러나 메모장 등의 다른 편집기를 사용하면 Visual Studio에서 프로젝트가 로드되는 동안 프로젝트 파일을 수정할 수 있습니다. Visual Studio가 프로젝트 파일이 변경된 것을 감지하고 프로젝트를 다시 로드하라고 요청합니다.

1. 메뉴 모음에서 **파일**, **열기**, **파일** 을 차례로 선택합니다. **파일 열기** 대화 상자에서 해당 프로젝트 폴더를 탐색하고 프로젝트(.vcxproj) 파일을 엽니다.

1. 프로젝트 파일에서 대상 Framework 버전에 대한 항목을 찾습니다. 예를 들어, 프로젝트가 .NET Framework 4.5를 사용하도록 디자인된 경우 `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` 의 `<PropertyGroup Label="Globals">` 요소에서 `<Project>` 을 찾습니다. `<TargetFrameworkVersion>` 요소가 없는 경우 프로젝트에 .NET Framework가 사용되지 않으므로 변경할 필요가 없습니다.

1. 값을 v3.5 또는 v4.6과 같은 원하는 프레임워크 버전으로 변경합니다.

1. 변경 내용을 저장하고 편집기를 닫습니다.

1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **프로젝트 다시 로드** 를 선택합니다.

1. 변경 내용을 확인하려면 **솔루션 탐색기** 에서 마우스 오른쪽 단추를 클릭하여 솔루션이 아닌 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택하여 프로젝트 **속성 페이지** 대화 상자를 엽니다. 대화 상자의 왼쪽 창에서 **구성 속성** 을 확장하고 **일반** 을 선택합니다. **.NET 대상 프레임워크 버전** 에 새 프레임워크 버전이 표시되는지 확인합니다.

### <a name="to-change-the-platform-toolset"></a>플랫폼 도구 집합을 변경하려면

1. Visual Studio의 **솔루션 탐색기** 에서 솔루션이 아닌 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택하여 프로젝트 **속성 페이지** 대화 상자를 선택합니다.

1. **속성 페이지** 대화 상자에서 **구성** 드롭다운 목록을 열고 **모든 구성** 을 선택합니다.

1. 대화 상자의 왼쪽 창에서 **구성 속성** 을 확장하고 **일반** 을 선택합니다.

1. 오른쪽 창에서 **플랫폼 도구 집합** 을 선택하고 드롭다운 목록에서 원하는 도구 집합을 선택합니다. 예를 들어 Visual Studio 2010 도구 집합을 설치한 경우 프로젝트에 사용하도록 **Visual Studio 2010 (v100)** 을 선택합니다.

1. **확인** 단추를 선택합니다.

## <a name="see-also"></a>참조

[명령줄의 MSBuild - C++](msbuild-visual-cpp.md)
