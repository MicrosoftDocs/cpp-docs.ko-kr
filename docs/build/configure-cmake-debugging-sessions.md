---
title: Visual Studio에서 CMake 디버깅 세션 구성
description: Visual Studio를 사용하여 CMake 디버거 설정을 구성하는 방법을 설명합니다.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 74be1f07b838cd77f4ee87f5e9d245410fe716de
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440298"
---
# <a name="configure-cmake-debugging-sessions"></a>CMake 디버깅 세션 구성

::: moniker range="msvc-140"

원시 CMake 지원은 Visual Studio 2017 이상에서 제공됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end

::: moniker range=">=msvc-150"

실행 가능한 모든 CMake 대상은 **일반** 도구 모음의 **시작 항목** 드롭다운에 표시됩니다. 하나를 선택하여 디버깅 세션을 시작하고 디버거를 시작합니다.

![CMake 시작 항목 드롭다운](media/cmake-startup-item-dropdown.png "CMake 시작 항목 드롭다운")

솔루션 탐색기에서 디버그 세션을 시작할 수도 있습니다. 먼저 **솔루션 탐색기** 창에서 **CMake 대상 뷰** 로 전환합니다.

![CMake 대상 보기 단추](media/cmake-targets-view.png  "CMake 대상 뷰 메뉴 항목")

그런 다음, 실행 파일을 마우스 오른쪽 단추로 클릭하고 **디버그** 를 선택합니다. 이 명령을 통해 활성 구성에 따라 선택된 대상의 디버깅이 자동으로 시작됩니다.

## <a name="customize-debugger-settings"></a>디버거 설정 사용자 지정

프로젝트의 모든 실행 가능한 CMake 대상에 대한 디버거 설정을 사용자 지정할 수 있습니다. 이러한 설정은 프로젝트 루트의 *`.vs`* 폴더에 있는 *launch.vs.json* 이라는 구성 파일에 있습니다. 디버깅 설정 세부 정보를 구성하고 저장할 수 있으므로 시작 구성 파일은 대부분의 디버깅 시나리오에서 유용합니다. 이 파일에는 세 가지 진입점이 있습니다.

- **디버그 메뉴:** 주 메뉴에서 **디버그 > ${activeDebugTarget}에 대한 디버그 및 시작 설정** 을 선택하여 활성 디버그 대상과 관련된 디버그 구성을 사용자 지정합니다. 디버그 대상을 선택하지 않은 경우 이 옵션은 회색으로 표시됩니다.

![디버그 메뉴 진입점](media/cmake-debug-menu.png "디버그 메뉴 진입점")

- **대상 뷰:** 솔루션 탐색기에서 **대상 뷰** 로 이동합니다. 그런 다음, 디버그 대상을 마우스 오른쪽 단추로 클릭하고 **디버그 구성 추가** 를 선택하여 선택한 대상과 관련된 디버그 구성을 사용자 지정합니다.

![대상 뷰 진입점](media/cmake-targets-add-debug-configuration.png "대상 뷰 진입점")

- **루트 CMakeLists.txt:** 루트 *CMakeLists.txt* 를 마우스 오른쪽 단추로 클릭하고 **디버그 구성 추가** 를 선택하여 **디버거 선택** 대화 상자를 엽니다. 대화 상자에서 *모든* 형식의 디버그 구성을 추가할 수 있지만, `projectTarget` 속성을 통해 호출할 CMake 대상을 수동으로 지정해야 합니다.

![디버거 대화 상자 선택](media/cmake-select-a-debugger.png "디버거 대화 상자 선택")

*launch.vs.json* 파일을 편집하여 임의 개수의 CMake 대상에 대해 디버그 구성을 만들 수 있습니다. 파일을 저장하면 Visual Studio는 **시작 항목** 드롭다운에서 새 구성 각각에 대해 항목을 만듭니다.

## <a name="reference-keys-in-cmakesettingsjson"></a>CMakeSettings.json의 참조 키

