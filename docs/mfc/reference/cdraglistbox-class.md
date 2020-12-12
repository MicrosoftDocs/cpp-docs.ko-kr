---
description: '자세히 알아보기: CDragListBox 클래스'
title: CDragListBox 클래스
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: 0dfa61503bd9c1aa3017d37b873a8948f61e68e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184767"
---
# <a name="cdraglistbox-class"></a>CDragListBox 클래스

클래스를 사용 하면 Windows 목록 상자의 기능을 제공 하는 것 외에도 `CDragListBox` 사용자가 목록 상자 내에서 파일 이름과 같은 목록 상자 항목을 이동할 수 있습니다.

## <a name="syntax"></a>구문

```
class CDragListBox : public CListBox
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDragListBox:: CDragListBox](#cdraglistbox)|`CDragListBox` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDragListBox:: BeginDrag](#begindrag)|끌기 작업이 시작 될 때 프레임 워크에서 호출 됩니다.|
|[CDragListBox:: CancelDrag](#canceldrag)|끌기 작업이 취소 될 때 프레임 워크에서 호출 됩니다.|
|[CDragListBox::D ragging](#dragging)|끌기 작업을 수행 하는 동안 프레임 워크에서 호출 됩니다.|
|[CDragListBox::D rawInsert](#drawinsert)|끌기 목록 상자의 삽입 안내선을 그립니다.|
|[CDragListBox::D ropped](#dropped)|항목이 삭제 된 후 프레임 워크에서 호출 됩니다.|
|[CDragListBox:: ItemFromPt](#itemfrompt)|끌고 있는 항목의 좌표를 반환 합니다.|

## <a name="remarks"></a>설명

이 기능을 사용 하는 목록 상자를 통해 사용자는 목록에서 항목을 정렬 하 여 가장 유용한 방식으로 나열할 수 있습니다. 기본적으로 목록 상자는 항목을 목록의 새 위치로 이동 합니다. 그러나 `CDragListBox` 항목을 이동 하지 않고 복사 하도록 개체를 사용자 지정할 수 있습니다.

클래스와 연결 된 목록 상자 컨트롤은 `CDragListBox` LBS_SORT 또는 LBS_MULTIPLESELECT 스타일을 포함 하지 않아야 합니다. 목록 상자 스타일에 대 한 설명은 [목록 상자 스타일](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)을 참조 하세요.

응용 프로그램의 기존 대화 상자에서 끌기 목록 상자를 사용 하려면 대화 상자 편집기를 사용 하 여 대화 상자 템플릿에 목록 상자 컨트롤을 추가한 다음 `Control` `CDragListBox` 대화 상자 템플릿의 목록 상자 컨트롤에 해당 하는 멤버 변수 (범주 및 변수 형식)를 할당 합니다.

멤버 변수에 컨트롤을 할당 하는 방법에 대 한 자세한 내용은 [대화 상자 컨트롤의 멤버 변수를 정의 하는 바로 가기](../../windows/adding-editing-or-deleting-controls.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a> CDragListBox:: BeginDrag

왼쪽 마우스 단추를 누르는 등의 끌기 작업을 시작할 수 있는 이벤트가 발생할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
끌고 있는 항목의 좌표를 포함 하는 [Cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

끌기가 허용 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

끌기 작업이 시작 될 때 발생 하는 동작을 제어 하려면이 함수를 재정의 합니다. 기본 구현에서는 마우스를 캡처하고 사용자가 왼쪽 또는 오른쪽 마우스 단추를 클릭 하거나 ESC 키를 누를 때까지 끌기 작업이 취소 될 때까지 끌기 모드를 유지 합니다.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a> CDragListBox:: CancelDrag

끌기 작업이 취소 될 때 프레임 워크에서 호출 됩니다.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
끌고 있는 항목의 좌표를 포함 하는 [Cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

### <a name="remarks"></a>설명

목록 상자 컨트롤에 대 한 특수 처리를 처리 하려면이 함수를 재정의 합니다.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a> CDragListBox:: CDragListBox

`CDragListBox` 개체를 생성합니다.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a> CDragListBox::D ragging

목록 상자 항목을 개체 내에서 끌 때 프레임 워크에서 호출 됩니다 `CDragListBox` .

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
커서의 x 및 y 화면 좌표를 포함 하는 [Cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

표시할 커서의 리소스 ID입니다. 다음 값을 사용할 수 있습니다.

- DL_COPYCURSOR 항목이 복사 됨을 나타냅니다.

- DL_MOVECURSOR 항목이 이동 됨을 나타냅니다.

- DL_STOPCURSOR는 현재 놓기 대상이 허용 되지 않음을 나타냅니다.

### <a name="remarks"></a>설명

기본 동작은 DL_MOVECURSOR을 반환 합니다. 추가 기능을 제공 하려는 경우이 함수를 재정의 합니다.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a> CDragListBox::D rawInsert

표시 된 인덱스를 가진 항목 앞에 삽입 안내선을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
삽입 지점의 0부터 시작 하는 인덱스입니다.

### <a name="remarks"></a>설명

-1 값은 삽입 안내선을 지웁니다. 삽입 안내선의 모양이 나 동작을 수정 하려면이 함수를 재정의 합니다.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a> CDragListBox::D ropped

개체 내에서 항목을 삭제할 때 프레임 워크에서 호출 `CDragListBox` 됩니다.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>매개 변수

*nSrcIndex*<br/>
삭제 된 문자열의 인덱스 (0부터 시작)를 지정 합니다.

*pt*<br/>
드롭 사이트의 좌표가 포함 된 [Cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

### <a name="remarks"></a>설명

기본 동작은 목록 상자 항목과 해당 데이터를 새 위치에 복사한 다음 원래 항목을 삭제 합니다. 목록 내의 다른 위치로 끌어 올 목록 상자 항목의 복사본을 사용 하도록 설정 하는 등의 기본 동작을 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a> CDragListBox:: ItemFromPt

*Pt* 에 있는 목록 상자 항목의 인덱스 (0부터 시작)를 검색 하려면이 함수를 호출 합니다.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
목록 상자 내 점의 좌표를 포함 하는 [Cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

*bAutoScroll*<br/>
스크롤이 허용 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="return-value"></a>반환 값

끌어서 목록 상자 항목의 인덱스 (0부터 시작)입니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)
