---
title: Visual Studio의 C/C++ 프로젝트 및 빌드 시스템
description: Visual Studio를 사용하여 모든 프로젝트 시스템을 기반으로 Windows, ARM 또는 Linux용 C++ 프로젝트를 컴파일하고 빌드합니다.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 193230ef393aa83d7ce4b9aec11a1fa2cb5052ce
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176072"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Visual Studio의 C/C++ 프로젝트 및 빌드 시스템

코드를 Visual Studio 프로젝트로 변환하거나 MSVC 도구 집합을 사용하여 컴파일할 필요 없이 Visual Studio를 사용하여 전체 IntelliSense 지원으로 어떤 C++ 코드 베이스라도 편집, 컴파일 및 빌드할 수 있습니다. 예를 들어 Windows 컴퓨터에서 Visual Studio의 플랫폼 간 CMake 프로젝트를 편집한 다음, 원격 Linux 컴퓨터에서 g++를 사용하여 Linux용으로 컴파일할 수 있습니다.

## <a name="c-compilation"></a>C++ 컴파일

C++ 프로그램을 *빌드* 한다는 것은 하나 이상의 파일에서 소스 코드를 컴파일한 다음, 파일을 실행 파일(.exe), 동적 로드 라이브러리(.dll) 또는 정적 라이브러리(.lib)에 연결함을 뜻합니다.

기본 C++ 컴파일에는 다음과 같은 세 가지 주요 단계가 포함됩니다.

- C++ 전처리기는 각 소스 파일의 모든 #지시문 및 매크로 정의를 변환합니다. 이로써 *변환 단위* 가 만들어집니다.
- C++ 컴파일러는 설정된 모든 컴파일러 옵션을 적용하여 각 변환 단위를 개체 파일(.obj)로 컴파일합니다.
- *링커* 는 설정된 링커 옵션을 적용하여 개체 파일을 단일 실행 파일로 병합합니다.

## <a name="the-msvc-toolset"></a>MSVC 도구 집합

Microsoft C++ 컴파일러, 링커, 표준 라이브러리 및 관련 유틸리티는 MSVC 컴파일러 도구 집합(도구 체인 또는 “빌드 도구”라고도 함)을 구성합니다. 이것들은 Visual Studio에 포함되어 있습니다. 또한 [Visual Studio 2019용 빌드 도구 다운로드](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)에서 도구 집합을 무료로 다운로드하여 독립 실행형 패키지로 사용할 수 있습니다.

명령줄에서 직접 MSVC 컴파일러(cl.exe)를 호출하여 간단한 프로그램을 빌드할 수 있습니다. 다음 명령은 단일 소스 코드 파일을 수락하고 cl.exe를 호출하여 *hello.exe* 라는 실행 파일을 빌드합니다.

```cmd
cl /EHsc hello.cpp
```

여기서 컴파일러(cl.exe)는 C++ 전처리기 및 링커를 자동으로 호출하여 최종 출력 파일을 생성합니다. 자세한 내용은 [명령줄에서 빌드](building-on-the-command-line.md)를 참조하세요.

## <a name="build-systems-and-projects"></a>빌드 시스템 및 프로젝트

대부분의 실제 프로그램에서는 여러 구성(디버그 및 릴리스), 여러 플랫폼(x86, x64, ARM 등), 사용자 지정 빌드 단계, 그리고 특정 순서로 컴파일되어야 하는 여러 실행 파일에 대해 여러 소스 파일을 컴파일해야 하는 복잡성을 관리하기 위해 몇 가지 ‘빌드 시스템’을 사용합니다. 빌드 구성 파일에서 설정을 만들면 빌드 시스템은 이 파일을 입력으로 받아들인 후 컴파일러를 호출합니다. 실행 파일을 빌드하는 데 필요한 소스 코드 파일 및 빌드 구성 파일의 집합을 *프로젝트* 라고 합니다.

다음 목록은 Visual Studio 프로젝트의 다양한 옵션을 나열한 것입니다.

- C++: Visual Studio IDE를 사용하여 Visual Studio 프로젝트를 만들고 속성 페이지를 사용하여 Visual Studio 프로젝트를 구성합니다. Visual Studio 프로젝트는 Windows에서 실행되는 프로그램을 생성합니다. 개요는 Visual Studio 설명서에서 [컴파일 및 빌드](/visualstudio/ide/compiling-and-building-in-visual-studio)를 참조하세요.

