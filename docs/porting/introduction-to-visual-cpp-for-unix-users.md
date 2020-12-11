---
description: '자세한 정보: UNIX 사용자 용 Microsoft c + + 소개'
title: UNIX 사용자를 위한 Microsoft C++ 소개
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 1047ba4e07803bfd6863a0b7da5d0e8473938586
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159832"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>UNIX 사용자를 위한 Microsoft C++ 소개

이 항목에서는 Visual Studio를 처음 사용 하는 모든 유형의 UNIX 사용자를 위한 정보를 제공 하며, 명령줄 또는 Visual Studio를 사용 하 여 c + +를 사용 하 여 생산성을 유지 하려고 합니다. Windows를 대상으로 하는 Microsoft c + + 컴파일러와 함께 Visual Studio를 사용할 수 있습니다. Visual Studio IDE를 UNIX 환경 (예: 원격 Linux 컴퓨터, MinGW-전환 하거나 mingw-w64 및 Linux 용 Windows 하위 시스템)에서 사용할 수도 있습니다. Visual Studio에서 c + +를 사용 하려면 **c + +를 사용한 데스크톱 개발** 워크 로드를 설치 해야 합니다. Visual Studio 설치 관리자를 열어 작업을 설치 하거나 선택적 구성 요소를 추가 또는 제거 합니다. 또한 원격 Linux 컴퓨터를 대상으로 하는 경우 **c + + 워크 로드를 사용 하 여 Linux 개발** 을 설치 합니다. Android 또는 iOS 개발의 경우 **c + +를 사용한 모바일 개발** 워크 로드를 설치 합니다.

## <a name="getting-started-on-the-command-line"></a>명령줄에서 시작

UNIX 명령줄 환경을 사용 하는 것과 유사한 방식으로 명령줄에서 Microsoft c + + 컴파일러를 사용할 수 있습니다. 명령줄 C 및 C++ 컴파일러(CL.EXE), 링커(LINK.EXE) 및 UNIX에서 만든 유틸리티의 Microsoft 버전인 NMAKE.EXE를 비롯한 기타 도구를 사용하여 명령 프롬프트에서 컴파일합니다.

UNIX에서는 /usr/bin 등의 공용 폴더에 명령이 설치됩니다. Visual Studio에서 명령줄 도구는 Visual Studio 설치 디렉터리의 VC\bin 하위 디렉터리 및 그 하위 디렉터리에 설치됩니다. UNIX와 달리 이러한 도구는 일반 명령 프롬프트 창에서 사용할 수 없습니다. 명령줄 도구를 사용 하려면 c + + 프로그램을 컴파일하는 데 필요한 경로 및 기타 환경 변수를 설정 하는 특수 개발자 명령 프롬프트를 사용 해야 합니다. 자세한 내용은 [명령줄에서 C/C++ 코드 빌드](../build/building-on-the-command-line.md) 및 [연습: 명령줄에서 네이티브 C++ 프로그램 컴파일](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)을 참조하세요.

## <a name="debugging-your-code"></a>코드 디버그

Microsoft c + + 프로젝트에 대 한 Visual Studio 디버거는 명령줄에서 또는 IDE 내에서 사용할 수 있습니다. [/Z7,/zi,/zi (디버그 정보 형식)](../build/reference/z7-zi-zi-debug-information-format.md) 스위치로 컴파일하여 소스를 단계별로 실행할 수 있습니다. 자세한 내용은 [네이티브 코드 디버그](/visualstudio/debugger/debugging-native-code) 및 [C++ 데스크톱 개발에 Visual Studio IDE 사용](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)을 참조하세요.

GCC 또는 Clang로 컴파일된 프로그램의 경우 Visual Studio는 GDB, LLDB 또는 지정 하는 사용자 지정 디버거를 호출 합니다.

## <a name="visual-studio-project-system"></a>Visual Studio 프로젝트 시스템

