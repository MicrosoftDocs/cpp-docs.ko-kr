---
title: vcpkg를 Visual Studio 또는 Visual Studio Code와 통합
description: vcpkg를 Windows의 Visual Studio나 macOS 및 Linux의 Visual Studio Code와 통합하는 방법을 알아봅니다.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: b6f092313dde14b10a05d4cff0904adf5174b264
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684120"
---
# <a name="integrate-vcpkg-with-visual-studio-or-visual-studio-code"></a>vcpkg를 Visual Studio 또는 Visual Studio Code와 통합

vcpkg는 C 및 C++ 라이브러리용 플랫폼 간 명령줄 패키지 관리자입니다. vcpkg를 Windows의 Visual Studio나 Linux 및 macOS의 Visual Studio Code와 통합할 수 있습니다.

## <a name="integrate-with-visual-studio-on-windows"></a>Windows의 Visual Studio와 통합

### <a name="integrate-per-user"></a>사용자 단위 통합

vcpkg 루트 디렉터리에서 **`vcpkg integrate install`** 을 실행하여 사용자 단위로 모든 vcpkg 헤더 파일과 이진 파일을 찾도록 Visual Studio를 구성합니다. Visual Studio에서 VC++ 디렉터리 경로를 편집할 필요가 없습니다. vcpkg의 클론이 여러 개 있는 경우 이 명령을 실행하는 클론이 새 기본 위치가 됩니다.

이제 폴더 또는 헤더 이름을 입력하여 헤더를 포함할 수 있으며 자동 완성이 도움이 됩니다. 라이브러리에 연결하거나 프로젝트 참조를 추가하는 추가 단계가 필요하지 않습니다. 다음 일러스트레이션에서는 Visual Studio가 *`azure-storage-cpp`* 헤더를 찾는 방법을 보여 줍니다. vcpkg는 대상 플랫폼으로 분할된 *`/installed`* 하위 폴더에 헤더를 배치합니다. 다음 다이어그램에서는 라이브러리의 *`/was`* 하위 폴더에 있는 포함 파일의 목록을 보여 줍니다.

![Visual Studio 편집기의 IntelliSense 자동 완성 팝업 창](media/vcpkg-intellisense.png "vcpkg 및 IntelliSense")

### <a name="integrate-per-project"></a>프로젝트 단위 통합

활성 vcpkg 인스턴스에서 버전과 다른 라이브러리의 특정 버전을 사용해야 하는 경우 다음 단계를 따르세요.

1. vcpkg의 새 클론을 생성합니다. 자세한 내용은 [vcpkg 설치](install-vcpkg.md)를 참조하세요.

1. 새 vcpkg 루트 디렉터리로 변경합니다.

1. 필요한 버전을 가져오도록 라이브러리의 포트 파일을 수정합니다.

1. **`vcpkg install <library>`** 를 실행합니다. 자세한 내용은 [vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)를 참조하세요.

1. **`vcpkg integrate project`** 를 사용하여 프로젝트 단위로 해당 라이브러리를 참조하는 NuGet 패키지를 만듭니다.

## <a name="integrate-with-visual-studio-code-on-linux-or-macos"></a>Linux 또는 macOS의 Visual Studio Code와 통합

셸 또는 터미널 창에서 디렉터리를 vcpkg 루트 디렉터리로 변경합니다. 그런 다음, **`./vcpkg integrate install`** 을 실행하여 Linux 또는 macOS의 Visual Studio Code를 구성합니다. 이 명령은 vcpkg 도구 및 라이브러리의 위치를 설정하고 소스 파일에서 IntelliSense를 사용하도록 설정합니다.

## <a name="remove-vcpkg-integration"></a>vcpkg 통합 제거

**`integrate`** 옵션을 사용한 경우 vcpkg 인스턴스를 제거하기 전에 통합을 제거해야 합니다. 통합을 제거하고 정리하려면 디렉터리를 vcpkg 루트 디렉터리로 변경합니다. 통합이 정리되도록 하려면 Windows에서는 **`vcpkg integrate remove`** 를 실행하고, Linux 또는 macOS에서는 **`./vcpkg integrate remove`** 명령을 실행합니다.

## <a name="see-also"></a>추가 정보

[vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자](./vcpkg.md)\
[GitHub의 vcpkg](https://github.com/Microsoft/vcpkg)\
[vcpkg 설치](install-vcpkg.md)\
[vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)\
[vcpkg 명령줄 참조](vcpkg-command-line-reference.md)\
[빠른 시작](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[자주 묻는 질문](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
