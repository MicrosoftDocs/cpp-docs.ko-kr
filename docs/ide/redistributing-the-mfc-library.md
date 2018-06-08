---
title: MFC 라이브러리 재배포 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a49bf18721f605abe0c6e496d3532012c9c92c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340400"
---
# <a name="redistributing-the-mfc-library"></a>MFC 라이브러리 재배포
MFC 라이브러리에 응용 프로그램을 동적 연결하는 경우 일치하는 MFC DLL을 재배포해야 합니다. 예를 들어 Visual Studio 2015와 함께 제공되는 MFC의 버전을 사용하여 MFC 앱을 빌드하는 경우 사용자 앱이 narrow 문자 또는 유니코드 지원에 대해 컴파일되는지 여부에 따라 mfc140.dll 또는 mfc140u.dll을 재배포해야 합니다.  
  
> [!NOTE]
>  mfc140.dll 파일은 Visual Studio 2015 RTM의 재배포 가능 파일 디렉터리에서 생략되었습니다. 대신 Windows\system32 및 Windows\syswow64 디렉터리에서 Visual Studio 2015가 설치할 버전을 사용할 수 있습니다.  
  
 모든 MFC DLL은 CRT(C 런타임 라이브러리)의 공유 버전을 사용하므로 CRT를 재배포해야 할 수도 있습니다. Visual Studio 2015와 함께 제공되는 MFC 버전은 Windows 10의 일부로 배포되는 범용 CRT 라이브러리를 사용합니다. 이전 버전의 Windows에서 Visual Studio 2015를 사용하여 빌드한 MFC 응용 프로그램을 실행하려면 범용 CRT를 재배포해야 합니다. 운영 체제 구성 요소로서 또는 로컬 배포를 사용하여 범용 CRT를 재배포하는 방법에 대한 내용은 [범용 CRT 소개](http://go.microsoft.com/fwlink/p/?linkid=617977)를 참조합니다. 지원되는 버전의 Windows에서 중앙 배포에 대한 범용 CRT를 다운로드하려면 [Windows 10 유니버설 C 런타임](http://go.microsoft.com/fwlink/p/?LinkId=619489)을 참조합니다. 로컬 배포에 대한 ucrtbase.dll의 재배포 가능 아키텍처별 버전은 Windows SDK에 있습니다. 기본적으로 Visual Studio는 아키텍처별 하위 디렉터리의 C:\Program Files (x86)\Windows Kits\10\Redist\ucrt\DLLs\에 이러한 버전을 설치합니다.  
  
 이전 버전의 MFC 라이브러리를 사용하여 앱을 빌드하는 경우 재배포 가능 파일 디렉터리에서 일치하는 CRT DLL을 재배포해야 합니다. 예를 들어 Visual Studio 2013(vc120) 도구 집합을 사용하여 MFC 응용 프로그램을 빌드하는 경우 msvcr120.dll을 재배포해야 합니다. 일치하는 mfc`<version>`u.dll 또는 mfc`<version>`.dll도 재배포해야 합니다.  
  
 응용 프로그램을 MFC에 정적으로 연결하는 경우(즉, **속성 페이지** 대화 상자의 **일반** 탭에서 **정적 라이브러리에서 MFC 사용**을 지정하는 경우) MFC DLL을 재배포할 필요가 없습니다. 그러나 정적 연결이 응용 프로그램의 내부 배포 및 테스트에 사용될 수 있다 해도 MFC를 재배포하는 데는 사용하지 않는 것이 좋습니다. Visual C++ 라이브러리를 배포하는 데 권장되는 전략에 대한 자세한 내용은 [배포 방법 선택](../ide/choosing-a-deployment-method.md)을 참조합니다.  
  
 응용 프로그램이 WebBrowser 컨트롤(예: [CHtmlView 클래스](../mfc/reference/chtmlview-class.md) 또는 [CHtmlEditView 클래스](../mfc/reference/chtmleditview-class.md))을 구현하는 MFC 클래스를 사용하는 경우 대상 컴퓨터에 최신 공통 제어 파일이 있을 수 있도록 최신 버전의 Microsoft Internet Explorer를 설치하는 것이 좋습니다. (최소 Internet Explorer 4.0이 필요합니다.) Internet Explorer 구성 요소를 설치하는 방법에 대한 정보는 Microsoft 지원 웹 사이트의 "문서 185375: Internet Explorer의 단일 EXE 설치 만들기"에서 가능합니다.  
  
 응용 프로그램이 MFC 데이터베이스 클래스를 사용하는 경우(예: [CRecordset 클래스](../mfc/reference/crecordset-class.md) 및 [CRecordView 클래스](../mfc/reference/crecordview-class.md)), 응용 프로그램에서 사용하는 ODBC 및 모든 ODBC 드라이버를 재배포해야 합니다. 자세한 내용은 [데이터베이스 지원 파일 재배포](../ide/redistributing-database-support-files.md)를 참조하세요.  
  
 MFC 응용 프로그램이 Windows Forms 컨트롤을 사용하는 경우 응용 프로그램과 함께 mfcmifc80.dll을 재배포해야 합니다. 이 DLL은 해당 응용 프로그램 로컬 폴더의 응용 프로그램을 통해 또는 [Gacutil.exe(전역 어셈블리 캐시 도구)](/dotnet/framework/tools/gacutil-exe-gac-tool)를 사용하여 GAC(전역 어셈블리 캐시)에 배포하여 재배포될 수 있는 strong-name-signed .NET 어셈블리입니다.  
  
 MFC DLL을 재배포하는 경우 반드시 디버그 버전이 아니라 일반 정품 버전을 재배포해야 합니다. DLL의 디버그 버전은 재배포할 수 없습니다. MFC DLL의 디버그 버전 이름은 "d"로 끝납니다(예: Mfc140d.dll).  
  
 VCRedist_*architecture*.exe 또는 Visual Studio와 함께 설치된 병합 모듈을 사용하거나 응용 프로그램과 동일한 폴더에 MFC DLL을 배포하여 MFC를 재배포할 수 있습니다. MFC를 재배포하는 방법에 대한 자세한 내용은 [Visual C++ 파일 재배포](../ide/redistributing-visual-cpp-files.md)를 참조하세요.  
  
## <a name="installation-of-localized-mfc-components"></a>지역화된 MFC 구성 요소 설치  
 MFC 지역화 DLL을 설치하여 응용 프로그램을 지역화하려는 경우 재배포 가능 병합 파일(.msm)을 사용해야 합니다. 예를 들어 x86 컴퓨터에서 응용 프로그램을 지역화하려는 경우 x86 컴퓨터용 설치 패키지에 Microsoft_VC`<version>`_MFCLOC_x86.msm을 병합해야 합니다.  
  
 재배포 가능 .msm 파일에는 지역화에 사용되는 DLL이 포함되어 있습니다. 지원되는 각 언어당 하나의 DLL이 있습니다. 설치 프로세스는 대상 컴퓨터의 %windir%\system32\ 폴더에 이러한 Dll을 설치합니다.  
  
 MFC 응용 프로그램을 지역화하는 방법에 대한 자세한 내용은 [TN057: MFC 구성 요소 지역화](../mfc/tn057-localization-of-mfc-components.md) 및 Microsoft 지원 웹 사이트의 [문서 208983: MFC LOC DLL 사용 방법](http://go.microsoft.com/fwlink/p/?linkid=198025)을 참조하십시오.  
  
 응용 프로그램 로컬 폴더에 MFC DLL을 배포하여 MFC 지역화 DLL을 재배포할 수 있습니다. Visual C++ 라이브러리를 재배포하는 방법에 대한 자세한 내용은 [Visual C++ 파일 재배포](../ide/redistributing-visual-cpp-files.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Visual C++ 파일 재배포](../ide/redistributing-visual-cpp-files.md)