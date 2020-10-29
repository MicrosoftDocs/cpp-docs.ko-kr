---
title: 고급 속성 페이지 (프로젝트)
ms.date: 08/10/2020
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 3b1e45f984cd40d6ea42ead25b045fc8688ad0a7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924043"
---
# <a name="advanced-property-page"></a>고급 속성 페이지

::: moniker range="<=msvc-150"

고급 속성 페이지는 Visual Studio 2019 이상에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end

::: moniker range="msvc-160"

고급 속성 페이지는 Visual Studio 2019 이상에서 사용할 수 있습니다.

## <a name="advanced-properties"></a>고급 속성

- **대상 파일 확장명**

   빌드 출력에 사용할 파일 확장명을 지정 합니다. *`.exe`* 응용 프로그램, *`.lib`* 정적 라이브러리 및 dll의 경우 기본적으로로 설정 *`.dll`* 됩니다.

- **정리할 때 삭제할 확장명**

   **정리** 옵션( **빌드** 메뉴)은 프로젝트 구성이 빌드되는 중간 디렉터리에서 파일을 삭제합니다. 이 속성에 지정 된 확장명을 가진 파일은 **정리가** 실행 되거나 다시 작성 될 때 삭제 됩니다. 빌드 시스템은 중간 디렉터리에 이러한 확장명이 있는 모든 파일을 삭제 합니다. 또한 위치에 관계 없이 모든 알려진 빌드 출력을 삭제 합니다. (파일 등의 중간 출력을 포함 하는 *`.obj`* ) 이 속성에서 와일드 카드 문자를 지정할 수 있습니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>을 참조하세요.

- **빌드 로그 파일**

   프로젝트를 빌드할 때마다 생성 되는 로그 파일에 대해 기본 위치가 아닌 위치를 지정할 수 있습니다. 기본 위치는 매크로로 지정 됩니다 `$(IntDir)$(MSBuildProjectName).log` .

   프로젝트 매크로를 사용하여 디렉터리 위치를 변경할 수 있습니다. [빌드 명령 및 속성에 대 한 일반 매크로](common-macros-for-build-commands-and-properties.md)를 참조 하세요.

- **기본 설정 빌드 도구 아키텍처**

   X86 또는 x64 빌드 도구를 사용할지 여부를 지정 합니다.

- **디버그 라이브러리 사용**

   디버그 또는 릴리스 빌드를 만들지 여부를 지정 합니다.

- **Unity (점보) 빌드 사용**

   컴파일 전에 많은 c + + 소스 파일을 하나 이상의 파일로 결합 하는 더 빠른 빌드 프로세스를 사용 하도록 설정 합니다. 이러한 결합 된 파일을 *unity* 파일 이라고 합니다. Unity 게임 엔진과는 관련이 없습니다.

- **OutDir에 콘텐츠 복사**

   프로젝트의 *콘텐츠로* 표시 된 항목을 프로젝트의 출력 디렉터리 ()에 복사 `$(OutDir)` 합니다. 이 설정은 배포를 간소화할 수 있습니다. 이 속성은 Visual Studio 2019 버전 16.7부터 사용할 수 있습니다.

- **OutDir에 프로젝트 참조 복사**

   실행 파일 (DLL 및 EXE 파일) 프로젝트 참조 항목을 프로젝트의 출력 디렉터리 ()에 복사 `$(OutDir)` 합니다. C + +/CLI ( [`/clr`](clr-common-language-runtime-compilation.md) ) 프로젝트에서이 속성은 무시 됩니다. 대신 각 프로젝트 참조의 **로컬 복사** 속성은 출력 디렉터리에 복사 되는지 여부를 제어 합니다. 이 설정은 로컬 배포를 간소화할 수 있습니다. Visual Studio 2019 버전 16.7부터 사용할 수 있습니다.

- **OutDir에 프로젝트 참조 기호 복사**

   프로젝트 참조 실행 파일과 함께 프로젝트 참조 항목에 대 한 PDB 파일을 프로젝트의 출력 디렉터리 ()에 복사 `$(OutDir)` 합니다. 이 속성은 c + +/CLI 프로젝트에 대해 항상 사용할 수 있습니다. 이 설정은 디버그 배포를 간소화할 수 있습니다. Visual Studio 2019 버전 16.7부터 사용할 수 있습니다.

- **C + + 런타임을 OutDir로 복사**

   런타임 Dll을 프로젝트의 출력 디렉터리 ()에 복사 `$(OutDir)` 합니다. 이 설정은 로컬 배포를 간소화할 수 있습니다. Visual Studio 2019 버전 16.7부터 사용할 수 있습니다.

- **MFC 사용**

   Mfc 프로젝트가 MFC DLL에 정적 또는 동적으로 연결 되는지 여부를 지정 합니다. 비 MFC 프로젝트에서 **표준 Windows 라이브러리를 사용** 하 여 mfc에 포함 된 Win32 라이브러리 연결을 선택 합니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>을 참조하세요.

- **문자 집합**

   또는를 설정 해야 하는지 여부를 정의 `_UNICODE` `_MBCS` 합니다. 해당하는 경우 링커 진입점에도 영향을 줍니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>을 참조하세요.

- **전체 프로그램 최적화**

   [`/GL`](gl-whole-program-optimization.md)컴파일러 옵션 및 링커 옵션을 지정 합니다 [`/LTCG`](ltcg-link-time-code-generation.md) . 기본적으로 디버그 구성에서는 전체 프로그램 최적화를 사용할 수 없으며 릴리스 구성에 사용할 수 있습니다.

- **MSVC 도구 집합 버전**

   프로젝트를 빌드하는 데 사용 되는 MSVC 도구 집합의 전체 버전을 지정 합니다. 도구 집합의 다양 한 업데이트 및 미리 보기 버전이 설치 되어 있을 수 있습니다. 여기에서 사용할 항목을 지정할 수 있습니다.

## <a name="ccli-properties"></a>C + +/CLI 속성

- **공용 언어 런타임 지원**

   [`/clr`](clr-common-language-runtime-compilation.md)컴파일러 옵션을 사용 합니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>을 참조하세요.

- **.NET 대상 프레임워크 버전**

   관리 프로젝트에서 대상으로 지정할 .NET Framework 버전을 지정합니다.

- **관리 증분 빌드 사용**

   관리 되는 프로젝트의 경우이 옵션을 사용 하면 어셈블리를 생성할 때 외부 표시 여부를 검색할 수 있습니다. 관리 되는 프로젝트에 대 한 변경 내용이 다른 프로젝트에 표시 되지 않으면 종속 프로젝트가 다시 빌드되지 않습니다. 관리 되는 증분 빌드는 관리 되는 프로젝트를 포함 하는 솔루션의 빌드 시간을 대폭 개선할 수 있습니다.

::: moniker-end
