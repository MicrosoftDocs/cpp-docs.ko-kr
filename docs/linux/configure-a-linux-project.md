---
title: Visual Studio에서 Linux MSBuild C++ 프로젝트 구성
ms.date: 10/16/2020
description: Visual Studio에서 MSBuild 기반 Linux 프로젝트를 구성하여 빌드할 수 있습니다.
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 451f34c257c210463ce11b11f27bc218d41b45c8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921817"
---
# <a name="configure-a-linux-msbuild-c-project-in-visual-studio"></a>Visual Studio에서 Linux MSBuild C++ 프로젝트 구성

::: moniker range="msvc-140"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

이 항목에서는 [Visual Studio에서 Linux MSBuild C++ 프로젝트 만들기](create-a-new-linux-project.md)에 설명된 대로 MSBuild 기반 Linux 프로젝트를 구성하는 방법을 설명합니다. Linux CMake 프로젝트의 경우 [Linux CMake 프로젝트 구성](cmake-linux-project.md)을 참조하세요.

물리적 Linux 머신, 가상 머신 또는 [Linux용 Windows 하위 시스템](/windows/wsl/about)(WSL)을 대상으로 지정하도록 Linux 프로젝트를 구성할 수 있습니다.

::: moniker range="msvc-160"

**Visual Studio 2019 버전 16.1** :

- WSL을 대상으로 하는 경우 원격 Linux 시스템을 대상으로 할 때 필수적인 IntelliSense를 빌드하고 가져오는 데 필요한 복사 작업을 방지할 수 있습니다.

- 빌드 및 디버깅에 대한 별도 Linux 대상을 지정할 수 있습니다.

::: moniker-end

## <a name="general-settings"></a>일반 설정

구성 옵션을 보려면 **프로젝트 > 속성** 메뉴를 선택하거나 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **속성** 을 선택합니다. **일반 설정** 이 나타납니다.

![일반 구성](media/settings_general.png)

기본적으로 실행 파일(.out)이 빌드됩니다. 정적 또는 동적 라이브러리를 빌드하거나 기존 메이크파일을 사용하려면 **구성 형식** 설정을 사용합니다.

WSL(Linux용 Windows 하위 시스템)용으로 빌드하는 경우 WSL 버전 1은 64개의 병렬 컴파일 프로세스로 제한됩니다. 이 값은 **구성 속성 > C/C++ > 일반** 에서 **최대 병렬 컴파일 작업** 설정에 따라 제어됩니다.

사용 중인 WSL 버전과 관계없이 병렬 컴파일 프로세스를 64개 넘게 사용하려는 경우 일반적으로 더 빠르고 안정적인 Ninja를 사용하여 빌드하는 것이 좋습니다. Ninja를 사용하여 빌드하려면 **구성 속성 > 일반** 에서 **증분 빌드 사용** 설정을 지정합니다.

속성 페이지의 설정에 대한 자세한 내용은 [Linux 프로젝트 속성 페이지 참조](prop-pages-linux.md)를 참조하세요.

## <a name="remote-settings"></a>원격 설정

원격 Linux 컴퓨터와 관련된 설정을 변경하려면 [일반](prop-pages/general-linux.md) 아래에 표시되는 원격 설정을 구성합니다.

