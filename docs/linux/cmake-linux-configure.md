---
title: Visual Studio에서 Linux CMake 프로젝트 구성
description: Visual Studio에서 Linux CMake 설정을 구성하는 방법
ms.date: 08/08/2020
ms.openlocfilehash: c4c2d4682b6d18f9175a92a810b3f86d8132fc0c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921921"
---
# <a name="configure-a-linux-cmake-project-in-visual-studio"></a>Visual Studio에서 Linux CMake 프로젝트 구성

::: moniker range="msvc-140"
Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다. 이러한 버전에 대한 설명서를 보려면 목차 위에 있는 **버전** 드롭다운을 **Visual Studio 2017** 또는 **Visual Studio 2019** 로 설정합니다.
::: moniker-end

::: moniker range=">=msvc-150"
이 항목에서는 원격 Linux 시스템 또는 WSL(Linux용 Windows 하위 시스템)을 대상으로 하는 CMake 프로젝트에 Linux 구성을 추가하는 방법을 설명합니다. [Visual Studio에서 Linux CMake 프로젝트 만들기](cmake-linux-project.md)로 시작된 시리즈를 계속합니다. MSBuild를 사용하는 경우에는 [Visual Studio에서 Linux MSBuild 프로젝트 구성](configure-a-linux-project.md)을 참조하세요.

## <a name="add-a-linux-configuration"></a>Linux 구성 추가

하나의 구성을 사용하여 동일한 소스 코드를 갖는 다양한 플랫폼(Windows, WSL, 원격 시스템)을 대상으로 지정할 수 있습니다. 또한 구성을 사용하여 컴파일러를 설정하고, 환경 변수를 전달하고, CMake를 호출하는 방법을 사용자 지정할 수 있습니다. *CMakeSettings.json* 파일은 [CMake 설정 사용자 지정](../build/customize-cmake-settings.md)에 나열된 속성의 일부 또는 전부를 지정하며 원격 Linux 머신의 빌드 설정을 제어하는 추가 속성도 지정할 수 있습니다.
::: moniker-end

::: moniker range="msvc-150"
Visual Studio 2017에서 기본 CMake 설정을 변경하려면 주 메뉴에서 **CMake** > **CMake 설정 변경** > **CMakeLists.txt** 를 선택합니다. 또는 **솔루션 탐색기** 에서 *CMakeLists.txt* 를 마우스 오른쪽 단추로 클릭하고 **CMake 설정 변경** 을 선택합니다. 그러면 Visual Studio가 루트 프로젝트 폴더에 새 *CMakeSettings.json* 파일을 만듭니다. 변경하려면 파일을 열고 직접 수정합니다. 자세한 내용은 [CMake 설정 사용자 지정](../build/customize-cmake-settings.md)을 참조하세요.

Visual Studio 2017(및 Visual Studio 2019 버전 16.0)의 Linux-Debug에 대한 기본 구성은 다음과 같습니다.

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="msvc-160"
Visual Studio 2019의 기본 CMake 설정을 변경하려면 주 도구 모음에서 **구성** 드롭다운을 열고 **구성 관리** 를 선택합니다.

![CMake 구성 관리](../build/media/vs2019-cmake-manage-configurations.png "CMake 구성 드롭다운")

이 명령은 루트 프로젝트 폴더의 *CMakeSettings.json* 파일을 편집하는 데 사용할 수 있는 **CMake 설정 편집기** 를 엽니다. JSON 편집기의 **JSON 편집** 단추를 클릭하여 편집기에서 파일을 열 수도 있습니다. 자세한 내용은 [CMake 설정 사용자 지정](../build/customize-cmake-settings.md)을 참조하세요.

