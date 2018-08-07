---
title: 데스크톱 응용 프로그램(Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4cd8e8c6e3b9626000a8bef3d86a89f5e122d611
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571531"
---
# <a name="desktop-applications-visual-c"></a>데스크톱 응용 프로그램(Visual C++)
C++를 이용한 *데스크톱 응용 프로그램*은 전체 Windows API를 모두 사용할 수 있으며 Windows나 시스템 콘솔 창에서 실행할 수 있는 네이티브 응용 프로그램입니다. 데스크톱 응용 프로그램은 Windows XP부터 Windows 10에 이르기까지 실행될 수 있습니다. (Windows XP는 더 이상 공식적으로 지원되지 않으며 이후 도입된 많은 Windows API가 존재합니다.)

데스크톱 응용 프로그램은 Windows 10에서 실행하는 PC, XBox, Windows Phone, Surface Hub 및 기타 장치에서 실행할 수 있는 한 유니버설 Windows 플랫폼(UWP) 앱과 다릅니다. 데스크톱과 UWP 응용 프로그램을 참조 하세요 [기술을 선택](https://msdn.microsoft.com/library/windows/desktop/dn614993\(v=vs.85\).aspx)합니다.  


**데스크톱 브리지** Windows API 집합에 Windows 10 기존 데스크톱 응용 프로그램 또는 COM 개체로 UWP 앱 패키지를 UWP 터치, 또는 최신에서 Api 호출 등의 기능을 추가할 수 있습니다. 또한 Visual Studio 및 패키지 및 Windows Api를 사용 하 여 서로 통신 해야 단일에서 패키지에서 데스크톱 솔루션에 UWP 앱을 추가할 수 있습니다.  
   
Visual Studio 2017 버전 15.4 이상에서 크게 기존 데스크톱 응용 프로그램을 패키징하는 작업을 단순화 하는 Windows 응용 프로그램 패키지 프로젝트를 만들 수 있습니다. 어떤 레지스트리 호출에 대해 몇 가지 제한 사항이 적용 됩니다. 또는 데스크톱 응용 프로그램 Api 사용 하지만 대부분의 앱 패키지에 실행 하는 동안 유사한 기능을 달성 하기 위해 대체 코드 경로 만들 수 있습니다. 자세한 내용은 [데스크톱 브리지](/windows-uwp/porting/desktop-to-uwp-root)를 참조하세요.  
  
 **용어**  
  
-   A *Win32* 응용 프로그램은 네이티브 데스크톱 응용 프로그램 수 있도록 하는 c + +에서 사용 하는 Windows [Windows C Api 및/또는 COM Api](https://msdn.microsoft.com/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT 및 표준 라이브러리 Api 및 타사 라이브러리입니다. Win32 응용 프로그램은 개발자가 Windows 프로시저 함수 내에서 Windows 메시지를 명시적으로 처리해준 Windows로 실행될 수 있습니다.  Win32 응용 프로그램이라는 공통된 이름을 사용하지만 32비트(x86) 또는 64비트(x64) 이진 파일로 컴파일할 수 있습니다. Visual Studio IDE에서 x86 용어 및 Win32는 동의어입니다.  
  
-   합니다 [구성 요소 개체 모델 (COM)](https://msdn.microsoft.com/library/windows/desktop/ms694363\(v=vs.85\).aspx) 는 서로 통신할 수 있는 다른 언어로 작성 된 프로그램을 사용 하도록 설정 하는 사양입니다. 많은 Windows 구성요소가 COM 개체로 구현되어 있으며 표준 COM 규칙에 따라 생성, 검색 및 소멸됩니다.  C++ 데스크톱 응용 프로그램의 COM 개체를 사용하는 것은 비교적 간단하지만 고유한 COM 개체를 작성하는 것은 더 높은 수준입니다. [라이브러리 ATL(액티브 템플릿)](../atl/atl-com-desktop-components.md)은 매크로 및 COM 개발을 간소화하는 도우미 함수를 제공합니다.  
  
-   MFC 응용 프로그램은 사용하는 Windows 데스크톱 응용 프로그램의 [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md)를 이용해 사용자 인터페이스를 만들 수 있습니다. MFC 응용 프로그램 역시 CRT 및 표준 라이브러리 API뿐만 아니라 COM 구성 요소를 사용할 수도 있습니다. MFC는 창 메시지 루프 및 Windows API를 통해 가벼운 C++ 객체 지향 래퍼를 제공합니다. MFC는 응용 프로그램에 대 한 기본 선택-특히 엔터프라이즈 형 응용 프로그램-는 많은 사용자 인터페이스 컨트롤이 나 사용자 지정 컨트롤입니다. MFC 창 관리, 직렬화, 텍스트 조작, 인쇄 및 리본과 같은 최신 사용자 인터페이스 요소에 대한 편리한 도우미 클래스를 제공합니다. MFC를 효율적으로 적용하려면 Win32에 대해 잘 알고 있어야 합니다.  
  
-   C++/CLI 응용 프로그램 또는 구성요소를 사용하고 C++ 구문을 확장(C++ 사양에서 허용 됨)하여 .NET과 네이티브 C++ 코드 간의 상호작용을 가능하도록 합니다.  C++/CLI 응용 프로그램은 네이티브로 실행하는 부분과 .NET 기본 클래스 라이브러리에 액세스할 수 있는 .NET 프레임워크에서 실행되는 부분으로 구성됩니다. C++/CLI는 C# 또는 Visual Basic으로 작성된 코드와 함께 동작하는 네이티브 C++ 코드가 필요할 경우 먼저 고려할 수 있는 방식입니다. 사용자 인터페이스 코드가 아닌 .NET DLL에서 주로 사용됩니다. 자세한 내용은 [.NET 프로그래밍 C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)를 참조합니다.  
  
 C++로 만든 Windows 데스크톱 응용 프로그램이라면 CRT(C 런타임) 및 표준 라이브러리 클래스 및 함수, COM 개체 및 공용 Windows 함수라고 통칭 Windows API를 사용할 수 있습니다. C++의 Windows 데스크톱 응용 프로그램에 대한 소개는 [C++로 만드는 Windows용 프로그램 알아보기](http://go.microsoft.com/fwlink/p/?LinkId=262281)(영문)를 참조하세요.  
  
## <a name="in-this-section"></a>단원 내용  
  
|제목|설명|  
|-----------|-----------------|  
|[콘솔 응용 프로그램](../windows/console-applications-in-visual-cpp.md)|콘솔 앱에 대한 정보가 들어 있습니다. Win32 또는 Win64 콘솔 응용 프로그램에는 고유의 창이나 메시지 루프가 없습니다. 콘솔 창에서 실행되고 입력 및 출력이 명령줄을 통해 처리됩니다.|  
|[Windows 데스크톱 응용 프로그램](../windows/windows-desktop-applications-cpp.md)|콘솔 아닌 windows에서 실행 되는 데스크톱 응용 프로그램을 만드는 방법입니다.|  
|[DirectX (C++)를 사용하여 게임을 만들기 위한 리소스](../windows/resources-for-creating-a-game-using-directx.md)|C++을 이용한 게임 만들기에 대한 콘텐츠가 연결되어 있습니다.|  
|[연습: 정적 라이브러리 만들기 및 사용](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|.lib 이진 파일을 만드는 방법입니다.|  
|[방법: Windows 데스크톱 응용 프로그램에서 Windows 10 SDK 사용](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows 10 SDK를 사용하여 빌드할 프로젝트를 설정하는 단계를 설명합니다.|  
  
## <a name="related-articles"></a>관련 문서  
  
|제목|설명|  
|-----------|-----------------|  
|[Windows Development](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Windows API 및 COM에 대한 정보를 제공합니다. 일부 Windows API 및 타사 DLL이 COM 개체로 구현됩니다.|  
|[Hilo: Developing C++ Applications for Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Windows Animation 및 Direct2D를 사용하는 리치 클라이언트 Windows 데스크톱 응용 프로그램을 만들어서 캐러셀 기반 사용자 인터페이스를 만드는 방법에 대해 설명합니다.  이 자습서에서는 Windows 7 이후 업데이트되지 않았지만 여전히 Win32 프로그래밍에 대한 소개를 제공합니다.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual Studio에 포함된 Visual C++의 주요 기능을 설명하고 Visual C++ 설명서의 나머지 부분에 연결합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Visual C++](../visual-cpp-in-visual-studio.md)