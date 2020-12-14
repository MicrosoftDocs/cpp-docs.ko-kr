---
description: '자세히 알아보기: CMFCColorPopupMenu 클래스'
title: CMFCColorPopupMenu 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: 1668064fa253ea17bdce1ba393bd892ef8769b71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211832"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 클래스

사용자가 문서 또는 응용 프로그램에서 색을 선택 하는 데 사용 하는 팝업 메뉴를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|`CMFCColorPopupMenu` 개체를 생성합니다.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|도킹 가능한 분리 색 막대를 만듭니다. [CMFCPopupMenu:: CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)를 재정의 합니다.|
|[CMFCColorPopupMenu:: GetMenuBar](#getmenubar)|팝업 메뉴 안에 포함 된 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 를 반환 합니다. [CMFCPopupMenu:: GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)를 재정의 합니다.|
|`CMFCColorPopupMenu::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|포함 된 개체의 속성 표 컨트롤 개체를 설정 합니다 `CMFCColorBar` .|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|`m_bEnabledInCustomizeMode`|색 막대를 표시할지 여부를 결정 하는 부울 값입니다.|
|`m_wndColorBar`|`CMFCColorBar`색 선택 항목을 제공 하는 개체입니다.|

### <a name="remarks"></a>설명

이 클래스는 클래스의 팝업 메뉴 기능을 상속 `CMFCPopupMenu` 하 고 `CMFCColorBar` 색 선택 기능을 제공 하는 개체를 관리 합니다. 도구 모음 프레임 워크가 사용자 지정 모드에 있고 `m_bEnabledInCustomizeMode` 멤버가 FALSE로 설정 된 경우 색 막대 개체는 표시 되지 않습니다. 사용자 지정 모드에 대 한 자세한 내용은 [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) 를 참조 하세요.

에 대 한 자세한 내용은 `CMFCColorBar` [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcolorpopupmenu

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a> CMFCColorPopupMenu::CMFCColorPopupMenu

`CMFCColorPopupMenu` 개체를 생성합니다.

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*분판*<br/>
진행 팝업 메뉴에 프레임 워크가 표시 하는 색의 배열입니다.

*color*<br/>
진행 기본 선택 된 색입니다.

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

*nHorzDockRows*<br/>
진행 색 막대가 가로로 도킹 될 때 표시 되는 행의 수입니다.

*nVertDockColumns*<br/>
진행 세로 방향으로 도킹할 때 색 막대의 열 수입니다.

*colorAutomatic*<br/>
진행 자동 단추를 클릭할 때 프레임 워크에서 적용 하는 기본 색입니다.

*uiCommandID*<br/>
진행 색 막대 컨트롤 명령 ID입니다.

*bStdColorDlg*<br/>
진행 표준 시스템 색 대화 상자 또는 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 대화 상자를 표시할지 여부를 나타내는 부울입니다.

*pParentBtn*<br/>
진행 부모 단추에 대 한 포인터입니다.

*nID*<br/>
진행 명령 ID입니다.

### <a name="remarks"></a>설명

오버 로드 된 각 생성자는 `m_bEnabledInCustomizeMode` 멤버를 FALSE로 설정 합니다.

### <a name="example"></a>예제

다음 예제에서는 개체를 생성 하는 방법을 보여 줍니다 `CMFCColorPopupMenu` .

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a> CMFCColorPopupMenu::CreateTearOffBar

도킹 가능한 분리 색 막대를 만듭니다.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*pWndMain*\
진행 분리 막대의 부모 창에 대 한 포인터입니다.

*uiID*\
진행 분리 된 표시줄의 명령 ID입니다.

*lpszName*\
진행 분리 된 표시줄의 창 텍스트입니다.

### <a name="return-value"></a>반환 값

새 분리 컨트롤 막대 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 개체를 만들어 [cpane 클래스](../../mfc/reference/cpane-class.md) 포인터로 캐스팅 합니다. [MFC 클래스 개체의 형식 캐스팅](../../mfc/reference/type-casting-of-mfc-class-objects.md)에 설명 된 캐스팅 매크로 중 하나를 사용 하 여이 값을 [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 포인터로 다시 캐스팅할 수 있습니다.

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a> CMFCColorPopupMenu:: GetMenuBar

팝업 메뉴 안에 포함 된 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 를 반환 합니다.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>반환 값

포함 된에 대 한 포인터 `CMFCPopupMenuBar` 입니다.

### <a name="remarks"></a>설명

색 팝업 메뉴에는 포함 된 [CMFCPopupMenuBar 클래스](../../mfc/reference/cmfcpopupmenubar-class.md) 개체가 있습니다. 응용 프로그램에서 다른 포함 된 형식을 사용 하는 경우 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a> CMFCColorPopupMenu::SetPropList

포함 된 개체의 속성 표 컨트롤 개체를 설정 합니다 `CMFCColorBar` .

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>매개 변수

*pWndList*<br/>
진행 속성 표 컨트롤 개체에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
