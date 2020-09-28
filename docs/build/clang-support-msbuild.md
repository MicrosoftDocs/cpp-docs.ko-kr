---
title: Visual Studio 프로젝트의 Clang/LLVM 지원
ms.date: 06/02/2020
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: a34b8931fa344071d319770ef1c55fc46d27e1e2
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686347"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Visual Studio 프로젝트의 Clang/LLVM 지원

::: moniker range="<=vs-2017"

CMake 및 MSBuild 프로젝트 모두에 대한 Clang 지원은 Visual Studio 2019에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 버전 16.2를 사용하여 Windows 또는 Linux를 대상으로 하는 C++ Visual Studio 프로젝트(MSBuild)를 편집, 빌드 및 디버그할 수 있습니다.

## <a name="install"></a>설치

Visual Studio에서 최상으로 IDE를 지원하려면 Windows용 최신 Clang 컴파일러 도구를 사용하는 것이 좋습니다. 이러한 도구가 아직 없는 경우 Visual Studio 설치 관리자를 열고 **C++를 사용한 데스크톱 개발** 선택적 구성 요소 아래에서 **Windows용 C++ Clang 도구**를 선택하여 설치할 수 있습니다. 컴퓨터에서 기존 Clang 설치를 사용하려면 **v142 빌드 도구용 C++ Clang-cl** 선택적 구성 요소를 선택합니다. Microsoft C++ 표준 라이브러리에는 현재 Clang 8.0.0 이상이 필요합니다. Clang의 번들 버전은 Microsoft의 표준 라이브러리 구현에서 최신 업데이트가 적용되도록 자동으로 업데이트됩니다.

![개별 구성 요소 탭이 선택되고 C++ Clang 구성 요소가 표시된 Visual Studio 설치 프로그램의 스크린샷](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Clang 도구를 사용하도록 Windows 프로젝트 구성

Clang을 사용하도록 Visual Studio 프로젝트를 구성하려면 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. 일반적으로 대화 상자 위쪽에서 **모든 구성**을 먼저 선택해야 합니다. 그런 다음 **일반** > **플랫폼 도구 집합**에서 **LLVM(clang-cl)** 을 선택한 다음 **확인**을 선택합니다.

![구성 속성 > 일반이 선택되고 플랫폼 도구 집합 및 LLVM(clang cl) 옵션이 강조 표시된 속성 페이지 대화 상자의 스크린샷](media/clang-msbuild-prop-page.png)

Visual Studio와 함께 번들로 제공되는 Clang 도구를 사용하는 경우 추가 단계가 필요하지 않습니다. Windows 프로젝트의 경우 Visual Studio는 기본적으로 [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) 모드에서 Clang을 호출하고 표준 라이브러리의 Microsoft 구현과 연결됩니다. 기본적으로 **clang-cl.exe**는 *%VCINSTALLDIR%\\Tools\\Llvm\\bin\\* 및 *%VCINSTALLDIR%\\Tools\\Llvm\\x64\\bin\\* 에 있습니다.

사용자 지정 Clang 설치를 사용하는 경우 사용자 지정 Clang 설치 루트를 첫 번째 디렉터리로 추가하여 **프로젝트** > **속성** > **VC++ 디렉터리** > **구성 속성** > **실행 파일 디렉터리**를 수정하거나 `LLVMInstallDir` 속성의 값을 변경할 수 있습니다. 자세한 내용은 [사용자 지정 LLVM 위치 설정](#custom_llvm_location)을 참조하세요.

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Clang 도구를 사용하도록 Linux 프로젝트 구성

Linux 프로젝트의 경우 Visual Studio는 Clang GCC 호환 프런트 엔드를 사용합니다. 프로젝트 속성과 거의 모든 컴파일러 플래그가 동일합니다.

Clang을 사용하도록 Visual Studio Linux 프로젝트를 구성하려면

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
1. 일반적으로 대화 상자 위쪽에서 **모든 구성**을 먼저 선택해야 합니다.
1. **일반** > **플랫폼 도구 집합**에서 Linux용 Windows 하위 시스템을 사용하는 경우 **WSL_Clang_1_0**을 선택하고, 원격 컴퓨터 또는 VM을 사용하는 경우 **Remote_Clang_1_0**을 선택합니다.
1. **확인**을 누릅니다.

![구성 속성 > 일반이 선택되고 플랫폼 도구 집합 및 LLVM(clang cl) 옵션이 강조 표시된 콘솔 앱 Clang Visual Studio 2019 속성 페이지 대화 상자의 스크린샷](media/clang-msbuild-prop-page.png)

Linux에서 Visual Studio는 기본적으로 PATH 환경 속성에서 발견된 첫 번째 Clang 위치를 사용합니다. 사용자 지정 Clang 설치를 사용하는 경우 `LLVMInstallDir` 속성의 값을 변경하거나 **프로젝트** > **속성** > **VC++ 디렉터리** > **구성 속성** > **실행 파일 디렉터리**에서 경로를 바꿔야 합니다. 자세한 내용은 [사용자 지정 LLVM 위치 설정](#custom_llvm_location)을 참조하세요.

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a> 사용자 지정 LLVM 위치 설정

*Directory.build.props* 파일을 만들고 해당 파일을 프로젝트의 루트 폴더에 추가하여 하나 이상의 프로젝트에 대해 LLVM의 사용자 지정 경로를 설정할 수 있습니다. 루트 솔루션 폴더에 추가하면 솔루션의 모든 프로젝트에 적용할 수 있습니다. 파일은 다음과 비슷합니다(실제 경로로 바꿔야 함).

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>추가 속성 설정, 편집, 빌드 및 디버그

Clang 구성을 설정한 후 다시 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 다시 로드**를 선택합니다. 이제 Clang 도구를 사용하여 프로젝트를 빌드하고 디버그할 수 있습니다. Visual Studio는 Clang 컴파일러를 사용 중임을 감지하고 IntelliSense, 강조 표시, 탐색 및 기타 편집 기능을 제공합니다. 오류 및 경고는 **출력 창**에 표시됩니다. Clang 구성의 프로젝트 속성 페이지는 MSVC와 매우 비슷하지만, 편집하며 계속하기와 같은 일부 컴파일러 종속 기능은 Clang 구성에 사용할 수 없습니다. 속성 페이지에서 사용할 수 없는 Clang 컴파일러 또는 링커 옵션을 설정하려면 속성 페이지의 **구성 속성** > **C/C++(또는 링커)**  > **명령줄** > **추가 옵션**에서 수동으로 추가할 수 있습니다.

디버깅하는 경우 중단점, 메모리 및 데이터 시각화, 그리고 대부분의 다른 디버깅 기능을 사용할 수 있습니다.  

![Clang 디버깅](media/clang-debug-msbuild.png)

::: moniker-end
