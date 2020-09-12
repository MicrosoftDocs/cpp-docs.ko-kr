---
title: iOS를 사용하여 빌드할 도구 설치 및 구성
ms.date: 10/17/2019
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
ms.openlocfilehash: 26dea080f3d3f05885f348dcaf1c66a0db2a36b5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041993"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>iOS를 사용하여 빌드할 도구 설치 및 구성

Visual Studio를 **C++를 사용한 플랫폼 간 모바일 개발** 도구와 함께 사용하여 iOS 코드를 편집 및 디버그하고 iOS 시뮬레이터 또는 iOS 디바이스에 배포할 수 있습니다. 그러나 라이선스 제한으로 인해 Mac에서는 코드를 원격으로 빌드하고 실행해야 합니다. Visual Studio를 사용하여 iOS 앱을 빌드 및 실행하려면 Mac에서 원격 에이전트 [vcremote](https://www.npmjs.com/package/vcremote)를 설정 및 구성해야 합니다. 원격 에이전트는 Visual Studio의 빌드 요청을 처리하고 Mac에 연결된 iOS 디바이스 또는 Mac의 iOS 시뮬레이터에서 앱을 실행합니다.

> [!NOTE]
> Mac이 아닌 클라우드에 호스트된 Mac 서비스를 사용하는 방법에 대한 자세한 내용은 [Configure Visual Studio to connect to your cloud hosted Mac](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017&preserve-view=true#configure-visual-studio-to-connect-to-your-cloud-hosted-mac)(클라우드에 호스트된 Mac에 연결하도록 Visual Studio 구성)을 참조하세요. 지침은 Visual Studio Tools for Apache Cordova를 사용한 빌드에 해당합니다. 지침을 사용하여 C++로 빌드하려면 `vcremote`를 `remotebuild`로 대체합니다.

iOS를 사용하여 빌드하는 도구를 설치한 경우 Visual Studio 및 Mac에서 iOS 개발용 원격 에이전트를 신속하게 구성 및 업데이트하는 방법은 이 문서를 참조하세요.

## <a name="prerequisites"></a>전제 조건

원격 에이전트를 설치 및 사용하여 iOS용 코드를 개발하려면 다음 필수 조건이 있어야 합니다.

- macOS Mojave 버전 10.14 이상을 실행하는 Mac 컴퓨터

- [APPLE ID](https://appleid.apple.com/)

- 활성 [Apple 개발자 프로그램](https://developer.apple.com/programs/) 계정

   배포용이 아닌 테스트용으로 iOS 디바이스에 테스트용 로드 앱을 허용하는 체험 계정을 가져올 수 있습니다.

- [Xcode](https://developer.apple.com/xcode/downloads/) 버전 10.2.1 이상

   Xcode는 앱 스토어에서 다운로드할 수 있습니다.

- Xcode 명령줄 도구

   Xcode 명령줄 도구를 설치하려면 Mac에서 터미널 앱을 열고 다음 명령을 입력합니다.

   `xcode-select --install`

- Xcode에서 앱을 서명하는 서명 ID로 구성된 Apple ID 계정

   Xcode에서 서명 ID를 보거나 설정하려면 **Xcode** 메뉴를 열고 **기본 설정**을 선택합니다. **계정** 을 선택하고 Apple ID를 선택한 다음 **세부 정보 보기** 단추를 선택합니다. 자세한 지침은 [Apple ID 계정 추가](https://help.apple.com/xcode/mac/current/#/devaf282080a)를 참조하세요.

   서명 요구 사항에 대한 자세한 내용은 [앱 서명이란](https://help.apple.com/xcode/mac/current/#/dev3a05256b8)을 참조하세요.

- 개발에 iOS 디바이스를 사용하는 경우 디바이스에 대해 Xcode에서 구성된 프로비저닝 프로필

   Xcode는 필요에 따라 서명 인증서를 생성하는 자동 서명 기능을 제공합니다. Xcode 자동 서명에 대한 자세한 내용은 [자동 서명](https://help.apple.com/xcode/mac/current/#/dev80cc24546)을 참조하세요.

   수동 서명을 수행하려면 앱에 대한 프로비저닝 프로필을 만들어야 합니다. 프로비저닝 프로필을 만드는 방법에 대한 자세한 내용은 [개발 프로비저닝 프로필 만들기](https://help.apple.com/developer-account/#/devf2eb157f8)를 참조하세요.

- [Node.js](https://nodejs.org/) version 12.14.1 and npm version 6.13.4

   Mac에 Node.js 버전의 12.14.1를 설치 합니다. Node.js 패키지를 설치 하는 경우 npm version 6.13.4과 함께 제공 되어야 합니다. 다른 버전의 Node.js 및 npm은 원격 에이전트 `vcremote`에 사용된 일부 모듈을 지원하지 않을 수 있으므로 `vcremote` 설치가 실패할 수 있습니다. [노드 버전 관리자](https://nodejs.org/en/download/package-manager/#nvm)와 같은 패키지 관리자를 사용 하 여 Node.js를 설치 하는 것이 좋습니다. 명령을 사용 하 여 `sudo` Node.js를 설치 하지 마세요 .를 사용 하는 경우 일부 모듈은 설치에 실패할 수 있습니다 `sudo` .

## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> iOS용 원격 에이전트 설치

C++를 사용한 모바일 개발 워크로드를 설치하면 Visual Studio는 Mac에서 실행되는 원격 에이전트인 [vcremote](https://www.npmjs.com/package/vcremote)와 통신하여 파일을 전송하고, iOS 앱을 빌드 및 실행하고, 디버깅 명령을 보낼 수 있습니다.

원격 에이전트를 설치하기 전에 [필수 조건](#prerequisites)을 충족하고 [C++를 사용한 플랫폼 간 모바일 개발](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools)의 설치 단계를 완료했는지 확인합니다.

### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> 원격 에이전트를 다운로드하여 설치하려면

- Mac의 터미널 앱에서 현재 사용 중인 Node.js 버전이 필요한 버전 12.14.1 확인 합니다. 버전을 확인 하려면 다음 명령을 실행 합니다.

  `node -v`
  
  올바른 버전이 아닌 경우 필수 구성 요소에서 Node.js 설치 지침을 따라야 할 수도 있습니다. 그런 다음 Node.js를 다시 시작 합니다.

- 필요한 Node.js 사용 중인지 확인 한 후 다음 명령을 실행 하 여 해당 Node.js 버전 아래에 vcremote를 설치 합니다.

   `npm install -g --unsafe-perm vcremote`

   전역 설치 (**-g**) 스위치를 권장 하지만 필수는 아닙니다. 전역 설치 스위치를 사용 하지 않는 경우 vcremote는 터미널 앱의 현재 활성 경로 아래에 설치 됩니다.

   설치하는 동안 `vcremote`가 설치되고 Mac에서 개발자 모드가 활성화됩니다. [Homebrew](https://brew.sh/)와 두 개의 npm 패키지(`vcremote-lib` 및 `vcremote-utils`)도 설치됩니다. 설치가 완료되면 건너뛴 선택적 종속성에 대한 경고를 무시해도 안전합니다.

   > [!NOTE]
   > Homebrew를 설치하려면 sudo(관리자) 액세스 권한이 있어야 합니다. sudo 액세스 권한 없이 `vcremote`를 설치해야 하는 경우 usr/local 위치에 Homebrew를 수동으로 설치하고 해당 bin 폴더를 사용자의 경로에 추가하면 됩니다. 자세한 내용은 [Homebrew 설명서](https://github.com/Homebrew/homebrew/wiki/Installation)를 참조하세요. 개발자 모드를 수동으로 사용하도록 설정하려면 터미널 앱에서 다음 명령을 입력합니다. `DevToolsSecurity -enable`

Visual Studio를 새 버전으로 업데이트하는 경우 현재 원격 에이전트 버전도 업데이트해야 합니다. 원격 에이전트를 업데이트하려면 원격 에이전트 다운로드 및 설치 단계를 반복합니다.

## <a name="start-the-remote-agent"></a><a name="Start"></a> 원격 에이전트 시작

Visual Studio에서 iOS 코드를 빌드 및 실행하려면 원격 에이전트가 실행되고 있어야 합니다. Visual Studio가 원격 에이전트와 쌍으로 연결되어야 통신할 수 있습니다. 기본적으로 원격 에이전트는 Visual Studio와 쌍으로 연결되기 위해 PIN이 필요한 보안된 연결 모드로 실행됩니다.

### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> 원격 에이전트를 시작하려면

- Mac의 터미널 앱에서 다음 명령을 입력합니다.

   `vcremote`

   이렇게 하면 기본 빌드 디렉터리가 `~/vcremote`인 원격 에이전트가 시작됩니다. 추가 구성 옵션은 [Configure the remote agent on the Mac](#ConfigureMac)을 참조하세요.

에이전트를 처음 시작할 때 및 새 클라이언트 인증서를 만들 때마다 호스트 이름, 포트, PIN을 비롯해 Visual Studio에서 에이전트를 구성하는 데 필요한 정보가 표시됩니다.

![vcremote를 사용하여 보안 PIN 생성](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "vcremote를 사용하여 보안 PIN 생성")

Visual Studio에서 호스트 이름을 사용하여 원격 에이전트를 구성하려는 경우 Windows에서 호스트 이름으로 Mac을 ping하여 원격 에이전트에 연결할 수 있는지 확인합니다. 그렇지 않은 경우 대신 IP 주소를 사용해야 할 수도 있습니다.

생성된 PIN은 일회용이며 제한된 시간 동안만 유효합니다. 시간이 만료되기 전에 Visual Studio를 원격 에이전트와 쌍으로 연결하지 않으면 새 PIN을 생성해야 합니다. 자세한 내용은 [Generate a new security PIN](#GeneratePIN)을 참조하세요.

보안되지 않은 모드에서 원격 에이전트를 사용할 수 있습니다. 보안되지 않은 모드에서 PIN 없이 원격 에이전트를 Visual Studio와 쌍으로 연결할 수 있습니다.

#### <a name="to-disable-secured-connection-mode"></a>보안된 연결 모드를 사용하지 않도록 설정하려면

- `vcremote`에서 보안 연결 모드를 사용하지 않도록 설정하려면 Mac의 터미널 앱에서 다음 명령을 입력합니다.

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>보안된 연결 모드를 사용하도록 설정하려면

- 보안된 연결 모드를 사용하도록 설정하려면 다음 명령을 입력합니다.

   `vcremote --secure true`

원격 에이전트를 시작한 후 중지할 때까지 Visual Studio에서 사용할 수 있습니다.

#### <a name="to-stop-the-remote-agent"></a>원격 에이전트를 중지하려면

- 터미널 창이 `vcremote` 에서 실행 되 고 있는 경우 **컨트롤** + **C**를 입력 합니다.

## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> Visual Studio에서 원격 에이전트 구성

Visual Studio에서 원격 에이전트에 연결하려면 Visual Studio 옵션에서 원격 구성을 지정해야 합니다.

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Visual Studio에서 원격 에이전트를 구성하려면

1. Mac에서 에이전트가 실행되고 있지 않은 경우 [원격 에이전트 시작](#Start)의 단계를 따르세요. Visual Studio가 성공적으로 쌍을 이루고 연결한 다음 프로젝트를 빌드하려면 Mac에서 `vcremote`를 실행해야 합니다.

1. Mac에서 Mac의 호스트 이름 또는 IP 주소를 가져옵니다.

   터미널 창에서 **ifconfig** 명령을 사용하여 IP 주소를 가져올 수 있습니다. 활성 네트워크 인터페이스 아래에 나열된 inet 주소를 사용합니다.

1. Visual Studio 메뉴 모음에서 **도구**, **옵션**을 차례로 선택합니다.

1. **옵션** 대화 상자에서 **플랫폼 간**, **C++**, **iOS**를 확장합니다.

1. **호스트 이름** 및 **포트** 필드에서 시작할 때 원격 에이전트에 의해 지정된 값을 입력합니다. 호스트 이름은 Mac의 DNS 이름 또는 IP 주소일 수 있습니다. 기본 포트는 3030입니다.

   > [!NOTE]
   > 호스트 이름을 사용하여 Mac을 ping할 수 없는 경우 IP 주소를 사용해야 할 수도 있습니다.

1. 기본 보안된 연결 모드에서 원격 에이전트를 사용하는 경우 **보안** 확인란을 선택한 다음 **Pin** 필드에 원격 에이전트에 의해 지정된 PIN 값을 입력합니다. 보안되지 않은 연결 모드에서 원격 에이전트를 사용하는 경우 **보안** 확인란을 선택 취소하고 **Pin** 필드를 비워 둡니다.

1. **연결**을 선택하여 연결을 사용하도록 설정합니다.

   ![iOS 빌드에 대한 vcremote 연결 구성](../cross-platform/media/cppmdd-options-ios.png "iOS 빌드에 대한 vcremote 연결 구성")

   호스트 이름 또는 포트를 변경할 때까지 연결이 유지됩니다. **옵션** 대화 상자에서 호스트 이름 또는 포트를 변경하는 경우 변경 내용을 취소하려면 **되돌리기** 단추를 선택하여 이전 연결로 되돌립니다.

   연결이 성공하지 못한 경우 [Start the remote agent](#Start)의 단계에 따라 원격 에이전트가 실행되고 있는지 확인합니다. 원격 에이전트 PIN이 생성된 이후 너무 많은 시간이 경과한 경우 Mac에서 [Generate a new security PIN](#GeneratePIN) 의 단계를 따른 후 다시 시도합니다. Mac의 호스트 이름을 사용하는 경우 **호스트 이름** 필드에 대신 IP 주소를 사용하여 시도합니다.

1. **원격 루트** 필드의 폴더 이름을 업데이트하여 Mac의 홈(*~*) 디렉터리에서 원격 에이전트에 사용되는 폴더를 지정합니다. 기본적으로 원격 에이전트는 `/Users/<username>/vcremote`를 원격 루트로 사용합니다.

1. **확인** 을 선택하여 원격 연결 설정을 저장합니다.

Visual Studio는 사용할 때마다 동일한 정보를 사용하여 Mac의 원격 에이전트에 연결합니다. Mac에서 새 보안 인증서를 생성하거나 해당 호스트 이름 또는 IP 주소가 변경되지 않는 한 Visual Studio를 원격 에이전트와 쌍으로 다시 연결할 필요가 없습니다.

## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Generate a new security PIN

원격 에이전트를 처음 시작하는 경우 생성된 PIN은 제한된 시간(기본적으로 10분) 동안만 유효합니다. 시간이 만료되기 전에 Visual Studio를 원격 에이전트와 쌍으로 연결하지 않으면 새 PIN을 생성해야 합니다.

### <a name="to-generate-a-new-pin"></a>새 PIN을 생성하려면

1. 에이전트를 중지합니다(또는 Mac에서 두 번째 터미널 앱 창을 열고 여기에 명령 입력).

1. 터미널 앱에서 다음 명령을 입력합니다.

   `vcremote generateClientCert`

   원격 에이전트가 새 임시 PIN을 생성합니다. 새 PIN을 사용하여 Visual Studio를 쌍으로 연결하려면 [Visual Studio에서 원격 에이전트 구성](#ConfigureVS)의 단계를 반복합니다.

## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> 새 서버 인증서 생성

보안을 위해, Visual Studio를 원격 에이전트와 연결하는 서버 인증서는 Mac의 IP 주소 또는 호스트 이름에 연결되어 있습니다. 이러한 값이 변경되면 새 서버 인증서를 생성한 후 Visual Studio를 새 값으로 다시 구성해야 합니다.

### <a name="to-generate-a-new-server-certificate"></a>새 서버 인증서를 생성하려면

1. `vcremote` 에이전트를 중지합니다.

1. 터미널 앱에서 다음 명령을 입력합니다.

   `vcremote resetServerCert`

1. 확인 메시지가 표시되면 `Y`을 입력합니다.

1. 터미널 앱에서 다음 명령을 입력합니다.

   `vcremote generateClientCert`

   이 명령은 새 임시 PIN을 생성합니다.

1. 새 PIN을 사용하여 Visual Studio를 쌍으로 연결하려면 [Visual Studio에서 원격 에이전트 구성](#ConfigureVS)의 단계를 반복합니다.

## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Configure the remote agent on the Mac

다양한 명령줄 옵션을 사용하여 원격 에이전트를 구성할 수 있습니다. 예를 들어 빌드 요청을 수신할 포트와 파일 시스템에 유지할 최대 빌드 수를 지정할 수 있습니다. 기본적으로 해당 제한은 10개 빌드입니다. 원격 에이전트는 종료 시 최대값을 초과하는 빌드를 제거합니다.

### <a name="to-configure-the-remote-agent"></a>원격 에이전트를 구성하려면

- 원격 에이전트 명령의 전체 목록을 보려면 터미널 앱에서 다음을 입력합니다.

   `vcremote --help`

- 보안 모드를 사용하지 않도록 설정하고 단순한 HTTP 기반 연결을 사용하려면 다음을 입력합니다.

   `vcremote --secure false`

   이 옵션을 사용하는 경우 Visual Studio에서 에이전트를 구성할 때 **보안** 확인란을 선택 취소하고 **Pin** 필드를 비워 둡니다.

- 원격 에이전트 파일의 위치를 지정하려면 다음을 입력합니다.

   `vcremote --serverDir directory_path`

   여기서 *directory_path* 는 로그 파일, 빌드 및 서버 인증서를 배치할 Mac의 위치입니다. 기본적으로 이 위치는 `/Users/<username>/vcremote`입니다. 빌드는 이 위치에 빌드 번호를 기준으로 구성됩니다.

- 백그라운드 프로세스를 사용하여 `stdout` 및 `stderr` 을 server.log라는 파일에 캡처하려면 다음을 입력합니다.

   `vcremote > server.log 2>&1 &`

   server.log 파일은 빌드 문제를 해결하는 데 도움이 될 수 있습니다.

- 명령줄 매개 변수 대신 구성 파일을 사용하여 에이전트를 실행하려면 다음 명령을 입력합니다.

   `vcremote --config config_file_path`

   여기서 *config_file_path* 는 JSON 형식의 구성 파일 경로입니다. 시작 옵션과 해당 값에 대시가 포함되어서는 안 됩니다.

## <a name="troubleshoot-the-remote-agent"></a>원격 에이전트 문제 해결

### <a name="debugging-on-an-ios-device"></a>iOS 디바이스에서 디버깅

iOS 디바이스에서 디버깅이 작동하지 않는 경우 iOS 디바이스와 통신하는 데 사용되는 [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller) 도구에 문제가 있을 수 있습니다. 이 도구는 일반적으로 `vcremote`를 설치하는 동안 Homebrew에서 설치됩니다. 문제를 해결하려면 아래 단계를 수행합니다.

터미널 앱을 열고 다음을 순서대로 실행하여 `ideviceinstaller` 및 해당 종속성을 업데이트합니다.

1. Homebrew가 업데이트되었는지 확인

   `brew update`

1. `libimobiledevice` 및 `usbmuxd` 제거

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. 최신 버전의 `libimobiledevice` 및 `usbmuxd` 설치

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. `ideviceinstaller` 제거 후 다시 설치

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

디바이스에 설치된 앱을 나열하여 `ideviceinstaller`가 디바이스와 통신할 수 있는지 확인합니다.

`ideviceinstaller -l`

`/var/db/lockdown` 폴더에 액세스할 수 없는 `ideviceinstaller` 오류가 발생하는 경우 다음을 사용하여 폴더의 권한을 변경합니다.

`sudo chmod 777 /var/db/lockdown`

그런 다음 `ideviceinstaller`가 디바이스와 통신할 수 있는지 다시 확인합니다.

## <a name="see-also"></a>참고 항목

- [C++를 사용한 플랫폼 간 모바일 개발 설치](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
