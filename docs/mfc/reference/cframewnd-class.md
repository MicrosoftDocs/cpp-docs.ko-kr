---
description: '자세히 알아보기: CFrameWnd 클래스'
title: CFrameWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
ms.openlocfilehash: 85bad5ad63a07b58f245df06a44d82f58d6a561c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184285"
---
# <a name="cframewnd-class"></a>CFrameWnd 클래스

창 관리를 위한 멤버와 함께 겹쳐진 Windows SDI(단일 문서 인터페이스) 또는 팝업 프레임 창의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFrameWnd:: CFrameWnd](#cframewnd)|`CFrameWnd` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFrameWnd:: 고 프레임 프레임](#activateframe)|사용자가 프레임을 표시 하 고 사용할 수 있도록 합니다.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|프레임 창을 모달로 설정 합니다.|
|[CFrameWnd::Create](#create)|을 호출 하 여 개체와 연결 된 Windows 프레임 창을 만들고 초기화 합니다 `CFrameWnd` .|
|[CFrameWnd::CreateView](#createview)|에서 파생 되지 않은 프레임 안에 뷰를 만듭니다 `CView` .|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|컨트롤 막대를 도킹 합니다.|
|[CFrameWnd:: EnableDocking](#enabledocking)|컨트롤 막대를 도킹할 수 있습니다.|
|[CFrameWnd:: EndModalState](#endmodalstate)|프레임 창의 모달 상태를 종료 합니다. 에서 사용 하지 않도록 설정 된 모든 창을 사용 하도록 설정 `BeginModalState` 합니다.|
|[CFrameWnd:: FloatControlBar](#floatcontrolbar)|컨트롤 막대를 부동 합니다.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|활성 개체를 반환 합니다 `CDocument` .|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|활성 개체를 반환 합니다 `CFrameWnd` .|
|[CFrameWnd::GetActiveView](#getactiveview)|활성 개체를 반환 합니다 `CView` .|
|[CFrameWnd::GetControlBar](#getcontrolbar)|컨트롤 막대를 검색 합니다.|
|[CFrameWnd::GetDockState](#getdockstate)|프레임 창의 도크 상태를 검색 합니다.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|현재 MFC 응용 프로그램에서 메뉴의 표시 상태를 검색 합니다.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|현재 MFC 응용 프로그램에서 메뉴의 기본 동작이 숨겨지거나 표시 되는지 여부를 나타냅니다.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|프레임 창에 속하는 상태 표시줄에 대 한 포인터를 반환 합니다.|
|[CFrameWnd::GetMessageString](#getmessagestring)|명령 ID에 해당 하는 메시지를 검색 합니다.|
|[CFrameWnd::GetTitle](#gettitle)|관련 컨트롤 막대의 제목을 검색 합니다.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|`OnInitialUpdate`프레임 창의 모든 뷰에 속하는 멤버 함수를 호출 합니다.|
|[CFrameWnd::InModalState](#inmodalstate)|프레임 창이 모달 상태 인지 여부를 나타내는 값을 반환 합니다.|
|[CFrameWnd::IsTracking](#istracking)|분할자 막대가 현재 이동 되 고 있는지 여부를 확인 합니다.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|을 호출 하 여 액셀러레이터 키 테이블을 로드 합니다.|
|[CFrameWnd::LoadBarState](#loadbarstate)|을 호출 하 여 컨트롤 모음 설정을 복원 합니다.|
|[CFrameWnd::LoadFrame](#loadframe)|을 호출 하 여 리소스 정보에서 프레임 창을 동적으로 만듭니다.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|프레임 창에서 테두리 공간을 협상 합니다.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|지정 된 컨트롤 막대에 대해 동작이 수행 될 때마다 호출 됩니다.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|내부 항목에 대 한 SHIFT + F1 도움말을 처리 합니다.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|응용 프로그램의 주 프레임 창을 인쇄 미리 보기 모드에서 나 밖으로 설정 합니다.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|연결 된 메뉴가 업데이트 될 때 프레임 워크에서 호출 됩니다.|
|[CFrameWnd::RecalcLayout](#recalclayout)|개체의 컨트롤 막대 위치를 조정 `CFrameWnd` 합니다.|
|[CFrameWnd::SaveBarState](#savebarstate)|을 호출 하 여 컨트롤 막대 설정을 저장 합니다.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|지정 된 뷰를 Rich Preview의 활성 뷰로 지정 합니다.|
|[CFrameWnd::SetActiveView](#setactiveview)|활성 개체를 설정 `CView` 합니다.|
|[CFrameWnd::SetDockState](#setdockstate)|를 호출 하 여 주 창에서 프레임 창을 도킹 합니다.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|현재 MFC 응용 프로그램의 메뉴 표시 상태를 숨기 거 나 표시로 설정 합니다.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|현재 MFC 응용 프로그램의 메뉴 기본 동작을 숨기 거 나 표시할 수 있도록 설정 합니다.|
|[CFrameWnd::SetMessageText](#setmessagetext)|표준 상태 표시줄의 텍스트를 설정 합니다.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|작업 표시줄에 표시 되는 Windows 7 진행률 표시줄의 현재 위치를 설정 합니다.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|작업 표시줄에 표시 되는 Windows 7 진행률 표시줄의 범위를 설정 합니다.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|작업 표시줄 단추에 표시 되는 진행률 표시기의 유형 및 상태를 설정 합니다.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|오버로드됨. 작업 표시줄 단추에 오버레이를 적용 하 여 응용 프로그램 상태 또는 사용자에 게 알림을 표시 합니다.|
|[CFrameWnd::SetTitle](#settitle)|관련 컨트롤 막대의 제목을 설정 합니다.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|을 호출 하 여 컨트롤 막대를 표시 합니다.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|개체의 하위 항목인 모든 창을 표시 `CFrameWnd` 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|프레임에 대 한 클라이언트 창을 만듭니다.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|현재 MFC 응용 프로그램의 메뉴가 숨겨지기 전에 호출 됩니다.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|현재 MFC 응용 프로그램의 메뉴가 표시 되기 전에 호출 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|메뉴 항목에 대해 자동 사용 및 사용 안 함 기능을 제어 합니다.|
|[CFrameWnd::rectDefault](#rectdefault)|`CRect` `CFrameWnd` 창에서 창의 초기 크기와 위치를 선택할 수 있도록 개체를 만들 때이 정적를 매개 변수로 전달 합니다.|

## <a name="remarks"></a>설명

응용 프로그램에 대 한 유용한 프레임 창을 만들려면에서 클래스를 파생 시킵니다 `CFrameWnd` . 파생 클래스에 멤버 변수를 추가 하 여 응용 프로그램에 특정 한 데이터를 저장 합니다. 파생 클래스에서 메시지 처리기 멤버 함수 및 메시지 맵을 구현하여 메시지가 창에 전달될 때 수행되는 작업을 지정합니다.

다음 세 가지 방법으로 프레임 창을 생성할 수 있습니다.

- [Create](#create)를 사용 하 여 직접 생성 합니다.

- [Loadframe](#loadframe)을 사용 하 여 직접 구성 합니다.

- 문서 템플릿을 사용 하 여 간접적으로 구성 합니다.

또는를 호출 하기 `Create` 전에 `LoadFrame` c + + 연산자를 사용 하 여 힙에서 프레임 창 개체를 구성 해야 합니다 **`new`** . 를 호출 하기 전에 `Create` [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) global 함수를 사용 하 여 창 클래스를 등록 하 여 프레임에 대 한 아이콘 및 클래스 스타일을 설정할 수도 있습니다.

`Create`멤버 함수를 사용 하 여 프레임의 생성 매개 변수를 즉각적인 인수로 전달 합니다.

`LoadFrame` 는 보다 작은 인수 `Create` 를 사용 하며, 대신 프레임의 캡션, 아이콘, 액셀러레이터 키 테이블 및 메뉴를 포함 하 여 리소스에서 대부분의 기본값을 검색 합니다. 에서 액세스할 수 있도록 하려면 `LoadFrame` 이러한 모든 리소스의 리소스 ID가 같아야 합니다 (예: IDR_MAINFRAME).

개체는 `CFrameWnd` 뷰 및 문서를 포함 하는 경우 프로그래머가 직접 생성 하지 않고 프레임 워크에 의해 간접적으로 생성 됩니다. `CDocTemplate`개체는 프레임 생성, 포함 하는 뷰의 생성 및 해당 문서에 대 한 뷰 연결을 오케스트레이션 합니다. 생성자의 매개 변수는 `CDocTemplate` 관련 된 `CRuntimeClass` 세 가지 클래스 (문서, 프레임 및 뷰)의를 지정 합니다. `CRuntimeClass`개체는 사용자가 지정 하는 경우 (예: 새 파일 명령 또는 MDI (다중 문서 인터페이스) 창 새 명령 사용) 프레임 워크에서 동적으로 새 프레임을 만드는 데 사용 됩니다.

위의 RUNTIME_CLASS 메커니즘이 제대로 작동 하려면에서 파생 된 프레임 창 클래스를 `CFrameWnd` DECLARE_DYNCREATE으로 선언 해야 합니다.

에는 `CFrameWnd` Windows 용 일반적인 응용 프로그램에서 기본 창에 대해 다음과 같은 기능을 수행 하는 기본 구현이 포함 되어 있습니다.

- `CFrameWnd`프레임 창은 Windows 활성 창이 나 현재 입력 포커스와 무관 한 현재 활성 뷰를 추적 합니다. 프레임이 다시 활성화 되 면를 호출 하 여 활성 보기에 알림 메시지를 표시 합니다 `CView::OnActivateView` .

- 명령 메시지와의, 및 함수에 의해 처리 되는 메시지를 비롯 한 많은 일반적인 프레임 알림 메시지 `OnSetFocus` `OnHScroll` `OnVScroll` `CWnd` 는 `CFrameWnd` 프레임 창에서 현재 활성 뷰로 위임 됩니다.

- 현재 활성 뷰 (또는 MDI 프레임의 경우 현재 활성화 된 MDI 자식 프레임 창)는 프레임 창의 캡션을 결정할 수 있습니다. 프레임 창의 FWS_ADDTOTITLE 스타일 비트를 꺼서이 기능을 사용 하지 않도록 설정할 수 있습니다.

- `CFrameWnd`프레임 창은 프레임 창의 클라이언트 영역 내에서 컨트롤 막대, 뷰 및 기타 자식 창의 위치를 관리 합니다. 프레임 창에는 도구 모음 및 기타 컨트롤 막대 단추의 유휴 시간 업데이트도 수행 됩니다. `CFrameWnd`또한 프레임 창에는 도구 모음 및 상태 표시줄을 설정/해제 하는 명령에 대 한 기본 구현이 있습니다.

- `CFrameWnd`프레임 창은 주 메뉴 모음을 관리 합니다. 팝업 메뉴가 표시 되 면 프레임 창에서 UPDATE_COMMAND_UI 메커니즘을 사용 하 여 사용, 사용 안 함 또는 선택 해야 하는 메뉴 항목을 결정 합니다. 사용자가 메뉴 항목을 선택 하면 프레임 창에서 해당 명령에 대 한 메시지 문자열을 사용 하 여 상태 표시줄을 업데이트 합니다.

- `CFrameWnd`프레임 창에는 자동으로 키보드 액셀러레이터를 변환 하는 선택적 액셀러레이터 테이블이 있습니다.

- 프레임 창에는 상황에 맞는 `CFrameWnd` 도움말에 사용 되는 선택적 도움말 ID가로 설정 되어 있습니다 `LoadFrame` . 프레임 창은 상황에 맞는 도움말 (SHIFT + F1) 및 인쇄 미리 보기 모드와 같은 semimodal 상태의 기본 조정자입니다.

- `CFrameWnd`프레임 창이 파일 관리자에서 끌어온 파일을 열고 프레임 창에 끌어 놓으면 됩니다. 파일 확장명이 등록 되 고 응용 프로그램에 연결 된 경우 프레임 창은 사용자가 파일 관리자에서 데이터 파일을 열거나 Windows 함수를 호출할 때 발생 하는 DDE (동적 데이터 교환) 열기 요청에 응답 합니다 `ShellExecute` .

- 프레임 창이 주 응용 프로그램 창 (즉,) 인 경우 `CWinThread::m_pMainWnd` 사용자가 응용 프로그램을 닫으면 프레임 창에 사용자에 게 수정 된 문서를 저장 하 라는 메시지가 표시 됩니다 ( `OnClose` 및의 경우 `OnQueryEndSession` ).

- 프레임 창이 주 응용 프로그램 창인 경우 프레임 창은 WinHelp를 실행 하기 위한 컨텍스트입니다. 프레임 창을 닫으면이 응용 프로그램에 대 한 도움말을 위해 시작 된 WINHELP.EXE 종료 됩니다.

C + + 연산자를 사용 **`delete`** 하 여 프레임 창을 제거 하지 마십시오. 대신 `CWnd::DestroyWindow`를 사용하세요. `CFrameWnd`의 구현은 `PostNcDestroy` 창이 소멸 될 때 c + + 개체를 삭제 합니다. 사용자가 프레임 창을 닫으면 기본 `OnClose` 처리기가를 호출 `DestroyWindow` 합니다.

에 대 한 자세한 내용은 `CFrameWnd` [프레임 창](../../mfc/frame-windows.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a> CFrameWnd:: 고 프레임 프레임

사용자가 표시 하 고 사용할 수 있도록이 멤버 함수를 호출 하 여 프레임 창을 활성화 하 고 복원 합니다.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>매개 변수

*nCmdShow*<br/>
[CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)에 전달할 매개 변수를 지정 합니다. 기본적으로 프레임이 표시 되 고 올바르게 복원 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 일반적으로 사용자에 게 프레임 창이 나 해당 콘텐츠를 표시할 수 있는 사용자 인터페이스 이벤트 (예: DDE, OLE 또는 기타 이벤트)가 발생 한 후에 호출 됩니다.

기본 구현에서는 프레임을 활성화 하 고 Z 순서의 맨 위에 표시 하 고 필요한 경우 응용 프로그램의 주 프레임 창에 대해 동일한 단계를 수행 합니다.

프레임이 활성화 되는 방법을 변경 하려면이 멤버 함수를 재정의 합니다. 예를 들어 MDI 자식 창이 최대화 되도록 강제할 수 있습니다. 적절 한 기능을 추가한 다음 명시적인 *Ncmdshow* 를 사용 하 여 기본 클래스 버전을 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a> CFrameWnd:: BeginModalState

프레임 창을 모달로 만들기 위해 이 멤버 함수를 호출합니다.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a> CFrameWnd:: CFrameWnd

개체를 생성 `CFrameWnd` 하지만 표시 되는 프레임 창을 만들지는 않습니다.

```
CFrameWnd();
```

### <a name="remarks"></a>설명

`Create`을 호출 하 여 표시 되는 창을 만듭니다.

## <a name="cframewndcreate"></a><a name="create"></a> CFrameWnd:: Create

을 호출 하 여 개체와 연결 된 Windows 프레임 창을 만들고 초기화 합니다 `CFrameWnd` .

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CWnd* pParentWnd = NULL,
    LPCTSTR lpszMenuName = NULL,
    DWORD dwExStyle = 0,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
Windows 클래스의 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 클래스 이름은 `AfxRegisterWndClass` 전역 함수 또는 Windows 함수에 등록 된 모든 이름일 수 있습니다 `RegisterClass` . NULL 인 경우에는 미리 정의 된 기본 특성을 사용 `CFrameWnd` 합니다.

*lpszWindowName*<br/>
창 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 제목 표시줄의 텍스트로 사용 됩니다.

*dwStyle*<br/>
창 [스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 특성을 지정 합니다. 제목 표시줄에 창에 표시 되는 문서 이름이 자동으로 표시 되도록 하려면 FWS_ADDTOTITLE 스타일을 포함 합니다.

*rect*<br/>
창의 크기와 위치를 지정 합니다. *RectDefault* 값을 사용 하면 창에서 새 창의 크기와 위치를 지정할 수 있습니다.

*pParentWnd*<br/>
이 프레임 창의 부모 창을 지정 합니다. 이 매개 변수는 최상위 프레임 창의 경우 NULL 이어야 합니다.

*lpszMenuName*<br/>
창에 사용할 메뉴 리소스의 이름을 식별 합니다. 메뉴에 문자열 대신 정수 ID가 있는 경우 MAKEINTRESOURCE를 사용 합니다. 이 매개 변수는 NULL일 수 있습니다.

*dwExStyle*<br/>
창 확장 [스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) 특성을 지정 합니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 구조체에 대 한 포인터를 지정 합니다. 이 매개 변수는 NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CFrameWnd`두 단계로 개체를 생성 합니다. 먼저 개체를 생성 하는 생성자를 호출 `CFrameWnd` 하 고를 호출 하 여 `Create` Windows 프레임 창을 만들고 개체에 연결 `CFrameWnd` 합니다. `Create` 창의 클래스 이름과 창 이름을 초기화 하 고 해당 스타일, 부모 및 연결 된 메뉴에 대 한 기본값을 등록 합니다.

대신를 사용 `LoadFrame` `Create` 하 여 인수를 지정 하는 대신 리소스에서 프레임 창을 로드 합니다.

## <a name="cframewndcreateview"></a><a name="createview"></a> CFrameWnd:: CreateView

`CreateView`을 호출 하 여 프레임 내에서 뷰를 만듭니다.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
보기 및 문서의 유형을 지정 합니다.

*nID*<br/>
뷰의 ID 번호입니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CWnd` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 사용 하 여 프레임 내에서 파생 되지 않은 "뷰"를 만들 수 `CView` 있습니다. 를 호출한 후에 `CreateView` 는 보기를 활성으로 수동으로 설정 하 고 표시 되도록 설정 해야 합니다. 이러한 작업은에서 자동으로 수행 되지 않습니다 `CreateView` .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a> CFrameWnd::D ockControlBar

컨트롤 막대가 프레임 창에 도킹 되도록 합니다.

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
도킹할 컨트롤 막대를 가리킵니다.

*nDockBarID*<br/>
도킹에 대해 고려할 프레임 창의 면을 결정 합니다. 0 이거나 다음 중 하나 이상이 될 수 있습니다.

- 프레임 창의 위쪽에 도킹을 AFX_IDW_DOCKBAR_TOP 합니다.

- 프레임 창의 아래쪽에 도킹을 AFX_IDW_DOCKBAR_BOTTOM 합니다.

- 프레임 창의 왼쪽에 도킹을 AFX_IDW_DOCKBAR_LEFT 합니다.

- 프레임 창의 오른쪽에 도킹을 AFX_IDW_DOCKBAR_RIGHT 합니다.

0 인 경우에는 대상 프레임 창에서 도킹을 사용 하도록 설정 된 모든 쪽에 컨트롤 막대를 도킹할 수 있습니다.

*lpRect*<br/>
대상 프레임 창의 비클라이언트 영역에서 컨트롤 막대를 도킹할 화면 좌표를 결정 합니다.

### <a name="remarks"></a>설명

컨트롤 막대는 [Ccontrolbar:: enabledocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) 및 [CFrameWnd:: enabledocking](#enabledocking)에 대 한 호출에 지정 된 프레임 창의 측면 중 하나에 도킹 됩니다. 선택한 측면은 *nDockBarID* 에 의해 결정 됩니다.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a> CFrameWnd:: EnableDocking

프레임 창에서 도킹 가능한 컨트롤 막대를 사용 하도록 설정 하려면이 함수를 호출 합니다.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>매개 변수

*dwDockStyle*<br/>
컨트롤 막대의 도킹 사이트로 사용할 수 있는 프레임 창의 면을 지정 합니다. 다음 중 하나 이상이 될 수 있습니다.

- CBRS_ALIGN_TOP 클라이언트 영역의 맨 위에 도킹을 허용 합니다.

- 클라이언트 영역의 아래쪽에 도킹을 허용 CBRS_ALIGN_BOTTOM.

- CBRS_ALIGN_LEFT 클라이언트 영역의 왼쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_RIGHT 클라이언트 영역의 오른쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_ANY은 클라이언트 영역의 어느 쪽에 나 도킹할 수 있습니다.

### <a name="remarks"></a>설명

기본적으로 컨트롤 막대는 위쪽, 아래쪽, 왼쪽, 오른쪽 순서로 프레임 창의 옆쪽에 도킹 됩니다.

### <a name="example"></a>예제

  [CToolBar:: Create](../../mfc/reference/ctoolbar-class.md#create)의 예제를 참조 하세요.

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a> CFrameWnd:: EndModalState

프레임 창을 모달에서 모덜리스로 변경하려면 이 멤버 함수를 호출합니다.

```
virtual void EndModalState();
```

### <a name="remarks"></a>설명

`EndModalState`[Beginmodalstate](#beginmodalstate)에서 사용 하지 않도록 설정 된 모든 창을 사용 하도록 설정 합니다.

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a> CFrameWnd:: FloatControlBar

컨트롤 막대를 프레임 창에 도킹할 수 없게 하려면이 함수를 호출 합니다.

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
컨트롤 막대를 부동으로 가리킵니다.

*까지*<br/>
컨트롤 막대의 왼쪽 위 모퉁이가 배치 될 위치 (화면 좌표)입니다.

*dwStyle*<br/>
새 프레임 창에서 컨트롤 막대를 가로 또는 세로로 맞출지 여부를 지정 합니다. 다음 중 하나일 수 있습니다.

- 컨트롤 막대의 방향을 세로로 CBRS_ALIGN_TOP 합니다.

- 컨트롤 막대의 방향을 세로로 CBRS_ALIGN_BOTTOM 합니다.

- 컨트롤 막대의 가로 방향을 CBRS_ALIGN_LEFT 합니다.

- 컨트롤 막대의 가로 방향을 CBRS_ALIGN_RIGHT 합니다.

가로 및 세로 방향 모두를 지정 하 여 스타일을 전달 하는 경우 도구 모음의 가로 방향이 지정 됩니다.

### <a name="remarks"></a>설명

일반적으로이 작업은 프로그램이 이전 실행에서 설정을 복원할 때 응용 프로그램 시작 시 수행 됩니다.

이 함수는 도킹에 사용할 수 없는 위치에서 컨트롤 막대를 끌 때 왼쪽 마우스 단추를 놓으면 프레임 워크에서 호출 됩니다.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a> CFrameWnd:: GetActiveDocument

현재 활성 뷰에 연결 된 현재에 대 한 포인터를 가져오려면이 멤버 함수를 호출 `CDocument` 합니다.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>반환 값

현재 [CDocument](../../mfc/reference/cdocument-class.md)에 대 한 포인터입니다. 현재 문서가 없으면 NULL을 반환 합니다.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a> CFrameWnd:: GetActiveFrame

MDI 프레임 창의 활성 MDI (다중 문서 인터페이스) 자식 창에 대 한 포인터를 가져오려면이 멤버 함수를 호출 합니다.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>반환 값

활성 MDI 자식 창에 대 한 포인터입니다. 응용 프로그램이 SDI 응용 프로그램 이거나 MDI 프레임 창에 활성 문서가 없으면 암시적 **`this`** 포인터가 반환 됩니다.

### <a name="remarks"></a>설명

활성 MDI 자식이 없거나 응용 프로그램이 SDI (단일 문서 인터페이스) 이면 암시적 **`this`** 포인터가 반환 됩니다.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a> CFrameWnd:: GetActiveView

이 멤버 함수를 호출 하 여 프레임 창에 연결 된 활성 뷰 (있는 경우)에 대 한 포인터를 가져옵니다 `CFrameWnd` .

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>반환 값

현재 [CView](../../mfc/reference/cview-class.md)에 대 한 포인터입니다. 현재 보기가 없으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

이 함수는 MDI 주 프레임 창 ()에 대해 호출 될 때 NULL을 반환 `CMDIFrameWnd` 합니다. MDI 응용 프로그램에서 MDI 주 프레임 창에는 연결 된 뷰가 없습니다. 대신 각 개별 자식 창 ( `CMDIChildWnd` )에는 하나 이상의 관련 보기가 있습니다. MDI 응용 프로그램의 활성 뷰는 먼저 활성 MDI 자식 창을 찾은 다음 해당 자식 창에 대 한 활성 뷰를 찾는 방법으로 가져올 수 있습니다. 활성 MDI 자식 창은 함수를 호출 `MDIGetActive` 하거나 `GetActiveFrame` 다음에서 보여 주는 것 처럼 찾을 수 있습니다.

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a> CFrameWnd:: GetControlBar

`GetControlBar`를 호출 하 여 ID와 연결 된 컨트롤 막대에 대 한 액세스 권한을 얻습니다.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
컨트롤 막대의 ID 번호입니다.

### <a name="return-value"></a>반환 값

ID와 연결 된 컨트롤 막대에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*NID* 매개 변수는 `Create` 컨트롤 막대의 메서드에 전달 되는 고유 식별자를 참조 합니다. 컨트롤 막대에 대 한 자세한 내용은 [컨트롤 막대](../../mfc/control-bars.md)에 대 한 항목을 참조 하세요.

`GetControlBar` 는 부동 이더라도 현재 프레임의 자식 창이 아닌 컨트롤 막대를 반환 합니다.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a> CFrameWnd:: GetDockState

이 멤버 함수를 호출 하 여 개체의 프레임 창 컨트롤 막대에 대 한 상태 정보를 저장 `CDockState` 합니다.

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>매개 변수

*state*<br/>
반환 될 때 프레임 창에 있는 컨트롤 막대의 현재 상태를 포함 합니다.

### <a name="remarks"></a>설명

그런 다음 또는을 사용 하 여의 콘텐츠를 저장소에 쓸 수 있습니다 `CDockState` `CDockState::SaveState` `Serialize` . 나중에 컨트롤 막대를 이전 상태로 복원 하려면 또는를 사용 하 여 상태를 로드 `CDockState::LoadState` `Serialize` 한 다음 `SetDockState` 를 호출 하 여 이전 상태를 프레임 창의 컨트롤 막대에 적용 합니다.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a> CFrameWnd:: Getmenu 상태

현재 MFC 응용 프로그램에서 메뉴의 표시 상태를 검색 합니다.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>반환 값

반환 값은 다음 값을 가질 수 있습니다.

- AFX_MBS_VISIBLE (0x01)-메뉴가 표시 됩니다.

- AFX_MBS_HIDDEN (0x02)-메뉴가 숨겨집니다.

### <a name="remarks"></a>설명

런타임 오류가 발생 하는 경우이 메서드는 디버그 모드에서 어설션 하 고 [Cexception](../../mfc/reference/cexception-class.md) 클래스에서 파생 된 예외를 발생 시킵니다.

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a> CFrameWnd:: Getmenu바 표시 유형

현재 MFC 응용 프로그램에서 메뉴의 기본 상태가 숨겨지거나 표시 되는지 여부를 나타냅니다.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>반환 값

이 메서드는 다음 값 중 하나를 반환합니다.

- AFX_MBV_KEEPVISIBLE (0x01)-메뉴가 항상 표시 되며 기본적으로 포커스가 포함 되지 않습니다.

- AFX_MBV_DISPLAYONFOCUS (0x02)-메뉴는 기본적으로 숨겨져 있습니다. 메뉴가 숨겨진 경우 ALT 키를 눌러 메뉴를 표시 하 고 포커스를 제공 합니다. 메뉴가 표시 되 면 ALT 또는 ESC 키를 눌러 숨깁니다.

- DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 () (0x04) (비트 조합 (또는))-메뉴는 기본적으로 숨겨져 있습니다. AFX_MBV_ 메뉴가 숨겨진 경우 F10 키를 눌러 메뉴를 표시 하 고 포커스를 제공 합니다. 메뉴가 표시 되 면 F10 키를 눌러 메뉴에 포커스를 설정 하거나 해제 합니다. ALT 또는 ESC 키를 눌러 숨길 때까지 메뉴가 표시 됩니다.

### <a name="remarks"></a>설명

런타임 오류가 발생 하는 경우이 메서드는 디버그 모드에서 어설션 하 고 [Cexception](../../mfc/reference/cexception-class.md) 클래스에서 파생 된 예외를 발생 시킵니다.

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a> CFrameWnd:: GetMessageBar

이 멤버 함수를 호출 하 여 상태 표시줄에 대 한 포인터를 가져옵니다.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>반환 값

상태 표시줄 창에 대 한 포인터입니다.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a> CFrameWnd:: GetMessageString

이 함수를 재정의 하 여 명령 Id에 사용자 지정 문자열을 제공 합니다.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
원하는 메시지의 리소스 ID입니다.

*rMessage*<br/>
`CString` 메시지를 저장할 개체입니다.

### <a name="remarks"></a>설명

기본 구현에서는 *nID* 에서 지정 된 문자열을 리소스 파일에서 로드 합니다. 이 함수는 상태 표시줄의 메시지 문자열을 업데이트 해야 할 때 프레임 워크에서 호출 됩니다.

## <a name="cframewndgettitle"></a><a name="gettitle"></a> CFrameWnd:: GetTitle

창 개체의 제목을 검색 합니다.

```
CString GetTitle() const;
```

### <a name="return-value"></a>반환 값

창 개체의 현재 제목을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a> CFrameWnd:: InitialUpdateFrame

`IntitialUpdateFrame`를 사용 하 여 새 프레임을 만든 후를 호출 `Create` 합니다.

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
프레임 창이 연결 된 문서를 가리킵니다. NULL일 수 있습니다.

*bMakeVisible*<br/>
TRUE 이면 프레임이 표시 되 고 활성 상태가 되어야 함을 나타냅니다. FALSE 이면 하위 항목이 표시 되지 않습니다.

### <a name="remarks"></a>설명

이렇게 하면 해당 프레임 창의 모든 뷰가 해당 호출을 수신 `OnInitialUpdate` 합니다.

또한 이전에 활성 뷰가 없는 경우에는 프레임 창의 기본 뷰가 활성화 됩니다. 기본 뷰는 AFX_IDW_PANE_FIRST의 자식 ID를 사용 하는 뷰입니다. 마지막으로, *Bmakevisible* 이 0이 아닌 경우 프레임 창이 표시 됩니다. *Bmakevisible* 이 0 이면 프레임 창의 현재 포커스와 표시 상태는 변경 되지 않고 그대로 유지 됩니다. 새 파일 및 파일 열기의 프레임 워크 구현을 사용 하는 경우에는이 함수를 호출할 필요가 없습니다.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a> CFrameWnd:: InModalState

프레임 창이 모달 또는 모덜리스 인지 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>반환 값

예 이면 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cframewndistracking"></a><a name="istracking"></a> CFrameWnd:: IsTracking

이 멤버 함수를 호출 하 여 창의 분할자 막대가 현재 이동 중인지 여부를 확인 합니다.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>반환 값

분할자 작업이 진행 중인 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a> CFrameWnd:: LoadAccelTable

을 호출 하 여 지정한 액셀러레이터 키 테이블을 로드 합니다.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
액셀러레이터 키 리소스의 이름을 식별 합니다. 리소스가 정수 ID로 식별 되는 경우 MAKEINTRESOURCE를 사용 합니다.

### <a name="return-value"></a>반환 값

액셀러레이터 키 테이블이 성공적으로 로드 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

한 번에 하나의 테이블만 로드할 수 있습니다.

리소스에서 로드 되는 액셀러레이터 테이블은 응용 프로그램이 종료 될 때 자동으로 해제 됩니다.

`LoadFrame`를 호출 하 여 프레임 창을 만들 경우 프레임 워크는 메뉴 및 아이콘 리소스와 함께 액셀러레이터 키 테이블을 로드 하 고이 멤버 함수에 대 한 후속 호출을 필요 하지 않습니다.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a> CFrameWnd:: Load 상태

이 함수를 호출 하 여 프레임 창이 소유한 각 컨트롤 표시줄의 설정을 복원 합니다.

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
초기화 (INI) 파일의 섹션 이름 또는 상태 정보가 저장 되는 Windows 레지스트리의 키입니다.

### <a name="remarks"></a>설명

복원 된 정보에는 표시 유형, 가로/세로 방향, 도킹 상태 및 컨트롤 막대 위치가 포함 됩니다.

복원 하려는 설정은를 호출 하기 전에 레지스트리에 써야 합니다 `LoadBarState` . [CWinApp:: SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)를 호출 하 여 레지스트리에 정보를 씁니다. [Save바코드 상태](#savebarstate)를 호출 하 여 INI 파일에 정보를 씁니다.

## <a name="cframewndloadframe"></a><a name="loadframe"></a> CFrameWnd:: LoadFrame

을 호출 하 여 리소스 정보에서 프레임 창을 동적으로 만듭니다.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*nIDResource*<br/>
프레임 창과 연결 된 공유 리소스의 ID입니다.

*dwDefaultStyle*<br/>
프레임의 [스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)입니다. 제목 표시줄에 창에 표시 되는 문서 이름이 자동으로 표시 되도록 하려면 FWS_ADDTOTITLE 스타일을 포함 합니다.

*pParentWnd*<br/>
프레임의 부모에 대 한 포인터입니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 구조체에 대 한 포인터입니다. 이 매개 변수는 NULL일 수 있습니다.

### <a name="remarks"></a>설명

`CFrameWnd`두 단계로 개체를 생성 합니다. 먼저, 개체를 생성 하는 생성자를 호출 `CFrameWnd` 하 고 `LoadFrame` Windows 프레임 창과 연결 된 리소스를 로드 하 고 프레임 창을 개체에 연결 하는을 호출 합니다 `CFrameWnd` . *NIDResource* 매개 변수는 메뉴, 액셀러레이터 키 테이블, 아이콘 및 프레임 창의 제목에 대 한 문자열 리소스를 지정 합니다.

`Create` `LoadFrame` 모든 프레임 창의 생성 매개 변수를 지정 하려는 경우 대신 멤버 함수를 사용 합니다.

프레임 워크는 `LoadFrame` 문서 템플릿 개체를 사용 하 여 프레임 창을 만들 때를 호출 합니다.

프레임 워크는 *pContext* 인수를 사용 하 여 포함 된 뷰 개체를 포함 하 여 프레임 창에 연결할 개체를 지정 합니다. 를 호출할 때 *pContext* 인수를 NULL로 설정할 수 있습니다 `LoadFrame` .

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a> CFrameWnd:: m_bAutoMenuEnable

이 데이터 멤버를 사용 하는 경우 (기본값) 사용자가 메뉴를 아래로 이동 하면 ON_UPDATE_COMMAND_UI 또는 ON_COMMAND 처리기가 없는 메뉴 항목이 자동으로 비활성화 됩니다.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>설명

ON_COMMAND 처리기가 있지만 ON_UPDATE_COMMAND_UI 처리기가 없는 메뉴 항목은 자동으로 사용 하도록 설정 됩니다.

이 데이터 멤버가 설정 되 면 도구 모음 단추를 사용 하는 것과 같은 방식으로 메뉴 항목이 자동으로 활성화 됩니다.

> [!NOTE]
> `m_bAutoMenuEnable` 최상위 메뉴 항목에는 영향을 주지 않습니다.

이 데이터 멤버는 현재 선택 항목에 따라 선택적 명령의 구현을 간소화 하 고 메뉴 항목을 사용 하거나 사용 하지 않도록 설정 하는 ON_UPDATE_COMMAND_UI 처리기를 작성 해야 하는 필요성을 줄입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a> CFrameWnd:: NegotiateBorderSpace

OLE 내부 활성화 중에 프레임 창에서 테두리 공간을 협상 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>매개 변수

*nBorderCmd*<br/>
에서 다음 값 중 하나를 포함 합니다 `enum BorderCmd` .

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
테두리의 좌표를 지정 하는, [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `CFrameWnd` OLE 테두리 공간 협상의 구현입니다.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a> CFrameWnd:: OnBarCheck

지정 된 컨트롤 막대에 대해 동작이 수행 될 때마다 호출 됩니다.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
표시 되는 컨트롤 막대의 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤 막대가 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a> CFrameWnd:: OnContextHelp

내부 항목에 대 한 SHIFT + F1 도움말을 처리 합니다.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>설명

상황에 맞는 도움말을 사용 하려면 다음을 추가 해야 합니다.

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

문을 `CFrameWnd` 클래스 메시지 맵에 추가 하 고이 멤버 함수를 사용 하기 위해 액셀러레이터-테이블 항목 (일반적으로 SHIFT + F1)도 추가 합니다.

응용 프로그램이 OLE 컨테이너인 경우 `OnContextHelp` 프레임 창 개체 내에 포함 된 모든 내부 항목을 도움말 모드로 전환 합니다. 커서가 화살표와 물음표로 바뀌고 사용자는 마우스 포인터를 이동 하 고 마우스 왼쪽 단추를 눌러 대화 상자, 창, 메뉴 또는 명령 단추를 선택할 수 있습니다. 이 멤버 함수는 `WinHelp` 커서 아래에 있는 개체의 도움말 컨텍스트를 사용 하 여 Windows 함수를 호출 합니다.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a> CFrameWnd:: OnCreateClient

을 실행 하는 동안 프레임 워크에서 호출 `OnCreate` 됩니다.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>매개 변수

*lpcs*<br/>
Windows [Createstruct](/windows/win32/api/winuser/ns-winuser-createstructw) 구조체에 대 한 포인터입니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하지 마세요.

이 함수의 기본 구현은 `CView` 가능 하면 *pContext* 에 제공 된 정보에서 개체를 만듭니다.

이 함수를 재정의 하 여 개체에 전달 된 값을 재정의 `CCreateContext` 하거나 프레임 창의 주 클라이언트 영역에 있는 컨트롤이 만들어지는 방식을 변경 합니다. 재정의할 수 있는 `CCreateContext`멤버는 [ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 클래스에서 설명합니다.

> [!NOTE]
> 구조에 전달 된 값을 바꾸지 마십시오 `CREATESTRUCT` . 참조용 으로만 사용 됩니다. 예를 들어 초기 창 사각형을 재정의 하려면 `CWnd` [precreatewindow](../../mfc/reference/cwnd-class.md#precreatewindow)멤버 함수를 재정의 합니다.

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a> CFrameWnd:: OnHideMenuBar

이 함수는 시스템에서 현재 MFC 응용 프로그램의 메뉴 모음을 숨기려는 경우 호출 됩니다.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>설명

이 이벤트 처리기를 사용 하면 시스템에서 메뉴를 숨기려는 경우 응용 프로그램에서 사용자 지정 작업을 수행할 수 있습니다. 메뉴가 숨겨지지 않도록 할 수 있지만 예를 들어 다른 메서드를 호출 하 여 메뉴 스타일이 나 상태를 검색할 수 있습니다.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a> CFrameWnd:: OnSetPreviewMode

애플리케이션의 주 프레임 창을 인쇄 미리 보기 모드 내부 및 외부로 설정하려면 이 멤버 함수를 호출합니다.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>매개 변수

*bPreview*<br/>
응용 프로그램을 인쇄 미리 보기 모드로 배치할지 여부를 지정 합니다. 인쇄 미리 보기에 넣으려면 TRUE로 설정 하 고, 미리 보기 모드를 취소 하려면 FALSE로 설정 합니다.

*pState*<br/>
구조체에 대 한 포인터 `CPrintPreviewState` 입니다.

### <a name="remarks"></a>설명

기본 구현에서는 모든 표준 도구 모음을 사용 하지 않도록 설정 하 고 주 메뉴와 주 클라이언트 창을 숨깁니다. 그러면 MDI 프레임 창이 임시 SDI 프레임 창으로 전환 됩니다.

인쇄 미리 보기 중에 컨트롤 막대와 다른 프레임 창 부분을 숨기고 표시 하는 작업을 사용자 지정 하려면이 멤버 함수를 재정의 합니다. 재정의 된 버전 내에서 기본 클래스 구현을 호출 합니다.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a> CFrameWnd:: OnShowMenuBar

이 함수는 시스템에서 현재 MFC 응용 프로그램의 메뉴 모음을 표시 하려고 할 때 호출 됩니다.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>설명

이 이벤트 처리기를 사용 하면 메뉴가 표시 될 때 응용 프로그램에서 사용자 지정 작업을 수행할 수 있습니다. 메뉴가 표시 되지 않도록 할 수 있지만 예를 들어 다른 메서드를 호출 하 여 메뉴 스타일이 나 상태를 검색할 수 있습니다.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a> CFrameWnd:: OnUpdateControlBarMenu

연결 된 메뉴가 업데이트 될 때 프레임 워크에서 호출 됩니다.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>매개 변수

*pCmdUI*<br/>
업데이트 명령을 생성 한 메뉴를 나타내는 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터입니다. 업데이트 처리기는 *pCmdUI* 을 통해 `CCmdUI`개체의 [Enable](../../mfc/reference/ccmdui-class.md#enable) member 함수를 호출하여 사용자 인터페이스를 업데이트합니다.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a> CFrameWnd:: RecalcLayout

표준 컨트롤 막대가 설정/해제 되거나 프레임 창의 크기가 조정 될 때 프레임 워크에서 호출 됩니다.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>매개 변수

*bNotify*<br/>
프레임 창의 활성 내부 항목에 레이아웃 변경 알림이 수신 되는지 여부를 결정 합니다. TRUE 이면 항목에 알림이 표시 됩니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 멤버 함수의 기본 구현에서는 `CWnd` 멤버 함수를 호출 `RepositionBars` 하 여 프레임 및 주 클라이언트 창 (일반적으로 또는 MDICLIENT)에 있는 모든 컨트롤 막대의 위치를 변경 `CView` 합니다.

프레임 창의 레이아웃이 변경 된 후에 컨트롤 막대의 모양과 동작을 제어 하려면이 멤버 함수를 재정의 합니다. 예를 들어, 컨트롤 막대를 설정 하거나 해제 하거나 다른 컨트롤 막대를 추가 하는 경우 호출 합니다.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a> CFrameWnd:: rectDefault

창에서 `CRect` 창의 초기 크기와 위치를 선택할 수 있도록 창을 만들 때이 정적를 매개 변수로 전달 합니다.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a> CFrameWnd:: Save 상태

이 함수를 호출 하 여 프레임 창이 소유한 각 컨트롤 막대에 대 한 정보를 저장 합니다.

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
초기화 파일의 섹션 이름 또는 상태 정보가 저장 되는 Windows 레지스트리의 키입니다.

### <a name="remarks"></a>설명

이 정보는 [Load 상태](#loadbarstate)를 사용 하 여 초기화 파일에서 읽을 수 있습니다. 저장 된 정보에는 표시 유형, 가로/세로 방향, 도킹 상태 및 컨트롤 막대 위치가 포함 됩니다.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a> CFrameWnd:: SetActivePreviewView

지정 된 뷰를 Rich Preview의 활성 뷰로 지정 합니다.

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>매개 변수

*pViewNew*<br/>
활성화할 뷰에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a> CFrameWnd:: SetActiveView

활성 뷰를 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>매개 변수

*pViewNew*<br/>
[CView](../../mfc/reference/cview-class.md) 개체에 대 한 포인터를 지정 하거나 활성 뷰가 없는 경우 NULL을 지정 합니다.

*bNotify*<br/>
뷰에 활성화를 알릴지 여부를 지정 합니다. TRUE 이면 `OnActivateView` 새 뷰에 대해이 호출 되 고, FALSE 이면가 호출 되지 않습니다.

### <a name="remarks"></a>설명

프레임 워크는 사용자가 프레임 창 내의 뷰로 포커스를 변경할 때이 함수를 자동으로 호출 합니다. 를 명시적으로 호출 `SetActiveView` 하 여 포커스를 지정 된 뷰로 변경할 수 있습니다.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a> CFrameWnd:: SetDockState

개체에 저장 된 상태 정보를 `CDockState` 프레임 창의 컨트롤 막대에 적용 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>매개 변수

*state*<br/>
저장 된 상태를 프레임 창의 컨트롤 막대에 적용 합니다.

### <a name="remarks"></a>설명

컨트롤 막대의 이전 상태를 복원 하려면 또는를 사용 하 여 저장 된 상태를 `CDockState::LoadState` 로드 `Serialize` 한 다음 `SetDockState` 를 사용 하 여 프레임 창의 컨트롤 막대에 적용할 수 있습니다. 이전 상태는 `CDockState` 를 사용 하 여 개체에 저장 됩니다. `GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a> CFrameWnd:: Setmenu 상태

현재 MFC 응용 프로그램의 메뉴 표시 상태를 숨기 거 나 표시로 설정 합니다.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>매개 변수

*nState*\
진행 메뉴를 표시 하거나 숨길지 여부를 지정 합니다. *Nstate* 매개 변수는 다음 값을 가질 수 있습니다.

- `AFX_MBS_VISIBLE` (0x01)-메뉴가 숨겨져 있지만 표시 되는 경우 효과가 없는 메뉴를 표시 합니다.
- `AFX_MBS_HIDDEN` (0x02)-메뉴가 표시 되는 경우 메뉴를 숨기으 나 숨겨진 경우에는 효과가 없습니다.

### <a name="return-value"></a>반환 값

이 메서드가 메뉴 상태를 성공적으로 변경 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

런타임 오류가 발생 하는 경우이 메서드는 디버그 모드에서 어설션 하 고 [Cexception](../../mfc/reference/cexception-class.md) 클래스에서 파생 된 예외를 발생 시킵니다.

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a> CFrameWnd:: Setmenu바 표시 유형

현재 MFC 응용 프로그램의 메뉴 기본 동작을 숨기 거 나 표시할 수 있도록 설정 합니다.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>매개 변수

*nStyle*\
진행 메뉴를 기본적으로 숨길지 아니면 표시 하 고 포커스를 표시할지 여부를 지정 합니다. *Nstyle* 매개 변수는 다음 값을 가질 수 있습니다.

- `AFX_MBV_KEEPVISIBLE` (0x01)-메뉴가 항상 표시 되며 기본적으로 포커스가 포함 되지 않습니다.

- `AFX_MBV_DISPLAYONFOCUS` (0x02)-메뉴는 기본적으로 숨겨져 있습니다. 메뉴가 숨겨진 경우 ALT 키를 눌러 메뉴를 표시 하 고 포커스를 제공 합니다. 메뉴가 표시 되 면 ALT 또는 ESC 키를 눌러 메뉴를 숨깁니다.

- `AFX_MBV_DISPLAYONFOCUS` (0x02) &#124; `AFX_MBV_DISPLAYONF10` (0x04) (비트 조합 (or))-메뉴는 기본적으로 숨겨져 있습니다. 메뉴가 숨겨진 경우 F10 키를 눌러 메뉴를 표시 하 고 포커스를 제공 합니다. 메뉴가 표시 되 면 F10 키를 눌러 메뉴에 포커스를 설정 하거나 해제 합니다. ALT 또는 ESC 키를 눌러 숨길 때까지 메뉴가 표시 됩니다.

### <a name="remarks"></a>설명

*Nstyle* 매개 변수의 값이 유효 하지 않은 경우이 메서드는 디버그 모드에서 어설션 하 고 릴리스 모드에서 [Cinvalidargexception](../../mfc/reference/cinvalidargexception-class.md) 을 발생 시킵니다. 다른 런타임 오류가 발생 하는 경우이 메서드는 디버그 모드에서 어설션 하 고 [Cexception](../../mfc/reference/cexception-class.md) 클래스에서 파생 된 예외를 발생 시킵니다.

이 메서드는 Windows Vista 이상용으로 작성 된 응용 프로그램의 메뉴 상태에 영향을 줍니다.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a> CFrameWnd:: SetMessageText

ID가 0 인 상태 표시줄 창에 문자열을 넣으려면이 함수를 호출 합니다.

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
상태 표시줄에 배치할 문자열을 가리킵니다.

*nID*<br/>
상태 표시줄에 배치할 문자열의 문자열 리소스 ID입니다.

### <a name="remarks"></a>설명

일반적으로 상태 표시줄의 가장 왼쪽, 가장 긴 창입니다.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a> CFrameWnd:: SetProgressBarPosition

작업 표시줄에 표시 되는 Windows 7 진행률 표시줄의 현재 위치를 설정 합니다.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>매개 변수

*nProgressPos*<br/>
설정할 위치를 지정 합니다. 로 설정 된 범위 내에 있어야 합니다 `SetProgressBarRange` .

### <a name="remarks"></a>설명

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a> CFrameWnd:: SetProgressBarRange

작업 표시줄에 표시 되는 Windows 7 진행률 표시줄의 범위를 설정 합니다.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>매개 변수

*nRangeMin*<br/>
최소 값입니다.

*nRangeMax*<br/>
최대값입니다.

### <a name="remarks"></a>설명

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a> CFrameWnd:: SetProgressBarState

작업 표시줄 단추에 표시 되는 진행률 표시기의 유형 및 상태를 설정 합니다.

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>매개 변수

*tbpFlags*<br/>
진행률 단추의 현재 상태를 제어 하는 플래그입니다. 모든 상태가 함께 사용할 수 없으므로 TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED 플래그 중 하나만 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a> CFrameWnd:: SetTaskbarOverlayIcon

오버로드됨. 작업 표시줄 단추에 오버레이를 적용 하 여 응용 프로그램 상태를 표시 하거나 사용자에 게 알립니다.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>매개 변수

*nIDResource*<br/>
오버레이로 사용할 아이콘의 리소스 ID를 지정 합니다. 자세한 내용은 *Hicon* 에 대 한 설명을 참조 하세요.

*lpcszDescr*<br/>
접근성을 위해 오버레이가 전달 하는 정보의 대체 텍스트 버전을 제공 하는 문자열에 대 한 포인터입니다.

*hIcon*<br/>
오버레이로 사용할 아이콘 핸들입니다. 이 아이콘은 16x16 픽셀을 96 dpi (인치당 도트 수)로 측정 하는 작은 아이콘 이어야 합니다. 작업 표시줄 단추에 오버레이 아이콘이 이미 적용 된 경우 기존 오버레이가 바뀝니다. 이 값은 NULL 일 수 있습니다. NULL 값이 처리 되는 방법은 작업 표시줄 단추가 단일 창이 나 창의 그룹을 나타내는지 여부에 따라 달라 집니다. 더 이상 필요 하지 않은 경우에는 호출 응용 프로그램에서 *Hicon* 을 해제 해야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE입니다. OS 버전이 Windows 7 보다 작거나 아이콘을 설정 하는 동안 오류가 발생 하면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cframewndsettitle"></a><a name="settitle"></a> CFrameWnd:: SetTitle

창 개체의 제목을 설정 합니다.

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>매개 변수

*lpszTitle*<br/>
창 개체의 제목을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a> CFrameWnd:: ShowControlBar

이 멤버 함수를 호출 하 여 컨트롤 막대를 표시 하거나 숨깁니다.

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
표시 하거나 숨길 컨트롤 막대에 대 한 포인터입니다.

*bShow*<br/>
TRUE 이면 컨트롤 막대를 표시 하도록 지정 합니다. FALSE 이면 컨트롤 막대를 숨기도록 지정 합니다.

*bDelay*<br/>
TRUE 이면 컨트롤 막대를 표시 하는 지연입니다. FALSE 이면 컨트롤 막대를 즉시 표시 합니다.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a> CFrameWnd:: ShowOwnedWindows

개체의 하위 항목인 모든 창을 표시 하려면이 멤버 함수를 호출 `CFrameWnd` 합니다.

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
소유 된 창을 표시 하거나 숨길지 여부를 지정 합니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 클래스](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 클래스](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 구조체](../../mfc/reference/cruntimeclass-structure.md)
