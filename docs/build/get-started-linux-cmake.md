---
title: Visual Studio에서 C++ 플랫폼 간 프로젝트 만들기
description: Linux와 Windows를 모두 대상으로 하는 Visual Studio에서 C++ 오픈 소스 CMake 프로젝트를 설정, 컴파일 및 디버깅하는 방법
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328751"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>자습서: Visual Studio에서 C++ 크로스 플랫폼 프로젝트 만들기

Windows에서는 더 이상 Visual Studio C 및 C++ 개발을 지원하지 않습니다. 이 자습서에서는 Windows 및 Linux에서 C++ 교차 플랫폼 개발에 Visual Studio를 사용하는 방법을 보여 주십니다. CMake를 기반으로 하므로 Visual Studio 프로젝트를 만들거나 생성할 필요가 없습니다. CMakeLists.txt 파일이 포함된 폴더를 열면 Visual Studio에서 IntelliSense를 구성하고 설정을 자동으로 빌드합니다. Windows에서 로컬로 코드를 편집, 빌드 및 디버깅을 빠르게 시작할 수 있습니다. 그런 다음, 모든 비주얼 스튜디오 내에서, 리눅스에서 동일한 작업을 수행 하도록 구성을 전환.

이 자습서에서는 다음 작업 방법을 알아봅니다.

> [!div class="checklist"]
>
> * GitHub에서 오픈 소스 CMake 프로젝트 복제
> * Visual Studio에서 프로젝트 열기
> * Windows에서 실행 파일 대상 빌드 및 디버그
> * Linux 머신에 대한 연결 추가
> * Linux에서 동일한 대상 빌드 및 디버그

## <a name="prerequisites"></a>사전 요구 사항

