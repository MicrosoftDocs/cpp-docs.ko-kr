---
description: '자세한 정보: MFC 프로그램 또는 컨트롤 소스 및 헤더 파일'
title: MFC 프로그램 또는 컨트롤 소스 및 헤더 파일
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
ms.openlocfilehash: dfe20b2e458db72a14c9ccc78df6f481442b72b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137854"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC 프로그램 또는 컨트롤 소스 및 헤더 파일

Visual Studio에서 MFC 프로젝트를 만들 때, 생성하는 프로젝트에 대해 선택한 옵션에 따라 다음 파일이 생성됩니다. 예를 들어 사용자 프로젝트는 대화 상자 기반 프로젝트 또는 클래스를 만드는 경우에만 *Projname* dlg.cpp 및 *Projname* dlg.h 파일을 포함합니다.

이러한 파일은 모두 *Projname* 디렉터리와 솔루션 탐색기의 헤더 파일(.h 파일) 폴더 또는 원본 파일(.cpp 파일) 폴더에 있습니다.

|파일 이름|Description|
|---------------|-----------------|
|*Projname*.h|프로그램 또는 DLL에 대한 주 포함 파일입니다. 다른 헤더 파일에 대한 `#include` 지시문 및 모든 전역 기호를 포함합니다. `CWinApp`에서 `CPrjnameApp` 클래스를 파생시키고 `InitInstance` 멤버 함수를 선언합니다. 컨트롤의 경우 `CPrjnameApp` 클래스는 `COleControlModule`에서 파생됩니다.|
|*Projname*.cpp|주 프로그램 소스 파일입니다. `CWinApp`에서 파생된 `CPrjnameApp` 클래스의 한 개체를 만들고 `InitInstance` 멤버 함수를 재정의합니다.<br /><br /> 실행 파일의 경우 `CPrjnameApp::InitInstance`은 여러 작업을 수행합니다. 문서 및 뷰 간의 연결 역할을 하는 문서 템플릿을 등록하고, 주 프레임 창을 만들고, 빈 문서를 만듭니다(또는 애플리케이션에 명령줄 인수로 지정된 경우 문서를 엽니다).<br /><br /> DLL 및 ActiveX(이전의 OLE) 컨트롤의 경우 `CProjNameApp::InitInstance`은 `COleObjectFactory::RegisterAll`를 호출하여 OLE에 컨트롤의 개체 팩터리를 등록하고 `AfxOLEInit`을 호출합니다. 또한 멤버 함수 `CProjNameApp::ExitInstance`은 **AfxOleTerm** 를 호출하여 메모리에서 컨트롤을 언로드하는 데 사용됩니다.<br /><br /> 또한 이 파일은 `DllRegisterServer` 및 `DllUnregisterServer` 함수를 구현하여 Windows 등록 데이터베이스에 컨트롤을 등록하고 등록 취소합니다.|
|*Projname* ctrl.h, *Projname* ctrl.cpp|`CProjnameCtrl` 클래스를 구현하고 선언합니다. `CProjnameCtrl`은 `COleControl`에서 파생되며, 컨트롤을 초기화하고 그리며 직렬화(로드 및 저장)하는 일부 멤버 함수의 기본 구현을 정의합니다. 메시지, 이벤트 및 디스패치 맵을 정의합니다.|
|*Projname* dlg.cpp, *Projname* dlg.h|대화 상자 기반 애플리케이션을 선택한 경우 생성했습니다. 해당 파일은 `CProjnameDlg`이라는 대화 상자 클래스를 파생시키고 구현하며, 대화 상자를 초기화하고 대화 상자 데이터 교환(DDX)를 수행하는 기본 멤버 함수를 포함합니다. 대화 상자 클래스 정보는 *Projname*.cpp 대신 이러한 파일에도 배치됩니다.|
|Dlgproxy.cpp, Dlgproxy.h|대화 상자 기반 프로그램에서 기본 대화 상자용 프로젝트의 Automation 프록시 클래스에 대한 구현 및 헤더 파일입니다. 이는 Automation 지원을 선택한 경우에만 사용됩니다.|
|*Projname* doc.cpp, *Projname* doc.h|`CProjnameDoc`이라는 문서 클래스를 파생시키고 구현하며, 문서를 초기화하고 직렬화(저장 및 로드)하고 디버깅 진단을 구현하는 기본 멤버 함수를 포함합니다.|
|*Projname* set.h/.cpp|데이터베이스를 지원하고 레코드 집합 클래스를 포함하는 프로그램을 만드는 경우 만들었습니다.|
|*Projname* view.cpp, *Projname* view.h|문서 데이터를 표시하고 인쇄하는 데 사용되는 `CProjnameView`이라는 뷰 클래스를 파생시키고 구현합니다. `CProjnameView` 클래스는 다음 MFC 클래스 중 하나에서 파생됩니다.<br /><br />- [CEditView](../../mfc/reference/ceditview-class.md)<br />- [CFormView](../../mfc/reference/cformview-class.md)<br />- [CRecordView](../../mfc/reference/crecordview-class.md)<br />- [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)<br />- [CTreeView](../../mfc/reference/ctreeview-class.md)<br />- [CListView](../../mfc/reference/clistview-class.md)<br />- [CRichEditView](../../mfc/reference/cricheditview-class.md)<br />- [CScrollView](../../mfc/reference/cscrollview-class.md)<br />- [CView](../../mfc/reference/cview-class.md)<br />- [CHTMLView](../../mfc/reference/chtmlview-class.md)<br />- [CHTMLEditView](../../mfc/reference/chtmleditview-class.md)<br /><br /> 프로젝트의 뷰 클래스는 뷰를 그리고 디버깅 진단을 구현하는 기초 멤버 함수를 포함합니다. 인쇄에 대한 지원을 사용한 경우 메시지 맵 항목은 인쇄, 인쇄 설정 및 미리 보기 명령 메시지에 대해 추가됩니다. 이러한 항목은 기본 뷰 클래스에서 해당 멤버 함수를 호출합니다.|
|*Projname* PropPage.h, *Projname* PropPage.cpp|`CProjnamePropPage` 클래스를 구현하고 선언합니다. `CProjnamePropPage`은 `COlePropertyPage`에서 파생되고 기본 멤버 함수 `DoDataExchange`은 데이터 교환 및 유효성 검사를 구현하기 위해 제공됩니다.|
|IPframe.cpp, IPframe.h|애플리케이션 마법사의 **자동화 옵션** 페이지(3/6 단계)에서 미니 서버 또는 전체 서버 옵션을 선택하는 경우 만들었습니다. 해당 파일은 컨테이너 프로그램에서 서버를 내부에서 활성화할 때 사용된 **CInPlaceFrame** 이라는 내부 프레임 창 클래스를 파생시키고 구현합니다.|
|Mainfrm.cpp, Mainfrm.h|[CFrameWnd](../../mfc/reference/cframewnd-class.md)(SDI 애플리케이션용) 또는 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)(MDI 애플리케이션용)에서 **CMainFrame** 클래스를 파생시킵니다. 애플리케이션 마법사의 **애플리케이션 옵션** 페이지(4/6 단계)에서 해당 옵션을 선택한 경우 **CMainFrame** 클래스는 도구 모음 단추 및 상태 표시줄의 생성을 처리합니다. **CMainFrame** 사용에 대한 내용은 [애플리케이션 마법사로 만든 프레임 창 클래스](../../mfc/frame-window-classes-created-by-the-application-wizard.md)를 참조합니다.|
|Childfrm.cpp, Childfrm.h|**CChildFrame** 클래스를 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)에서 파생시킵니다. **CChildFrame** 클래스는 MDI 문서 프레임 창에 사용됩니다. 이러한 파일은 MDI 옵션을 선택하는 경우 항상 만들어집니다.|

## <a name="see-also"></a>참고 항목

[Visual Studio C++ 프로젝트용으로 만든 파일 형식](file-types-created-for-visual-cpp-projects.md)<br>
[ATL 프로그램 또는 컨트롤 소스 및 헤더 파일](atl-program-or-control-source-and-header-files.md)<br>
[CLR 프로젝트](files-created-for-clr-projects.md)
