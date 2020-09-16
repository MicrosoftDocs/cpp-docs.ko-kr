---
title: Visual Studio에서 C++ Linux 워크로드 설치
description: Visual Studio에서 C++에 대한 Linux 워크로드를 다운로드하고, 설치하고, 설정하는 방법입니다.
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 3f8e6eb8285652078e5f26ca58601bc6ccfa80d1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040979"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Linux 워크로드 다운로드, 설치 및 설정

::: moniker range="vs-2015"

Linux 프로젝트는 Visual Studio 2017 이상에서 지원됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end

::: moniker range=">=vs-2017"

Windows에서 Visual Studio IDE를 사용하여 원격 Linux 시스템, 가상 머신 또는 [Linux용 Windows 하위 시스템](/windows/wsl/about)에서 실행되는 C++ 프로젝트를 작성, 편집 및 디버그할 수 있습니다.

CMake를 Visual Studio 프로젝트로 변환할 필요 없이 CMake를 사용하는 기존 코드 베이스에서 작업할 수 있습니다. 코드 베이스가 플랫폼 간 기반인 경우 Visual Studio 내에서 Windows와 Linux를 모두 대상으로 할 수 있습니다. 예를 들어 Visual Studio를 사용하여 Windows에서 코드를 편집, 빌드, 디버그할 수 있습니다. 그런 다음 Linux 환경에서 빌드 및 디버그하기 위해 프로젝트의 대상을 신속하게 Linux로 변경합니다. Linux 헤더 파일은 로컬 컴퓨터에 자동으로 복사됩니다. Visual Studio는 전체 IntelliSense 지원(문 완성, 정의로 이동 등)을 제공하기 위해 해당 파일을 사용합니다.

이러한 시나리오에서는 **C++를 사용한 Linux 개발** 워크로드가 필요합니다.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio 설치

1. Windows 검색 상자:

   ![Windows 검색 상자](media/visual-studio-installer-search.png)

1. **앱** 결과에서 설치 관리자를 찾아 두 번 클릭합니다. 설치 프로그램이 열리면 **수정**을 선택한 다음, **워크로드** 탭을 클릭합니다. **기타 도구 집합**으로 아래로 스크롤하여 **C++를 사용한 Linux 개발** 워크로드를 선을 선택합니다.

   ![Linux 개발용 Visual C++ 워크로드](media/linuxworkload.png)

1. IoT 또는 포함된 플랫폼을 대상으로 지정하는 경우 오른쪽의 **설치 세부 정보** 창으로 이동합니다. **C++를 사용한 Linux 개발** 아래에서 **선택적 구성 요소**를 확장하고 필요한 구성 요소를 선택합니다. Linux용 CMake 지원이 기본적으로 선택됩니다.

1. **수정**을 클릭하여 설치를 계속합니다.

## <a name="options-for-creating-a-linux-environment"></a>Linux 환경 만들기 옵션

아직 Linux 머신이 없는 경우 Azure에서 Linux 가상 머신을 만들 수 있습니다. 자세한 내용은 [빠른 시작: Azure Portal에서 Linux 가상 머신 만들기](/azure/virtual-machines/linux/quick-create-portal)를 참조하세요.

Windows 10에서 WSL(Linux용 Windows 하위 시스템)에 선호하는 Linux 배포판을 설치하고 대상으로 지정할 수 있습니다. 자세한 내용은 [Windows 10용 Linux용 Windows 하위 시스템 설치 가이드](/windows/wsl/install-win10)를 참조하세요. Windows 스토어에 액세스할 수 없는 경우 [WSL 배포판 패키지를 수동으로 다운로드](/windows/wsl/install-manual)할 수 있습니다. WSL은 편리한 콘솔 환경이지만 그래픽 애플리케이션에 권장되지 않습니다.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio의 Linux 프로젝트는 원격 Linux 시스템 또는 WSL에 다음 종속성이 설치되어야 합니다.

