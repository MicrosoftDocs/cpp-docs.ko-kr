---
title: C++의 Windows 프로그래밍 개요
ms.date: 04/06/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6ec12428b090d2317a6f2e5cc493d1e4f9392ff4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494408"
---
# <a name="overview-of-windows-programming-in-c"></a>C++의 Windows 프로그래밍 개요

Windows 서버, 클라우드에서 또는 Xbox에서 다양 한 종류의 (x 86, x64 또는 ARM)는 Windows PC에서 실행 되는 프로그램을 쓸 Visual c + +를 사용할 수 있습니다. 잘 작성 된 c + + 프로그램에 이러한 품질:

- 메모리 요구 사항을 효율적으로
- 전력 소비 경제적인 옵션
- 다중 코어 및 다중 코어 장치를 최대한 활용할 수
- 일반 컴퓨팅 (GPGPU) 그래픽 처리 장치에서 작업을 수행할 수
- 하드웨어에서 다른 최신 고급 기능을 활용할 수 있습니다.

Visual C++를 사용하여 광범위한 범주의 다양한 Windows 앱을 구현할 수 있습니다. 이러한 범주에 서로 다른 프로그래밍 모델 없거나 년간 추가한 앱 모델입니다. 각 모델 플랫폼에 대 한 액세스를 제공 하 고 창 및 대화 상자와 같은 사용자 인터페이스를 만들 다른 라이브러리 및 Api를 사용 합니다. UWP에 대 한 몇 가지 제한 사항이 이러한 범주 중 하나에서 타사 라이브러리 뿐만 아니라 c + + 표준 라이브러리를 사용할 수 있습니다.

