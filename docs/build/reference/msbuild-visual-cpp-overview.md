---
title: Visual Studio에서 C++ 프로젝트용 MSBuild 내부
description: MSBuild에서 Visual Studio c + + 프로젝트에 사용 하는 지원 파일, 속성 및 대상입니다.
ms.date: 10/14/2020
helpviewer_keywords:
- MSBuild overview
ms.openlocfilehash: b08db751bfe04c7cd3ce2c2f4741c9ee8956cf74
ms.sourcegitcommit: 6e5429e076e552b32e8bdc49480c51498d7924c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099682"
---
# <a name="msbuild-internals-for-c-projects"></a>C++ 프로젝트용 MSBuild 내부

IDE에서 프로젝트 속성을 설정한 다음, 다음 프로젝트를 저장하는 경우 Visual Studio는 프로젝트 설정을 프로젝트 파일에 씁니다. 프로젝트 파일에는 프로젝트에 고유한 설정이 포함 되어 있습니다. 그러나 프로젝트를 빌드하는 데 필요한 모든 설정이 포함 되어 있지는 않습니다. 프로젝트 파일에는 추가 *지원 파일*의 네트워크를 포함하는 `Import` 요소가 들어 있습니다. 지원 파일에는 프로젝트를 빌드하는 데 필요한 나머지 속성, 대상 및 설정이 포함 되어 있습니다.

지원 파일의 대부분의 대상 및 속성은 빌드 시스템을 구현하는 용도로 존재합니다. 이 문서에서는 MSBuild 명령줄에서 지정할 수 있는 유용한 대상과 속성을 설명 합니다. 더 많은 대상과 속성을 검색하려면 지원 파일 디렉터리에서 파일을 살펴봅니다.

## <a name="support-file-directories"></a>지원 파일 디렉터리