- CMakeLists.txt 파일이 포함된 폴더를 엽니다. CMake 지원은 Visual Studio에 통합되어 있습니다. 어떤 방식으로도 CMake 파일을 수정하지 않고 IDE를 사용하여 편집, 테스트, 디버그할 수 있습니다. 이렇게 하면 다른 편집기를 사용하는 다른 사용자와 동일한 CMake 프로젝트에서 작업할 수 있습니다. 플랫폼 간 개발에는 CMake를 사용하는 것이 좋습니다. 자세한 내용은 [CMake 프로젝트](cmake-projects-in-visual-studio.md)를 참조하세요.

- 프로젝트 파일이 없는 소스 파일의 느슨한 폴더를 엽니다. Visual Studio에서는 추론을 사용하여 파일을 빌드합니다. 이것은 작은 콘솔 애플리케이션을 손쉽게 컴파일하고 실행할 수 있는 방법입니다. 자세한 내용은 [폴더 열기 프로젝트](open-folder-projects-cpp.md)를 참조하세요.

- 메이크파일이나 기타 빌드 시스템 구성 파일을 포함하는 폴더를 엽니다. JSON 파일을 폴더에 추가하여 임의의 빌드 명령을 호출하도록 Visual Studio를 구성할 수 있습니다. 자세한 내용은 [폴더 열기 프로젝트](open-folder-projects-cpp.md)를 참조하세요.

- Visual Studio에서 Windows 메이크파일을 엽니다. 자세한 내용은 [NMAKE 참조](reference/nmake-reference.md)를 참조하세요.

## <a name="msbuild-from-the-command-line"></a>명령줄에서 MSBuild 사용

명령줄 옵션과 함께 .vcxproj 파일을 MSBuild에 전달하여 명령줄에서 MSBuild를 호출할 수 있습니다. 이 방법을 사용하려면 MSBuild를 잘 이해해야 하며 필요한 경우에만 사용하는 것이 좋습니다. 자세한 내용은 [MSBuild](msbuild-visual-cpp.md)를 참조하세요.

## <a name="in-this-section"></a>섹션 내용

[Visual Studio 프로젝트](creating-and-managing-visual-cpp-projects.md)\
기본 빌드 시스템(MSBuild)을 사용하여 Visual Studio에서 C++ 프로젝트를 만들고 구성하고 빌드하는 방법입니다.

[CMake 프로젝트](cmake-projects-in-visual-studio.md)\
Visual Studio에서 CMake 프로젝트를 코딩, 빌드, 배포하는 방법입니다.

[폴더 열기 프로젝트](open-folder-projects-cpp.md)\
임의의 빌드 시스템을 기반으로 하거나 빌드 시스템 없이 Visual Studio를 사용하여 C++ 프로젝트를 코딩, 빌드, 배포하는 방법입니다.

[릴리스 빌드](release-builds.md)\
최종 사용자에게 배포하기 위해 최적화된 릴리스 빌드를 만들고 문제를 해결하는 방법입니다.

[명령줄에서 MSVC 도구 집합 사용](building-on-the-command-line.md)\
Visual Studio IDE를 사용하는 대신, 명령줄에서 직접 C/C++ 컴파일러 및 빌드 도구를 사용하는 방법을 설명합니다.

[Visual Studio에서 DLL 빌드](dlls-in-visual-cpp.md)\
Visual Studio에서 C/C++ DLL(공유 라이브러리)을 만들고 디버그하고 배포하는 방법입니다.

[연습: 정적 라이브러리 만들기 및 사용](walkthrough-creating-and-using-a-static-library-cpp.md)\
**.lib** 이진 파일을 만드는 방법입니다.

[C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)\
격리된 애플리케이션 및 side-by-side 어셈블리 아이디어를 기반으로 하는 Windows 데스크톱 애플리케이션의 배포 모델에 대해 설명합니다.

[64비트, x64 대상에 대한 C++ 프로젝트 구성](configuring-programs-for-64-bit-visual-cpp.md)\
MSVC 빌드 도구를 사용하여 64비트 x64 하드웨어를 대상으로 하는 방법입니다.

[ARM 프로세서에 대한 C++ 프로젝트 구성](configuring-programs-for-arm-processors-visual-cpp.md)\
MSVC 빌드 도구를 사용하여 ARM 하드웨어를 대상으로 하는 방법입니다.

[코드 최적화](optimizing-your-code.md)\
프로그램의 안내에 따른 최적화를 포함해 다양한 방식으로 코드를 최적화하는 방법입니다.

[Windows XP용 프로그램 구성](configuring-programs-for-windows-xp.md)\
MSVC 빌드 도구로 Windows XP를 대상으로 하는 방법입니다.

[C/C++ 빌드 참조](reference/c-cpp-building-reference.md)\
C++, 컴파일러/링커 옵션 및 다양한 빌드 도구를 사용한 프로그램 빌드와 관련된 참조 문서의 링크를 제공합니다.
