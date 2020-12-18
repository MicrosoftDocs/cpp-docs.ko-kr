---
description: '자세한 정보: 지원되는 플랫폼(Visual C++)'
title: 지원되는 플랫폼(Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 80f8693a8cef7368953779d82100ce02e41f5cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207516"
---
# <a name="supported-platforms-visual-c"></a>지원되는 플랫폼(Visual C++)

Visual Studio를 사용하여 빌드한 응용 프로그램은 다음과 같이 다양한 플랫폼을 대상으로 할 수 있습니다.

|운영 체제|x86|X64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|X|X|||
|Windows Server 2008|X|X|||
|Windows 7|X|X|||
|Windows Server 2012 R2|X|X|||
|Windows 8|X|X|X||
|Windows 8.1|X|X|X||
|Windows 10|X|X|X|X|
|Android \*\*|X|X|X|X|
|iOS \*\*|X|X|X|X|
|Linux \*\*\*|X|X|X|X|

\* Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 및 Visual Studio 2012 업데이트 1 버전에 포함된 Windows XP 플랫폼 도구 집합을 사용하여 Windows XP 및 Windows Server 2003 프로젝트를 빌드할 수 있습니다. 이 플랫폼 도구 집합을 다운로드하고 사용하는 방법에 대한 자세한 내용은 [Windows XP용 프로그램 구성](../build/configuring-programs-for-windows-xp.md)을 참조하세요. 플랫폼 도구 집합을 변경하는 방법에 대한 자세한 내용은 [방법: 대상 프레임워크 및 플랫폼 도구 집합 수정](../build/how-to-modify-the-target-framework-and-platform-toolset.md)을 참조하세요.

\*\* Visual Studio 2017 이상 설치 관리자에서 **C++를 사용한 모바일 개발** 워크로드를 설치할 수 있습니다. Visual Studio 2015 설치에서 선택 사항인 **플랫폼 간 모바일 개발용 Visual C++** 구성 요소를 선택하여 iOS 또는 Android 플랫폼을 대상으로 지정할 수 있습니다. 자세한 내용은 [플랫폼 간 모바일 개발용 Visual C++ 설치](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)를 참조하세요. IOS 코드를 작성하려면 Mac 컴퓨터가 있어야 하며 다른 요구 사항을 충족해야 합니다. 필수 구성 요소 목록 및 설치 지침을 보려면 [iOS를 사용하여 빌드할 수 있도록 도구 설치 및 구성](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios)을 참조하세요. 대상 하드웨어와 일치하는 x86 또는 ARM 코드를 빌드할 수 있습니다. iOS 시뮬레이터, Android용 Microsoft Visual Studio 에뮬레이터, 일부 Android 디바이스용으로 빌드하려면 x86 구성을 사용합니다. iOS 디바이스 및 대부분의 Android 디바이스용으로 빌드하려면 ARM 구성을 사용합니다.

\*\*\* Visual Studio 2017 이상용 설치 관리자에 **C++를 사용한 Linux 개발** 워크로드를 설치하여 Linux 플랫폼을 대상으로 지정할 수 있습니다. 자세한 내용은 [Linux 작업 다운로드, 설치, 설정](../linux/download-install-and-setup-the-linux-development-workload.md)을 참조하세요. 이 도구 집합은 대상 컴퓨터에서 실행 파일을 컴파일하므로 지원되는 모든 아키텍처에 대해 빌드할 수 있습니다.

\*\*\*\* ARM64 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

대상 플랫폼 구성을 설정하는 방법에 대한 자세한 내용은 [방법: 64비트, x64 플랫폼을 대상으로 한 Visual C++ 프로젝트 구성](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio 버전의 Visual C++ 도구 및 기능](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [시작](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
