---
title: Visual Studio에서 속성을 빌드하고 C++ 컴파일러를 설정 합니다.
description: C++ 컴파일러 및 링커 옵션과 기타 빌드 설정을 변경 하려면 Visual Studio IDE를 사용 합니다.
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 6c05dd00324113819dd145e46bf10dfeb96a66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078232"
---
# <a name="set-compiler-and-build-properties"></a>컴파일러 및 빌드 속성 설정

IDE에서 프로젝트를 빌드하는 데 필요한 모든 정보는 *속성*으로 공개됩니다. 이 정보에는 애플리케이션 이름, 확장명(예: DLL, LIB, EXE), 컴파일러 옵션, 링커 옵션, 디버거 설정, 사용자 지정 빌드 단계 및 다른 많은 항목이 포함됩니다. 일반적으로 *속성 페이지* 를 사용 하 여 이러한 속성을 보고 수정 합니다. 속성 페이지에 액세스 하려면 주 메뉴에서 **project** >  **_projectname_ 속성** 을 선택 하거나 **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

## <a name="default-properties"></a>기본 속성

프로젝트를 만들 때 시스템은 다양한 속성에 대해 값을 지정합니다. 기본값은 프로젝트의 종류 및 앱 마법사에서 선택한 옵션에 따라 다소 다릅니다. 예를 들어 ATL 프로젝트에는 MIDL 파일과 관련된 속성이 있지만 이 파일들은 기본 콘솔 애플리케이션에는 없습니다. 기본 속성은 속성 페이지의 일반 창에 표시됩니다.

