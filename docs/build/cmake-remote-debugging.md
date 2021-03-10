---
title: '자습서: 원격 Windows 머신에서 CMake 프로젝트 디버그'
ms.date: 12/4/2020
ms.topic: tutorial
description: Windows에서 Visual Studio C++를 사용하여 CMake 프로젝트를 만들고 빌드하는 방법입니다. 그런 다음 원격 Windows 머신에서 배포하고 디버그할 수 있습니다.
ms.openlocfilehash: 575b815559cbe70384b4669c94cf003daa3ee7d7
ms.sourcegitcommit: 5efc34c2b98d4d0d3e41aec38b213f062c19d078
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844509"
---
# <a name="tutorial-debug-a-cmake-project-on-a-remote-windows-machine"></a>자습서: 원격 Windows 머신에서 CMake 프로젝트 디버그

이 자습서에서는 Windows에서 Visual Studio C++를 사용하여 원격 Windows 머신에서 배포하고 디버그할 수 있는 CMake 프로젝트를 만들고 빌드합니다. 이 자습서는 Windows ARM64와 관련되지만 해당 단계를 다른 아키텍처에 대해 일반화할 수 있습니다.

Visual Studio에서 ARM64의 기본 디버깅 환경은 ARM64 Windows 머신을 원격으로 디버그합니다. 이 자습서에 설명된 것처럼 디버그 설정을 구성하지 않고 ARM64 CMake 프로젝트를 디버그하려고 하면 Visual Studio가 원격 머신을 찾을 수 없다는 오류가 표시됩니다.

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 알아봅니다.

> [!div class="checklist"]
>
> * CMake 프로젝트 만들기
> * ARM64용으로 빌드하도록 CMake 프로젝트 구성
> * 원격 ARM64 Windows 머신에서 실행되도록 CMake 프로젝트 구성
> * 원격 ARM64 Windows 머신에서 실행되는 CMake 프로젝트 디버그

## <a name="prerequisites"></a>필수 구성 요소

### <a name="on-the-host-machine"></a>호스트 머신의 경우

플랫폼 간 C++ 개발을 위해 Visual Studio를 설정하려면 대상 아키텍처용 빌드 도구를 설치합니다. 이 자습서에서는 다음을 수행하여 ARM64 빌드 도구를 설치합니다.

1. Visual Studio 설치 관리자를 실행합니다. 아직 Visual Studio를 설치하지 않았다면 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조하세요.
1. Visual Studio 설치 관리자 홈 화면에서 **수정** 을 선택합니다.
1. 위쪽의 선택 항목에서 **개별 구성 요소** 를 선택합니다.
1. **컴파일러, 빌드 도구 및 런타임** 섹션으로 스크롤합니다.
1. 다음이 선택되어 있는지 확인합니다.
    - **Windows용 C++ CMake 도구**
    - **MSVC v142 - VS 2019 C++ ARM64 빌드 도구(최신)** `ARM` 빌드 도구가 아닌 `ARM64` 빌드 도구를 선택하고(64 찾기) `VS 2019`에 맞는 버전을 선택하는 것이 중요합니다.
1. **수정** 을 선택하여 도구를 설치합니다.

### <a name="on-the-remote-machine"></a>원격 머신의 경우

