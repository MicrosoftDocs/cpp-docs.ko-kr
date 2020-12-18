---
description: '자세한 정보: CMake 빌드 설정 사용자 지정'
title: Visual Studio에서 CMake 빌드 설정 사용자 지정
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: a7a0dcf946d4bef3a1dc7eb63fd2c22be6740682
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156855"
---
# <a name="customize-cmake-build-settings"></a>CMake 빌드 설정 사용자 지정

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 **CMake 설정 편집기** 를 사용하여 구성을 추가하고 설정을 사용자 지정할 수 있습니다. 이 편집기는 *CMakeSettings.json* 파일을 수동으로 편집할 필요가 없도록 도와주기 위해 개발된 대안이지만, 파일을 직접 편집하는 것을 선호하는 경우 편집기의 오른쪽 위에 있는 **JSON 편집** 링크를 클릭하면 됩니다.

편집기를 열려면 주 도구 모음에서 **구성** 드롭다운을 클릭하고 **구성 관리** 를 선택합니다.

![CMake 구성 드롭다운](media/vs2019-cmake-manage-configurations.png)

이제 왼쪽에 설치된 구성과 함께 **설정 편집기** 가 보입니다.

![CMake 설정 편집기](media/cmake-settings-editor.png)

Visual Studio는 기본적으로 하나의 `x64-Debug` 구성을 제공합니다. 녹색 더하기 기호를 클릭하여 다른 구성을 추가할 수 있습니다. 편집기에 표시되는 설정은 선택한 구성에 따라 달라질 수 있습니다.

편집기에서 선택하는 옵션은 *CMakeSettings.json* 이라는 파일에 기록됩니다. 이 파일은 프로젝트를 빌드할 때 CMake로 전달되는 환경 변수 및 명령줄 인수를 제공합니다. Visual Studio는 절대로 *CMakeLists.txt* 파일을 자동으로 구성하지 않습니다. *CMakeSettings.json* 을 사용하면 CMake 프로젝트 파일을 건들지 않고 Visual Studio를 통해 빌드를 사용자 지정할 수 있으므로 다른 팀원들이 각자 사용하는 도구로 이 파일을 사용할 수 있습니다.

## <a name="cmake-general-settings"></a>CMake 일반 설정

다음 설정은 **일반** 제목 아래에서 사용할 수 있습니다.

### <a name="configuration-name"></a>구성 이름

**name** 설정에 해당합니다. 이 이름은 C++ 구성 드롭다운에 표시됩니다. `${name}` 매크로를 사용하여 경로 등의 다른 속성 값을 작성할 수 있습니다.

### <a name="configuration-type"></a>구성 형식

**configurationType** 설정에 해당합니다. 선택한 생성기의 빌드 구성 형식을 정의합니다. 현재 지원되는 값은 "Debug", "MinSizeRel", "Release" 및 "RelWithDebInfo"입니다. [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)에 매핑됩니다.

### <a name="toolset"></a>도구 집합

**inheritedEnvironments** 설정에 해당합니다. 선택한 구성을 빌드하는 데 사용하는 컴파일러 환경을 정의합니다. 지원되는 값은 구성 형식에 따라 다릅니다. 사용자 지정 환경을 만들려면 설정 편집기의 오른쪽 위 모서리에서 **JSON 편집** 을 선택하여 *CMakeSettings.json* 파일을 직접 편집합니다.

### <a name="cmake-toolchain-file"></a>CMake 도구 체인 파일

[CMake 도구 체인 파일](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html)의 경로입니다. 이 경로는 CMake에 "-DCMAKE_TOOLCHAIN_FILE = \<filepath>"로 전달됩니다. 도구 체인 파일은 컴파일러 및 도구 체인 유틸리티, 기타 대상 플랫폼의 위치 및 컴파일러 관련 정보를 지정합니다. 이 설정이 지정되지 않은 경우 Visual Studio는 기본적으로 [vcpkg 도구 체인 파일](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake)을 사용합니다.

### <a name="build-root"></a>빌드 루트

