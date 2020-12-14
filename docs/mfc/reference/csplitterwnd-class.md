---
description: '자세히 알아보기: CSplitterWnd 클래스'
title: CSplitterWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: 4888a9e0085895dd1a323f797c7e90bfbf7226d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342649"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd 클래스

여러 개의 창이 포함된 창인 분할자 창 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSplitterWnd:: CSplitterWnd](#csplitterwnd)|를 호출 하 여 `CSplitterWnd` 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSplitterWnd:: ActivateNext](#activatenext)|다음 창이 나 이전 창 명령을 수행 합니다.|
|[CSplitterWnd:: CanActivateNext](#canactivatenext)|다음 창이 나 이전 창 명령을 현재 사용할 수 있는지 확인 합니다.|
|[CSplitterWnd:: Create](#create)|을 호출 하 여 동적 분할자 창을 만들고 개체에 연결 `CSplitterWnd` 합니다.|
|[CSplitterWnd:: CreateScrollBarCtrl](#createscrollbarctrl)|공유 스크롤 막대 컨트롤을 만듭니다.|
|[CSplitterWnd:: CreateStatic](#createstatic)|을 호출 하 여 정적 분할자 창을 만들고 개체에 연결 `CSplitterWnd` 합니다.|
|[CSplitterWnd:: CreateView](#createview)|을 호출 하 여 분할자 창에 창을 만듭니다.|
|[CSplitterWnd::D eleteColumn](#deletecolumn)|분할자 창에서 열을 삭제 합니다.|
|[CSplitterWnd::D eleteRow](#deleterow)|분할자 창에서 행을 삭제 합니다.|
|[CSplitterWnd::D eleteView](#deleteview)|분할자 창에서 뷰를 삭제 합니다.|
|[CSplitterWnd::D oKeyboardSplit](#dokeyboardsplit)|일반적으로 "창 분할"의 키보드 분할 명령을 수행 합니다.|
|[CSplitterWnd::D oScroll](#doscroll)|분할 창의 동기화 된 스크롤을 수행 합니다.|
|[CSplitterWnd::D oScrollBy](#doscrollby)|지정 된 픽셀 수 만큼 분할 창을 스크롤합니다.|
|[CSplitterWnd:: Getactivepgea](#getactivepane)|프레임의 포커스 또는 활성 뷰에서 활성 창을 결정 합니다.|
|[CSplitterWnd:: GetColumnCount](#getcolumncount)|현재 창 열 수를 반환 합니다.|
|[CSplitterWnd:: GetColumnInfo](#getcolumninfo)|지정 된 열에 대 한 정보를 반환 합니다.|
|[CSplitterWnd:: GetPane](#getpane)|지정 된 행과 열에 있는 창을 반환 합니다.|
|[CSplitterWnd:: GetRowCount](#getrowcount)|현재 창 행 수를 반환 합니다.|
|[CSplitterWnd:: GetRowInfo](#getrowinfo)|지정 된 행에 대 한 정보를 반환 합니다.|
|[CSplitterWnd:: GetScrollStyle](#getscrollstyle)|공유 스크롤 막대 스타일을 반환 합니다.|
|[CSplitterWnd:: IdFromRowCol](#idfromrowcol)|지정 된 행과 열에 있는 창의 자식 창 ID를 반환 합니다.|
|[CSplitterWnd:: IsChildPane](#ischildpane)|를 호출 하 여 창이 현재 분할자 창의 자식 창 인지 여부를 확인 합니다.|
|[CSplitterWnd:: IsTracking](#istracking)|분할자 막대가 현재 이동 되 고 있는지 여부를 확인 합니다.|
|[CSplitterWnd:: RecalcLayout](#recalclayout)|을 호출 하 여 행 또는 열 크기를 조정한 후 분할자 창을 다시 표시 합니다.|
|[CSplitterWnd:: setactivep\](#setactivepane)|프레임의 활성 창이 되도록 창을 설정 합니다.|
|[CSplitterWnd:: SetColumnInfo](#setcolumninfo)|을 호출 하 여 지정 된 열 정보를 설정 합니다.|
|[CSplitterWnd:: SetRowInfo](#setrowinfo)|을 호출 하 여 지정 된 행 정보를 설정 합니다.|
|[CSplitterWnd:: SetScrollStyle](#setscrollstyle)|분할자 창의 공유 스크롤 막대 지원에 대 한 새로운 스크롤 막대 스타일을 지정 합니다.|
|[CSplitterWnd:: SplitColumn](#splitcolumn)|프레임 창이 세로로 분할 되는 위치를 나타냅니다.|
|[CSplitterWnd:: SplitRow](#splitrow)|프레임 창이 가로로 분할 되는 위치를 나타냅니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CSplitterWnd:: OnDraw](#ondraw)|분할자 창을 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CSplitterWnd:: OnDrawSplitter](#ondrawsplitter)|분할 창의 이미지를 렌더링 합니다.|
|[CSplitterWnd:: OnInvertTracker](#oninverttracker)|분할 창의 이미지를 프레임 창과 같은 크기 및 모양으로 렌더링 합니다.|

## <a name="remarks"></a>설명

창은 일반적으로 [CView](../../mfc/reference/cview-class.md)에서 파생 된 응용 프로그램 관련 개체 이지만 적절 한 자식 창 ID가 있는 모든 [CWnd](../../mfc/reference/cwnd-class.md) 개체가 될 수 있습니다.

`CSplitterWnd`개체는 일반적으로 부모 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 또는 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 개체에 포함 됩니다. `CSplitterWnd`다음 단계를 사용 하 여 개체를 만듭니다.

1. `CSplitterWnd`부모 프레임에 멤버 변수를 포함 합니다.

2. 부모 프레임의 [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) 멤버 함수를 재정의 합니다.

3. 재정의 된 내에서 `OnCreateClient` 의 [Create](#create) 또는 [CreateStatic](#createstatic) 멤버 함수를 호출 합니다 `CSplitterWnd` .

`Create`멤버 함수를 호출 하 여 동적 분할자 창을 만듭니다. 일반적으로 동적 분할자 창은 동일한 문서의 여러 개별 창 또는 뷰를 만들고 스크롤 하는 데 사용 됩니다. 프레임 워크는 분할자에 대 한 초기 창을 자동으로 만듭니다. 그러면 사용자가 분할자 창의 컨트롤을 작동할 때 프레임 워크에서 추가 창을 만들고 크기를 조정 하 고 삭제 합니다.

를 호출 하는 경우 `Create` 창이 너무 작아 완전히 표시 되지 않는 경우를 결정 하는 최소 행 높이 및 열 너비를 지정 합니다. 를 호출한 후에 `Create` 는 [Setcolumninfo](#setcolumninfo) 및 [setrowinin](#setrowinfo) 멤버 함수를 호출 하 여 이러한 최소값을 조정할 수 있습니다.

또한 `SetColumnInfo` 및 `SetRowInfo` 멤버 함수를 사용 하 여 열에 "이상적인" 너비를 설정 하 고 행에 "이상적인" 높이를 설정 합니다. 프레임 워크에서 분할자 창을 표시 하면 먼저 부모 프레임이 표시 된 다음 분할자 창이 표시 됩니다. 그런 다음 프레임 워크는 이상적인 차원에 따라 열과 행에 창을 배치 하 고 왼쪽 위에서 분할자 창의 클라이언트 영역 오른쪽 아래 모서리로 작업 합니다.

동적 분할자 창의 모든 창은 동일한 클래스 여야 합니다. 동적 분할자 창을 지 원하는 친숙 한 응용 프로그램에는 Microsoft Word 및 Microsoft Excel이 포함 됩니다.

`CreateStatic`멤버 함수를 사용 하 여 정적 분할자 창을 만들 수 있습니다. 사용자는 정적 분할자 창에 있는 창의 크기 (숫자나 순서 아님)만 변경할 수 있습니다.

정적 분할자를 만들 때는 정적 분할자의 모든 창을 구체적으로 만들어야 합니다. 부모 프레임의 멤버 함수가 반환 하기 전에 모든 창을 만들어야 `OnCreateClient` 합니다. 그렇지 않으면 프레임 워크에서 창을 올바르게 표시 하지 않습니다.

`CreateStatic`멤버 함수는 최소 행 높이와 열 너비가 0 인 정적 분할자를 자동으로 초기화 합니다. 를 호출한 후 `Create` 에는 [Setcolumninfo](#setcolumninfo) 및 [setrowinin](#setrowinfo) 멤버 함수를 호출 하 여 이러한 최소값을 조정 합니다. 또한를 `SetColumnInfo` `SetRowInfo` 호출 하 `CreateStatic` 여 원하는 이상적인 창 차원을 표시 하 고 나 서를 사용 합니다.

정적 분할자의 개별 창은 종종 서로 다른 클래스에 속합니다. 정적 분할자 창의 예제는 그래픽 편집기 및 Windows 파일 관리자를 참조 하세요.

분할자 창은 창에 있는 스크롤 막대를 제외한 특수 스크롤 막대를 지원 합니다. 이러한 스크롤 막대는 개체의 자식 `CSplitterWnd` 이며 창과 공유 됩니다.

분할자 창을 만들 때 이러한 특수 스크롤 막대를 만듭니다. 예를 들어 한 `CSplitterWnd` 행, 두 개의 열 및 WS_VSCROLL 스타일이 있는에는 두 창에서 공유 하는 세로 스크롤 막대가 표시 됩니다. 사용자가 스크롤 막대를 움직이면 WM_VSCROLL 메시지가 두 창으로 전송 됩니다. 창에서 스크롤 막대 위치를 설정 하면 공유 스크롤 막대가 설정 됩니다.

분할자 창에 대 한 자세한 내용은 [Technical Note 29](../../mfc/tn029-splitter-windows.md)를 참조 하십시오.

동적 분할자 창을 만드는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- MFC 샘플 [Scribble](../../overview/visual-cpp-samples.md)

- MFC 샘플 [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a> CSplitterWnd:: ActivateNext

다음 창이 나 이전 창 명령을 수행 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>매개 변수

*bPrev*<br/>
활성화할 창을 나타냅니다. 이전의 경우 **TRUE** 입니다. 다음의 경우 **FALSE** 입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 [CView](../../mfc/reference/cview-class.md) 클래스가 구현에 위임 하는 데 사용 하는 높은 수준의 명령입니다 `CSplitterWnd` .

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a> CSplitterWnd:: CanActivateNext

다음 창이 나 이전 창 명령이 현재 가능한 지 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>매개 변수

*bPrev*<br/>
활성화할 창을 나타냅니다. 이전의 경우 **TRUE** 입니다. 다음의 경우 **FALSE** 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 [CView](../../mfc/reference/cview-class.md) 클래스가 구현에 위임 하는 데 사용 하는 높은 수준의 명령입니다 `CSplitterWnd` .

## <a name="csplitterwndcreate"></a><a name="create"></a> CSplitterWnd:: Create

동적 분할자 창을 만들려면 `Create` 멤버 함수를 호출 합니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
분할자 창의 부모 프레임 창입니다.

*nMaxRows*<br/>
분할자 창에 있는 최대 행 수입니다. 이 값은 2를 초과 해서는 안 됩니다.

*nMaxCols*<br/>
분할자 창에 있는 열의 최대 개수입니다. 이 값은 2를 초과 해서는 안 됩니다.

*sizeMin*<br/>
창이 표시 될 수 있는 최소 크기를 지정 합니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 구조체에 대 한 포인터입니다. 대부분의 경우이는 부모 프레임 창에 전달 되는 *pContext* 수 있습니다.

*dwStyle*<br/>
창 스타일을 지정 합니다.

*nID*<br/>
창의 자식 창 ID입니다. 분할자 창이 다른 분할자 창 안에 중첩 되지 않은 경우 ID를 AFX_IDW_PANE_FIRST 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CSplitterWnd`다음 단계를 수행 하 여를 부모 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 또는 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 개체에 포함할 수 있습니다.

1. `CSplitterWnd`부모 프레임에 멤버 변수를 포함 합니다.

1. 부모 프레임의 [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) 멤버 함수를 재정의 합니다.

1. `Create`재정의 된 내에서 멤버 함수를 호출 합니다 `OnCreateClient` .

부모 프레임 내에서 분할자 창을 만들 때 부모 프레임의 *pContext* 매개 변수를 분할자 창에 전달 합니다. 그렇지 않으면이 매개 변수는 NULL 일 수 있습니다.

동적 분할자 창의 초기 최소 행 높이 및 열 너비는 *sizeMin* 매개 변수를 통해 설정 됩니다. 창이 너무 작아 완전히 표시 되지 않는지 여부를 확인 하는 이러한 최소값은 [Setrowinfo](#setrowinfo) 및 [setcolumninfo](#setcolumninfo) 멤버 함수로 변경할 수 있습니다.

동적 분할자 창에 대 한 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](../../mfc/multiple-document-types-views-and-frame-windows.md), [기술 참고 29](../../mfc/tn029-splitter-windows.md)및 클래스 개요 문서의 "분할자 창"을 참조 하십시오 `CSplitterWnd` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a> CSplitterWnd:: CreateScrollBarCtrl

공유 스크롤 막대 컨트롤을 만들기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
창 스타일을 지정 합니다.

*nID*<br/>
창의 자식 창 ID입니다. 분할자 창이 다른 분할자 창 안에 중첩 되지 않은 경우 ID를 AFX_IDW_PANE_FIRST 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateScrollBarCtrl`스크롤 막대 옆에 있는 추가 컨트롤을 포함 하도록를 재정의 합니다. 기본 동작은 일반 Windows scroll bar 컨트롤을 만드는 것입니다.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a> CSplitterWnd:: CreateStatic

정적 분할자 창을 만들려면 `CreateStatic` 멤버 함수를 호출 합니다.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
분할자 창의 부모 프레임 창입니다.

*nRows*<br/>
행의 수입니다. 이 값은 16을 초과할 수 없습니다.

*nCols*<br/>
열의 수입니다. 이 값은 16을 초과할 수 없습니다.

*dwStyle*<br/>
창 스타일을 지정 합니다.

*nID*<br/>
창의 자식 창 ID입니다. 분할자 창이 다른 분할자 창 안에 중첩 되지 않은 경우 ID를 AFX_IDW_PANE_FIRST 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

는 `CSplitterWnd` 일반적으로 `CFrameWnd` 다음 단계를 수행 하 여 부모 또는 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 개체에 포함 됩니다.

1. `CSplitterWnd`부모 프레임에 멤버 변수를 포함 합니다.

1. 부모 프레임의 `OnCreateClient` 멤버 함수를 재정의 합니다.

1. `CreateStatic`재정의 된 [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)내에서 멤버 함수를 호출 합니다.

정적 분할자 창에는 종종 다른 클래스에서 가져온 고정 된 수의 창이 포함 되어 있습니다.

정적 분할자 창을 만들 때 동시에 모든 창을 만들어야 합니다. [Createview](#createview) 멤버 함수는 일반적으로이 용도로 사용 되지만 다른 비 뷰 클래스도 만들 수 있습니다.

정적 분할자 창의 초기 최소 행 높이 및 열 너비는 0입니다. 창이 너무 작아 완전히 표시 되지 않는 경우를 확인 하는 이러한 최소값은 [Setrowinfo](#setrowinfo) 및 [setcolumninfo](#setcolumninfo) 멤버 함수를 사용 하 여 변경할 수 있습니다.

정적 분할자 창에 스크롤 막대를 추가 하려면 WS_HSCROLL 및 WS_VSCROLL 스타일을 *Dwstyle* 에 추가 합니다.

정적 분할자 창에 대 한 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technical Note 29](../../mfc/tn029-splitter-windows.md)및 클래스 개요 문서의 "분할자 창"을 참조 하십시오 `CSplitterWnd` .

## <a name="csplitterwndcreateview"></a><a name="createview"></a> CSplitterWnd:: CreateView

정적 분할자 창의 창을 만듭니다.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>매개 변수

*행*<br/>
새 뷰를 놓을 분할자 창 행을 지정 합니다.

*col*<br/>
새 뷰를 놓을 분할자 창 열을 지정 합니다.

*pViewClass*<br/>
새 뷰의 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 지정 합니다.

*sizeInit*<br/>
새 뷰의 초기 크기를 지정 합니다.

*pContext*<br/>
뷰를 만드는 데 사용 되는 생성 컨텍스트에 대 한 포인터입니다. 일반적으로 분할자 창이 만들어지는 부모 프레임의 재정의 된 [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) 멤버 함수에 전달 되는 *pContext* 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크가 분할자를 표시 하기 전에 정적 분할자 창의 모든 창을 만들어야 합니다.

또한 프레임 워크는 동적 분할자 창의 사용자가 창, 행 또는 열을 분할 하는 경우 새 창을 만들기 위해이 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a> CSplitterWnd:: CSplitterWnd

를 호출 하 여 `CSplitterWnd` 개체를 생성 합니다.

```
CSplitterWnd();
```

### <a name="remarks"></a>설명

`CSplitterWnd`두 단계로 개체를 생성 합니다. 먼저 개체를 만든 `CSplitterWnd` 다음 [Create](#create) member 함수를 호출 하는 생성자를 호출 합니다 .이 함수는 분할자 창을 만들고 개체에 연결 `CSplitterWnd` 합니다.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a> CSplitterWnd::D eleteColumn

분할자 창에서 열을 삭제 합니다.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>매개 변수

*colDelete*<br/>
삭제할 열을 지정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 동적 분할자 창의 논리를 구현 하기 위해 프레임 워크에서 호출 됩니다. 즉, 분할자 창에 SPLS_DYNAMIC_SPLIT 스타일이 있는 경우입니다. 가상 함수 [Createview](#createview)와 함께 사용자 지정 하 여 고급 동적 분할자를 구현할 수 있습니다.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a> CSplitterWnd::D eleteRow

분할자 창에서 행을 삭제 합니다.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>매개 변수

*rowDelete*<br/>
삭제할 행을 지정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 동적 분할자 창의 논리를 구현 하기 위해 프레임 워크에서 호출 됩니다. 즉, 분할자 창에 SPLS_DYNAMIC_SPLIT 스타일이 있는 경우입니다. 가상 함수 [Createview](#createview)와 함께 사용자 지정 하 여 고급 동적 분할자를 구현할 수 있습니다.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a> CSplitterWnd::D eleteView

분할자 창에서 뷰를 삭제 합니다.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>매개 변수

*행*<br/>
뷰를 삭제할 분할자 창 행을 지정 합니다.

*col*<br/>
뷰를 삭제할 분할자 창 열을 지정 합니다.

### <a name="remarks"></a>설명

활성 뷰를 삭제 하는 중이면 다음 뷰가 활성화 됩니다. 기본 구현에서는 뷰가 [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)에서 자동으로 삭제 되는 것으로 가정 합니다.

이 멤버 함수는 동적 분할자 창의 논리를 구현 하기 위해 프레임 워크에서 호출 됩니다. 즉, 분할자 창에 SPLS_DYNAMIC_SPLIT 스타일이 있는 경우입니다. 가상 함수 [Createview](#createview)와 함께 사용자 지정 하 여 고급 동적 분할자를 구현할 수 있습니다.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a> CSplitterWnd::D oKeyboardSplit

일반적으로 "창 분할"의 키보드 분할 명령을 수행 합니다.

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 [CView](../../mfc/reference/cview-class.md) 클래스가 구현에 위임 하는 데 사용 하는 높은 수준의 명령입니다 `CSplitterWnd` .

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a> CSplitterWnd::D oScroll

분할 창의 동기화 된 스크롤을 수행 합니다.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>매개 변수

*pViewFrom*<br/>
스크롤 메시지가 시작 되는 뷰에 대 한 포인터입니다.

*nScrollCode*<br/>
사용자의 스크롤 요청을 나타내는 스크롤 막대 코드입니다. 이 매개 변수는 두 부분으로 구성 됩니다. 즉, 가로로 발생 하는 스크롤의 유형을 결정 하는 하위 바이트와 세로로 발생 하는 스크롤의 유형을 결정 하는 상위 바이트입니다.

- SB_BOTTOM 아래쪽으로 스크롤됩니다.

- SB_LINEDOWN 한 줄 아래로 스크롤합니다.

- SB_LINEUP 한 줄 위로 스크롤합니다.

- SB_PAGEDOWN 한 페이지 아래로 스크롤합니다.

- SB_PAGEUP 한 페이지를 위로 스크롤합니다.

- SB_TOP 맨 위로 스크롤합니다.

*bDoScroll*<br/>
지정 된 스크롤 동작이 발생 하는지 여부를 확인 합니다. *Bdoscroll* 이 TRUE 이면 (즉, 자식 창이 있고 분할 창에 스크롤 범위가 있으면) 지정 된 스크롤 동작이 수행 될 수 있습니다. *Bdoscroll* 이 FALSE 이면 (즉, 자식 창이 없거나 분할 뷰에 스크롤 범위가 없는 경우) 스크롤이 수행 되지 않습니다.

### <a name="return-value"></a>반환 값

동기화 된 스크롤이 발생 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 뷰가 스크롤 메시지를 받을 때 분할 창의 동기화 된 스크롤을 수행 하기 위해 프레임 워크에서 호출 됩니다. 동기화 된 스크롤이 허용 되기 전에 사용자가 작업을 수행 하도록 하려면를 재정의 합니다.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a> CSplitterWnd::D oScrollBy

지정 된 픽셀 수 만큼 분할 창을 스크롤합니다.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>매개 변수

*pViewFrom*<br/>
스크롤 메시지가 시작 되는 뷰에 대 한 포인터입니다.

*sizeScroll*<br/>
가로 및 세로 방향으로 스크롤할 픽셀 수입니다.

*bDoScroll*<br/>
지정 된 스크롤 동작이 발생 하는지 여부를 확인 합니다. *Bdoscroll* 이 TRUE 이면 (즉, 자식 창이 있고 분할 창에 스크롤 범위가 있으면) 지정 된 스크롤 동작이 수행 될 수 있습니다. *Bdoscroll* 이 FALSE 이면 (즉, 자식 창이 없거나 분할 뷰에 스크롤 범위가 없는 경우) 스크롤이 수행 되지 않습니다.

### <a name="return-value"></a>반환 값

동기화 된 스크롤이 발생 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 *sizeScroll* 로 표시 되는 크기에 따라 분할 창의 동기화 된 스크롤을 수행 하기 위해 스크롤 메시지에 대 한 응답으로 프레임 워크에서 호출 됩니다. 양수 값은 아래로 스크롤하고 오른쪽으로 스크롤 하는 것을 의미 합니다. 음수 값은 위쪽 및 왼쪽으로 스크롤 하는 것을 의미 합니다.

Scroll을 허용 하기 전에 사용자가 작업을 수행 하도록 하려면를 재정의 합니다.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a> CSplitterWnd:: Getactivepgea

프레임의 포커스 또는 활성 뷰에서 활성 창을 결정 합니다.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>매개 변수

*pRow*<br/>
**`int`** 활성 창에 대 한 행 번호를 검색 하는에 대 한 포인터입니다.

*pCol*<br/>
**`int`** 활성 창의 열 번호를 검색 하는에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

활성 창에 대 한 포인터입니다. 활성 창이 없으면 NULL입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 분할자 창에서 활성 창을 확인 하기 위해 프레임 워크에서 호출 됩니다. 활성 창을 가져오기 전에 사용자가 작업을 수행 하도록 하려면를 재정의 합니다.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a> CSplitterWnd:: GetColumnCount

현재 창 열 수를 반환 합니다.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>반환 값

분할자의 현재 열 수를 반환 합니다. 정적 분할자의 경우이 값은 최대 열 수 이기도 합니다.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a> CSplitterWnd:: GetColumnInfo

지정 된 열에 대 한 정보를 반환 합니다.

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>매개 변수

*col*<br/>
열을 지정합니다.

*cxCur*<br/>
**`int`** 열의 현재 너비에 설정할에 대 한 참조입니다.

*cxMin*<br/>
**`int`** 열의 현재 최소 너비에 설정할에 대 한 참조입니다.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a> CSplitterWnd:: GetPane

지정 된 행과 열에 있는 창을 반환 합니다.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>매개 변수

*행*<br/>
행을 지정 합니다.

*col*<br/>
열을 지정합니다.

### <a name="return-value"></a>반환 값

지정 된 행과 열에 있는 창을 반환 합니다. 반환 된 창은 일반적으로 [CView](../../mfc/reference/cview-class.md)파생 클래스입니다.

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a> CSplitterWnd:: GetRowCount

현재 창 행 수를 반환 합니다.

```
int GetRowCount() const;
```

### <a name="return-value"></a>반환 값

분할자 창의 현재 행 수를 반환 합니다. 정적 분할자 창의 경우이는 최대 행 수 이기도 합니다.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a> CSplitterWnd:: GetRowInfo

지정 된 행에 대 한 정보를 반환 합니다.

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>매개 변수

*행*<br/>
행을 지정 합니다.

*cyCur*<br/>
**`int`** 행의 현재 높이 (픽셀)로 설정할에 대 한 참조입니다.

*cyMin*<br/>
**`int`** 행의 현재 최소 높이 (픽셀)로 설정할에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 지정 된 행에 대 한 정보를 가져옵니다. *CyCur* 매개 변수는 지정 된 행의 현재 높이로 채워지고 *cyMin* 은 행의 최소 높이로 채워집니다.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a> CSplitterWnd:: GetScrollStyle

분할자 창의 공유 스크롤 막대 스타일을 반환 합니다.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 다음 windows 스타일 플래그 중 하나 이상입니다.

- 분할자에서 현재 공유 가로 스크롤 막대를 관리 하는지 여부를 WS_HSCROLL 합니다.

- 분할자에서 현재 공유 세로 스크롤 막대를 관리 하는지 여부를 WS_VSCROLL 합니다.

0 인 경우 분할자 창은 현재 공유 스크롤 막대를 관리 하지 않습니다.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a> CSplitterWnd:: IdFromRowCol

지정 된 행 및 열에서 창의 자식 창 ID를 가져옵니다.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>매개 변수

*행*<br/>
분할자 창 행을 지정 합니다.

*col*<br/>
분할자 창 열을 지정 합니다.

### <a name="return-value"></a>반환 값

창의 자식 창 ID입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 뷰가 아닌 창을 만드는 데 사용 되며 창이 존재 하기 전에 호출 될 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a> CSplitterWnd:: IsChildPane

*PWnd* 가 현재이 분할자 창의 자식 창 인지 여부를 확인 합니다.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
테스트할 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다.

*pRow*<br/>
행 번호를 저장할에 대 한 포인터 **`int`** 입니다.

*pCol*<br/>
열 번호를 저장할에 대 한 포인터 **`int`** 입니다.

### <a name="return-value"></a>반환 값

0이 아니면 *pWnd* 는 현재이 분할자 창의 자식 창이 고 *Prow* 와 *pcol* 은 분할자 창에서 창의 위치로 채워집니다. *PWnd* 가이 분할자 창의 자식 창이 아닌 경우 0이 반환 됩니다.

### <a name="remarks"></a>설명

6.0 이전의 Visual C++ 버전에서이 함수는 다음과 같이 정의 되었습니다.

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

이 버전은 이제 사용 되지 않으며 사용 하지 않아야 합니다.

## <a name="csplitterwndistracking"></a><a name="istracking"></a> CSplitterWnd:: IsTracking

이 멤버 함수를 호출 하 여 창의 분할자 막대가 현재 이동 중인지 여부를 확인 합니다.

```
BOOL IsTracking();
```

### <a name="return-value"></a>반환 값

분할자 작업이 진행 중인 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a> CSplitterWnd:: OnDrawSplitter

분할 창의 이미지를 렌더링 합니다.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
그릴 장치 컨텍스트에 대 한 포인터입니다. *PDC* 가 NULL 이면 [CWnd:: redrawwindow](../../mfc/reference/cwnd-class.md#redrawwindow) 가 프레임 워크에서 호출 되 고 분할 창이 그려지지 않습니다.

*nType*<br/>
값으로 `enum ESplitType` , 다음 중 하나일 수 있습니다.

- `splitBox` 분할자 끌기 상자입니다.

- `splitBar` 분할 된 두 창 사이에 표시 되는 막대입니다.

- `splitIntersection` 분할 창의 교집합입니다. 이 요소는 Windows 95/98에서 실행 될 때 호출 되지 않습니다.

- `splitBorder` 분할 창 테두리입니다.

*rect*<br/>
분할 창의 크기와 모양을 지정 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 분할자 창의 정확한 특성을 그리거나 지정 하기 위해 프레임 워크에서 호출 됩니다. `OnDrawSplitter`분할자 창의 다양 한 그래픽 구성 요소에 대 한 이미지의 고급 사용자 지정을 재정의 합니다. 기본 이미지는 분할자 막대의 교차점을 함께 혼합 한다는 점에서 Windows 또는 Microsoft Windows 95/98에 대 한 Microsoft Works의 분할자와 비슷합니다.

동적 분할자 창에 대 한 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](../../mfc/multiple-document-types-views-and-frame-windows.md), [기술 참고 29](../../mfc/tn029-splitter-windows.md)및 클래스 개요 문서의 "분할자 창"을 참조 하십시오 `CSplitterWnd` .

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a> CSplitterWnd:: OnInvertTracker

분할 창의 이미지를 프레임 창과 같은 크기 및 모양으로 렌더링 합니다.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
추적 사각형을 지정 하는 개체에 대 한 참조 `CRect` 입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 분할자 크기를 조정 하는 동안 프레임 워크에서 호출 됩니다. `OnInvertTracker`분할자 창의 이미지에 대 한 고급 사용자 지정을 재정의 합니다. 기본 이미지는 분할자 막대의 교차점을 함께 혼합 한다는 점에서 Windows 또는 Microsoft Windows 95/98에 대 한 Microsoft Works의 분할자와 비슷합니다.

동적 분할자 창에 대 한 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](../../mfc/multiple-document-types-views-and-frame-windows.md), [기술 참고 29](../../mfc/tn029-splitter-windows.md)및 클래스 개요 문서의 "분할자 창"을 참조 하십시오 `CSplitterWnd` .

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a> CSplitterWnd:: RecalcLayout

을 호출 하 여 행 또는 열 크기를 조정한 후 분할자 창을 다시 표시 합니다.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 행 및 열 크기를 [Setrowinfo](#setrowinfo) 및 [setcolumninfo](#setcolumninfo) 멤버 함수로 조정한 후 분할자 창을 올바르게 다시 표시 합니다. 분할 창이 표시 되기 전의 생성 프로세스의 일부로 행 및 열 크기를 변경 하는 경우에는이 멤버 함수를 호출할 필요가 없습니다.

프레임 워크는 사용자가 분할자 창의 크기를 조정 하거나 분할을 이동할 때마다이 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

  [CSplitterWnd:: SetColumnInfo](#setcolumninfo)의 예제를 참조 하세요.

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a> CSplitterWnd:: setactivep\

프레임의 활성 창이 되도록 창을 설정 합니다.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*행*<br/>
*PWnd* 가 NULL 인 경우 활성 상태가 되는 창의 행을 지정 합니다.

*col*<br/>
*PWnd* 이 NULL 이면 창의 열을 활성 상태로 지정 합니다.

*pWnd*<br/>
`CWnd` 개체에 대한 포인터입니다. NULL 인 경우 *행* 및 *열* 로 지정 된 창이 활성 상태로 설정 됩니다. NULL이 아닌 경우 활성으로 설정 된 창을 지정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 프레임 창 내에서 사용자가 포커스를 창으로 변경 하는 경우 창을 활성으로 설정 하기 위해 프레임 워크에서 호출 됩니다. 를 명시적으로 호출 `SetActivePane` 하 여 포커스를 지정 된 뷰로 변경할 수 있습니다.

행과 열 중 하나를 제공 **하거나** *pWnd* 을 제공 하 여 창을 지정 합니다.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a> CSplitterWnd:: SetColumnInfo

을 호출 하 여 지정 된 열 정보를 설정 합니다.

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>매개 변수

*col*<br/>
분할자 창 열을 지정 합니다.

*cxIdeal*<br/>
분할자 창 열의 이상적인 너비 (픽셀)를 지정 합니다.

*cxMin*<br/>
분할자 창 열의 최소 너비 (픽셀)를 지정 합니다.

### <a name="remarks"></a>설명

열에 대 한 새 최소 너비 및 이상적인 너비를 설정 하려면이 멤버 함수를 호출 합니다. 열 최소값은 열이 너무 작아 완전히 표시 되지 않는 경우를 결정 합니다.

프레임 워크에서 분할자 창을 표시 하면 왼쪽 위에서 분할자 창의 클라이언트 영역 오른쪽 아래 모서리로 작업 하 여 이상적인 차원에 따라 열과 행에 창이 배치 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a> CSplitterWnd:: SetRowInfo

을 호출 하 여 지정 된 행 정보를 설정 합니다.

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>매개 변수

*행*<br/>
분할자 창 행을 지정 합니다.

*cyIdeal*<br/>
분할자 창 행의 이상적인 높이 (픽셀)를 지정 합니다.

*cyMin*<br/>
분할자 창 행의 최소 높이 (픽셀)를 지정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 행의 최대 높이와 이상적인 높이를 새로 설정 합니다. 행 최소값은 행이 너무 작아 완전히 표시 되지 않는 경우를 결정 합니다.

프레임 워크에서 분할자 창을 표시 하면 왼쪽 위에서 분할자 창의 클라이언트 영역 오른쪽 아래 모서리로 작업 하 여 이상적인 차원에 따라 열과 행에 창이 배치 됩니다.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a> CSplitterWnd:: SetScrollStyle

분할자 창의 공유 스크롤 막대 지원에 대 한 새 스크롤 스타일을 지정 합니다.

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
분할자 창의 공유 스크롤 막대 지원에 대 한 새로운 스크롤 스타일로, 다음 값 중 하나일 수 있습니다.

- WS_HSCROLL 가로 공유 스크롤 막대를 만들거나 표시 합니다.

- 세로 공유 스크롤 막대를 만들거나 표시 WS_VSCROLL 합니다.

### <a name="remarks"></a>설명

스크롤 막대를 만든 후에는 해당 스타일 없이를 호출한 경우에도 제거 되지 않습니다 `SetScrollStyle` . 대신 해당 스크롤 막대가 숨겨집니다. 이렇게 하면 스크롤 막대가 숨겨진 경우에도 해당 상태를 유지할 수 있습니다. 호출 후 `SetScrollStyle` 모든 변경 내용을 적용 하려면 [RecalcLayout](#recalclayout) 를 호출 해야 합니다.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a> CSplitterWnd:: SplitColumn

프레임 창이 세로로 분할 되는 위치를 나타냅니다.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>매개 변수

*cxBefore*<br/>
분할이 발생 하는 위치 (픽셀)입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 세로 분할자 창을 만들 때 호출 됩니다. `SplitColumn` 분할이 발생 하는 기본 위치를 나타냅니다.

`SplitColumn` 는 동적 분할자 창의 논리를 구현 하기 위해 프레임 워크에서 호출 됩니다. 즉, 분할자 창에 SPLS_DYNAMIC_SPLIT 스타일이 있는 경우입니다. 가상 함수 [Createview](#createview)와 함께 사용자 지정 하 여 고급 동적 분할자를 구현할 수 있습니다.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a> CSplitterWnd:: SplitRow

프레임 창이 가로로 분할 되는 위치를 나타냅니다.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>매개 변수

*cyBefore*<br/>
분할이 발생 하는 위치 (픽셀)입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 가로 분할자 창을 만들 때 호출 됩니다. `SplitRow` 분할이 발생 하는 기본 위치를 나타냅니다.

`SplitRow` 는 동적 분할자 창의 논리를 구현 하기 위해 프레임 워크에서 호출 됩니다. 즉, 분할자 창에 SPLS_DYNAMIC_SPLIT 스타일이 있는 경우입니다. 가상 함수 [Createview](#createview)와 함께 사용자 지정 하 여 고급 동적 분할자를 구현할 수 있습니다.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a> CSplitterWnd:: OnDraw

분할자 창을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
디바이스 컨텍스트에 대한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[MFC 샘플 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)