기본적으로 기본 Visual Studio 지원 파일은 다음 디렉터리에 있습니다. 이 정보는 버전별입니다.

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019"></a>Visual Studio 2019

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\`*

  대상에서 사용되는 기본 대상 파일(.targets) 및 속성 파일(.props)을 포함합니다. 기본적으로 $(VCTargetsPath) 매크로는 이 디렉터리를 참조합니다. *`<version>`* 자리 표시자는 Visual studio 버전: v160 For Visual studio 2019, v150 For Visual studio 2017를 나타냅니다.

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\Platforms\<platform>\`*

  해당 부모 디렉터리의 대상과 속성을 재정의하는 플랫폼별 대상 및 속성 파일을 포함합니다. 이 디렉터리에는 이 디렉터리에 있는 대상에서 사용되는 작업을 정의하는 DLL도 포함됩니다. *`<platform>`* 자리 표시자는 ARM, ARM64, Win32 또는 x64 하위 디렉터리를 나타냅니다.

- *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  빌드에서 지정 된를 사용 하 여 c + + 응용 프로그램을 생성할 수 있도록 하는 디렉터리를 포함 합니다 *`<toolset>`* . *`<platform>`* 자리 표시자는 ARM, ARM64, Win32 또는 x64 하위 디렉터리를 나타냅니다. *`<toolset>`* 자리 표시자는 도구 집합 하위 디렉터리를 나타냅니다.

::: moniker-end

::: moniker range=">=vs-2017"

### <a name="visual-studio-2017"></a>Visual Studio 2017

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`*

  대상에서 사용 하는 기본 대상 파일 ( *`.targets`* ) 및 속성 파일 ()을 포함 합니다 *`.props`* . 기본적으로 매크로는 `$(VCTargetsPath)` 이 디렉터리를 참조 합니다.

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\Platforms\<platform>\`*

  해당 부모 디렉터리의 대상과 속성을 재정의하는 플랫폼별 대상 및 속성 파일을 포함합니다. 이 디렉터리에는 이 디렉터리에 있는 대상에서 사용되는 작업을 정의하는 DLL도 포함됩니다. *`<platform>`* 자리 표시자는 ARM, ARM64, Win32 또는 x64 하위 디렉터리를 나타냅니다.

- *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  빌드에서 지정 된를 사용 하 여 c + + 응용 프로그램을 생성할 수 있도록 하는 디렉터리를 포함 합니다 *`<toolset>`* . *`<platform>`* 자리 표시자는 ARM, Win32 또는 x64 하위 디렉터리를 나타냅니다. *`<toolset>`* 자리 표시자는 도구 집합 하위 디렉터리를 나타냅니다.

::: moniker-end

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 및 이전 버전

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\`*

  대상에서 사용되는 기본 대상 파일(.targets) 및 속성 파일(.props)을 포함합니다. 기본적으로 $(VCTargetsPath) 매크로는 이 디렉터리를 참조합니다.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\Platforms\<platform>\`*

  해당 부모 디렉터리의 대상과 속성을 재정의하는 플랫폼별 대상 및 속성 파일을 포함합니다. 이 디렉터리에는 이 디렉터리에 있는 대상에서 사용되는 작업을 정의하는 DLL도 포함됩니다. *`<platform>`* 자리 표시자는 ARM, Win32 또는 x64 하위 디렉터리를 나타냅니다.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\<version>\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  빌드에서 지정 된를 사용 하 여 c + + 응용 프로그램을 생성할 수 있도록 하는 디렉터리를 포함 합니다 *`<toolset>`* . *`<version>`* 자리 표시자는 Visual studio 2012에 대 한 V110, Visual Studio 2013 V120 및 V140 For Visual studio 2015입니다. *`<platform>`* 자리 표시자는 ARM, Win32 또는 x64 하위 디렉터리를 나타냅니다. *`<toolset>`* 자리 표시자는 도구 집합 하위 디렉터리를 나타냅니다. 예를 들어 Visual Studio 2015 도구 집합을 사용 하 여 Windows 앱을 빌드하는 것은 v140입니다. 또는 Visual Studio 2013 도구 집합을 사용 하 여 Windows XP 용 빌드를 v120_xp 합니다.

- *`<drive>:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\Platforms\<platform>\PlatformToolsets\<toolset>\`*

  빌드에서 Visual Studio 2008 또는 Visual Studio 2010 응용 프로그램을 생성할 수 있도록 하는 경로에는이 포함 되지 않습니다 *`<version>`* . 이러한 버전에서는 자리 표시 *`<platform>`* 자가 Itanium, Win32 또는 x64 하위 디렉터리를 나타냅니다. *`<toolset>`* 자리 표시자는 v90 또는 v100 도구 집합 하위 디렉터리를 나타냅니다.

## <a name="support-files"></a>설치 파일

지원 파일 디렉터리에는 다음과 같은 확장을 사용하는 파일이 포함되어 있습니다.

| 확장명 | Description |
| --------- | ----------- |
| *`.targets`* | 대상에서 실행되는 작업을 지정하는 `Target` XML 요소를 포함합니다. 또한 파일 및 명령줄 옵션을 작업 매개 변수에 할당하는 데 사용되는 `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup` 및 사용자 정의 `Item` 요소를 포함할 수 있습니다.<br /><br /> 자세한 내용은 [Target 요소(MSBuild)](/visualstudio/msbuild/target-element-msbuild)를 참조하세요. |
| *`.props`* | 빌드하는 동안 사용되는 파일 및 매개 변수 설정을 지정하는 `Property Group` 및 사용자 정의 `Property` XML 요소를 포함합니다.<br /><br /> 또한 추가 설정을 지정하는 `ItemDefinitionGroup` 및 사용자 정의 `Item` XML 요소를 포함할 수 있습니다. 항목 정의 그룹에 정의 된 항목은 속성과 비슷하지만 명령줄에서 액세스할 수 없습니다. Visual Studio 프로젝트 파일은 속성 대신 항목을 사용하여 설정을 나타내는 경우가 많습니다.<br /><br /> 자세한 내용은 [ItemGroup 요소 (msbuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [Itemdefinitiongroup 요소 (Msbuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)및 [Item 요소 (msbuild)](/visualstudio/msbuild/item-element-msbuild)를 참조 하세요. |
| *`.xml`* | IDE 사용자 인터페이스 요소를 선언 하 고 초기화 하는 XML 요소를 포함 합니다. 예를 들면 속성 시트, 속성 페이지, textbox 컨트롤 및 listbox 컨트롤 등이 있습니다.<br /><br /> *`.xml`* 파일은 MSBuild가 아닌 IDE를 직접 지원 합니다. 그러나 IDE 속성의 값은 빌드 속성과 항목에 할당됩니다.<br /><br /> 대부분의 *`.xml`* 파일은 로캘별 하위 디렉터리에 있습니다. 예를 들어 영어 (미국) 지역의 파일은에 `$(VCTargetsPath)\1033\` 있습니다. |

## <a name="user-targets-and-properties"></a>사용자 대상 및 속성

MSBuild를 효과적으로 사용 하기 위해 유용 하 고 관련 된 속성 및 대상을 파악 하는 데 도움이 됩니다. 대부분의 속성과 대상은 Visual Studio 빌드 시스템을 구현 하는 데 도움이 되며, 따라서 사용자와 관련이 없습니다. 이 섹션에서는에 대해 알고 있는 사용자 지향 속성 및 대상에 대해 설명 합니다.

### <a name="platformtoolset-property"></a>`PlatformToolset` 속성

`PlatformToolset` 속성은 빌드에 사용되는 MSVC 도구 집합을 결정합니다. 기본적으로 현재 도구 집합이 사용됩니다. 이 속성을 설정 하면 해당 값이 리터럴 문자열과 연결 되어 경로를 형성 합니다. 특정 플랫폼에 대 한 프로젝트를 빌드하는 데 필요한 속성 및 대상 파일이 들어 있는 디렉터리입니다. 해당 플랫폼 도구 집합 버전을 사용하여 빌드하려면 플랫폼 도구 집합을 설치해야 합니다.

예를 들어 Visual Studio 2015 도구 및 라이브러리를 사용하여 애플리케이션을 빌드하려면 `PlatformToolset` 속성을 `v140`으로 설정합니다.

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>`PreferredToolArchitecture` 속성

`PreferredToolArchitecture` 속성은 32비트 또는 64비트 컴파일러 및 도구가 빌드에 사용되는지 여부를 결정합니다. 이 속성은 출력 플랫폼 아키텍처 또는 구성에 영향을 주지 않습니다. 기본적으로 MSBuild는이 속성이 설정 되지 않은 경우 x86 버전의 컴파일러 및 도구를 사용 합니다.

예를 들어 64비트 컴파일러 및 도구를 사용하여 애플리케이션을 빌드하려면 `PreferredToolArchitecture` 속성을 `x64`로 설정합니다.

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>`UseEnv` 속성

기본적으로 현재 프로젝트의 플랫폼별 설정은 PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION 및 PLATFORM 환경 변수를 재정의합니다. `UseEnv`환경 변수가 재정의 되지 않도록 하려면 속성을로 설정 합니다 **`true`** .

> `msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>대상