*CMakeSettings.json* 파일의 모든 키를 참조하려면 *launch.vs.json* 에서 키 앞에 `cmake.`를 추가하세요. 다음 예제에서는 *CMakeSettings.json* 파일에서 현재 선택한 구성에 대한 `remoteCopySources` 키 값을 가져오는 간단한 *launch.vs.json* 파일을 보여줍니다.

```json
{
  "version": "0.2.1",
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

*CMakeSettings.json* 에 정의되어 있는 **환경 변수** 는 `${env.VARIABLE_NAME}` 구문을 사용하여 launch.vs.json에서도 사용할 수 있습니다. Visual Studio 2019 버전 16.4 이상에서는 *CMakeSettings.json* 에서 지정하는 환경을 사용하여 자동으로 디버그 대상이 시작됩니다. 환경 변수를 **Null** 로 설정하면 설정 해제됩니다.

## <a name="launchvsjson-reference"></a>Launch.vs.json 참조

모든 디버깅 시나리오를 지원할 수 있는 다양한 *launch.vs.json* 속성이 있습니다. 다음 속성은 원격 및 로컬의 모든 디버그 구성에 공통된 것입니다.

- `projectTarget`: 프로젝트를 빌드할 때 호출할 CMake 대상을 지정합니다. **디버그 메뉴** 또는 **대상 뷰** 에서 *launch.vs.json* 을 입력하면 Visual Studio는 이 속성을 자동으로 채웁니다. 이 값은 **시작 항목** 드롭다운에 나열된 기존 디버그 대상의 이름과 일치해야 합니다.

- `env`: 구문을 사용하여 추가할 부가적인 환경 변수:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: 디버그할 프로그램에 전달되는 명령줄 인수입니다.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>원격 프로젝트 및 WSL에 대한 Launch.vs.json 참조

Visual Studio 2019 버전 16.6에서는 원격 시스템 및 WSL에서의 디버깅을 간소화하기 위해 `type: cppgdb`의 새 디버그 구성을 추가했습니다. `type: cppdbg`의 이전 디버그 구성은 계속 지원됩니다.

### <a name="configuration-type-cppgdb"></a>구성 형식`cppgdb`

- `name`: **시작 항목** 드롭다운에서 구성을 식별하기 위한 식별 이름입니다.
- `project`: 프로젝트 파일의 상대 경로를 지정합니다. CMake 프로젝트를 디버깅할 때는 일반적으로 이 경로를 변경하지 않아도 됩니다.
- `projectTarget`: 프로젝트를 빌드할 때 호출할 CMake 대상을 지정합니다. **디버그 메뉴** 또는 **대상 뷰** 에서 *launch.vs.json* 을 입력하면 Visual Studio는 이 속성을 자동으로 채웁니다. 이 대상 값은 **시작 항목** 드롭다운에 나열된 기존 디버그 대상의 이름과 일치해야 합니다.
- `debuggerConfiguration`: 사용할 디버깅 기본값 집합을 나타냅니다. Visual Studio 2019 버전 16.6에서 유일하게 유효한 옵션은 `gdb`입니다. Visual Studio 2019 버전 16.7 이상도 `gdbserver`를 지원합니다.
- `args`: 시작할 때 디버그 중인 프로그램에 전달되는 명령줄 인수입니다.
- `env`: 디버그 중인 프로그램에 전달되는 부가적인 환경 변수입니다. 예: `{"DISPLAY": "0.0"}`.
- `processID`: 연결할 Linux 프로세스 ID입니다. 원격 프로세스에 연결하는 경우에만 사용됩니다. 자세한 내용은 [GDB를 사용하여 프로세스에 연결할 때 발생하는 문제 해결](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)을 참조하세요.

#### <a name="additional-options-for-the-gdb-configuration"></a>`gdb` 구성을 위한 부가적 옵션입니다.

- `program`: 기본값은 `"${debugInfo.fullTargetPath}"`입니다. 디버그할 애플리케이션의 Unix 경로입니다. 빌드 또는 배포 위치의 대상 실행 파일과 다른 경우에만 필요합니다.
- `remoteMachineName`: 기본값은 `"${debugInfo.remoteMachineName}"`입니다. 디버그할 프로그램을 호스팅하는 원격 시스템의 이름입니다. 빌드 시스템과 다른 경우에만 필요합니다. [연결 관리자](../linux/connect-to-your-remote-linux-computer.md)에 기존 항목이 있어야 합니다. **Ctrl+Space** 를 눌러 모든 기존 원격 연결의 목록을 표시합니다.
- `cwd`: 기본값은 `"${debugInfo.defaultWorkingDirectory}"`입니다. `program`이 실행되는 원격 시스템의 디렉터리에 대한 Unix 경로입니다. 디렉터리가 있어야 합니다.
- `gdbpath`: 기본값은 `/usr/bin/gdb`입니다. 디버깅하는 데 사용되는 `gdb`에 대한 전체 Unix 경로입니다. `gdb`의 사용자 지정 버전을 사용하는 경우에만 필요합니다.
- `preDebugCommand`: `gdb`를 호출하기 직전에 실행할 Linux 명령입니다. 명령이 완료될 때까지 `gdb`는 시작되지 않습니다. `gdb`를 실행하기 전에 옵션을 사용하여 스크립트를 실행할 수 있습니다.

#### <a name="additional-options-allowed-with-the-gdbserver-configuration-167-or-later"></a>`gdbserver` 구성에서 허용되는 추가 옵션(16.7 이상)

- `program`: 기본값은 `"${debugInfo.fullTargetPath}"`입니다. 디버그할 애플리케이션의 Unix 경로입니다. 빌드 또는 배포 위치의 대상 실행 파일과 다른 경우에만 필요합니다.
- `remoteMachineName`:  기본값은 `"${debugInfo.remoteMachineName}"`입니다. 디버그할 프로그램을 호스팅하는 원격 시스템의 이름입니다. 빌드 시스템과 다른 경우에만 필요합니다. [연결 관리자](../linux/connect-to-your-remote-linux-computer.md)에 기존 항목이 있어야 합니다. **Ctrl+Space** 를 눌러 모든 기존 원격 연결의 목록을 표시합니다.
- `cwd`: 기본값은 `"${debugInfo.defaultWorkingDirectory}"`입니다. `program`이 실행되는 원격 시스템의 디렉터리에 대한 전체 Unix 경로입니다. 디렉터리가 있어야 합니다.
- `gdbPath`: 기본값은 `${debugInfo.vsInstalledGdb}`입니다. 디버그하는 데 사용되는 `gdb`의 전체 Windows 경로입니다. C/C++ 워크로드를 사용하여 Linux 개발과 함께 설치된 `gdb`가 기본값입니다.
- `gdbserverPath`: 기본값은 `usr/bin/gdbserver`입니다. 디버깅하는 데 사용되는 `gdbserver`에 대한 전체 Unix 경로입니다.
- `preDebugCommand`: `gdbserver`를 시작하기 직전에 실행할 Linux 명령입니다. 명령이 완료될 때까지 `gdbserver`는 시작되지 않습니다.

#### <a name="deployment-options"></a>배포 옵션

다음 옵션을 사용하여 원격 디버그 컴퓨터에서 빌드 컴퓨터(CMakeSettings.json에 정의되어 있음)를 분리하세요.

- `remoteMachineName`: 원격 디버깅 컴퓨터입니다. 빌드 컴퓨터와 다른 경우에만 필요합니다. [연결 관리자](../linux/connect-to-your-remote-linux-computer.md)에 기존 항목이 있어야 합니다. **Ctrl+Space** 를 눌러 모든 기존 원격 연결의 목록을 표시합니다.
- `disableDeploy`: 기본값은 **`false`** 입니다. 빌드/디버그 분리가 사용할 수 없는 상태인지 여부를 나타냅니다. **`false`** 인 경우 이 옵션을 사용하면 서로 분리된 두 컴퓨터에서 빌드 및 디버그가 수행되게 할 수 있습니다.
- `deployDirectory`: 실행 파일을 복사할 `remoteMachineName`의 해당 디렉터리에 대한 전체 Unix 경로입니다.
- `deploy`: 고급 배포 설정의 배열입니다. 배포 프로세스를 더 세부적으로 제어하려는 경우에만 이러한 설정을 구성해야 합니다. 기본적으로 프로세스에서 디버그하는 데 필요한 파일만 원격 디버깅 컴퓨터에 배포됩니다.
  - `sourceMachine`: 복사되는 파일이나 디렉터리가 있는 컴퓨터입니다. **Ctrl+Space** 를 누르면 연결 관리자에 저장된 모든 원격 연결의 목록이 표시됩니다. WSL에서 기본적으로 빌드하는 경우 이 옵션은 무시됩니다.
  - `targetMachine`: 파일이나 디렉터리가 복사되는 대상 컴퓨터입니다. **Ctrl+Space** 를 누르면 연결 관리자에 저장된 모든 원격 연결의 목록이 표시됩니다.
  - `sourcePath`: `sourceMachine`에 있는 파일 또는 디렉터리 위치입니다.
  - `targetPath`: `targetMachine`에 있는 파일 또는 디렉터리 위치입니다.
  - `deploymentType`: 배포 유형에 대한 설명입니다. `LocalRemote`와 `RemoteRemote`가 지원됩니다. `LocalRemote`는 로컬 파일 시스템에서 *launch.vs.json* 의 `remoteMachineName`가 지정하는 원격 시스템으로 복사하는 것을 뜻합니다. `RemoteRemote`는 *CMakeSettings.json* 에 지정된 원격 빌드 시스템에서 *launch.vs.json* 에 지정된 다른 원격 시스템으로 복사하는 것을 뜻합니다.
  - `executable`: 배포된 파일이 실행 파일인지 여부를 나타냅니다.

### <a name="execute-custom-gdb-commands"></a>사용자 지정 `gdb` 명령 실행

Visual Studio에서는 사용자 지정 `gdb` 명령을 실행하여 기본 디버거와 직접 상호 작용할 수 있도록 지원합니다. 자세한 내용은 [사용자 지정 `gdb` lldb 명령 실행](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)을 참조하세요.

### <a name="enable-logging"></a>로깅 사용

MIEngine 로깅을 사용하여 `gdb`로 전송되는 명령, `gdb`가 반환하는 출력, 각 명령이 실행되는 데 걸리는 시간을 확인할 수 있습니다. [자세히](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>구성 형식 `cppdbg`

`cppdbg` 구성 형식을 사용하여 원격 시스템 또는 WSL에서 디버그할 때 다음 옵션을 사용할 수 있습니다. Visual Studio 2019 버전 16.6 이상에서는 `cppgdb` 구성 형식이 권장됩니다.

- `name`: **시작 항목** 드롭다운에서 구성을 식별하기 위한 식별 이름입니다.

- `project`: 프로젝트 파일의 상대 경로를 지정합니다. CMake 프로젝트를 디버깅할 때는 일반적으로 이 값을 변경하지 않아도 됩니다.

- `projectTarget`: 프로젝트를 빌드할 때 호출할 CMake 대상을 지정합니다. **디버그 메뉴** 또는 **대상 뷰** 에서 *launch.vs.json* 을 입력하면 Visual Studio는 이 속성을 자동으로 채웁니다. 이 값은 **시작 항목** 드롭다운에 나열된 기존 디버그 대상의 이름과 일치해야 합니다.

- `args`: 시작할 때 디버그 중인 프로그램에 전달되는 명령줄 인수입니다.

- `processID`: 연결할 Linux 프로세스 ID입니다. 원격 프로세스에 연결하는 경우에만 사용됩니다. 자세한 내용은 [GDB를 사용하여 프로세스에 연결할 때 발생하는 문제 해결](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)을 참조하세요.

- `program`: 기본값은 `"${debugInfo.fullTargetPath}"`입니다. 디버그할 애플리케이션의 Unix 경로입니다. 빌드 또는 배포 위치의 대상 실행 파일과 다른 경우에만 필요합니다.

- `remoteMachineName`:  기본값은 `"${debugInfo.remoteMachineName}"`입니다. 디버그할 프로그램을 호스팅하는 원격 시스템의 이름입니다. 빌드 시스템과 다른 경우에만 필요합니다. [연결 관리자](../linux/connect-to-your-remote-linux-computer.md)에 기존 항목이 있어야 합니다. **Ctrl+Space** 를 눌러 모든 기존 원격 연결의 목록을 표시합니다.

- `cwd`: 기본값은 `"${debugInfo.defaultWorkingDirectory}"`입니다. `program`이 실행되는 원격 시스템의 디렉터리에 대한 전체 Unix 경로입니다. 디렉터리가 있어야 합니다.

- `environment`: 디버그 중인 프로그램에 전달되는 부가적인 환경 변수입니다. 예를 들면 다음과 같습니다.

  ```json
    "environment": [
        {
          "name": "ENV1",
          "value": "envvalue1"
        },
        {
          "name": "ENV2",
          "value": "envvalue2"
        }
      ]
  ```

- `pipeArgs`: 연결을 구성하기 위해 파이프 프로그램에 전달되는 명령줄 인수의 배열입니다. 파이프 프로그램은 Visual Studio와 `gdb` 간에 표준 입력/출력을 릴레이하는 데 사용됩니다. CMake 프로젝트를 디버깅할 때 이 배열의 대부분은 **사용자 지정할 필요가 없습니다**. 단, 원격 시스템에서 `gdb`를 시작하는 `${debuggerCommand}`는 예외입니다. 다음과 같이 수정할 수 있습니다.

  - Linux 시스템에 있는 DISPLAY 환경 변수의 값을 내보냅니다. 다음 예제에서는 이 값이 `:1`입니다.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "export DISPLAY=:1;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

  - `gdb`를 실행하기 전에 스크립트를 실행합니다. 스크립트에 실행 권한이 설정되어 있는지 확인합니다.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: 프로세스가 시작되는 즉시 중단할지 여부를 지정하는 부울입니다. 기본값은 false입니다.

- `visualizerFile`: 이 프로세스를 디버그할 때 사용할 [.natvis 파일](/visualstudio/debugger/create-custom-views-of-native-objects)입니다. 이 옵션은 `gdb` 자동 서식 지정과 호환되지 않습니다. 또한 이 속성을 설정할 때 `showDisplayString`을 설정합니다.

- `showDisplayString`: `visualizerFile`이 지정된 경우 표시 문자열을 사용 하도록 설정하는 부울입니다. 이 옵션을 **`true`** 로 설정하면 디버그하는 동안 성능이 저하될 수 있습니다.

- `setupCommands`: 기본 디버거를 설정하기 위해 실행할 하나 이상의 `gdb` 명령입니다.

- `miDebuggerPath`: `gdb`의 전체 경로입니다. 지정하지 않으면 Visual Studio에서 디버거를 위해 먼저 경로를 검색합니다.

- 마지막으로, `cppgdb` 구성 형식에 대해 정의된 모든 배포 옵션도 `cppdbg` 구성 형식에서 사용할 수 있습니다.

### <a name="debug-using-gdbserver"></a>`gdbserver`를 사용해 디버그하기

`gdbserver`를 사용하여 디버그하도록 `cppdbg` 구성을 구성할 수 있습니다. 자세한 내용과 샘플 시작 구성은 Microsoft C++ 팀 블로그 게시물인 [`gdbserver`를 사용하여 Linux CMake 프로젝트 디버깅](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)에서 확인할 수 있습니다.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="see-also"></a>참조

[Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)\
[Linux CMake 프로젝트 구성](../linux/cmake-linux-project.md)\
[원격 Linux 컴퓨터에 연결](../linux/connect-to-your-remote-linux-computer.md)\
[CMake 빌드 설정 사용자 지정](customize-cmake-settings.md)\
[CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)\
[Linux 프로젝트 배포, 실행 및 디버그](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)

::: moniker-end
