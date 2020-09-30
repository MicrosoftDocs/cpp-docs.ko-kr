---
title: 데스크톱 애플리케이션(Visual C++)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: 26448ca65b3162e2adfe6988dfd8c9e85432429c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504434"
---
# <a name="desktop-applications-visual-c"></a>데스크톱 애플리케이션(Visual C++)

C + +의 *데스크톱 응용 프로그램* 은 Windows api의 전체 집합에 액세스 하 여 창 또는 시스템 콘솔에서 실행할 수 있는 네이티브 응용 프로그램입니다. C + +의 데스크톱 응용 프로그램은 windows 10을 통해 windows XP에서 실행할 수 있습니다. windows XP는 더 이상 공식적으로 지원 되지 않으며 그 이후에 도입 된 많은 Windows Api가 있습니다.

데스크톱 응용 프로그램은 Windows 10을 실행 하는 Pc에서 실행할 수 있는 UWP (유니버설 Windows 플랫폼) 앱과 다르며 XBox, Windows Phone, Surface Hub 및 기타 장치 에서도 실행할 수 있습니다. 데스크톱 및 UWP 응용 프로그램에 대 한 자세한 내용은 [기술 선택](/windows/win32/choose-your-technology)을 참조 하세요.

## <a name="desktop-bridge"></a>데스크톱 브리지

Windows 10에서는 기존 데스크톱 응용 프로그램 또는 COM 개체를 UWP 앱으로 패키지 하 고 터치와 같은 UWP 기능을 추가 하거나 최신 Windows API 집합에서 Api를 호출할 수 있습니다. 또한 Visual Studio에서 데스크톱 솔루션에 UWP 앱을 추가 하 고 단일 패키지로 함께 패키지 하 고 Windows Api를 사용 하 여 서로 통신할 수 있습니다.

Visual Studio 2017 버전 15.4 이상에서 Windows 응용 프로그램 패키지 프로젝트를 만들어 기존 데스크톱 응용 프로그램을 패키지 하는 작업을 크게 간소화할 수 있습니다. 데스크톱 응용 프로그램에서 사용 하는 레지스트리 호출 또는 Api와 관련 하 여 몇 가지 제한 사항이 적용 되지만, 대부분의 경우 응용 프로그램 패키지에서 실행 되는 동안 유사한 기능을 얻기 위해 대체 코드 경로를 만들 수 있습니다. 자세한 내용은 [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root)를 참조하세요.

## <a name="terminology"></a>용어

- *Win32* 응용 프로그램은 c + +의 windows 데스크톱 응용 프로그램으로, 네이티브 [windows C api 및/또는 COM Api](/windows/win32/apiindex/windows-api-list) CRT 및 표준 라이브러리 api와 타사 라이브러리를 사용할 수 있습니다. 창에서 실행 되는 Win32 응용 프로그램의 경우 개발자는 Windows 프로시저 함수 내에서 Windows 메시지를 사용 하 여 명시적으로 작업 해야 합니다. 이름에도 불구 하 고 Win32 응용 프로그램을 32 비트 (x86) 또는 64 비트 (x64) 이진으로 컴파일할 수 있습니다. Visual Studio IDE에서 x86 및 Win32 용어는 동의어입니다.

- [COM (구성 요소 개체 모델)](/windows/win32/com/the-component-object-model) 은 서로 다른 언어로 작성 된 프로그램이 서로 통신할 수 있도록 하는 사양입니다. 많은 Windows 구성 요소가 COM 개체로 구현 되며 개체 만들기, 인터페이스 검색 및 개체 소멸에 대 한 표준 COM 규칙을 따릅니다.  C + + 데스크톱 응용 프로그램에서 COM 개체를 사용 하는 것은 비교적 간단 하지만 고유한 COM 개체를 작성 하는 것이 더 고급입니다. [ATL (액티브 템플릿 라이브러리)](../atl/atl-com-desktop-components.md) 은 COM 개발을 간소화 하는 매크로 및 도우미 함수를 제공 합니다.

- MFC 응용 프로그램은 [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) 를 사용 하 여 사용자 인터페이스를 만드는 Windows 데스크톱 응용 프로그램입니다. MFC 응용 프로그램은 CRT 및 표준 라이브러리 Api를 비롯 하 여 COM 구성 요소를 사용할 수도 있습니다. MFC는 창 메시지 루프 및 Windows Api에 대 한 씬 c + + 개체 지향 래퍼를 제공 합니다. MFC는 다양 한 사용자 인터페이스 컨트롤이 나 사용자 지정 사용자 정의 컨트롤을 포함 하는 응용 프로그램 (특히 엔터프라이즈급 응용 프로그램)에 대 한 기본 선택입니다. MFC는 리본 같은 창 관리, serialization, 텍스트 조작, 인쇄 및 최신 사용자 인터페이스 요소에 대 한 편리한 도우미 클래스를 제공 합니다. MFC를 효과적으로 사용 하려면 Win32에 대해 잘 알고 있어야 합니다.

