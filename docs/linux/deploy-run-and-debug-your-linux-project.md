---
title: Visual Studio에서 Linux MSBuild C++ 프로젝트 배포, 실행 및 디버그
description: Visual Studio에서 MSBuild 기반 C++ Linux 프로젝트로부터 원격 대상으로 코드를 컴파일하고, 실행하고, 디버그하는 방법을 설명합니다.
ms.date: 08/08/2020
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 4200e30b445f4a09fc60083db0067996c96ea953
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686706"
---
# <a name="deploy-run-and-debug-your-linux-msbuild-project"></a>Linux MSBuild 프로젝트 배포, 실행 및 디버그

::: moniker range="vs-2015"
Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다. 이러한 버전에 대한 설명서를 보려면 목차 위에 있는 **버전** 드롭다운을 **Visual Studio 2017** 또는 **Visual Studio 2019**로 설정합니다.
::: moniker-end

Visual Studio에서 MSBuild 기반 Linux C++ 프로젝트를 만들고 [Linux 연결 관리자](connect-to-your-remote-linux-computer.md)를 사용하여 프로젝트에 연결하면 해당 프로젝트를 실행하고 디버그할 수 있습니다. 원격 대상에서 코드를 컴파일, 실행 및 디버그합니다.

::: moniker range="vs-2019"

