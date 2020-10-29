---
title: 일반 속성 페이지(프로젝트)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: eaaa2c7428809c05532642b0f9ac53146c6f01a9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924286"
---
# <a name="general-property-page-project"></a>일반 속성 페이지(프로젝트)

::: moniker range=">=msvc-160"

이 항목은 Windows 용 Visual Studio 프로젝트에 적용 됩니다. Linux 프로젝트의 경우 [Linux c + + 속성 페이지 참조](../../linux/prop-pages-linux.md)를 참조 하세요. Cmake 프로젝트의 경우 [Visual Studio의 cmake 프로젝트](../cmake-projects-in-visual-studio.md)를 참조 하세요. Android 프로젝트의 경우 [일반 프로젝트 속성 (Android c + +)](../../cross-platform/general-android-prop-page.md)을 참조 하세요. Android 메이크파일 프로젝트의 경우 [일반 프로젝트 속성 (Android c + + 메이크파일)](../../cross-platform/general-makefile-android-prop-page.md) 을 참조 하세요.

솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하면 왼쪽 창의 **구성 속성** 노드 아래에 있는 **일반** 속성 페이지에 다음 속성이 표시 됩니다.

- **출력 디렉터리**

   링커 등의 도구가 빌드 프로세스 중에 생성되는 모든 최종 출력 파일을 배치하는 디렉터리를 지정합니다. 일반적으로 이 디렉터리에는 링커, 라이브러리 관리자 또는 BSCMake와 같은 도구의 출력이 포함됩니다. 기본적으로 이 속성은 매크로 $(SolutionDir)$(Configuration)\에서 지정한 디렉터리입니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>을 참조하세요.

- **중간 디렉터리**

   컴파일러 등의 도구가 빌드 프로세스 중에 생성되는 모든 중간 파일을 배치하는 디렉터리를 지정합니다. 일반적으로 이 디렉터리에는 C/C++ 컴파일러, MIDL 및 리소스 컴파일러와 같은 도구의 출력이 포함됩니다. 기본적으로 이 속성은 매크로 $(Configuration)\에서 지정한 디렉터리입니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>을 참조하세요.

- **대상 이름**

   이 프로젝트에서 생성하는 파일 이름을 지정합니다. 기본적으로 이 속성은 매크로 $(ProjectName)에서 지정한 파일 이름입니다.

- **구성 유형**

  선택할 수 있는 여러 구성 형식이 있습니다.

  - **애플리케이션(.exe)**

     링커 도구 집합(C/C++ 컴파일러, MIDL, 리소스 컴파일러, 링커, BSCMake, XML Web services 프록시 생성기, 사용자 지정 빌드, 사전 빌드, 사전 링크, 사후 빌드 이벤트)을 표시합니다.

  - **동적 라이브러리(.dll)**

     링커 도구 집합을 표시하고 /DLL 링커 옵션을 지정하고 CL에 _WINDLL define을 추가합니다.

  - **메이크파일**

     메이크파일 도구 집합(NMake)을 표시합니다.

  - **정적 라이브러리(.lib)**

     라이브러리 관리자 도구 집합(링커를 라이브러리 관리자로 대체하고 XML Web services 프록시 생성기를 생략하는 점을 제외하고 링커 도구 집합과 같음)을 표시합니다.

  - **유틸리티**

     유틸리티 도구 집합(MIDL, 사용자 지정 빌드, 사전 빌드, 사후 빌드 이벤트)을 표시합니다.

  프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>을 참조하세요.

