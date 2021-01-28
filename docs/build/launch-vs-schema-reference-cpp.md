---
title: launch.vs.json 스키마 참조(C++)
description: '`launch.vs.json` 파일의 스키마 요소를 설명합니다.'
ms.date: 12/02/2020
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 0338f3c8c6bf9eff73a0464ad6c9aac777afacc2
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667454"
---
# <a name="launchvsjson-schema-reference-c"></a>launch.vs.json 스키마 참조(C++)

*launch.vs.json* 파일을 사용해 디버깅 매개 변수를 구성합니다. 파일을 만들려면 **솔루션 탐색기** 에서 실행 파일을 마우스 오른쪽 단추로 클릭하고 **디버깅 및 시작 설정** 을 선택합니다. 프로젝트와 가장 많이 일치하는 옵션을 선택한 후 다음 속성을 사용하여 필요에 따라 구성을 수정합니다. CMake 프로젝트 디버깅에 대한 자세한 내용은 [CMake 디버깅 세션 구성](./configure-cmake-debugging-sessions.md)을 참조하세요.

## <a name="default-properties"></a>기본 속성

|속성|유형|Description|
|-|-|-|
|`args`|array|시작된 프로그램에 전달되는 명령줄 인수를 지정합니다.|
|`buildConfigurations`|array| 빌드 모드 이름을 지정하여 구성을 적용하는 키-값 쌍입니다. 예: `Debug` 또는 `Release`과 선택한 빌드 모드에 따라 사용할 구성.
|`currentDir`|string|빌드 대상의 전체 디렉터리 경로를 지정합니다. 이 매개 변수가 설정되어 있지 않으면 자동으로 검색됩니다.|
|`cwd`|문자열|프로그램이 실행될 원격 시스템의 디렉터리에 대한 전체 경로입니다. 기본값은 `"${debugInfo.defaultWorkingDirectory}"`입니다.|
|`debugType`|string|코드의 형식(기본, 관리 또는 혼합)에 따라 디버깅 모드를 지정합니다. 이 매개 변수가 설정되어 있지 않으면 자동으로 검색됩니다. 허용되는 값은 `"native"`, `"managed"`, `"mixed"`입니다.|
|`env`|array| 사용자 지정 환경 변수의 키-값 목록을 지정합니다. 예: `env:{"myEnv":"myVal"}`.|
|`inheritEnvironments`|array|여러 원본에서 상속되는 환경 변수 집합을 지정합니다. *`CMakeSettings.json`* 또는 *`CppProperties.json`* 과 같은 파일에 일부 변수를 정의하고 디버그 컨텍스트에 사용할 수 있도록 설정할 수 있습니다.  **Visual Studio 16.4:** `env.VARIABLE_NAME` 구문을 사용하여 대상별로 환경 변수를 지정합니다. 변수를 설정 해제하려면 `"null"`로 설정합니다.|
|`name`|문자열|**시작 항목** 드롭다운에서 항목 이름을 지정합니다.|
|`noDebug`|boolean|시작된 프로그램을 디버그할지 여부를 지정합니다. 지정되지 않은 경우 이 매개 변수의 기본값은 **`false`** 입니다.|
|`portName`|string|실행 중인 프로세스에 연결할 때 포트 이름을 지정합니다.|
| `program`|문자열|실행할 디버그 명령입니다. 기본값은 `"${debugInfo.fullTargetPath}"`입니다.|
|`project`|string|프로젝트 파일의 상대 경로를 지정합니다. CMake 프로젝트를 디버깅할 때는 일반적으로 이 값을 변경하지 않아도 됩니다. |
|`projectTarget`|string|`project`를 빌드할 때 호출되는 선택적 대상을 지정합니다. 대상은 **시작 항목** 드롭다운의 이름과 일치해야 합니다.|
|`stopOnEntry`|boolean|프로세스가 시작되고 디버거가 연결되는 즉시 중단할지 여부를 지정합니다. 이 매개 변수의 기본값은 **`false`** 입니다.|
|`remoteMachine`|string|프로그램이 시작된 원격 컴퓨터의 이름을 지정합니다.|
|`type`|문자열|프로젝트가 `dll`인지, 아니면 `exe`인지 여부를 지정합니다. 기본값은 .exe입니다.|

## <a name="c-linux-properties"></a>C++ Linux 속성

