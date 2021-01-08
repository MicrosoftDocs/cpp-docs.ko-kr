---
title: Windows, Linux 및 macOS에서 vcpkg 설치
description: Windows, macOS 및 Linux에서 vcpkg를 설치하고 업데이트하는 방법을 알아봅니다.
ms.date: 12/17/2020
ms.topic: reference
ms.technology: cpp-ide
ms.openlocfilehash: aee9561dc94164c08e4d69ec49f60961392c1854
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684117"
---
# <a name="install-vcpkg-on-windows-linux-and-macos"></a>Windows, Linux 및 macOS에서 vcpkg 설치

vcpkg GitHub 리포지토리에서 로컬 클론(복사본)을 만들어 vcpkg를 설치합니다.

## <a name="install-vcpkg"></a>vcpkg 설치

구체적인 지침을 보려면 플랫폼을 선택합니다.

### <a name="linux"></a>[Linux](#tab/linux)

Linux의 필수 조건:

- [Git](https://git-scm.com/downloads)
- g++ 버전 6 이상

#### <a name="to-install-linux-development-tools"></a>Linux 개발 도구를 설치하는 방법

Linux 배포가 다르면 다른 패키지를 설치해야 할 수 있습니다. Debian, Ubuntu, popOS 및 기타 Debian 기반 배포에서는 다음 지침을 따르세요.

1. 셸 창에서 다음 명령을 실행합니다.

   **`sudo apt-get update`**

1. 업데이트가 완료되면 다음 명령을 실행합니다.

   **`sudo apt-get install build-essential tar curl zip unzip`**

CentOS에서는 다음 지침을 따르세요.

1. 셸 창에서 다음 명령을 실행합니다.

   **`sudo yum install centos-release-scl`**

1. 그런 다음, 다음 명령을 실행하여 개발 도구를 설치하고 사용하도록 설정합니다.

   **`sudo yum install devtoolset-7`**

   **`scl enable devtoolset-7 bash`**

기타 모든 배포에서는 g++ 6 이상을 설치해야 합니다.

#### <a name="to-copy-and-set-up-vcpkg-on-linux"></a>Linux에서 vcpkg를 복사하고 설정하는 방법

1. 셸 창에서 복제된 vcpkg 인스턴스의 디렉터리를 만듭니다. 다른 빌드 대상을 위한 라이브러리를 설치하려는 경우 대상을 디렉터리 이름에 포함하는 것이 좋습니다. 공백 없는 짧은 경로 이름(예: *`./x64`* 또는 *`./iot`* )을 사용하는 것이 좋습니다. 그러지 않으면 일부 포트 빌드 시스템에서 경로 문제가 발생할 수 있기 때문입니다. 셸 창에서 방금 만든 디렉터리로 변경합니다.

1. GitHub에서 vcpkg 리포지토리([https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg))를 복제합니다.

   > **`git clone https://github.com/microsoft/vcpkg`**

   이 명령은 리포지토리의 로컬 복사본을 *`vcpkg`* 하위 디렉터리에 만듭니다. 이 위치는 이 vcpkg 클론의 vcpkg ‘루트 디렉터리’입니다.

1. 그런 다음, vcpkg 루트 디렉터리로 변경하고 다음 vcpkg 부트스트래퍼 명령을 실행합니다.

   > **`./bootstrap-vcpkg.sh`**

   부트스트래퍼는 컴파일러, 도구 및 표준 라이브러리의 위치를 사용하여 vcpkg를 구성합니다.

### <a name="macos"></a>[macOS](#tab/macos)

macOS의 필수 조건:

- macOS 개발자 도구
- macOS 10.14 이하에서는 다음도 필요합니다.
  - Homebrew
  - g++ 버전 6 이상

#### <a name="to-install-macos-developer-tools"></a>macOS 개발자 도구를 설치하는 방법

1. macOS 10.15에서는 터미널에서 다음 명령을 실행합니다.

   **`xcode-select --install`**

   그런 다음, 표시되는 창의 프롬프트를 따릅니다.

macOS 10.14 이하에서는 Homebrew에서 g++도 설치해야 합니다. 이 절차는 macOS 10.15 이전 버전을 사용하는 경우에만 필요합니다.

#### <a name="to-install-gcc-for-macos-before-1015"></a>macOS 10.15 이전 버전용 GCC를 설치하는 방법

1. Homebrew를 설치하려면 터미널을 열고 다음 명령을 실행합니다.

   **`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`**

1. 최신 버전의 GCC를 설치하려면 터미널에서 다음 명령을 실행합니다.

   **`brew install gcc`**

#### <a name="to-copy-and-set-up-vcpkg-on-macos"></a>macOS에서 vcpkg를 복사하고 설정하는 방법

1. 터미널에서 복제된 vcpkg 인스턴스의 디렉터리를 만듭니다. 다른 빌드 대상을 위한 라이브러리를 설치하려는 경우 대상을 디렉터리 이름에 포함하는 것이 좋습니다. 공백 없는 짧은 경로 이름(예: *`./macos`* 또는 *`./iot`* )을 사용하는 것이 좋습니다. 그러지 않으면 일부 포트 빌드 시스템에서 경로 문제가 발생할 수 있기 때문입니다. 터미널에서 방금 만든 디렉터리로 변경합니다.

1. GitHub에서 vcpkg 리포지토리([https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg))를 복제합니다.

   > **`git clone https://github.com/microsoft/vcpkg`**

   이 명령은 리포지토리의 로컬 복사본을 *`vcpkg`* 하위 디렉터리에 만듭니다. 이 위치는 이 vcpkg 클론의 vcpkg ‘루트 디렉터리’입니다.

1. 그런 다음, vcpkg 루트 디렉터리로 변경하고 다음 vcpkg 부트스트래퍼 명령을 실행합니다.

   > **`./bootstrap-vcpkg.sh`**

   부트스트래퍼는 컴파일러, 도구 및 표준 라이브러리의 위치를 사용하여 vcpkg를 구성합니다.

### <a name="windows"></a>[Windows](#tab/windows)

필수 조건:

- Windows 7 이상
- [Windows용 GIT](https://git-scm.com/downloads)
- 영어 언어 팩이 포함된 [Visual Studio](https://visualstudio.microsoft.com/) 2015 업데이트 3 이상

#### <a name="to-copy-and-set-up-vcpkg-on-windows"></a>Windows에서 vcpkg를 복사하고 설정하는 방법

1. 명령 프롬프트 창에서 복제된 vcpkg 인스턴스의 디렉터리를 만듭니다. 다른 빌드 대상을 위한 라이브러리를 설치하려는 경우 대상을 디렉터리 이름에 포함하는 것이 좋습니다. 공백 없는 짧은 경로 이름(예: *`C:\src\win32\`* 또는 *`C:\dev\iot\`* )을 사용하는 것이 좋습니다. 그러지 않으면 일부 포트 빌드 시스템에서 경로 문제가 발생할 수 있기 때문입니다. 명령 창에서 방금 만든 디렉터리로 변경합니다.

1. GitHub에서 vcpkg 리포지토리([https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg))를 복제합니다.

   > **`git clone https://github.com/microsoft/vcpkg`**

   이 명령은 리포지토리의 로컬 복사본을 *`vcpkg`* 하위 디렉터리에 만듭니다. 이 위치는 이 vcpkg 클론의 vcpkg ‘루트 디렉터리’입니다.

1. 다운로드가 완료되면 명령 프롬프트 창에서 *`vcpkg`* 디렉터리로 변경합니다.

1. vcpkg 루트 디렉터리에서 다음 vcpkg 부트스트래퍼 명령을 실행합니다.

   > **`bootstrap-vcpkg.bat`**

   부트스트래퍼는 Microsoft C/C++ 도구, 라이브러리 및 Windows SDK의 위치를 사용하여 vcpkg를 구성합니다.

---

vcpkg가 설정되면 라이브러리를 설치할 수 있습니다. 자세한 내용은 [vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)를 참조하세요. vcpkg를 Windows의 Visual Studio나 원하는 플랫폼의 Visual Studio Code와 통합할 수도 있습니다. 자세한 내용은 [vcpkg 통합](integrate-vcpkg.md)을 참조하세요.

## <a name="update-vcpkg"></a>vcpkg 업데이트

vcpkg 패키지 관리자는 GitHub에서 정기적으로 업데이트됩니다. vcpkg의 클론을 최신 버전으로 업데이트하려면 vcpkg 루트 디렉터리에서 **`git pull`** 을 실행합니다. 이 명령은 vcpkg의 복사본을 GitHub의 버전과 동기화합니다. 다운로드가 완료되면 부트스트래퍼를 다시 실행합니다. 부트스트래퍼가 vcpkg 프로그램을 다시 빌드하지만 설치된 라이브러리는 그대로 둡니다.

## <a name="uninstall-vcpkg"></a>vcpkg 제거

vcpkg를 제거하려면 *`vcpkg`* 디렉터리를 삭제하면 됩니다. 이 디렉터리를 삭제하면 vcpkg 배포 및 vcpkg에 의해 설치된 모든 라이브러리가 제거됩니다.

그러나 **`vcpkg integrate install`** 을 실행한 경우 폴더가 제거되기 전에 **`vcpkg integrate remove`** 를 실행하여 통합이 정리되었는지 확인해야 합니다. 자세한 내용은 [vcpkg 통합](integrate-vcpkg.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

[vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자](./vcpkg.md)\
[GitHub의 vcpkg](https://github.com/Microsoft/vcpkg)\
[vcpkg 통합](integrate-vcpkg.md)\
[vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)\
[vcpkg 명령줄 참조](vcpkg-command-line-reference.md)\
[빠른 시작](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[자주 묻는 질문](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
