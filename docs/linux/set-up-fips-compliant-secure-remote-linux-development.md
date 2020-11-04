---
title: FIPS 규격 보안 원격 Linux 개발 설정
description: 원격 개발을 위해 Visual Studio와 Linux 머신 간에 FIPS 규격 암호화 연결을 설정하는 방법입니다.
ms.date: 01/17/2020
ms.openlocfilehash: b7eb6bfd32d362415eda057bfa78afe80fb9e2f4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924690"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>FIPS 규격 보안 원격 Linux 개발 설정

::: moniker range="<=msvc-150"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다. FIPS 규격 보안 원격 Linux 개발은 Visual Studio 2019 버전 16.5 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="msvc-160"

FIPS(Federal Information Processing Standard) 게시 140-2는 암호화 모듈에 대한 미국 정부 표준입니다. 표준 구현은 NIST에서 유효성을 검사합니다. Windows에서 [FIPS 규격 암호화 모듈에 대한 지원의 유효성](/windows/security/threat-protection/fips-140-validation)을 검사했습니다. Visual Studio 2019 버전 16.5 이상에서는 원격 개발을 위해 Linux 시스템에 대한 보안 FIPS 규격 암호화 연결을 사용할 수 있습니다.

Visual Studio와 원격 Linux 시스템 간에 안전한 FIPS 규격 연결을 설정하는 방법을 소개합니다. 본 가이드는 Visual Studio에서 CMake 또는 MSBuild Linux 프로젝트를 빌드할 때 적용할 수 있습니다. 이 문서는 [원격 Linux 머신에 연결](connect-to-your-remote-linux-computer.md)에서의 FIPS 규격 버전 연결 지침입니다.

## <a name="prepare-a-fips-compliant-connection"></a>FIPS 규격 연결 준비

Visual Studio와 원격 Linux 시스템 간의 FIPS 규격 암호화 보안 SSH 연결을 사용하려면 몇 가지 준비가 필요합니다. FIPS-140-2 규격의 경우 Visual Studio는 RSA 키만 지원합니다.

이 문서의 예제에서는 OpenSSH 서버 버전 7.6과 함께 Ubuntu 18.04 LTS를 사용합니다. 그러나 OpenSSH의 비교적 최근 버전을 사용하는 모든 배포판에 대한 지침은 동일해야 합니다.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>원격 시스템에서 SSH 서버 설정

1. Linux 시스템에서 OpenSSH 서버를 설치하고 시작합니다.

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 시스템이 부팅될 때 SSH 서버가 자동으로 시작되도록 하려면 systemctl을 사용하여 사용하도록 설정합니다.

   ```bash
   sudo systemctl enable ssh
   ```

