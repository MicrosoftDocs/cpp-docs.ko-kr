---
description: '자세한 정보: 방법: 명령줄에서 64비트 x64 호스팅 MSVC 도구 집합 사용'
title: '방법: 명령줄에서 64비트 MSVC 도구 집합 사용'
ms.date: 07/24/2019
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: d5e712802f420d425f4a0291d88220c22d4aeb62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162731"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>방법: 명령줄에서 64비트 x64 호스팅 MSVC 도구 집합 사용

Visual Studio에는 32비트, 64비트 또는 ARM 기반 Windows 운영 체제에서 실행 가능한 플랫폼 특정 버전을 만드는 데 사용할 수 있는 C++ 컴파일러, 링커 및 기타 도구가 포함됩니다. 다른 선택적 Visual Studio 워크로드에서는 C++ 도구를 사용하여 iOS, Android, Linux 같은 다른 플랫폼을 대상으로 할 수 있습니다. 기본 빌드 아키텍처는 32비트 x86 호스팅 도구를 사용하여 32비트 x86 네이티브 Windows 코드를 빌드합니다. 그러나 64비트 컴퓨터인 경우가 있습니다. Visual Studio를 64비트 Windows 운영 체제에 설치하면 64비트 x64 호스팅 네이티브 및 교차 컴파일러에 대한 추가적인 개발자 명령 프롬프트 바로 가기를 사용할 수 있습니다. X86, x64 또는 ARM 프로세서에 대한 코드를 빌드할 때는 64비트 x64 호스팅 도구 집합을 사용하여 64비트에 사용 가능한 프로세서 및 메모리 공간을 활용할 수 있습니다.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>64비트 호스팅 개발자 명령 프롬프트 바로 가기

Windows 10에서 이 명령 프롬프트에 액세스하려면 **시작** 메뉴에서 **Visual Studio 2019** 등과 같은 Visual Studio 버전에 대한 폴더를 연 다음, x64 네이티브 또는 교차 도구 개발자 명령 프롬프트 중 하나를 선택합니다.

![x64 네이티브 도구 명령 프롬프트](media/x64-native-tools-command-prompt.png "시작 메뉴의 x64 네이티브 도구")

Windows 8에서 이러한 명령 프롬프트에 액세스하려면 **시작** 화면에서 **모든 앱** 을 엽니다. 설치된 Visual Studio 버전에 대한 제목에서 **Visual Studio** 폴더(이전 Visual Studio 버전의 경우 **Visual Studio Tools** 일 수 있음)를 엽니다. 이전 버전의 Windows에서는 **시작** 을 선택하고 **모든 프로그램** 을 확장한 다음, 해당 **Visual Studio** 버전에 대한 폴더(및 이전 버전의 Visual Studio에서는 **Visual Studio Tools**)를 선택합니다. 자세한 내용은 [개발자 명령 프롬프트 바로 가기](building-on-the-command-line.md#developer_command_prompt_shortcuts)를 참조하세요.

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Vcvarsall.bat를 사용하여 64비트 호스팅 빌드 아키텍처 설정

네이티브 또는 교차 컴파일러 도구 빌드 구성은 명령줄에서 vcvarsall.bat를 실행하여 사용할 수 있습니다. 이 명령 파일은 기존 명령 프롬프트 창에서 특정 빌드 아키텍처를 사용할 수 있게 하는 경로 및 환경 변수를 구성합니다. 특정 지침은 [개발자 명령 파일 위치](building-on-the-command-line.md#developer_command_file_locations)를 참조하세요.

## <a name="remarks"></a>설명

> [!NOTE]
> 각 Visual Studio 버전에 포함된 특정 도구에 대한 자세한 정보는 [Visual Studio 버전의 Visual C++도구 및 기능](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md)을 참조하세요.
>
> Visual Studio IDE를 사용하여 64비트 애플리케이션을 만드는 방법에 대한 자세한 내용은 [방법: 64비트, x64 플랫폼을 대상으로 한 Visual C++ 프로젝트 구성](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)을 참조하세요.

Visual Studio 설치 관리자에서 C++ 워크로드를 설치할 때는 항상 x86 및 x64 코드 빌드를 위해 32비트 x86 호스팅 네이티브 및 교차 컴파일러 도구를 설치합니다. 유니버설 Windows 플랫폼 워크로드를 포함할 경우 ARM 코드 빌드를 위해 x86 호스팅 교차 컴파일러 도구도 설치합니다. 64비트 x64 프로세서에 이러한 워크로드를 설치할 경우, x86, x64 및 ARM 코드 빌드를 위한64비트 네이티브 및 교차 컴파일러 도구도 포함됩니다. 32비트 및 64비트 도구는 동일한 코드를 생성하지만 64비트 도구는 미리 컴파일된 헤더 기호 및 전체 프로그램 최적화([/GL](reference/gl-whole-program-optimization.md) 및 [/LTCG](reference/ltcg-link-time-code-generation.md)) 옵션을 위해 더 많은 메모리를 지원합니다. 32비트 도구를 사용할 때 메모리 제한이 발생하는 경우 64비트 도구를 사용해 보십시오.

## <a name="see-also"></a>참조

[64비트, x64 대상에 대한 C++ 프로젝트 구성](configuring-programs-for-64-bit-visual-cpp.md)<br/>