1. 원격 머신에 원격 도구를 설치합니다. 이 자습서의 경우 [원격 도구 다운로드 및 설치](/visualstudio/debugger/remote-debugging-cpp#download-and-install-the-remote-tools)의 지침에 따라 ARM64 도구를 설치합니다.
1. 원격 머신에서 원격 디버거를 시작하고 구성합니다. 이 자습서의 경우 원격 Windows 머신에서 [원격 디버거 설치](/visualstudio/debugger/remote-debugging-cpp#BKMK_setup)의 지침에 따라 수행합니다.

## <a name="create-a-cmake-project"></a>CMake 프로젝트 만들기

Windows 호스트 머신에서 다음을 수행합니다.
1. Visual Studio를 실행합니다.
1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.
1. **CMake 프로젝트** > **다음** 을 선택합니다.
1. 프로젝트 이름을 지정하고 위치를 선택합니다. 그런 다음 **만들기** 를 선택합니다.

Visual Studio에서 프로젝트를 만들고 **솔루션 탐색기** 를 채우는 데 몇 분 정도 걸립니다.

## <a name="configure-for-arm64"></a>ARM64에 대한 구성

ARM64 Windows 머신을 대상으로 하려면 ARM64 빌드 도구를 사용하여 빌드해야 합니다.

Visual Studio **구성** 드롭다운을 선택하고 **구성 관리** 를 선택합니다.

![Visual Studio 구성 드롭다운에서 구성 관리 선택](media/vs2019-cmake-manage-configurations.png)

**새 구성 추가**(녹색 **+** 단추)를 선택하여 새 구성을 추가합니다.
표시되는 **CMakeSettings** 대화 상자에서 **arm64-debug** 를 선택한 후 **선택** 을 누릅니다.

![arm64-debug 구성 추가](media/cmake-add-config-icon-with-target-dialog.png)

그러면 *`CmakeSettings.json`* 파일에 **arm64-Debug** 라는 디버그 구성이 추가됩니다. 이 구성 이름은 **구성** 드롭다운에서 해당 설정을 쉽게 식별할 수 있도록 하는 고유한 식별 이름입니다.

**도구 집합** 드롭다운이 **msvc_arm64_x64** 로 설정됩니다. 이제 설정이 다음과 같이 나타납니다.

![CMake 설정 대화 상자](media/cmake-settings-editor2.png)

> [!Note]
> **도구 집합** 드롭다운에서 **msvc_arm64** 는 32비트 호스트 도구를 선택하여 ARM64에 크로스 컴파일하는 반면, **msvc_arm64 x64** 는 64비트 호스트 도구를 선택하여 ARM64에 크로스 컴파일합니다(이 자습서에서 수행함).

`CMakeSettings.json` 파일을 저장합니다. 구성 드롭다운에서 **arm64-debug** 를 선택합니다. `CMakeSettings.json` 파일을 저장한 후 목록에 표시되려면 잠시 시간이 걸릴 수 있습니다.

![Visual Studio 구성 드롭다운에서 arm64-debug가 선택되어 있는지 확인](media/vs2019-cmake-manage-configurations-arm.png) 

## <a name="add-a-debug-configuration-file"></a>디버그 구성 파일 추가

다음으로, 원격 머신을 찾을 수 있는 위치를 다른 구성 세부 정보와 함께 Visual Studio에 알리는 구성 정보를 추가합니다.

**보기 전환** 단추를 선택하여 **솔루션 탐색기** 뷰를 대상 뷰로 변경합니다.

![솔루션 탐색기 보기 전환 단추](media/solution-explorer-switch-view.png)

그런 다음 **솔루션 탐색기** 에서 **CMake 대상 뷰** 를 두 번 클릭하여 프로젝트를 확인합니다.

프로젝트 폴더(이 예제에서는 **CMakeProject3 Project**)를 연 후 실행 파일을 마우스 오른쪽 단추로 클릭하고 **디버그 구성 추가** 를 선택합니다.

![디버그 구성 추가 선택](media/cmake-targets-add-debug-configuration.png)

그러면 프로젝트에 `launch.vs.json` 파일이 만들어집니다. 이 파일을 열고 다음 항목을 변경하여 원격 디버깅을 사용하도록 설정합니다.

- `projectTarget`: 위의 지침에 따라 **솔루션 탐색기** 대상 뷰에서 디버그 구성 파일을 추가한 경우에는 이 항목이 설정되어 있습니다.
- `remoteMachineName`: 원격 ARM64 머신의 IP 주소 또는 해당 머신 이름으로 설정합니다.

`launch.vs.json` 설정에 대한 자세한 내용은 [launch.vs.json 스키마 참조](launch-vs-schema-reference-cpp.md)를 참조하세요.

> [!Note]
>  **솔루션 탐색기** 의 대상 뷰 대신 폴더 뷰를 사용하는 경우 `CMakeLists.txt` 파일을 마우스 오른쪽 단추로 클릭하고 **디버그 구성 추가** 를 선택합니다. 이 작업은 다음과 같은 방법으로 대상 뷰에서 디버그 구성을 추가하는 것과 다릅니다.
> - 디버거를 선택하라는 메시지가 표시됩니다(**C/C++ 원격 Windows 디버그** 선택).
> - Visual Studio의 경우 `launch.vs.json` 파일에서 제공하는 구성 템플릿 정보가 더 적으므로, 직접 정보를 추가해야 합니다. `remoteMachineName` 및 `projectTarget` 항목을 제공해야 합니다. 대상 뷰에서 구성을 추가하는 경우 `remoteMachineName`만 지정하면 됩니다.
> - `projectTarget` 설정 값에 대해 시작 항목 드롭다운을 확인하여 대상의 고유한 이름을 가져옵니다. 예를 들어 이 자습서의 경우 ‘CMakeProject3.exe’입니다.

## <a name="start-the-remote-debugger-monitor-on-the-remote-windows-machine"></a>원격 Windows 머신에서 원격 디버거 모니터 시작

CMake 프로젝트를 실행하기 전에 원격 Windows 머신에서 Visual Studio 2019 원격 디버거가 실행 중인지 확인합니다.  인증 상황에 따라 원격 디버거 옵션을 변경해야 할 수도 있습니다.

예를 들어 원격 머신의 Visual Studio 원격 디버거 메뉴 모음에서 **도구** > **옵션** 을 선택합니다. 환경 설정 방법에 맞게 **인증 모드** 를 설정합니다.

![원격 디버거 인증 옵션](media/remote-debugger-options.png)

그런 다음, 호스트 머신의 Visual Studio에서 `launch.vs.json` 파일을 일치하도록 업데이트합니다. 예를 들어 원격 디버거에서 **인증 없음** 업데이트를 선택하는 경우 `configurations` 섹션 `launch.vs.json`에 **“authenticationType”: “none”** 을 추가하여 프로젝트의 `launch.vs.json` 파일을 업데이트합니다. 그러지 않으면 `"authenticationType"`의 기본값이 `"windows"`로 지정되어 명시적으로 지정할 필요가 없습니다. 다음 예제에서는 인증 없는 경우를 위해 구성된 `launch.vs.json` 파일을 보여 줍니다.

``` XAML
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
        "type": "remoteWindows",
        "authenticationType": "none"
        "name": "CMakeLists.txt",
        "project": "CMakeLists.txt",
        "projectTarget": "CMakeProject3.exe",
        "remoteMachineName": "<ip address goes here>",
        "cwd": "${debugInfo.defaultWorkingDirectory}",
        "program": "${debugInfo.fullTargetPath}",
        "deploy": [],
        "args": [],
        "env": {}
    },
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeProject3.exe",
      "name": "CMakeProject3.exe"
    }
  ]
}
```

## <a name="debug-the-app"></a>앱 디버그

호스트 머신의 Visual Studio **솔루션 탐색기** 에서 CMake 프로젝트의 CPP 파일을 엽니다. 여전히 **CMake 대상 뷰** 를 사용 중인 경우에는 **(실행 파일)** 노드를 열어 표시해야 합니다.

기본 CPP 파일은 간단한 Hello World 콘솔 앱입니다. `return 0;`에서 중단점을 설정합니다.

Visual Studio 도구 모음에서 **시작 항목** 드롭다운을 사용하여 `launch.vs.json` 파일에서 `"name"`에 대해 지정한 이름을 선택합니다.

![CMakeProject3.exe가 선택된 시작 항목 드롭다운 예제](media/startup-item.png)

디버깅을 시작하려면 Visual Studio 도구 모음에서 **디버그** > **디버깅 시작** 을 선택합니다(또는 **F5** 누름).

디버깅이 시작되지 않으면 `launch.vs.json` 파일에 다음이 올바르게 설정되어 있는지 확인합니다.
- `"remoteMachineName"`은 원격 ARM64 Windows 머신의 IP 주소나 머신 이름으로 설정해야 합니다.
- `"name"`은 Visual Studio 시작 항목 드롭다운에서 선택한 항목과 일치해야 합니다.
- `"projectTarget"`은 디버그할 CMake 대상의 이름과 일치해야 합니다.
- `"type"`는 `"remoteWindows"`여야 합니다.
- 원격 디버거의 인증 형식이 **인증 없음** 으로 설정된 경우 `launch.vs.json` 파일에 `"authenticationType": "none"`이 설정되어야 합니다.
- Windows 인증을 사용 중인 경우에는 메시지가 표시되면 원격 머신에서 인식되는 계정을 사용하여 로그인합니다.

프로젝트가 빌드된 후에는 원격 ARM64 Windows 머신에 앱이 표시됩니다.

![원격 Windows ARM64 머신에서 실행 중인 Hello CMake 콘솔 앱](media/remote-cmake-app.png)

호스트 머신의 Visual Studio는 `return 0;`의 중단점에서 중지되어야 합니다.

## <a name="what-you-learned"></a>학습 내용

이 자습서에서는 CMake 프로젝트를 만들고 ARM64 Windows용으로 빌드되도록 구성했으며 원격 ARM64 Windows 머신에서 디버그했습니다.

## <a name="next-steps"></a>다음 단계

Visual Studio에서 CMake 프로젝트를 구성하고 디버깅하는 방법을 자세히 알아봅니다.

> [!div class="nextstepaction"]
> [Visual Studio의 CMake 프로젝트](cmake-projects-in-visual-studio.md)\
> [CMake 빌드 설정 사용자 지정](customize-cmake-settings.md)\
> [CMake 디버깅 세션 구성](configure-cmake-debugging-sessions.md)\
> [CMake 미리 정의된 구성 참조](cmake-predefined-configuration-reference.md)\
[launch.vs.json 스키마 참조](launch-vs-schema-reference-cpp.md)