* 플랫폼 간 C++ 개발용 Visual Studio 설정
  * 먼저 [Visual Studio를 설치하고](https://visualstudio.microsoft.com/vs/) **C++ 워크로드를 사용하여 C++** 및 Linux 개발을 사용하여 데스크톱 **개발을 선택합니다.** 이 최소 설치는 3GB에 불과합니다. 다운로드 속도에 따라 설치에 10분 이상 걸리지 않아야 합니다.

* 플랫폼 간 C++ 개발용 Linux 머신 설정
  * Visual Studio에는 특정 버전의 Linux가 필요하지 않습니다. OS는 물리적 컴퓨터, VM 또는 클라우드에서 실행할 수 있습니다. 또한 리눅스 (WSL)에 대 한 Windows 하위 시스템을 사용할 수 있습니다. 그러나 이 자습서에서는 그래픽 환경이 필요합니다. WSL은 주로 명령줄 작업을 위한 것이기 때문에 여기에 권장되지 않습니다.
  * 비주얼 스튜디오는 리눅스 컴퓨터에 이러한 도구가 필요합니다 : C ++ 컴파일러, gdb, ssh, rsync, 닌자, 그리고 우편. 데비안 기반 시스템에서는 이 명령을 사용하여 다음 종속성을 설치할 수 있습니다.

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio에는 서버 모드가 활성화된 Linux 컴퓨터에서 최신 버전의 CMake가 필요합니다(최소 3.8). Microsoft에서는 모든 Linux 배포판에 설치할 수 있는 CMake의 유니버설 빌드를 제공합니다. 이 빌드를 사용하여 최신 기능이 있는지 확인하는 것이 좋습니다. GitHub의 [CMake 리포지토리의 Microsoft 포크](https://github.com/Microsoft/CMake/releases)에서 CMake 이진 파일을 가져올 수 있습니다. 해당 페이지로 이동하여 Linux 컴퓨터에서 시스템 아키텍처와 일치하는 버전을 다운로드한 다음 실행 항목으로 표시합니다.

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * `-–help`를 사용하여 스크립트를 실행하는 옵션을 확인할 수 있습니다. `–prefix` **/usr/bin은** Visual Studio에서 CMake를 찾는 기본 위치이므로 **/usr** 경로에 설치를 지정하는 옵션을 사용하는 것이 좋습니다. 다음 예제에서는 Linux-x86_64 스크립트를 보여줍니다. 다른 대상 플랫폼을 사용하는 경우 필요에 따라 변경합니다.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Windows 머신에 설치된 Windows용 Git
* GitHub 계정.

## <a name="clone-an-open-source-cmake-project-from-github"></a>GitHub에서 오픈 소스 CMake 프로젝트 복제

이 자습서에서는 GitHub에서 글머리 기호 물리SDK를 사용합니다. 그것은 많은 응용 프로그램에 대한 충돌 감지 및 물리 시뮬레이션을 제공합니다. SDK에는 추가 코드를 작성하지 않고도 컴파일하고 실행하는 샘플 실행 프로그램이 포함되어 있습니다. 이 자습서는 소스 코드를 수정하거나 스크립트를 빌드하지 않습니다. 시작하려면 Visual Studio가 설치된 컴퓨터에서 GitHub에서 *bullet3* 리포지토리를 복제합니다.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Visual Studio 메인 메뉴에서 **파일 > 열기 > CMake를**선택합니다. 방금 다운로드한 bullet3 리포지토리의 루트에 있는 CMakeLists.txt 파일로 이동합니다.

    ![파일 > 열기 > CMake의 Visual Studio 메뉴](media/cmake-open-cmake.png)

    폴더를 열면 폴더 구조가 **솔루션 탐색기**에서 표시됩니다.

    ![Visual Studio 솔루션 탐색기 폴더 보기](media/cmake-bullet3-solution-explorer.png)

    이 보기에서는 논리적 보기 또는 필터링된 보기가 아니라 디스크에 표시된 내용을 정확하게 보여줍니다. 기본적으로 숨겨진 파일을 표시하지 않습니다.

1. **폴더의** 모든 파일을 보려면 모든 파일 표시 단추를 선택합니다.

    ![Visual Studio 솔루션 탐색기 모든 파일 표시 단추](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>대상 보기로 전환

CMake를 사용하는 폴더를 열 때 Visual Studio에서는 자동으로 CMake 캐시를 생성합니다. 프로젝트의 크기에 따라 이 작업은 몇 분 정도가 걸릴 수 있습니다.

1. **출력 창**에서 **출력 보기 대상**을 선택한 다음, **CMake**를 선택하여 캐시 생성 프로세스의 상태를 모니터링합니다. 작업이 완료되면 "대상 정보 추출 완료"라는 메시지가 표시됩니다.

   ![CMake의 출력을 보여주는 Visual Studio 출력 창](media/cmake-bullet3-output-window.png)

   이 작업이 완료되면 IntelliSense가 구성됩니다. 프로젝트를 빌드하고 응용 프로그램을 디버깅할 수 있습니다. 이제 Visual Studio에서 CMakeLists 파일에 지정된 대상을 기반으로 솔루션의 논리적 보기를 표시합니다.

1. **솔루션 탐색기**에서 **솔루션 및 폴더** 단추를 사용하여 CMake 대상 보기로 전환합니다.

   ![CMake 대상 보기를 보여주는 솔루션 탐색기의 솔루션 및 폴더 단추](media/cmake-bullet3-show-targets.png)

   글머리 기호 SDK에서 해당 보기가 표시된 내용은 다음과 같습니다.

   ![솔루션 탐색기 CMake 대상 보기](media/cmake-bullet3-targets-view.png)

   대상 보기는 이 원본 자료에 포함된 내용보다 직관적인 보기를 제공합니다. 일부 대상은 라이브러리이고 다른 대상은 실행 파일임을 확인할 수 있습니다.

1. 해당 파일이 디스크의 어디에 있든지에 관계 없이 CMake 대상 보기에서 노드를 확장하여 해당 소스 코드 파일을 확인하세요.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>명시적 Windows x64-Debug 구성 추가

Visual Studio는 Windows용 기본 **x64-디버그** 구성을 만듭니다. 구성을 통해 Visual Studio가 CMake에서 사용하려는 대상 플랫폼을 이해할 수 있습니다. 기본 구성은 디스크에 표시되지 않습니다. 구성을 명시적으로 추가하면 Visual Studio에서 *CMakeSettings.json*이라는 파일을 만듭니다. 지정한 모든 구성에 대한 설정으로 채워집니다.

1. 새 구성을 추가합니다. 도구 모음에서 **구성** 드롭다운을 열고 **구성 관리를 선택합니다.**

   ![구성 관리 드롭다운](media/cmake-bullet3-manage-configurations.png)

   [CMake 설정 편집기가](customize-cmake-settings.md) 열립니다. 편집기 왼쪽에 있는 녹색 및 기호를 선택하여 새 구성을 추가합니다. **CMakeSettings에 구성 추가** 대화 상자가 나타납니다.

   ![CMakeSettings에 구성 추가 대화 상자](media/cmake-bullet3-add-configuration-x64-debug.png)

   이 대화 상자에는 Visual Studio에 포함된 모든 구성과 만드는 사용자 지정 구성이 표시됩니다. **x64-디버그** 구성을 계속 사용하려면 첫 번째 구성이 어야 합니다. **x64-디버그를**선택한 다음 **선택** 단추를 선택합니다. Visual Studio는 **x64-디버그에**대한 구성으로 CMakeSettings.json 파일을 만들고 디스크에 저장합니다. CMakeSettings.json에서 직접 이름 매개 변수를 변경하여 구성에 대해 원하는 이름을 사용할 수 있습니다.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Windows에서 중단점 설정, 빌드 및 실행

이 단계에서는 글머리 기호 물리학 라이브러리를 보여주는 예제 프로그램을 디버깅합니다.
  
1. **솔루션 탐색기**에서 AppBasicExampleGui를 선택하고 확장합니다.

1. `BasicExample.cpp`파일을 엽니다.

1. 실행 중인 응용 프로그램을 클릭할 때 적중되는 중단점을 설정합니다. 클릭 이벤트는 도우미 클래스 내의 메서드에서 처리됩니다. 신속하게 수행하려면:

   1. 구조체에서 `CommonRigidBodyBase` `BasicExample` 파생되는 것을 선택합니다. 30호선 주변에 있습니다.

   1. **정의로 이동**을 마우스 오른쪽 단추로 클릭하고 선택합니다. 이제 커먼리지드바디베이스.h 의 헤더에 있습니다.

   1. 소스 위의 브라우저 보기에서 `CommonRigidBodyBase`에 있는 것을 볼 수 있습니다. 오른쪽에서 검사할 멤버를 선택할 수 있습니다. 드롭다운을 열고 헤더에서 해당 함수의 정의로 이동하도록 선택합니다. `mouseButtonCallback`

      ![Visual Studio 멤버 목록 도구 모음](media/cmake-bullet3-member-list-toolbar.png)

1. 이 함수의 첫 번째 줄에 중단점을 배치합니다. Visual Studio 디버거에서 실행할 때 응용 프로그램 창 내에서 마우스 단추를 클릭하면 적중됩니다.

1. 응용 프로그램을 실행하려면 도구 모음에서 시작 드롭다운을 선택합니다. 그것은 "시작 항목 선택"이라는 녹색 재생 아이콘이있는 것입니다. 드롭다운에서 AppBasicExampleGui.exe를 선택합니다. 이제 실행 파일 이름이 시작 단추에 표시됩니다.

   ![시작 항목 선택의 Visual Studio 도구 모음 시작 드롭다운](media/cmake-bullet3-launch-button.png)

1. 시작 단추를 선택하여 응용 프로그램 및 필요한 종속성을 빌드한 다음 Visual Studio 디버거가 연결된 것으로 시작합니다. 몇 분 후에 실행 중인 애플리케이션이 다음과 같이 표시됩니다.

   ![Windows 애플리케이션을 디버깅하는 Visual Studio](media/cmake-bullet3-launched.png)

1. 애플리케이션 창으로 마우스를 이동시킨 다음, 중단점을 트리거하는 단추를 클릭하세요. 중단점은 Visual Studio를 포그라운드로 다시 가져오고 편집기는 실행이 일시 중지된 줄을 표시합니다. 응용 프로그램 변수, 개체, 스레드 및 메모리를 검사하거나 코드를 대화형으로 단계별로 검사할 수 있습니다. **계속을** 선택하여 응용 프로그램이 다시 시작하도록 한 다음 정상적으로 종료합니다. 또는 중지 단추를 사용하여 Visual Studio 내에서 실행을 중지합니다.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Linux 구성 추가 및 원격 머신에 연결

1. Linux 구성을 추가합니다. **솔루션 탐색기** 보기에서 CMakeSettings.json 파일을 마우스 오른쪽 단추로 클릭하고 **구성 추가**를 선택합니다. 이전과 동일한 CMakeSettings에 구성 추가 대화 상자가 표시됩니다. 이번에는 **Linux-디버깅을** 선택한 다음 CMakeSettings.json 파일(ctrl + s)을 저장합니다.

1. 구성 드롭다운에서 **Linux-디버그를** 선택합니다.

   ![X64-Debug 및 Linux-Debug 옵션을 포함한 구성 시작 드롭다운](media/cmake-bullet3-linux-configuration-item.png)

   Linux 시스템에 처음 연결하는 경우 **원격 시스템에 연결** 대화 상자가 나타납니다.

   ![Visual Studio 원격 시스템에 연결 대화 상자](media/cmake-bullet3-connection-manager.png)

   원격 연결을 이미 추가한 경우 **플랫폼 간 연결 관리자를**> 도구 > 옵션 으로 이동하여 이 창을 열 수 >.

1. Linux [컴퓨터에 연결 정보를](/cpp/linux/connect-to-your-remote-linux-computer) 제공하고 **연결**을 선택합니다. 비주얼 스튜디오는 **리눅스 디버그에**대한 기본 연결로 CMakeSettings.json에 해당 컴퓨터를 추가합니다. 또한 원격 컴퓨터에서 헤더를 아래로 당겨, 그래서 당신은 [그 원격 연결에 특정 IntelliSense를](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense)얻을 . 다음으로 Visual Studio는 파일을 원격 컴퓨터로 전송하고 원격 시스템에서 CMake 캐시를 생성합니다. 이러한 단계는 네트워크 속도와 원격 컴퓨터의 전원에 따라 다소 시간이 걸릴 수 있습니다. CMake 출력 창에 "대상 정보 추출 완료"라는 메시지가 표시되면 완료된 것으로 확인됩니다.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>리눅스에서 중단점 설정, 빌드 및 실행

데스크톱 응용 프로그램이기 때문에 디버그 구성에 몇 가지 추가 구성 정보를 제공해야 합니다.

1. CMake 대상 보기에서 AppBasicExampleGui를 마우스 오른쪽 단추로 클릭하고 **디버그 및 시작 설정을** 선택하여 숨겨진 **.vs** 하위 폴더에 있는 launch.vs.json 파일을 엽니다. 이 파일은 개발 환경에서 로컬에 위치합니다. 팀에서 파일을 확인하고 저장하려는 경우 프로젝트의 루트로 이동시킬 수 있습니다. 이 파일에서 AppBasicExampleGui에 대한 구성이 추가되었습니다. 이러한 기본 설정은 대부분의 경우 작동하지만 여기에는 적용되지 않습니다. 데스크톱 응용 프로그램이기 때문에 Linux 컴퓨터에서 볼 수 있도록 프로그램을 실행하려면 몇 가지 추가 정보를 제공해야 합니다.

1. Linux 컴퓨터에서 환경 변수 `DISPLAY` 값을 찾으려면 다음 명령을 실행합니다.

   ```cmd
   echo $DISPLAY
   ```

   AppBasicExampleGui의 구성에는 매개 변수 배열인 "pipeArgs"가 있습니다. 여기에는 "${디버거명령}"이라는 줄이 포함되어 있습니다. 원격 컴퓨터에서 gdb를 실행하는 명령입니다. Visual Studio는 해당 명령이 실행되기 전에 디스플레이를 이 컨텍스트로 내보내야 합니다. 예를 들어 디스플레이 값이 `:1`다음과 같이 해당 줄을 수정하는 경우

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. 응용 프로그램을 시작하고 디버깅합니다. 도구 모음에서 **시작 항목 선택** 드롭다운을 열고 **AppBasicExampleGui**를 선택합니다. 다음으로 도구 모음에서 녹색 재생 아이콘을 선택하거나 **F5를**누릅니다. 응용 프로그램과 해당 종속성은 원격 Linux 컴퓨터에 빌드된 다음 Visual Studio 디버거가 연결된 것으로 시작됩니다. 원격 Linux 머신에 애플리케이션 창이 표시됩니다.

1. 응용 프로그램 창으로 마우스를 이동하고 버튼을 클릭합니다. 중단점이 적중되었습니다. 프로그램 실행이 일시 중지되고 Visual Studio가 전경으로 돌아오면 중단점이 표시됩니다. Linux 콘솔 창도 Visual Studio에 나타납니다. 창은 원격 Linux 컴퓨터에서 출력을 제공하며 에 `stdin`대한 입력을 허용할 수도 있습니다. 다른 Visual Studio 창과 마찬가지로 원하는 위치에 도킹할 수 있습니다. 그 위치는 향후 세션에서 유지됩니다.

   ![Visual Studio Linux 콘솔 창](media/cmake-bullet3-linux-console.png)

1. Visual Studio를 사용하여 대화형으로 코드를 통해 애플리케이션 변수, 개체, 스레드, 메모리 및 단계를 검사할 수 있습니다. 하지만 이번에는 로컬 Windows 환경 대신 원격 Linux 컴퓨터에서 모든 작업을 수행합니다. **계속을** 선택하여 응용 프로그램이 정상적으로 다시 시작되고 종료될 수 있도록 하거나 로컬 실행과 마찬가지로 중지 단추를 선택할 수 있습니다.

1. Visual Studio가 Linux에서 애플리케이션을 시작한 이후에 호출 스택 창을 살펴보고 `x11OpenGLWindow`에 대한 호출을 보세요.

   ![Linux 호출 스택을 보여주는 호출 스택 창](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>학습 내용

이 자습서에서는 GitHub에서 직접 코드 베이스를 복제했습니다. 수정 하지 않고 Windows에서 빌드, 실행 및 디버깅했습니다. 그런 다음 사소한 구성 변경과 함께 동일한 코드 베이스를 사용하여 원격 Linux 컴퓨터에서 빌드, 실행 및 디버깅했습니다.

## <a name="next-steps"></a>다음 단계

Visual Studio에서 CMake 프로젝트를 구성하고 디버깅하는 방법을 자세히 알아봅니다.

> [!div class="nextstepaction"]
> [비주얼 스튜디오에서 CMake 프로젝트](cmake-projects-in-visual-studio.md)<br/><br/>
> [Linux CMake 프로젝트 구성](../linux/cmake-linux-project.md)<br/><br/>
> [원격 Linux 컴퓨터에 연결](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [CMake 빌드 설정 사용자 지정](customize-cmake-settings.md)<br/><br/>
> [CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)<br/><br/>
> [Linux 프로젝트 배포, 실행 및 디버그](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)
>
