---
description: '자세히 알아보기: CMFCReBar 클래스'
title: CMFCReBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: fcfad39ddb9c5f3bdacc5a06ebb65d22bc8c7a4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289831"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 클래스

`CMFCReBar`개체는 rebar 컨트롤의 레이아웃, 지 속성 및 상태 정보를 제공 하는 컨트롤 막대입니다.
자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCReBar : public CPane
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCReBar:: AddBar](#addbar)|크기 조정 막대에 밴드를 추가 합니다.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)를 재정의 합니다.)|
|[CMFCReBar:: CanFloat](#canfloat)|[Cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)를 재정의 합니다.|
|[CMFCReBar:: Create](#create)|Rebar 컨트롤을 만들고이를 개체에 연결 `CMFCReBar` 합니다.|
|[CMFCReBar:: EnableDocking](#enabledocking)|[Cbasepane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)을 재정의 합니다.|
|[CMFCReBar:: Getre바 밴드 Infosize](#getrebarbandinfosize)||
|[CMFCReBar:: GetReBarCtrl](#getrebarctrl)|기본 [Cre바 ctrl](../../mfc/reference/crebarctrl-class.md) 공용 컨트롤에 직접 액세스할 수 있습니다.|
|[CMFCReBar:: OnShowControlBarMenu](#onshowcontrolbarmenu)|[Cpane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)를 재정의 합니다.|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|( [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)를 재정의 합니다.)|
|[CMFCReBar:: OnUpdateCmdUI](#onupdatecmdui)|( [Cbasepane:: OnUpdateCmdUI](cbasepane-class.md)를 재정의 합니다.)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|( [Cbasepane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)를 재정의 합니다.)|

## <a name="remarks"></a>설명

`CMFCReBar`개체는 다양 한 자식 창을 포함할 수 있습니다. 여기에는 편집 상자, 도구 모음 및 목록 상자가 포함 됩니다. 크기 조정 막대의 크기를 프로그래밍 방식으로 조정 하거나 사용자가 크기 조정 막대를 끌어 크기 조정 막대를 수동으로 조정할 수 있습니다. Rebar 개체의 배경을 선택한 비트맵으로 설정할 수도 있습니다.

Rebar 개체는 toolbar 개체와 비슷하게 동작 합니다. Rebar 컨트롤은 하나 이상의 밴드를 포함할 수 있으며 각 밴드에는 그리퍼 막대, 비트맵, 텍스트 레이블 및 자식 창이 포함 될 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCReBar` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 rebar 컨트롤을 만들고 여기에 밴드를 추가 하는 방법을 보여 줍니다. 밴드는 내부 도구 모음으로 작동 합니다. 이 코드 조각은 [Rebar 테스트 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cpane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRebar

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a> CMFCReBar:: AddBar

크기 조정 막대에 밴드를 추가 합니다.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in, out] Rebar에 삽입할 자식 창에 대 한 포인터입니다. 참조 된 개체는 **WS_CHILD** 창 스타일을 포함 해야 합니다.

*pszText*<br/>
진행 Rebar에 표시할 텍스트를 지정 합니다. 텍스트가 자식 창의 일부가 아닙니다. 대신 rebar 자체에 표시 됩니다.

*.pbmp*<br/>
[in, out] Rebar 배경에 표시할 비트맵을 지정 합니다.

*dwStyle*<br/>
진행 밴드에 적용할 스타일을 포함 합니다. 밴드 스타일의 전체 목록은 `fStyle` Windows SDK 설명서의 [Re바 밴드 정보](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) 구조에서에 대 한 설명을 참조 하세요.

*clrFore*<br/>
진행 Rebar의 전경색을 나타냅니다.

*clrBack*<br/>
진행 Rebar의 배경색을 나타냅니다.

### <a name="return-value"></a>반환 값

밴드가 rebar에 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcrebarcreate"></a><a name="create"></a> CMFCReBar:: Create

Rebar 컨트롤을 만들어 [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) 개체에 연결 합니다.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
[in, out] 이 rebar 컨트롤의 부모 창에 대 한 포인터입니다.

*dwCtrlStyle*<br/>
진행 Rebar 컨트롤의 스타일을 지정 합니다. 기본 스타일 값은 **RBS_BANDBORDERS** 입니다 .이 값은 좁은 선을 표시 하 여 rebar 컨트롤에서 인접 한 밴드를 분리 합니다. 유효한 스타일 목록은 Windows SDK 설명서에서 [Rebar 컨트롤 스타일](/windows/win32/Controls/rebar-control-styles) 을 참조 하세요.

*dwStyle*<br/>
진행 Rebar 컨트롤의 창 스타일입니다. 유효한 스타일 목록은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*nID*<br/>
진행 Rebar의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

Rebar가 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a> CMFCReBar:: GetReBarCtrl

`CReBarCtrl`개체에 대 한 기본 공용 컨트롤에 대 한 직접 액세스를 제공 합니다 `CMFCReBar` .

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>반환 값

내부 개체에 대 한 참조 `CReBarCtrl` 입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 rebar를 사용자 지정할 때 Windows rebar 공용 컨트롤 기능을 활용 합니다.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

진행 *Bstretch*<br/>
진행 *Bhorz*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a> CMFCReBar:: CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a> CMFCReBar:: EnableDocking

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>매개 변수

진행 *dwDockStyle*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a> CMFCReBar:: Getre바 밴드 Infosize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a> CMFCReBar:: OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>매개 변수

[in] *CPoint*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a> CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>매개 변수

진행 *point*<br/>
진행 *Pti*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCReBar:: OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>매개 변수

진행 *Ptarget*<br/>
진행 *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a> CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>매개 변수

진행 *Dwalignment*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cre바 Ctrl 클래스](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane 클래스](../../mfc/reference/cpane-class.md)
