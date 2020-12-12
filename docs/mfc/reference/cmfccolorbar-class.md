---
description: '자세한 정보: CMFCColorBar 클래스'
title: CMFCColorBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 5a2935c71a5579dddb2133f2ac6589a6bd447ef6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327709"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 클래스

`CMFCColorBar`클래스는 문서 또는 응용 프로그램에서 색을 선택할 수 있는 도킹 컨트롤 막대를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CMFCColorBar:: CMFCColorBar](#cmfccolorbar)|`CMFCColorBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCColorBar:: ContextToSize](#contexttosize)|색 막대 컨트롤의 단추를 포함 하는 데 필요한 세로 및 가로 여백을 계산한 다음 해당 단추의 위치를 조정 합니다.|
|[CMFCColorBar:: CreateControl](#createcontrol)|색 막대 컨트롤 창을 만들고 개체에 연결한 `CMFCColorBar` 다음 지정 된 색 색상표를 포함 하도록 컨트롤의 크기를 조정 합니다.|
|[CMFCColorBar:: Create](#create)|색 막대 컨트롤 창을 만들고이를 개체에 연결 `CMFCColorBar` 합니다.|
|[CMFCColorBar:: Enable자동 단추](#enableautomaticbutton)|자동 단추를 표시 하거나 숨깁니다.|
|[CMFCColorBar:: EnableOtherButton](#enableotherbutton)|사용자가 더 많은 색을 선택할 수 있는 대화 상자 표시를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCColorBar:: GetColor](#getcolor)|현재 선택 된 색을 검색 합니다.|
|[CMFCColorBar:: GetCommandID](#getcommandid)|현재 색 막대 컨트롤의 명령 ID를 검색 합니다.|
|[CMFCColorBar:: GetHighlightedColor](#gethighlightedcolor)|색 단추에 포커스가 있음을 나타내는 색을 검색 합니다. 즉, 단추가 *활성* 상태입니다.|
|[CMFCColorBar:: GetHorzMargin](#gethorzmargin)|왼쪽 또는 오른쪽 색 셀과 클라이언트 영역 경계 사이의 공백의 가로 여백을 검색 합니다.|
|[CMFCColorBar:: GetVertMargin](#getvertmargin)|위쪽 또는 아래쪽 색 셀과 클라이언트 영역 경계 사이의 공간에 해당 하는 세로 여백을 검색 합니다.|
|[CMFCColorBar:: IsTearOff](#istearoff)|현재 색 막대를 도킹할 수 있는지 여부를 나타냅니다.|
|[CMFCColorBar:: SetColor](#setcolor)|현재 선택 된 색을 설정 합니다.|
|[CMFCColorBar:: SetColorName](#setcolorname)|지정 된 색의 새 이름을 설정 합니다.|
|[CMFCColorBar:: SetCommandID](#setcommandid)|색 막대 컨트롤의 새 명령 ID를 설정 합니다.|
|[CMFCColorBar:: SetDocumentColors](#setdocumentcolors)|현재 문서에 사용 되는 색 목록을 설정 합니다.|
|[CMFCColorBar:: SetHorzMargin](#sethorzmargin)|왼쪽 또는 오른쪽 색 셀과 클라이언트 영역 경계 사이의 공백의 가로 여백을 설정 합니다.|
|[CMFCColorBar:: SetVertMargin](#setvertmargin)|위쪽 또는 아래쪽 색 셀과 클라이언트 영역 경계 사이의 공백의 세로 여백을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCColorBar:: AdjustLocations](#adjustlocations)|색 막대 컨트롤에서 색 단추의 위치를 조정 합니다.|
|[CMFCColorBar:: AllowChangeTextLabels](#allowchangetextlabels)|색 단추의 텍스트 레이블을 변경할 수 있는지 여부를 나타냅니다.|
|[CMFCColorBar:: AllowShowOnList](#allowshowonlist)|사용자 지정 프로세스 중에 도구 모음 목록에 색 막대 컨트롤 개체를 표시할 수 있는지 여부를 나타냅니다.|
|[CMFCColorBar:: CalcSize](#calcsize)|레이아웃 계산 프로세스의 일부로 프레임 워크에서 호출 됩니다.|
|[CMFCColorBar:: CreatePalette](#createpalette)|지정 된 색 배열의 색을 사용 하 여 색상표를 초기화 합니다.|
|[CMFCColorBar:: GetColorGridSize](#getcolorgridsize)|색 막대 컨트롤의 표에 있는 행과 열의 수를 계산 합니다.|
|[CMFCColorBar:: GetExtraHeight](#getextraheight)|현재 색 막대에서 **다른** 단추, 문서 색 등의 기타 사용자 인터페이스 요소를 표시 하는 데 필요한 추가 높이를 계산 합니다.|
|[CMFCColorBar:: InitColors](#initcolors)|지정 된 색상표 또는 시스템 기본 색상표의 색을 사용 하 여 색 배열을 초기화 합니다.|
|[CMFCColorBar:: OnKey](#onkey)|사용자가 키보드 단추를 누를 때 프레임 워크에서 호출 됩니다.|
|[CMFCColorBar:: OnSendCommand](#onsendcommand)|Popup 컨트롤의 계층 구조를 닫기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorBar:: OnUpdateCmdUI](#onupdatecmdui)|항목이 표시 되기 전에 색 막대 컨트롤의 사용자 인터페이스 항목을 설정 하거나 해제 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorBar:: OpenColorDialog](#opencolordialog)|색 대화 상자를 엽니다.|
|[CMFCColorBar:: Rebuild](#rebuild)|색 막대 컨트롤을 완전히 다시 그립니다.|
|[CMFCColorBar:: SelectPalette](#selectpalette)|지정 된 장치 컨텍스트의 논리 색상표를 현재 색 막대 컨트롤의 부모 단추에 대 한 팔레트에 설정 합니다.|
|[CMFCColorBar:: SetPropList](#setproplist)|보호 된 `m_pWndPropList` 데이터 멤버를 속성 표 컨트롤에 대 한 지정 된 포인터로 설정 합니다.|
|[CMFCColorBar:: ShowCommandMessageString](#showcommandmessagestring)|상태 표시줄의 메시지 줄을 업데이트 하기 위해 색 막대 컨트롤을 소유 하는 프레임 창을 요청 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|`m_bInternal`|마우스 이벤트가 처리 되는지 여부를 결정 하는 부울 필드입니다. 일반적으로이 필드가 TRUE이 고 사용자 지정 모드가 FALSE 인 경우 마우스 이벤트가 처리 됩니다.|
|`m_bIsEnabled`|컨트롤을 사용할 수 있는지 여부를 나타내는 부울입니다.|
|`m_bIsTearOff`|색 막대 컨트롤이 도킹을 지원 하는지 여부를 나타내는 부울입니다.|
|`m_BoxSize`|색 막대 모눈의 셀 크기를 지정 하는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.|
|`m_bShowDocColorsWhenDocked`|색 막대를 도킹할 때 문서 색을 표시할지 여부를 나타내는 부울입니다. 자세한 내용은 [Cmfccolorbar:: SetDocumentColors](#setdocumentcolors)를 참조 하세요.|
|`m_bStdColorDlg`|표준 시스템 색 대화 상자 또는 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 대화 상자를 표시할지 여부를 나타내는 부울입니다. 자세한 내용은 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)을 참조 하세요.|
|`m_ColorAutomatic`|현재 자동 색을 저장 하는 [Colorref](/windows/win32/gdi/colorref) 입니다. 자세한 내용은 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)을 참조 하세요.|
|`m_ColorNames`|RGB 색 집합을 해당 이름과 연결 하는 [Cmap](../../mfc/reference/cmap-class.md) 개체입니다.|
|`m_colors`|색 막대 컨트롤에 표시 되는 색을 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값의 [CArray](../../mfc/reference/carray-class.md) 입니다.|
|`m_ColorSelected`|사용자가 색 막대 컨트롤에서 현재 선택한 색인 [Colorref](/windows/win32/gdi/colorref) 값입니다.|
|`m_lstDocColors`|문서에서 현재 사용 되는 색을 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값의 [CList](../../mfc/reference/clist-class.md) 입니다.|
|`m_nCommandID`|색 단추의 명령 ID 인 부호 없는 정수입니다.|
|`m_nHorzMargin`|색 표에서 색 단추 사이의 가로 여백에 해당 하는 정수입니다.|
|`m_nHorzOffset`|색 단추 중심의 가로 오프셋 인 정수입니다. 이 값은 단추가 색 외에도 텍스트 또는 이미지를 표시 하는 경우에 중요 합니다.|
|`m_nNumColumns`|색 막대 컨트롤 색의 열 수 인 정수입니다.|
|`m_nNumColumnsVert`|색의 세로 방향 모눈에 있는 열 수 인 정수입니다.|
|`m_nNumRowsHorz`|색의 가로 방향 표에서 열 수 인 정수입니다.|
|`m_nRowHeight`|색 표에서 색 단추 행의 높이를 나타내는 정수입니다.|
|`m_nVertMargin`|색 표에서 색 단추 사이의 세로 여백에 해당 하는 정수입니다.|
|`m_nVertOffset`|색 단추의 가운데에 대 한 세로 오프셋을 나타내는 정수입니다. 이 값은 단추가 색 외에도 텍스트 또는 이미지를 표시 하는 경우에 중요 합니다.|
|`m_Palette`|색 막대 컨트롤에 사용 되는 색의 [Cpalette](../../mfc/reference/cpalette-class.md) 입니다.|
|`m_pParentBtn`|현재 단추의 부모인 [Cmfccolorbutton](../../mfc/reference/cmfccolorbutton-class.md) 개체에 대 한 포인터입니다. 이 값은 색 단추가 도구 모음 컨트롤의 계층 구조에 있거나 색 속성 그리드 컨트롤에 있는 경우에 중요 합니다.|
|`m_pParentRibbonBtn`|리본에 있고 현재 단추의 부모 단추인 [Cmfcribbon colorbutton](../../mfc/reference/cmfcribboncolorbutton-class.md) 개체에 대 한 포인터입니다. 이 값은 색 단추가 도구 모음 컨트롤의 계층 구조에 있거나 색 속성 그리드 컨트롤에 있는 경우에 중요 합니다.|
|`m_pWndPropList`|[Cmfcpropertygridctrl](../../mfc/reference/cmfcpropertygridctrl-class.md) 개체에 대 한 포인터입니다.|
|`m_strAutoColor`|**자동** 단추에 표시 되는 텍스트인 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다. 자세한 내용은 [Cmfccolorbar:: Enable자동 단추](#enableautomaticbutton)를 참조 하세요.|
|`m_strDocColors`|문서 색 단추에 표시 되는 텍스트인 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다. 자세한 내용은 [Cmfccolorbar:: SetDocumentColors](#setdocumentcolors)를 참조 하세요.|
|`m_strOtherColor`|*다른* 단추에 표시 되는 텍스트인 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다. 자세한 내용은 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)을 참조 하세요.|

## <a name="remarks"></a>설명

일반적으로 개체를 직접 만들지 않습니다 `CMFCColorBar` . 대신, [Cmfccolormenubutton 클래스](../../mfc/reference/cmfccolormenubutton-class.md) (메뉴 및 도구 모음에 사용 됨) 또는 [cmfccolorbutton 클래스](../../mfc/reference/cmfccolorbutton-class.md) 에서 개체를 만듭니다 `CMFCColorBar` .

`CMFCColorBar`클래스는 다음과 같은 기능을 제공 합니다.

- 문서 색 목록을 자동으로 조정 합니다.

- 상태를 문서 상태와 함께 저장 하 고 복원 합니다.

- "자동" 단추를 관리 합니다.

- [Cmfccolorpickerctrl 클래스](../../mfc/reference/cmfccolorpickerctrl-class.md) 컨트롤을 사용 하 여 사용자 지정 색을 선택 합니다.

- "분리" 상태를 지원 합니다 ( [Cmfccolormenubutton 클래스](../../mfc/reference/cmfccolormenubutton-class.md)를 사용 하 여 만든 경우).

응용 프로그램에 기능을 통합 하려면 `CMFCColorBar` 다음을 수행 합니다.

1. 일반 메뉴 단추를 만들고 ID_CHAR_COLOR와 같은 ID를 할당 합니다.

1. 프레임 창 클래스에서 [CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) 메서드를 재정의 하 고 일반 메뉴 단추를 [Cmfccolormenubutton 클래스](../../mfc/reference/cmfccolormenubutton-class.md) 개체로 바꿉니다 ( [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)를 호출 하 여).

1. `CMFCColorBar` [Cmfccolormenubutton 클래스](../../mfc/reference/cmfccolormenubutton-class.md) 를 만드는 동안 모든 스타일을 설정 하 고 개체의 기능을 사용 하거나 사용 하지 않도록 설정 합니다. `CMFCColorMenuButton`개체는 `CMFCColorBar` 프레임 워크가 메서드를 호출한 후 개체를 동적으로 만듭니다 `CreatePopupMenu` .

사용자가 색 막대 컨트롤 단추를 클릭 하면 프레임 워크에서 매크로를 사용 `ON_COMMAND` 하 여 색 막대 컨트롤의 부모에 알립니다. 매크로에서 명령 ID 매개 변수는 1 단계에서 색 막대 컨트롤 단추에 할당 한 값 (이 예제에서는 ID_CHAR_COLOR)입니다. 자세한 내용은 [Cmfccolormenubutton 클래스](../../mfc/reference/cmfccolormenubutton-class.md), cmfccolorbutton [클래스](../../mfc/reference/cmfccolorbutton-class.md), [cmfccolormenukerctrl 클래스](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx 클래스](../../mfc/reference/cframewndex-class.md)및 [cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md) 클래스를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 색 막대를 구성 하는 방법을 보여 줍니다 `CMFCColorBar` . 메서드는 가로 및 세로 여백을 설정 하 고, 기타 단추를 사용 하도록 설정 하 고, 색 막대 컨트롤 창을 만들고, 현재 선택 된 색을 설정 합니다. 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcolorbar

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a> CMFCColorBar:: AdjustLocations

색 막대 컨트롤에서 색 단추의 위치를 조정 합니다.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>설명

이 메서드는 WM_SIZE 메시지를 처리 하는 동안 프레임 워크에서 호출 됩니다.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a> CMFCColorBar:: AllowChangeTextLabels

색 단추의 텍스트 레이블을 변경할 수 있는지 여부를 나타냅니다.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>반환 값

항상 FALSE입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 항상 FALSE를 반환 하며,이는 텍스트 레이블을 수정할 수 없음을 의미 합니다. 텍스트 레이블을 수정할 수 있도록 하려면이 메서드를 재정의 합니다.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a> CMFCColorBar:: AllowShowOnList

사용자 지정 프로세스 중에 도구 모음 목록에 색 막대 컨트롤 개체를 표시할 수 있는지 여부를 나타냅니다.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>반환 값

항상 TRUE입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 항상 TRUE를 반환 합니다. 즉, 프레임 워크에서 사용자 지정 프로세스 중 색 막대 컨트롤을 표시할 수 있습니다. 다른 동작을 구현 하려면이 메서드를 재정의 합니다.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a> CMFCColorBar:: CalcSize

레이아웃 계산 프로세스의 일부로 프레임 워크에서 호출 됩니다.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>매개 변수

*bVertDock*<br/>
진행 색 막대 컨트롤이 세로로 도킹 되도록 지정 하려면 TRUE로 설정 합니다. 색 막대 컨트롤이 가로로 도킹 되도록 지정 하려면 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

색 막대 컨트롤에서 색 단추 배열의 크기입니다.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a> CMFCColorBar:: CMFCColorBar

`CMFCColorBar` 개체를 생성합니다.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>매개 변수

*분판*<br/>
진행 색 막대 컨트롤에 프레임 워크가 표시 하는 색의 배열입니다.

*color*<br/>
진행 처음에 선택한 색입니다.

*lpszAutoColor*<br/>
진행 *자동* (기본) 색 단추의 텍스트 레이블이나 NULL입니다.

자동 단추의 표준 레이블은 **자동** 입니다.

*lpszOtherColor*<br/>
진행 추가 색을 선택 하거나 NULL을 표시 하는 *기타* 단추의 텍스트 레이블입니다.

다른 단추의 표준 레이블은 다른 **색 ...** 입니다.

*lpszDocColors*<br/>
진행 문서 색 단추의 텍스트 레이블입니다. 문서 색 색상표에는 문서에서 현재 사용 하는 모든 색이 나열 됩니다.

*lstDocColors*<br/>
진행 문서에서 현재 사용 하는 색 목록입니다.

*nColumns*<br/>
진행 색 배열에 포함 된 열의 수입니다.

*nRowsDockHorz*<br/>
진행 색 막대가 가로로 도킹 될 때 표시 되는 행의 수입니다.

*nColDockVert*<br/>
진행 세로 방향으로 도킹할 때 색 막대의 열 수입니다.

*colorAutomatic*<br/>
진행 자동 단추를 클릭할 때 프레임 워크에서 적용 하는 기본 색입니다.

*nCommandID*<br/>
진행 색 막대 컨트롤 명령 ID입니다.

*pParentBtn*<br/>
진행 부모 단추에 대 한 포인터입니다.

*src*<br/>
진행 `CMFCColorBar` 새 개체에 복사할 기존 개체 `CMFCColorBar` 입니다.

*uiCommandID*<br/>
진행 명령 ID입니다.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a> CMFCColorBar:: ContextToSize

색 막대 컨트롤의 단추를 포함 하는 데 필요한 세로 및 가로 여백을 계산 하 고 해당 단추의 위치를 조정 합니다.

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSquareButtons*\
진행 색 막대 컨트롤의 단추 모양이 정사각형 임을 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

*bCenterButtons*\
진행 색 막대 컨트롤 단추의 표면에 있는 콘텐츠가 가운데 맞춤 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbarcreate"></a><a name="create"></a> CMFCColorBar:: Create

색 막대 컨트롤 창을 만들고이를 개체에 연결 `CMFCColorBar` 합니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
진행 부모 창에 대 한 포인터입니다.

*dwStyle*<br/>
진행 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)의 비트 조합 (or)입니다.

*nID*<br/>
진행 명령 ID입니다.

*pPalette*<br/>
진행 색의 색상표에 대 한 포인터입니다. 기본값은 NULL입니다.

*nColumns*<br/>
진행 색 막대 컨트롤의 열 수입니다. 기본값은 0입니다.

*nRowsDockHorz*<br/>
진행 가로 방향으로 도킹할 때 색 막대 컨트롤의 행 수입니다. 기본값은 0입니다.

*nColDockVert*<br/>
진행 세로 방향으로 도킹할 때 색 막대 컨트롤의 열 수입니다. 기본값은 0입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

개체를 생성 하려면 `CMFCColorBar` 클래스 생성자를 호출한 후이 메서드를 호출 합니다. `Create`메서드는 Windows 컨트롤을 만들고 색 목록을 초기화 합니다.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a> CMFCColorBar:: CreateControl

색 막대 컨트롤 창을 만들고, 개체에 연결 하 `CMFCColorBar` 고, 지정 된 색상표를 포함 하는 컨트롤 창의 크기를 조정 합니다.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
진행 부모 창에 대 한 포인터입니다. NULL이 될 수 없습니다.

*rect*<br/>
진행 색 막대 컨트롤을 그릴 위치를 지정 하는 경계 사각형입니다.

*nID*<br/>
진행 컨트롤 ID입니다.

*nColumns*<br/>
진행 색 막대 컨트롤의 이상적인 열 수입니다. 이 메서드는 지정 된 색 색상표에 맞게 해당 숫자를 수정 합니다. 기본값은-1입니다. 즉,이 매개 변수는 지정 되지 않습니다.

*pPalette*<br/>
진행 색의 색상표 또는 NULL에 대 한 포인터입니다. 이 매개 변수가 NULL 인 경우이 메서드는 20 개의 색이 지정 된 것 처럼 색 막대 컨트롤의 크기를 계산 합니다. 기본값은 NULL입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 *rect*, *Ncolumns* 및 *pPalette* 매개 변수를 사용 하 여 색 막대 컨트롤의 적절 한 수 또는 행과 열을 계산한 다음 [cmfccolorbar:: Create](#create) 메서드를 호출 합니다.

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a> CMFCColorBar:: CreatePalette

지정 된 색 배열의 색을 사용 하 여 색상표를 초기화 합니다.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>매개 변수

*arColors*\
진행 색의 배열입니다.

*색*\
진행 색의 색상표입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorBar:: Enable자동 단추

자동 단추를 표시 하거나 숨깁니다.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 *자동* (기본) 색 단추의 텍스트 레이블이나 NULL입니다.

자동 단추의 표준 레이블은 **자동** 입니다.

*colorAutomatic*<br/>
진행 자동 단추를 클릭할 때 프레임 워크에서 적용 하는 기본 색입니다.

*bEnable*<br/>
진행 자동 단추를 사용 하려면 TRUE로 설정 합니다. 자동 단추를 사용 하지 않으려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

*LpszLabel* 매개 변수가 NULL 이거나 *BENABLE* 매개 변수가 FALSE 인 경우 자동 단추의 텍스트 레이블이 삭제 됩니다.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorBar:: EnableOtherButton

사용자가 더 많은 색을 선택할 수 있는 대화 상자 표시를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 추가 색을 선택 하거나 NULL을 표시 하는 *기타* 단추의 텍스트 레이블입니다.

이 단추에 대 한 표준 레이블이 **추가 색**...입니다.

*bAltColorDlg*<br/>
진행 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 대화 상자를 표시 하려면 TRUE로 설정 합니다. FALSE 이면 표준 [CColorDialog](../../mfc/reference/ccolordialog-class.md) 대화 상자가 표시 됩니다. 기본값은 TRUE입니다.

*bEnable*<br/>
진행 단추를 사용 하려면 TRUE이 고, 그렇지 않으면입니다. FALSE 이면 단추를 사용 하지 않습니다. 기본값은 TRUE입니다.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a> CMFCColorBar:: GetColor

현재 선택 된 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

현재 선택한 색입니다.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a> CMFCColorBar:: GetColorGridSize

색 막대 컨트롤의 표에 있는 행과 열의 수를 계산 합니다.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>매개 변수

*bVertDock*\
진행 세로 도킹 된 색 막대 컨트롤에 대해 계산을 수행 하려면 TRUE이 고, 그렇지 않으면 가로 도킹 된 컨트롤에 대 한 계산을 수행 합니다.

### <a name="return-value"></a>반환 값

[](../../atl-mfc-shared/reference/csize-class.md) `cx` 구성 요소에 열 수가 포함 되 고 해당 `cy` 구성 요소에 행 수가 포함 된 csize 개체입니다.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a> CMFCColorBar:: GetCommandID

현재 색 막대 컨트롤의 명령 ID를 검색 합니다.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>반환 값

명령 ID입니다.

### <a name="remarks"></a>설명

사용자가 새 색을 선택 하면 프레임 워크는 WM_COMMAND 메시지에 명령 ID를 보내 개체의 부모에 알립니다 `CMFCColorBar` .

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a> CMFCColorBar:: GetExtraHeight

현재 색 막대에서 **기타** 단추 또는 문서 색과 같은 기타 사용자 인터페이스 요소를 표시 하는 데 필요한 추가 높이를 계산 합니다.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>매개 변수

*nNumColumns*\
진행 색 막대 컨트롤에 문서 색이 포함 되어 있는 경우 문서 색의 표에 표시할 열 수입니다. 그렇지 않으면이 값이 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

필요한 계산 된 추가 높이입니다.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a> CMFCColorBar:: GetHighlightedColor

색 단추에 포커스가 있음을 나타내는 색을 검색 합니다. 즉, 단추가 *활성* 상태입니다.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>반환 값

RGB 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a> CMFCColorBar:: GetHorzMargin

왼쪽 또는 오른쪽 색 셀과 클라이언트 영역 경계 사이의 공백의 가로 여백을 검색 합니다.

```
int GetHorzMargin();
```

### <a name="return-value"></a>반환 값

가로 여백입니다.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a> CMFCColorBar:: GetVertMargin

위쪽 또는 아래쪽 색 셀과 클라이언트 영역 경계 사이의 공간에 해당 하는 세로 여백을 검색 합니다.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>반환 값

세로 여백입니다.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a> CMFCColorBar:: InitColors

지정 된 색상표의 색 이나 시스템 기본 색상표를 사용 하 여 색 배열을 초기화 합니다.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>매개 변수

*pPalette*\
진행 Palette 개체에 대 한 포인터 이거나 NULL입니다. 이 매개 변수가 NULL 이면이 메서드는 운영 체제의 기본 색상표를 사용 합니다.

*arColors*\
진행 색의 배열입니다.

### <a name="return-value"></a>반환 값

색 배열의 요소 수입니다.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a> CMFCColorBar:: IsTearOff

현재 색 막대를 도킹할 수 있는지 여부를 나타냅니다.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>반환 값

현재 색 막대 컨트롤을 도킹할 수 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

색 막대 컨트롤을 도킹할 수 있는 경우 컨트롤 막대에서 분리 하 고 다른 위치에 도킹할 수 있습니다.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a> CMFCColorBar:: OnKey

사용자가 키보드 단추를 누를 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>매개 변수

*nChar*<br/>
진행 사용자가 누른 키의 가상 키 코드입니다.

### <a name="return-value"></a>반환 값

이 메서드가 지정 된 키를 처리 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a> CMFCColorBar:: OnSendCommand

팝업 컨트롤의 계층 구조를 닫기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>매개 변수

*pButton*\
진행 도구 모음에 있는 컨트롤에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCColorBar:: OnUpdateCmdUI

항목이 표시 되기 전에 색 막대 컨트롤의 사용자 인터페이스 항목을 설정 하거나 해제 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>매개 변수

*pTarget*<br/>
진행 업데이트할 사용자 인터페이스 항목이 들어 있는 창에 대 한 포인터입니다.

*bDisableIfNoHndler*<br/>
진행 메시지 맵에 처리기가 정의 되어 있지 않으면 사용자 인터페이스 항목을 사용 하지 않도록 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

응용 프로그램의 사용자가 사용자 인터페이스 항목을 클릭 하면 해당 항목은 사용 또는 사용 안 함으로 표시 되어야 하는지 여부를 알아야 합니다. 명령 메시지의 대상은 ON_UPDATE_COMMAND_UI 명령 처리기를 구현 하 여이 정보를 제공 합니다. 이 메서드를 사용 하 여 명령을 처리할 수 있습니다. 자세한 내용은 [CCmdUI 클래스](../../mfc/reference/ccmdui-class.md)를 참조 하세요.

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a> CMFCColorBar:: OpenColorDialog

색 대화 상자를 엽니다.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>매개 변수

*colorDefault*<br/>
진행 색 대화 상자를 열 때 기본적으로 선택 되는 색입니다.

*colorRes*<br/>
제한이 사용자가 선택한 색입니다.

### <a name="return-value"></a>반환 값

사용자가 색을 선택한 경우 TRUE입니다. 사용자가 색 대화 상자를 취소 한 경우 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a> CMFCColorBar:: Rebuild

색 막대 컨트롤을 완전히 다시 그립니다.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a> CMFCColorBar:: SelectPalette

지정 된 장치 컨텍스트의 논리 색상표를 현재 색 막대 컨트롤의 부모 단추에 대 한 팔레트에 설정 합니다.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*\
진행 현재 색 막대 컨트롤의 부모 단추에 대 한 장치 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

현재 색 막대 컨트롤의 부모 단추 색상표로 대체 되는 색상표에 대 한 포인터입니다.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a> CMFCColorBar:: SetColor

현재 선택 된 색을 설정 합니다.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 RGB 색 값입니다.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a> CMFCColorBar:: SetColorName

지정 된 색의 새 이름을 설정 합니다.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 색의 RGB 값입니다.

*strName*<br/>
진행 지정 된 색의 새 이름입니다.

### <a name="remarks"></a>설명

이 메서드는 응용 프로그램의 모든 개체에서 지정 된 색의 이름을 변경 합니다 `CMFCColorBar` .

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a> CMFCColorBar:: SetCommandID

색 막대 컨트롤의 새 명령 ID를 설정 합니다.

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>매개 변수

*nCommandID*<br/>
진행 명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 색 막대 컨트롤의 명령 ID를 수정 하 고 해당 ID가 변경 되었음을 컨트롤의 부모 창에 알립니다.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorBar:: SetDocumentColors

현재 문서에 사용 되는 색 목록을 설정 합니다.

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszCaption*<br/>
진행 색 막대 컨트롤이 도킹 되지 않을 때 표시 되는 캡션입니다.

*lstDocColors*<br/>
진행 현재 문서 색을 대체 하는 색 목록입니다.

*Bshow고정*<br/>
진행 색 막대 컨트롤을 도킹할 때 문서 색을 표시 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

*문서 색* 은 문서에서 현재 사용 되는 색입니다. 프레임 워크는 문서 색 목록을 자동으로 유지 하지만이 메서드를 사용 하 여 목록을 수정할 수 있습니다.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a> CMFCColorBar:: SetHorzMargin

왼쪽 또는 오른쪽 색 셀과 클라이언트 영역의 경계 사이에 있는 공백의 가로 여백을 설정 합니다.

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>매개 변수

*nHorzMargin*<br/>
진행 가로 여백 (픽셀)입니다.

### <a name="remarks"></a>설명

기본적으로 [cmfccolorbar:: cmfccolorbar](#cmfccolorbar) 생성자는 가로 여백을 4 픽셀로 설정 합니다.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a> CMFCColorBar:: SetPropList

보호 된 `m_pWndPropList` 데이터 멤버를 속성 표 컨트롤에 대 한 지정 된 포인터로 설정 합니다.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>매개 변수

*pWndList*\
진행 속성 표 컨트롤 개체에 대 한 포인터입니다.

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a> CMFCColorBar:: SetVertMargin

위쪽 또는 아래쪽 색 셀과 클라이언트 영역 경계 사이의 공백의 세로 여백을 설정 합니다.

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>매개 변수

*nVertMargin*<br/>
진행 세로 여백 (픽셀)입니다.

### <a name="remarks"></a>설명

기본적으로 [cmfccolorbar:: cmfccolorbar](#cmfccolorbar) 생성자는 세로 여백을 4 픽셀로 설정 합니다.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a> CMFCColorBar:: ShowCommandMessageString

상태 표시줄의 메시지 줄을 업데이트 하기 위해 색 막대 컨트롤을 소유 하는 프레임 창을 요청 합니다.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>매개 변수

*uiCmdId*<br/>
진행 명령 ID입니다. 이 매개 변수는 무시 됩니다.

### <a name="remarks"></a>설명

이 메서드는 WM_SETMESSAGESTRING 메시지를 색 막대 컨트롤의 소유자에 게 보냅니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
