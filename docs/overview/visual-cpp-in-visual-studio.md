---
title: Visual Studio의 C++
description: Visual Studio에서 Microsoft C/C++ 컴파일러, 코드 편집기, 관련 도구를 사용하여 Windows, Linux, Android, iOS용 프로그램을 개발하는 방법을 알아봅니다.
ms.date: 11/05/2020
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
ms.openlocfilehash: 32d8f45c1ae0ffeabcfd7b22988f125b138c1f4d
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334158"
---
# <a name="c-in-visual-studio"></a>Visual Studio의 C++

:::moniker range="msvc-160"

> [!NOTE]
> 이 개발자 설명서는 Visual Studio 2019에 적용됩니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.
>
> 프로그램을 실행할 수 있도록 Microsott Visual C++ 2019 재배포 가능 패키지를 찾고 있다면 Microsoft Visual Studio 사이트의 [다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하세요. **모든 다운로드** 에서 **기타 도구, 프레임워크 및 재배포 가능 패키지** 섹션을 펼칩니다. 대상 아키텍처를 선택한 다음 **다운로드** 단추를 선택합니다.
>
> 이전 재배포 가능 패키지의 경우 [이전 버전 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/) 페이지를 엽니다. **기타 도구, 프레임워크 및 재배포 가능 패키지** 섹션을 펼칩니다. 다운로드하려는 재배포 가능 버전을 찾고 대상 아키텍처를 선택한 다음 **다운로드** 단추를 선택합니다.

:::moniker-end

:::moniker range="msvc-150"

> [!NOTE]
> 이 개발자 설명서는 Visual Studio 2017에 적용됩니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.
>
> 프로그램을 실행할 수 있도록 Microsoft Visual C++ 2017 이전 재배포 가능 패키지를 찾고 있다면 Microsoft Visual Studio 사이트의 [이전 버전 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/) 페이지로 이동하세요. **기타 도구, 프레임워크 및 재배포 가능 패키지** 섹션을 펼칩니다. 다운로드하려는 재배포 가능 버전을 찾고 대상 아키텍처를 선택한 다음 **다운로드** 단추를 선택합니다.

:::moniker-end

:::moniker range="msvc-140"

> [!NOTE]
> 이 개발자 설명서는 Visual Studio 2015에 적용됩니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.
>
> 프로그램을 실행할 수 있도록 Microsott Visual C++ 2015 이전 재배포 가능 패키지를 찾고 있다면 Microsoft Visual Studio 사이트의 [이전 버전 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/) 페이지로 이동하세요. **기타 도구, 프레임워크 및 재배포 가능 패키지** 섹션을 펼칩니다. 다운로드하려는 재배포 가능 버전을 찾고 대상 아키텍처를 선택한 다음 **다운로드** 단추를 선택합니다.

:::moniker-end

Microsoft Visual C++(MSVC)는 Windows에서 Visual Studio의 일부로 사용할 수 있는 C++, C, 어셈블리 언어 개발 도구 및 라이브러리를 말합니다. 이러한 도구 및 라이브러리를 통해 UWP(유니버설 Windows 플랫폼) 앱, 네이티브 Windows 데스크톱 및 서버 애플리케이션, Windows, Linux, Android 및 iOS에서 실행되는 플랫폼 간 라이브러리 및 앱뿐만 아니라 .NET Framework를 사용하는 관리 앱 및 라이브러리를 만들 수 있습니다. MSVC를 사용하면 간단한 콘솔 앱 항목부터 가장 정교하고 복잡한 Windows 데스크톱용 앱까지, 디바이스 드라이버 및 운영 체제 구성 요소부터 모바일 디바이스용 플랫폼 간 게임까지, 가장 작은 IoT 디바이스부터 Azure 클라우드의 다중 서버 고성능 컴퓨팅 기능까지 작성할 수 있습니다.

Visual Studio 2015, 2017 및 2019를 Side-by-Side 설치할 수 있습니다. Visual Studio 2019(컴파일러 도구 세트 v142) 또는 Visual Studio 2017(v141)을 사용하면 Visual Studio 2017(v141) 및 Visual Studio 2015(v140)의 도구 세트를 통해 프로그램을 편집 및 빌드할 수 있습니다.

## <a name="whats-new-and-conformance-history"></a>새로운 기능 및 규칙 기록

[Visual Studio의 새로운 C++ 기능](what-s-new-for-visual-cpp-in-visual-studio.md)\
Visual Studio의 새로운 기능을 알아봅니다.

[Visual Studio 2003~2015의 새로운 C++ 기능](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
2003 - 2015에서 Visual Studio의 각 버전용 C++의 새로운 기능에 대해 알아봅니다.

[Visual Studio의 C++ 규칙 향상](cpp-conformance-improvements.md)\
Visual Studio의 C++ 규칙 향상에 대해 알아봅니다.

[Microsoft C++ 언어 규칙 테이블](visual-cpp-language-conformance.md)\
MSVC C++ 컴파일러의 기능별 규칙 상태 목록입니다.

[Microsoft C/C++ 변경 기록 2003~2015](../porting/visual-cpp-change-history-2003-2015.md)\
이전 버전의 주요 변경 내용에 대해 알아봅니다.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Visual Studio 설치 및 이전 버전에서 업그레이드

[Visual Studio에 C++ 지원 설치](../build/vscpp-step-0-installation.md)\
Visual Studio를 다운로드하고 Microsoft C/C++ 도구 집합을 설치합니다.

[Microsoft C++ 이식 및 업그레이드 가이드](../porting/visual-cpp-porting-and-upgrading-guide.md)\
Visual Studio 2015 이상으로 코드를 포팅하고 프로젝트를 업그레이드하여 C++ 표준에 대한 컴파일러 규칙을 활용하고 컴파일 시간 및 Spectre 완화와 같은 보안 기능을 크게 개선하기 위한 지침.

[Visual Studio 버전의 C++ 도구 및 기능](visual-cpp-tools-and-features-in-visual-studio-editions.md)\
여러 버전의 Visual Studio에 대해 알아봅니다.

[지원되는 플랫폼](supported-platforms-visual-cpp.md)\
Microsoft C/C++ 컴파일러에서 지원하는 플랫폼을 알아보세요.

## <a name="learn-c"></a>C++ 알아보기

[C++ 시작하기](../cpp/welcome-back-to-cpp-modern-cpp.md)\
코드를 빠르고 안전하게 작성하고 C 스타일 프로그래밍에서 흔히 저지르는 많은 실수를 피할 수 있도록 C++11 이상을 기반으로 하는 최신 C++ 프로그래밍 기술에 대해 자세히 알아봅니다.

[표준 C++](https://isocpp.org/)\
C++에 대해 알아보기, 최신 C++ 개요 살펴보기, 서적, 문서, 토론 및 이벤트 링크 찾기

[Visual Studio를 학습하고 첫 번째 C++ 프로젝트 만들기](../build/vscpp-step-1-create.md)\
Visual Studio에서 C++를 작성하는 방법에 대한 학습을 시작합니다.

[Visual Studio C++ 샘플](visual-cpp-samples.md)\
Microsoft에서 제공하는 C++ 코드 샘플에 대한 정보입니다.

## <a name="c-development-tools"></a>C++ 개발 도구

[Visual Studio의 C++ 개발 개요](overview-of-cpp-development.md)\
Visual Studio IDE를 사용하여 프로젝트 만들기, 코드 편집, 라이브러리에 연결, 컴파일, 디버그, 단위 테스트 만들기, 정적 분석 수행, 배포 등의 작업을 수행하는 방법입니다.

[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)\
MSVC 컴파일러 및 링커 옵션을 사용하여 Visual Studio C++ 프로젝트, CMake 프로젝트 및 기타 프로젝트를 만들고 구성하는 방법입니다.

[C++ 코드 작성 및 리팩터링](../ide/writing-and-refactoring-code-cpp.md)\
C++ 편집기의 생산성 기능을 사용하여 코드를 리팩터링, 탐색, 이해 및 작성하는 방법입니다.

[네이티브 코드 디버그](/visualstudio/debugger/debugging-native-code)\
C++ 프로젝트에서 Visual Studio 디버거를 사용합니다.

[C/C++용 코드 분석 개요](../code-quality/code-analysis-for-c-cpp-overview.md)\
SAL 주석 또는 C++ Core Guidelines 검사 프로그램을 사용하여 정적 분석을 수행합니다.

[Visual Studio에서 C/C++에 대한 단위 테스트 작성](/visualstudio/test/writing-unit-tests-for-c-cpp)\
C++, Google Test, Boost.Test 또는 CTest에 대한 Microsoft 유닛 테스트 프레임워크를 사용하여 단위 테스트를 만듭니다.

## <a name="write-applications-in-c"></a>C++에서 애플리케이션 작성

[유니버설 Windows 앱(C++)](../cppcx/universal-windows-apps-cpp.md)\
Windows 개발자 센터의 가이드 및 참조 내용을 알아봅니다. UWP 앱 개발에 대한 자세한 내용은 [유니버설 Windows 플랫폼 소개](/windows/uwp/get-started/universal-application-platform-guide) 및 [C++을 사용하여 첫 번째 UWP 앱 만들기](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)를 참조하세요.

[데스크톱 애플리케이션(C++)](../windows/desktop-applications-visual-cpp.md)\
Windows용 기존 네이티브 C++ 데스크톱 애플리케이션을 만드는 방법을 알아봅니다.

[C++/CLI를 사용한 .NET 프로그래밍](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
C# 또는 Visual Basic과 같은 언어로 작성된 네이티브 C++ 및 .NET 프로그램 간의 상호 운용성을 활성화하는 DLL을 만드는 방법을 알아봅니다.

[Linux 프로그래밍](../linux/index.yml)\
Visual Studio IDE를 사용하여 GCC로 컴파일을 위해 원격 Linux 머신으로 코딩 및 배포합니다.

[Visual Studio에서 C/C++ DLL 만들기](../build/dlls-in-visual-cpp.md)\
Win32, ATL 및 MFC를 사용하여 Windows 데스크톱 DLL을 만드는 방법을 설명하고 DLL을 컴파일 및 등록하는 방법에 대해 알아봅니다.

[병렬 프로그래밍](../parallel/parallel-programming-in-visual-cpp.md)\
병렬 패턴 라이브러리, C++ AMP, OpenMP 및 Windows에서의 다중 스레딩과 관련된 기타 기능을 사용하는 방법에 대해 알아봅니다.

[보안 모범 사례](../security/security-best-practices-for-cpp.md)\
악의적 코드나 무단 사용으로부터 애플리케이션을 보호하는 방법에 대해 알아봅니다.

[클라우드 및 웹 프로그래밍](../cloud/cloud-and-web-programming-in-visual-cpp.md)\
C++에는 웹 및 클라우드에 연결하기 위한 다양한 옵션이 있습니다.

[데이터 액세스](../data/data-access-in-cpp.md)\
ODBC 및 OLE DB를 사용하여 데이터베이스에 연결합니다.

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)\
현지 및 국제적 개발을 위한 다양한 텍스트 및 문자열 형식과 인코딩을 사용하는 방법을 알아봅니다.

## <a name="languages-reference"></a>언어 참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)\
C++ 프로그래밍 언어의 Microsoft 구현에 대한 참조 가이드입니다.

[C/C++ 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)\
공유 C 및 C++ 언어 전처리기에 대한 일반적인 참조입니다.

[C 언어 참조](../c-language/c-language-reference.md)\
C 프로그래밍 언어의 Microsoft 구현에 대한 참조 가이드입니다.

[컴파일러 내장 함수 및 어셈블리 언어](../intrinsics/compiler-intrinsics-and-assembly-language.md)\
각 플랫폼에서 Microsoft C/C++ 컴파일러가 지원하거나 구현하는 컴파일러 내장 함수를 안내합니다.

## <a name="c-libraries-in-visual-studio"></a>Visual Studio의 C++ 라이브러리

다음 섹션에서는 Visual Studio에서 제공되는 다양한 C 및 C++ 라이브러리에 대한 정보를 제공합니다.

[C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)\
보안 문제가 있는 것으로 알려진 함수에 대해 보안을 강화한 대안을 포함합니다.

[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)\
C++ 표준 라이브러리입니다.

[ATL(액티브 템플릿 라이브러리)](../atl/atl-com-desktop-components.md)\
COM 구성 요소 및 응용 프로그램을 지원합니다.

[MFC(Microsoft Foundation Class) 라이브러리](../mfc/mfc-desktop-applications.md)\
기존 또는 Office 스타일 사용자 인터페이스가 포함된 데스크톱 응용 프로그램 만들기를 지원합니다.

[PPL(병렬 패턴 라이브러리)](../parallel/concrt/parallel-patterns-library-ppl.md)\
CPU에서 실행되는 비동기 및 병렬 알고리즘입니다.

[C++ AMP(C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)\
GPU에서 실행되는 대규모 병렬 알고리즘입니다.

[WRL(Windows 런타임 템플릿 라이브러리)](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)\
UWP(유니버설 Windows 플랫폼) 앱 및 구성 요소

[C++/CLI를 사용한 .NET 프로그래밍](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
CLR(공용 언어 런타임)에 대한 프로그래밍입니다.

## <a name="third-party-open-source-c-libraries"></a>타사 오픈 소스 C++ 라이브러리

플랫폼 간 **vcpkg** 명령줄 도구는 900개가 넘는 C++ 오픈 소스 라이브러리를 검색 및 설치하는 작업을 상당히 간소화합니다. [vcpkg: Windows용 C++ 패키지 관리자](../build/vcpkg.md)를 참조하세요.

## <a name="feedback-and-community"></a>사용자 의견 및 커뮤니티

[Microsoft Docs Q&A](/answers/topics/c%2B%2B.html)\
Microsoft Docs는 검색 가능한 질문과 대답 포럼을 호스트합니다. C++ 관련 문제에 대한 커뮤니티 지원을 위한 게시물에는 `C++` 태그를 추가하세요.

[Microsoft C/C++ 도구 집합의 문제를 보고하는 방법](how-to-report-a-problem-with-the-visual-cpp-toolset.md)\
Microsoft Visual C/C++ 도구 집합(컴파일러, 링커 및 기타 도구)에 대한 효과적인 오류 보고서를 만드는 방법과 보고서를 전송하는 방법을 알아봅니다.

Microsoft [C++ 팀 블로그](https://devblogs.microsoft.com/cppblog/)\
새로운 기능과 Visual Studio의 C++ 도구 개발자가 제공하는 최신 정보를 자세히 알아봅니다.

[Visual Studio C++ Developer Community](https://aka.ms/vsfeedback/browsecpp)\
Visual Studio의 C++에 대한 도움말을 확인하고, 버그를 제출하고, 제안을 합니다.