1. 루트로 */etc/ssh/sshd_config* 를 엽니다. 다음 줄을 편집(또는 없는 경우, 추가)합니다.

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa는 유일하게 Virtual Studio가 지원하는 FIPS 규격 호스트 키 알고리즘입니다. aes\*-ctr 알고리즘은 FIPS 규격이기는 하지만 Visual Studio에서 구현이 승인되지 않았습니다. ecdh\* 키 교환 알고리즘은 FIPS 규격이지만 Visual Studio에서 지원하지 않습니다.

   하지만 이러한 옵션으로 제한되지 않고, 추가 암호화, 호스트 키 알고리즘 등을 사용하도록 SSH를 구성할 수 있습니다. 고려해야 할 다른 관련 보안 옵션은 `PermitRootLogin`, `PasswordAuthentication` 및 `PermitEmptyPasswords`입니다. 자세한 내용은 sshd_config에 대한 기본 페이지 또는 [SSH 서버 구성](https://www.ssh.com/ssh/sshd_config) 문서를 참조하세요.

1. sshd_config를 저장하고 닫은 후 SSH 서버를 다시 시작하여 새 구성을 적용합니다.

   ```bash
   sudo service ssh restart
   ```

다음으로 Windows 컴퓨터에 RSA 키 쌍을 만듭니다. 그런 다음 SSH에서 사용하기 위해 공개 키를 원격 Linux 시스템에 복사합니다.

### <a name="to-create-and-use-an-rsa-key-file"></a>RSA 키 파일을 만들고 사용하기

1. Windows 컴퓨터에서 다음 명령을 사용하여 퍼블릭/프라이빗 RSA 키 쌍을 생성합니다.

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   이 명령은 퍼블릭 키와 프라이빗 키를 만듭니다. 기본적으로 키는 *%USERPROFILE%\\.ssh\\id_rsa* 및 *%USERPROFILE%\\.ssh\\id_rsa.pub* 에 저장됩니다. (Powershell에서는 cmd 매크로 `$env:USERPROFILE` 대신 `%USERPROFILE%`을 사용) 키 이름을 변경하는 경우 이어지는 다음 단계에서 변경된 이름을 사용합니다.  보안 강화를 위해 암호를 사용하는 것이 좋습니다.

1. Windows에서 Linux 머신으로 퍼블릭 키를 복사합니다.

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. Linux 시스템에서 권한 있는 키 목록에 키를 추가하고 파일에 올바른 권한이 있는지 확인합니다.

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. 이제 SSH에서 새 키가 작동하는지 테스트하여 확인할 수 있습니다. Windows에서 로그인하는 데 사용:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

SSH를 성공적으로 설정하고, 암호화 키를 생성 및 배포하고, 연결을 테스트했습니다. 이제 Visual Studio 연결을 설정할 준비가 되었습니다.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Visual Studio에서 원격 시스템에 연결

1. Visual Studio의 메뉴 모음에서 **도구 > 옵션** 을 선택하여 **옵션** 대화 상자를 엽니다. 그런 다음 **플랫폼 간 > 연결 관리자** 를 선택하여 연결 관리자 대화 상자를 엽니다.

   이전에 Visual Studio에서 연결을 설정하지 않은 경우 프로젝트를 처음 빌드할 때 Visual Studio에서 연결 관리자 대화 상자를 엽니다.

1. 연결 관리자 대화 상자에서 **추가** 단추를 선택하여 새 연결을 추가합니다.

   ![연결 관리자](media/settings_connectionmanager.png)

   **원격 시스템에 연결** 창이 표시됩니다.

   ![원격 시스템에 연결](media/connect.png)

1. **원격 시스템에 연결** 대화 상자에서 원격 머신의 연결 정보를 입력합니다.

   | 입력 | 설명
   | ----- | ---
   | **호스트 이름**           | 대상 디바이스의 이름 또는 IP 주소
   | **포트**                | SSH 서비스가 실행되는 포트(일반적으로 22)
   | **사용자 이름**           | 인증할 사용자
   | **인증 형식** | FIPS 규격 연결에 대한 프라이빗 키 선택
   | **프라이빗 키 파일**    | SSH 연결을 위해 생성된 프라이빗 키 파일
   | **암호**          | 위에서 선택한 프라이빗 키와 함께 사용된 암호

   인증 유형을 **프라이빗 키** 로 변경합니다. 프라이빗 키의 경로를 **프라이빗 키 파일** 필드에 입력합니다. **찾아보기** 단추를 사용하여 대신 프라이빗 키 파일로 이동할 수 있습니다. 그런 다음 **암호** 필드에서 프라이빗 키 파일을 암호화하는 데 사용되는 암호를 입력합니다.

1. **연결** 단추를 선택하여 원격 컴퓨터에 대한 연결을 시도합니다.

   연결에 성공하면 Visual Studio에서 원격 헤더를 사용하도록 IntelliSense를 구성합니다. 자세한 내용은 [원격 시스템의 헤더에 대한 IntelliSense](configure-a-linux-project.md#remote_intellisense)를 참조하세요.

   연결이 실패하면 변경해야 하는 입력 상자에 빨간색 윤곽선이 표시됩니다.

   ![연결 관리자 오류](media/settings_connectionmanagererror.png)

   연결 문제를 해결하는 방법에 관한 자세한 내용은 [원격 Linux 컴퓨터에 연결](connect-to-your-remote-linux-computer.md)을 참조하세요.

## <a name="command-line-utility-for-the-connection-manager"></a>연결 관리자에 대한 명령줄 유틸리티  

**Visual Studio 2019 버전 16.5 이상** : ConnectionManager.exe는 Visual Studio 외부에서 원격 개발 연결을 관리하는 명령줄 유틸리티입니다. 새 개발 컴퓨터를 프로비저닝하는 등의 작업에 유용합니다. 또는 연속 통합을 위해 Visual Studio를 설정하는 데 사용할 수 있습니다. ConnectionManager 명령에 대한 예제 및 전체 참조는 [ConnectionManager 참조](connectionmanager-reference.md)를 참조하세요.  

## <a name="optional-enable-or-disable-fips-mode"></a>선택 사항: FIPS 모드 사용 또는 사용 안 함

Windows에서 FIPS 모드를 전역적으로 사용하도록 설정할 수 있습니다.

1. FIPS 모드를 사용하도록 설정하려면 **Windows+R** 을 눌러 실행 대화 상자를 연 다음 gpedit.msc를 실행합니다.

1. **로컬 컴퓨터 정책 > 컴퓨터 구성 > Windows 설정 > 보안 설정 > 로컬 정책** 을 확장하고 **보안 옵션** 을 선택합니다.

1. **정책** 에서 **시스템 암호화: 암호화, 해시 및 서명에 FIPS 규격 알고리즘을 사용** 을 선택한 다음, **엔터** 키를 눌러 해당 대화 상자를 엽니다.

1. **로컬 보안 설정** 탭에서 **사용** 또는 **사용 안 함** 을 선택하고 **확인** 을 선택하여 변경 내용을 저장합니다.

> [!WARNING]
> FIPS 모드를 사용하도록 설정하면 일부 애플리케이션이 예기치 않게 중단되거나 동작하지 않을 수 있습니다. 자세한 내용은 블로그 게시물 [“FIPS 모드”를 더 이상 권장하지 않는 이유](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)를 참조하세요.

## <a name="additional-resources"></a>추가 자료

[FIPS 140 유효성 검사에 대한 Microsoft 설명서](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: 암호화 모듈에 대한 보안 요구 사항](https://csrc.nist.gov/publications/detail/fips/140/2/final)(NIST 기준)

[암호화 알고리즘 유효성 검사 프로그램: 유효성 검사 참고 사항](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes)(NIST 기준)

[“FIPS 모드”를 더 이상 권장하지 않는 이유](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)에 대한 Microsoft 블로그 게시물

[SSH 서버 구성](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>관련 항목

[Linux 프로젝트 구성](configure-a-linux-project.md)\
[Linux CMake 프로젝트 구성](cmake-linux-project.md)\
[원격 Linux 컴퓨터에 연결](connect-to-your-remote-linux-computer.md)\
[Linux 프로젝트 배포, 실행 및 디버그](deploy-run-and-debug-your-linux-project.md)\
[CMake 디버깅 세션 구성](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
