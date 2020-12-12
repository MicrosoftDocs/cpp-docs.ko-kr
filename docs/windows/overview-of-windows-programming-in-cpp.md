---
description: '자세한 정보: c + +의 Windows 프로그래밍 개요'
title: C++의 Windows 프로그래밍 개요
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 812fef686208f5f9d4f1c23cd5eb9b2cb8b227bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180112"
---
# <a name="overview-of-windows-programming-in-c"></a>C++의 Windows 프로그래밍 개요

C + +를 사용 하 여 만들 수 있는 다양 한 Windows 응용 프로그램 범주가 있습니다. 각에는 자체 프로그래밍 모델 및 Windows 관련 라이브러리 집합이 있으며 c + + 표준 라이브러리와 타사 c + + 라이브러리를 모두 사용할 수 있습니다.

이 섹션에서는 Visual Studio 및 MFC/ATL 래퍼 라이브러리를 사용 하 여 Windows 프로그램을 만드는 방법을 설명 합니다. Windows 플랫폼 자체에 대 한 설명서는 [windows 설명서](/windows/index)를 참조 하십시오.

## <a name="command-line-console-applications"></a>명령줄 (콘솔) 응용 프로그램

C + + 콘솔 응용 프로그램은 콘솔 창의 명령줄에서 실행 되며 텍스트 출력만 표시할 수 있습니다. 자세한 내용은 [c + +에서 콘솔 계산기 만들기](../get-started/tutorial-console-cpp.md)를 참조 하세요.

## <a name="native-desktop-client-applications"></a>네이티브 데스크톱 클라이언트 응용 프로그램

*네이티브 데스크톱 클라이언트 응용 프로그램* 은 원래 네이티브 [Windows c api 또는 COM (구성 요소 개체 모델) api](/windows/win32/apiindex/windows-api-list) 를 사용 하 여 운영 체제에 액세스 하는 c 또는 c + + 창 응용 프로그램입니다. 이러한 Api는 대부분 C로 작성 됩니다. 네이티브 데스크톱 응용 프로그램을 만드는 방법에는 여러 가지가 있습니다. 즉, 운영 체제 이벤트를 처리 하는 C 스타일 메시지 루프를 사용 하 여 Win32 Api를 직접 사용할 수 있습니다. 또는 Win32를 래핑하는 약간의 개체 지향 c + + 라이브러리인 *Microsoft Foundation Classes* (MFC)를 사용 하 여 프로그래밍할 수 있습니다. 두 방법 모두 UWP (유니버설 Windows 플랫폼)와 비교 하 여 "최신"으로 간주 되지는 않지만 현재는 완전히 지원 되며, 오늘날 전 세계 수백만 줄의 코드가 실행 되 고 있습니다. 창에서 실행 되는 Win32 응용 프로그램의 경우 개발자는 Windows 프로시저 함수 내에서 Windows 메시지를 사용 하 여 명시적으로 작업 해야 합니다. 이름에도 불구 하 고 Win32 응용 프로그램을 32 비트 (x86) 또는 64 비트 (x64) 이진으로 컴파일할 수 있습니다. Visual Studio IDE에서 x86 및 Win32 용어는 동의어입니다.

기존 Windows c + + 프로그래밍을 시작 하려면 [Win32 및 c + + 시작](/windows/win32/LearnWin32/learn-to-program-for-windows)을 참조 하세요. Win32를 이해 하 고 나면 [MFC 데스크톱 응용 프로그램](../mfc/mfc-desktop-applications.md)에 대해 더 쉽게 알아볼 수 있습니다. 정교한 그래픽을 사용 하는 기존 c + + 데스크톱 응용 프로그램의 예는 [Hilo: Windows 용 c + + 응용 프로그램 개발](/previous-versions/msdn10/ff708696(v=msdn.10))을 참조 하세요.

### <a name="c-or-net"></a>C + + 또는 .NET