- [Windows 유니버설 앱](#BK_WindowsUniversal). Windows 앱의 세 번째 범주는 Windows 8에 처음 추가되었고 이 앱 범주는 Windows 10에서 계속 지원됩니다. 이 앱을 "Windows 앱"이라고도 하며 다양한 장치를 대상으로 하는 데스크톱 및 모바일 앱을 포함합니다. C++/CX, Windows 런타임 개발 지원이 포함된 C++ 언어 또는 WRL(Windows 런타임 라이브러리)을 사용하는 COM을 통한 표준 C++로 이러한 앱을 작성할 수 있습니다. 이들 앱은 원래 전체 화면으로 실행되도록 디자인되었으나 Windows 10 사용자는 데스크톱 창에서 이들 앱을 실행할 수 있습니다. 이들 앱은 터치를 지향하지만 사용자가 원하거나 터치 화면이 없으면 마우스로 쉽게 작동할 수 있습니다. 이러한 앱은 Microsoft Store 유발한 "Store" 앱을 호출 되 고 팩트에서 배포 됩니다.

UWP 앱, 휴대폰 및 태블릿 같은 모든 Windows 10 장치 및 데스크톱에서 실행할 수 있습니다. 데스크톱에서는 항상 전체 화면으로 실행되지 않고 데스크톱 창으로 실행될 수 있습니다. 이러한 앱은 Xbox 및 앞으로 제공될 장치에서도 실행될 수 있습니다.  UWP 앱 사용자 인터페이스 요소, 서비스 및 Windows에서 지원 되는 다양 한 하드웨어 장치에 대 한 인터페이스를 제공 하는 Windows 런타임에서 실행 됩니다.

C +의 UWP 앱을 작성할 수 있습니다 + CX, c + + 언어 사용할 수는 [C + + /cli WinRT 라이브러리](https://moderncpp.com/) 몇 가지 시나리오에 대 한 합니다. UWP 앱을 네이티브 코드로 컴파일 및 XAML 사용자 인터페이스가 있거나 DirectX를 사용 합니다. Windows 런타임 구성 요소는 네이티브 코드로 작성 된 UWP 앱의 다른 언어로 작성 된 사용할 수 있습니다. 자세한 내용은 [c + + 유니버설 Windows 플랫폼 앱을 만들](http://go.microsoft.com/fwlink/?LinkID=534976)를 [DirectX를 사용 하 여 첫 번째 UWP 게임을 만들](http://go.microsoft.com/fwlink/p/?LinkId=244656), 및 [Windows 런타임 구성 요소 만들기 c + +에서](http://go.microsoft.com/fwlink/p/?LinkId=244658)합니다.

   이 범주에는 서버 및 클라우드 프로그래밍의 컨텍스트에서 핵심 구성 요소 및 계산 코드에 C++를 사용하는 경우도 포함됩니다. 경우에 따라 서버 또는 클라우드 응용 프로그램의 핵심 부분에서 성능 집중적인 코드를 C++로 작성하여 성능을 최대화합니다. 해당 코드를 DLL로 컴파일하고 C# 또는 Visual Basic에서 이 코드를 사용할 수 있습니다.

- **.NET Framework 응용 프로그램**. 대부분의.NET Framework 응용 프로그램은 C# 또는 Visual Basic로 작성 하 고 있지만 C + + CLI (의 `/clr` Visual c + +에서 컴파일러 옵션). 관리되는 코드와 네이티브 코드를 포함하는 더 큰 응용 프로그램에서는 최소한 interop 레이어에 대해 C++/CLI를 사용하는 것이 좋습니다.

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

Windows 10에서는 태블릿, 휴대폰 및 데스크톱과 같은 모든 Windows 10 장치에서 앱을 실행할 수 있습니다. 데스크톱에서는 항상 전체 화면으로 실행되지 않고 데스크톱 창으로 실행될 수 있습니다. 이러한 앱은 Xbox 및 앞으로 제공될 장치에서도 실행될 수 있습니다.  두 앱 형식에 대한 프로그래밍 모델은 Win32 데스크톱 응용 프로그램과 다릅니다. 이러한 Windows 앱은 사용자 인터페이스 요소, 이들 앱에 대한 필수 서비스 및 지원되는 다양한 하드웨어 장치에 대한 인터페이스를 제공하는 Windows 런타임에서 실행됩니다. 이들 앱은 네이티브 코드로 컴파일되고 XAML 사용자 인터페이스가 있거나 DirectX를 사용합니다. 다른 Windows 앱을 사용할 수 있는 네이티브 코드에서 Windows 런타임 구성 요소를 작성할 수도 있습니다-C#, Visual Basic 또는 JavaScript로 작성 된 응용 프로그램입니다. 자세한 내용은 [c + + UWP "Hello world" 앱을 만들](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)를 [DirectX를 사용 하 여 간단한 UWP 게임을 만들기](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), 및 [Windows 런타임 구성 요소 만들기 c + +에서](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)합니다.

> [!TIP]
> Windows 10용 Microsoft 스토어를 통해 배포하기 위해 기존 데스크톱 응용 프로그램을 패키지하는 데스크톱 앱 변환기를 사용할 수 있습니다. 자세한 내용은 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)(Centennial 프로젝트에서 Visual C++ 런타임 사용) 및 [데스크톱 브리지를 사용하여 데스크톱 앱을 UWP(유니버설 Windows 플랫폼)로 가져오기](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root)를 참조하세요.

유니버설 Windows 플랫폼 샘플에 대한 자세한 내용은 [GitHub의 Windows 유니버설 샘플](https://github.com/Microsoft/Windows-universal-samples)을 참조하세요.

기존 Windows 8.1 프로젝트가 있고 Windows 10으로 포팅 하려는 경우 참조 [유니버설 Windows 플랫폼으로 포팅](../porting/porting-to-the-universal-windows-platform-cpp.md)합니다. 내용은 UWP 앱에 통합 하려는 기존의 클래식 Win32 데스크톱 라이브러리 및 코드가 있는 경우 [방법: 유니버설 Windows 플랫폼 앱에서 기존 c + + 코드를 사용 하 여](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)입니다.

일반적으로 참조 UWP에 대 한 자세한 내용은 [유니버설 Windows 플랫폼 (UWP) 앱 이란?](/windows/uwp/get-started/whats-a-uwp)합니다.

이러한 모든 개념에 대한 자세한 내용은 [Windows 유니버설 앱 가이드](http://go.microsoft.com/fwlink/p/?linkid=534605)를 참조하세요.

##  <a name="BK_Native"></a> 데스크톱 및 서버 응용 프로그램

데스크톱용 Windows 클라이언트 응용 프로그램 작성의 기본 사항을 알아보려면 [C++에서 Windows 응용 프로그램 개발](https://msdn.microsoft.com/vstudio//hh304489) 및 [C++에서 Windows 프로그래밍 소개](https://msdn.microsoft.com/library/windows/desktop/ff381398)를 참조하세요.

Windows 10에서 다양 한 데스크톱 프로그램을 만들려면 Visual c + +를 사용할 수 있습니다.

- 명령줄 응용 프로그램 및 유틸리티 자세한 내용은 [콘솔 응용 프로그램](../windows/console-applications-in-visual-cpp.md)합니다.

- 정교한 그래픽 사용자 인터페이스의 소비자 응용 프로그램 자세한 내용은 [Hilo: Windows용 C++ 응용 프로그램 개발](http://go.microsoft.com/fwlink/p/?LinkId=256417)을 참조하세요.

- .NET Framework에서 실행 되는 엔터프라이즈 및 기간 업무 앱 대부분의.NET Framework 응용 프로그램은 C# 또는 Visual Basic에서 기록 됩니다. 에서는 C + + 네이티브 c + + 라이브러리를 사용 하는.NET 코드를 사용 하도록 설정 하는 interop 레이어를 만들려면 CLI입니다. 자세한 내용은 [.NET 프로그래밍 C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)를 참조합니다.

- 네이티브 코드에서 실행되는 SQL 데이터베이스 클라이언트 자세한 내용은 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)를 참조하세요.

- Microsoft Office 응용 프로그램의 추가 기능 자세한 내용은 [Outlook 2010의 C++ 추가 기능 빌드](http://go.microsoft.com/fwlink/p/?LinkId=256420)를 참조하세요.

- 장치 드라이버 자세한 내용은 [WDK(Windows 드라이버 키트)](http://go.microsoft.com/fwlink/p/?LinkId=256421)를 참조하세요.

- Windows 서비스. 자세한 내용은 [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications)을 참조하세요.

Visual C++를 사용하여 C++ 응용 프로그램이나 C# 또는 Visual Basic과 같은 다른 언어로 작성된 앱이 소비할 수 있는 Win32 DLL 또는 COM DLL에서 거의 모든 종류의 사용자 지정 고성능 기능을 패키지할 수 있습니다. WIn32 DLL에 대한 자세한 내용은 [DLLs in Visual C++](../build/dlls-in-visual-cpp.md)를 참조하세요. COM 개발에 대한 자세한 내용은 [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal)을 참조하세요.

## <a name="games"></a>게임

DirectX 게임은 PC 또는 Xbox에서 실행할 수 있습니다. 자세한 내용은 [DirectX 개발자 센터](http://go.microsoft.com/fwlink/p/?LinkId=256418)를 참조하세요.

## <a name="sdks-libraries-and-header-files"></a>Sdk, 라이브러리 및 헤더 파일

Visual c + +는 C 런타임 라이브러리 (CRT), c + + 표준 라이브러리 및 기타 Microsoft 전용 라이브러리를 포함합니다. 이러한 라이브러리에 대 한 헤더 파일이 포함 된 포함 폴더는 \VC\ 폴더 아래에서 또는 Windows SDK 설치 폴더에서 CRT의 경우 Visual Studio 설치 디렉터리에서.

사용할 수는 [Vcpkg 패키지 관리자](../vcpkg.md) 편리 하 게 Windows에 대 한 수백 개의 타사 오픈 소스 라이브러리를 설치 합니다.

Microsoft 라이브러리는 다음과 같습니다.

- MFC(Microsoft Foundation Class): 단추, 목록 상자, 트리 뷰 및 기타 컨트롤이 있는 다양한 기능의 사용자 인터페이스가 있는 일반적인 Windows 프로그램, 특히 엔터프라이즈 응용 프로그램을 만들기 위한 개체 지향 프레임워크입니다. 자세한 내용은 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)을 참조하세요.

- ATL(Active Template Library): COM 구성 요소를 만들기 위한 강력한 도우미 라이브러리입니다. 자세한 내용은 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)을 참조하세요.

- C++ AMP(C++ Accelerated Massive Parallelism): GPU에서 고성능 일반 계산 작업에 사용할 수 있는 라이브러리입니다. 자세한 내용은 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)을 참조하세요.

- 동시성 런타임: 다중 코어 및 다중 코어 장치에 대한 병렬 및 비동기 프로그래밍 작업을 간소화하는 라이브러리입니다. 자세한 내용은 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)을 참조하세요.

많은 Windows 프로그래밍 시나리오에는 Windows 운영 체제 구성 요소에 액세스할 수 있는 헤더 파일을 포함하는 Windows SDK도 필요합니다. 기본적으로 Visual Studio는 유니버설 Windows 앱을 개발할 수 있도록 하는 c + + 데스크톱 워크 로드의 구성 요소로 Windows SDK를 설치 합니다. UWP 앱을 개발 하려면 Windows 10 버전의 Windows SDK를 해야 합니다. 정보를 참조 하세요 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)합니다. (이전 버전 Windows의 Windows Sdk에 대 한 자세한 내용은 참조는 [Windows SDK 아카이브](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**프로그램 파일 (x86) \Windows 키트** 설치 된 Windows SDK의 모든 버전에 대 한 기본 위치입니다.

Xbox, Azure 등 다른 플랫폼은 설치가 필요한 고유의 SDK가 있습니다. 자세한 내용은 DirectX 개발자 센터 및 Azure 개발자 센터를 참조하세요.

## <a name="development-tools"></a>개발 도구

Visual Studio는 네이티브 코드에 대한 강력한 디버거, 정적 분석 도구, 그래픽 디버깅 도구, 완벽한 기능을 갖춘 코드 편집기, 유닛 테스트 지원 및 다른 많은 도구와 유틸리티를 포함합니다. 자세한 내용은 [Visual Studio를 사용 하 여 개발 시작 하기](/visualstudio/ide/get-started-developing-with-visual-studio), 및 [IDE 및 개발 도구](../ide/ide-and-tools-for-visual-cpp-development.md)합니다.

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual c + + 개발자 콘텐츠에 대 한 부모 항목입니다.|