Visual Studio 지원 파일에는 수백 가지 대상이 있습니다. 그러나 대부분은 사용자가 무시할 수 있는 시스템 기반 대상입니다. 대부분의 시스템 대상은 접두사 ()를 접두사로 `_` 사용 하거나,,,, 또는로 시작 하는 이름을 사용 `PrepareFor` `Compute` `Before` `After` `Pre` `Post` 합니다.

다음 표에는 몇 가지 유용한 사용자 기반 대상이 나열되어 있습니다.

| Target | 설명 |
| ------ | ----------- |
| BscMake | Microsoft Browse Information Maintenance Utility 도구(bscmake.exe)를 실행합니다. |
| 빌드 | 프로젝트를 빌드합니다.<br /><br /> 이 대상은 프로젝트의 기본값입니다. |
| ClCompile | MSVC 컴파일러 도구(cl.exe)를 실행합니다. |
| 정리 | 일시적이고 중간 빌드 파일을 삭제합니다. |
| Lib | Microsoft 32비트 라이브러리 관리자 도구(lib.exe)를 실행합니다. |
| 링크 | MSVC 링커 도구(link.exe)를 실행합니다. |
| ManifestResourceCompile | 매니페스트에서 리소스 목록을 추출한 다음, Microsoft Windows Resource Compiler 도구(rc.exe)를 실행합니다. |
| Midl | MIDL(Microsoft 인터페이스 정의 언어) 컴파일러 도구(midl.exe)를 실행합니다. |
| 다시 빌드 | 프로젝트를 정리한 다음, 빌드합니다. |
| ResourceCompile | Microsoft Windows 리소스 컴파일러 도구(rc.exe)를 실행합니다. |
| XdcMake | XML 문서 도구(xdcmake.exe)를 실행합니다. |
| Xsd | XML 스키마 정의 도구(xsd.exe)를 실행합니다. *참고를 참조 하세요.* |

> [!NOTE]
> Visual Studio 2017부터 **xsd** 파일에 대한 C++ 프로젝트 지원이 사용되지 않습니다. **CppCodeProvider.dll**을 수동으로 GAC에 추가하여 **Microsoft.VisualC.CppCodeProvider**를 계속 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보

[MSBuild 작업 참조](/visualstudio/msbuild/msbuild-task-reference)\
[BscMake 작업](/visualstudio/msbuild/bscmake-task)\
[CL 작업](/visualstudio/msbuild/cl-task)\
[CPPClean 작업](/visualstudio/msbuild/cppclean-task)\
[LIB 작업](/visualstudio/msbuild/lib-task)\
[작업 연결](/visualstudio/msbuild/link-task)\
[MIDL 작업](/visualstudio/msbuild/midl-task)\
[MT 작업](/visualstudio/msbuild/mt-task)\
[RC 작업](/visualstudio/msbuild/rc-task)\
[SetEnv 작업](/visualstudio/msbuild/setenv-task)\
[VCMessage 작업](/visualstudio/msbuild/vcmessage-task)\
[XDCMake 작업](/visualstudio/msbuild/xdcmake-task)
