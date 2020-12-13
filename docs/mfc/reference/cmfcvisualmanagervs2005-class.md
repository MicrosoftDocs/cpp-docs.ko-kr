---
description: '자세히 알아보기: CMFCVisualManagerVS2005 클래스'
title: CMFCVisualManagerVS2005 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetDockingTabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetMDITabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetPropertyGridGroupColor
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetTabFrameColors
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawCaptionButton
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawPaneCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawSeparator
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawTab
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawToolBoxFrame
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnEraseTabsArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillHighlightedArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillMiniFrameCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnUpdateSystemColors
helpviewer_keywords:
- CMFCVisualManagerVS2005 [MFC], GetDockingTabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetMDITabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetPropertyGridGroupColor
- CMFCVisualManagerVS2005 [MFC], GetTabFrameColors
- CMFCVisualManagerVS2005 [MFC], HasOverlappedAutoHideButtons
- CMFCVisualManagerVS2005 [MFC], OnDrawAutoHideButtonBorder
- CMFCVisualManagerVS2005 [MFC], OnDrawCaptionButton
- CMFCVisualManagerVS2005 [MFC], OnDrawPaneCaption
- CMFCVisualManagerVS2005 [MFC], OnDrawSeparator
- CMFCVisualManagerVS2005 [MFC], OnDrawTab
- CMFCVisualManagerVS2005 [MFC], OnDrawToolBoxFrame
- CMFCVisualManagerVS2005 [MFC], OnEraseTabsArea
- CMFCVisualManagerVS2005 [MFC], OnFillAutoHideButtonBackground
- CMFCVisualManagerVS2005 [MFC], OnFillHighlightedArea
- CMFCVisualManagerVS2005 [MFC], OnFillMiniFrameCaption
- CMFCVisualManagerVS2005 [MFC], OnUpdateSystemColors
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
ms.openlocfilehash: 74192e1c0e4c7189a64d872bcc1761cf21e5365d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331646"
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 클래스

