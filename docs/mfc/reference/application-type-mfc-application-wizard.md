---
description: '자세히 알아보기: 응용 프로그램 종류, MFC 응용 프로그램 마법사'
title: MFC 애플리케이션 마법사, 애플리케이션 종류
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.apptype
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
ms.openlocfilehash: 178e9c1319b17e356273fc3e59d2133c8d4aa54c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322787"
---
# <a name="application-type-mfc-application-wizard"></a>MFC 애플리케이션 마법사, 애플리케이션 종류

[Mfc 응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md) 의이 페이지를 사용 하 여 기본 기능을 디자인 하 고 새 MFC 응용 프로그램에 추가할 수 있습니다.

- **애플리케이션 종류**

  응용 프로그램에 만들려는 문서 지원 유형을 지정 합니다. 응용 프로그램에 사용할 수 있는 사용자 인터페이스 옵션은 선택한 응용 프로그램의 형식에 따라 결정 됩니다. 자세한 내용은 [사용자 인터페이스 기능, MFC 응용 프로그램 마법사를](../../mfc/reference/user-interface-features-mfc-application-wizard.md) 참조 하세요.

   문서 형식에 대 한 자세한 내용은 다음을 참조 하세요.

  - [SDI 및 MDI](../../mfc/sdi-and-mdi.md)

  - [프레임 창](../../mfc/frame-windows.md)

  - [프레임 창 클래스](../../mfc/frame-window-classes.md)

  - [문서, 뷰 및 프레임 워크](../../mfc/documents-views-and-the-framework.md)

  - [대화 상자](../../mfc/dialog-boxes.md)

  |옵션|설명|
  |------------|-----------------|
  |**단일 문서**|응용 프로그램에 대 한 SDI (단일 문서 인터페이스) 아키텍처를 만듭니다. 여기서 뷰 클래스는 [CView 클래스](../../mfc/reference/cview-class.md)를 기반으로 합니다. 마법사의 [MFC 응용 프로그램 마법사, 생성 된 클래스](../../mfc/reference/generated-classes-mfc-application-wizard.md) 에서 뷰의 기본 클래스를 변경할 수 있습니다. 예를 들어, 폼 기반 응용 프로그램을 만들려면 뷰 클래스에 대해 [CFormView 클래스](../../mfc/reference/cformview-class.md) 를 사용 합니다.<br /><br /> 이 유형의 응용 프로그램에서 문서의 프레임 창은 하나의 문서만 포함할 수 있습니다.|
  |**여러 문서**|응용 프로그램에 대해 뷰 클래스의 기반이 되는 MDI (다중 문서 인터페이스) 아키텍처를 만듭니다 `CView` . 마법사의 **생성 된 클래스** 페이지에서 뷰의 기본 클래스를 변경할 수 있습니다. 예를 들어 `CFormView` 뷰 클래스에 대해를 사용 하 여 양식 기반 응용 프로그램을 만듭니다.<br /><br /> 이 유형의 응용 프로그램에서 문서의 프레임 창은 여러 자식 창을 포함할 수 있습니다.|
  |**탭 문서**|각 문서를 별도의 탭에 배치 합니다.|
  |**대화 상자 기반**|대화 상자 클래스의 기반이 되는 응용 프로그램에 대 한 대화 상자 기반 아키텍처를 만듭니다 `CDialog` . HTML 대화 상자를 만들려면 **html 대화 상자 사용** 상자를 선택 합니다.|
  |**HTML 대화 상자 사용**|대화 상자 응용 프로그램에만 해당 합니다. [CDialog 클래스](../../mfc/reference/cdialog-class.md)대신 [CDHtmlDialog 클래스](../../mfc/reference/cdhtmldialog-class.md) 에서 dialog 클래스를 파생 합니다. 이 확인란을 선택 하면 `CDHtmlDialog` 마법사의 [MFC 응용 프로그램 마법사, 생성 된 클래스](../../mfc/reference/generated-classes-mfc-application-wizard.md) 의 **기본 클래스** 상자에이 표시 됩니다.<br /><br /> `CDHtmlDialog`파생 된 대화 상자는 html 기반 대화 상자를 표시 하 고, 데이터를 html 컨트롤과 교환 하 고, html 이벤트를 처리 합니다.|
  |**여러 최상위 문서**|뷰 클래스의 기반이 되는 응용 프로그램에 대 한 여러 최상위 아키텍처를 만듭니다 `CView` .<br /><br /> 이 유형의 응용 프로그램에서는 사용자가 **파일** 메뉴에서 **새로 만들기** (또는 **새 프레임**)를 클릭할 때 응용 프로그램에서 부모가 바탕 화면에 암시적으로 포함 된 창을 만듭니다. 새 문서 프레임이 작업 표시줄에 표시 되며 응용 프로그램 창의 클라이언트 영역으로 제한 되지 않습니다.|

