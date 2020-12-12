---
description: '자세히 알아보기: CAutoHideDockSite 클래스'
title: CAutoHideDockSite 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 00ac5224d559f84378bd87bd9abe56756a6f4d97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261283"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 클래스

는 `CAutoHideDockSite` [CDockSite 클래스](../../mfc/reference/cdocksite-class.md) 를 확장 하 여 자동 숨기기 도킹 창을 구현 합니다.

## <a name="syntax"></a>구문

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

| 이름 | 설명 |
|-|-|
|Name|설명|
|`CAutoHideDockSite::CAutoHideDockSite`|`CAutoHideDockSite` 개체를 생성합니다.|
|`CAutoHideDockSite::~CAutoHideDockSite`|소멸자|

### <a name="public-methods"></a>Public 메서드

| 이름 | 설명 |
|-|-|
|Name|설명|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|`CAutoHideDockSite`이 창 메뉴에 표시 되는지 여부를 나타냅니다.|
|[CAutoHideDockSite:: CanAcceptPane](#canacceptpane)|기본 창 개체가 [CMFCAutoHideBar 클래스](../../mfc/reference/cmfcautohidebar-class.md)에서 파생 되는지 여부를 확인 합니다.|
|[CAutoHideDockSite::D ockPane](#dockpane)|이 개체에 창을 도킹 `CAuotHideDockSite` 합니다.|
|[CAutoHideDockSite:: GetAlignRect](#getalignrect)|화면 좌표에서 도크 사이트의 크기를 검색 합니다.|
|[CAutoHideDockSite:: RepositionPanes](#repositionpanes)|의 창에 `CAutoHideDockSite` 전역 여백과 단추 간격이 있는 창을 다시 그립니다.|
|[CAutoHideDockSite:: SetOffsetLeft](#setoffsetleft)|도킹 막대 왼쪽의 여백을 설정 합니다.|
|[CAutoHideDockSite:: SetOffsetRight](#setoffsetright)|도킹 막대 오른쪽의 여백을 설정 합니다.|
|[CAutoHideDockSite:: UnSetAutoHideMode](#unsetautohidemode)|의 개체에 대해 [CMFCAutoHideBar:: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) 를 호출 `CAutoHideDockSite` 합니다.|

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|Name|설명|
|[CAutoHideDockSite:: m_nExtraSpace](#m_nextraspace)|도구 모음과 도킹 표시줄 가장자리 사이의 간격 크기를 정의 합니다. 이 공간은 도크 공간의 맞춤에 따라 왼쪽 가장자리 또는 위쪽 가장자리에서 측정 됩니다.|

## <a name="remarks"></a>설명

[CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)를 호출 하면 프레임 워크에서 자동으로 개체를 만듭니다 `CAutoHideDockSite` . 대부분의 경우이 클래스를 직접 인스턴스화하거나 사용 하지 않아도 됩니다.

도킹 막대는 도크 창의 왼쪽과 [CMFCAutoHideButton 클래스](../../mfc/reference/cmfcautohidebutton-class.md)의 왼쪽 사이의 간격입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>예제

다음 예제에서는 개체에서 개체를 검색 하는 방법과 `CAutoHideDockSite` `CMFCAutoHideBar` 도킹 표시줄의 왼쪽 및 오른쪽 여백을 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxautohidedocksite

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a> CAutoHideDockSite:: CanAcceptPane

기본 창이 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 개체 인지 또는에서 파생 되었는지 여부를 확인 `CMFCAutoHideBar` 합니다.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>매개 변수

*pBar*\
진행 프레임 워크에서 테스트 하는 기본 창입니다.

### <a name="return-value"></a>반환 값

*Pbar* 가에서 파생 되 면 TRUE `CMFCAutoHideBar` 이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

기본 창 개체가에서 파생 되는 경우 `CMFCAutoHideBar` 를 포함할 수 있습니다 `CAutoHideDockSite` .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a> CAutoHideDockSite::D ockPane

이 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 개체에 창을 도킹 합니다.

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pWnd*\
진행 프레임 워크가 도킹 하는 창입니다.

*dockMethod*\
진행 창에 대 한 도킹 옵션입니다.

*lpRect*\
진행 도킹 된 창에 대 한 경계를 지정 하는 사각형입니다.

### <a name="remarks"></a>설명

기본 구현에서는 나중에 사용 하기 위해 제공 되는 *dockMethod* 매개 변수를 사용 하지 않습니다.

*LpRect* 가 NULL 인 경우 프레임 워크는 도킹 사이트의 기본 위치에 창을 배치 합니다. 도크 사이트가 가로 인 경우 기본 위치는 도크 사이트의 맨 왼쪽에 있습니다. 그렇지 않으면 기본 위치가 도크 사이트의 맨 위에 있습니다.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a> CAutoHideDockSite:: GetAlignRect

화면 좌표에서 도크 사이트의 크기를 검색 합니다.

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

*직교*\
진행 사각형에 대 한 참조입니다. 메서드는이 사각형에 도크 사이트의 크기를 저장 합니다.

### <a name="remarks"></a>설명

사각형은 오프셋 여백에 맞게 조정 되어 포함 되지 않습니다.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a> CAutoHideDockSite:: m_nExtraSpace

[CAutoHideDockSite 클래스](../../mfc/reference/cautohidedocksite-class.md) 와 [CMFCAutoHideBar 클래스](../../mfc/reference/cmfcautohidebar-class.md) 개체의 가장자리 사이의 공간 크기입니다.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>설명

이에 `CMFCAutoHideBar` 도킹 되 면 `CAutoHideDockSite` 전체 도크 사이트를 점유 하지 않아야 합니다. 이 전역 변수는의 왼쪽 또는 위쪽 테두리와 해당 가장자리 사이의 추가 공백을 제어 합니다 `CMFCAutoHideBar` `CAutoHideDockSite` . 위쪽 또는 왼쪽 가장자리가 사용 되는지 여부는 현재 맞춤에 따라 결정 됩니다.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a> CAutoHideDockSite:: SetOffsetLeft

도킹 막대 왼쪽의 여백을 설정 합니다.

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
진행 새 오프셋입니다.

### <a name="remarks"></a>설명

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 개체는 개체에 정적으로 배치 됩니다 `CAutoHideDockSite` . 즉, 사용자가 개체의 위치를 수동으로 변경할 수 없습니다 `CMFCAutoHideBar` . 메서드는 맨 왼쪽의 왼쪽과의 왼쪽 `SetOffsetLeft` 간 간격을 제어 합니다 `CMFCAutoHideBar` `CAutoHideDockSite` .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a> CAutoHideDockSite:: SetOffsetRight

도킹 막대 오른쪽의 여백을 설정 합니다.

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
진행 새 오프셋입니다.

### <a name="remarks"></a>설명

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 개체는 개체에 정적으로 배치 됩니다 `CAutoHideDockSite` . 즉, 사용자가 개체의 위치를 수동으로 변경할 수 없습니다 `CMFCAutoHideBar` . 메서드는의 오른쪽 `SetOffsetRight` 및 오른쪽 사이의 간격을 제어 합니다 `CMFCAutoHideBar` `CAutoHideDockSite` .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a> CAutoHideDockSite:: RepositionPanes

[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)에서 창을 다시 그립니다.

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>매개 변수

*rectNewClientArea*\
진행 예약 된 값입니다.

### <a name="remarks"></a>설명

기본 구현에서는 *rectNewClientArea* 를 사용 하지 않습니다. 전역 도구 모음 여백과 단추 간격으로 창을 다시 그립니다.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a> CAutoHideDockSite:: UnSetAutoHideMode

도크 사이트의 개체에 대해 [CMFCAutoHideBar:: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) 를 호출 합니다.

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>매개 변수

*pAutoHideToolbar*\
진행 에 있는 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 개체 창에 대 한 포인터 `CAutoHideDockSite` 입니다.

### <a name="remarks"></a>설명

이 메서드는 *pAutoHideToolbar* 을 포함 하는 행을 검색 합니다. 해당 `CMFCAutoHideBar.UnSetAutoHideMode` 행의 모든 개체에 대해를 호출 `CMFCAutoHideBar` 합니다. *PAutoHideToolbar* 를 찾을 수 없거나 NULL 인 경우이 메서드 `CMFCAutoHideBar.UnSetAutoHideMode` 는의 모든 개체에 대해를 호출 `CMFCAutoHideBar` `CAutoHideDockSite` 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite 클래스](../../mfc/reference/cdocksite-class.md)