- C + +/CLI 응용 프로그램 또는 구성 요소는 c + + 구문에 대 한 확장을 사용 하 여 .NET 및 네이티브 C + + 코드 간의 상호 작용을 사용 하도록 설정 합니다.  C + +/CLI 응용 프로그램은 기본적으로 실행 되는 파트와 .NET Framework에서 실행 되는 파트를 .NET 기본 클래스 라이브러리에 액세스할 수 있습니다. C + +/CLI는 c # 또는 Visual Basic로 작성 된 코드를 사용 해야 하는 네이티브 c + + 코드를 사용 하는 경우 기본 설정 된 옵션입니다. 사용자 인터페이스 코드가 아닌 .NET Dll에서 사용 하기 위한 것입니다. 자세한 내용은 [C++/CLI를 사용한 .NET 프로그래밍(Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조하세요.

C + +의 모든 데스크톱 응용 프로그램은 C 런타임 (CRT) 및 표준 라이브러리 클래스 및 함수, COM 개체 및 공용 Windows 함수를 사용할 수 있습니다 .이를 Windows API 라고 통칭 합니다. C + +의 Windows 데스크톱 응용 프로그램에 대 한 소개는 [Win32 및 c + + 시작](/windows/win32/LearnWin32/learn-to-program-for-windows)을 참조 하세요.

## <a name="in-this-section"></a>단원 내용

|제목|설명|
|-----------|-----------------|
|[C++의 Windows 콘솔 애플리케이션](./overview-of-windows-programming-in-cpp.md)|콘솔 앱에 대한 정보가 들어 있습니다. Win32 또는 Win64 콘솔 애플리케이션에는 고유의 창이나 메시지 루프가 없습니다. 콘솔 창에서 실행되고 입력 및 출력이 명령줄을 통해 처리됩니다.|
|[연습: Windows 데스크톱 애플리케이션 만들기(C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|간단한 Windows 데스크톱 응용 프로그램을 만듭니다.|
|[빈 Windows 데스크톱 애플리케이션 만들기](./overview-of-windows-programming-in-cpp.md)|기본 파일이 없는 Windows 데스크톱 프로젝트를 만드는 방법|
|[빈 Win32 애플리케이션에 파일 추가](./overview-of-windows-programming-in-cpp.md)|빈 프로젝트에 파일을 추가 하는 방법|
|[리소스 파일 작업](working-with-resource-files.md)|데스크톱 응용 프로그램에 이미지, 아이콘, 문자열 테이블 및 기타 리소스를 추가 하는 방법입니다.|
|[DirectX를 사용하여 게임을 만들기 위한 리소스(C++)](resources-for-creating-a-game-using-directx.md)|C + +로 게임을 만들기 위한 콘텐츠에 대 한 링크입니다.|
|[연습: 정적 라이브러리 만들기 및 사용](../build/walkthrough-creating-and-using-a-static-library-cpp.md)|.Lib 이진 파일을 만드는 방법|
|[방법: Windows 데스크톱 응용 프로그램에서 Windows 10 SDK 사용](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows 10 SDK를 사용하여 빌드할 프로젝트를 설정하는 단계를 설명합니다.|

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[Windows 개발](/windows/win32/index)|Windows API 및 COM에 대한 정보를 제공합니다. 일부 Windows API 및 타사 DLL이 COM 개체로 구현됩니다.|
|[Hilo: Developing C++ Applications for Windows 7](/previous-versions/msdn10/ff708696(v=msdn.10))|Windows Animation 및 Direct2D를 사용하는 리치 클라이언트 Windows 데스크톱 애플리케이션을 만들어서 캐러셀 기반 사용자 인터페이스를 만드는 방법에 대해 설명합니다.  이 자습서는 Windows 7부터 업데이트 되지 않았지만 Win32 프로그래밍에 대 한 철저 한 소개를 제공 합니다.|
|[C + +의 Windows 프로그래밍 개요](overview-of-windows-programming-in-cpp.md)|C + +에서 Windows 데스크톱 프로그래밍의 주요 기능에 대해 설명 합니다.|

## <a name="see-also"></a>참고 항목

[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)
