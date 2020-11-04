---
title: Visual Studio에서 대상 Linux 시스템에 연결
description: Visual Studio C++ 프로젝트 내에서 원격 Linux 머신 또는 Linux용 Windows 하위 시스템에 연결하는 방법입니다.
ms.date: 01/17/2020
ms.openlocfilehash: da74d1c735a29304fdf46e920eac45580f386259
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921791"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Visual Studio에서 대상 Linux 시스템에 연결

::: moniker range="msvc-140"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="msvc-150"

원격 머신 또는 WSL(Linux용 Windows 하위 시스템)을 대상으로 하도록 Linux 프로젝트를 구성할 수 있습니다. 원격 머신 및 WSL에 대해 Visual Studio 2017에서 원격 연결을 설정해야 합니다.

::: moniker-end

::: moniker range="msvc-160"

원격 머신 또는 WSL(Linux용 Windows 하위 시스템)을 대상으로 하도록 Linux 프로젝트를 구성할 수 있습니다. 원격 머신에 대해 Visual Studio에서 원격 연결을 설정해야 합니다. WSL에 연결하려면 [WSL에 연결](#connect-to-wsl) 섹션으로 건너뜁니다.

::: moniker-end

::: moniker range=">=msvc-150"

원격 연결을 사용하는 경우 Visual Studio C++는 원격 머신에 Linux 프로젝트를 빌드합니다. 물리적 머신, 클라우드의 VM 또는 WSL 등은 중요하지 않습니다.
프로젝트를 빌드하기 위해 Visual Studio는 소스 코드를 원격 Linux 컴퓨터에 복사합니다. 그런 다음 Visual Studio 설정에 따라 코드를 컴파일합니다.

::: moniker-end

::: moniker range="msvc-160"

> [!NOTE]
> Visual Studio 2019 버전 16.5 이상에서는 원격 개발을 위해 Linux 시스템에 대한 안전한 FIPS(Federal Information Processing Standard) 140-2 규격 암호화 연결도 지원합니다. FIPS 규격 연결을 사용하려면 대신 [FIPS 규격 보안 원격 Linux 개발 설정](set-up-fips-compliant-secure-remote-linux-development.md)의 단계를 따르세요.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>원격 시스템에서 SSH 서버 설정

Linux 시스템에서 SSH를 아직 설정하지 않은 상태로 실행한 경우 다음 단계에 따라 설치합니다. 이 문서의 예제에서는 OpenSSH 서버 버전 7.6과 함께 Ubuntu 18.04 LTS를 사용합니다. 그러나 OpenSSH의 비교적 최근 버전을 사용하는 모든 배포판에 대한 지침은 동일해야 합니다.

1. Linux 시스템에서 OpenSSH 서버를 설치하고 시작합니다.

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 시스템이 부팅될 때 SSH 서버가 자동으로 시작되도록 하려면 systemctl을 사용하여 사용하도록 설정합니다.

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>원격 연결 설정

1. Visual Studio의 메뉴 모음에서 **도구 > 옵션** 을 선택하여 **옵션** 대화 상자를 엽니다. 그런 다음 **플랫폼 간 > 연결 관리자** 를 선택하여 연결 관리자 대화 상자를 엽니다.

   이전에 Visual Studio에서 연결을 설정하지 않은 경우 프로젝트를 처음 빌드할 때 Visual Studio에서 연결 관리자 대화 상자를 엽니다.

1. 연결 관리자 대화 상자에서 **추가** 단추를 선택하여 새 연결을 추가합니다.

   ![연결 관리자](media/settings_connectionmanager.png)

   어느 쪽 경우이든 **원격 시스템에 연결** 창이 표시됩니다.

   ![원격 시스템에 연결](media/connect.png)

1. 다음 정보를 입력합니다.

   | 입력 | 설명
   | ----- | ---
   | **호스트 이름**           | 대상 디바이스의 이름 또는 IP 주소
   | **포트**                | SSH 서비스가 실행되는 포트(일반적으로 22)
   | **사용자 이름**           | 인증할 사용자
   | **인증 형식** | 암호 및 프라이빗 키가 모두 지원됨
   | **암호**            | 입력한 사용자 이름의 암호
   | **프라이빗 키 파일**    | SSH 연결을 위해 생성된 프라이빗 키 파일
   | **암호**          | 위에서 선택한 프라이빗 키와 함께 사용된 암호

   인증을 위해 암호 또는 키 파일과 암호를 사용할 수 있습니다. 대부분의 개발 시나리오에서는 암호 인증으로 충분하지만 키 파일은 더 안전합니다. 키 쌍이 이미 있는 경우 다시 사용할 수 있습니다. 현재 Visual Studio는 원격 연결에 대해 RSA 및 DSA 키만 지원합니다.

1. **연결** 단추를 선택하여 원격 컴퓨터에 대한 연결을 시도합니다.

   연결에 성공하면 Visual Studio에서 원격 헤더를 사용하도록 IntelliSense를 구성합니다. 자세한 내용은 [원격 시스템의 헤더에 대한 IntelliSense](configure-a-linux-project.md#remote_intellisense)를 참조하세요.

   연결이 실패하면 변경해야 하는 입력 상자에 빨간색 윤곽선이 표시됩니다.

   ![연결 관리자 오류](media/settings_connectionmanagererror.png)

   인증을 위해 키 파일을 사용하는 경우 대상 머신의 SSH 서버가 실행 중이고 올바르게 구성되었는지 확인합니다.

   ::: moniker-end

   ::: moniker range="msvc-160"

## <a name="logging-for-remote-connections"></a>원격 연결에 대한 로깅

   로깅을 활성화하여 연결 문제를 해결할 수 있습니다. 메뉴 모음에서 **도구 > 옵션** 을 선택합니다. **옵션** 대화 상자에서 **플랫폼 간 > 로깅** 을 선택합니다.

   ![원격 로깅](media/remote-logging-vs2019.png)

   로그에는 연결, 원격 머신으로 전송되는 모든 명령(해당 텍스트, 종료 코드, 실행 시간), Visual Studio에서 셸로 전송되는 모든 출력이 포함됩니다. 로깅은 Visual Studio의 모든 플랫폼 간 CMake 프로젝트 또는 MSBuild 기반 Linux 프로젝트에 대해 작동합니다.

   파일 또는 출력 창의 **플랫폼 간 로깅** 창에 출력되도록 구성할 수 있습니다. MSBuild 기반 Linux 프로젝트의 경우 원격 머신으로 전송된 MSBuild 명령은 Out of Process로 내보내므로 **출력 창** 으로 라우팅되지 않습니다. 대신 “msbuild_” 접두사가 포함된 형태로 파일에 기록됩니다.

## <a name="command-line-utility-for-the-connection-manager"></a>연결 관리자에 대한 명령줄 유틸리티  

**Visual Studio 2019 버전 16.5 이상** : ConnectionManager.exe는 Visual Studio 외부에서 원격 개발 연결을 관리하는 명령줄 유틸리티입니다. 새 개발 컴퓨터를 프로비저닝하는 등의 작업에 유용합니다. 또는 연속 통합을 위해 Visual Studio를 설정하는 데 사용할 수 있습니다. ConnectionManager 명령에 대한 예제 및 전체 참조는 [ConnectionManager 참조](connectionmanager-reference.md)를 참조하세요.  

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="tcp-port-forwarding"></a>TCP 포트 전달

Visual Studio의 Linux 지원에는 TCP 포트 전달에 대한 종속성이 있습니다. 원격 시스템에 TCP 포트 전달이 사용하지 않도록 설정되어 있는 경우 **Rsync** 및 **gdbserver** 가 영향을 받습니다. 이 종속성의 영향을 받는 경우 이 [제안 티켓](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html)을 Developer Community에서 추천할 수 있습니다.

rsync는 MSBuild 기반 Linux 프로젝트 및 CMake 프로젝트 모두에서 [IntelliSense에 사용할 원격 시스템의 헤더를 Windows에 복사](configure-a-linux-project.md#remote_intellisense)하는 데 사용됩니다. TCP 포트 전달을 사용하도록 설정할 수 없는 경우 원격 헤더의 자동 다운로드를 사용하지 않도록 설정합니다. 이 기능을 사용하지 않도록 설정하려면 **도구 > 옵션 > 플랫폼 간 > 연결 관리자 > 원격 헤더 IntelliSense 관리자** 를 사용합니다. 원격 시스템에 TCP 포트 전달이 사용하도록 설정되어 있지 않은 경우 IntelliSense의 원격 헤더 다운로드가 시작되면 다음 오류가 표시됩니다.

![헤더 오류](media/port-forwarding-headers-error.png)

rsync는 원격 시스템에 소스 파일을 복사하기 위한 Visual Studio의 CMake 지원에도 사용됩니다. TCP 포트 전달을 사용하도록 설정할 수 없는 경우 sftp를 원격 소스 복사 방법으로 사용할 수 있습니다. sftp는 대개 rsync보다 느리지만, TCP 포트 전달에 대한 종속성이 없습니다. [CMake 설정 편집기](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)에서 **remoteCopySourcesMethod** 속성을 사용하여 원격 소스 복사 방법을 관리할 수 있습니다. 원격 시스템에 TCP 포트 전달이 사용하지 않도록 설정된 경우 처음 rsync를 호출하면 CMake 출력 창에 오류가 표시됩니다.

![Rsync 오류](media/port-forwarding-copy-error.png)

gdbserver는 임베디드 디바이스에서 디버그하는 데 사용할 수 있습니다. TCP 포트 전달을 사용하도록 설정할 수 없는 경우 모든 원격 디버깅 시나리오에 대해 gdb를 사용해야 합니다. gdb는 원격 시스템에서 프로젝트를 디버그할 때 기본적으로 사용됩니다.

## <a name="connect-to-wsl"></a>WSL에 연결

::: moniker-end

::: moniker range="msvc-150"

Visual Studio 2017에서는 원격 Linux 머신에 사용하는 것과 같은 단계를 사용하여 WSL에 연결합니다. **호스트 이름** 으로 **localhost** 를 사용합니다.

::: moniker-end

::: moniker range="msvc-160"

Visual Studio 2019 버전 16.1에서는 [WSL(Linux용 Windows 하위 시스템)](/windows/wsl/about)과 함께 C++를 사용하기 위한 기본 지원을 추가했습니다. 즉, 로컬 WSL 설치에서 직접 빌드 및 디버그할 수 있습니다. 더 이상 원격 연결을 추가하거나 SSH를 구성할 필요가 없습니다. 자세한 내용은 여기서 [WSL 설치 방법](/windows/wsl/install-win10)을 참조하세요.

Visual Studio에서 작동하도록 WSL 설치를 구성하려면 gcc 또는 clang, gdb, ninja-build(Visual Studio 2019 버전 16.6 이상을 사용하는 CMake 프로젝트에만 필요), rsync 및 zip 도구가 설치되어 있어야 합니다. g++ 컴파일러도 설치하는 이 명령을 사용하여 APT를 사용하는 배포판에 설치할 수 있습니다.

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

자세한 내용은 [Linux 작업 다운로드, 설치, 설정](download-install-and-setup-the-linux-development-workload.md)을 참조하세요.

WSL에 대해 MSBuild 프로젝트를 구성하려면 [Linux 프로젝트 구성](configure-a-linux-project.md)을 참조하세요. WSL에 대해 CMake 프로젝트를 구성하려면 [Linux CMake 프로젝트 구성](cmake-linux-project.md)을 참조하세요. WSL을 사용하여 간단한 콘솔 애플리케이션을 만드는 단계별 지침을 따르려면 [Visual Studio 2019 및 WSL(Linux용 Windows 하위 시스템)의 C++](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)에 대한 소개 블로그 게시물을 참조하세요.

::: moniker-end

## <a name="see-also"></a>관련 항목

[Linux 프로젝트 구성](configure-a-linux-project.md)\
[Linux CMake 프로젝트 구성](cmake-linux-project.md)\
[Linux 프로젝트 배포, 실행 및 디버그](deploy-run-and-debug-your-linux-project.md)\
[CMake 디버깅 세션 구성](../build/configure-cmake-debugging-sessions.md)
