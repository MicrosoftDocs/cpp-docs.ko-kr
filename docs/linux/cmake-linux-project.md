---
title: Visual Studio에서 CMake Linux 프로젝트 만들기
description: Visual Studio에서 Linux CMake 프로젝트를 만드는 방법
ms.date: 08/06/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 5753dbb37c11686becb3e141261284b68468a3bc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507957"
---
# <a name="create-a-cmake-linux-project-in-visual-studio"></a>Visual Studio에서 CMake Linux 프로젝트 만들기

::: moniker range="vs-2015"
Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다. 이러한 버전에 대한 설명서를 보려면 목차 위에 있는 **버전** 드롭다운을 **Visual Studio 2017** 또는 **Visual Studio 2019**로 설정합니다.
::: moniker-end

::: moniker range=">=vs-2017"

플랫폼 간 프로젝트 또는 오픈 소스로 만들 프로젝트에 대해 CMake를 사용하는 것이 좋습니다. CMake 프로젝트를 사용하여 Windows, WSL(Linux용 Windows 하위 시스템) 및 원격 시스템에서 동일한 소스 코드를 빌드하고 디버그할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

먼저 CMake 구성 요소를 비롯하여 Visual Studio Linux 워크로드가 설치되어 있는지 확인합니다. 이는 Visual Studio 설치 관리자의 **C++를 사용한 Linux 개발** 워크로드의 일부입니다. 설치되어 있는지 확실치 않은 경우 [Visual Studio에서 C++ Linux 워크로드 설치](download-install-and-setup-the-linux-development-workload.md)를 참조하세요.

또한 원격 컴퓨터에 다음이 설치되어 있는지 확인합니다.

- gcc
- gdb
- rsync
- zip
- ninja-build(Visual Studio 2019 이상)
::: moniker-end

::: moniker range="vs-2017"
Visual Studio에서 CMake가 지원되려면 CMake 3.8에 도입된 서버 모드 지원이 필요합니다. Microsoft 제공 CMake 변형의 경우 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)에서 미리 빌드된 최신 이진 파일을 다운로드합니다.

이진 파일은 `~/.vs/cmake`에 설치됩니다. 이진 파일을 배포하면 프로젝트가 자동으로 다시 생성됩니다. *CMakeSettings.json*의 `cmakeExecutable` 필드에 지정된 CMake가 유효하지 않고(존재하지 않거나 지원되지 않는 버전인 경우) 미리 빌드된 이진 파일이 있는 경우 Visual Studio는 `cmakeExecutable`을 무시하고 미리 빌드된 이진 파일을 사용합니다.

Visual Studio 2017에서는 CMake 프로젝트를 처음부터 만들 수 없지만, 다음 섹션에 설명된 대로 기존 CMake 프로젝트가 포함된 폴더를 열 수 있습니다.
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019를 사용하여 원격 Linux 시스템 또는 WSL에서 빌드하고 디버그할 수 있으며, 해당 시스템에서 CMake가 호출됩니다. CMake 버전 3.14 이상을 대상 컴퓨터에 설치해야 합니다.

대상 컴퓨터에 최신 버전의 CMake가 있는지 확인합니다. 배포의 기본 패키지 관리자가 제공하는 버전이 Visual Studio에 필요한 모든 기능을 지원하기에 충분하지 않을 수 있습니다. Visual Studio 2019는 CMake의 최신 버전이 Linux 시스템에 설치되어 있는지 검색합니다. 아무 버전도 찾지 못하는 경우 Visual Studio는 편집기 창의 맨 위에 정보 표시줄을 표시합니다. [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)에서 CMake을 설치할 것을 제안합니다.

Visual Studio 2019에서는 CMake 프로젝트를 처음부터 만들거나 기존 CMake 프로젝트를 열 수 있습니다. 새 CMake 프로젝트를 만들려면 아래 지침을 따르세요. 또는 CMake가 이미 있는 경우 [CMake 프로젝트 폴더 열기](#open-a-cmake-project-folder)로 건너뜁니다.

## <a name="create-a-new-linux-cmake-project"></a>새 Linux CMake 프로젝트 만들기

Visual Studio 2019에서 새 Linux CMake 프로젝트를 만들려면

1. Visual Studio에서 **파일 > 새 프로젝트**를 선택하거나 **Ctrl + Shift + N**을 누릅니다.
1. **언어**를 **C++** 로 설정하고 “CMake”를 검색합니다. **다음**을 선택합니다. **이름** 및 **위치**를 입력하고, **만들기**를 선택합니다.

또는 Visual Studio 2019에서 자체 CMake 프로젝트를 열 수 있습니다. 다음 섹션에서 해당 방법을 설명합니다.

Visual Studio는 실행 파일 이름 및 필요한 최소 CMake 버전만 사용하여 최소한의 *CMakeLists.txt* 파일을 만듭니다. 하지만 이 파일을 원하는 대로 수동으로 편집할 수 있습니다. Visual Studio에서 변경 내용을 덮어쓰지 않습니다.

Visual Studio 2019에서 CMake 스크립트를 쉽게 이해하고, 편집하고, 작성할 수 있도록 다음 리소스를 참조하세요.

- [Visual Studio의 CMake용 편집기 내 설명서](https://devblogs.microsoft.com/cppblog/in-editor-documentation-for-cmake-in-visual-studio/)
- [CMake 스크립트에 대한 코드 탐색](https://devblogs.microsoft.com/cppblog/code-navigation-for-cmake-scripts/)
- [CMake 프로젝트에서 파일 및 대상을 쉽게 추가, 제거 및 이름 바꾸기](https://devblogs.microsoft.com/cppblog/easily-add-remove-and-rename-files-and-targets-in-cmake-projects/)
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>CMake 프로젝트 폴더 열기

기존 CMake 프로젝트가 포함된 폴더를 열면, Visual Studio는 CMake 캐시의 변수를 사용하여 IntelliSense를 구성하고 자동으로 빌드합니다. 로컬 구성 및 디버깅 설정은 JSON 파일에 저장됩니다. 필요에 따라 이들 파일을 Visual Studio를 사용하는 다른 사용자와 공유할 수 있습니다.

Visual Studio는 *CMakeLists.txt* 파일을 수정하지 않습니다. 이렇게 하면 동일한 프로젝트에서 작업하는 다른 사용자가 기존 도구를 계속 사용할 수 있습니다. *CMakeLists.txt* 또는 경우에 따라 *CMakeSettings.json*에 대한 편집 내용을 저장하면, Visual Studio가 캐시를 다시 생성합니다. **기존 캐시** 구성을 사용하는 경우에는 Visual Studio에서 캐시를 수정하지 않습니다.

Visual Studio의 CMake 지원에 관한 일반적인 내용은 [Visual Studio의 CMake 프로젝트](../build/cmake-projects-in-visual-studio.md)를 참조하세요. 계속하기 전에 여기서 읽어보세요.

시작하려면 주 메뉴에서 **파일** > **열기** > **폴더**를 선택하거나 [개발자 명령 프롬프트](../build/building-on-the-command-line.md) 창에 `devenv.exe <foldername>`을 입력합니다. 열린 폴더에는 소스 코드와 함께 *CMakeLists.txt* 파일이 있어야 합니다.

다음 예제에서는 간단한 *CMakeLists.txt* 파일과 .cpp 파일을 보여 줍니다.

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="next-steps"></a>다음 단계

[Linux CMake 프로젝트 구성](cmake-linux-configure.md)

## <a name="see-also"></a>참조

[Visual Studio의 CMake 프로젝트](../build/cmake-projects-in-visual-studio.md)<br/>
::: moniker-end
