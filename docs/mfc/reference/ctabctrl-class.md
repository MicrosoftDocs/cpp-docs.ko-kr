---
description: '자세히 알아보기: CTabCtrl 클래스'
title: CTabCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: 363e97ec848976b78b1c75b70997ff6f4b4b5c36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318574"
---
# <a name="ctabctrl-class"></a>CTabCtrl 클래스

Windows의 공용 탭 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CTabCtrl:: CTabCtrl](#ctabctrl)|`CTabCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTabCtrl:: AdjustRect](#adjustrect)|창 사각형이 지정 된 탭 컨트롤의 표시 영역을 계산 하거나 지정 된 표시 영역에 해당 하는 창 사각형을 계산 합니다.|
|[CTabCtrl:: Create](#create)|탭 컨트롤을 만들어 개체의 인스턴스에 연결 `CTabCtrl` 합니다.|
|[CTabCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 탭 컨트롤을 만들고 개체의 인스턴스에 연결 `CTabCtrl` 합니다.|
|[CTabCtrl::D eleteAllItems](#deleteallitems)|탭 컨트롤에서 모든 항목을 제거 합니다.|
|[CTabCtrl::D eleteItem](#deleteitem)|탭 컨트롤에서 항목을 제거 합니다.|
|[CTabCtrl::D eselectAll](#deselectall)|탭 컨트롤의 항목을 다시 설정 하 여 눌린 항목을 지웁니다.|
|[CTabCtrl::D rawItem](#drawitem)|지정 된 탭 컨트롤 항목을 그립니다.|
|[CTabCtrl:: GetCurFocus](#getcurfocus)|탭 컨트롤의 현재 포커스가 있는 탭을 검색 합니다.|
|[CTabCtrl:: GetCurSel](#getcursel)|탭 컨트롤에서 현재 선택 된 탭을 결정 합니다.|
|[CTabCtrl:: GetExtendedStyle](#getextendedstyle)|탭 컨트롤에 현재 사용 되 고 있는 확장 스타일을 검색 합니다.|
|[CTabCtrl:: GetImageList](#getimagelist)|탭 컨트롤과 연결 된 이미지 목록을 검색 합니다.|
|[CTabCtrl:: GetItem](#getitem)|탭 컨트롤의 탭에 대 한 정보를 검색 합니다.|
|[CTabCtrl:: GetItemCount](#getitemcount)|탭 컨트롤에서 탭 수를 검색합니다.|
|[CTabCtrl:: GetItemRect](#getitemrect)|탭 컨트롤의 탭에 대 한 경계 사각형을 검색 합니다.|
|[CTabCtrl:: GetItemState](#getitemstate)|표시 된 탭 컨트롤 항목의 상태를 검색 합니다.|
|[CTabCtrl:: GetRowCount](#getrowcount)|탭 컨트롤에서 현재 행 수를 검색 합니다.|
|[CTabCtrl:: GetToolTips](#gettooltips)|탭 컨트롤과 연결 된 도구 설명 컨트롤의 핸들을 검색 합니다.|
|[CTabCtrl:: HighlightItem](#highlightitem)|탭 항목의 강조 상태를 설정 합니다.|
|[CTabCtrl:: System.windows.media.visualtreehelper.hittest](#hittest)|지정 된 화면 위치에 있는 탭 (있는 경우)을 결정 합니다.|
|[CTabCtrl:: InsertItem](#insertitem)|탭 컨트롤에 새 탭을 삽입 합니다.|
|[CTabCtrl:: RemoveImage](#removeimage)|탭 컨트롤의 이미지 목록에서 이미지를 제거 합니다.|
|[CTabCtrl:: SetCurFocus](#setcurfocus)|탭 컨트롤에서 지정 된 탭으로 포커스를 설정 합니다.|
|[CTabCtrl:: SetCurSel](#setcursel)|탭 컨트롤에서 탭을 선택 합니다.|
|[CTabCtrl:: SetExtendedStyle](#setextendedstyle)|탭 컨트롤에 대 한 확장 스타일을 설정 합니다.|
|[CTabCtrl:: Seon Agelist](#setimagelist)|탭 컨트롤에 이미지 목록을 할당 합니다.|
|[CTabCtrl:: SetItem](#setitem)|탭의 특성 중 일부 또는 모두를 설정 합니다.|
|[CTabCtrl:: SetItemExtra](#setitemextra)|탭 컨트롤의 응용 프로그램 정의 데이터에 예약 된 탭 당 바이트 수를 설정 합니다.|
|[CTabCtrl:: SetItemSize](#setitemsize)|항목의 너비와 높이를 설정 합니다.|
|[CTabCtrl:: SetItemState](#setitemstate)|표시 된 탭 컨트롤 항목의 상태를 설정 합니다.|
|[CTabCtrl:: SetMinTabWidth](#setmintabwidth)|탭 컨트롤에 있는 항목의 최소 너비를 설정 합니다.|
|[CTabCtrl:: SetPadding](#setpadding)|탭 컨트롤에서 각 탭의 아이콘 및 레이블 주위에 있는 공간 크기 (패딩)를 설정 합니다.|
|[CTabCtrl:: SetToolTips](#settooltips)|탭 컨트롤에 도구 설명 컨트롤을 할당 합니다.|

## <a name="remarks"></a>설명

"탭 컨트롤"은 노트북의 구분선 또는 파일 캐비닛의 레이블과 유사 합니다. 애플리케이션은 탭 컨트롤을 사용하여 창 또는 대화 상자의 동일한 영역에 대해 여러 페이지를 정의할 수 있습니다. 각 페이지는 사용자가 해당 탭을 선택할 때 응용 프로그램이 표시 하는 정보 집합 또는 컨트롤 그룹으로 구성 됩니다. 특수 한 유형의 탭 컨트롤은 단추와 같은 탭을 표시 합니다. 단추를 클릭 하면 페이지를 표시 하는 대신 명령이 즉시 수행 됩니다.

이 컨트롤 (및 `CTabCtrl` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

사용에 대 한 자세한 내용은 `CTabCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [ctabctrl 사용](../../mfc/using-ctabctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a> CTabCtrl:: AdjustRect

창 사각형이 지정 된 탭 컨트롤의 표시 영역을 계산 하거나 지정 된 표시 영역에 해당 하는 창 사각형을 계산 합니다.

```cpp
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*bLarger*<br/>
수행할 작업을 나타냅니다. 이 매개 변수가 TRUE 이면 *lpRect* 는 표시 사각형을 지정 하 고 해당 창 사각형을 받습니다. 이 매개 변수가 FALSE 이면 *lpRect* 는 창 사각형을 지정 하 고 해당 표시 사각형을 받습니다.

*lpRect*<br/>
지정 된 사각형을 지정 하 고 계산 된 사각형을 받는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a> CTabCtrl:: Create

탭 컨트롤을 만들어 개체의 인스턴스에 연결 `CTabCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
탭 컨트롤의 스타일을 지정 합니다. Windows SDK에 설명 된 [탭 컨트롤 스타일](/windows/win32/Controls/tab-control-styles)의 조합을 적용 합니다. 컨트롤에 적용할 수 있는 창 스타일 목록은 **설명 부분** 을 참조 하세요.

*rect*<br/>
탭 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
탭 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
탭 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

개체를 초기화 하는 작업이 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`CTabCtrl`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` 탭 컨트롤을 만들고이를 개체에 연결 `CTabCtrl` 합니다.

탭 컨트롤 스타일 외에도 탭 컨트롤에 다음 창 스타일을 적용할 수 있습니다.

- WS_CHILD 탭 컨트롤을 나타내는 자식 창을 만듭니다. WS_POPUP 스타일과 함께 사용할 수 없습니다.

- WS_VISIBLE 처음에 표시 되는 탭 컨트롤을 만듭니다.

- WS_DISABLED 처음에는 사용 하지 않도록 설정 된 창을 만듭니다.

- WS_GROUP 사용자가 화살표 키를 사용 하 여 한 컨트롤에서 다음 컨트롤로 이동할 수 있는 컨트롤 그룹의 첫 번째 컨트롤을 지정 합니다. 첫 번째 컨트롤이 같은 그룹에 속하는 WS_GROUP 스타일로 정의 된 모든 컨트롤입니다. WS_GROUP 스타일을 가진 다음 컨트롤은 스타일 그룹을 종료 하 고 다음 그룹을 시작 합니다. 즉, 한 그룹은 다음에 시작 하는 위치로 끝납니다.

- WS_TABSTOP 사용자가 TAB 키를 사용 하 여 이동할 수 있는 컨트롤 수 중 하나를 지정 합니다. TAB 키를 누르면 사용자가 WS_TABSTOP 스타일로 지정 된 다음 컨트롤로 이동 합니다.

확장 창 스타일을 사용 하 여 탭 컨트롤을 만들려면 대신 [Ctabctrl:: CreateEx](#createex) 를 호출 `Create` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a> CTabCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CTabCtrl` 합니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
만들려는 컨트롤의 확장 스타일을 지정 합니다. 확장 된 Windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*<br/>
탭 컨트롤의 스타일을 지정 합니다. Windows SDK에 설명 된 [탭 컨트롤 스타일](/windows/win32/Controls/tab-control-styles)의 조합을 적용 합니다. 컨트롤에 적용할 수 있는 창 스타일 목록은 [Create](#create) 의 **설명** 을 참조 하세요.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에서 만들 창의 크기와 위치를 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
컨트롤의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateEx` [Create](#create) 대신를 사용 하 여 **WS_EX_** windows 확장 스타일로 지정 된 확장 된 windows 스타일을 적용 합니다.

`CreateEx`*Dwexstyle* 로 지정 된 확장 된 Windows 스타일을 사용 하 여 컨트롤을 만듭니다. [SetExtendedStyle](#setextendedstyle)를 사용 하 여 컨트롤과 관련 된 확장 스타일을 설정 합니다. 예를 들어를 사용 하 여 WS_EX_CONTEXTHELP와 같은 스타일을 `CreateEx` 설정 하지만을 사용 하 여 이러한 스타일을 `SetExtendedStyle` TCS_EX_FLATSEPARATORS로 설정 합니다. 자세한 내용은 Windows SDK의 [탭 컨트롤 확장 스타일](/windows/win32/Controls/tab-control-extended-styles) 에서 설명 하는 스타일을 참조 하세요.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a> CTabCtrl:: CTabCtrl

`CTabCtrl` 개체를 생성합니다.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a> CTabCtrl::D eleteAllItems

탭 컨트롤에서 모든 항목을 제거 합니다.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a> CTabCtrl::D eleteItem

탭 컨트롤에서 지정 된 항목을 제거 합니다.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
삭제할 항목의 0부터 시작 하는 값입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a> CTabCtrl::D eselectAll

탭 컨트롤의 항목을 다시 설정 하 여 눌린 항목을 지웁니다.

```cpp
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>매개 변수

*fExcludeFocus*<br/>
Deselection 항목의 범위를 지정 하는 플래그입니다. 이 매개 변수를 FALSE로 설정 하면 모든 탭 단추가 다시 설정 됩니다. TRUE로 설정 되 면 현재 선택 된 항목을 제외한 모든 탭 항목이 다시 설정 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall)의 동작을 구현 합니다.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a> CTabCtrl::D rawItem

소유자 그리기 탭 컨트롤의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
칠할 항목을 설명 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다.

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CTabCtrl` 합니다.

응용 프로그램은이 멤버 함수가 종료 되기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a> CTabCtrl:: GetCurFocus

현재 포커스가 있는 탭의 인덱스를 검색 합니다.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>반환 값

현재 포커스가 있는 탭의 인덱스 (0부터 시작)입니다.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a> CTabCtrl:: GetCurSel

탭 컨트롤에서 현재 선택 된 탭을 검색 합니다.

```
int GetCurSel() const;
```

### <a name="return-value"></a>반환 값

성공 하면 선택 된 탭의 인덱스 (0부터 시작)이 고, 선택 된 탭이 없으면-1입니다.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a> CTabCtrl:: GetExtendedStyle

탭 컨트롤에 현재 사용 되 고 있는 확장 스타일을 검색 합니다.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>반환 값

탭 컨트롤에 현재 사용 중인 확장 스타일을 나타냅니다. 이 값은 Windows SDK 설명 된 대로 [탭 컨트롤 확장 스타일](/windows/win32/Controls/tab-control-extended-styles)의 조합입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)의 동작을 구현 합니다.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a> CTabCtrl:: GetImageList

탭 컨트롤에 연관된 이미지 목록을 검색합니다.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>반환 값

성공할 경우 탭 컨트롤의 이미지 목록에 대한 포인터이고 그렇지 않으면 NULL입니다.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a> CTabCtrl:: GetItem

탭 컨트롤의 탭에 대 한 정보를 검색 합니다.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
탭의 인덱스 (0부터 시작)입니다.

*pTabCtrlItem*<br/>
검색할 정보를 지정 하는 데 사용 되는 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 구조체에 대 한 포인터입니다. 탭에 대 한 정보를 수신 하는 데도 사용 됩니다. 이 구조체는 `InsertItem` , `GetItem` 및 멤버 함수와 함께 사용 됩니다 `SetItem` .

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

메시지가 전송 되 면 `mask` 멤버는 반환할 특성을 지정 합니다. `mask`멤버가 TCIF_TEXT 값을 지정 하는 경우 `pszText` 멤버는 항목 텍스트를 받는 버퍼의 주소를 포함 해야 하며 `cchTextMax` 멤버는 버퍼의 크기를 지정 해야 합니다.

- `mask`

   `TCITEM`검색 하거나 설정할 구조체 멤버를 지정 하는 값입니다. 이 멤버는 0 이거나 다음 값의 조합일 수 있습니다.

  - `pszText`멤버가 유효한 TCIF_TEXT입니다.

  - `iImage`멤버가 유효한 TCIF_IMAGE입니다.

  - `lParam`멤버가 유효한 TCIF_PARAM입니다.

  - `pszText`히브리어 또는 아랍어 시스템에서 오른쪽에서 왼쪽 읽기 순서를 사용 하 여의 텍스트를 표시 TCIF_RTLREADING 합니다.

  - `dwState`멤버가 유효한 TCIF_STATE입니다.

- `pszText`

   구조에 탭에 대 한 정보가 포함 된 경우 탭 텍스트를 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다. 구조가 정보를 수신 하는 경우이 멤버는 탭 텍스트를 받는 버퍼의 주소를 지정 합니다.

- `cchTextMax`

   가 가리키는 버퍼의 크기 `pszText` 입니다. 구조에서 정보를 수신 하지 않는 경우이 멤버는 무시 됩니다.

- `iImage` 탭 컨트롤의 이미지 목록에 대 한 인덱스 이거나 탭에 대 한 이미지가 없는 경우-1입니다.

- `lParam`

   탭과 연결 된 응용 프로그램 정의 데이터입니다. 탭 당 4 바이트 이상의 응용 프로그램 정의 데이터가 있는 경우 응용 프로그램에서 구조를 정의 하 고 구조 대신 사용 해야 합니다 `TCITEM` . 응용 프로그램 정의 구조체의 첫 번째 멤버는 [Tcitemheader](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)구조체 여야 합니다. `TCITEMHEADER`구조체는 구조체와 동일 `TCITEM` 하지만 멤버는 포함 하지 않습니다 `lParam` . 구조 크기와 구조체 크기의 차이는 `TCITEMHEADER` 탭 당 추가 바이트 수와 같아야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a> CTabCtrl:: GetItemCount

탭 컨트롤에서 탭 수를 검색합니다.

```
int GetItemCount() const;
```

### <a name="return-value"></a>반환 값

탭 컨트롤의 항목 수입니다.

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a> CTabCtrl:: GetItemRect

탭 컨트롤에서 지정 된 탭에 대 한 경계 사각형을 검색 합니다.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
탭 항목의 인덱스 (0부터 시작)입니다.

*lpRect*<br/>
탭의 경계 사각형을 받는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다. 이러한 좌표는 뷰포트의 현재 매핑 모드를 사용 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a> CTabCtrl:: GetItemState

*Nitem* 으로 식별 된 탭 컨트롤 항목의 상태를 검색 합니다.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
상태 정보를 검색할 항목의 인덱스 번호 (0부터 시작)입니다.

*dwMask*<br/>
반환할 항목의 상태 플래그를 지정 하는 마스크입니다. 값 목록은 Windows SDK 설명 된 대로 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 구조의 mask 멤버를 참조 하십시오.

### <a name="return-value"></a>반환 값

상태 정보를 받는 DWORD 값에 대 한 참조입니다. 다음 값 중 하나일 수 있습니다.

|값|설명|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|탭 컨트롤 항목이 선택 됩니다.|
|TCIS_HIGHLIGHTED|탭 컨트롤 항목이 강조 표시 되 고 탭과 텍스트가 현재 강조 표시 색을 사용 하 여 그려집니다. 강조 색을 사용 하는 경우이 색은 디더링된 색이 아니라 진정한 보간입니다.|

### <a name="remarks"></a>설명

항목의 상태는 `dwState` 구조체의 멤버에 의해 지정 됩니다 `TCITEM` .

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a> CTabCtrl:: GetRowCount

탭 컨트롤에서 현재 행 수를 검색 합니다.

```
int GetRowCount() const;
```

### <a name="return-value"></a>반환 값

탭 컨트롤의 탭 행 수입니다.

### <a name="remarks"></a>설명

TCS_MULTILINE 스타일이 있는 tab 컨트롤만 탭의 여러 행을 가질 수 있습니다.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a> CTabCtrl:: GetToolTips

탭 컨트롤과 연결 된 도구 설명 컨트롤의 핸들을 검색 합니다.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 도구 설명 컨트롤의 핸들 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

탭 컨트롤은 TCS_TOOLTIPS 스타일이 있는 경우 도구 설명 컨트롤을 만듭니다. 멤버 함수를 사용 하 여 탭 컨트롤에 도구 설명 컨트롤을 할당할 수도 있습니다 `SetToolTips` .

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a> CTabCtrl:: HighlightItem

탭 항목의 강조 상태를 설정 합니다.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>매개 변수

*idItem*<br/>
Tab 컨트롤 항목의 인덱스 (0부터 시작)입니다.

*fHighlight*<br/>
설정할 강조 상태를 지정 하는 값입니다. 이 값이 TRUE 이면 탭이 강조 표시 됩니다. FALSE 이면 탭이 기본 상태로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)을 구현 합니다.

## <a name="ctabctrlhittest"></a><a name="hittest"></a> CTabCtrl:: System.windows.media.visualtreehelper.hittest

지정 된 화면 위치에 있는 탭 (있는 경우)을 결정 합니다.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>매개 변수

*pHitTestInfo*<br/>
테스트할 화면 위치를 지정 하는 Windows SDK에 설명 된 대로 [Tchittestinfo](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

탭의 인덱스 (0부터 시작)를 반환 하 고, 지정 된 위치에 탭이 없으면-1을 반환 합니다.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a> CTabCtrl:: InsertItem

기존 탭 컨트롤에 새 탭을 삽입 합니다.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
새 탭의 인덱스 (0부터 시작)입니다.

*pTabCtrlItem*<br/>
탭의 특성을 지정 하는 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 구조체에 대 한 포인터입니다.

*lpszItem*<br/>
탭의 텍스트를 포함 하는 null로 끝나는 문자열의 주소입니다.

*nImage*<br/>
이미지 목록에서 삽입할 이미지의 인덱스 (0부터 시작)입니다.

*nMask*<br/>
`TCITEM`설정할 구조 특성을 지정 합니다. 0 또는 다음 값의 조합일 수 있습니다.

- `pszText`멤버가 유효한 TCIF_TEXT입니다.

- `iImage`멤버가 유효한 TCIF_IMAGE입니다.

- TCIF_PARAM *lParam* 멤버가 유효 합니다.

- `pszText`히브리어 또는 아랍어 시스템에서 오른쪽에서 왼쪽 읽기 순서를 사용 하 여의 텍스트를 표시 TCIF_RTLREADING 합니다.

- *Dwstate* 멤버가 유효 TCIF_STATE.

*lParam*<br/>
탭과 연결 된 응용 프로그램 정의 데이터입니다.

*dwState*<br/>
항목의 상태에 대 한 값을 지정 합니다. 자세한 내용은 Windows SDK의 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 을 참조 하십시오.

*dwStateMask*<br/>
설정할 상태를 지정 합니다. 자세한 내용은 Windows SDK의 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 을 참조 하십시오.

### <a name="return-value"></a>반환 값

성공 하는 경우 새 탭의 인덱스 (0부터 시작)입니다. 그렇지 않으면-1입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a> CTabCtrl:: RemoveImage

탭 컨트롤의 이미지 목록에서 지정 된 이미지를 제거 합니다.

```cpp
void RemoveImage(int nImage);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
제거할 이미지의 0부터 시작 하는 인덱스입니다.

### <a name="remarks"></a>설명

탭 컨트롤은 각 탭의 이미지 인덱스를 업데이트 하므로 각 탭은 동일한 이미지와 연결 된 상태로 유지 됩니다.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a> CTabCtrl:: SetCurFocus

탭 컨트롤에서 지정 된 탭으로 포커스를 설정 합니다.

```cpp
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
포커스를 가져오는 탭의 인덱스를 지정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)의 동작을 구현 합니다.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a> CTabCtrl:: SetCurSel

탭 컨트롤에서 탭을 선택 합니다.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
선택할 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

성공 하면 이전에 선택한 탭의 인덱스 (0부터 시작)이 고, 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

탭 컨트롤은이 함수를 사용 하 여 탭을 선택 하는 경우 TCN_SELCHANGING 또는 TCN_SELCHANGE 알림 메시지를 보내지 않습니다. 사용자가 키보드를 클릭 하거나 키보드를 사용 하 여 탭을 변경할 때 WM_NOTIFY를 사용 하 여 이러한 알림이 전송 됩니다.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a> CTabCtrl:: SetExtendedStyle

탭 컨트롤에 대 한 확장 스타일을 설정 합니다.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>매개 변수

*dwNewStyle*<br/>
탭 컨트롤 확장 스타일의 조합을 지정 하는 값입니다.

*dwExMask*<br/>
영향을 받을 *Dwnewstyle* 의 스타일을 나타내는 DWORD 값입니다. *Dwexmask* 의 확장 된 스타일만 변경 됩니다. 다른 모든 스타일은 그대로 유지 됩니다. 이 매개 변수가 0 이면 *Dwnewstyle* 의 모든 스타일이 영향을 받게 됩니다.

### <a name="return-value"></a>반환 값

Windows SDK 설명 된 대로 이전 [탭 컨트롤 확장 스타일](/windows/win32/Controls/tab-control-extended-styles)을 포함 하는 DWORD 값입니다.

### <a name="return-value"></a>반환 값

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)의 동작을 구현 합니다.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a> CTabCtrl:: Seon Agelist

탭 컨트롤에 이미지 목록을 할당 합니다.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>매개 변수

*pImageList*<br/>
탭 컨트롤에 할당할 이미지 목록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이전 이미지 목록에 대 한 포인터를 반환 하거나, 이전 이미지 목록이 없는 경우 NULL을 반환 합니다.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a> CTabCtrl:: SetItem

탭의 특성 중 일부 또는 모두를 설정 합니다.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
항목의 인덱스 (0부터 시작)입니다.

*pTabCtrlItem*<br/>
새 항목 특성을 포함 하는 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 구조체에 대 한 포인터입니다. `mask`멤버는 설정할 특성을 지정 합니다. `mask`멤버가 TCIF_TEXT 값을 지정 하는 경우 `pszText` 멤버는 null로 끝나는 문자열의 주소이 고 `cchTextMax` 멤버는 무시 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [GetItem](#getitem)의 예제를 참조 하세요.

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a> CTabCtrl:: SetItemExtra

탭 컨트롤의 응용 프로그램 정의 데이터에 예약 된 탭 당 바이트 수를 설정 합니다.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
설정할 추가 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)의 동작을 구현 합니다.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a> CTabCtrl:: SetItemSize

탭 컨트롤 항목의 높이 및 너비를 설정합니다.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
탭 제어 항목의 새로운 너비 및 높이입니다(픽셀).

### <a name="return-value"></a>반환 값

탭 제어 항목의 이전 높이 및 너비를 반환합니다.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a> CTabCtrl:: SetItemState

*Nitem* 으로 식별 된 탭 컨트롤 항목의 상태를 설정 합니다.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
상태 정보를 설정할 항목의 인덱스 번호 (0부터 시작)입니다.

*dwMask*<br/>
설정할 항목의 상태 플래그를 지정 하는 마스크입니다. 값 목록은 Windows SDK 설명 된 대로 [Tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 구조의 mask 멤버를 참조 하십시오.

*dwState*<br/>
상태 정보를 포함 하는 DWORD 값에 대 한 참조입니다. 다음 값 중 하나일 수 있습니다.

|값|설명|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|탭 컨트롤 항목이 선택 됩니다.|
|TCIS_HIGHLIGHTED|탭 컨트롤 항목이 강조 표시 되 고 탭과 텍스트가 현재 강조 표시 색을 사용 하 여 그려집니다. 강조 색을 사용 하는 경우이 색은 디더링된 색이 아니라 진정한 보간입니다.|

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a> CTabCtrl:: SetMinTabWidth

탭 컨트롤에 있는 항목의 최소 너비를 설정 합니다.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>매개 변수

*cx*<br/>
탭 컨트롤 항목에 대해 설정 되는 최소 너비입니다. 이 매개 변수를-1로 설정 하면 컨트롤에서 기본 탭 너비를 사용 하 게 됩니다.

### <a name="return-value"></a>반환 값

이전 최소 탭 너비입니다.

### <a name="return-value"></a>반환 값

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)의 동작을 구현 합니다.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a> CTabCtrl:: SetPadding

탭 컨트롤에서 각 탭의 아이콘 및 레이블 주위에 있는 공간 크기 (패딩)를 설정 합니다.

```cpp
void SetPadding(CSize size);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
탭 컨트롤에서 각 탭의 아이콘 및 레이블 주위에 있는 공간 크기 (패딩)를 설정 합니다.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a> CTabCtrl:: SetToolTips

탭 컨트롤에 도구 설명 컨트롤을 할당 합니다.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>매개 변수

*pWndTip*<br/>
도구 설명 컨트롤의 핸들입니다.

### <a name="remarks"></a>설명

을 호출 하 여 탭 컨트롤과 연결 된 도구 설명 컨트롤을 가져올 수 있습니다 `GetToolTips` .

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl 클래스](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl 클래스](../../mfc/reference/clistctrl-class.md)