**Visual Studio 2019 버전 16.1** 디버깅 및 빌드에 다른 Linux 시스템을 대상으로 지정할 수 있습니다. 예를 들어 IoT 시나리오를 대상으로 하는 경우, x64에서 교차 컴파일하여 ARM 디바이스에 배포할 수 있습니다. 자세한 내용은 이 문서의 뒷부분에 있는 [빌드 및 디버깅에 다른 머신 지정](#separate_build_debug)을 참조하세요.

::: moniker-end

Linux 프로젝트를 조작하고 디버그할 수 있는 여러 가지 방법이 있습니다.

- 중단점, 조사식 창과 같은 기존의 Visual Studio 기능을 사용하여 변수를 마우스 단추로 가리켜 디버그합니다. 이러한 메서드를 사용하여 다른 프로젝트 형식에 사용하는 일반적인 방법으로 디버그할 수 있습니다.

- Linux 콘솔 창에서 대상 컴퓨터의 출력을 봅니다. 또한 콘솔을 사용하여 대상 컴퓨터에 입력을 보낼 수 있습니다.

## <a name="debug-your-linux-project"></a>Linux 프로젝트 디버그

1. **디버깅** 속성 페이지에서 디버깅 모드를 선택합니다.

   ::: moniker range="vs-2019"

   GDB는 Linux에서 실행되는 애플리케이션을 디버그하는 데 사용됩니다. 원격 시스템(WSL 아님)에서 디버깅할 때 GDB는 두 가지 모드에서 실행할 수 있고, 모드는 프로젝트의 **디버깅** 속성 페이지에 있는 **디버깅 모드** 옵션에서 선택할 수 있습니다.

   ![구성 속성 > 디버깅이 선택되고 디버깅 모드가 강조 표시되고 드롭다운 목록에서 GDB가 선택 및 강조 표시된 Visual Studio 2019 Linux 콘솔 앱 속성 페이지 대화 상자의 스크린샷](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB는 Linux에서 실행되는 애플리케이션을 디버그하는 데 사용됩니다. GDB는 두 가지 모드에서 실행할 수 있고, 모드는 프로젝트의 **디버깅** 속성 페이지에 있는 **디버깅 모드**에서 선택할 수 있습니다.

   ![구성 속성 > 디버깅이 선택되고 디버깅 모드가 강조 표시되고 드롭다운 목록에서 GDB가 선택 및 강조 표시된 Visual Studio 2017 Linux 콘솔 앱 속성 페이지 대화 상자의 스크린샷](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - **gdbserver** 모드에서 원격 시스템의 gdbserver에 연결된 GDB는 로컬에서 실행됩니다.

   - **gdb** 모드에서 Visual Studio 디버거는 원격 시스템에서 GDB를 구동합니다. GDB의 로컬 버전이 대상 컴퓨터에 설치된 버전과 호환되지 않을 경우 더 나은 옵션입니다. Linux 콘솔 창이 지원하는 모드는 이 모드뿐입니다.

   > [!NOTE]
   > gdbserver 디버깅 모드에서 중단점에 도달할 수 없는 경우 gdb 모드를 시도해 보세요. 우선 원격 대상에 gdb가 [설치](download-install-and-setup-the-linux-development-workload.md)되어 있어야 합니다.

1. Visual Studio에서 표준 **디버그** 도구 모음을 사용하여 원격 대상을 선택합니다.

   사용할 수 있는 원격 대상은 목록에 이름 또는 IP 주소로 표시됩니다.

   ![원격 대상](media/remote_target.png)

   아직 원격 대상에 연결하지 않은 경우 [Linux 연결 관리자](connect-to-your-remote-linux-computer.md)를 사용하여 원격 대상에 연결하라는 지침이 표시됩니다.

   ![원격 아키텍처](media/architecture.png)

1. 실행될 것을 알고 있는 일부 코드의 왼쪽 여백을 클릭하여 중단점을 설정합니다.

   중단점을 설정한 코드 줄에 빨간 점이 표시됩니다.

1. **F5** 키(또는 **디버그 > 디버깅 시작**)를 눌러 디버깅을 시작합니다.

   디버깅을 시작하면 애플리케이션이 시작되기 전에 원격 대상에서 컴파일됩니다. 모든 컴파일 오류는 **오류 목록** 창에 표시됩니다.

   오류가 없는 경우 앱이 시작되고 디버거가 중단점에서 일시 중지됩니다.

   ![중단점 도달](media/hit_breakpoint.png)

   이제 **F10** 또는 **F11** 키와 같은 명령 키를 눌러 현재 상태의 애플리케이션과 상호작용하고, 변수를 보고, 코드를 단계별로 상호작용할 수 있습니다.

1. Linux 콘솔을 사용하여 앱과 상호 작용하려면 **디버그 > Linux 콘솔**을 선택합니다.

   ![Linux 콘솔 메뉴](media/consolemenu.png)

   이 콘솔에서는 대상 컴퓨터의 콘솔 출력을 표시하고 입력을 받아들이고 대상 컴퓨터로 보냅니다.

   ![Linux 콘솔 창](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-projects"></a>다른 디버깅 옵션 구성(MSBuild 프로젝트)

- 프로젝트의 **디버깅** 속성 페이지에서 **프로그램 인수** 항목을 사용하여 명령줄 인수를 실행 파일에 전달할 수 있습니다.
- 프로젝트의 **디버깅** 속성 페이지에서 **사전 실행 명령**을 사용하여 `DISPLAY` 환경 변수를 내보낼 수 있습니다. 예: `export DISPLAY=:0.0`

   ![프로그램 인수](media/settings_programarguments.png)

- 특정 디버거 옵션은 **추가 디버거 명령** 항목을 통해 GDB에 전달될 수 있습니다.  예를 들어 SIGILL(잘못된 명령) 신호를 무시하고자 할 경우  위 그림처럼 **추가 디버거 명령** 항목에 다음 내용을 추가하면 **handle** 명령을 사용하여 이 작업을 수행할 수 있습니다.

   `handle SIGILL nostop noprint`

## <a name="debug-with-attach-to-process"></a>프로세스에 연결을 사용하여 디버그

Visual Studio 프로젝트에 대한 [디버깅](prop-pages/debugging-linux.md) 속성 페이지 및 CMake 프로젝트에 대한 **Launch.vs.json** 설정은 실행 중인 프로세스에 연결할 수 있도록 하는 설정을 갖습니다. 이러한 설정에 제공된 것 이외의 추가 컨트롤이 필요한 경우 솔루션 또는 작업 영역의 루트에 `Microsoft.MIEngine.Options.xml`이라는 파일을 배치할 수 있습니다. 다음은 간단한 예제입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection**에는 필요할 수 있는 대부분의 특성이 있습니다. 위의 예제에서는 추가 .so 라이브러리를 검색할 위치를 지정하는 방법을 보여 줍니다. 자식 요소 **ServerOptions**는 gdbserver를 대신 사용하여 원격 프로세스에 연결할 수 있습니다. 이렇게 하려면 기호를 사용하여 로컬 gdb 클라이언트(Visual Studio 2017에서 제공되는 것은 위에 표시됨) 및 이진 파일의 로컬 복사본을 지정해야 합니다. **SetupCommands** 요소를 통해 gdb에 직접 명령을 전달할 수 있습니다. GitHub의 [LaunchOptions.xsd 스키마](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd)에서 사용 가능한 모든 옵션을 찾을 수 있습니다.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging-in-msbuild-based-linux-projects"></a><a name="separate_build_debug"></a> MSBuild 기반 Linux 프로젝트에서 빌드 및 디버깅을 위해 다른 컴퓨터 지정

Visual Studio 2019 버전 16.1에서는 MSBuild 기반 Linux 프로젝트와 원격 Linux 머신을 대상으로 하는 CMake 프로젝트 둘 다에 대해, 원격 빌드 머신과 원격 디버그 머신을 분리할 수 있습니다. 예를 들어 IoT 시나리오를 대상으로 하는 경우, 이제 x64에서 교차 컴파일하여 ARM 디바이스에 배포할 수 있습니다.

기본적으로 원격 디버그 머신은 원격 빌드 머신과 같습니다(**구성 속성** > **일반** > **원격 빌드 머신**). 새 원격 디버그 머신을 지정하려면 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **구성 속성** > **디버깅** > **원격 디버그 머신**으로 이동합니다.  

![Linux 원격 디버그 머신](media/linux-remote-debug-machine.png)

**원격 디버그 머신**의 드롭다운 메뉴에는 설정된 원격 연결이 모두 채워져 있습니다. 새 원격 연결을 추가하려면 **도구** > **옵션** > **플랫폼 간** > **연결 관리자**로 이동하거나, **빠른 실행**에서 “연결 관리자”를 검색합니다. 프로젝트의 속성 페이지에서 새 원격 배포 디렉터리를 지정할 수도 있습니다(**구성 속성** > **일반** > **원격 배포 디렉터리**).

기본적으로 프로세스에서 디버그하는 데 필요한 파일만 원격 디버깅 머신에 배포됩니다. **솔루션 탐색기**를 사용하여 원격 디버그 머신에 배포할 소스 파일을 구성할 수 있습니다. 소스 파일을 클릭하면 솔루션 탐색기 바로 아래에 해당 파일 속성의 미리 보기가 표시됩니다.

![Linux 배포 가능 파일](media/linux-deployable-content.png)

**콘텐츠** 속성은 원격 디버그 머신에 파일을 배포할지 여부를 지정합니다. **속성 페이지** > **Configuration Manager**로 이동한 다음, 해당 구성의 **배포**를 선택 취소하면 배포를 완전히 해제할 수 있습니다.

프로젝트 배포를 더 세부적으로 제어해야 하는 경우도 있습니다. 예를 들어 배포하려는 파일 중 일부가 솔루션 외부에 있거나, 파일 또는 디렉터리별로 원격 배포 디렉터리를 사용자 지정하려고 합니다. 이러한 경우 .vcxproj 파일에 다음 코드 블록을 추가하고 “example.cpp”를 실제 파일 이름으로 바꿉니다.

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>CMake 프로젝트

원격 Linux 머신을 대상으로 하는 CMake 프로젝트의 경우 launch.vs.json에서 새 원격 디버그 머신을 지정할 수 있습니다. 기본적으로 “remoteMachineName” 값은 사용자의 원격 빌드 머신에 해당하는 CMakeSettings.json의 “remoteMachineName” 속성과 동기화됩니다. 이러한 속성은 더 이상 일치하지 않아도 되며, launch.vs.json의 “remoteMachineName” 값에 따라 배포 및 디버그에 사용되는 원격 머신이 결정됩니다.

![CMake 원격 디버그 머신](media/cmake-remote-debug-machine.png)

IntelliSense에서 설정된 모든 원격 연결 목록을 제안합니다. **도구** > **옵션** > **플랫폼 간** > **연결 관리자**로 이동하거나, **빠른 실행**에서 “연결 관리자”를 검색하면 새 원격 연결을 추가할 수 있습니다.

배포를 완전히 제어하려는 경우 launch.vs.json 파일에 다음 코드 블록을 추가할 수 있습니다. 자리 표시자 값을 실제 값으로 바꿔야 합니다.

```json
"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]
```

::: moniker-end

## <a name="next-steps"></a>다음 단계

- Linux에서 ARM 디바이스를 디버깅하려면 [Visual Studio에서 포함된 ARM 디바이스 디버깅](https://devblogs.microsoft.com/cppblog/debugging-an-embedded-arm-device-in-visual-studio/) 블로그 게시물을 참조하세요.

## <a name="see-also"></a>참고 항목

[C++ 디버깅 속성(Linux C++)](prop-pages/debugging-linux.md)
