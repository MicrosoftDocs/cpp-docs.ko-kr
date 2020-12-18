---
description: '자세한 정보: tasks.vs.json 스키마 참조(++)'
title: tasks.vs.json 스키마 참조(C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 1fd4cfb960afa1260c8ea85c0e7fe9274c77ac68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275323"
---
# <a name="tasksvsjson-schema-reference-c"></a>tasks.vs.json 스키마 참조(C++)

열려 있는 폴더 프로젝트에서 소스 코드를 빌드하는 방법을 Visual Studio에 알리기 위해 *tasks.vs.json* 파일을 추가합니다. 이 파일에서 임의의 작업을 정의한 다음 **솔루션 탐색기** 바로 가기 메뉴에서 호출할 수 있습니다. 모든 빌드 명령은 *CMakeLists.txt* 에 지정되어 있기 때문에 CMake 프로젝트는 이 파일을 사용하지 않습니다. CMake 이외의 빌드 시스템의 경우 *tasks.vs.json* 에서 빌드 명령을 지정하고 빌드 스크립트를 호출할 수 있습니다. *tasks.vs.json* 사용에 대한 일반적인 정보는 [“폴더 열기” 개발에 대한 빌드 및 디버그 작업 사용자 지정](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)을 참조하세요.

작업에는 `default`, `launch`, `remote` 또는 `msbuild`의 네 가지 값 중 하나를 가질 수 있는 `type` 속성이 있습니다. 원격 연결이 필요하지 않는 한 대부분의 작업은 `launch`를 사용해야 합니다.

## <a name="default-properties"></a>기본 속성

기본 속성은 모든 유형의 작업에서 사용할 수 있습니다.

|속성|유형|Description|
|-|-|-|
|`taskLabel`|문자열| (필수) 사용자 인터페이스에 사용되는 작업 레이블을 지정합니다.|
|`appliesTo`|string| (필수) 명령이 수행될 수 있는 파일을 지정합니다. 와일드카드 사용이 지원됩니다(예: “ *”, “* .cpp”, “/*.txt”).|
|`contextType`|string| 허용되는 값: “custom”, “build”, “clean”, “rebuild”. 바로 가기 메뉴에서 작업이 표시되는 위치를 결정합니다. 기본값은 “custom”입니다.|
|`output`|string| 작업에 출력 태그를 지정합니다.|
|`inheritEnvironments`|array| 여러 소스에서 상속되는 환경 변수 집합을 지정합니다. *CMakeSettings.json* 또는 *CppProperties.json* 과 같은 파일에 변수를 정의하고 작업 컨텍스트에 사용하도록 할 수 있습니다. **Visual Studio 16.4:** : `env.VARIABLE_NAME` 구문을 사용하여 작업별로 환경 변수를 지정합니다. 변수를 설정 해제하려면 변수를 “Null”로 설정합니다.|
|`passEnvVars`|boolean| 작업 컨텍스트에 추가 환경 변수를 포함할지를 지정합니다. 관련 변수는 `envVars` 속성을 사용하여 정의된 변수와 다릅니다. 기본값은 “true”입니다.|

## <a name="launch-properties"></a>시작 속성

작업 유형이 `launch`인 경우 다음 속성을 사용할 수 있습니다.

|속성|유형|Description|
|-|-|-|
|`command`|문자열| 시작할 프로세스나 스크립트의 전체 경로를 지정합니다.|
|`args`|array| 명령에 전달되는 쉼표로 구분된 인수 목록을 지정합니다.|
|`launchOption`|string| 허용되는 값은 다음과 같습니다. “None”, “ContinueOnError”,”IgnoreError”. 오류가 있는 경우 명령을 사용하여 진행하는 방법을 지정합니다.|
|`workingDirectory`|string| 명령이 실행될 디렉터리를 지정합니다. 프로젝트의 현재 작업 디렉터리에 대한 기본값입니다.|
|`customLaunchCommand`|string| 명령을 실행하기 전에 적용할 전역 범위 사용자 지정을 지정합니다. %PATH%와 같은 환경 변수를 설정하는 데 유용합니다.|
|`customLaunchCommandArgs`|string| CustomLaunchCommand에 대한 인수를 지정합니다. `customLaunchCommand`가 필요합니다.|
 `env`| 사용자 지정 환경 변수의 키-값 목록을 지정합니다. 예: “myEnv”: “Myenv”|
|`commands`|array| 순서대로 호출할 명령의 목록을 지정합니다.|

### <a name="example"></a>예제

다음 작업은 [Cppproperties.json 스키마 참조](cppproperties-schema-reference.md#user_defined_environments)에 표시된 대로 메이크파일이 폴더에 제공되고 `Mingw64` 환경이 *Cppproperties.json* 에 정의된 경우 *make.exe* 를 호출합니다.

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

관련 작업은 **솔루션 탐색기** 에서 *.cpp* 파일을 마우스 오른쪽 단추로 클릭하면 바로 가기 메뉴에서 호출할 수 있습니다.

## <a name="remote-properties"></a>원격 속성

C++ 워크로드를 사용하여 Linux 개발을 설치하고 Visual Studio 연결 관리자를 사용하여 원격 컴퓨터에 연결을 추가하면 원격 작업이 활성화됩니다. 원격 작업은 원격 시스템에서 명령을 실행하고 여기에 파일을 복사할 수도 있습니다.

작업 유형이 `remote`인 경우 다음 속성을 사용할 수 있습니다.

|속성|유형|Description|
|-|-|-|
|`remoteMachineName`|문자열|원격 컴퓨터의 이름입니다. **연결 관리자** 의 컴퓨터 이름과 일치해야 합니다.|
|`command`|string|원격 컴퓨터에 보낼 명령입니다. 기본적으로 명령은 원격 시스템의 $HOME 디렉터리에서 실행됩니다.|
|`remoteWorkingDirectory`|string|원격 컴퓨터의 현재 작업 디렉터리입니다.|
|`localCopyDirectory`|string|원격 컴퓨터에 복사할 로컬 디렉터리입니다. 기본값은 현재 작업 디렉터리입니다.|
|`remoteCopyDirectory`|string|`localCopyDirectory`가 복사되는 원격 컴퓨터의 디렉터리입니다.|
|`remoteCopyMethod`|string| 복사에 사용할 메서드입니다. 허용되는 값: “none”, “sftp”, “rsync”. 대규모 프로젝트에는 rsync를 권장합니다.|
|`remoteCopySourcesOutputVerbosity`|string| 허용되는 값은 다음과 같습니다. “Normal”,”Verbose”,”Diagnostic”.|
|`rsyncCommandArgs`|string|“-t --delete”에 대한 기본값입니다.|
|`remoteCopyExclusionList`|array|`localCopyDirectory`에서 복사 작업에서 제외되는 쉼표로 구분된 파일 목록입니다.|

### <a name="example"></a>예제

다음 작업은 **솔루션 탐색기** 에서 *main.cpp* 를 마우스 오른쪽 단추로 클릭하면 바로 가기 메뉴에 표시됩니다. **연결 관리자** 에서 `ubuntu`라는 원격 컴퓨터에 종속됩니다. 작업은 Visual Studio에서 현재 열려 있는 폴더를 원격 컴퓨터의 `sample` 디렉터리로 복사한 다음 g++를 호출하여 프로그램을 빌드합니다.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>MSBuild 속성

작업 유형이 `msbuild`인 경우 다음 속성을 사용할 수 있습니다.

|속성|유형|Description|
|-|-|-|
|`verbosity`|문자열| MSBuild 프로젝트 빌드 출력 verbosityAllowed 값을 지정합니다. “Quiet”, “Minimal”, “Normal”, “Detailed”, “Diagnostic”.|
|`toolsVersion`|string| 프로젝트를 빌드할 도구 집합 버전을 지정합니다(예: “2.0”, “3.5”, “4.0”, “Current”). 기본값은 “Current”입니다.|
|`globalProperties`|개체|프로젝트에 전달할 전역 속성의 키-값 목록을 지정합니다(예: “Configuration”: “Release”).|
|`properties`|개체| 추가 프로젝트 전용 속성의 키-값 목록을 지정합니다.|
|`targets`|array| 프로젝트에서 순서대로 호출할 대상 목록을 지정합니다. 아무것도 지정하지 않으면 프로젝트의 기본 대상이 사용됩니다.|
