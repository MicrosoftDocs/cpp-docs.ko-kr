---
title: Visual Studio에서 C++ 플랫폼 간 프로젝트 만들기
description: Linux 및 Windows를 대상으로 하는 Visual Studio에서 C++ 오픈 소스 CMake 프로젝트를 설정하고, 컴파일하고, 디버그하는 방법.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: c420e0ee04e85d49ad752da085d38b2c5ff9d4fa
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344659"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>자습서: Visual Studio에서 C++ 플랫폼 간 프로젝트 만들기

Windows에서는 더 이상 Visual Studio C 및 C++ 개발을 지원하지 않습니다. 이 자습서에서는 Windows 및 Linux에서 C++ 플랫폼 간 개발에 Visual Studio를 사용하는 방법을 보여줍니다. CMake 기반이므로 Visual Studio 프로젝트를 만들거나 생성할 필요가 없습니다. CMakeLists.txt 파일이 포함된 폴더를 열 때 Visual Studio는 IntelliSense 및 빌드 설정을 자동으로 구성합니다. Windows에서 코드를 로컬로 편집, 빌드, 디버깅하는 작업을 신속하게 시작할 수 있습니다. 그런 다음 Linux에서 동일한 작업을 모두 Visual Studio 내에서 수행하도록 구성을 전환합니다.

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.

> [!div class="checklist"]
>
> * GitHub에서 오픈 소스 CMake 프로젝트 복제
> * Visual Studio에서 프로젝트 열기
> * Windows에서 실행 파일 대상 빌드 및 디버그
> * Linux 머신에 대한 연결 추가
> * Linux에서 동일한 대상 빌드 및 디버그

## <a name="prerequisites"></a>사전 요구 사항