- **컴파일러** - Visual Studio 2019는 GCC 및 [Clang](../build/clang-support-cmake.md)을 완벽하게 지원합니다.
- **gdb** - Visual Studio는 Linux 시스템에서 gdb를 자동으로 시작하고, Visual Studio 디버거의 프런트 엔드를 사용하여 Linux에서 완전히 신뢰할 수 있는 디버깅 환경을 제공합니다.
- **rsync** 및 **zip** - rsync 및 zip 포함으로 Visual Studio는 IntelliSense에서 사용하기 위해 Linux 시스템의 헤더 파일을 Windows 파일 시스템으로 추출할 수 있습니다.
- **make**
- **openssh-server**(원격 Linux 시스템 전용) - Visual Studio는 보안 SSH 연결을 통해 원격 Linux 시스템에 연결합니다.
- **CMake**(CMake 프로젝트 전용) - Linux에 대해 Microsoft의 [정적으로 링크한 CMake 이진 파일을 설치할 수 있습니다](https://github.com/microsoft/CMake/releases).
- **ninja-build**(CMake 프로젝트만 해당) - [Ninja](https://ninja-build.org/)는 Visual Studio 2019 버전 16.6 이상에서 Linux 및 WSL 구성 기본 생성기입니다.

다음 명령은 clang 대신 g++를 사용한다고 가정합니다.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio의 Linux 프로젝트는 원격 Linux 시스템 또는 WSL에 다음 종속성이 설치되어야 합니다.

- **gcc** - Visual Studio 2017은 GCC를 완벽하게 지원합니다.
- **gdb** - Visual Studio는 Linux 시스템에서 gdb를 자동으로 시작하고, Visual Studio 디버거의 프런트 엔드를 사용하여 Linux에서 완전히 신뢰할 수 있는 디버깅 환경을 제공합니다.
- **rsync** 및 **zip** - rsync 및 zip 포함으로 Visual Studio는 IntelliSense에서 사용하기 위해 Linux 시스템의 헤더 파일을 Windows 파일 시스템으로 추출할 수 있습니다.
- **make**
- **openssh-server** - Visual Studio는 보안 SSH 연결을 통해 원격 Linux 시스템에 연결합니다.
- **CMake**(CMake 프로젝트 전용) - Linux에 대해 Microsoft의 [정적으로 링크한 CMake 이진 파일을 설치할 수 있습니다](https://github.com/microsoft/CMake/releases).

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux 설정: WSL에서 Ubuntu

WSL을 대상으로 하는 경우, 빌드 및 디버그를 위해 원격 연결을 추가하거나 SSH를 구성할 필요가 없습니다. Intellisense 지원을 위해 Visual Studio를 사용하는 Linux 헤더의 자동 동기화에 **zip** 및 **rsync**가 필요합니다. **ninja-build**는 CMake 프로젝트에만 필요합니다. 필요한 애플리케이션이 아직 없는 경우 다음 명령을 사용하여 설치할 수 있습니다.

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>원격 Linux 시스템에서 Ubuntu

대상 Linux 시스템에 **openssh-server**, **g++** , **gdb** 및 **make**가 설치되어 있어야 합니다. **ninja-build**는 CMake 프로젝트에만 필요합니다. **ssh** 디먼이 실행 중이어야 합니다. IntelliSense 지원을 위해 로컬 컴퓨터와 원격 헤더를 자동 동기화하려면 **zip** 및 **rsync**가 필요합니다. 이러한 애플리케이션이 아직 없다면 다음과 같이 설치할 수 있습니다.

1. Linux 컴퓨터의 셸 프롬프트에서 다음을 실행합니다.

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   sudo 명령을 실행하기 위해 루트 암호를 입력하라는 메시지가 표시될 수 있습니다. 메시지가 표시되면 루트 암호를 입력하고 계속합니다. 완료되면 필수 서비스 및 도구가 설치됩니다.

1. 다음을 실행하여 ssh 서비스가 Linux 컴퓨터에서 실행되고 있는지 확인합니다.

   ```bash
   sudo service ssh start
   ```

   이 명령은 서비스를 시작하고 백그라운드에서 실행되어 연결을 허용할 준비를 완료합니다.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>WSL에서 Fedora

Fedora는 **dnf** 패키지 설치 관리자를 사용합니다. **g++** , **gdb**, **make**, **rsync**, **ninja-build** 및 **zip**을 다운로드하려면 다음을 실행합니다.

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

Intellisense 지원을 위해 Visual Studio를 사용하는 Linux 헤더의 자동 동기화에 **zip** 및 **rsync**가 필요합니다. **ninja-build**는 CMake 프로젝트에만 필요합니다.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>원격 Linux 시스템에서 Fedora

Fedora를 실행하는 대상 시스템은 **dnf** 패키지 설치 프로그램을 사용합니다. **openssh-server**, **g++** , **gdb**, **make**, **ninja-build**, **rsync** 및 **zip**을 다운로드하고 ssh 디먼을 다시 시작하려면 다음 지침을 따릅니다. **ninja-build**는 CMake 프로젝트에만 필요합니다.

1. Linux 컴퓨터의 셸 프롬프트에서 다음을 실행합니다.

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   sudo 명령을 실행하기 위해 루트 암호를 입력하라는 메시지가 표시될 수 있습니다. 메시지가 표시되면 루트 암호를 입력하고 계속합니다. 완료되면 필수 서비스 및 도구가 설치됩니다.

1. 다음을 실행하여 ssh 서비스가 Linux 컴퓨터에서 실행되고 있는지 확인합니다.

   ```bash
   sudo systemctl start sshd
   ```

   이 명령은 서비스를 시작하고 백그라운드에서 실행되어 연결을 허용할 준비를 완료합니다.

## <a name="next-steps"></a>다음 단계

이제 Linux 프로젝트를 만들거나 열고 대상 시스템에서 실행되도록 구성할 준비가 되었습니다. 자세한 내용은 다음을 참조하세요.

- [새 Linux 프로젝트 만들기](create-a-new-linux-project.md)
- [Linux CMake 프로젝트 구성](cmake-linux-project.md)

::: moniker-end
