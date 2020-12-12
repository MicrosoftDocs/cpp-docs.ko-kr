---
description: '자세히 알아보기: CMFCListCtrl 클래스'
title: CMFCListCtrl 클래스
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 6b62522b7b126552c3f49c423300fadb59f406f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265183"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 클래스

`CMFCListCtrl`클래스는 [CMFCHeaderCtrl 클래스](../../mfc/reference/cmfcheaderctrl-class.md)의 고급 헤더 컨트롤 기능을 지원 하 여 [CListCtrl 클래스](../../mfc/reference/clistctrl-class.md) 클래스의 기능을 확장 합니다.

## <a name="syntax"></a>구문

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|정렬 된 열을 다른 배경색으로 표시할 수 있습니다.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|여러 정렬 모드를 사용 합니다.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|밑줄이 있는 머리글 컨트롤에 대 한 참조를 반환 합니다.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|목록 컨트롤이 여러 정렬 모드 인지 여부를 확인 합니다.|
|[CMFCListCtrl:: OnCompareItems](#oncompareitems)|두 목록 컨트롤 항목을 비교 해야 하는 경우 프레임 워크에서 호출 됩니다.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|개별 셀의 배경색을 결정 해야 하는 경우 프레임 워크에서 호출 됩니다.|
|[CMFCListCtrl:: Ongetfont 글꼴](#ongetcellfont)|그리고 있는 셀의 글꼴을 가져와야 할 때 프레임 워크에서 호출 됩니다.|
|[CMFCListCtrl:: Ongeto Textcolor](#ongetcelltextcolor)|개별 셀의 텍스트 색을 결정 해야 하는 경우 프레임 워크에서 호출 됩니다.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|정렬 된 열 목록에서 정렬 열을 제거 합니다.|
|[CMFCListCtrl:: SetSortColumn](#setsortcolumn)|현재 정렬 된 열과 정렬 순서를 설정 합니다.|
|[CMFCListCtrl:: Sort](#sort)|목록 컨트롤을 정렬 합니다.|

## <a name="remarks"></a>설명

`CMFCListCtrl` 에서는 [CListCtrl 클래스](../../mfc/reference/clistctrl-class.md) 클래스에 대 한 두 가지 향상 된 기능을 제공 합니다. 첫째, 머리글에 정렬 화살표를 자동으로 그려 열 정렬이 사용 가능한 옵션 임을 나타냅니다. 둘째, 동시에 여러 열에 대 한 데이터 정렬을 지원 합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCListCtrl` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 목록 컨트롤을 만들고, 열을 삽입 하 고, 항목을 삽입 하 고, 항목의 텍스트를 설정 하 고, 목록 컨트롤의 글꼴을 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxlistctrl

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a> CMFCListCtrl::EnableMarkSortedColumn

정렬 된 열을 다른 배경색으로 표시 합니다.

```cpp
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*bMark*<br/>
진행 다른 배경색을 사용할지 여부를 결정 하는 부울 매개 변수입니다.

*bRedraw*<br/>
진행 컨트롤을 즉시 다시 그릴지 여부를 결정 하는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

`EnableMarkSortedColumn` 메서드를 사용 하 여 `CDrawingManager::PixelAlpha` 정렬 된 열에 사용할 색을 계산 합니다. 선택한 색은 일반 배경색을 기반으로 합니다.

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a> CMFCListCtrl::EnableMultipleSort

목록 컨트롤의 데이터 행을 여러 열로 정렬할 수 있도록 합니다.

```cpp
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 여러 열 정렬 모드를 사용할지 여부를 지정 하는 부울입니다.

### <a name="remarks"></a>설명

여러 열을 기준으로 정렬을 사용 하도록 설정 하면 열에 계층이 포함 됩니다. 데이터 행은 먼저 주 열을 기준으로 정렬 됩니다. 그런 다음 우선 순위에 따라 각 후속 열을 기준으로 모든 동등한 값이 정렬 됩니다.

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a> CMFCListCtrl::GetHeaderCtrl

헤더 컨트롤에 대 한 참조를 반환 합니다.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>반환 값

기본 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

목록 컨트롤에 대 한 헤더 컨트롤은 열 제목을 포함 하는 창입니다. 일반적으로 열 바로 위에 배치 됩니다.

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a> CMFCListCtrl::IsMultipleSort

목록 컨트롤이 현재 여러 열에 대 한 정렬을 지원 하는지 여부를 확인 합니다.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>반환 값

목록 컨트롤이 여러 정렬을 지 원하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CMFCListCtrl 클래스가](../../mfc/reference/cmfclistctrl-class.md) 여러 정렬을 지 원하는 경우 사용자가 목록 컨트롤의 데이터를 여러 열로 정렬할 수 있습니다. 여러 정렬을 사용 하려면 [CMFCListCtrl:: EnableMultipleSort](#enablemultiplesort)를 호출 합니다.

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a> CMFCListCtrl:: OnCompareItems

프레임 워크는 두 항목을 비교할 때이 메서드를 호출 합니다.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>매개 변수

*lParam1*<br/>
진행 비교할 첫 번째 항목입니다.

*lParam2*<br/>
진행 비교할 두 번째 항목입니다.

*iColumn*<br/>
진행 이 메서드가 정렬 하는 열의 인덱스입니다.

### <a name="return-value"></a>반환 값

두 항목의 상대 위치를 나타내는 정수입니다. 음수 값은 첫 번째 항목이 두 번째 항목 앞에와 야 함을 나타내고, 양수 값은 첫 번째 항목이 두 번째를 따라야 함을 나타내고, 0은 두 항목이 동일 함을 나타냅니다.

### <a name="remarks"></a>설명

기본 구현에서는 항상 0을 반환 합니다. 이 함수를 재정의 하 여 고유한 정렬 알고리즘을 제공 합니다.

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a> CMFCListCtrl::OnGetCellBkColor

프레임 워크는 개별 셀의 배경색을 결정 해야 하는 경우이 메서드를 호출 합니다.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>매개 변수

*nRow*<br/>
진행 해당 셀의 행입니다.

*nColumn*<br/>
진행 해당 셀의 열입니다.

### <a name="return-value"></a>반환 값

셀의 배경색을 지정 하는 COLOREF 값입니다.

### <a name="remarks"></a>설명

의 기본 구현에서는 `OnGetCellBkColor` 제공 된 입력 매개 변수를 사용 하지 않고만 호출 `GetBkColor` 합니다. 따라서 기본적으로 전체 목록 컨트롤은 같은 배경색을 갖습니다. `OnGetCellBkColor`별도의 배경색으로 개별 셀을 표시 하도록 파생 클래스에서 재정의할 수 있습니다.

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a> CMFCListCtrl:: Ongetfont 글꼴

프레임 워크는 개별 셀의 글꼴을 가져올 때이 메서드를 호출 합니다.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>매개 변수

*nRow*<br/>
진행 해당 셀의 행입니다.

*nColumn*<br/>
진행 해당 셀의 열입니다.

*dwData*<br/>
진행 사용자 정의 데이터입니다. 기본 구현에서는이 매개 변수를 사용 하지 않습니다.

### <a name="return-value"></a>반환 값

현재 셀에 사용 되는 글꼴에 대 한 핸들입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 NULL을 반환 합니다. 목록 컨트롤의 모든 셀에는 동일한 글꼴이 있습니다. 셀 마다 다른 글꼴을 제공 하려면이 메서드를 재정의 합니다.

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a> CMFCListCtrl:: Ongeto Textcolor

프레임 워크는 개별 셀의 텍스트 색을 결정 해야 하는 경우이 메서드를 호출 합니다.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>매개 변수

*nRow*<br/>
진행 해당 셀의 행입니다.

*nColumn*<br/>
진행 해당 셀의 열입니다.

### <a name="return-value"></a>반환 값

셀의 텍스트 색을 지정 하는 COLOREF 값입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 `GetTextColor` 입력 매개 변수에 관계 없이를 호출 합니다. 전체 목록 컨트롤의 텍스트 색이 동일 합니다. `OnGetCellTextColor`파생 클래스에서를 재정의 하 여 개별 셀을 개별 텍스트 색으로 표시할 수 있습니다.

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a> CMFCListCtrl::RemoveSortColumn

정렬 된 열 목록에서 정렬 열을 제거 합니다.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 제거할 열입니다.

### <a name="remarks"></a>설명

이 메서드는 헤더 컨트롤에서 정렬 열을 제거 합니다. [CMFCHeaderCtrl:: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)를 호출 합니다.

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a> CMFCListCtrl:: SetSortColumn

현재 정렬 된 열과 정렬 순서를 설정 합니다.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 정렬할 열입니다.

*가 나 끝*<br/>
진행 정렬 순서를 지정 하는 부울입니다.

*bAdd*<br/>
진행 메서드가 *iColumn* 으로 표시 된 열을 정렬 열 목록에 추가할지 여부를 지정 하는 부울입니다.

### <a name="remarks"></a>설명

이 메서드는 [CMFCHeaderCtrl:: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)메서드를 사용 하 여 헤더 컨트롤에 입력 매개 변수를 전달 합니다.

## <a name="cmfclistctrlsort"></a><a name="sort"></a> CMFCListCtrl:: Sort

목록 컨트롤을 정렬 합니다.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>매개 변수

*iColumn*<br/>
진행 정렬할 열입니다.

*가 나 끝*<br/>
진행 정렬 순서를 지정 하는 부울입니다.

*bAdd*<br/>
진행 이 메서드가 *iColumn* 로 표시 된 열을 정렬 열 목록에 추가할지 여부를 지정 하는 부울입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 클래스](../../mfc/reference/clistctrl-class.md)