* 플랫폼 간 C++ 개발용 Visual Studio 설정
  * 먼저 [Visual Studio를 설치](https://visualstudio.microsoft.com/vs/)하고 **C++를 사용한 데스크톱 개발** 및 **C++ 워크로드를 사용한 Linux 개발** 을 선택합니다. 이 최소 설치는 3GB밖에 안 됩니다. 다운로드 속도에 따라 설치는 10분 이상 걸리지 않습니다.

* 플랫폼 간 C++ 개발용 Linux 머신 설정
  * Visual Studio에는 특정 버전의 Linux가 필요하지 않습니다. OS는 물리적 컴퓨터, VM 또는 클라우드에서 실행될 수 있습니다. Linux용 Windows 하위 시스템(WSL)을 사용할 수도 있습니다. 그러나 이 자습서에서는 그래픽 환경이 필요합니다. 여기서는 명령줄 작업에 주로 사용되기 때문에 WSL은 사용하지 않는 것이 좋습니다.
  * Linux 컴퓨터에서 Visual Studio에 필요한 도구는 다음과 같습니다. C++ 컴파일러, gdb, ssh, rsync, make, zip. Debian 기반 시스템에서는 이 명령을 사용하여 다음과 같은 종속성을 설치할 수 있습니다.

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync make zip
    ```

  * Visual Studio는 서버 모드를 사용하도록 설정(3.8 이상)한 Linux 컴퓨터에 최신 버전의 CMake가 있어야 합니다. Microsoft에서는 모든 Linux 배포판에 설치할 수 있는 CMake의 유니버설 빌드를 제공합니다. 이 빌드를 사용하여 최신 기능이 설치되어 있는지 확인하는 것이 좋습니다. GitHub의 [CMake 리포지토리의 Microsoft 포크](https://github.com/Microsoft/CMake/releases)에서 CMake 이진 파일을 가져올 수 있습니다. 이 페이지로 이동하여 Linux 컴퓨터에 시스템 아키텍처와 일치하는 버전을 다운로드한 다음, 실행 파일로 표시합니다.

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * `-–help`를 사용하여 스크립트를 실행하는 옵션을 확인할 수 있습니다. `–prefix` 옵션을 사용하여 **/usr** 경로에 설치하도록 지정하는 것이 좋습니다. **/usr/bin** 이 Visual Studio에서 CMake를 찾는 기본 위치이기 때문입니다. 다음 예제에서는 Linux-x86_64 스크립트를 보여줍니다. 다른 대상 플랫폼을 사용하는 경우 필요에 따라 변경하세요.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Windows 머신에 설치된 Windows용 Git
* GitHub 계정

## <a name="clone-an-open-source-cmake-project-from-github"></a>GitHub에서 오픈 소스 CMake 프로젝트 복제

이 자습서에서는 GitHub의 글머리 기호 물리학 SDK를 사용하고, 여러 애플리케이션에 대한 충돌 검색 및 물리학 시뮬레이션을 제공합니다. SDK에는 추가 코드를 작성할 필요 없이 컴파일하고 실행하는 실행 파일 프로그램 샘플이 포함됩니다. 이 자습서에서는 소스 코드를 수정하거나 스크립트를 빌드하지 않습니다. 작업을 시작하려면 Visual Studio를 설치한 컴퓨터의 GitHub으로부터 *bullet3* 리포지토리를 복제합니다.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Visual Studio 주 메뉴에서 **파일 > 열기 > CMake** 를 차례로 선택합니다. 방금 다운로드한 bullet3 리포지토리의 루트에서 CMakeLists.txt 파일로 이동합니다.

    ![파일 > 열기 > CMake의 Visual Studio 메뉴](media/cmake-open-cmake.png)

    폴더를 열면 즉시 **솔루션 탐색기** 에 폴더 구조체가 표시됩니다.

    ![Visual Studio 솔루션 탐색기 폴더 보기](media/cmake-bullet3-solution-explorer.png)

    이 보기에서는 논리적 보기 또는 필터링된 보기가 아니라 디스크에 표시된 내용을 정확하게 보여줍니다. 기본적으로 숨겨진 파일을 표시하지 않습니다.

1. **모든 파일 표시** 단추를 선택하여 폴더에 있는 모든 파일을 확인하세요.

    ![Visual Studio 솔루션 탐색기 모든 파일 표시 단추](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>대상 보기로 전환

CMake를 사용하는 폴더를 열 때 Visual Studio에서는 자동으로 CMake 캐시를 생성합니다. 프로젝트의 크기에 따라 이 작업은 몇 분 정도가 걸릴 수 있습니다.

1. **출력 창** 에서 **출력 보기 대상** 을 선택한 다음, **CMake** 를 선택하여 캐시 생성 프로세스의 상태를 모니터링합니다. 작업이 완료되면 "대상 정보 추출 완료"라는 메시지가 표시됩니다.

   ![CMake의 출력을 보여주는 Visual Studio 출력 창](media/cmake-bullet3-output-window.png)

   이 작업이 완료되면 IntelliSense가 구성됩니다. 프로젝트를 빌드하고 애플리케이션을 디버그할 수 있습니다. 이제 Visual Studio에는 CMakeLists 파일에 지정된 대상에 따라 솔루션의 논리적 보기가 표시됩니다.

1. **솔루션 탐색기** 에서 **솔루션 및 폴더** 단추를 사용하여 CMake 대상 보기로 전환합니다.

   ![CMake 대상 보기를 보여주는 솔루션 탐색기의 솔루션 및 폴더 단추](media/cmake-bullet3-show-targets.png)

   글머리 기호 SDK에서 해당 보기가 표시된 내용은 다음과 같습니다.

   ![솔루션 탐색기 CMake 대상 보기](media/cmake-bullet3-targets-view.png)

   대상 보기는 이 원본 자료에 포함된 내용보다 직관적인 보기를 제공합니다. 일부 대상은 라이브러리이고 다른 대상은 실행 파일임을 확인할 수 있습니다.

1. 해당 파일이 디스크의 어디에 있든지에 관계 없이 CMake 대상 보기에서 노드를 확장하여 해당 소스 코드 파일을 확인하세요.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>명시적 Windows x64-Debug 구성 추가

Visual Studio는 Windows에 대한 기본 **x64-Debug** 구성을 만듭니다. 구성을 통해 Visual Studio가 CMake에서 사용하려는 대상 플랫폼을 이해할 수 있습니다. 기본 구성은 디스크에 표시되지 않습니다. 구성을 명시적으로 추가하는 경우 Visual Studio는 *CMakeSettings.json* 이라는 파일을 만듭니다. 이 파일은 지정하는 모든 구성에 대한 설정으로 채워져 있습니다.

1. 새 구성을 추가합니다. 도구 모음에서 **구성** 드롭다운을 열고 **구성 관리** 를 선택합니다.

   ![구성 관리 드롭다운](media/cmake-bullet3-manage-configurations.png)

   [CMake 설정 편집기](customize-cmake-settings.md)가 열립니다. 편집기 왼쪽에 있는 녹색 플러스 기호를 선택하여 새 구성을 추가합니다. **CMakeSettings에 구성 추가** 대화 상자가 나타납니다.

   ![CMakeSettings에 구성 추가 대화 상자](media/cmake-bullet3-add-configuration-x64-debug.png)

   이 대화 상자에서는 사용자가 만드는 모든 사용자 지정 구성뿐 아니라 Visual Studio에서 제공되는 모든 구성도 보여줍니다. **x64-Debug** 구성을 계속 사용하려면 해당 구성이 첫 번째로 추가한 구성이어야 합니다. **x64-Debug** 를 선택한 다음, **선택** 단추를 선택합니다. Visual Studio는 **x64-디버그** 에 대한 구성을 사용하여 CMakeSettings.json 파일을 만들어 디스크에 저장합니다. CMakeSettings.json에서 직접 이름 매개 변수를 변경하여 구성에 대해 원하는 이름을 사용할 수 있습니다.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Windows에서 중단점, 빌드 및 실행 설정

이 단계에서는 글머리 기호 물리학 라이브러리를 보여주는 예제 프로그램을 디버깅합니다.
  
1. **솔루션 탐색기** 에서 AppBasicExampleGui를 선택하고 확장합니다.

1. `BasicExample.cpp` 파일을 엽니다.

1. 실행 중인 애플리케이션을 클릭할 때 적중될 중단점을 설정합니다. 클릭 이벤트는 도우미 클래스 내의 메서드에서 처리됩니다. 신속하게 수행하려면:

   1. `BasicExample` 구조체가 파생되는 `CommonRigidBodyBase`를 선택합니다. 약 30줄입니다.

   1. **정의로 이동** 을 마우스 오른쪽 단추로 클릭하고 선택합니다. 이제 CommonRigidBodyBase.h 헤더로 이동한 상태입니다.

   1. 소스 위의 브라우저 보기를 통해 `CommonRigidBodyBase`로 이동한 상태임을 확인할 수 있어야 합니다. 오른쪽에서 검사할 멤버를 선택할 수 있습니다. 드롭다운을 열고 `mouseButtonCallback`을 선택하여 헤더에서 해당 함수의 정의로 이동합니다.

      ![Visual Studio 멤버 목록 도구 모음](media/cmake-bullet3-member-list-toolbar.png)

1. 이 함수의 첫 번째 줄에 중단점을 배치합니다. 애플리케이션이 Visual Studio 디버거에서 실행될 때 애플리케이션 창에 있는 마우스 단추를 클릭하면 이 중단점이 적중됩니다.

1. 애플리케이션을 시작하려면 도구 모음에서 시작 드롭다운을 선택합니다. "시작 항목 선택"이라는 녹색 재생 아이콘이 있는 것입니다. 드롭다운에서 AppBasicExampleGui.exe를 선택합니다. 이제 실행 파일 이름이 시작 단추에 표시됩니다.

   ![시작 항목 선택의 Visual Studio 도구 모음 시작 드롭다운](media/cmake-bullet3-launch-button.png)

1. 시작 단추를 선택하여 애플리케이션과 필요한 종속성을 빌드한 다음, 연결된 Visual Studio 디버거를 사용하여 시작하세요. 몇 분 후에 실행 중인 애플리케이션이 다음과 같이 표시됩니다.

   ![Windows 애플리케이션을 디버깅하는 Visual Studio](media/cmake-bullet3-launched.png)

1. 애플리케이션 창으로 마우스를 이동시킨 다음, 중단점을 트리거하는 단추를 클릭하세요. 그러면 중단점이 Visual Studio를 다시 전경으로 가져오고 편집기에는 실행이 일시 중지된 줄이 표시됩니다. 대화형으로 코드를 통해 애플리케이션 변수, 개체, 스레드, 메모리 또는 단계를 검사할 수 있습니다. **계속** 을 선택하여 애플리케이션이 다시 시작되게 한 다음, 정상적으로 종료합니다. 또는 중지 단추를 사용하여 Visual Studio 내에서 실행을 중지합니다.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Linux 구성 추가 및 원격 머신에 연결

1. Linux 구성을 추가합니다. **솔루션 탐색기** 보기에서 CMakeSettings.json 파일을 마우스 오른쪽 단추로 클릭하고 **구성 추가** 를 선택합니다. 이전과 동일한 CMakeSettings에 구성 추가 대화 상자가 표시됩니다. 이번에는 **Linux-Debug** 를 선택한 다음, CMakeSettings.json 파일을 저장(ctrl + s)합니다.

1. **Visual Studio 2019 버전 16.6 이상** CMake 설정 편집기 맨 아래로 스크롤하고 **고급 설정 표시** 를 선택합니다. **Unix 메이크파일** 을 **CMake 생성기** 로 선택한 다음 CMakeSettings.json 파일을 저장합니다(ctrl + s).

1. 구성 드롭다운에서 **Linux-Debug** 를 선택합니다.

   ![X64-Debug 및 Linux-Debug 옵션을 포함한 구성 시작 드롭다운](media/cmake-bullet3-linux-configuration-item.png)

   처음으로 Linux 시스템에 연결하는 경우 **원격 시스템에 연결** 대화 상자가 나타납니다.

   ![Visual Studio 원격 시스템에 연결 대화 상자](media/cmake-bullet3-connection-manager.png)

   원격 연결을 이미 추가한 경우 **도구 > 옵션 > 플랫폼 간 > 연결 관리자** 로 이동하여 이 창을 열 수 있습니다.

1. [Linux 컴퓨터에 연결 정보](../linux/connect-to-your-remote-linux-computer.md)를 제공하고 **연결** 을 선택합니다. Visual Studio는 이 컴퓨터를 CMakeSettings.json처럼 **Linux-Debug** 에 대한 기본 연결로 추가합니다. 또한 원격 컴퓨터에서 헤더를 가져오므로 [이 원격 연결에 고유한 IntelliSense](../linux/configure-a-linux-project.md#remote_intellisense)를 얻게 됩니다. 그런 다음, Visual Studio는 원격 컴퓨터에 파일을 보내고 원격 시스템에 CMake 캐시를 생성합니다. 이러한 단계는 네트워크 속도와 원격 컴퓨터의 기능에 따라 다소 시간이 걸릴 수 있습니다. CMake 출력 창에 "대상 정보 추출 완료" 메시지가 나타나면 이 작업이 완료되었음을 알 수 있습니다.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Linux에서 중단점, 빌드 및 실행 설정

데스크톱 애플리케이션이기 때문에 디버그 구성에 일부 추가 구성 정보를 입력해야 합니다.

1. CMake 대상 보기에서 AppBasicExampleGui를 마우스 오른쪽 단추로 클릭하고 **디버그 및 시작 설정** 을 선택하여 숨은 **.vs** 하위 폴더에 있는 launch.vs.json 파일을 엽니다. 이 파일은 개발 환경에서 로컬에 위치합니다. 팀에서 파일을 확인하고 저장하려는 경우 프로젝트의 루트로 이동시킬 수 있습니다. 이 파일에서 AppBasicExampleGui에 대한 구성이 추가되었습니다. 이러한 기본 설정은 대부분의 경우 작동하지만 여기서는 작동하지 않습니다. 데스크톱 애플리케이션이기 때문에 프로그램을 시작하려면 몇 가지 추가 정보를 입력해야 합니다. 그러면 Linux 컴퓨터에서 이 프로그램을 볼 수 있습니다.

1. Linux 컴퓨터에서 `DISPLAY` 환경 변수의 값을 알아보려면 이 명령을 실행하세요.

   ```cmd
   echo $DISPLAY
   ```

   AppBasicExampleGui의 구성에는 "pipeArgs" 매개 변수 배열이 있습니다. 그 안에는 "${debuggerCommand}" 줄이 있습니다. 이것은 원격 컴퓨터에서 gdb를 시작하는 명령입니다. Visual Studio는 이 명령이 실행되기 전에 이 컨텍스트에 표시를 내보내야 합니다. 예를 들어 표시의 값이 `:1`인 경우 해당 줄을 다음과 같이 수정하세요.

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. 애플리케이션을 시작하고 디버그합니다. 도구 모음에서 **시작 항목 선택** 드롭다운을 열고 **AppBasicExampleGui** 를 선택합니다. 그런 다음, 도구 모음에서 녹색 재생 아이콘을 선택하거나 **F5** 를 누릅니다. 그러면 애플리케이션과 애플리케이션의 종속성이 원격 Linux 컴퓨터에서 빌드되고, 이어서 연결된 Visual Studio 디버거로 시작됩니다. 원격 Linux 머신에 애플리케이션 창이 표시됩니다.

1. 애플리케이션 창으로 마우스를 이동한 다음, 단추를 클릭합니다. 중단점이 적중됩니다. 프로그램 실행이 일시 중지되고, Visual Studio가 전경에 표시되고, 중단점이 보입니다. Linux 콘솔 창도 Visual Studio에 나타납니다. 이 창은 원격 Linux 컴퓨터의 출력을 표시하고 `stdin`의 입력을 수락할 수도 있습니다. 모든 Visual Studio 창과 마찬가지로 이 창은 표시하고 싶은 위치에 고정할 수 있습니다. 한 번 정한 위치는 향후 세션에서 지속됩니다.

   ![Visual Studio Linux 콘솔 창](media/cmake-bullet3-linux-console.png)

1. Visual Studio를 사용하여 대화형으로 코드를 통해 애플리케이션 변수, 개체, 스레드, 메모리 및 단계를 검사할 수 있습니다. 하지만 이번에는 로컬 Windows 환경 대신 원격 Linux 컴퓨터에서 모든 작업을 수행합니다. **계속** 을 선택하여 애플리케이션이 다시 시작되었다가 정상적으로 종료되게 하거나 로컬 실행처럼 중지 단추를 선택할 수 있습니다.

1. Visual Studio가 Linux에서 애플리케이션을 시작한 이후에 호출 스택 창을 살펴보고 `x11OpenGLWindow`에 대한 호출을 보세요.

   ![Linux 호출 스택을 보여주는 호출 스택 창](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>학습 내용

이 자습서에서는 GitHub에서 직접 코드 베이스를 복제했습니다. 수정 없이 Windows에서 빌드하고 실행하고 디버그했습니다. 그런 다음, 약간의 구성 변경과 함께 이 코드 베이스를 원격 Linux 컴퓨터에서 빌드하고, 실행하고, 디버그했습니다.

## <a name="next-steps"></a>다음 단계

Visual Studio에서 CMake 프로젝트를 구성하고 디버깅하는 방법을 자세히 알아봅니다.

> [!div class="nextstepaction"]
> [Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)<br/><br/>
> [Linux CMake 프로젝트 구성](../linux/cmake-linux-project.md)<br/><br/>
> [원격 Linux 컴퓨터에 연결](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [CMake 빌드 설정 사용자 지정](customize-cmake-settings.md)<br/><br/>
> [CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)<br/><br/>
> [Linux 프로젝트 배포, 실행 및 디버그](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)
>