![Visual C&#43; &#43; 프로젝트 기본값](media/visual-c---project-defaults.png "Visual C++ 프로젝트 기본값")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>빌드 구성 및 대상 플랫폼에 속성 적용

애플리케이션 이름 같은 일부 속성은 대상 플랫폼 또는 디버그나 릴리스 빌드인지 여부에 관계 없이 모든 빌드 변형에 적용됩니다. 하지만 대부분의 속성은 구성에 종속적입니다. 이는 프로그램이 실행되는 특정 플랫폼 및 올바른 코드를 생성하기 위해 사용하는 특정 컴파일러 옵션을 컴파일러가 알아야 하기 때문입니다. 따라서 속성을 설정하는 경우 새 값이 적용되어야 할 구성 및 플랫폼에 반드시 주의해야 합니다. 디버그 Win32 빌드에만 적용해야 합니까 또는 디버그 ARM 및 디버그 x64에도 적용해야 합니까? 예를 들어 기본적으로 **최적화** 속성은 릴리스 구성에서 **속도 최대화(/O2)** 로 설정되지만 디버그 구성에는 사용할 수 없습니다.

속성 페이지는 수정이 필요한 경우 속성 값을 어떤 구성 및 플랫폼에 적용해야 하는지 항상 확인할 수 있도록 설계됩니다. 다음 그림에서는 맨 위의 목록 상자에서 구성 및 플랫폼 정보가 포함된 속성 페이지를 보여줍니다. **최적화** 속성은 여기에 설정된 경우 빨간색 화살표로 표시된 것처럼 활성 구성이 될 수 있는 디버그 Win32 빌드에만 적용됩니다.

![활성 구성을&#43; &#43; 표시 하는 Visual C 속성 페이지](media/visual-c---property-pages-showing-active-configuration.png "활성 C++ 구성을 보여 주는 시각적 속성 페이지")

다음 그림에서는 같은 프로젝트 속성 페이지를 보여주지만 구성은 릴리스로 변경되었습니다. 최적화 속성에 대해 다른 값입니다. 또한 활성 구성이 여전히 디버그입니다. 모든 구성에 대한 속성을 설정할 수 있으며, 활성 구성일 필요는 없습니다.

![릴리스 구성을&#43; &#43; 표시 하는 Visual C 속성 페이지](media/visual-c---property-pages-showing-release-config.png "릴리스 C++ 구성을 보여 주는 시각적 속성 페이지")

## <a name="target-platforms"></a>대상 플랫폼

*대상 플랫폼*은 실행 파일이 실행될 디바이스 및/또는 운영 체제의 종류를 참조합니다. 1 초과 플랫폼에 대해 프로젝트를 빌드할 수 있습니다. C++ 프로젝트에 대한 사용 가능한 대상 플랫폼은 프로젝트의 종류에 따라 다르며, Win32, x64, ARM, Android 및 iOS를 포함하지만 이에 국한되지 않습니다.     **Configuration Manager**에서 확인할 수 있는 **x86** 대상 플랫폼은 네이티브 C++ 프로젝트의 **Win32**와 동일합니다. Win32는 32비트 Windows를 의미하고 **x64**는 64비트 Windows를 의미합니다. 이 두 플랫폼에 대한 자세한 내용은 [실행 중인 32비트 애플리케이션](/windows/win32/WinProg64/running-32-bit-applications)을 참조합니다.

**Configuration Manager**에서 확인할 수 있는 **모든 CPU** 대상 플랫폼 값은 네이티브 C++ 프로젝트에 영향을 주지 않으며, C++/CLI 및 다른 .NET 프로젝트 형식에 대해 관련이 있습니다. 자세한 내용은 [/CLRIMAGETYPE(CLR 이미지 형식 지정)](reference/clrimagetype-specify-type-of-clr-image.md)을 참조하세요.

디버그 빌드에 대 한 속성을 설정 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- [C++ 디버그 구성에 대한 프로젝트 설정](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [디버거 설정 및 준비](/visualstudio/debugger/debugger-settings-and-preparation)
- [디버깅 준비: Visual C++ 프로젝트 형식](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Visual Studio 디버거에서 기호 파일(.pdb) 및 원본 파일 지정](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>C++ 컴파일러 및 링커 옵션

C++컴파일러 및 링커 옵션은 왼쪽 창의 **구성 속성**아래에 있는 **C/C++**  및 **링커** 노드 아래에 있습니다. 이는 컴파일러에 전달 되는 명령줄 옵션으로 직접 변환 됩니다. 특정 옵션에 대 한 설명서를 읽으려면 가운데 창에서 옵션을 선택 하 고 **f1**키를 누릅니다. 또는 [MSVC 컴파일러 옵션](reference/compiler-options.md) 및 [MSVC 링커 옵션](reference/linker-options.md)에서 모든 옵션에 대 한 설명서를 찾아볼 수 있습니다.

**속성 페이지** 대화 상자에는 현재 프로젝트와 관련 된 속성 페이지만 표시 됩니다. 예를 들어, 프로젝트에 .idl 파일이 없는 경우 MIDL 속성 페이지가 표시되지 않습니다. 각 속성 페이지의 설정에 대 한 자세한 내용은 [속성 페이지 (C++)](reference/property-pages-visual-cpp.md)를 참조 하세요.

## <a name="directory-and-path-values"></a>디렉터리 및 경로 값

MSBuild는 특정 문자열 값에 대해 "macros" 라는 컴파일 타임 상수를 사용할 수 있도록 지원 합니다. 디렉터리 및 경로입니다. 이러한 속성은 속성 [편집기](#property_editor)를 사용 하 여 참조 하 고 수정할 수 있는 속성 페이지에 표시 됩니다.

다음 그림에서는 Visual Studio C++ 프로젝트에 대 한 속성 페이지를 보여 줍니다. 왼쪽 창에서 **VC + + 디렉터리** *규칙* 을 선택 하 고 오른쪽 창에 해당 규칙과 연결 된 속성이 나열 됩니다. `$(...)` 값을 *매크로*라고 합니다. *매크로*는 Visual Studio 또는 MSBuild 시스템에서 정의한 값 또는 사용자 정의 값을 참조할 수 있는 컴파일 시간 상수입니다. 디렉터리 경로와 같이 하드 코드 된 값 대신 매크로를 사용 하 여 컴퓨터 간 속성 설정과 Visual Studio 버전 간의 속성 설정을 좀 더 쉽게 공유할 수 있으며, 프로젝트 설정이 [속성 상속](project-property-inheritance.md)에 올바르게 참여 하는지 확인할 수 있습니다.

![프로젝트 속성 페이지](media/project_property_pages_vc.png "Project_Property_Pages_VC")

모든 사용 가능한 매크로의 값을 보려면 속성 편집기를 사용할 수 있습니다.

### <a name="predefined-macros"></a>미리 정의된 매크로

*글로벌 매크로*<br/>
프로젝트 구성의 모든 항목에 적용됩니다. `$(name)` 구문이 있습니다. 전역 매크로의 예제는 `$(VCInstallDir)`이며, Visual Studio 설치의 루트 디렉터리에 저장됩니다. 전역 매크로는 MSBuild의 `PropertyGroup`에 해당합니다.

*항목 매크로*<br/>
`%(name)` 구문이 있습니다. 파일에 대한 항목 매크로는 해당 파일에만 적용됩니다. 예를 들어, `%(AdditionalIncludeDirectories)`를 사용하여 특정 파일에만 적용되는 포함 디렉터리를 지정하고 포함할 수 있습니다. 이러한 종류의 항목 매크로는 MSBuild의 `ItemGroup` 메타데이터에 해당합니다. 프로젝트 구성의 컨텍스트에서 사용되면 항목 매크로는 특정 형식의 모든 파일에 적용됩니다. 예를 들어 C/C++ **전처리기 정의** 구성 속성은 프로젝트의 모든 .cpp 파일에 적용되는 `%(PreprocessorDefinitions)` 항목 매크로를 사용할 수 있습니다. 이러한 종류의 항목 매크로는 MSBuild의 `ItemDefinitionGroup` 메타데이터에 해당합니다. 자세한 내용은 [항목 정의](/visualstudio/msbuild/item-definitions)를 참조하세요.

### <a name="user-defined-macros"></a>사용자 정의 매크로

*사용자 정의 매크로*를 만들어 프로젝트 빌드에서 변수로 사용할 수 있습니다. 예를 들어, 사용자 지정 빌드 단계 또는 사용자 지정 빌드 도구에 가치를 제공하는 사용자 정의 매크로를 만들 수 있습니다. 사용자 정의 매크로는 이름/값 쌍입니다. 프로젝트 파일에서 **$(** <em>name</em> **)** 표기법을 사용하여 값에 액세스합니다.

사용자 정의 매크로는 속성 시트에 저장됩니다. 프로젝트에 속성 시트가 아직 포함 되어 있지 않은 경우 [Visual Studio 프로젝트 설정 공유 또는 다시 사용](create-reusable-property-configurations.md)의 단계를 수행 하 여 프로젝트를 만들 수 있습니다.

#### <a name="to-create-a-user-defined-macro"></a>사용자 정의 매크로를 만들려면

1. **속성 관리자** 창을 엽니다. 메뉴 모음에서 **보기** > **속성 관리자** 를 선택 하거나 **다른 Windows** > **속성 관리자** > **확인** 합니다. 속성 시트에 대 한 바로 가기 메뉴를 열고 (이름이 사용자로 끝남) **속성**을 선택 합니다. 해당 속성 시트의 **속성 페이지** 대화 상자가 열립니다.

1. 대화 상자의 왼쪽 창에서 **사용자 매크로**를 선택합니다. 오른쪽 창에서 **매크로 추가** 단추를 선택하여 **사용자 매크로 추가** 대화 상자를 엽니다.

1. 대화 상자에서 매크로에 대한 이름 및 값을 지정합니다. 또는 **이 매크로를 빌드 환경의 환경 변수로 설정** 확인란을 선택합니다.

## <a name=""></a><a name="property_editor">속성 편집기</a>

속성 편집기를 사용하여 특정 문자열 속성을 수정하고 값으로 매크로를 선택할 수 있습니다. 속성 편집기에 액세스하려면 속성 페이지에서 속성을 선택한 후 오른쪽에 있는 아래쪽 화살표 단추를 선택합니다. 드롭다운 목록에 **\<편집>** 이 포함된 경우 이를 선택하여 해당 속성에 대한 속성 편집기를 표시할 수 있습니다.

![속성&#95;편집기&#95;드롭다운](media/property_editor_dropdown.png "Property_Editor_Dropdown")

속성 편집기에서 **매크로** 단추를 선택하여 사용 가능한 매크로와 해당 현재 값을 볼 수 있습니다. 다음 그림에서는 **매크로** 단추 선택 후 **추가 포함 디렉터리** 속성에 대한 속성 편집기를 보여 줍니다. **부모 또는 프로젝트 기본값에서 상속** 확인란이 선택되어 있고 새 값을 추가하면 현재 상속되는 모든 값에 새 값이 추가됩니다. 확인란의 선택을 취소하면 새 값이 상속된 값을 대체합니다. 대부분의 경우 확인란을 선택한 상태로 둡니다.

![속성 편집기, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>기본 디렉터리 집합에 포함 디렉터리 추가

포함 디렉터리를 프로젝트에 추가할 때 모든 기본 디렉터리를 재정의하지 않는 것이 중요합니다. 디렉터리를 추가하는 올바른 방법은 예를 들어, "C:\MyNewIncludeDir\\"과 같이 새 경로를 추가한 다음 속성 값에 **$(IncludePath)** 매크로를 추가하는 것입니다.

## <a name="quickly-browse-and-search-all-properties"></a>모든 속성을 빠르게 찾아서 검색

**모든 옵션** 속성 페이지(**속성 페이지** 대화 상자의 **구성 속성 &#124; C/C++** 노드 아래)를 사용하면 현재 컨텍스트에서 사용할 수 있는 속성을 신속하게 찾고 검색할 수 있습니다. 이 페이지에는 특수 검색 상자 및 결과를 필터링할 수 있는 간단한 구문이 있습니다.

접두사 없음:<br/>
속성 이름에서만 검색합니다(부분 문자열 대/소문자 구분 안 함).

'/' 또는 '-':<br/>
컴파일러 스위치에서만 검색합니다(접두사 대/소문자 구분 안 함).

v:<br/>
값에서만 검색합니다(부분 문자열 대/소문자 구분 안 함).

## <a name="set-environment-variables-for-a-build"></a>빌드에 대 한 환경 변수 설정

MSVC 컴파일러 (cl.exe)는 특정 환경 변수, 특히 LIB, LIBPATH, PATH 및 INCLUDE를 인식 합니다. IDE로 빌드하면 [VC++ Directories Property Page](reference/vcpp-directories-property-page.md) 속성 페이지에 설정된 속성이 환경 변수를 설정하는 데 사용됩니다. 개발자 명령 프롬프트가 LIB, LIBPATH 및 INCLUDE 값을 설정하는 경우 해당 값을 MSBuild 속성 값으로 대체합니다. 그러면 빌드에서 VC++ 디렉터리 실행 가능 디렉터리 속성 값을 PATH에 추가합니다. 사용자 정의 매크로를 생성한 다음 **이 매크로를 빌드 환경의 환경 변수로 설정**상자를 선택하여 사용자 정의 환경 변수를 설정할 수 있습니다.

## <a name="set-environment-variables-for-a-debugging-session"></a>디버깅 세션에 대 한 환경 변수 설정

프로젝트의 **속성 페이지** 대화 상자의 왼쪽 창에서 **구성 속성** 을 확장하고 **디버깅**을 선택합니다.

오른쪽 창에서 **환경** 또는 **환경 병합** 프로젝트 설정을 수정한 다음, **확인** 단추를 선택합니다.

## <a name="in-this-section"></a>섹션 내용

[Visual Studio 프로젝트 설정 공유 또는 재사용](create-reusable-property-configurations.md)<br/>
공유 하거나 다시 사용할 수 있는 사용자 지정 빌드 설정을 사용 하 여 props 파일을 만드는 방법

[프로젝트 속성 상속](project-property-inheritance.md)<br/>
빌드 프로세스의 props, .targets, .vcxproj 파일 및 환경 변수에 대 한 계산 순서를 설명 합니다.

[프로젝트 파일을 변경하지 않고 속성 및 대상 수정](modify-project-properties-without-changing-project-file.md)<br/>
프로젝트 파일을 수정 하지 않고 임시 빌드 설정을 만드는 방법

## <a name="see-also"></a>참고 항목

[Visual Studio 프로젝트 - C++](creating-and-managing-visual-cpp-projects.md)<br/>
[.vcxproj 및 .props 파일 구조](reference/vcxproj-file-structure.md)<br/>
[속성 페이지 XML 파일](reference/property-page-xml-files.md)<br/>