일반적으로 c #의 .NET 프로그래밍은 더 복잡 하 고 오류가 발생 하기 쉬우며 Win32 또는 MFC 보다 최신 개체 지향 API를 포함 합니다. 대부분의 경우 성능이 적합 합니다. .NET은 다양 한 그래픽을 위한 Windows Presentation Foundation (WPF) 기능을 제공 하며, Win32 및 최신 Windows 런타임 API를 모두 사용할 수 있습니다. 일반적으로 필요한 경우 데스크톱 응용 프로그램에 c + +를 사용 하는 것이 좋습니다.

- 메모리 사용에 대 한 정확한 제어
- 전력 소비의 가장 경제적
- 일반 컴퓨팅을 위한 GPU 사용
- DirectX에 대 한 액세스
- 표준 c + + 라이브러리의 과도 한 사용

또한 c + +의 기능과 효율성을 .NET 프로그래밍과 결합할 수 있습니다. C #에서 사용자 인터페이스를 만들고 c + +/CLI를 사용 하 여 응용 프로그램에서 네이티브 c + + 라이브러리를 사용할 수 있도록 할 수 있습니다. 자세한 내용은 [c + +/cli를 사용한 .Net 프로그래밍](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조 하세요.

## <a name="com-components"></a>COM 구성 요소

[COM (구성 요소 개체 모델)](/windows/win32/com/the-component-object-model) 은 서로 다른 언어로 작성 된 프로그램이 서로 통신할 수 있도록 하는 사양입니다. 많은 Windows 구성 요소가 COM 개체로 구현 되며 개체 만들기, 인터페이스 검색 및 개체 소멸에 대 한 표준 COM 규칙을 따릅니다.  C + + 데스크톱 응용 프로그램에서 COM 개체를 사용 하는 것은 비교적 간단 하지만 고유한 COM 개체를 작성 하는 것이 더 고급입니다. [ATL (액티브 템플릿 라이브러리)](../atl/atl-com-desktop-components.md) 은 COM 개발을 간소화 하는 매크로 및 도우미 함수를 제공 합니다. 자세한 내용은 [ATL COM 데스크톱 구성 요소](../atl/atl-com-desktop-components.md)를 참조 하세요.

## <a name="universal-windows-platform-apps"></a>유니버설 Windows 플랫폼 앱

UWP (유니버설 Windows 플랫폼)는 최신 Windows API입니다. UWP 앱은 모든 Windows 10 장치에서 실행 되 고, 사용자 인터페이스에 대해 XAML을 사용 하며, 완벽 하 게 터치 가능 합니다. UWP에 대 한 자세한 내용은 [uwp (유니버설 Windows 플랫폼) 앱 이란?](/windows/uwp/get-started/whats-a-uwp) 및 [Windows 유니버설 앱에](/windows/uwp/get-started/universal-application-platform-guide)대 한 가이드를 참조 하세요.

UWP에 대 한 원래 c + + 지원에는 (1) c + +/CX, 구문 확장이 포함 된 c + + 언어 또는 (2) 표준 c + + 및 COM을 기반으로 하는 Windows 런타임 라이브러리 (WRL)가 포함 되어 있습니다. C + +/CX와 WRL는 모두 계속 지원 됩니다. 새 프로젝트의 경우 표준 c + +를 기반으로 하 고 더 빠른 성능을 제공 하는 [c + +/Winrt](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)를 사용 하는 것이 좋습니다.

## <a name="desktop-bridge"></a>데스크톱 브리지

Windows 10에서는 기존 데스크톱 응용 프로그램 또는 COM 개체를 UWP 앱으로 패키지 하 고, 터치와 같은 UWP 기능을 추가 하거나, 최신 Windows API 집합에서 Api를 호출할 수 있습니다. 또한 Visual Studio에서 데스크톱 솔루션에 UWP 앱을 추가 하 고 단일 패키지로 함께 패키지 하 고 Windows Api를 사용 하 여 서로 통신할 수 있습니다.

Visual Studio 2017 버전 15.4 이상에서는 기존 데스크톱 응용 프로그램을 패키지 하는 작업을 크게 간소화할 수 있도록 Windows 응용 프로그램 패키지 프로젝트를 만들 수 있습니다. 데스크톱 응용 프로그램에서 사용할 수 있는 레지스트리 호출 또는 Api에는 몇 가지 제한 사항이 적용 됩니다. 그러나 대부분의 경우 응용 프로그램 패키지에서 실행 되는 동안 유사한 기능을 얻기 위해 대체 코드 경로를 만들 수 있습니다. 자세한 내용은 [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root)를 참조하세요.

