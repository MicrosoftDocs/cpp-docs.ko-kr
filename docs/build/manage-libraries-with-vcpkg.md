---
title: vcpkg를 사용하여 라이브러리 관리
description: Windows, macOS 및 Linux에서 vcpkg를 사용하여 라이브러리를 관리하는 방법을 알아봅니다.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: 88f8bc1cff7b4b04f5e38b5018676e313383733f
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684121"
---
# <a name="manage-libraries-with-vcpkg"></a>vcpkg를 사용하여 라이브러리 관리

[vcpkg를 설치](install-vcpkg.md)하면 로컬 머신에서 라이브러리를 가져오고 빌드하는 데 사용할 수 있습니다.

## <a name="search-the-list-of-available-libraries"></a>사용 가능한 라이브러리 목록 검색

### <a name="windows"></a>[Windows](#tab/windows)

사용 가능한 패키지를 보려면 명령 프롬프트에서 **`vcpkg search`** 를 입력합니다.

이 명령은 *`vcpkg/ports`* 하위 폴더의 제어 파일을 열거합니다. 다음과 같은 목록이 표시됩니다.

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

### <a name="macos"></a>[macOS](#tab/macos)

사용할 수 있는 패키지를 확인하려면 vcpkg 루트 디렉터리로 변경하고 터미널에서 **`./vcpkg search`** 를 입력합니다.

이 명령은 *`vcpkg/ports`* 하위 폴더의 제어 파일을 열거합니다. 다음과 같은 목록이 표시됩니다.

```Terminal
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

```Terminal
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-computer"></a>컴퓨터에 라이브러리 설치

**`vcpkg search`** 를 사용하여 라이브러리 이름을 찾은 후 **`vcpkg install`** 을 사용하여 라이브러리를 다운로드하고 컴파일합니다. vcpkg는 *ports* 디렉터리에 있는 라이브러리의 포트 파일을 사용합니다. 3자리 ID를 지정하지 않으면 vcpkg가 대상 플랫폼(x86-windows, x64-linux.cmake 또는 x64-osx.cmake)의 기본 3자리 ID를 사용하여 설치되고 컴파일됩니다.

Linux 라이브러리의 경우 vcpkg는 gcc가 로컬 시스템에 설치되어 있는지 여부에 따라 다릅니다. macOS에서는 vcpkg가 Clang을 사용합니다.

포트 파일이 종속성을 지정할 때 vcpkg도 해당 항목을 다운로드하고 설치합니다. 다운로드 후 vcpkg는 라이브러리가 사용하는 빌드 시스템과 동일한 시스템을 사용하여 라이브러리를 빌드합니다. CMake 및 MSBuild 프로젝트(Windows)가 선호되지만 MAKE도 다른 빌드 시스템과 함께 지원됩니다. vcpkg가 로컬 컴퓨터에서 지정된 빌드 시스템을 찾을 수 없으면 다운로드하여 설치합니다.

```Terminal
$ ./vcpkg install boost

The following packages will be built and installed:
    boost:x86-macos
  * bzip2:x86-macos
  * zlib:x86-macos
Additional packages (*) will be installed to complete this operation.
```

CMake 프로젝트의 경우 `CMAKE_TOOLCHAIN_FILE`을 사용하여 `find_package()`에서 라이브러리를 사용할 수 있도록 설정합니다. 예를 들면 다음과 같습니다.

```Terminal
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
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

명령줄에서 설치할 특정 옵션을 지정할 수 있습니다. 예를 들어 기본 SSL 백 엔드를 사용하여 curl 라이브러리를 설치하려면 **`./vcpkg install curl[ssl]`** 명령을 사용합니다. 이 명령은 필요한 필수 구성 요소를 설치합니다(필요한 경우 핵심 라이브러리 포함).

### <a name="linux"></a>[Linux](#tab/linux)

사용할 수 있는 패키지를 확인하려면 셸에서 vcpkg 루트 디렉터리로 변경하고 **`./vcpkg search`** 를 입력합니다.

이 명령은 *`vcpkg/ports`* 하위 폴더의 제어 파일을 열거합니다. 다음과 같은 목록이 표시됩니다.

```shell
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

패턴으로 필터링할 수 있습니다(예: **`./vcpkg search ta`** ).

```shell
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-linux-machine"></a>Linux 머신에 라이브러리 설치

**`./vcpkg search`** 를 사용하여 라이브러리 이름을 찾은 후 **`/vcpkg install`** 을 사용하여 라이브러리를 다운로드하고 컴파일합니다. vcpkg는 *`ports`* 디렉터리에 있는 라이브러리의 포트 파일을 사용합니다. 3자리 ID를 지정하지 않으면 vcpkg가 대상 플랫폼의 기본 3자리 ID(예: x64-linux.cmake)를 사용하여 설치되고 컴파일됩니다.

Linux 라이브러리의 경우 vcpkg는 gcc가 로컬 시스템에 설치되어 있는지 여부에 따라 다릅니다.

포트 파일이 종속성을 지정할 때 vcpkg도 해당 항목을 다운로드하고 설치합니다. 다운로드 후 vcpkg는 라이브러리가 사용하는 빌드 시스템과 동일한 시스템을 사용하여 라이브러리를 빌드합니다. CMake 프로젝트를 사용하는 것이 좋지만 MAKE도 다른 빌드 시스템과 함께 지원됩니다. vcpkg가 로컬 컴퓨터에서 지정된 빌드 시스템을 찾을 수 없으면 다운로드하여 설치합니다.

```shell
$ ./vcpkg install boost:x64-linux

The following packages will be built and installed:
    boost:x64-linux
  * bzip2:x64-linux
  * zlib:x64-linux
Additional packages (*) will be installed to complete this operation.
```

CMake 프로젝트의 경우 `CMAKE_TOOLCHAIN_FILE`을 사용하여 `find_package()`에서 라이브러리를 사용할 수 있도록 설정합니다. 예를 들면 다음과 같습니다.

```shell
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
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

명령줄에서 설치할 특정 옵션을 지정할 수 있습니다. 예를 들어 기본 SSL 백 엔드를 사용하여 curl 라이브러리를 설치하려면 **`./vcpkg install curl[ssl]`** 명령을 사용합니다. 이 명령은 필요한 필수 구성 요소를 설치합니다(필요한 경우 핵심 라이브러리 포함).

---

## <a name="list-the-libraries-already-installed"></a>이미 설치된 라이브러리 나열

일부 라이브러리를 설치한 후 Windows에서 **`vcpkg list`** 명령을 사용하여 설치된 라이브러리를 확인할 수 있습니다. Linux와 macOS 명령도 유사합니다.

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

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

다음 예제에서는 Windows에서 지정된 라이브러리만 업그레이드하는 방법을 보여 줍니다. Linux와 macOS 명령도 유사합니다. vcpgk는 필요에 따라 자동으로 종속성을 가져옵니다.

```cmd
c:\users\username\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
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

## <a name="see-also"></a>추가 정보

[vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자](./vcpkg.md)\
[GitHub의 vcpkg](https://github.com/Microsoft/vcpkg)\
[vcpkg 설치](install-vcpkg.md)\
[vcpkg 통합](integrate-vcpkg.md)\
[vcpkg 명령줄 참조](vcpkg-command-line-reference.md)\
[빠른 시작](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[자주 묻는 질문](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)\
[패키지 설치 및 사용 예: SQLite](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)
