---
title: CMake 미리 정의된 구성 참조
ms.description: Visual Studio provides several predefined build configurations for CMake projects on Linux, Windows, ARM, and IoT.
ms.date: 06/12/2019
helpviewer_keywords:
- CMake redefined configurations
ms.openlocfilehash: 3c957ebf92d038a9913b0fb9c4b06f1fae2da0a2
ms.sourcegitcommit: 2a96750322bca43a8a29fdc400e14ca36132f9c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93401045"
---
# <a name="cmake-predefined-build-configurations"></a>CMake 미리 정의된 빌드 구성

::: moniker range="msvc-140"

CMake 프로젝트는 Visual Studio 2017 이상에서 지원됩니다.

::: moniker-end

::: moniker range=">=msvc-150"

CMake 프로젝트에서 빌드 구성은 CMakeSettings.json 파일에 저장됩니다. 주 도구 모임의 빌드 구성 드롭다운에서 **구성 관리** 를 선택하면 Visual Studio에서 사용할 수 있는 기본 CMake 구성을 보여주는 대화 상자가 나타납니다.

- x86 디버그
- x86 릴리스
- x64 디버그
- x64 릴리스
- Linux-디버그
- Linux-릴리스
- IoT 디버그
- IoT 릴리스
- MinGW 디버그
- MinGW 릴리스

구성을 선택하면 프로젝트의 루트 폴더에 있는 *CMakeSettings.json* 파일에 추가됩니다. 그런 다음, 이를 사용하여 프로젝트를 빌드할 수 있습니다. 구성 속성에 대한 자세한 내용은 [CMakeSettings 참조](cmakesettings-reference.md)를 참조하세요.

## <a name="linux-predefined-build-configurations"></a>Linux 미리 정의된 빌드 구성:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "user@host",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [
        ".vs",
        ".git"
      ],
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [
        "linux_x64"
      ]
}

{
      "name": "Linux-Release",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "RelWithDebInfo",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [
        ".vs",
        ".git"
      ],
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [
        "linux_x64"
      ]
},
```


추가 컨트롤에서 다음과 같은 선택적 설정을 사용할 수 있습니다.

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

이러한 옵션을 사용하면 빌드하기 전후 및 CMake 생성 전에 원격 시스템에서 명령을 실행할 수 있습니다. 값은 원격 시스템에서 유효한 모든 명령일 수 있습니다. 출력은 Visual Studio로 다시 파이핑됩니다.

## <a name="iot-predefined-build-configurations"></a>IoT 미리 정의된 빌드 구성

```json
{
      "name": "IoT-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [
        "gcc-arm"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "intelliSenseMode": "linux-gcc-arm",
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "arm-none-eabi-gcc.exe"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "arm-none-eabi-g++.exe"
        },
        {
          "name": "CMAKE_C_FLAGS",
          "value": "-nostartfiles"
        },
        {
          "name": "CMAKE_CXX_FLAGS",
          "value": "-nostartfiles -fno-rtti -fno-exceptions"
        },
        {
          "name": "CMAKE_CXX_STANDARD",
          "value": "14"
        },
        {
          "name": "CMAKE_SYSTEM_NAME",
          "value": "Generic"
        },
        {
          "name": "CMAKE_SYSTEM_PROCESSOR",
          "value": "arm"
        }
      ]
    },
    {
      "name": "IoT-Release",
      "generator": "Ninja",
      "configurationType": "Release",
      "inheritEnvironments": [
        "gcc-arm"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "intelliSenseMode": "linux-gcc-arm",
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "arm-none-eabi-gcc.exe"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "arm-none-eabi-g++.exe"
        },
        {
          "name": "CMAKE_C_FLAGS",
          "value": "-nostartfiles"
        },
        {
          "name": "CMAKE_CXX_FLAGS",
          "value": "-nostartfiles -fno-rtti -fno-exceptions"
        },
        {
          "name": "CMAKE_CXX_STANDARD",
          "value": "14"
        },
        {
          "name": "CMAKE_SYSTEM_NAME",
          "value": "Generic"
        },
        {
          "name": "CMAKE_SYSTEM_PROCESSOR",
          "value": "arm"
        }
      ]
    }
```

## <a name="mingw-predefined-build-configurations"></a>MinGW 미리 정의된 빌드 구성

```json
{
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "7.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.INCLUDE};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ],
      "name": "Mingw64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [
        "mingw_64"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "intelliSenseMode": "linux-gcc-x64",
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "${env.BIN_ROOT}\\gcc.exe"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "${env.BIN_ROOT}\\g++.exe"
        }
      ]
    }

{
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "7.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.INCLUDE};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ],
      "name": "Mingw64-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "inheritEnvironments": [
        "mingw_64"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "intelliSenseMode": "linux-gcc-x64",
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "${env.BIN_ROOT}\\gcc.exe"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "${env.BIN_ROOT}\\g++.exe"
        }
      ]
    }