**buildRoot** 에 해당합니다. [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)에 매핑되고 CMake 캐시를 만들 위치를 지정합니다. 지정된 폴더가 없으면 만들어집니다.

## <a name="command-arguments"></a>명령 인수

다음 설정은 **명령 인수** 제목 아래에서 사용할 수 있습니다.

### <a name="cmake-command-arguments"></a>CMake 명령 인수

**cmakeCommandArgs** 에 해당합니다. CMake.exe에 전달되는 추가 [명령줄 옵션](https://cmake.org/cmake/help/latest/manual/cmake.1.html)을 지정합니다.

### <a name="build-command-arguments"></a>빌드 명령 인수

**buildCommandArgs** 에 해당합니다. 기본 빌드 시스템에 전달할 추가 스위치를 지정합니다. 예를 들어 Ninja 생성기를 사용하는 경우 `-v`를 전달하면 Ninja에서 명령줄을 출력하도록 강제합니다.

### <a name="ctest-command-arguments"></a>CTest 명령 인수

**ctestCommandArgs** 에 해당합니다. 테스트 실행 시 CTest에 전달되는 추가 [명령줄 옵션](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html)을 지정합니다.

## <a name="general-settings-for-remote-builds"></a>원격 빌드의 일반 설정

원격 빌드를 사용하는 Linux 같은 구성에는 다음 설정을 사용할 수도 있습니다.

### <a name="rsync-command-arguments"></a>rsync 명령 인수

빠른 다목적 파일 복사 도구인 [rsync](https://download.samba.org/pub/rsync/rsync.html)로 전달되는 추가 명령줄 옵션입니다.

## <a name="cmake-variables-and-cache"></a>CMake 변수 및 캐시

이러한 설정을 통해 CMake 변수를 설정하고 *CMakeSettings.json* 에 저장할 수 있습니다. 빌드 시 CMake에 전달되고 *CMakeLists.txt* 파일에 있는 모든 값을 재정의합니다. CMakeGUI를 사용할 때와 똑같은 방식으로 이 섹션을 사용하여 편집에 사용 가능한 모든 CMake 변수 목록을 볼 수 있습니다. 고급 변수(CMakeGUI당)를 포함하여 편집에 사용 가능한 모든 CMake 변수 목록을 보려면 **저장하고 캐시 생성** 단추를 클릭합니다. 목록을 변수 이름으로 필터링할 수 있습니다.

**변수** 에 해당합니다. **-D** *_이름_=_값_* 으로 CMake에 전달된 CMake 변수의 이름-값 쌍을 포함합니다. CMake 프로젝트 빌드 지침에서 CMake 캐시 파일에 변수를 직접 추가하도록 지정하는 경우 여기에 대신 추가하는 것이 좋습니다.

## <a name="advanced-settings"></a>고급 설정

### <a name="cmake-generator"></a>CMake 생성기

**생성기** 에 해당합니다. CMake **-G** 스위치에 매핑되고 사용할 [CMake 생성기](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)를 지정합니다. 이 속성은 다른 속성 값을 구성할 때 매크로(`${generator}`)로 사용할 수도 있습니다. Visual Studio에서 현재 지원하는 CMake 생성기는 다음과 같습니다.

- "Ninja"
- "Unix 메이크파일"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Ninja는 유연성과 기능 대신 빠른 속도로 빌드하도록 설계되었으므로 기본값으로 설정됩니다. 그러나 일부 CMake 프로젝트는 Ninja를 사용하여 올바르게 빌드하지 못할 수도 있습니다. 이 경우 CMake에서 Visual Studio 프로젝트를 대신 생성하도록 지시할 수 있습니다.

### <a name="intellisense-mode"></a>IntelliSense 모드

IntelliSense 엔진에서 사용하는 IntelliSense 모드입니다. 모드를 선택하지 않은 경우 Visual Studio는 지정된 도구 집합에서 상속합니다.  

### <a name="install-directory"></a>설치 디렉터리

CMake가 대상을 설치하는 디렉터리입니다. [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)에 매핑됩니다.

### <a name="cmake-executable"></a>CMake 실행 파일

파일 이름과 확장명이 포함된 CMake 프로그램 실행 파일의 전체 경로입니다. Visual Studio에서 사용자 지정 버전의 CMake를 사용할 수 있습니다. 원격 빌드의 경우 원격 머신의 CMake 위치를 지정합니다.

원격 빌드를 사용하는 Linux 같은 구성에는 다음 설정을 사용할 수도 있습니다.

### <a name="remote-cmakeliststxt-root"></a>원격 CMakeLists.txt 루트

루트 *CMakeLists.txt* 파일을 포함하는 원격 머신의 디렉터리입니다.

### <a name="remote-install-root"></a>원격 설치 루트

CMake가 대상을 설치하는 원격 머신의 디렉터리입니다. [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)에 매핑됩니다.

### <a name="remote-copy-sources"></a>원본 소스 복사

소스 파일을 원격 컴퓨터에 복사할지 여부를 지정하며, rsync 또는 sftp 중 무엇을 사용할 것인지 지정할 수 있습니다.

## <a name="directly-edit-cmakesettingsjson"></a>CMakeSettings.json 직접 편집

*CMakeSettings.json* 을 직접 편집하여 사용자 지정 구성을 만들 수도 있습니다. **설정 편집기** 의 오른쪽 위에는 편집할 파일을 여는 **JSON 편집** 단추가 있습니다.

다음 예제는 시작점으로 사용할 수 있는 샘플 구성을 보여줍니다.

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense를 사용하면 *CMakeSettings.json* 파일을 편집할 수 있습니다.

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

또한 호환되지 않는 설정을 선택하면 JSON 편집기가 그 사실을 알려줍니다.

파일의 각 속성에 대한 자세한 내용은 [CMakeSettings.json 스키마 참조](cmakesettings-reference.md)를 확인하세요.

::: moniker-end

::: moniker range="<=msvc-150"

Visual Studio 2017은 CMake.exe를 호출하여 지정된 프로젝트에 대한 CMake 캐시를 만드는 방법을 정의하는 몇 가지 CMake 구성을 제공합니다. 새 구성을 추가하려면 도구 모음에서 구성 드롭다운을 클릭하고 **구성 관리** 를 선택합니다.

   ![CMake 구성 관리](media/cmake-manage-configurations.png)

미리 정의된 구성 목록에서 다음을 선택할 수 있습니다.

   ![CMake 미리 정의된 구성](media/cmake-configurations.png)

처음 구성을 선택하면 Visual Studio가 프로젝트의 루트 폴더에 *CMakeSettings.json* 파일을 만듭니다. 이 파일은 예를 들어 **정리** 작업 후에 CMake 캐시 파일을 다시 만드는 데 사용됩니다.

추가 구성을 추가하려면 *CMakeSettings.json* 을 마우스 오른쪽 단추로 클릭하고 **구성 추가** 를 선택합니다.

   ![CMake 구성 추가](media/cmake-add-configuration.png "CMake 구성 추가")

**CMake 설정 편집기** 를 사용하여 파일을 편집할 수도 있습니다. **솔루션 탐색기** 에서 *CMakeSettings.json* 을 마우스 오른쪽 단추로 클릭하고 **CMake 설정 편집** 을 선택합니다. 또는 편집기 창 상단의 구성 드롭다운에서 **구성 관리** 를 선택합니다.

*CMakeSettings.json* 을 직접 편집하여 사용자 지정 구성을 만들 수도 있습니다. 다음 예제는 시작점으로 사용할 수 있는 샘플 구성을 보여줍니다.

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense를 사용하면 *CMakeSettings.json* 파일을 편집할 수 있습니다.

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

파일의 각 속성에 대한 자세한 내용은 [CMakeSettings.json 스키마 참조](cmakesettings-reference.md)를 확인하세요.

::: moniker-end

## <a name="see-also"></a>참조

[Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)<br/>
[Linux CMake 프로젝트 구성](../linux/cmake-linux-project.md)<br/>
[원격 Linux 컴퓨터에 연결](../linux/connect-to-your-remote-linux-computer.md)<br/>
[CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)<br/>
[Linux 프로젝트 배포, 실행 및 디버그](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)