- **문서/뷰 아키텍처 지원**

  [CDocument 클래스](../../mfc/reference/cdocument-class.md) 및 [CView 클래스](../../mfc/reference/cview-class.md) (기본값)를 사용 하 여 응용 프로그램에 문서/뷰 아키텍처를 포함할지 여부를 지정 합니다. 비 MFC 응용 프로그램을 이식 하는 경우 또는 컴파일된 실행 파일의 크기를 줄이려면이 확인란의 선택을 취소 합니다. 기본적으로 문서/뷰 아키텍처가 없는 응용 프로그램은 [CWinApp 클래스](../../mfc/reference/cwinapp-class.md)에서 파생 되며, 디스크 파일에서 문서를 열기 위한 MFC 지원을 포함 하지 않습니다.

- **리소스 언어**

  리소스의 언어를 설정 합니다. 이 목록에는 Visual Studio에서 설치 된 대로 시스템에서 사용할 수 있는 언어가 표시 됩니다. 시스템 언어가 아닌 다른 언어를 선택 하려면 해당 언어에 대 한 적절 한 템플릿 폴더가 이미 설치 되어 있어야 합니다.

  선택한 언어는 마법사의 [MFC 응용 프로그램 마법사 페이지, 문서 템플릿 문자열](../../mfc/reference/document-template-strings-mfc-application-wizard.md) 의 **지역화 된 문자열** 옵션에 반영 됩니다.

- **유니코드 라이브러리 사용**

  MFC 라이브러리의 유니코드 또는 유니코드가 아닌 버전을 사용할지 여부를 지정 합니다.

- **프로젝트 스타일**

  응용 프로그램에 표준 MFC, 파일 탐색기, Visual Studio 또는 Office 아키텍처와 표시가 있는지 여부를 나타냅니다. 자세한 내용은 [MFC 응용 프로그램 Explorer-Style 파일 만들기](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)를 참조 하세요.

  |옵션|설명|
  |------------|-----------------|
  |**MFC 표준**|표준 MFC 응용 프로그램 아키텍처를 제공 합니다.|
  |**파일 탐색기**|왼쪽 창이 [Ctreeview 클래스](../../mfc/reference/ctreeview-class.md) 이 고 오른쪽 창이 [CListView 클래스인](../../mfc/reference/clistview-class.md)분할자 창을 사용 하 여 파일 탐색기와 같은 응용 프로그램을 구현 합니다.|
  |**Visual Studio**|[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md) 에서 파생 되는 네 개의 도킹 가능한 창 (**파일 뷰**, **클래스 뷰**, **속성** 및 **출력**)이 포함 된 Visual Studio와 유사한 응용 프로그램을 구현 합니다 .이 응용 프로그램은 [CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md) 에서 파생 되는 주 프레임 창 (기본값)입니다.|
  |**Office**|[CmfcCMFCOutlookBar Bar 클래스](../../mfc/reference/cmfcribbonbar-class.md)에서 파생 된 리본, [클래스](../../mfc/reference/cmfcoutlookbar-class.md)에서 파생 된 Outlook 표시줄, [cmfccaptionbar 클래스](../../mfc/reference/cmfccaptionbar-class.md)에서 파생 된 캡션 표시줄 및 [CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md)에서 파생 된 주 프레임을 포함 하는 Office와 유사한 응용 프로그램을 구현 합니다.|

- **비주얼 스타일 및 색**

  응용 프로그램의 비주얼 스타일을 결정 합니다. 다음 옵션을 사용할 수 있습니다.

  - **Windows 네이티브/기본값**

  - **Office 2003**

  - **Visual Studio 2005**

  - **Office 2007 (파란색 테마)**

  - **Office 2007 (검정 테마)**

  - **Office 2007 (실버 테마)**

  - **Office 2007 (바다색 테마)**

- **비주얼 스타일 전환 사용**

  사용자가 일반적으로 메뉴 또는 리본에서 적절 한 비주얼 스타일을 선택 하 여 런타임에 응용 프로그램의 비주얼 스타일을 변경할 수 있는지 여부를 지정 합니다.

- **MFC 사용**

  MFC 라이브러리에 연결 하는 방법을 지정 합니다. 기본적으로 MFC는 공유 DLL로 연결 됩니다.

  |옵션|설명|
  |------------|-----------------|
  |**공유 DLL에서 MFC 사용**|MFC 라이브러리를 공유 DLL로 응용 프로그램에 연결 합니다. 응용 프로그램은 런타임에 MFC 라이브러리를 호출 합니다. 이 옵션을 사용 하면 MFC 라이브러리를 사용 하는 여러 실행 파일로 구성 된 응용 프로그램의 디스크 및 메모리 요구 사항을 줄일 수 있습니다. Win32 및 MFC 응용 프로그램 모두 DLL에서 함수를 호출할 수 있습니다 (기본값).|
  |**정적 라이브러리에서 MFC 사용**|빌드 시 응용 프로그램을 정적 MFC 라이브러리에 연결 합니다.|

## <a name="see-also"></a>참고 항목

[MFC 응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md)<br/>
[Visual Studio C++ 프로젝트용으로 만든 파일 형식](../../build/reference/file-types-created-for-visual-cpp-projects.md)
