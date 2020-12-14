---
description: '자세히 알아보기: CPaneDialog 클래스'
title: CPaneDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: 6efbbf710f09cf6507853b983a68578a24111a34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345175"
---
# <a name="cpanedialog-class"></a>CPaneDialog 클래스

`CPaneDialog`클래스는 도킹 가능한 모덜리스 대화 상자를 지원 합니다.

## <a name="syntax"></a>구문

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|기본 생성자입니다.|
|`CPaneDialog::~CPaneDialog`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPaneDialog:: Create](#create)|도킹 가능한 대화 상자를 만들고 개체에 연결 `CPaneDialog` 합니다.|
|`CPaneDialog::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CPaneDialog::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CPaneDialog:: HandleInitDialog](#handleinitdialog)|[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) 메시지를 처리 합니다. (를 다시 정의 `CBasePane::HandleInitDialog` 합니다.)|
|`CPaneDialog::OnEraseBkgnd`|[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) 메시지를 처리 합니다. ( [CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)를 재정의 합니다.)|
|`CPaneDialog::OnLButtonDblClk`|[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) 메시지를 처리 합니다. ( [CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)를 재정의 합니다.)|
|`CPaneDialog::OnLButtonDown`|[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) 메시지를 처리 합니다. ( [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)을 다시 정의 합니다.)|
|`CPaneDialog::OnUpdateCmdUI`|대화 상자 창을 업데이트 하기 위해 프레임 워크에서 호출 됩니다. [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md)를 재정의 합니다.|
|`CPaneDialog::OnWindowPosChanging`|[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) 메시지를 처리 합니다. ( [CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)를 재정의 합니다.)|
|[CPaneDialog:: SetOccDialogInfo](#setoccdialoginfo)|OLE 컨트롤 컨테이너의 대화 상자에 대 한 템플릿을 지정 합니다.|

## <a name="remarks"></a>설명

`CPaneDialog`두 단계로 개체를 생성 합니다. 먼저 코드에서 개체를 생성 합니다. 둘째, [CPaneDialog:: Create](#create)를 호출 합니다. 올바른 리소스 템플릿 이름 또는 템플릿 ID를 지정 하 고 부모 창에 포인터를 전달 해야 합니다. 그렇지 않으면 만들기 프로세스가 실패 합니다. 대화 상자에서 WS_CHILD 및 WS_VISIBLE 스타일을 지정 해야 합니다. WS_CLIPCHILDREN 및 WS_CLIPSIBLINGS 스타일도 지정 하는 것이 좋습니다. 자세한 내용은 [창 스타일](styles-used-by-mfc.md#window-styles)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpanedialog

## <a name="cpanedialogcreate"></a><a name="create"></a> CPaneDialog:: Create

도킹 대화 상자를 만들고 개체에 연결 `CPaneDialog` 합니다.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*lpszWindowName*<br/>
진행 도킹 대화 상자의 이름입니다.

*pParentWnd*<br/>
진행 부모 창을 가리킵니다.

*bHasGripper*<br/>
진행 캡션을 사용 하 여 도킹 대화 상자를 만들려면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

*lpszTemplateName*<br/>
진행 리소스 대화 상자 템플릿 이름입니다.

*nStyle*<br/>
진행 Windows 스타일입니다.

*nID*<br/>
진행 컨트롤 ID입니다.

*nIDTemplate*<br/>
진행 대화 상자 템플릿의 리소스 ID입니다.

*dwTabbedStyle*<br/>
진행 사용자가 다른 컨트롤 창을이 컨트롤 창의 캡션으로 끌 때 발생 하는 탭 창의 스타일입니다. 기본값은 AFX_CBRS_REGULAR_TABS입니다. 자세한 내용은 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) 메서드의 설명 섹션을 참조 하세요.

*Dwcontrol바 스타일*<br/>
진행 추가 스타일 특성입니다. 기본값은 AFX_DEFAULT_DOCKING_PANE_STYLE입니다. 자세한 내용은 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) 메서드의 설명 섹션을 참조 하세요.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `Create` `CPaneDialog` . 이 예제는 [집합 창 크기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a> CPaneDialog:: HandleInitDialog

[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) 메시지를 처리 합니다.

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*wParam*<br/>
진행 기본 키보드 포커스를 받을 컨트롤에 대 한 핸들입니다.

*lParam*<br/>
진행 추가 초기화 데이터를 지정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다. 또한 TRUE는 *wParam* 매개 변수로 지정 된 컨트롤에 키보드 포커스를 설정 합니다. FALSE로 설정 하면 기본 키보드 포커스를 설정할 수 없습니다.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 사용 하 여 컨트롤 및 대화 상자의 모양을 초기화 합니다. 프레임 워크는 대화 상자를 표시 하기 전에이 메서드를 호출 합니다.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a> CPaneDialog:: SetOccDialogInfo

OLE 컨트롤 컨테이너의 대화 상자에 대 한 템플릿을 지정 합니다.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>매개 변수

*pOccDialogInfo*<br/>
진행 대화 상자 개체를 만드는 데 사용 되는 대화 상자 템플릿에 대 한 포인터입니다. 이 매개 변수 값은 이후 [Coccmanager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) 메서드에 전달 됩니다.

### <a name="return-value"></a>반환 값

항상 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 OLE 컨트롤 사이트 및 ActiveX 컨트롤을 관리 하는 [Coccmanager](../../mfc/reference/coccmanager-class.md) 클래스를 지원 합니다. _AFX_OCC_DIALOG_INFO 구조는 afxocc 헤더 파일에 정의 되어 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)<br/>
[창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)