```

## <a name="x86-64-predefined-build-configurations"></a>x86-64 미리 정의된 빌드 구성

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
    {
      "name": "x86-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [
        "msvc_x64_x64"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
    {
      "name": "x64-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "inheritEnvironments": [
        "msvc_x64_x64"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
    {
      "name": "x86-Release2",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    }
  ]
}
```

::: moniker-end

::: moniker range="msvc-160"

CMake 프로젝트에서 빌드 구성은 CMakeSettings.json 파일에 저장됩니다. 주 도구 모임의 빌드 구성 드롭다운에서 **구성 관리** 를 선택하면 Visual Studio에서 사용할 수 있는 기본 CMake 구성을 보여주는 대화 상자가 나타납니다.

- x86 디버그
- x86 Clang 디버그
- x86 릴리스
- x86 Clang 릴리스
- x64 디버그
- x64 Clang 디버그
- x64 릴리스
- x64 Clang 릴리스
- Linux-디버그
- Linux-릴리스
- Linux-Clang-디버그
- Linux-Clang-릴리스
- 기존 캐시(원격)
- 기존 캐시
- MinGW 디버그
- MinGW 릴리스
- WSL 디버그
- WSL 릴리스
- WSL Clang 디버그
- WSL Clang 릴리스
- Clang

구성을 선택하면 프로젝트의 루트 폴더에 있는 CMakeSettings.json 파일에 추가됩니다. 그런 다음, 이를 사용하여 프로젝트를 빌드할 수 있습니다.

```json
{
  "configurations": [
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Release",
      "inheritEnvironments": [ "msvc_x64_x64" ],
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "variables": []
    },
    {
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Release",
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
    },
    {
      "name": "Linux-Release",
      "generator": "Unix Makefiles",
      "configurationType": "RelWithDebInfo",
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
    },
    {
      "name": "Linux-Clang-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_clang_x64" ],
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
    },
    {
      "name": "Linux-Clang-Release",
      "generator": "Unix Makefiles",
      "configurationType": "RelWithDebInfo",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_clang_x64" ],
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
    },
    {
      "name": "Existing Cache (Remote)",
      "cacheRoot": "",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCopySources": false,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    },
    {
      "name": "Mingw64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "mingw_64" ],
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "7.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.INCLUDE};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ],
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "${env.BIN_ROOT}\\gcc.exe",
          "type": "STRING"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "${env.BIN_ROOT}\\g++.exe",
          "type": "STRING"
        }
      ],
      "intelliSenseMode": "linux-gcc-x64"
    },
    {
      "name": "Mingw64-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "mingw_64" ],
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "7.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.INCLUDE};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ],
      "variables": [
        {
          "name": "CMAKE_C_COMPILER",
          "value": "${env.BIN_ROOT}\\gcc.exe",
          "type": "STRING"
        },
        {
          "name": "CMAKE_CXX_COMPILER",
          "value": "${env.BIN_ROOT}\\g++.exe",
          "type": "STRING"
        }
      ],
      "intelliSenseMode": "linux-gcc-x64"
    },
    {
      "name": "x64-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "msvc_x64_x64" ],
      "variables": []
    },
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "msvc_x86" ],
      "variables": []
    },
    {
      "name": "x86-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "msvc_x86" ],
      "variables": []
    },
    {
      "name": "x86-Clang-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "clang_cl_x86" ],
      "variables": []
    },
    {
      "name": "x86-Clang-Release",
      "generator": "Ninja",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "clang_cl_x86" ],
      "variables": []
    },
    {
      "name": "Existing Cache",
      "cacheRoot": "",
      "inheritEnvironments": [],
      "variables": []
    },
    {
      "name": "WSL-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeExecutable": "/usr/bin/cmake",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "wslPath": "${defaultWSLPath}",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    },
    {
      "name": "WSL-Release",
      "generator": "Unix Makefiles",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeExecutable": "/usr/bin/cmake",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "wslPath": "${defaultWSLPath}",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    },
    {
      "name": "WSL-Clang-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeExecutable": "/usr/bin/cmake",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_clang_x64" ],
      "wslPath": "${defaultWSLPath}",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    },
    {
      "name": "WSL-Clang-Release",
      "generator": "Unix Makefiles",
      "configurationType": "RelWithDebInfo",
      "buildRoot": "${projectDir}\\out\\build\\${name}",
      "installRoot": "${projectDir}\\out\\install\\${name}",
      "cmakeExecutable": "/usr/bin/cmake",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_clang_x64" ],
      "wslPath": "${defaultWSLPath}",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```

::: moniker-end

## <a name="see-also"></a>참조

[Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)<br/>
[Linux CMake 프로젝트 구성](../linux/cmake-linux-project.md)<br/>
[원격 Linux 컴퓨터에 연결](../linux/connect-to-your-remote-linux-computer.md)<br/>
[CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)<br/>
[Linux 프로젝트 배포, 실행 및 디버그](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)<br/>