- 원격 대상 Linux 컴퓨터를 지정하려면 **원격 빌드 머신** 항목을 사용합니다. 이렇게 하면 이전에 만든 연결 중 하나를 선택할 수 있습니다. 새 항목을 만들려면 [원격 Linux 컴퓨터에 연결](connect-to-your-remote-linux-computer.md) 섹션을 참조하세요.

   ![빌드 머신](media/remote-build-machine-vs2019.png)

   ::: moniker range="msvc-160"

   **Visual Studio 2019 버전 16.7** : WSL(Linux용 Windows 하위 시스템)을 대상으로 하려면 **플랫폼 도구 집합** 드롭다운을 **GCC for Windows Subsystem for Linux** (Linux용 Windows 하위 시스템의 GCC)로 설정합니다. 다른 원격 옵션이 사라지고 기본 WSL 셸에 대한 경로가 해당 자리에 나타납니다.

   ![WSL 빌드 머신](media/wsl-remote-vs2019.png)

   병렬 WSL 설치가 있는 경우 여기에 다른 경로를 지정할 수 있습니다. 여러 배포판 관리에 대한 자세한 내용은 [Linux용 Windows 하위 시스템 관리 및 구성](/windows/wsl/wsl-config#set-a-default-distribution)을 참조하세요.

   **구성 속성** > **디버깅** 페이지에서 디버깅에 대해 다른 대상을 지정할 수 있습니다.

   ::: moniker-end

- **원격 빌드 루트 디렉터리** 는 프로젝트가 원격 Linux 컴퓨터에서 빌드되는 루트 위치를 결정합니다. 달리 변경하지 않은 경우 기본값은 **~/projects** 로 설정됩니다.

- **원격 빌드 프로젝트 디렉터리** 는 원격 Linux 컴퓨터에서 이 특정 프로젝트가 빌드되는 위치입니다. 기본값은 **$(RemoteRootDir)/$(ProjectName)** 이며, 위에 설정된 루트 디렉터리 아래의 현재 프로젝트를 따라 명명된 디렉터리로 확장됩니다.

> [!NOTE]
> 프로젝트를 빌드하는 데 사용되는 기본 C 및 C++ 컴파일러 또는 링커 및 보관기를 변경하려면 **C/C++ > 일반** 섹션 및 **링커 > 일반** 섹션에서 적절한 항목을 사용합니다. 예를 들어 GCC 또는 Clang의 특정 버전을 지정할 수 있습니다. 자세한 내용은 [C/C++ 속성(Linux C++)](prop-pages/c-cpp-linux.md) 및 [링커 속성(Linux C++)](prop-pages/linker-linux.md)을 참조하세요.

## <a name="copy-sources-remote-systems-only"></a>소스 복사(원격 시스템에만 해당)

::: moniker range="msvc-160"

이 섹션은 WSL을 대상으로 하는 경우에는 적용되지 않습니다.

::: moniker-end

원격 시스템에서 빌드할 때 개발 PC의 소스 파일이 Linux 컴퓨터에 복사되어 해당 컴퓨터에서 컴파일됩니다. 기본적으로 Visual Studio 프로젝트의 모든 소스가 위의 설정에 지정된 위치에 복사됩니다. 그러나 추가 소스가 목록에 추가되거나, 소스 복사가 완전히 꺼질 수 있습니다(메이크파일 프로젝트에 대한 기본값).

- **복사할 소스** 가 원격 컴퓨터에 복사되는 소스를 결정합니다. 기본적으로 **\@(SourcesToCopyRemotely)** 는 프로젝트의 모든 소스 코드 파일로 설정되지만 이미지와 같은 자산/리소스 파일은 포함하지 않습니다.

- **소스 복사** 는 원격 컴퓨터에 소스 파일 복사를 사용하거나 사용하지 않기 위해 켜거나 끌 수 있습니다.

- **복사할 추가 소스** 를 통해 원격 시스템에 복사되는 추가 소스 파일을 추가할 수 있습니다. 세미콜론으로 구분된 목록을 지정하거나 **:=** 구문으로 사용할 로컬 및 원격 이름을 지정할 수 있습니다.

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>빌드 이벤트

원격 컴퓨터(또는 WSL)에서 모든 컴파일이 수행된 후 몇 가지 추가 빌드 이벤트가 프로젝트 속성의 빌드 이벤트 섹션에 추가되었습니다. 이들은 **원격 빌드 전 이벤트** , **원격 링크 전 이벤트** 및 **빌드 후 이벤트 제거** 이며, 프로세스의 개별 단계 전 또는 후에 원격 컴퓨터에서 발생합니다.

![빌드 이벤트](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a> 원격 시스템에서 헤더용 IntelliSense

**연결 관리자** 에서 새 연결을 추가하면 Visual Studio는 원격 시스템의 컴파일러용 포함 디렉터리를 자동으로 검색합니다. 그런 다음, Visual Studio는 해당 파일을 압축하여 로컬 Windows 컴퓨터의 디렉터리에 복사합니다. 그러면 Visual Studio 또는 CMake 프로젝트에서 해당 연결을 사용할 때마다 해당 디렉터리의 헤더가 IntelliSense를 제공하는 데 사용됩니다.

> [!NOTE]
> Visual Studio 2019 버전 16.5 이상에서는 원격 헤더 복사본이 최적화되었습니다. 이제 Linux 프로젝트를 열거나 Linux 대상에 대해 CMake를 구성하는 경우 헤더가 주문형으로 복사됩니다. 복사는 프로젝트의 지정된 컴파일러에 따라 프로젝트별로 백그라운드에서 수행됩니다. 자세한 내용은 [Linux IntelliSense의 정확도 및 성능 향상](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/)을 참조하세요.

이 기능은 zip이 설치된 Linux 컴퓨터에 따라 다릅니다. 이 apt-get 명령을 사용하여 zip을 설치할 수 있습니다.

```cmd
sudo apt install zip
```

헤더 캐시를 관리하려면 **도구 > 옵션, 플랫폼 간 > 연결 관리자> 원격 헤더 IntelliSense 관리자** 로 이동합니다. Linux 컴퓨터에서 변경한 후 헤더 캐시를 업데이트하려면 원격 연결을 선택한 후 **업데이트** 를 선택합니다. 연결 자체를 삭제하지 않고 헤더를 제거하려면 **삭제** 를 선택합니다. **탐색** 을 선택하여 **파일 탐색기** 에서 로컬 디렉터리를 엽니다. 이 폴더를 읽기 전용으로 취급합니다. Visual Studio 2017 15.3 이전 버전에서 작성된 기존 연결의 헤더를 다운로드하려면 연결을 선택한 다음, **다운로드** 를 선택합니다.

::: moniker range="msvc-150"

![플랫폼 간 > 연결 관리자 > 원격 헤더 IntelliSense 관리자가 선택된 옵션 대화 상자를 보여 주는 스크린샷](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="msvc-160"

![플랫폼 간 > 연결 관리자가 선택된 옵션 대화 상자를 보여 주는 스크린샷](media/connection-manager-vs2019.png)

로깅을 활성화하여 문제를 해결할 수 있습니다.

![원격 로깅](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="linux-target-locale"></a><a name="locale"></a> Linux 대상 로캘

Visual Studio에서는 설치된 패키지를 관리하거나 구성하지 않으므로 Visual Studio 언어 설정이 Linux 대상으로 전파되지 않습니다. **출력** 창에 표시되는 빌드 오류와 같은 메시지는 Linux 대상의 언어와 로캘을 사용하여 표시됩니다. Linux 대상에서 원하는 로캘을 구성해야 합니다.

## <a name="see-also"></a>참조

[컴파일러 설정 및 빌드 속성](../build/working-with-project-properties.md)<br/>
[C++ 일반 속성(Linux C++)](prop-pages/general-linux.md)<br/>
[VC++ 디렉터리(Linux C++)](prop-pages/directories-linux.md)<br/>
[소스 복사 프로젝트 속성(Linux C++)](prop-pages/copy-sources-project.md)<br/>
[빌드 이벤트 속성(Linux C++)](prop-pages/build-events-linux.md)