Visual Studio 프로젝트 시스템을 MSBuild 라고 합니다. XML 형식의 프로젝트 파일을 사용 합니다. C + + 프로젝트 파일의 확장명은 .vcxproj입니다. 잠재적으로 각각 다른 컴파일러 옵션 집합이나 다른 언어로 빌드된 여러 라이브러리와 실행 파일로 구성된 애플리케이션은 단일 *솔루션* 에 속하는 여러 프로젝트에 저장됩니다. 솔루션은 여러 프로젝트를 함께 그룹화하는 컨테이너에 대한 추상화입니다. 솔루션 정보는 확장명이 .sln 솔루션 파일에 저장됩니다. 자세한 내용은 [Visual Studio의 솔루션 및 프로젝트](/visualstudio/ide/solutions-and-projects-in-visual-studio) 및 [C++ 데스크톱 개발에 Visual Studio IDE 사용](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)을 참조하세요. 주 메뉴에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 사용할 수 있는 Visual Studio 프로젝트 템플릿을 표시 합니다.

Visual Studio 2017부터 CMake 프로젝트에 대 한 지원 뿐 아니라 임의의 빌드 시스템에서 Microsoft c + + 컴파일러를 사용 하는 옵션 뿐만 아니라 소스 파일의 느슨한 폴더와 프로젝트 파일은 포함 되지 않습니다. 자세한 내용은 [Visual studio의 ctoprojects](../build/cmake-projects-in-visual-studio.md) 및 [Visual Studio에서 폴더 열기](../build/open-folder-projects-cpp.md)를 참조 하세요.

## <a name="microsoft-specific-modifiers"></a>Microsoft 전용 한정자

Microsoft C++ 컴파일러는 Windows 운영 체제에 대한 프로그래밍을 지원하기 위해 표준 C++ 프로그래밍 언어에 대한 몇 가지 확장을 구현합니다. 이러한 확장은 특히 스토리지 클래스 특성, 함수 호출 규칙 및 기본 주소를 지정하는 데 사용됩니다. 지원되는 C++ 확장의 전체 목록은 [Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)를 참조하세요.

`/Za` 컴파일러 옵션을 통해 C++에 대한 모든 Microsoft 전용 확장을 사용하지 않도록 설정할 수 있습니다. 이 옵션은 여러 플랫폼에서 실행할 코드를 작성하려는 경우에 권장됩니다. `/Za` 컴파일러 옵션에 대한 자세한 내용은 [/Za, /Ze(언어 확장명 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md)를 참조하세요. C + + 컴파일러 규칙에 대 한 자세한 내용은 [Microsoft c + + 언어 규칙 테이블](../overview/visual-cpp-language-conformance.md) 및 [비표준 동작](../cpp/nonstandard-behavior.md)을 참조 하세요.

## <a name="precompiled-headers"></a>미리 컴파일된 헤더

Microsoft C 및 C++ 컴파일러는 인라인 코드를 포함하여 모든 C 또는 C++ 코드를 미리 컴파일하는 옵션을 제공합니다. 이 성능 기능을 사용하여 안정적인 코드 본문을 컴파일하고, 코드의 컴파일된 상태를 파일에 저장하고, 후속 컴파일 중 미리 컴파일된 코드와 아직 개발 중인 코드를 결합할 수 있습니다. 안정적인 코드는 다시 컴파일할 필요가 없기 때문에 각 후속 컴파일 속도가 향상됩니다.

기본적으로 미리 컴파일된 코드는 *pch.h* 및 *pch.cpp*(Visual Studio 2017 및 이전 버전에서 *stdafx.h* 및 *stdafx.cpp*) 파일에서 모두 지정됩니다. 미리 컴파일된 헤더에 대한 자세한 내용은 [미리 컴파일된 헤더 파일 만들기](../build/creating-precompiled-header-files.md)를 참조하세요.

## <a name="related-sections"></a>관련 단원

자세한 내용은 [Windows에서 Linux 프로그램 실행](../porting/porting-from-unix-to-win32.md)을 참조 하세요.

## <a name="see-also"></a>참조

[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)
