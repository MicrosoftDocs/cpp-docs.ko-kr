---
description: '자세히 알아보기: CMFCHeaderCtrl 클래스'
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: a6be476e095dc4a013705657e259a90d7cafe0d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265378"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

`CMFCHeaderCtrl`클래스는 헤더 컨트롤에서 여러 열의 정렬을 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCHeaderCtrl:: CMFCHeaderCtrl](#cmfcheaderctrl)|`CMFCHeaderCtrl` 개체를 생성합니다.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCHeaderCtrl:: EnableMultipleSort](#enablemultiplesort)|현재 헤더 컨트롤에 대해 *여러 열 정렬* 모드를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCHeaderCtrl:: GetColumnState](#getcolumnstate)|열이 정렬 되지 않았거나 오름차순 또는 내림차순으로 정렬 되는지 여부를 나타냅니다.|
|[CMFCHeaderCtrl:: GetSortColumn](#getsortcolumn)|헤더 컨트롤에서 정렬 된 첫 번째 열의 인덱스 (0부터 시작)를 검색 합니다.|
|`CMFCHeaderCtrl::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCHeaderCtrl:: IsAscending](#isascending)|머리글 컨트롤의 열이 오름차순으로 정렬 되는지 여부를 나타냅니다.|
|[CMFCHeaderCtrl:: IsDialogControl](#isdialogcontrol)|현재 머리글 컨트롤의 부모 창이 대화 상자 인지 여부를 나타냅니다.|
|[CMFCHeaderCtrl:: IsMultipleSort](#ismultiplesort)|현재 헤더 컨트롤이 *여러 열 정렬* 모드에 있는지 여부를 나타냅니다.|
|[CMFCHeaderCtrl:: RemoveSortColumn](#removesortcolumn)|정렬 열 목록에서 지정 된 열을 제거 합니다.|
|[CMFCHeaderCtrl:: SetSortColumn](#setsortcolumn)|헤더 컨트롤에서 지정 된 열의 정렬 순서를 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCHeaderCtrl:: OnDrawItem](#ondrawitem)|헤더 컨트롤 열을 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCHeaderCtrl:: OnDrawSortArrow](#ondrawsortarrow)|정렬 화살표를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCHeaderCtrl:: OnFillBackground](#onfillbackground)|헤더 제어 열의 배경을 채우기 위해 프레임 워크에서 호출 됩니다.|

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법과 `CMFCHeaderCtrl` 현재 헤더 컨트롤에 *여러 열 정렬* 모드를 사용 하도록 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>설명

`CMFCHeaderCtrl`클래스는 열이 정렬 되는 것을 나타내기 위해 header 컨트롤 열에 정렬 화살표를 그립니다. 부모 목록 컨트롤 ( [CMFCListCtrl 클래스](../../mfc/reference/cmfclistctrl-class.md))의 열 집합을 동시에 정렬할 수 있는 경우 *여러 열 정렬* 모드를 사용 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxheaderctrl

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a> CMFCHeaderCtrl:: CMFCHeaderCtrl

`CMFCHeaderCtrl` 개체를 생성합니다.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>설명

이 생성자는 다음 멤버 변수를 지정 된 값으로 초기화 합니다.

|멤버 변수|값|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a> CMFCHeaderCtrl:: EnableMultipleSort

현재 헤더 컨트롤에 대해 *여러 열 정렬* 모드를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 여러 열 정렬 모드를 사용 하려면 TRUE로 설정 합니다. 여러 열 정렬 모드를 사용 하지 않도록 설정 하 고 정렬 된 열 목록에서 열을 제거 하려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 여러 열 정렬 모드를 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 헤더 컨트롤이 여러 열 정렬 모드에 있는 경우 두 개 이상의 열이 정렬에 참여할 수 있습니다.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a> CMFCHeaderCtrl:: GetColumnState

열이 정렬 되지 않았거나 오름차순 또는 내림차순으로 정렬 되는지 여부를 나타냅니다.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 열의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 열의 정렬 상태를 나타내는 값입니다. 다음 테이블에서는 가능한 값을 나열합니다.

|값|설명|
|-----------|-----------------|
|-1|내림차순으로 정렬 됩니다.|
|0|정렬 되지 않았습니다.|
|1|오름차순으로 정렬 됩니다.|

### <a name="remarks"></a>설명

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a> CMFCHeaderCtrl:: GetSortColumn

헤더 컨트롤에서 정렬 된 첫 번째 열의 인덱스 (0부터 시작)를 검색 합니다.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>반환 값

정렬 된 열의 인덱스 이거나, 정렬 된 열이 없는 경우-1입니다.

### <a name="remarks"></a>설명

헤더 컨트롤이 *여러 열 정렬* 모드에 있고 디버그 모드에서 응용 프로그램을 컴파일한 경우이 메서드는 [CMFCHeaderCtrl:: GetColumnState](#getcolumnstate) 메서드를 대신 사용 하는 것을 어설션 하 고 제안 합니다. 헤더 컨트롤이 여러 열 정렬 모드에 있고 정품 모드로 응용 프로그램을 컴파일한 경우이 메서드는-1을 반환 합니다.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a> CMFCHeaderCtrl:: IsAscending

머리글 컨트롤의 열이 오름차순으로 정렬 되는지 여부를 나타냅니다.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>반환 값

머리글 컨트롤의 열이 오름차순으로 정렬 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드가 반환 하는 값은 헤더 컨트롤 항목에 적절 한 정렬 화살표를 표시 하는 데 사용 됩니다. [CMFCHeaderCtrl:: SetSortColumn](#setsortcolumn) 메서드를 사용 하 여 정렬 순서를 설정 합니다.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a> CMFCHeaderCtrl:: IsDialogControl

현재 머리글 컨트롤의 부모 창이 대화 상자 인지 여부를 나타냅니다.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>반환 값

현재 머리글 컨트롤의 부모 창이 대화 상자 이면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a> CMFCHeaderCtrl:: IsMultipleSort

현재 헤더 컨트롤이 *여러 열 정렬* 모드에 있는지 여부를 나타냅니다.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>반환 값

여러 열 정렬 모드를 사용할 수 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CMFCHeaderCtrl:: EnableMultipleSort](#enablemultiplesort) 메서드를 사용 하 여 여러 열 정렬 모드를 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 헤더 컨트롤이 여러 열 정렬 모드에 있는 경우 두 개 이상의 열이 정렬에 참여할 수 있습니다.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a> CMFCHeaderCtrl:: OnDrawItem

헤더 컨트롤 열을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*iItem*<br/>
진행 그릴 항목의 인덱스 (0부터 시작)입니다.

*rect*<br/>
진행 그릴 항목의 경계 사각형입니다.

*bIsPressed*<br/>
진행 누름 상태로 항목을 그리려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*bIsHighlighted*<br/>
진행 항목을 강조 표시 된 상태로 그리려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a> CMFCHeaderCtrl:: OnDrawSortArrow

정렬 화살표를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectArrow*<br/>
진행 정렬 화살표의 경계 사각형입니다.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a> CMFCHeaderCtrl:: OnFillBackground

헤더 제어 열의 배경을 채우기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a> CMFCHeaderCtrl:: RemoveSortColumn

정렬 열 목록에서 지정 된 열을 제거 합니다.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 제거할 열의 인덱스 (0부터 시작)입니다.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a> CMFCHeaderCtrl:: SetSortColumn

헤더 컨트롤에서 지정 된 열의 정렬 순서를 설정 합니다.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 헤더 제어 열의 인덱스 (0부터 시작)입니다. 이 매개 변수가 0 보다 작은 경우이 메서드는 정렬 열 목록에서 모든 열을 제거 합니다.

*가 나 끝*<br/>
진행 *IColumn* 매개 변수가 지정 하는 열의 정렬 순서를 지정 합니다. 오름차순으로 설정 하려면 TRUE로 설정 합니다. 내림차순으로 설정 하려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

*bAdd*<br/>
진행 *IColumn* 매개 변수가 지정 하는 열의 정렬 순서를 설정 하려면 TRUE로 설정 합니다.

현재 헤더 컨트롤이 *여러 열 정렬* 모드에 있으면이 메서드는 지정 된 열을 정렬 열 목록에 추가 합니다. [CMFCHeaderCtrl:: EnableMultipleSort](#enablemultiplesort) 를 사용 하 여 여러 열 정렬 모드를 설정 합니다.

여러 열 정렬 모드가 설정 되어 있지 않고이 메서드가 디버그 모드에서 컴파일되는 경우이 메서드는를 어설션 합니다. 여러 열 정렬 모드를 설정 하지 않은 경우이 메서드가 일반 정품 모드로 컴파일되면이 메서드는 먼저 정렬 열 목록에서 모든 열을 제거한 다음 지정 된 열을 목록에 추가 합니다.

정렬 열 목록에서 모든 열을 먼저 제거한 다음 지정 된 열을 목록에 추가 하려면 FALSE로 설정 합니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 열의 정렬 순서를 설정할 수 있습니다. 필요한 경우이 메서드는 열을 정렬 열 목록에 추가 합니다. 헤더 컨트롤은 정렬 순서를 사용 하 여 위나 아래로 가리키는 정렬 화살표를 그립니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 클래스](../../mfc/reference/cmfclistctrl-class.md)
