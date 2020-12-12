---
description: '자세히 알아보기: CMFCDropDownToolBar 클래스'
title: CMFCDropDownToolBar 클래스
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 158562829cb5bbebfb9a858d34751c56bdf46ed8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293991"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 클래스

사용자가 최상위 도구 모음 단추를 누르고 있을 때 나타나는 도구 모음입니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCDropDownToolBar:: AllowShowOnPaneMenu](#allowshowonpanemenu)|( `CPane::AllowShowOnPaneMenu`을 재정의합니다.)|
|[CMFCDropDownToolBar:: LoadBitmap](#loadbitmap)|[Cmfctoolbar:: LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap)을 재정의 합니다.|
|[CMFCDropDownToolBar:: LoadToolBar](#loadtoolbar)|[Cmfctoolbar:: LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)를 재정의 합니다.|
|[CMFCDropDownToolBar:: OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar:: OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar:: OnSendCommand](#onsendcommand)|( `CMFCToolBar::OnSendCommand`을 재정의합니다.)|
|[CMFCDropDownToolBar:: OnUpdateCmdUI](#onupdatecmdui)|[Cmfctoolbar:: OnUpdateCmdUI](cmfctoolbar-class.md)를 재정의 합니다.|

### <a name="remarks"></a>설명

`CMFCDropDownToolBar`개체는 도구 모음의 시각적 모양을 팝업 메뉴의 동작과 결합 합니다. 사용자가 드롭다운 도구 모음 단추를 누르고 있으면 ( [CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)참조) 드롭다운 도구 모음이 나타나고 사용자는 드롭다운 도구 모음에서 단추를 선택 하 고 마우스 단추를 놓으면 드롭다운 도구 모음에서 단추를 선택할 수 있습니다. 사용자가 드롭다운 도구 모음에서 단추를 선택 하면 해당 단추가 최상위 도구 모음에 현재 단추로 표시 됩니다.

드롭다운 도구 모음을 사용자 지정 하거나 도킹할 수 없으며 분리 상태를 사용할 수 없습니다.

다음 그림은 개체를 보여 줍니다 `CMFCDropDownToolBar` .

![CMFCDropDownToolbar의 예제](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDownToolbar의 예제")

`CMFCDropDownToolBar`일반 도구 모음을 만드는 것과 같은 방법으로 개체를 만듭니다 ( [Cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md)참조).

드롭다운 도구 모음을 부모 도구 모음에 삽입 하려면 다음을 수행 합니다.

1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.

2. `CMFCDropDownToolBarButton`드롭다운 도구 모음이 포함 된 개체를 만듭니다. 자세한 내용은 [CMFCDropDownToolbarButton:: CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)를 참조 하세요.

3. `CMFCDropDownToolBarButton` [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)를 사용 하 여 더미 단추를 개체로 바꿉니다.

도구 모음 단추에 대 한 자세한 내용은 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)를 참조 하세요. 드롭다운 도구 모음에 대 한 예제는 샘플 프로젝트 VisualStudioDemo를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `Create` `CMFCDropDownToolBar` . 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a> CMFCDropDownToolBar:: AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a> CMFCDropDownToolBar:: LoadBitmap

애플리케이션 리소스에서 도구 모음 이미지를 로드합니다.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>매개 변수

*uiResID*<br/>
진행 핫 도구 모음 이미지를 참조 하는 비트맵의 리소스 ID입니다.

*uiColdResID*<br/>
진행 콜드 도구 모음 이미지를 참조 하는 비트맵의 리소스 ID입니다.

*uiMenuResID*<br/>
진행 일반 메뉴 이미지를 참조 하는 비트맵의 리소스 ID입니다.

*인해*<br/>
진행 도구 모음을 잠그려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*uiDisabledResID*<br/>
진행 비활성화 된 도구 모음 이미지를 참조 하는 비트맵의 리소스 ID입니다.

*uiMenuDisabledResID*<br/>
진행 비활성화 된 메뉴 이미지를 참조 하는 비트맵의 리소스 ID입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 0이 아니고, 실패하면 0입니다.

### <a name="remarks"></a>설명

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 메서드는 이 메서드를 호출하여 도구 모음과 관련된 이미지를 로드합니다. 이미지 리소스의 사용자 지정 로드를 수행하려면 이 메서드를 재정의합니다.

`LoadBitmapEx` 메서드를 호출하여 도구 모음을 만든 후 추가 이미지를 로드합니다.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a> CMFCDropDownToolBar:: LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>매개 변수

진행 *uiResID*<br/>

진행 *uiColdResID*<br/>

진행 *uiMenuResID*<br/>

진행 *BOOL*<br/>

진행 *uiDisabledResID*<br/>

진행 *uiMenuDisabledResID*<br/>

진행 *uiHotResID*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a> CMFCDropDownToolBar:: OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

진행 *Nflags*<br/>

진행 *point*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a> CMFCDropDownToolBar:: OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

진행 *Nflags*<br/>

진행 *point*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a> CMFCDropDownToolBar:: OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>매개 변수

진행 *Pbutton*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCDropDownToolBar:: OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>매개 변수

진행 *Ptarget*<br/>

진행 *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar:: Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
