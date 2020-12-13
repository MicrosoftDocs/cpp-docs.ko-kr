---
description: '자세히 알아보기: CMFCPopupMenuBar 클래스'
title: CMFCPopupMenuBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: 4db8c02ed92aec5243f9a2c7800c6fd1f9747751
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334748"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar 클래스

팝업 메뉴에 포함된 메뉴 모음입니다.

## <a name="syntax"></a>구문

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|창 레이아웃을 즉시 다시 계산 합니다. ( [Cpane:: AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)를 재정의 합니다.)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|지정 된 메뉴 리소스에서 팝업 메뉴 항목을 로드 합니다.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|지연 된 팝업 메뉴 단추를 닫습니다.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|팝업 메뉴 단추에서 메뉴를 빌드합니다.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|지정 된 점이 있는 도구 모음을 찾습니다.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|메뉴 단추 이미지의 크기를 나타냅니다.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|기본 메뉴 항목의 식별자를 반환 합니다.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|가장 최근에 호출 된 메뉴 명령의 인덱스를 가져옵니다.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|팝업 메뉴 모음의 행 오프셋을 가져옵니다.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|지정 된 메뉴에서 팝업 메뉴 단추를 가져옵니다.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|팝업 메뉴 모음이 드롭다운 목록 모드에 있는지 여부를 나타냅니다.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|팝업 메뉴 모음이 색상표 모드에 있는지 여부를 나타냅니다.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|리본 패널 (기본적으로 FALSE) 인지 여부를 나타냅니다.|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|일반 모드의 리본 패널 (기본적으로 FALSE) 인지 여부를 나타냅니다.|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|보관 된 메뉴를 로드 합니다.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|팝업 메뉴 모음을 닫기 위해 지연 된 메뉴 단추를 복원 합니다.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|지정 된 인덱스에 있는 도구 모음 단추의 스타일을 설정 합니다. [Cmfctoolbar:: SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)을 재정의 합니다.|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|팝업 메뉴 모음의 행 오프셋을 설정 합니다.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|지정 된 지연 팝업 메뉴 단추에 대 한 타이머를 시작 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCPopupMenuBar:: m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|응용 프로그램에 Windows XP 모양이 있을 때 회색 세로 막대를 표시할지 여부를 지정 합니다.|

## <a name="remarks"></a>설명

는 `CMFCPopupMenuBar` [CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md) 와 동시에 생성 되 고 그 안에 포함 됩니다. 는 `CMFCPopupMenuBar` 개체의 전체 클라이언트 영역을 포함 합니다 `CMFCPopupMenu` . 키보드 및 마우스 입력을 지원 합니다. 또한 및에 대 한 입력을 `CMFCPopupMenu` 최상위 프레임 창에 전달 합니다.

## <a name="example"></a>예제