- **Windows SDK 버전**

   Windows 대상 플랫폼의 경우 프로젝트에 필요한 Windows SDK의 버전을 지정합니다. Visual Studio 설치 관리자를 사용하여 C++ 워크로드를 설치할 경우 Windows SDK의 필수 부분도 설치됩니다. 컴퓨터에서 다른 Windows SDK 버전을 설치한 경우 설치된 각 버전의 SDK 도구가 드롭다운에 표시됩니다.

   Windows 7 또는 Windows Vista를 대상으로 하려면 해당 플랫폼에 대해 Windows SDK 8.1이 이전 버전과 호환되므로 **8.1** 값을 사용합니다. 또한 targetver.h에서 **_WIN32_WINNT** 에 대한 적절한 값을 정의해야 합니다. Windows 7의 경우 0x0601입니다. [WINVER 및 _WIN32_WINNT 수정](../../porting/modifying-winver-and-win32-winnt.md)을 참조하세요.

   Visual Studio에 포함된 Windows XP 플랫폼 도구 집합을 설치하여 Windows XP 및 Windows 2003 Server 프로젝트를 빌드하는 현재 버전의 라이브러리를 사용할 수 있습니다. 이 플랫폼 도구 집합을 다운로드하고 사용하는 방법에 대한 자세한 내용은 [Windows XP용 프로그램 구성](../configuring-programs-for-windows-xp.md)을 참조하세요. 플랫폼 도구 집합을 변경하는 방법에 대한 자세한 내용은 [방법: 대상 프레임워크 및 플랫폼 도구 집합 수정](../how-to-modify-the-target-framework-and-platform-toolset.md)을 참조하세요.

- **플랫폼 도구 집합**

   프로젝트가 다른 버전의 Visual C++ 라이브러리 및 컴파일러를 대상으로 할 수 있도록 허용합니다. Visual Studio c + + 프로젝트는 Visual Studio에 의해 설치 된 기본 도구 집합을 대상으로 하거나, Windows XP에서 실행 될 수 있는 실행 파일을 만드는 도구 집합을 포함 하 여 여러 이전 버전의 Visual Studio에서 설치 된 도구 집합 중 하나를 대상으로 플랫폼 도구 집합을 변경하는 방법에 대한 자세한 내용은 [방법: 대상 프레임워크 및 플랫폼 도구 집합 수정](../how-to-modify-the-target-framework-and-platform-toolset.md)을 참조하세요.

- **C++ 언어 표준**

   사용할 언어 표준을 지정 합니다. 기본값은/std: c + + 14입니다. C + + 17 기능을 사용 하려면/sd: c + + 17을 지정 하 고 c + + 20 또는 기타 실험적 기능을 사용 하려면/c + +를 지정 합니다. 자세한 내용은 [/std (언어 표준 버전 지정)](std-specify-language-standard-version.md) 를 참조 하세요.

::: moniker-end

::: moniker range="<=msvc-150"

Visual Studio 2015 및 Visual Studio 2017에서 **솔루션 탐색기** 의 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하면 왼쪽 창의 **구성 속성** 노드 아래에 있는 **일반** 속성 페이지에 속성의 두 섹션이 표시 됩니다.

- 일반

- 프로젝트 기본값

## <a name="general"></a>일반

- **대상 플랫폼**

   프로젝트를 실행할 플랫폼을 지정합니다. 예를 들어 Windows, Android 또는 iOS입니다. 값이 **Windows 10** 이면 프로젝트가 유니버설 Windows 플랫폼을 대상으로 합니다. 이전 버전의 Windows를 대상으로 하는 경우 버전이 표시되지 않고 이 필드의 값이 단순히 **Windows** 로 표시됩니다. 이 필드는 프로젝트를 만들 때 설정되는 읽기 전용 필드입니다.

- **대상 플랫폼 버전 (Visual Studio 2015)**

   프로젝트를 실행할 수 있는 가장 낮은 플랫폼 버전을 지정합니다. 이 속성은 프로젝트 형식에서 지 원하는 경우에만 표시 됩니다. 앱이 최신 Windows SDK 버전의 기능을 활용할 수 있지만 해당 기능이 없는 이전 버전에서도 일부 기능은 손실되지만 실행될 수 있는 경우 이러한 두 속성의 값이 다를 수 있습니다. 이 경우 코드에서 런타임에 실행 중인 플랫폼의 버전을 확인해야 하며, 이전 플랫폼 버전에서 사용할 수 없는 기능은 사용하지 않도록 해야 합니다.

   C + + 프로젝트 시스템은이 옵션을 적용 하지 않습니다. C# 및 JavaScript와 같은 다른 언어와의 일관성을 위해 및 프로젝트 사용자를 위한 지침으로 포함되었습니다. Visual C++는 최소 버전에서 사용할 수 없는 기능을 사용하는 경우 오류를 생성하지 않습니다.