## <a name="games"></a>게임

DirectX 게임은 PC 또는 Xbox에서 실행할 수 있습니다. 자세한 내용은 [DirectX Graphics And 게이밍](/windows/win32/directx)를 참조 하세요.

## <a name="sql-server-database-clients"></a>SQL Server 데이터베이스 클라이언트

네이티브 코드에서 SQL Server 데이터베이스에 액세스 하려면 ODBC 또는 OLE DB를 사용 합니다. 자세한 내용은 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)를 참조하세요.

## <a name="windows-device-drivers"></a>Windows 디바이스 드라이버

드라이버는 응용 프로그램 및 기타 운영 체제 구성 요소에 액세스할 수 있는 하드웨어 장치에서 데이터를 만드는 하위 수준 구성 요소입니다. 자세한 내용은 [WDK (Windows 드라이버 키트)](/windows-hardware/drivers/index)를 참조 하세요.

## <a name="windows-services"></a>Windows 서비스

Windows *서비스* 는 사용자 조작이 거의 없이 백그라운드에서 실행할 수 있는 프로그램입니다. 이러한 프로그램을 UNIX 시스템의 *디먼* 이라고 합니다. 자세한 내용은 [서비스](/windows/win32/services/services)를 참조하세요.

## <a name="sdks-libraries-and-header-files"></a>Sdk, 라이브러리 및 헤더 파일

Visual Studio는 CRT (C 런타임 라이브러리), c + + 표준 라이브러리 및 기타 Microsoft 전용 라이브러리를 포함 합니다. 이러한 라이브러리에 대 한 헤더 파일을 포함 하는 대부분의 포함 폴더는 Visual Studio 설치 디렉터리의 \VC\ 폴더에 있습니다. Windows 및 CRT 헤더 파일은 Windows SDK 설치 폴더에 있습니다.

[Vcpkg 패키지 관리자](../build/vcpkg.md) 를 사용 하면 Windows 용 수백 개의 타사 오픈 소스 라이브러리를 편리 하 게 설치할 수 있습니다.

Microsoft 라이브러리는 다음과 같습니다.

- MFC(Microsoft Foundation Class): 단추, 목록 상자, 트리 뷰 및 기타 컨트롤이 있는 다양한 기능의 사용자 인터페이스가 있는 일반적인 Windows 프로그램, 특히 엔터프라이즈 애플리케이션을 만들기 위한 개체 지향 프레임워크입니다. 자세한 내용은 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)을 참조하세요.

- ATL(Active Template Library): COM 구성 요소를 만들기 위한 강력한 도우미 라이브러리입니다. 자세한 내용은 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)을 참조하세요.

- C++ AMP(C++ Accelerated Massive Parallelism): GPU에서 고성능 일반 계산 작업에 사용할 수 있는 라이브러리입니다. 자세한 내용은 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)을 참조하세요.

- 동시성 런타임: 다중 코어 및 다중 코어 디바이스에 대한 병렬 및 비동기 프로그래밍 작업을 간소화하는 라이브러리입니다. 자세한 내용은 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)을 참조하세요.

