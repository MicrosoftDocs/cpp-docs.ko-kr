---
description: '자세한 정보: Visual Studio에서 C++ 빌드 시스템에 대해 폴더 열기 지원'
title: Visual Studio에서 C++ 빌드 시스템에 대해 폴더 열기 지원
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 35434f70543b2f3241c50a005700bdf4a2564f95
ms.sourcegitcommit: bdaa0bf20cc0fc79bc70cbab45defd55328e27d7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99588787"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Visual Studio에서 C++ 빌드 시스템에 대해 폴더 열기 지원

::: moniker range="msvc-140"

폴더 열기 기능은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range=">=msvc-150"

Visual Studio 2017 이상에서 "폴더 열기" 기능을 통해 소스 파일의 폴더를 열고 IntelliSense, 검색, 리팩터링, 디버깅 등의 지원을 통해 코딩을 즉시 시작할 수 있습니다. 파일을 편집, 생성, 이동 또는 삭제하면 Visual Studio는 변경 내용을 자동으로 추적하고 해당 IntelliSense 인덱스를 계속해서 업데이트합니다. .sln 또는 .vcxproj 파일이 로드되지 않습니다. 필요한 경우 간단한 .json 파일을 통해 매개 변수를 작성하고 시작할 수 있을 뿐만 아니라 사용자 지정 작업을 지정할 수도 있습니다. 이 기능을 사용하면 모든 타사 빌드 시스템을 Visual Studio에 통합할 수 있습니다. 폴더 열기에 대한 일반적인 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)을 참조하세요.

## <a name="cmake-and-qt"></a>CMake 및 Qt