Visual Studio 2019 버전 16.1 이상의 기본 Linux-Debug 구성은 다음과 같습니다.

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```

Visual Studio 2019 버전 16.6 이상에서 Ninja는 원격 시스템 또는 WSL을 대상으로 하는 구성의 기본 생성기입니다. 자세한 내용은 [C++ 팀 블로그](https://devblogs.microsoft.com/cppblog/linux-development-with-visual-studio-first-class-support-for-gdbserver-improved-build-times-with-ninja-and-updates-to-the-connection-manager/)에서 이 게시물을 참조하세요.

::: moniker-end
::: moniker range=">=msvc-150"
이러한 설정에 대한 자세한 내용은 [CMakeSettings.json 참조](../build/cmakesettings-reference.md)를 참조하세요.

빌드를 수행할 때

- 원격 시스템을 대상으로 지정하는 경우 Visual Studio는 기본적으로 **도구** > **옵션** > **플랫폼 간** > **연결 관리자** 아래의 목록에서 첫 번째 원격 시스템을 원격 대상으로 선택합니다.
- 원격 연결이 발견되지 않으면 만들라는 메시지가 표시됩니다. 자세한 내용은 [원격 Linux 컴퓨터에 연결](connect-to-your-remote-linux-computer.md)을 참조하세요.

## <a name="choose-a-linux-target"></a>Linux 대상 선택

CMake 프로젝트 폴더를 열면 Visual Studio가 *CMakeLists.txt* 파일을 구문 분석하고 **x86-Debug** 의 Windows 대상을 지정합니다. 원격 Linux 시스템을 대상으로 지정하려면 Linux 컴파일러를 기반으로 프로젝트 설정을 변경합니다. 예를 들어 Linux에서 GCC를 사용하고 디버그 정보를 사용하여 컴파일하는 경우 다음을 선택합니다.  **Linux-GCC-Debug** 또는 **Linux-GCC-Release**.

원격 Linux 대상을 지정하면 원격 시스템에 원본이 복사됩니다.

대상을 선택하면 CMake는 프로젝트에 대한 CMake 캐시를 생성하도록 Linux 시스템에서 자동으로 실행됩니다.

![Linux에서 CMake 캐시 생성](media/cmake-linux-1.png "Linux에서 CMake 캐시 생성")

::: moniker-end
::: moniker range="msvc-160"

### <a name="target-windows-subsystem-for-linux"></a>Linux용 Windows 하위 시스템을 대상으로 지정

WSL(Linux용 Windows 하위 시스템)을 대상으로 지정하는 경우 원격 연결을 추가할 필요가 없습니다.

WSL을 대상으로 지정하려면 주 도구 모음의 구성 드롭다운에서 **구성 관리** 를 선택합니다.

![CMake 구성 관리](../build/media/vs2019-cmake-manage-configurations.png "CMake 구성 드롭다운")

**CMakeSettings.json** 창이 표시됩니다.

![구성 추가](media/cmake-linux-configurations.png "CMake 설정에 구성 추가")

**구성 추가** (녹색 '+' 단추)를 누른 다음, GCC를 사용하는 경우 **Linux-GCC-Debug** 또는 **Linux-GCC-Release** 를 선택합니다. Clang/LLVM 도구 집합을 사용하는 경우 Clang 변형을 사용합니다.  **선택** 을 누른 다음, **Ctrl+S** 를 눌러 구성을 저장합니다.

**Visual Studio 2019 버전 16.1** WSL을 대상으로 지정하는 경우 Linux의 컴파일러가 탑재된 Windows 파일 시스템의 소스 파일에 직접 액세스할 수 있기 때문에 Visual Studio는 소스 파일을 복사하고 두 개의 빌드 트리 동기 복사본을 유지 관리하지 않아도 됩니다.
::: moniker-end
::: moniker range=">=msvc-150"

### <a name="intellisense"></a>IntelliSense

정확한 C++ IntelliSense를 사용하려면 C++ 소스 파일이 참조하는 C++ 헤더에 대한 액세스가 필요합니다. Visual Studio는 자동으로 Linux에서 CMake 프로젝트가 참조하는 헤더를 사용하여 최고 충실도의 IntelliSense 환경을 제공합니다. 자세한 내용은 [원격 헤더를 위한 IntelliSense](configure-a-linux-project.md#remote_intellisense)를 참조하세요.

### <a name="locale-setting"></a>로캘 설정

Visual Studio에서는 설치된 패키지를 관리하거나 구성하지 않으므로 Visual Studio 언어 설정이 Linux 대상으로 전파되지 않습니다. 출력 창에 표시되는 빌드 오류와 같은 메시지는 Linux 대상의 언어와 로캘을 사용하여 표시됩니다. Linux 대상에서 원하는 로캘을 구성해야 합니다.

## <a name="additional-settings"></a>추가 설정

다음 설정을 사용하여 빌드하기 전후 및 CMake 생성 전에 Linux 시스템에서 명령을 실행할 수 있습니다. 값은 원격 시스템에서 유효한 모든 명령일 수 있습니다. 출력은 Visual Studio로 다시 파이핑됩니다.

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

## <a name="next-steps"></a>다음 단계

[CMake 디버깅 세션 구성](../build/configure-cmake-debugging-sessions.md?toc=/cpp/linux/toc.json&bc=/cpp/_breadcrumb/toc.json)

## <a name="see-also"></a>참고 항목

[프로젝트 속성 사용](../build/working-with-project-properties.md)<br/>
[CMake 사용자 지정 설정](../build/customize-cmake-settings.md)<br/>
[CMake 미리 정의된 구성 참조](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
