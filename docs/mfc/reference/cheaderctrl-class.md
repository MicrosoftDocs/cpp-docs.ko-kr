---
description: '자세히 알아보기: CHeaderCtrl 클래스'
title: CHeaderCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: 9fe17b6c2553526af40ead253cd7c03fa6b57612
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184012"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 클래스

Windows의 공용 헤더 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHeaderCtrl:: CHeaderCtrl](#cheaderctrl)|`CHeaderCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHeaderCtrl:: ClearAllFilters](#clearallfilters)|헤더 컨트롤에 대 한 모든 필터를 지웁니다.|
|[CHeaderCtrl:: ClearFilter](#clearfilter)|헤더 컨트롤에 대 한 필터를 지웁니다.|
|[CHeaderCtrl:: Create](#create)|헤더 컨트롤을 만들고이를 개체에 연결 `CHeaderCtrl` 합니다.|
|[CHeaderCtrl:: CreateDragImage](#createdragimage)|헤더 컨트롤 내에서 항목 이미지의 투명 버전을 만듭니다.|
|[CHeaderCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 헤더 컨트롤을 만들고이를 `CListCtrl` 개체에 연결 합니다.|
|[CHeaderCtrl::D eleteItem](#deleteitem)|헤더 컨트롤에서 항목을 삭제 합니다.|
|[CHeaderCtrl::D rawItem](#drawitem)|헤더 컨트롤의 지정 된 항목을 그립니다.|
|[CHeaderCtrl:: EditFilter](#editfilter)|헤더 컨트롤의 지정 된 필터 편집을 시작 합니다.|
|[CHeaderCtrl:: GetBitmapMargin](#getbitmapmargin)|헤더 컨트롤에서 비트맵 여백의 너비를 검색 합니다.|
|[CHeaderCtrl:: GetFocusedItem](#getfocuseditem)|현재 머리글 컨트롤에서 포커스가 있는 항목의 식별자를 가져옵니다.|
|[CHeaderCtrl:: GetImageList](#getimagelist)|헤더 컨트롤에서 머리글 항목을 그리는 데 사용 되는 이미지 목록의 핸들을 검색 합니다.|
|[CHeaderCtrl:: GetItem](#getitem)|헤더 컨트롤의 항목에 대 한 정보를 검색 합니다.|
|[CHeaderCtrl:: GetItemCount](#getitemcount)|헤더 컨트롤의 항목 수를 검색 합니다.|
|[CHeaderCtrl:: GetItemDropDownRect](#getitemdropdownrect)|헤더 컨트롤의 지정 된 드롭다운 단추에 대 한 경계 사각형 정보를 가져옵니다.|
|[CHeaderCtrl:: GetItemRect](#getitemrect)|헤더 컨트롤에서 지정 된 항목의 경계 사각형을 검색 합니다.|
|[CHeaderCtrl:: GetOrderArray](#getorderarray)|헤더 컨트롤에서 항목의 왼쪽에서 오른쪽 순서를 검색 합니다.|
|[CHeaderCtrl:: GetOverflowRect](#getoverflowrect)|현재 머리글 컨트롤에 대 한 오버플로 단추의 경계 사각형을 가져옵니다.|
|[CHeaderCtrl:: System.windows.media.visualtreehelper.hittest](#hittest)|지정 된 지점에 있는 헤더 항목 (있는 경우)을 결정 합니다.|
|[CHeaderCtrl:: InsertItem](#insertitem)|헤더 컨트롤에 새 항목을 삽입 합니다.|
|[CHeaderCtrl:: Layout](#layout)|지정 된 사각형 내에서 헤더 컨트롤의 크기와 위치를 검색 합니다.|
|[CHeaderCtrl:: OrderToIndex](#ordertoindex)|헤더 컨트롤의 순서에 따라 항목의 인덱스 값을 검색 합니다.|
|[CHeaderCtrl:: SetBitmapMargin](#setbitmapmargin)|헤더 컨트롤에서 비트맵 여백의 너비를 설정 합니다.|
|[CHeaderCtrl:: SetFilterChangeTimeout](#setfilterchangetimeout)|필터 특성에서 변경이 발생 하는 시간 사이의 시간 제한 간격을 설정 하 고 알림 게시를 설정 합니다 `HDN_FILTERCHANGE` .|
|[CHeaderCtrl:: SetFocusedItem](#setfocuseditem)|현재 헤더 컨트롤의 지정 된 헤더 항목에 포커스를 설정 합니다.|
|[CHeaderCtrl:: SetHotDivider](#sethotdivider)|헤더 항목의 수동 끌어서 놓기를 나타내기 위해 헤더 항목 간의 구분선을 변경 합니다.|
|[CHeaderCtrl:: Seon Agelist](#setimagelist)|헤더 컨트롤에 이미지 목록을 할당 합니다.|
|[CHeaderCtrl:: SetItem](#setitem)|헤더 컨트롤에서 지정 된 항목의 특성을 설정 합니다.|
|[CHeaderCtrl:: SetOrderArray](#setorderarray)|머리글 컨트롤의 왼쪽에서 오른쪽으로 항목의 순서를 설정 합니다.|

## <a name="remarks"></a>설명

헤더 컨트롤은 일반적으로 텍스트 또는 숫자 열 집합 위에 배치 되는 창입니다. 각 열에 대 한 제목을 포함 하 고 파트로 나눌 수 있습니다. 사용자는 파트를 구분 하는 구분선을 끌어 각 열의 너비를 설정할 수 있습니다. 헤더 컨트롤에 대 한 예시의 경우 [헤더 컨트롤](/windows/win32/Controls/header-controls)을 참조 하세요.

이 컨트롤과 `CHeaderCtrl` 클래스는 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

Windows 95/Internet Explorer 4.0 공용 컨트롤에 추가 된 기능에는 다음이 포함 됩니다.

- 헤더 항목 사용자 지정 순서 지정.

- 헤더 항목을 다시 정렬 하기 위한 머리글 항목 끌어서 놓기 개체를 만들 때 HDS_DRAGDROP 스타일을 사용 `CHeaderCtrl` 합니다.

- 열 크기를 조정 하는 동안 머리글 열 텍스트를 지속적으로 볼 수 있습니다. 개체를 만들 때 HDS_FULLDRAG 스타일을 사용 `CHeaderCtrl` 합니다.

- 헤더 핫 트래킹을 포인터가 포인터를 가리킬 때 헤더 항목을 강조 표시 합니다. 개체를 만들 때 HDS_HOTTRACK 스타일을 사용 `CHeaderCtrl` 합니다.

- 이미지 목록 지원. 헤더 항목은 개체 또는 텍스트에 저장 된 이미지를 포함할 수 있습니다 `CImageList` .

사용에 대 한 자세한 내용은 `CHeaderCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CHeaderCtrl 사용](../../mfc/using-cheaderctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a> CHeaderCtrl:: CHeaderCtrl

`CHeaderCtrl` 개체를 생성합니다.

```
CHeaderCtrl();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a> CHeaderCtrl:: ClearAllFilters

헤더 컨트롤에 대 한 모든 필터를 지웁니다.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 대로 열 값이-1 인 Win32 메시지 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) 의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a> CHeaderCtrl:: ClearFilter

헤더 컨트롤에 대 한 필터를 지웁니다.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>매개 변수

*nColumn*<br/>
지울 필터를 나타내는 열 값입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a> CHeaderCtrl:: Create

헤더 컨트롤을 만들고이를 개체에 연결 `CHeaderCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
헤더 컨트롤의 스타일을 지정 합니다. 헤더 컨트롤 스타일에 대 한 설명은 Windows SDK의 [헤더 컨트롤 스타일](/windows/win32/Controls/header-control-styles) 을 참조 하세요.

*rect*<br/>
헤더 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
헤더 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
헤더 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CHeaderCtrl`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` 헤더 컨트롤을 만들고이를 개체에 연결 `CHeaderCtrl` 합니다.

헤더 컨트롤 스타일 외에도 다음과 같은 일반적인 컨트롤 스타일을 사용 하 여 헤더 컨트롤의 위치와 크기 조정 방법을 결정할 수 있습니다 (자세한 내용은 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 참조).

- CCS_BOTTOM 하면 컨트롤이 부모 창의 클라이언트 영역 맨 아래에 배치 되 고 너비가 부모 창의 너비와 동일 하 게 설정 됩니다.

- CCS_NODIVIDER 2 픽셀 강조 표시를 컨트롤의 맨 위에 그릴 수 없습니다.

- CCS_NOMOVEY WM_SIZE 메시지에 대 한 응답으로 컨트롤의 크기를 조정 하 고 세로 방향으로 이동 하지 않습니다. CCS_NORESIZE 스타일이 사용 되는 경우이 스타일은 적용 되지 않습니다. 헤더 컨트롤에는 기본적으로이 스타일이 있습니다.

- CCS_NOPARENTALIGN는 컨트롤이 부모 창의 위쪽 이나 아래쪽으로 자동으로 이동 하는 것을 방지 합니다. 대신 부모 창의 크기를 변경 하더라도 컨트롤이 부모 창 내에서 해당 위치를 유지 합니다. CCS_TOP 또는 CCS_BOTTOM 스타일도 사용 되는 경우 높이가 기본값으로 조정 되지만 위치와 너비는 그대로 유지 됩니다.

- CCS_NORESIZE는 처음 크기 또는 새 크기를 설정할 때 컨트롤의 기본 너비와 높이를 사용 하지 못하도록 합니다. 대신, 컨트롤은 만들거나 크기를 조정 하기 위해 요청에 지정 된 너비와 높이를 사용 합니다.

- CCS_TOP 하면 컨트롤이 부모 창의 클라이언트 영역 위쪽에 배치 되 고 너비가 부모 창의 너비와 동일 하 게 설정 됩니다.

헤더 컨트롤에 다음 창 스타일을 적용할 수도 있습니다 (자세한 내용은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 참조).

- WS_CHILD 자식 창을 만듭니다. WS_POPUP 스타일과 함께 사용할 수 없습니다.

- WS_VISIBLE 처음에 표시 되는 창을 만듭니다.

- WS_DISABLED 처음에는 사용 하지 않도록 설정 된 창을 만듭니다.

- WS_GROUP 사용자가 화살표 키를 사용 하 여 한 컨트롤에서 다음 컨트롤로 이동할 수 있는 컨트롤 그룹의 첫 번째 컨트롤을 지정 합니다. 첫 번째 컨트롤이 같은 그룹에 속하는 WS_GROUP 스타일로 정의 된 모든 컨트롤입니다. WS_GROUP 스타일을 가진 다음 컨트롤은 스타일 그룹을 종료 하 고 다음 그룹을 시작 합니다. 즉, 한 그룹은 다음에 시작 하는 위치로 끝납니다.

- WS_TABSTOP 사용자가 TAB 키를 사용 하 여 이동할 수 있는 컨트롤 수 중 하나를 지정 합니다. TAB 키를 누르면 사용자가 WS_TABSTOP 스타일로 지정 된 다음 컨트롤로 이동 합니다.

컨트롤과 함께 확장 된 windows 스타일을 사용 하려는 경우 대신 [Createex](#createex) 를 호출 `Create` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a> CHeaderCtrl:: CreateEx

컨트롤 (자식 창)을 만들어 개체와 연결 `CHeaderCtrl` 합니다.

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
헤더 컨트롤의 스타일입니다. 헤더 컨트롤 스타일에 대 한 설명은 Windows SDK의 [헤더 컨트롤 스타일](/windows/win32/Controls/header-control-styles) 을 참조 하세요. 추가 스타일 목록은 [Create](#create) 를 참조 하세요.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에서 만들 창의 크기와 위치를 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
컨트롤의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateEx`대신를 사용 `Create` 하 여 **WS_EX_** windows 확장 스타일로 지정 된 확장 된 windows 스타일을 적용 합니다.

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a> CHeaderCtrl:: CreateDragImage

헤더 컨트롤 내에서 항목 이미지의 투명 버전을 만듭니다.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
헤더 컨트롤에 있는 항목의 인덱스 (0부터 시작)입니다. 이 항목에 할당 된 이미지는 투명 이미지의 기반이 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 [CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다. 그렇지 않으면 NULL입니다. 반환 된 목록에는 하나의 이미지만 포함 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)의 동작을 구현 합니다. 헤더 항목 끌어서 놓기를 지원 하기 위해 제공 됩니다.

`CImageList`반환 된 포인터가 가리키는 개체는 임시 개체 이며 다음 유휴 시간 처리 시 삭제 됩니다.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a> CHeaderCtrl::D eleteItem

헤더 컨트롤에서 항목을 삭제 합니다.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
삭제할 항목의 인덱스 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a> CHeaderCtrl::D rawItem

소유자 그리기 헤더 컨트롤의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
칠할 항목을 설명 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다.

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CHeaderCtrl` 합니다.

응용 프로그램은이 멤버 함수가 종료 되기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a> CHeaderCtrl:: EditFilter

헤더 컨트롤의 지정 된 필터 편집을 시작 합니다.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>매개 변수

*nColumn*<br/>
편집할 열입니다.

*bDiscardChanges*<br/>
사용자가 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) 메시지가 전송 될 때 필터를 편집 하는 경우 사용자의 편집 변경 내용을 처리 하는 방법을 지정 하는 값입니다.

사용자가 변경한 내용을 취소 하려면 TRUE를 지정 하 고, 사용자가 변경한 내용을 적용 하려면 FALSE를 지정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a> CHeaderCtrl:: GetBitmapMargin

헤더 컨트롤에서 비트맵 여백의 너비를 검색 합니다.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>반환 값

비트맵 여백의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a> CHeaderCtrl:: GetFocusedItem

현재 헤더 컨트롤에 포커스가 있는 항목의 인덱스를 가져옵니다.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>반환 값

포커스가 있는 헤더 항목의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_headerCtrl` 현재 헤더 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 및 메서드를 보여 줍니다 `SetFocusedItem` `GetFocusedItem` . 코드의 이전 섹션에서는 5 개의 열이 있는 헤더 컨트롤을 만들었습니다. 그러나 열이 표시 되지 않도록 열 구분 기호를 끌 수 있습니다. 다음 예제에서는 마지막 열 헤더를 설정 하 고 포커스 항목으로 확인 합니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a> CHeaderCtrl:: GetImageList

헤더 컨트롤에서 머리글 항목을 그리는 데 사용 되는 이미지 목록의 핸들을 검색 합니다.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>반환 값

[CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)의 동작을 구현 합니다. `CImageList`반환 된 포인터가 가리키는 개체는 임시 개체 이며 다음 유휴 시간 처리 시 삭제 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a> CHeaderCtrl:: GetItem

헤더 컨트롤 항목에 대 한 정보를 검색 합니다.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
검색할 항목의 인덱스 (0부터 시작)를 지정 합니다.

*pHeaderItem*<br/>
새 항목을 받는 [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 구조체에 대 한 포인터입니다. 이 구조체는 `InsertItem` 및 멤버 함수와 함께 사용 됩니다 `SetItem` . 요소에 설정 된 플래그는 `mask` 반환 될 때 해당 요소의 값을 올바르게 채워야 합니다. `mask`요소가 0으로 설정 된 경우 다른 구조체 요소의 값은 의미가 없습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a> CHeaderCtrl:: GetItemCount

헤더 컨트롤의 항목 수를 검색 합니다.

```
int GetItemCount() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 헤더 컨트롤 항목 수 그렇지 않으면-1입니다.

### <a name="example"></a>예제

  [CHeaderCtrl::D eleteitem](#deleteitem)의 예제를 참조 하세요.

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a> CHeaderCtrl:: GetItemDropDownRect

현재 머리글 컨트롤의 머리글 항목에 대 한 드롭다운 단추의 경계 사각형을 가져옵니다.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*iItem*\
진행 HDF_SPLITBUTTON 스타일이 있는 헤더 항목의 인덱스 (0부터 시작)입니다. 자세한 내용은 `fmt` [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 구조체의 멤버를 참조 하십시오.

*lpRect*\
제한이 경계 사각형 정보를 수신 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 함수가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_headerCtrl` 현재 헤더 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>예제

다음 코드 예제는 `GetItemDropDownRect` 메서드. 코드의 이전 섹션에서는 5 개의 열이 있는 헤더 컨트롤을 만들었습니다. 다음 코드 예제에서는 머리글 드롭다운 단추에 예약 된 첫 번째 열의 위치 주위에 3D 사각형을 그립니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a> CHeaderCtrl:: GetItemRect

헤더 컨트롤에서 지정 된 항목의 경계 사각형을 검색 합니다.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
헤더 컨트롤 항목의 인덱스 (0부터 시작)입니다.

*lpRect*<br/>
경계 사각형 정보를 받는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체의 주소에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)의 동작을 구현 합니다.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a> CHeaderCtrl:: GetOrderArray

헤더 컨트롤에서 항목의 왼쪽에서 오른쪽 순서를 검색 합니다.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>매개 변수

*piArray*<br/>
왼쪽에서 오른쪽으로 표시 되는 순서 대로 header 컨트롤에 있는 항목의 인덱스 값을 받는 버퍼의 주소에 대 한 포인터입니다.

*iCount*<br/>
헤더 제어 항목 수입니다. 음수가 아니어야 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)의 동작을 구현 합니다. 헤더 항목 순서 지정을 지원 하기 위해 제공 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a> CHeaderCtrl:: GetOverflowRect

현재 머리글 컨트롤의 오버플로 단추에 대 한 경계 사각형을 가져옵니다.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*lpRect*\
제한이 경계 사각형 정보를 수신 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 함수가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

헤더 컨트롤에 동시에 표시할 수 있는 것 보다 많은 항목이 포함 된 경우 컨트롤은 표시 되지 않는 항목으로 스크롤 하는 오버플로 단추를 표시할 수 있습니다. 오버플로 단추를 표시 하려면 헤더 컨트롤에 HDS_OVERFLOW 및 HDF_SPLITBUTTON 스타일이 있어야 합니다. 경계 사각형은 오버플로 단추를 포함 하 고 오버플로 단추가 표시 되는 경우에만 존재 합니다. 자세한 내용은 [헤더 컨트롤 스타일](/windows/win32/Controls/header-control-styles)을 참조 하세요.

이 메서드는 Windows SDK에서 설명 하는 [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_headerCtrl` 현재 헤더 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>예제

다음 코드 예제는 `GetOverflowRect` 메서드. 코드의 이전 섹션에서는 5 개의 열이 있는 헤더 컨트롤을 만들었습니다. 그러나 열이 표시 되지 않도록 열 구분 기호를 끌 수 있습니다. 일부 열이 표시 되지 않는 경우 헤더 컨트롤은 오버플로 단추를 그립니다. 다음 코드 예제에서는 오버플로 단추 위치 주위에 3D 사각형을 그립니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a> CHeaderCtrl:: System.windows.media.visualtreehelper.hittest

지정 된 지점에 있는 헤더 항목 (있는 경우)을 결정 합니다.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>매개 변수

*phdhti*\
[in, out] 테스트의 결과를 확인 하 고 받을 지점을 지정 하는 [Hdhittestinfo](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 위치에서 헤더 항목 (있는 경우)의 인덱스 (0부터 시작)입니다. 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_headerCtrl` 현재 헤더 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>예제

다음 코드 예제는 `HitTest` 메서드. 이 코드 예제의 이전 섹션에서는 5 개의 열이 있는 헤더 컨트롤을 만들었습니다. 그러나 열이 표시 되지 않도록 열 구분 기호를 끌 수 있습니다. 이 예에서는 열이 표시 되는 경우 해당 열의 인덱스를 보고 하 고, 열이 표시 되지 않는 경우-1을 보고 합니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a> CHeaderCtrl:: InsertItem

헤더 컨트롤의 지정 된 인덱스에 새 항목을 삽입 합니다.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
삽입할 항목의 인덱스(0부터 시작)입니다. 값이 0 이면 항목이 헤더 컨트롤의 시작 부분에 삽입 됩니다. 값이 최 댓 값 보다 크면 헤더 컨트롤의 끝에 항목이 삽입 됩니다.

*phdi*<br/>
삽입할 항목에 대 한 정보를 포함 하는 [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 새 항목의 인덱스입니다. 그렇지 않으면-1입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a> CHeaderCtrl:: Layout

지정 된 사각형 내에서 헤더 컨트롤의 크기와 위치를 검색 합니다.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>매개 변수

*pHeaderLayout*<br/>
헤더 컨트롤의 크기와 위치를 설정 하는 데 사용 되는 정보를 포함 하는 [HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 지정 된 사각형을 차지할 새 헤더 컨트롤의 적절 한 크기를 결정 하는 데 사용 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a> CHeaderCtrl:: OrderToIndex

헤더 컨트롤의 순서에 따라 항목의 인덱스 값을 검색 합니다.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>매개 변수

*n 순서*<br/>
항목이 머리글 컨트롤에서 왼쪽에서 오른쪽으로 표시 되는 순서 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

헤더 컨트롤의 순서에 따라 항목의 인덱스입니다. 인덱스는 0부터 시작 하 여 왼쪽에서 오른쪽으로 계산 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 매크로 [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)의 동작을 구현 합니다. 헤더 항목 순서 지정을 지원 하기 위해 제공 됩니다.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a> CHeaderCtrl:: SetBitmapMargin

헤더 컨트롤에서 비트맵 여백의 너비를 설정 합니다.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
기존 헤더 컨트롤 내에서 비트맵을 둘러싼 여백의 너비 (픽셀)입니다.

### <a name="return-value"></a>반환 값

비트맵 여백의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a> CHeaderCtrl:: SetFilterChangeTimeout

필터 특성에서 변경이 발생 하는 시간과 [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) 알림 게시 사이의 제한 시간 간격을 설정 합니다.

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>매개 변수

*dwTimeOut*<br/>
시간 제한 값 (밀리초)입니다.

### <a name="return-value"></a>반환 값

수정 되는 필터 컨트롤의 인덱스입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a> CHeaderCtrl:: SetFocusedItem

현재 헤더 컨트롤의 지정 된 헤더 항목에 포커스를 설정 합니다.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>매개 변수

*iItem*\
진행 헤더 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_headerCtrl` 현재 헤더 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 및 메서드를 보여 줍니다 `SetFocusedItem` `GetFocusedItem` . 코드의 이전 섹션에서는 5 개의 열이 있는 헤더 컨트롤을 만들었습니다. 그러나 열이 표시 되지 않도록 열 구분 기호를 끌 수 있습니다. 다음 예제에서는 마지막 열 헤더를 설정 하 고 포커스 항목으로 확인 합니다.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a> CHeaderCtrl:: SetHotDivider

헤더 항목의 수동 끌어서 놓기를 나타내기 위해 헤더 항목 간의 구분선을 변경 합니다.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
포인터의 위치입니다. 헤더 컨트롤은 포인터의 위치를 기준으로 적절 한 구분선을 강조 표시 합니다.

*nIndex*<br/>
강조 표시 된 구분선의 인덱스입니다.

### <a name="return-value"></a>반환 값

강조 표시 된 구분선의 인덱스입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)의 동작을 구현 합니다. 헤더 항목 끌어서 놓기를 지원 하기 위해 제공 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a> CHeaderCtrl:: Seon Agelist

헤더 컨트롤에 이미지 목록을 할당 합니다.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>매개 변수

*pImageList*<br/>
`CImageList`헤더 컨트롤에 할당할 이미지 목록을 포함 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이전에 헤더 컨트롤에 할당 된 [CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)의 동작을 구현 합니다. `CImageList`반환 된 포인터가 가리키는 개체는 임시 개체 이며 다음 유휴 시간 처리 시 삭제 됩니다.

### <a name="example"></a>예제

  [CHeaderCtrl:: GetImageList](#getimagelist)의 예제를 참조 하세요.

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a> CHeaderCtrl:: SetItem

헤더 컨트롤에서 지정 된 항목의 특성을 설정 합니다.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
조작할 항목의 인덱스 (0부터 시작)입니다.

*pHeaderItem*<br/>
새 항목에 대 한 정보를 포함 하는 [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CHeaderCtrl:: GetItem](#getitem)의 예제를 참조 하세요.

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a> CHeaderCtrl:: SetOrderArray

머리글 컨트롤의 왼쪽에서 오른쪽으로 항목의 순서를 설정 합니다.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>매개 변수

*iCount*<br/>
헤더 제어 항목 수입니다.

*piArray*<br/>
왼쪽에서 오른쪽으로 표시 되는 순서 대로 header 컨트롤에 있는 항목의 인덱스 값을 받는 버퍼의 주소에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 매크로 [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)의 동작을 구현 합니다. 헤더 항목 순서 지정을 지원 하기 위해 제공 됩니다.

### <a name="example"></a>예제

  [CHeaderCtrl:: GetOrderArray](#getorderarray)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 클래스](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 클래스](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 클래스](../../mfc/reference/cimagelist-class.md)