|속성|형식|Description|
|-|-|-|
|`program`|문자열|원격 컴퓨터의 프로그램 실행 파일에 대한 전체 경로입니다. CMake를 사용하는 경우 이 필드의 값으로 `${debugInfo.fullTargetPath}`라는 매크로를 사용할 수 있습니다.|
|`processId`|integer|디버거를 연결할 선택적 프로세스 ID입니다.|
|`sourceFileMap`|개체|디버그 엔진에 전달되는 선택적 소스 파일 매핑입니다. 형식: `{ "\<Compiler source location>": "\<Editor source location>" }` 또는 `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. 예: `{ "/home/user/foo": "C:\\foo" }` 또는 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. [소스 파일 맵 옵션](#source_file_map_options)을 참조하세요.|
|`additionalProperties`|string|sourceFileMapOptions 중 하나입니다. 다음을 참조하세요.|
|`MIMode`|string|MIDebugEngine이 연결할 MI 지원 콘솔 디버거의 형식을 나타냅니다. 허용되는 값은 `"gdb"`, `"lldb"`입니다.|
|`args`|array|프로그램에 전달되는 명령줄 인수입니다.|
|`environment`|array|프로그램의 환경에 추가할 환경 변수입니다. 예: `[ { "name": "squid", "value": "clam" } ]`.|
|`targetArchitecture`|string|디버기의 아키텍처입니다. 이 매개 변수가 설정되어 있지 않으면 자동으로 검색됩니다. 허용되는 값은 `x86`, `arm`, `arm64`, `mips`, `x64`, `amd64`, `x86_64`입니다.|
|`visualizerFile`|string|이 프로세스를 디버그할 때 사용할 .natvis 파일입니다. 이 옵션은 GDB 자동 서식 지정과 호환되지 않습니다. 이 설정을 사용하는 경우 `"showDisplayString"`을 참조하세요.|
|`showDisplayString`|boolean|visualizerFile이 지정된 경우 `showDisplayString`은 표시 문자열을 사용하도록 설정합니다. 이 옵션을 활성화하면 디버깅 중에 성능이 저하될 수 있습니다.|
|`remoteMachineName`|string|Gdb를 호스팅하는 원격 Linux 컴퓨터와 디버그할 프로그램입니다. 새 Linux 머신을 추가하기 위해 연결 관리자를 사용합니다. CMake를 사용하는 경우 이 필드의 값으로 `${debugInfo.remoteMachineName}`이라는 매크로를 사용할 수 있습니다.|
|`miDebuggerPath`|string|MI 지원 디버거(예: gdb)의 경로입니다. 지정하지 않으면 디버거의 경로를 먼저 검색합니다.|
|`miDebuggerServerAddress`|string|연결할 MI 지원 디버거 서버의 네트워크 주소입니다. 예: localhost:1234|
|`setupCommands`|array|기본 디버거를 설정하기 위해 실행할 하나 이상의 GDB/LLDB 명령입니다. 예: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. [설치 명령 시작](#launch_setup_commands)을 참조하세요.|
|`customLaunchSetupCommands`|array|이것이 제공되면 대상을 시작하는 데 사용되는 기본 명령이 다른 명령으로 바뀝니다. 예를 들어 대상 프로세스에 연결하기 위한 “-target-attach”일 수 있습니다. 빈 명령 목록은 시작 명령을 어떤 것으로도 교체하지 않습니다. 이는 디버거가 명령줄 옵션으로 시작 옵션을 제공받는 경우에 유용할 수 있습니다. 예: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|string|디버거가 완전히 설정된 후 실행하여 대상 프로세스가 실행되게 하는 명령입니다. 허용되는 값은 "exec-run", "exec-continue", "None"입니다. 기본값은 "exec-run"입니다.|
|`debugServerPath`|string|시작할 디버그 서버의 선택적 전체 경로입니다. 기본값은 Null입니다.|
|`debugServerArgs`|string|선택적 디버그 서버 인수입니다. 기본값은 Null입니다.|
|`filterStderr`|boolean|서버에서 시작한 패턴을 stderr 스트림에서 검색하고, stderr을 디버그 출력에 기록합니다. 기본값은 **`false`** 입니다.|
|`coreDumpPath`|string|지정된 프로그램에 대한 코어 덤프 파일의 선택적 전체 경로입니다. 기본값은 Null입니다.|
externalConsole|boolean|true이면 디버기에 대해 콘솔이 시작됩니다. **`false`** 인 경우 콘솔이 시작되지 않습니다. 이 설정의 기본값은 **`false`** 입니다. 이 옵션은 어떤 경우 기술적인 이유로 인해 무시됩니다.|
|`pipeTransport`|string|있을 경우 디버거가 원격 컴퓨터에 연결할 때 Visual Studio와 MI 지원 디버거(예: gdb) 사이에 표준 입/출력을 릴레이하는 파이프와 다른 실행 파일을 사용하게 합니다. 허용되는 값: 하나 이상의 [파이프 전송 옵션](#pipe_transport_options).|

## <a name="c-windows-remote-debug-and-deploy-properties"></a><a name="remote_deploy_debug"></a> C++ Windows 원격 디버그 및 배포 속성

원격 머신에서 앱을 디버그하고 배포할 때 사용됩니다.

|속성|형식|Description|
|-|-|-|
|`cwd`|문자열|원격 컴퓨터에 있는 대상의 작업 디렉터리입니다. CMake를 사용하는 경우 이 필드의 값으로 `${debugInfo.defaultWorkingDirectory}`라는 매크로를 사용할 수 있습니다. 기본값은 디버그 프로그램/명령의 디렉터리입니다.|
|`deploy`|문자열|배포할 추가 파일 또는 디렉터리를 지정합니다. 예를 들면 다음과 같습니다.<br> `"deploy": {"sourcePath":"<Full path to source file/directory on host machine>", "targetPath":"<Full destination path to file/directory on target machine>"}` |
|`deployDirectory`|문자열|프로젝트 출력이 자동으로 배포되는 원격 머신의 위치입니다. 기본값은 `C:\Windows Default Deploy Directory\<name of app>`입니다.|
|`deployDebugRuntimeLibraries`|문자열|활성 플랫폼용 디버그 런타임 라이브러리를 배포할지 여부를 지정합니다. 활성 configurationType이 `"Debug"`인 경우 기본값은 `"true"`입니다.|
|`deployRuntimeLibraries`|문자열|활성 플랫폼용 런타임 라이브러리를 배포할지 여부를 지정합니다. 활성 configurationType이 `"MinSizeRel"`, `"RelWithDebInfo"` 또는 `"Release"`인 경우 기본값은 `"true"`입니다.|
|`disableDeploy` | boolean | 파일을 배포할지 여부를 지정합니다. |
|`remoteMachineName`|문자열|프로그램이 시작된 원격 ARM64 Windows 머신의 이름을 지정합니다. 서버 이름이거나 원격 머신의 IP 주소일 수 있습니다. |
|`authenticationType`|문자열|원격 연결 형식을 지정합니다. 가능한 값은 `"windows"` 및 `"none"`입니다. 기본값은 `"windows"`입니다. 원격 머신에서 실행 중인 원격 디버거에 지정된 인증 설정과 일치해야 합니다.|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a> 설치 명령 시작

`setupCommands` 속성과 함께 사용됨:

|속성|형식|Description|
|-|-|-|
|`text`|문자열|실행할 디버거 명령입니다.|
|`description`|string|명령에 대한 선택적 설명입니다.|
|`ignoreFailures`|boolean|true이면 명령의 오류가 무시됩니다. 기본값은 **`false`** 입니다.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a> 파이프 전송 옵션

`pipeTransport` 속성과 함께 사용됨:

|속성|형식|Description|
|-|-|-|
|`pipeCwd`|문자열|파이프 프로그램의 작업 디렉터리에 대한 정규화된 경로입니다.|
|`pipeProgram`|string|실행할 정규화된 파이프 명령입니다.|
|`pipeArgs`|array|연결을 구성하기 위해 파이프 프로그램에 전달되는 명령줄 인수입니다.|
|`debuggerPath`|string|대상 컴퓨터의 디버거에 대한 전체 경로(예: /usr/bin/gdb)입니다.|
|`pipeEnv`|개체|파이프 프로그램에 전달되는 환경 변수입니다.|
|`quoteArgs`|boolean|개별 인수에 공백이나 탭과 같은 문자를 포함하는 경우 따옴표로 묶어야 하나요? **`false`** 인 경우 디버거 명령이 더 이상 자동으로 따옴표로 묶이지 않습니다. 기본값은 **`true`** 입니다.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a> 소스 파일 맵 옵션

`sourceFileMap` 속성과 함께 사용:

|속성|형식|Description|
|-|-|-|
|`editorPath`|문자열|편집기에서 찾을 소스 코드의 위치입니다.|
|`useForBreakpoints`|boolean|중단점을 설정할 때 이 소스 매핑을 사용해야 합니다. **`false`** 인 경우 중단점 설정에 파일 이름과 줄 숫자만 사용됩니다. **`true`** 인 경우 이 소스 매핑이 사용되는 경우에만 파일의 전체 경로와 줄 번호를 사용해 중단점이 설정됩니다. 아니면 중단점을 설정할 때 파일 이름과 줄 번호만 사용합니다. 기본값은 **`true`** 입니다.|
