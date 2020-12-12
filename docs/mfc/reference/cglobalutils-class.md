---
description: '자세히 알아보기: CGlobalUtils 클래스'
title: CGlobalUtils 클래스
ms.date: 10/18/2018
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
ms.openlocfilehash: d1e2f096825d34a907afbcdb022c550b94476906
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184103"
---
# <a name="cglobalutils-class"></a>CGlobalUtils 클래스

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CGlobalUtils
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CGlobalUtils::CanBeAttached](#canbeattached)||
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||
|[CGlobalUtils::CheckAlignment](#checkalignment)||
|[CGlobalUtils::CyFromString](#cyfromstring)||
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||
|[CGlobalUtils::FlipRect](#fliprect)||
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||
|[CGlobalUtils::GetWndIcon](#getwndicon)||
|[CGlobalUtils::SetNewParent](#setnewparent)||
|[CGlobalUtils::StringFromCy](#stringfromcy)||
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||

## <a name="remarks"></a>설명

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CGlobalUtils](../../mfc/reference/cglobalutils-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxglobalutils

## <a name="cglobalutilsadjustrecttoworkarea"></a><a name="adjustrecttoworkarea"></a> CGlobalUtils::AdjustRectToWorkArea

```cpp
void AdjustRectToworkArea(
    CRect& rect,
    CRect* pRectDelta = NULL);
```

### <a name="parameters"></a>매개 변수

[in, out] *rect*<br/>
진행 *pRectDelta*<br/>

### <a name="remarks"></a>설명

## <a name="cglobalutilscalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> CGlobalUtils::CalcExpectedDockedRect

```cpp
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,
    CWnd* pWndTodock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>매개 변수

진행 *barContainerManager*<br/>

진행 *pWndTodock*<br/>

진행 *Ptmouse*<br/>

제한이 *rectResult*<br/>

제한이 *Bdrawtab*<br/>

제한이 *Pptargetbar*<br/>

### <a name="remarks"></a>설명

## <a name="cglobalutilscanbeattached"></a><a name="canbeattached"></a> CGlobalUtils:: CanBeAttached

```
BOOL CanBeAttached(CWnd* pWnd) const;
```

### <a name="parameters"></a>매개 변수

진행 *pWnd*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilscanpanebeinfloatingmultipaneframewnd"></a><a name="canpanebeinfloatingmultipaneframewnd"></a> CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd

```
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;
```

### <a name="parameters"></a>매개 변수

진행 *pWnd*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilscheckalignment"></a><a name="checkalignment"></a> CGlobalUtils:: CheckAlignment

```
BOOL CheckAlignment(
    CPoint point,
    CBasePane* pBar,
    int nSensitivity,
    const CDockingManager* pDockManager,
    BOOL bOuterEdge,
    DWORD& dwAlignment,
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,
    LPCRECT lpRectBounds = NULL) const;
```

### <a name="parameters"></a>매개 변수

진행 *point*<br/>

진행 *Pbar*<br/>

진행 *Nsensitivity*<br/>

진행 *pDockManager*<br/>

진행 *bOuterEdge*<br/>

제한이 *Dwalignment*<br/>

진행 *dwEnabledDockBars*<br/>

진행 *lpRectBounds*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilscyfromstring"></a><a name="cyfromstring"></a> CGlobalUtils::CyFromString

```
BOOL CyFromString(
    CY& cy,
    LPCTSTR psz);
```

### <a name="parameters"></a>매개 변수

제한이 *cy*<br/>

진행 *psz*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsdecimalfromstring"></a><a name="decimalfromstring"></a> CGlobalUtils::D ecimalFromString

```
BOOL DecimalFromString(
    DECIMAL& decimal,
    LPCTSTR psz);
```

### <a name="parameters"></a>매개 변수

제한이 *decimal*<br/>

진행 *psz*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsfliprect"></a><a name="fliprect"></a> CGlobalUtils::FlipRect

```cpp
void FlipRect(
    CRect& rect,
    int nDegrees);
```

### <a name="parameters"></a>매개 변수

[in, out] *rect*<br/>
진행 *n도*<br/>

### <a name="remarks"></a>설명

## <a name="cglobalutilsforceadjustlayout"></a><a name="forceadjustlayout"></a> CGlobalUtils::ForceAdjustLayout

```cpp
void ForceAdjustLayout(
    CDockingManager* pDockManager,
    BOOL bForce = FALSE,
    BOOL bForceInvisible = FALSE);
```

### <a name="parameters"></a>매개 변수

[in, out] *pDockManager*<br/>

진행 *Bforce*<br/>

진행 *Bforceinvisible* 않음<br/>

### <a name="remarks"></a>설명

## <a name="cglobalutilsgetdockingmanager"></a><a name="getdockingmanager"></a> CGlobalUtils::GetDockingManager

```
CDockingManager* GetDockingManager(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

진행 *pWnd*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsgetoppositealignment"></a><a name="getoppositealignment"></a> CGlobalUtils::GetOppositeAlignment

```
DWORD GetOppositeAlignment(DWORD dwAlign);
```

### <a name="parameters"></a>매개 변수

진행 *Dwalign*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsgetpaneandalignfrompoint"></a><a name="getpaneandalignfrompoint"></a> CGlobalUtils::GetPaneAndAlignFromPoint

```
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,
    CPoint pt,
    CDockablePane** ppTargetControlBar,
    DWORD& dwAlignment,
    BOOL& bTabArea,
    BOOL& bCaption);
```

### <a name="parameters"></a>매개 변수

진행 *barContainerManager*<br/>

진행 *pt*<br/>

제한이 *Pptargetcontrolbar*<br/>

제한이 *Dwalignment*<br/>

제한이 *Btabarea*<br/>

제한이 *Bcaption*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsgetwndicon"></a><a name="getwndicon"></a> CGlobalUtils::GetWndIcon

```
HICON GetWndIcon(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

진행 *pWnd*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilssetnewparent"></a><a name="setnewparent"></a> CGlobalUtils::SetNewParent

```cpp
void SetNewParent(
    CObList& lstControlBars,
    CWnd* pNewParent,
    BOOL bCheckVisibility = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Lstcontrolbars*<br/>

진행 *pNewParent*<br/>

진행 *Bcheckvisibility*<br/>

### <a name="remarks"></a>설명

## <a name="cglobalutilsstringfromcy"></a><a name="stringfromcy"></a> CGlobalUtils:: StringFromCy

```
BOOL StringFromCy(
    CString& str,
    CY& cy);
```

### <a name="parameters"></a>매개 변수

제한이 *str*<br/>

진행 *cy*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cglobalutilsstringfromdecimal"></a><a name="stringfromdecimal"></a> CGlobalUtils:: StringFromDecimal

```
BOOL StringFromDecimal(
    CString& str,
    DECIMAL& decimal);
```

### <a name="parameters"></a>매개 변수

제한이 *str*<br/>

진행 *decimal*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
