---
title: 'vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자'
description: vcpkg는 Windows, macOS 및 Linux에서 오픈 소스 C++ 라이브러리 획득 및 설치를 크게 간소화하는 명령줄 패키지 관리자입니다.
ms.date: 07/06/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: ec908824c19099ad6eaa46a4d85c0187ef12b3fd
ms.sourcegitcommit: 102bd6f7a878d85c8ceab8f28d0359f562850ea0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862557"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자

vcpkg는 C++ 용 명령줄 패키지 관리자입니다. vcpkg는 Windows, Linux 및 macOS에서 타사 라이브러리 획득 및 설치를 크게 간소화합니다. 프로젝트에서 타사 라이브러리를 사용하는 경우 vcpkg를 사용하여 설치하는 것이 좋습니다. vcpkg는 오픈 소스와 독점 라이브러리를 모두 지원합니다. vcpkg Windows 카탈로그의 모든 라이브러리가 isual Studio 2015, Visual Studio 2017 및 Visual Studio 2019와의 호환성 테스트를 거쳤습니다. vcpkg는 현재 Windows 및 Linux/macOS 카탈로그 사이에서 1,900개 이상의 라이브러리를 지원합니다. C++ 커뮤니티는 지속적으로 두 카탈로그에 더 많은 라이브러리를 추가하고 있습니다.

## <a name="simple-yet-flexible"></a>단순하면서도 유연한

하나의 명령으로 소스를 다운로드하고 라이브러리를 구축할 수 있습니다. vcpkg는 그 자체가 GitHub에서 사용할 수 있는 오픈 소스 프로젝트입니다. 원하는 방식으로 프라이빗 vcpkg 클론을 사용자 지정할 수 있습니다. 예를 들어 다른 라이브러리 또는 공용 카탈로그에서 발견되는 것과는 다른 버전의 라이브러리를 지정할 수 있습니다. 단일 컴퓨터에 여러 개의 vcpkg 복제본을 가질 수 있습니다. 각 항목은 원하는 컴파일 스위치를 사용하여 라이브러리의 사용자 지정 컬렉션을 생성하도록 설정될 수 있습니다. 각 복제본은 자체 계층에서만 작동하는 vcpkg.exe의 자체 복사본이 포함된 자체 포함 환경입니다. vcpkg는 어떤 환경 변수에도 추가되지 않으며 Windows 레지스트리 또는 Visual Studio에 종속되지 않습니다.

## <a name="sources-not-binaries"></a>이진 파일이 아닌 소스