`CMFCVisualManagerVS2005` 응용 프로그램에 Microsoft Visual Studio 2005 모양을 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](#getdockingtabsborderssize)|프레임 워크는 도킹 되 고 탭 되는 창을 그릴 때이 메서드를 호출 합니다. [Cmfcvisualmanager:: GetDockingTabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](#getmditabsborderssize)|프레임 워크는이 메서드를 호출 하 여 창을 그리기 전에 MDITabs 창의 테두리 크기를 확인 합니다. [Cmfcvisualmanager:: GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)를 재정의 합니다.|
|[CMFCVisualManagerVS2005:: GetPropertyGridGroupColor](#getpropertygridgroupcolor)|[CMFCVisualManagerOffice2003:: GetPropertyGridGroupColor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::GetTabFrameColors](#gettabframecolors)|[CMFCVisualManagerOffice2003:: GetTabFrameColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](#hasoverlappedautohidebuttons)|현재 비주얼 관리자에서 자동 숨기기 단추가 겹치는 지 여부를 반환 합니다. [Cmfcvisualmanager:: HasOverlappedAutoHideButtons](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|[CMFCVisualManagerOffice2003:: OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder)를 재정의 합니다.|
|[CMFCVisualManagerVS2005:: OnDrawCaptionButton](#ondrawcaptionbutton)|( `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`을 재정의합니다.)|
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](#ondrawpanecaption)|[CMFCVisualManagerOffice2003:: OnDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption)를 재정의 합니다.|
|[CMFCVisualManagerVS2005:: OnDrawSeparator](#ondrawseparator)|[CMFCVisualManagerOffice2003:: OnDrawSeparator](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator)를 재정의 합니다.|
|[CMFCVisualManagerVS2005:: OnDrawTab](#ondrawtab)|[CMFCVisualManagerOffice2003:: OnDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab)을 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](#ondrawtoolboxframe)|[Cmfcvisualmanager:: OnDrawToolBoxFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnEraseTabsArea](#onerasetabsarea)|[CMFCVisualManagerOffice2003:: OnEraseTabsArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|[CMFCVisualManagerOffice2003:: OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](#onfillhighlightedarea)|[CMFCVisualManagerOffice2003:: OnFillHighlightedArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea)를 재정의 합니다.|
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](#onfillminiframecaption)|( `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`을 재정의합니다.)|
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](#onupdatesystemcolors)|[CMFCVisualManagerOffice2003:: OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors)를 재정의 합니다.|

## <a name="remarks"></a>설명

CMFCVisualManagerVS2005 클래스를 사용 하 여 Microsoft Visual Studio 2005와 비슷하게 응용 프로그램의 시각적 모양을 변경 합니다.

이 클래스의 모든 멤버는이 클래스의 상위 항목인 [Cmfcvisualmanager 클래스](../../mfc/reference/cmfcvisualmanager-class.md)에서 파생 되는 가상 함수입니다.

## <a name="example"></a>예제

다음 예제에서는 visual manager VS 2005를 사용 하는 방법을 보여 줍니다. 이 코드 조각은 [데스크톱 경고 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)

[CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxvisualmanagervs2005

## <a name="cmfcvisualmanagervs2005getdockingtabsborderssize"></a><a name="getdockingtabsborderssize"></a> CMFCVisualManagerVS2005::GetDockingTabsBordersSize

```
virtual int GetDockingTabsBordersSize();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005getmditabsborderssize"></a><a name="getmditabsborderssize"></a> CMFCVisualManagerVS2005::GetMDITabsBordersSize

```
virtual int GetMDITabsBordersSize();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a> CMFCVisualManagerVS2005:: GetPropertyGridGroupColor

```
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```

### <a name="parameters"></a>매개 변수

진행 *pPropList*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005gettabframecolors"></a><a name="gettabframecolors"></a> CMFCVisualManagerVS2005::GetTabFrameColors

```
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,
    COLORREF& clrDark,
    COLORREF& clrBlack,
    COLORREF& clrHighlight,
    COLORREF& clrFace,
    COLORREF& clrDarkShadow,
    COLORREF& clrLight,
    CBrush*& pbrFace,
    CBrush*& pbrBlack);
```

### <a name="parameters"></a>매개 변수

진행 *pTabWnd*<br/>
진행 *Clrdark*<br/>
진행 *Clrblack*<br/>
진행 *Clrhighlight*<br/>
진행 *Clrface*<br/>
진행 *clrDarkShadow*<br/>
진행 *Clrlight*<br/>
진행 *pbrFace*<br/>
진행 *pbrBlack*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005hasoverlappedautohidebuttons"></a><a name="hasoverlappedautohidebuttons"></a> CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons

```
virtual BOOL HasOverlappedAutoHideButtons() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a> CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder

```
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *rectBounds*<br/>
진행 *rectBorderSize*<br/>
진행 *Pbutton*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawcaptionbutton"></a><a name="ondrawcaptionbutton"></a> CMFCVisualManagerVS2005:: OnDrawCaptionButton

```
virtual void OnDrawCaptionButton(
    CDC* pDC,
    CMFCCaptionButton* pButton,
    BOOL bActive,
    BOOL bHorz,
    BOOL bMaximized,
    BOOL bDisabled,
    int nImageID = -1);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *Pbutton*<br/>
진행 *Bactive*<br/>
진행 *Bhorz*<br/>
진행 *Bmaximized*<br/>
진행 *Bdisabled*<br/>
진행 *nImageID*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawpanecaption"></a><a name="ondrawpanecaption"></a> CMFCVisualManagerVS2005::OnDrawPaneCaption

```
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,
    CDockablePane* pBar,
    BOOL bActive,
    CRect rectCaption,
    CRect rectButtons);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *Pbar*<br/>
진행 *Bactive*<br/>
진행 *rectCaption*<br/>
진행 *rectButtons*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawseparator"></a><a name="ondrawseparator"></a> CMFCVisualManagerVS2005:: OnDrawSeparator

```
virtual void OnDrawSeparator(
    CDC* pDC,
    CBasePane* pBar,
    CRect rect,
    BOOL bIsHoriz);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *Pbar*<br/>
[in] *rect*<br/>
진행 *bIsHoriz*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawtab"></a><a name="ondrawtab"></a> CMFCVisualManagerVS2005:: OnDrawTab

```
virtual void OnDrawTab(
    CDC* pDC,
    CRect rectTab,
    int iTab,
    BOOL bIsActive,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *rectTab*<br/>
[in] *iTab*<br/>
진행 *bIsActive*<br/>
진행 *pTabWnd*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005ondrawtoolboxframe"></a><a name="ondrawtoolboxframe"></a> CMFCVisualManagerVS2005::OnDrawToolBoxFrame

```
virtual void OnDrawToolBoxFrame(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
[in] *rect*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005onerasetabsarea"></a><a name="onerasetabsarea"></a> CMFCVisualManagerVS2005::OnEraseTabsArea

```
virtual void OnEraseTabsArea(
    CDC* pDC,
    CRect rect,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
[in] *rect*<br/>
진행 *pTabWnd*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a> CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground

```
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,
    CRect rect,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
[in] *rect*<br/>
진행 *Pbutton*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a> CMFCVisualManagerVS2005::OnFillHighlightedArea

```
virtual void OnFillHighlightedArea(
    CDC* pDC,
    CRect rect,
    CBrush* pBrush,
    CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
[in] *rect*<br/>
진행 *Pbrush*<br/>
진행 *Pbutton*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005onfillminiframecaption"></a><a name="onfillminiframecaption"></a> CMFCVisualManagerVS2005::OnFillMiniFrameCaption

```
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,
    CRect rectCaption,
    CPaneFrameWnd* pFrameWnd,
    BOOL bActive);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
진행 *rectCaption*<br/>
진행 *pFrameWnd*<br/>
진행 *Bactive*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagervs2005onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a> CMFCVisualManagerVS2005::OnUpdateSystemColors

```
virtual void OnUpdateSystemColors();
```

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 클래스](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerOfficeXP 클래스](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)<br/>
[CMFCVisualManagerWindows 클래스](../../mfc/reference/cmfcvisualmanagerwindows-class.md)<br/>
[CMFCVisualManagerOffice2003 클래스](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)