많은 Windows 프로그래밍 시나리오에는 Windows 운영 체제 구성 요소에 액세스할 수 있는 헤더 파일을 포함하는 Windows SDK도 필요합니다. 기본적으로 Visual Studio는 유니버설 Windows 앱 개발을 가능 하 게 하는 c + + 데스크톱 워크 로드의 구성 요소로 Windows SDK를 설치 합니다. UWP 앱을 개발 하려면 Windows SDK의 Windows 10 버전이 필요 합니다. 자세한 내용은 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)를 참조 하세요. 이전 버전의 Windows 용 Windows Sdk에 대 한 자세한 내용은 [Windows SDK 보관](https://developer.microsoft.com/windows/downloads/sdk-archive))을 참조 하세요.

**Program Files (x86) \windows** kit는 설치한 모든 버전의 Windows SDK에 대 한 기본 위치입니다.

Xbox, Azure 등 다른 플랫폼은 설치가 필요한 고유의 SDK가 있습니다. 자세한 내용은 DirectX 개발자 센터 및 Azure 개발자 센터를 참조하세요.

## <a name="development-tools"></a>개발 도구

Visual Studio는 네이티브 코드에 대한 강력한 디버거, 정적 분석 도구, 그래픽 디버깅 도구, 완벽한 기능을 갖춘 코드 편집기, 유닛 테스트 지원 및 다른 많은 도구와 유틸리티를 포함합니다. 자세한 내용은 [Visual studio를 사용 하 여 개발 시작](/visualstudio/ide/get-started-developing-with-visual-studio)및 [Visual Studio의 c + + 개발 개요](../overview/overview-of-cpp-development.md)를 참조 하세요.

## <a name="in-this-section"></a>단원 내용

|제목|설명|
|-----------|-----------------|
|[연습: 표준 c + + 프로그램 만들기](walkthrough-creating-a-standard-cpp-program-cpp.md)| Windows 콘솔 응용 프로그램을 만듭니다.|
|[연습: Windows 데스크톱 애플리케이션 만들기(C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|네이티브 Windows 데스크톱 응용 프로그램을 만듭니다.|
|[Windows 데스크톱 마법사](windows-desktop-wizard.md)|마법사를 사용 하 여 새 Windows 프로젝트를 만듭니다.|
|[ATL(액티브 템플릿 라이브러리)](../atl/atl-com-desktop-components.md)|C + +에서 COM 구성 요소를 만들려면 ATL 라이브러리를 사용 합니다.|
|[MFC(Microsoft Foundation Class)](../mfc/mfc-desktop-applications.md)|MFC를 사용 하 여 대화 상자 및 컨트롤을 사용 하는 크고 작은 Windows 응용 프로그램 만들기|
|[ATL 및 MFC 공유 클래스](../atl-mfc-shared/atl-mfc-shared-classes.md)|ATL 및 MFC에서 공유 되는 CString과 같은 클래스를 사용 합니다.|
|[데이터 액세스](../data/data-access-in-cpp.md)| OLE DB 및 ODBC|
|[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)|Windows의 다양 한 문자열 형식입니다.|
|[DirectX를 사용 하 여 게임을 만들기 위한 리소스](resources-for-creating-a-game-using-directx.md)
|[방법: Windows 데스크톱 응용 프로그램에서 Windows 10 SDK 사용](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[리소스 파일 작업](working-with-resource-files.md)|데스크톱 응용 프로그램에 이미지, 아이콘, 문자열 테이블 및 기타 리소스를 추가 하는 방법입니다.|
|[DirectX를 사용하여 게임을 만들기 위한 리소스(C++)](resources-for-creating-a-game-using-directx.md)|C + +로 게임을 만들기 위한 콘텐츠에 대 한 링크입니다.|
|[방법: Windows 데스크톱 응용 프로그램에서 Windows 10 SDK 사용](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows 10 SDK를 사용하여 빌드할 프로젝트를 설정하는 단계를 설명합니다.|
|[네이티브 데스크톱 애플리케이션 배포](deploying-native-desktop-applications-visual-cpp.md)|Windows에서 네이티브 응용 프로그램을 배포 합니다.|

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)|Visual C++ 개발자 콘텐츠에 대 한 부모 항목입니다.|
[C + +/CLI를 사용한 .NET 개발](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|.NET 응용 프로그램 및 구성 요소와의 통신을 가능 하 게 하는 네이티브 c + + 라이브러리에 대 한 래퍼를 만듭니다.|
|[.NET 및 UWP 용 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)|C + +/CX 및 c + +/CLI에서 공유 하는 구문 요소에 대 한 참조|
|[유니버설 Windows 앱(C++)](../cppcx/universal-windows-apps-cpp.md)|C + +/CX 또는 Windows 런타임 템플릿 라이브러리 (WRL)를 사용 하 여 UWP 응용 프로그램을 작성 합니다.|
|[COM 및 .NET의 C++ 특성](attributes/cpp-attributes-com-net.md)|.NET 또는 COM을 사용 하는 Windows 전용 프로그래밍에 대 한 비표준 특성입니다.|
