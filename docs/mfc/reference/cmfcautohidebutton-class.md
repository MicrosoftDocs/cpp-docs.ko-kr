---
description: '자세히 알아보기: CMFCAutoHideButton 클래스'
title: CMFCAutoHideButton 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 9d100417193ea8a757b02b9cc8fad0cdedf668f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336574"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton 클래스

숨기도록 구성된 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 를 표시하거나 숨기는 단추입니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|자동 숨기기 단추를 만들고 초기화합니다.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|자동 숨기기 단추의 맞춤을 검색합니다.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|자동 숨기기 단추와 연결 된 [CDockablePane](../../mfc/reference/cdockablepane-class.md) 개체를 반환 합니다.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|자동 숨기기 단추의 크기를 결정합니다.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|자동 숨기기 단추에 대한 텍스트 레이블의 크기를 반환합니다.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|자동 숨기기 단추를 강조 표시합니다.|
|[CMFCAutoHideButton::IsActive](#isactive)|자동 숨기기 단추가 활성 상태인지를 나타냅니다.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|자동 숨기기 단추의 강조 표시 상태를 반환합니다.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|자동 숨기기 단추가 가로 또는 세로로 표시되는지를 결정합니다.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|단추의 표시 여부를 나타냅니다.|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|자동 숨기기 단추를 그릴 때 프레임워크에서 이 메서드를 호출합니다.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|자동 숨기기 단추의 테두리를 그릴 때 프레임워크에서 이 메서드를 호출합니다.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|자동 숨기기 단추의 배경을 채울 때 프레임워크에서 이 메서드를 호출합니다.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|연결 된 [CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)를 표시 하거나 숨깁니다.|
|[CMFCAutoHideButton::ShowButton](#showbutton)|자동 숨기기 단추를 표시하거나 숨깁니다.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>설명

만들어질 때 개체는 `CMFCAutoHideButton` [CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)에 연결 됩니다. 사용자가 `CMFCAutoHideButton` 개체를 조작할 때 `CDockablePane` 개체가 숨겨지거나 표시됩니다.

기본적으로 프레임워크에서는 사용자가 자동 숨기기를 설정할 때 자동으로 `CMFCAutoHideButton`을 만듭니다. 프레임워크에서는 `CMFCAutoHideButton` 클래스 대신 사용자 지정 UI 클래스의 요소를 만들 수 있습니다. 프레임워크에서 사용해야 하는 사용자 지정 UI 클래스를 지정하려면 사용자 지정 UI 클래스와 같은 정적 멤버 변수 `CMFCAutoHideBar::m_pAutoHideButtonRTS`를 설정합니다. 기본적으로 이 변수는 `CMFCAutoHideButton`로 설정됩니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCAutoHideButton` 개체를 생성하고 `CMFCAutoHideButton` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 예제에서는 `Create` 메서드를 사용하여 `CMFCAutoHideButton` 개체를 초기화하고, 연결된 `CDockablePane` 클래스를 표시하고, 자동 숨기기 단추를 표시하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>요구 사항

**헤더:** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a> CMFCAutoHideButton:: BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a> CMFCAutoHideButton:: Create

자동 숨기기 단추를 만들고 초기화 합니다.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>매개 변수

*pParentBar*<br/>
진행 부모 도구 모음에 대 한 포인터입니다.

*pAutoHideWnd*<br/>
진행 [CDockablePane](../../mfc/reference/cdockablepane-class.md) 개체에 대 한 포인터입니다. 이 자동 숨기기 단추는을 숨기고 표시 `CDockablePane` 합니다.

*dwAlignment*<br/>
진행 주 프레임 창과 단추의 맞춤을 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

개체를 만들 때는 `CMFCAutoHideButton` 자동 숨기기 단추를 특정와 연결 해야 합니다 `CDockablePane` . 사용자는 자동 숨기기 단추를 사용 하 여 연결 된을 숨기 거 나 표시할 수 있습니다 `CDockablePane` .

*Dwalignment* 매개 변수는 자동 숨기기 단추가 응용 프로그램에 상주 하는 위치를 나타냅니다. 이 매개 변수는 다음 값 중 하나가 될 수 있습니다.

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a> CMFCAutoHideButton:: GetAlignment

자동 숨기기 단추의 맞춤을 검색합니다.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>반환 값

자동 숨기기 단추의 현재 맞춤을 포함 하는 DWORD 값입니다.

### <a name="remarks"></a>설명

자동 숨기기 단추의 맞춤은 응용 프로그램에 단추가 있는 위치를 나타냅니다. 다음 값 중 하나일 수 있습니다.

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a> CMFCAutoHideButton:: GetAutoHideWindow

자동 숨기기 단추와 연결 된 [CDockablePane](../../mfc/reference/cdockablepane-class.md) 개체를 반환 합니다.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>반환 값

연결 된 개체에 대 한 포인터 `CDockablePane` 입니다.

### <a name="remarks"></a>설명

자동 숨기기 단추를와 연결 하려면를 `CDockablePane` `CDockablePane` [CMFCAutoHideButton:: Create](#create) 메서드에 매개 변수로 전달 합니다.

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a> CMFCAutoHideButton:: GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a> CMFCAutoHideButton:: GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a> CMFCAutoHideButton:: GetSize

자동 숨기기 단추의 크기를 결정합니다.

```
CSize GetSize() const;
```

### <a name="return-value"></a>반환 값

`CSize`단추 크기를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

계산 된 크기는 자동 숨기기 단추의 테두리 크기를 포함 합니다.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a> CMFCAutoHideButton:: GetTextSize

자동 숨기기 단추에 대한 텍스트 레이블의 크기를 반환합니다.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>반환 값

자동 숨기기 단추의 텍스트 크기를 포함 하는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a> CMFCAutoHideButton:: IsActive

자동 숨기기 단추가 활성 상태인지를 나타냅니다.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>반환 값

자동 숨기기 단추가 활성화 되어 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

연결 된 [CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md) 창이 표시 되 면 자동 숨기기 단추가 활성화 됩니다.

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a> CMFCAutoHideButton:: IsHorizontal

자동 숨기기 단추가 가로 또는 세로로 표시되는지를 결정합니다.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>반환 값

단추가 가로 인 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크는 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) 개체를 만들 때 해당 개체의 방향을 설정 합니다.  [CMFCAutoHideButton:: Create](#create) 메서드에서 *dwalignment* 매개 변수를 사용 하 여 방향을 제어할 수 있습니다.

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a> CMFCAutoHideButton:: IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a> CMFCAutoHideButton:: IsVisible

자동 숨기기 단추가 표시 되는지 여부를 나타냅니다.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>반환 값

단추가 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a> CMFCAutoHideButton:: OnDraw

자동 숨기기 단추를 그릴 때 프레임워크에서 이 메서드를 호출합니다.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 자동 숨기기 단추의 모양을 사용자 지정 하려면에서 파생 된 새 클래스를 만듭니다 `CMFCAutoHideButton` . 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a> CMFCAutoHideButton:: OnDrawBorder

자동 숨기기 단추의 테두리를 그릴 때 프레임워크에서 이 메서드를 호출합니다.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectBounds*<br/>
진행 자동 숨기기 단추의 경계 사각형입니다.

*rectBorderSize*<br/>
진행 자동 숨기기 단추의 각 면에 대 한 테두리 두께입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 각 자동 숨기기 단추의 테두리를 사용자 지정 하려면에서 파생 된 새 클래스를 만듭니다 `CMFCAutoHideButton` . 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a> CMFCAutoHideButton:: OnFillBackground

자동 숨기기 단추의 배경을 채울 때 프레임워크에서 이 메서드를 호출합니다.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 자동 숨기기 단추의 경계 사각형입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 자동 숨기기 단추의 배경을 사용자 지정 하려면에서 파생 된 새 클래스를 만듭니다 `CMFCAutoHideButton` . 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a> CMFCAutoHideButton:: ShowAttachedWindow

연결 된 [CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)를 표시 하거나 숨깁니다.

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 이 메서드가 연결 된를 표시 하는지 여부를 지정 하는 부울입니다 `CDockablePane` .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a> CMFCAutoHideButton:: ShowButton

자동 숨기기 단추를 표시하거나 숨깁니다.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 자동 숨기기 단추를 표시할지 여부를 지정 하는 부울입니다.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a> CMFCAutoHideButton:: Move

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>매개 변수

진행 *Noffset*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a> CMFCAutoHideButton:: ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pnewbar*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a> CMFCAutoHideButton:: UnSetAutoHideMode

자동 숨기기 모드를 사용하지 않도록 설정합니다.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>매개 변수

*pFirstBarInGroup*<br/>
진행 그룹의 첫 번째 막대에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a> CMFCAutoHideButton:: HighlightButton

자동 숨기기 단추를 강조 표시 합니다.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>매개 변수

*bHighlight*<br/>
새 자동 숨기기 단추 상태를 지정 합니다. TRUE 이면 단추가 강조 표시 되 고 FALSE 이면 단추가 강조 표시 되지 않습니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a> CMFCAutoHideButton:: IsHighlighted

자동 숨기기 단추의 강조 상태를 반환 합니다.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>반환 값

자동 숨기기 단추가 강조 표시 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar 클래스](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite 클래스](../../mfc/reference/cautohidedocksite-class.md)