- **Windows SDK 버전 (Visual Studio 2017)**

   Windows 대상 플랫폼의 경우 프로젝트에 필요한 Windows SDK의 버전을 지정합니다. Visual Studio 설치 관리자를 사용하여 C++ 워크로드를 설치할 경우 Windows SDK의 필수 부분도 설치됩니다. 컴퓨터에서 다른 Windows SDK 버전을 설치한 경우 설치된 각 버전의 SDK 도구가 드롭다운에 표시됩니다.

   Windows 7 또는 Windows Vista를 대상으로 하려면 해당 플랫폼에 대해 Windows SDK 8.1이 이전 버전과 호환되므로 **8.1** 값을 사용합니다. 또한 targetver.h에서 **_WIN32_WINNT** 에 대한 적절한 값을 정의해야 합니다. Windows 7의 경우 0x0601입니다. [WINVER 및 _WIN32_WINNT 수정](../../porting/modifying-winver-and-win32-winnt.md)을 참조하세요.

   Visual Studio에 포함된 Windows XP 플랫폼 도구 집합을 설치하여 Windows XP 및 Windows 2003 Server 프로젝트를 빌드하는 현재 버전의 라이브러리를 사용할 수 있습니다. 이 플랫폼 도구 집합을 다운로드하고 사용하는 방법에 대한 자세한 내용은 [Windows XP용 프로그램 구성](../configuring-programs-for-windows-xp.md)을 참조하세요. 플랫폼 도구 집합을 변경하는 방법에 대한 자세한 내용은 [방법: 대상 프레임워크 및 플랫폼 도구 집합 수정](../how-to-modify-the-target-framework-and-platform-toolset.md)을 참조하세요.

- **출력 디렉터리**

   링커 등의 도구가 빌드 프로세스 중에 생성되는 모든 최종 출력 파일을 배치하는 디렉터리를 지정합니다. 일반적으로 이 디렉터리에는 링커, 라이브러리 관리자 또는 BSCMake와 같은 도구의 출력이 포함됩니다. 기본적으로 이 속성은 매크로 $(SolutionDir)$(Configuration)\에서 지정한 디렉터리입니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>을 참조하세요.

- **중간 디렉터리**

   컴파일러 등의 도구가 빌드 프로세스 중에 생성되는 모든 중간 파일을 배치하는 디렉터리를 지정합니다. 일반적으로 이 디렉터리에는 C/C++ 컴파일러, MIDL 및 리소스 컴파일러와 같은 도구의 출력이 포함됩니다. 기본적으로 이 속성은 매크로 $(Configuration)\에서 지정한 디렉터리입니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>을 참조하세요.

- **대상 이름**

   이 프로젝트에서 생성하는 파일 이름을 지정합니다. 기본적으로 이 속성은 매크로 $(ProjectName)에서 지정한 파일 이름입니다.

- **대상 확장명**

   이 프로젝트에서 생성하는 파일 이름 확장명(예: .exe 또는 .dll)을 지정합니다.

- **정리할 때 삭제할 확장명**

   **정리** 옵션( **빌드** 메뉴)은 프로젝트 구성이 빌드되는 중간 디렉터리에서 파일을 삭제합니다. 이 속성을 통해 지정된 확장명을 가진 파일은 **정리** 를 실행하거나 다시 빌드를 수행할 경우 삭제됩니다. 중간 디렉터리에 있는 이러한 확장명의 파일뿐 아니라 빌드 시스템은 위치에 관계없이 알려진 빌드 출력(.obj 파일과 같은 중간 출력 포함)도 삭제합니다. 와일드카드 문자를 지정할 수 있습니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>을 참조하세요.

- **빌드 로그 파일**

   프로젝트를 빌드할 때마다 생성되는 로그 파일에 대해 기본값이 아닌 위치를 지정할 수 있습니다. 기본 위치는 매크로 $(IntDir)$(MSBuildProjectName).log에서 지정됩니다.

   프로젝트 매크로를 사용하여 디렉터리 위치를 변경할 수 있습니다. [빌드 명령 및 속성에 대 한 일반 매크로](common-macros-for-build-commands-and-properties.md)를 참조 하세요.