Windows 카탈로그에 있는 라이브러리의 경우 vcpkg는 이진 파일<sup>1</sup> 대신 소스를 다운로드합니다. 찾을 수 있는 가장 최신 Visual Studio 버전을 사용하여 해당 소스를 컴파일합니다. C++에서는 애플리케이션 코드와 사용하는 모든 라이브러리가 동일한 컴파일러 및 컴파일러 버전을 사용하여 컴파일되어야 합니다. vcpkg를 사용하여 이진 파일 불일치 및 이로 인해 발생할 수 있는 문제를 제거하거나 적어도 크게 줄일 수 있습니다. 특정 버전의 컴파일러에서 표준화된 팀에서는 한 팀 구성원이 vcpkg를 사용하여 소스를 다운로드하고 이진 파일 집합을 컴파일할 수 있습니다. 그런 다음 내보내기 명령을 사용하여 이진 파일과 헤더를 압축하여 다른 팀 구성원에게 내보낼 수 있습니다. 자세한 내용은 아래의 [컴파일된 이진 파일 및 헤더 내보내기](#export_binaries_per_project)를 참조하세요.

또한 포트 컬렉션에 프라이빗 라이브러리가 있는 vcpkg 클론을 만들 수 있습니다. 미리 작성된 이진 파일 및 헤더를 다운로드하는 포트를 추가합니다. 그런 다음, 해당 파일을 기본 위치에 단순히 복사하는 *portfile.cmake* 파일을 작성합니다.

<sup>1</sup> *참고: 일부 독점 라이브러리에서는 소스를 사용할 수 없습니다. 이러한 경우 vcpkg는 호환되는 미리 작성된 이진 파일을 다운로드합니다.*

## <a name="installation"></a>설치

GitHub에서 vcpkg 리포지토리([https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg))를 복제합니다. 원하는 폴더 위치에 다운로드할 수 있습니다. 이 위치는 vcpkg ‘루트’입니다. 다운로드가 완료되면 명령 셸에서 해당 디렉터리로 변경합니다.

vcpkg 루트 디렉터리에서 vcpkg 부트스트래퍼를 실행합니다.

- **`bootstrap-vcpkg.bat`** (Windows)
- **`./bootstrap-vcpkg.sh`** (Linux, macOS)

Linux 또는 macOS에서는 다음 예제에서 vcpkg 명령에 **`./`** 를 접두사로 추가해야 할 수 있습니다. vcpkg 루트 디렉터리에서 해당 명령을 실행해야 합니다.

## <a name="search-the-list-of-available-libraries"></a>사용 가능한 라이브러리 목록 검색

사용 가능한 패키지를 보려면 명령 프롬프트에서 **`vcpkg search`** 를 입력합니다.

이 명령은 *vcpkg/ports* 하위 폴더에 제어 파일을 열거합니다. 다음과 같은 목록이 표시됩니다.

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

패턴으로 필터링할 수 있습니다(예: **`vcpkg search ta`** ).

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>로컬 컴퓨터에 라이브러리 설치

**`vcpkg search`** 를 사용하여 라이브러리 이름을 찾은 후 **`vcpkg install`** 을 사용하여 라이브러리를 다운로드하고 컴파일합니다. vcpkg는 *ports* 디렉터리에 있는 라이브러리의 포트 파일을 사용합니다. 3자리 ID를 지정하지 않으면 vcpkg가 대상 플랫폼(x86-windows, x64-linux.cmake 또는 x64-osx.cmake)의 기본 3자리 ID를 사용하여 설치되고 컴파일됩니다.

Linux 라이브러리의 경우 vcpkg는 gcc가 로컬 시스템에 설치되어 있는지 여부에 따라 다릅니다. macOS에서는 vcpkg가 Clang을 사용합니다.

포트 파일이 종속성을 지정할 때 vcpkg도 해당 항목을 다운로드하고 설치합니다. 다운로드 후 vcpkg는 라이브러리가 사용하는 빌드 시스템과 동일한 시스템을 사용하여 라이브러리를 빌드합니다. CMake 및 MSBuild 프로젝트(Windows)가 선호되지만 MAKE도 다른 빌드 시스템과 함께 지원됩니다. vcpkg가 로컬 컴퓨터에서 지정된 빌드 시스템을 찾을 수 없으면 다운로드하여 설치합니다.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

CMake 프로젝트의 경우 `CMAKE_TOOLCHAIN_FILE`을 사용하여 `find_package()`에서 라이브러리를 사용할 수 있도록 설정합니다. 예를 들어 Linux 또는 macOS에서:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake
```

Windows에서:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake
```

일부 라이브러리에는 설치 가능한 옵션이 포함됩니다. 예를 들어 curl 라이브러리를 검색하면 대괄호로 묶인 지원되는 옵션 목록도 표시됩니다.

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

이 경우 **`[`** 및 **`]`** 대괄호는 메타 문자가 아닌 리터럴입니다.

명령줄에서 설치할 특정 옵션을 지정할 수 있습니다. 예를 들어 Windows용 기본 SSL 백 엔드를 사용하여 curl 라이브러리를 설치하려면 **`vcpkg install curl[ssl]:x86-windows`** 명령을 사용합니다. 이 명령은 필요한 필수 구성 요소를 설치합니다(필요한 경우 핵심 라이브러리 포함).

```cmd
> vcpkg list
curl:x86-windows            7.68.0-3   A library for transferring data with URLs
curl[non-http]:x86-windows             Enables protocols beyond HTTP/HTTPS/HTTP2
curl[ssl]:x86-windows                  Default SSL backend
curl[sspi]:x86-windows                 SSPI support
curl[winssl]:x86-windows               SSL support (Secure Channel / "WinSSL")
zlib:x86-windows            1.2.11-6   A compression library
```

## <a name="list-the-libraries-already-installed"></a>이미 설치된 라이브러리 나열

일부 라이브러리를 설치한 후 어떤 라이브러리를 갖고 있는지 **`vcpkg list`** 를 사용하여 확인할 수 있습니다.

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Visual Studio와 통합(Windows)

### <a name="per-user"></a>사용자 단위

**`vcpkg integrate install`** 을 실행하여 사용자 단위로 모든 vcpkg 헤더 파일과 이진 파일을 찾도록 Visual Studio를 구성할 수 있습니다. VC + + 디렉터리 경로를 수동으로 편집할 필요가 없습니다. vcpkg의 클론이 여러 개 있는 경우 이 명령을 실행하는 클론이 새 기본 위치가 됩니다.

이제 폴더/헤더를 입력하는 것만으로 헤더를 포함할 수 있으며 자동 완성이 도움이 됩니다. 라이브러리에 연결하거나 프로젝트 참조를 추가하는 추가 단계는 필요 없습니다. 다음 그림에서는 Visual Studio가 azure-storage-cpp 헤더를 찾는 방법을 보여 줍니다. vcpkg는 대상 플랫폼으로 분할된 */installed* 하위 폴더에 헤더를 배치합니다. 다음 다이어그램에서는 라이브러리의 */was* 하위 폴더에 있는 포함 파일의 목록을 보여줍니다.

![vcpkg 및 IntelliSense](media/vcpkg-intellisense.png "vcpkg 및 IntelliSense")

### <a name="per-project"></a>프로젝트 단위

활성 vcpkg 인스턴스에서 버전과 다른 라이브러리의 특정 버전을 사용해야 하는 경우 다음 단계를 따르세요.

1. vcpkg의 새 클론을 생성합니다.
1. 필요한 버전을 가져오도록 라이브러리의 프로필을 수정합니다.
1. **`vcpkg install <library>`** 를 실행합니다.
1. **`vcpkg integrate project`** 를 사용하여 프로젝트 단위로 해당 라이브러리를 참조하는 NuGet 패키지를 만듭니다.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Visual Studio Code와 통합(Linux/macOS)

**`vcpkg integrate install`** 을 실행하여 Linux/macOS에서 Visual Studio Code를 구성합니다. 이 명령은 vcpkg 인리스트먼트 위치를 설정하고 소스 파일에서 IntelliSense를 사용하도록 설정합니다.

## <a name="target-linux-from-windows-via-wsl"></a>WSL을 통해 Windows에서 Linux 대상 지정

WSL(Linux용 Windows 하위 시스템)을 사용하여 Windows 컴퓨터에서 Linux 바이너리를 생성할 수 있습니다. 지침에 따라 [Windows 10에서 WSL을 설정](/windows/wsl/install-win10)합니다. 그런 다음, [Linux용 Visual Studio 확장](https://devblogs.microsoft.com/cppblog/targeting-windows-subsystem-for-linux-from-visual-studio/)을 사용하여 구성합니다. Windows 및 Linux용으로 빌드된 모든 라이브러리를 동일한 폴더에 배치하는 것이 좋습니다. Windows 및 WSL 모두에서 액세스할 수 있습니다.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> 컴파일된 이진 파일 및 헤더 내보내기

팀의 모든 사용자가 공통 라이브러리를 다운로드하고 작성하는 것은 비효율적입니다. 단일 팀 멤버는 **`vcpkg export`** 명령을 사용하여 이진 파일 및 헤더의 일반 zip 파일 또는 NuGet 패키지를 만들 수 있습니다. 그런 다음 다른 팀 멤버와 공유하기가 쉽습니다.

## <a name="updateupgrade-installed-libraries"></a>설치된 라이브러리 업데이트/업그레이드

공용 카탈로그는 라이브러리의 최신 버전으로 최신 상태로 유지됩니다. 로컬 라이브러리 중 어떤 것이 오래되었는지 확인하려면 **`vcpkg update`** 를 사용합니다. 포트 컬렉션을 공용 카탈로그의 최신 버전으로 업데이트할 준비가 되면 **`vcpkg upgrade`** 명령을 실행합니다. 최신 버전이 아닌 설치된 모든 라이브러리를 자동으로 다운로드하여 다시 작성합니다.

기본적으로는 **`vcpkg upgrade`** 명령은 만료된 라이브러리를 나열할 뿐 업그레이드하지는 않습니다. 실제로 라이브러리를 업그레이드하려면 **`--no-dry-run`** 옵션을 사용합니다.

```cmd
> vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>업그레이드 옵션

- **`--no-dry-run`** 업그레이드를 수행합니다. 지정되지 않은 경우 명령은 만료된 패키지를 나열합니다.
- **`--keep-going`** 한 번 실패하더라도 패키지를 계속 설치합니다.
- **`--triplet <t>`** 정규화되지 않은 패키지의 기본 3자리 ID를 설정합니다.
- **`--vcpkg-root <path>`** 현재 디렉터리 또는 도구 디렉터리 대신 사용할 vcpkg 디렉터리를 지정합니다.

### <a name="upgrade-example"></a>업그레이드 예제

다음 예제에서는 지정된 라이브러리를 업그레이드하는 방법을 보여줍니다. vcpgk는 필요에 따라 자동으로 종속성을 가져옵니다.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>새 라이브러리 제공

원하는 모든 라이브러리를 개인 포트 컬렉션에 포함할 수 있습니다. 공용 카탈로그에 대한 새 라이브러리를 제안하려면 [GitHub vcpkg 문제 페이지](https://github.com/Microsoft/vcpkg/issues)에서 문제를 엽니다.

## <a name="remove-a-library"></a>라이브러리 제거

**`vcpkg remove`** 를 입력하여 설치된 라이브러리를 제거합니다. 종속된 라이브러리가 있는 경우 모든 다운스트림 라이브러리가 제거되는 **`--recurse`** 를 사용하여 명령을 다시 실행하라는 메시지가 표시됩니다.

## <a name="customize-vcpkg"></a>Vcpkg 사용자 지정

원하는 어떤 방식으로든 vcpkg의 클론을 수정할 수 있습니다. 여러 vcpkg 클론을 만든 다음 각 클론에서 포트 파일을 수정할 수도 있습니다. 이 방법은 특정 라이브러리 버전을 얻거나 특정 명령줄 매개 변수를 지정하는 간단한 방법입니다. 예를 들어 기업의 개별 개발자 그룹은 해당 그룹과 관련된 종속성이 있는 소프트웨어에서 작업할 수 있습니다. 해결 방법은 각 팀에 대해 vcpkg의 클론을 설정하는 것입니다. 그런 다음 복제본을 수정하여 라이브러리 버전을 다운로드하고 각 팀에 필요한 컴파일 스위치를 설정합니다.

## <a name="update-vcpkg"></a>vcpkg 업데이트

vcpkg 패키지 관리자는 GitHub에서 정기적으로 업데이트됩니다. vcpkg의 클론을 최신 버전으로 업데이트하려면 vcpkg 루트 디렉터리에서 **`git pull`** 을 실행합니다. 이 명령은 vcpkg의 복사본을 GitHub의 버전과 동기화합니다. 다운로드가 완료되면 부트스트래퍼를 다시 실행합니다. 부트스트래퍼가 vcpkg 프로그램을 다시 빌드하지만 설치된 라이브러리는 그대로 둡니다.

## <a name="uninstall-vcpkg"></a>vcpkg 제거

vcpkg를 제거하려면 vcpkg 디렉터리를 삭제하면 됩니다. 이 디렉터리를 삭제하면 vcpkg 배포 및 vcpkg에 의해 설치된 모든 라이브러리가 제거됩니다.

그러나 **`vcpkg integrate install`** 을 실행한 경우 폴더가 제거되기 전에 **`vcpkg integrate remove`** 를 실행하여 통합이 정리되었는지 확인해야 합니다.

## <a name="send-feedback-about-vcpkg"></a>vcpkg에 대한 사용자 의견 보내기

**`vcpkg contact --survey`** 명령을 사용하여 버그 신고 및 기능 제안을 비롯한 vcpkg 관련 피드백을 Microsoft에 보냅니다.

## <a name="the-vcpkg-folder-hierarchy"></a>Vcpkg 폴더 계층 구조

모든 vcpkg 기능 및 데이터는 단일 디렉터리 계층 구조에서 독립적이며 "인스턴스"라고 합니다. 레지스트리 설정 또는 환경 변수는 없습니다. 한 컴퓨터에 vcpkg의 인스턴스가 얼마든지 있을 수 있으며 서로를 방해하지 않습니다.

Vcpkg 인스턴스의 내용:

- buildtrees - 빌드된 각 라이브러리의 소스의 하위 폴더 포함
- docs - 설명서 및 예제
- downloads - 다운로드된 도구 또는 소스의 캐시 복사본. 설치 명령을 실행하면 vcpkg는 여기를 먼저 검색합니다.
- installed - 설치된 각 라이브러리의 헤더 및 이진 파일 포함. Visual Studio와 통합하는 것은 본질적으로 이 폴더를 검색 경로에 추가하는 것입니다.
- packages - 단계적 설치를 위한 내부 폴더
- ports - 카탈로그의 각 라이브러리, 버전 및 다운로드 위치를 설명하는 파일. 필요한 경우 고유한 포트를 추가할 수 있습니다.
- scripts - vcpkg가 사용하는 스크립트(CMake, PowerShell)
- toolsrc - vcpkg 및 관련 구성 요소에 대한 C++ 소스 코드
- triplets - 지원되는 각 대상 플랫폼(예: x86-windows 또는 x64-uwp)에 대한 설정 포함

## <a name="command-line-reference"></a>명령줄 참조

|명령|설명|
|---------|---------|
|**`vcpkg search [pat]`**|설치할 수 있는 패키지 검색|
|**`vcpkg install <pkg>...`**|패키지 설치|
|**`vcpkg remove <pkg>...`**|패키지 제거|
|**`vcpkg remove --outdated`**|만료된 패키지 모두 제거|
|**`vcpkg list`**|설치된 패키지 나열|
|**`vcpkg update`**|업데이트할 패키지 목록 표시|
|**`vcpkg upgrade`**|만료된 모든 패키지 다시 빌드|
|**`vcpkg hash <file> [alg]`**|특정 알고리즘에 따라 파일 해시, 기본 SHA512|
|**`vcpkg integrate install`**|설치된 패키지를 누구나 사용할 수 있도록 설정 처음 사용할 때 관리자 권한 필요|
|**`vcpkg integrate remove`**|사용자 수준 통합 제거|
|**`vcpkg integrate project`**|개별 VS 프로젝트 사용을 위한 참조 NuGet 패키지 생성|
|**`vcpkg export <pkg>... [opt]...`**|패키지 내보내기|
|**`vcpkg edit <pkg>`**|편집할 포트 열기(%EDITOR% 사용, 기본 '코드')|
|**`vcpkg create <pkg> <url> [archivename]`**|새 패키지 만들기|
|**`vcpkg cache`**|컴파일된 캐시 패키지 나열|
|**`vcpkg version`**|버전 정보 표시|
|**`vcpkg contact --survey`**|사용자 의견을 보낼 연락처 정보를 표시합니다.|

### <a name="options"></a>옵션

|옵션|설명|
|---------|---------|
|**`--triplet <t>`**|세 가지 대상 아키텍처를 지정합니다. (기본값: `%VCPKG_DEFAULT_TRIPLET%`, **`vcpkg help triplet`** 참조)|
|**`--vcpkg-root <path>`**|vcpkg 루트 디렉터리 지정(기본값: `%VCPKG_ROOT%`)|