다음 예제에서는 개체에서 개체를 초기화 하는 방법을 보여 줍니다 `CMFCPopupMenuBar` `CMFCPopupMenu` . 이 코드 조각은 [클라이언트 그리기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpopupmenubar

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a> CMFCPopupMenuBar:: AdjustSizeImmediate

팝업 메뉴 모음 창의 레이아웃을 즉시 다시 계산 합니다. ( [Cpane:: AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)를 재정의 합니다.

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>매개 변수

*bRecalcLayout*<br/>
진행 팝업 메뉴 모음 창의 레이아웃을 자동으로 다시 계산 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a> CMFCPopupMenuBar:: BuildOrigItems

지정 된 메뉴 리소스에서 팝업 메뉴 항목을 로드 합니다.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>매개 변수

*uiMenuResID*<br/>
진행 로드할 메뉴 리소스의 메뉴 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a> CMFCPopupMenuBar:: CloseDelayedSubMenu 메뉴

지연 된 팝업 메뉴 단추를 닫습니다.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a> CMFCPopupMenuBar:: ExportToMenu

팝업 메뉴 단추에서 메뉴를 빌드합니다.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>반환 값

새 메뉴에 대 한 핸들을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a> CMFCPopupMenuBar:: FindDestintationToolBar

지정 된 점이 있는 도구 모음을 찾습니다.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
진행 화면의 점입니다.

### <a name="return-value"></a>반환 값

점이 있는 경우 해당 점이 있는 도구 모음에 대 한 핸들을 반환 하 고 그렇지 않으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a> CMFCPopupMenuBar:: GetCurrentMenuImageSize

메뉴 단추 이미지의 크기를 나타냅니다.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>반환 값

도구 모음에 있는 메뉴 단추 이미지의 크기를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a> CMFCPopupMenuBar:: GetDefaultMenuId

기본 메뉴 항목의 식별자를 반환 합니다.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>반환 값

팝업 메뉴 모음에서 기본 메뉴 항목의 식별자를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a> CMFCPopupMenuBar:: GetLastCommandIndex

가장 최근에 호출 된 메뉴 명령의 인덱스를 가져옵니다.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>반환 값

호출 된 마지막 메뉴 명령의 인덱스를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a> CMFCPopupMenuBar:: GetOffset

팝업 메뉴 모음의 행 오프셋을 가져옵니다.

```
int GetOffset() const;
```

### <a name="return-value"></a>반환 값

팝업 메뉴 모음의 행 오프셋을 반환 합니다.

### <a name="remarks"></a>설명

이 값은 [CMFCPopupMenuBar:: SetOffset](#setoffset)를 사용 하 여 설정 됩니다.

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a> CMFCPopupMenuBar:: ImportFromMenu

지정 된 메뉴에서 팝업 메뉴 단추를 가져옵니다.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>매개 변수

*hMenu*<br/>
진행 팝업 메뉴 단추를 가져올 메뉴입니다.

*bShowAllCommands*<br/>
진행 메뉴의 모든 명령을 가져올 경우 TRUE이 고 거의 사용 되지 않는 경우에는 FALSE입니다.

### <a name="return-value"></a>반환 값

메뉴에서 메뉴 단추를 성공적으로 가져온 경우 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a> CMFCPopupMenuBar:: IsDropDownListMode

팝업 메뉴 모음이 드롭다운 목록 모드에 있는지 여부를 나타냅니다.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>반환 값

팝업 메뉴 모음이 드롭다운 목록 모드에 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a> CMFCPopupMenuBar:: IsPaletteMode

팝업 메뉴 모음이 색상표 모드에 있는지 여부를 나타냅니다.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>반환 값

색상표 모드가 활성화 된 경우 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

메뉴 모음이 팔레트 모드로 설정 된 경우 메뉴 항목은 여러 열 및 제한 된 수의 행에 표시 됩니다.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a> CMFCPopupMenuBar:: Is리본 패널

리본 패널 (기본적으로 FALSE) 인지 여부를 나타냅니다.

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>반환 값

기본적으로 FALSE를 반환 합니다 .이는 리본 패널이 아님을 나타냅니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a> CMFCPopupMenuBar:: IsRibbonPanelInRegularMode

일반 모드의 리본 패널 (기본적으로 FALSE) 인지 여부를 나타냅니다.

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>반환 값

기본적으로 FALSE를 반환 하 여 일반 모드에서 리본 패널이 아님을 나타냅니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a> CMFCPopupMenuBar:: LoadFromHash

보관 된 메뉴를 로드 합니다.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>매개 변수

*hMenu*<br/>
진행 로드할 보관 된 메뉴에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

메뉴가 성공적으로 로드 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a> CMFCPopupMenuBar:: m_bDisableSideBarInXPMode

Windows XP 모양을 사용할 때 응용 프로그램에 회색 세로 막대가 있는지 여부를 나타내는 부울 매개 변수입니다.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>설명

이 멤버 변수가 FALSE로 설정 되어 있고 응용 프로그램에 Windows XP 모양이 있는 경우 프레임 워크는 응용 프로그램에서 회색 세로 막대를 그립니다.

기본값은 FALSE입니다.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a> CMFCPopupMenuBar:: RestoreDelayedSubMenu

팝업 메뉴 모음을 닫기 위해 지연 된 메뉴 단추를 복원 합니다.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a> CMFCPopupMenuBar:: SetButtonStyle

지정 된 인덱스에 있는 도구 모음 단추의 스타일을 설정 합니다. [Cmfctoolbar:: SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)을 재정의 합니다.

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 스타일을 설정할 도구 모음 단추의 인덱스 (0부터 시작)입니다.

*nStyle*<br/>
진행 단추의 스타일입니다. 사용 가능한 도구 모음 단추 스타일의 목록에 대 한 [도구 모음 컨트롤 스타일](../../mfc/reference/toolbar-control-styles.md) 을 참조 하세요.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a> CMFCPopupMenuBar:: SetOffset

팝업 메뉴 모음의 행 오프셋을 설정 합니다.

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>매개 변수

*iOffset*<br/>
진행 팝업 메뉴 모음을 오프셋할 행 수입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a> CMFCPopupMenuBar:: StartPopupMenuTimer

지정 된 지연 팝업 메뉴 단추에 대 한 타이머를 시작 합니다.

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>매개 변수

*pMenuButton*<br/>
진행 지연 타이머를 설정할 메뉴 단추에 대 한 포인터입니다.

*nDelayFactor*<br/>
진행 표준 메뉴 지연 시간 (일반적으로 0.5 초에서 5 초 사이)으로 곱하는 지연 계수 (최소 1)입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md)