CMake는 C++ 데스크톱 워크로드의 구성 요소로 Visual Studio IDE에 통합됩니다. CMake의 워크플로는 이 문서에 설명된 워크플로와 동일하지 않습니다. CMake를 사용하는 경우 [Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)를 참조하세요. 또한 CMake를 사용하여 Qt 프로젝트를 만들거나 Visual Studio 2015 또는 Visual Studio 2017에 [Qt Visual Studio 확장](https://download.qt.io/development_releases/vsaddin/)을 사용할 수도 있습니다.

## <a name="other-build-systems"></a>기타 빌드 시스템

주 메뉴에서 직접 지원되지 않는 빌드 시스템 또는 컴파일러 도구 집함과 함께 Visual Studio IDE를 사용하려면 **파일 | 열기 | 폴더** 를 선택하거나 **Ctrl + Shift + Alt + O** 를 누릅니다. 소스 코드 파일이 포함된 폴더로 이동합니다. 프로젝트를 빌드하고 IntelliSense를 구성하고 디버깅 매개 변수를 설정하려면 다음 세 가지 JSON 파일을 추가합니다.

| 파일 | Description |
|-|-|
|CppProperties.json|검색에 대한 사용자 지정 구성 정보를 지정합니다. 필요한 경우 이 파일을 루트 프로젝트 폴더에 만듭니다. (CMake 프로젝트에서 사용되지 않습니다.)|
|tasks.vs.json|사용자 지정 빌드 명령을 지정합니다. **솔루션 탐색기** 의 상황에 맞는 메뉴 항목 **작업 구성** 을 통해 액세스합니다.|
|launch.vs.json|디버거의 명령줄 인수를 지정합니다. **솔루션 탐색기** 의 상황에 맞는 메뉴 항목 **디버그 및 시작 설정** 을 통해 액세스합니다.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>CppProperties.json을 사용하여 코드 탐색 구성

IntelliSense 및 검색 동작(예: **정의로 이동**)이 제대로 작동하려면 Visual Studio가 어떤 컴파일러가 사용되는지, 시스템 헤더가 어디에 위치하는지, 추가 포함 파일이 사용자가 연 폴더(작업 영역 폴더)에 없는 경우 어디에 위치하는지 알고 있어야 합니다. 구성을 지정하려면 기본 도구 모음의 드롭다운에서 **구성 관리** 를 선택할 수 있습니다.

![구성 관리 드롭다운](media/manage-configurations-dropdown.png)

Visual Studio는 다음과 같은 기본 구성을 제공합니다.

![기본 구성](media/default-configurations.png)

예를 들어 **x64-Debug** 를 선택하는 경우 Visual Studio는 루트 프로젝트 폴더에 *CppProperties.json* 이라는 파일을 만듭니다.

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

이 구성은 Visual Studio [x64 개발자 명령 프롬프트](building-on-the-command-line.md)의 환경 변수를 상속합니다. 이러한 변수 중 하나가 `INCLUDE`이며, `${env.INCLUDE}` 매크로를 사용하여 여기에서 이를 참조할 수 있습니다. `includePath` 속성은 Visual Studio에게 IntelliSense에 필요한 모든 원본을 찾을 수 있는 위치를 알려줍니다. 이 경우 "INCLUDE 환경 변수에 지정된 모든 디렉터리와 현재 작업 폴더 트리의 모든 디렉터리를 확인합니다."라고 표시됩니다. `name` 속성은 드롭다운에 표시되는 이름이며 원하는 모든 이름이 될 수 있습니다. `defines` 속성은 조건부 컴파일 블록이 발견될 때 IntelliSense에 힌트를 제공합니다. `intelliSenseMode` 속성은 컴파일러 유형에 따라 몇 가지 힌트를 추가로 제공합니다. MSVC, GCC 및 Clang에 몇 가지 옵션을 사용할 수 있습니다.

> [!NOTE]
> Visual Studio가 *CppProperties.json* 의 설정을 무시하는 것으로 보이는 경우 *.gitignore* 파일(예: `!/CppProperties.json`)에 예외를 추가해 보세요.

## <a name="default-configuration-for-mingw-w64"></a>MinGW-w64에 대한 기본 구성

MinGW-W64 구성을 추가하는 경우 JSON은 다음과 비슷합니다.

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
  ]
}
```

`environments` 블록에 유의하세요. 이 블록은 환경 변수처럼 동작하고 *CppProperties.json* 파일뿐 아니라 다른 구성 파일인 *task.vs.json* 및 *launch.vs.json* 에도 사용할 수 있는 속성을 정의합니다. `Mingw64` 구성은 `mingw_w64` 환경을 상속하며, `INCLUDE` 속성을 사용하여 `includePath`의 값을 지정합니다. 필요에 따라 이 배열 속성에 다른 경로를 추가할 수 있습니다.

`intelliSenseMode` 속성은 GCC에 적절한 값으로 설정됩니다. 이러한 속성에 대한 자세한 내용은 [CppProperties.json 스키마 참조](cppproperties-schema-reference.md)를 참조하세요.

모든 것이 제대로 작동하는 경우 한 형식 위로 마우스를 가져가면 GCC 헤더에서 IntelliSense가 표시됩니다.

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>IntelliSense 진단 사용

기대하는 IntelliSense가 표시되지 않는 경우 **도구** > **옵션** > **텍스트 편집기** > **C/C++**  > **고급** 으로 이동하고 **로깅 사용** 을 **`true`** 로 설정하여 문제를 해결할 수 있습니다. 먼저 **로깅 수준** 은 5로, **로깅 필터** 는 8로 설정해 보세요.

![진단 로깅](media/diagnostic-logging.png)

출력은 **출력 창** 으로 파이핑되고 *다음에서 출력 보기: Visual C++ 로그* 를 선택하면 표시됩니다. 출력에는 무엇보다 IntelliSense에서 사용하려는 실제 포함 경로의 목록이 포함됩니다. 이 경로가 *CppProperties.json* 의 경로와 일치하지 않으면 폴더를 닫고 캐시된 검색 데이터를 포함하는 *.vs* 하위 폴더를 삭제해 보세요.

### <a name="define-build-tasks-with-tasksvsjson"></a>tasks.vs.json으로 빌드 작업 정의

현재 작업 영역에 있는 파일에 대한 빌드 스크립트 또는 기타 외부 작업을 IDE에서 직접 작업으로 실행하여 자동화할 수 있습니다. 파일 또는 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 구성** 을 선택하여 새 작업을 구성할 수 있습니다.

![폴더 열기 구성 작업](media/configure-tasks.png)

이 작업은 Visual Studio가 루트 프로젝트 폴더에 만드는 .vs 폴더에서 *tasks.vs.json* 파일을 만들거나 엽니다. 이 파일에서 임의의 작업을 정의한 다음, 상황에 맞는 **솔루션 탐색기** 메뉴에서 호출할 수 있습니다. GCC 예제를 계속하기 위해 다음 코드 조각에서는 *g++.exe* 를 호출하여 프로젝트를 빌드하는 단일 작업으로 전체 *tasks.vs.json* 파일을 보여 줍니다. 이 프로젝트에 *hello.cpp* 라는 단일 파일이 포함되어 있다고 가정합니다.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

JSON 파일은 *.vs* 하위 폴더에 배치됩니다. 해당 폴더를 보려면 **솔루션 탐색기** 맨 위에 있는 **모든 파일 표시** 단추를 클릭합니다. **솔루션 탐색기** 에서 루트 노드를 마우스 오른쪽 단추로 클릭하고 **build hello** 를 선택하여 이 작업을 실행할 수 있습니다. 작업이 완료되면 **솔루션 탐색기** 에 새 파일 *hello.exe* 가 표시됩니다.

여러 종류의 작업을 정의할 수 있습니다. 다음 예제에서는 단일 작업을 정의하는 *tasks.vs.json* 파일을 보여 줍니다. `taskLabel`은 상황에 맞는 메뉴에 표시되는 이름을 정의합니다. `appliesTo`는 명령을 수행할 수 있는 파일을 정의합니다. `command` 속성은 콘솔에 대한 경로(Windows의 경우 *cmd.exe*)를 식별하는 COMSPEC 환경 변수를 참조합니다. CppProperties.json 또는 CMakeSettings.json에 선언된 환경 변수를 참조할 수도 있습니다. `args` 속성은 호출할 명령줄을 지정합니다. `${file}` 매크로는 **솔루션 탐색기** 에서 선택한 파일을 검색합니다. 다음 예제에서는 현재 선택된 .cpp 파일의 파일 이름을 표시합니다.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

*tasks.vs.json* 이 저장되면 폴더의 *.cpp* 파일을 마우스 오른쪽 단추로 클릭하고, 바로 가기 메뉴에서 **파일 이름 표시** 를 선택하여 출력 창에 표시된 파일 이름을 확인할 수 있습니다.

자세한 내용은 [Tasks.vs.json 스키마 참조](tasks-vs-json-schema-reference-cpp.md)를 참조하세요.

### <a name="configure-debugging-parameters-with-launchvsjson"></a>launch.vs.json으로 디버깅 매개 변수 구성

프로그램의 명령줄 인수 및 디버깅 명령을 사용자 지정하려면 **솔루션 탐색기** 에서 실행 파일을 마우스 오른쪽 단추로 클릭하고 **디버그 및 시작 설정** 을 선택합니다. 이렇게 하면 기존 *launch.vs.json* 파일이 열리며, 파일이 없는 경우에는 최소 시작 설정 집합을 사용하여 새 파일을 만듭니다. 먼저 구성하려는 디버그 세션의 종류를 선택할 수 있습니다. MinGw-w64 프로젝트를 디버깅하는 경우 **MinGW/Cygwin에 대한 C/C++ 시작(gdb)** 을 선택합니다. 이렇게 하면 기본값에 대한 몇 가지 학습된 추측과 함께 *gdb.exe* 를 사용하기 위한 시작 구성이 만들어집니다. 이러한 기본값 중 하나가 `MINGW_PREFIX`입니다. 아래에 표시된 대로 리터럴 경로를 바꾸거나 *CppProperties.json* 에서 `MINGW_PREFIX` 속성을 정의할 수 있습니다.

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

디버깅을 시작하려면 디버그 드롭다운에서 실행 파일을 선택한 다음 녹색 화살표를 클릭합니다.

![디버거 시작](media/launch-debugger-gdb.png)

**디버거 초기화** 대화 상자와 프로그램을 실행하는 외부 콘솔 창이 표시됩니다.

자세한 내용은 [launch.vs.json 스키마 참조](launch-vs-schema-reference-cpp.md)를 참조하세요.

## <a name="launching-other-executables"></a>다른 실행 파일 시작

컴퓨터의 모든 실행 파일에 대한 시작 설정을 정의할 수 있습니다. 다음 예제에서는 *7za* 를 시작하고 추가 인수를 `args` JSON 배열에 추가하여 지정합니다.

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

이 파일을 저장하면 [디버그 대상] 드롭다운에 새 구성이 표시되고 이 구성을 선택하여 디버거를 시작할 수 있습니다. 실행 파일의 개수에 관계없이 원하는 만큼 많은 수의 디버그 구성을 만들 수 있습니다. 이제 **F5** 키를 누르면 디버거가 시작되고 이미 설정한 모든 중단점에 적중됩니다. 그리고 친숙한 모든 디버거 창과 해당 기능을 사용할 수 있습니다.

::: moniker-end