- **플랫폼 도구 집합**

   프로젝트가 다른 버전의 Visual C++ 라이브러리 및 컴파일러를 대상으로 할 수 있도록 허용합니다. Visual Studio c + + 프로젝트는 Visual Studio에 의해 설치 된 기본 도구 집합을 대상으로 하거나, Windows XP에서 실행 될 수 있는 실행 파일을 만드는 도구 집합을 포함 하 여 여러 이전 버전의 Visual Studio에서 설치 된 도구 집합 중 하나를 대상으로 플랫폼 도구 집합을 변경하는 방법에 대한 자세한 내용은 [방법: 대상 프레임워크 및 플랫폼 도구 집합 수정](../how-to-modify-the-target-framework-and-platform-toolset.md)을 참조하세요.

- **관리 증분 빌드 사용**

   관리 프로젝트의 경우 이를 통해 어셈블리를 생성할 때 외부 표시 유형을 검색할 수 있습니다. 관리 프로젝트에 대한 변경 내용이 다른 프로젝트에 표시되지 않는 경우 종속 프로젝트가 다시 빌드되지 않습니다. 그러면 관리 프로젝트를 포함하는 솔루션에서 빌드 시간을 크게 개선할 수 있습니다.

## <a name="project-defaults"></a>프로젝트 기본값

프로젝트 기본값 섹션의 속성은 수정할 수 있는 기본 속성을 나타냅니다. 이러한 속성에 대한 정의는 *설치 디렉터리* \VC\VCProjectDefaults의 .props 파일에서 확인할 수 있습니다.

- **구성 유형**

  선택할 수 있는 여러 구성 형식이 있습니다.

  - **애플리케이션(.exe)**

     링커 도구 집합(C/C++ 컴파일러, MIDL, 리소스 컴파일러, 링커, BSCMake, XML Web services 프록시 생성기, 사용자 지정 빌드, 사전 빌드, 사전 링크, 사후 빌드 이벤트)을 표시합니다.

  - **동적 라이브러리(.dll)**

     링커 도구 집합을 표시하고 /DLL 링커 옵션을 지정하고 CL에 _WINDLL define을 추가합니다.

  - **메이크파일**

     메이크파일 도구 집합(NMake)을 표시합니다.

  - **정적 라이브러리(.lib)**

     라이브러리 관리자 도구 집합(링커를 라이브러리 관리자로 대체하고 XML Web services 프록시 생성기를 생략하는 점을 제외하고 링커 도구 집합과 같음)을 표시합니다.

  - **유틸리티**

     유틸리티 도구 집합(MIDL, 사용자 지정 빌드, 사전 빌드, 사후 빌드 이벤트)을 표시합니다.

  프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>을 참조하세요.

- **MFC 사용**

   MFC 프로젝트가 MFC DLL에 정적 또는 동적으로 연결하는지를 지정합니다. 비 MFC 프로젝트는 **표준 Windows 라이브러리 사용** 을 선택하여 MFC를 사용할 때 포함되는 다양한 Win32 라이브러리에 연결할 수 있습니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>을 참조하세요.

- **문자 집합**

   _UNICODE 또는 _MBCS를 설정해야 하는지를 정의합니다. 해당하는 경우 링커 진입점에도 영향을 줍니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>을 참조하세요.

- **공용 언어 런타임 지원**

   [/clr](clr-common-language-runtime-compilation.md) 컴파일러 옵션을 사용하게 합니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>을 참조하세요.

- **.NET 대상 프레임워크 버전**

   관리 프로젝트에서 대상으로 지정할 .NET Framework 버전을 지정합니다.

- **전체 프로그램 최적화**

   [/GL](gl-whole-program-optimization.md) 컴파일러 옵션 및 [/LTCG](ltcg-link-time-code-generation.md) 링커 옵션을 지정합니다. 기본적으로 디버그 구성에 대해 비활성화되고 소매 구성에 대해 활성화됩니다.

- **Windows Store 앱 지원**

   이 프로젝트가 Windows 런타임(유니버설 Windows 플랫폼) 앱을 지원하는지 여부를 지정합니다. 자세한 내용은 [/ZW(Windows 런타임 컴파일)](zw-windows-runtime-compilation.md) 및 Windows 개발자 센터를 참조하세요.

::: moniker-end

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)
