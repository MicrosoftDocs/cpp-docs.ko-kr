---
description: '자세히 알아보기: CMFCToolBarComboBoxButton 클래스'
title: CMFCToolBarComboBoxButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: aa28d1b125a5e1baf56a9e6e10812e7e6e56312f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163914"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 클래스

콤보 상자 컨트롤 ( [Ccombobox 클래스](../../mfc/reference/ccombobox-class.md))을 포함 하는 도구 모음 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|`CMFCToolBarComboBoxButton`를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolBarComboBoxButton:: AddItem](#additem)|콤보 상자 목록의 끝에 항목을 추가 합니다.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|콤보 상자 목록에 항목을 추가 합니다. 목록에서 항목의 순서는에 의해 지정 됩니다 `Compare` .|
|[CMFCToolBarComboBoxButton:: Compare](#compare)|두 항목을 비교 합니다. 콤보 상자 목록에를 추가 하는 항목을 정렬 하기 위해 호출 `AddSortedItems` 됩니다.|
|[CMFCToolBarComboBoxButton:: CreateEdit](#createedit)|콤보 상자 단추에 대 한 새 편집 컨트롤을 만듭니다.|
|[CMFCToolBarComboBoxButton::D eleteItem](#deleteitem)|콤보 상자 목록에서 항목을 삭제 합니다.|
|[CMFCToolBarComboBoxButton:: FindItem](#finditem)|지정 된 문자열이 포함 된 항목의 인덱스를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetByCmd](#getbycmd)|지정 된 명령 ID를 사용 하 여 콤보 상자 단추에 대 한 포인터를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetComboBox](#getcombobox)|콤보 상자 단추에 포함 된 콤보 상자 컨트롤에 대 한 포인터를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetCount](#getcount)|콤보 상자 목록의 항목 수를 반환 합니다.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾습니다. 해당 단추의 콤보 상자 목록에 있는 항목 수를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetCurSel](#getcursel)|콤보 상자 목록에서 선택한 항목의 인덱스를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetCurSelAll](#getcurselall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾고 해당 단추의 콤보 상자 목록에서 선택한 항목의 인덱스를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetEditCtrl](#geteditctrl)|콤보 상자 단추에 포함 된 편집 컨트롤에 대 한 포인터를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetItem](#getitem)|콤보 상자 목록에서 지정 된 인덱스와 연결 된 문자열을 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetItemAll](#getitemall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾고 해당 단추의 콤보 상자 목록에서 인덱스와 연결 된 문자열을 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetItemData](#getitemdata)|콤보 상자 목록에서 지정 된 인덱스와 연결 된 32 비트 값을 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetItemDataAll](#getitemdataall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾고 해당 단추의 콤보 상자 목록에서 인덱스와 연결 된 32 비트 값을 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetItemDataPtrAll](#getitemdataptrall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾습니다. 해당 단추의 콤보 상자 목록에서 인덱스와 연결 된 32 비트 값을 검색 하 고 32 비트 값을 포인터로 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetText](#gettext)|콤보 상자의 편집 컨트롤에서 텍스트를 반환 합니다.|
|[CMFCToolBarComboBoxButton:: GetTextAll](#gettextall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾고 해당 단추의 편집 컨트롤에서 텍스트를 반환 합니다.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|응용 프로그램의 콤보 상자 단추를 도구 모음의 위쪽에 맞출지 아니면 맞출지를 결정 합니다.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|응용 프로그램의 콤보 상자 단추가 평면 모양 인지 여부를 결정 합니다.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|콤보 상자의 목록 상자와 편집 컨트롤에서 모든 항목을 제거 합니다.|
|[CMFCToolBarComboBoxButton:: SelectItem](#selectitem)|인덱스, 32 비트 값 또는 문자열에 따라 콤보 상자에서 항목을 선택 하 고 선택 항목에 대해 콤보 상자 컨트롤에 알립니다.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|지정 된 명령 ID를 가진 콤보 상자 단추를 찾습니다. `SelectItem`을 호출 하 여 해당 문자열, 인덱스 또는 32 비트 값에 따라 해당 단추의 콤보 상자에서 항목을 선택 합니다.|
|[CMFCToolBarComboBoxButton:: Setcenter 세로](#setcentervert)|응용 프로그램의 콤보 상자 단추를 도구 모음 위쪽에 세로로 맞출지 아니면 맞출지 지정 합니다.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|드롭다운 목록 상자의 높이를 설정 합니다.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|응용 프로그램의 콤보 상자 단추를 평면 모양으로 표시할지 여부를 지정 합니다.|

## <a name="remarks"></a>설명

도구 모음에 콤보 상자 단추를 추가 하려면 다음 단계를 수행 합니다.

1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.

2. 개체를 생성 `CMFCToolBarComboBoxButton` 합니다.

3. AFX_WM_RESETTOOLBAR 메시지를 처리 하는 메시지 처리기에서 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)를 사용 하 여 더미 단추를 새 콤보 상자 단추로 바꿉니다.

자세한 내용은 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)를 참조 하세요. 콤보 상자 도구 모음 단추의 예는 프로젝트 VisualStudioDemo 예제를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CMFCToolBarComboBoxButton` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 편집 및 콤보 상자를 사용 하도록 설정 하 고, 응용 프로그램에서 콤보 상자 단추의 세로 위치를 설정 하 고, 목록 상자를 놓을 때 높이를 설정 하 고, 응용 프로그램에서 콤보 상자 단추의 평면 스타일 모양을 설정 하 고, 콤보 상자 단추의 편집 상자에 텍스트를 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbarcomboboxbutton

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a> CMFCToolBarComboBoxButton:: AddItem

목록 상자에 고유한 항목을 추가 합니다.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>매개 변수

*lpszItem*<br/>
진행 목록 상자에 추가할 항목의 텍스트입니다.

*dwData*<br/>
진행 목록 상자에 추가할 항목과 연결 된 데이터입니다.

### <a name="return-value"></a>반환 값

목록 상자에 있는 마지막 항목의 인덱스입니다.

### <a name="remarks"></a>설명

목록 상자 스타일을 정렬 하는 경우에는이 메서드를 사용 하지 마십시오.

항목 텍스트가 목록 상자에 이미 있는 경우 새 데이터가 기존 항목과 함께 저장 됩니다. 항목 검색은 대/소문자를 구분 합니다.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a> CMFCToolBarComboBoxButton::AddSortedItem

[비교](#compare) 메서드에서 정의한 순서로 항목을 목록 상자에 추가 합니다.

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>매개 변수

*lpszItem*<br/>
진행 목록 상자에 추가할 항목의 텍스트입니다.

*dwData*<br/>
진행 목록 상자에 추가할 항목과 연결 된 데이터입니다.

### <a name="return-value"></a>반환 값

목록 상자에 추가 된 항목의 인덱스입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 목록 상자에 특정 순서로 항목을 추가 합니다.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a> CMFCToolBarComboBoxButton:: CanBeStretched

콤보 상자 단추 크기를 변경할 수 있는지 여부를 나타냅니다.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>반환 값

TRUE를 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a> CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) 개체를 생성 합니다.

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 새 단추의 명령 ID입니다.

*iImage*<br/>
진행 [새로 만들기] 단추와 연결 된 이미지의 이미지 인덱스입니다.

*dwStyle*<br/>
진행 새 단추의 스타일입니다.

*iWidth*<br/>
진행 새 단추의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

기본 너비는 150 픽셀입니다.

도구 모음 단추 스타일 목록은 [Toolbar 컨트롤 스타일](../../mfc/reference/toolbar-control-styles.md) 을 참조 하세요.

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a> CMFCToolBarComboBoxButton:: ClearData

사용자 정의 데이터를 삭제 합니다.

```
virtual void ClearData();
```

### <a name="remarks"></a>설명

기본적으로이 메서드는 아무 작업도 수행 하지 않습니다. 사용자 정의 데이터를 삭제 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a> CMFCToolBarComboBoxButton:: Compare

두 문자열을 비교합니다.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>매개 변수

*lpszItem1*<br/>
진행 비교할 첫 번째 문자열입니다.

*lpszItem2*<br/>
진행 비교할 두 번째 문자열입니다.

### <a name="return-value"></a>반환 값

문자열 간의 대/소문자를 구분 하는 사전적 관계를 나타내는 값입니다. 다음 테이블에서는 가능한 값을 나열합니다.

|값|설명|
|-----------|-----------------|
|\<0|첫 번째 문자열이 두 번째 문자열 보다 작은 경우|
|0|첫 번째 문자열은 second와 같습니다.|
|>0|첫 번째 문자열이 두 번째 문자열 보다 큽니다.|

### <a name="remarks"></a>설명

목록 상자에서 항목을 정렬 하는 방법을 변경 하려면이 메서드를 재정의 합니다.

비교는 대/소문자를 구분 합니다.

이 메서드는 [AddSortedItem](#addsorteditem) 메서드에서만 호출 됩니다.

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a> CMFCToolBarComboBoxButton:: CopyFrom

지정 된의 상태를 `CMFCToolBarComboBoxButton` 현재 개체에 복사 합니다.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 원본 `CMFCToolBarComboBoxButton` 개체입니다.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a> CMFCToolBarComboBoxButton::CreateCombo

콤보 상자 단추에 대 한 새 콤보 상자를 만듭니다.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 단추의 부모 창에 대 한 포인터입니다.

*rect*<br/>
진행 콤보 상자의 경계 사각형입니다.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 새 콤보 상자에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a> CMFCToolBarComboBoxButton:: CreateEdit

콤보 상자 단추에 대 한 새 편집 상자를 만듭니다.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 단추의 부모 창에 대 한 포인터입니다.

*rect*<br/>
진행 새 편집 상자의 경계 사각형입니다.

*dwEditStyle*<br/>
진행 새 편집 상자의 컨트롤 스타일입니다.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 새 편집 상자에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

프레임 워크는 콤보 상자 단추에 대 한 새 편집 상자를 만들 때이 메서드를 호출 합니다. [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) 를 만드는 방법을 변경 하려면이 메서드를 재정의 합니다.

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a> CMFCToolBarComboBoxButton::D eleteItem

목록 상자에서 지정 된 항목을 삭제 합니다.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 삭제할 항목의 인덱스 (0부터 시작)입니다.

*dwData*<br/>
진행 삭제할 항목과 연결 된 데이터입니다.

*lpszText*<br/>
진행 삭제할 항목의 텍스트입니다. 텍스트가 동일한 항목이 여러 개 있는 경우 첫 번째 항목이 삭제 됩니다.

### <a name="return-value"></a>반환 값

항목이 있고 삭제 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a> CMFCToolBarComboBoxButton::D uplicateData

사용자 정의 데이터를 복제 합니다.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>설명

기본적으로이 메서드는 아무 작업도 수행 하지 않습니다. 사용자 정의 데이터를 복사 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a> CMFCToolBarComboBoxButton:: EnableWindow

편집 및 콤보 상자를 사용 하거나 사용 하지 않도록 설정 합니다.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 편집 및 콤보 상자를 사용 하려면 TRUE로 설정 합니다. 편집 및 콤보 상자를 사용 하지 않으려면 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

사용 하지 않도록 설정 하면 컨트롤이 활성화 될 수 없으며 사용자 입력을 허용할 수 없습니다.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a> CMFCToolBarComboBoxButton:: ExportToMenuButton

콤보 상자 단추 명령 ID를 사용 하 여 응용 프로그램 문자열 테이블의 문자열을 지정 된 메뉴에 복사 합니다.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>매개 변수

*menuButton*<br/>
제한이 메뉴 단추에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

항상 TRUE입니다.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a> CMFCToolBarComboBoxButton:: FindItem

목록 상자에서 지정 된 문자열을 포함 하는 첫 번째 항목의 인덱스를 반환 합니다.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
진행 목록 상자에서 검색할 텍스트입니다.

### <a name="return-value"></a>반환 값

항목의 인덱스입니다. 항목을 찾을 수 없는 경우 또는 CB_ERR입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a> CMFCToolBarComboBoxButton:: GetByCmd

지정 된 명령 ID를 가진 콤보 상자 단추에 대 한 포인터를 가져옵니다.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

*bIsFocus*<br/>
진행 포커스가 있는 단추만 검색 하려면 TRUE로 설정 합니다. 모든 단추를 검색 하려면 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

콤보 상자 단추에 대 한 포인터입니다. 또는 단추를 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a> CMFCToolBarComboBoxButton:: GetComboBox

콤보 상자 단추의 콤보 상자에 대 한 포인터를 반환 합니다.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 [Ccombobox 클래스](../../mfc/reference/ccombobox-class.md) 개체에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a> CMFCToolBarComboBoxButton::GetContextMenuID

콤보 상자 단추에 대 한 바로 가기 메뉴 리소스 ID를 가져옵니다.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>반환 값

바로 가기 메뉴 리소스 ID입니다.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a> CMFCToolBarComboBoxButton:: GetCount

목록 상자에 있는 항목 수를 반환 합니다.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

목록 상자에 있는 항목의 수입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a> CMFCToolBarComboBoxButton::GetCountAll

지정 된 명령 ID를 가진 콤보 상자 단추의 목록 상자에 있는 항목의 수를 가져옵니다.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

목록 상자에 있는 항목의 수입니다. 그렇지 않으면 콤보 상자 단추를 찾을 수 없습니다 CB_ERR 합니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a> CMFCToolBarComboBoxButton:: GetCurSel

목록 상자에서 현재 선택 된 항목의 인덱스를 가져옵니다.

```
int GetCurSel() const;
```

### <a name="return-value"></a>반환 값

목록 상자에서 현재 선택 된 항목의 인덱스입니다. 또는 항목을 선택 하지 않은 경우 CB_ERR 합니다.

### <a name="remarks"></a>설명

목록 상자 인덱스는 0부터 시작 합니다.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a> CMFCToolBarComboBoxButton:: GetCurSelAll

지정 된 명령 ID를 가진 콤보 상자 단추의 목록 상자에서 현재 선택 된 항목의 인덱스를 반환 합니다.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

목록 상자에서 현재 선택 된 항목의 인덱스입니다. 그렇지 않으면 선택 된 항목이 없거나 콤보 상자 단추를 찾을 수 없는 경우에 CB_ERR 합니다.

### <a name="remarks"></a>설명

목록 상자 인덱스는 0부터 시작 합니다.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a> CMFCToolBarComboBoxButton:: GetEditCtrl

콤보 상자 단추의 편집 상자에 대 한 포인터를 반환 합니다.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하는 경우 입력란에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a> CMFCToolBarComboBoxButton::GetHwnd

콤보 상자에 대 한 창 핸들을 반환 합니다.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>반환 값

창 핸들 이거나, 콤보 상자가 창 개체와 연결 되어 있지 않으면 NULL입니다.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a> CMFCToolBarComboBoxButton:: GetItem

목록 상자의 지정 된 인덱스에 있는 항목과 연결 된 문자열을 반환 합니다.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

항목과 연결 된 문자열에 대 한 포인터입니다. 그렇지 않으면 인덱스 매개 변수가 잘못 된 경우 NULL이 고, 인덱스 매개 변수가-1이 고 콤보 상자에 선택 된 항목이 없는 경우에는 NULL입니다.

### <a name="remarks"></a>설명

인덱스 매개 변수-1은 현재 선택 된 항목의 문자열을 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a> CMFCToolBarComboBoxButton:: GetItemAll

지정 된 명령 ID를 가진 콤보 상자 단추의 목록 상자에서 지정 된 인덱스에 있는 항목과 연결 된 문자열을 반환 합니다.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 항목의 문자열에 대 한 포인터입니다. 그렇지 않으면 인덱스가 유효 하지 않거나, 콤보 상자 단추를 찾을 수 없거나, index가-1이 고 콤보 상자에 선택 된 항목이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

인덱스 값-1은 현재 선택 된 항목의 문자열을 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a> CMFCToolBarComboBoxButton:: GetItemData

목록 상자의 특정 인덱스에 있는 항목과 연결 된 데이터를 반환 합니다.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

항목과 연결 된 데이터입니다. 항목이 없으면 0이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

인덱스 매개 변수-1은 현재 선택 된 항목과 연결 된 데이터를 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a> CMFCToolBarComboBoxButton:: GetItemDataAll

특정 명령 ID를 가진 콤보 상자 단추의 목록 상자에 있는 특정 인덱스의 항목과 연결 된 데이터를 반환 합니다.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 항목에 연결 된 데이터이 고, 그렇지 않으면입니다. 지정 된 인덱스가 유효 하지 않으면 0이 고, 콤보 상자 단추를 찾을 수 없으면 CB_ERR입니다.

### <a name="remarks"></a>설명

인덱스 매개 변수-1은 현재 선택 된 항목과 연결 된 데이터를 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a> CMFCToolBarComboBoxButton:: GetItemDataPtrAll

특정 명령 ID를 가진 콤보 상자 단추의 목록 상자에 있는 특정 인덱스의 항목과 연결 된 데이터를 반환 합니다. 이 데이터는 포인터로 반환 됩니다.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콤보 상자 단추의 명령 ID입니다.

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 항목과 연결 된 포인터이 고, 그렇지 않으면입니다. 오류가 발생 하면-1이 고, 콤보 상자 단추를 찾을 수 없으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a> CMFCToolBarComboBoxButton:: GetPrompt

콤보 상자 단추에 대 한 프롬프트 문자열을 반환 합니다.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>반환 값

프롬프트 문자열입니다.

### <a name="remarks"></a>설명

이 메서드는 현재 구현 되어 있지 않습니다.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a> CMFCToolBarComboBoxButton:: GetText

편집 상자의 텍스트를 가져옵니다.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>반환 값

편집 상자의 텍스트입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a> CMFCToolBarComboBoxButton:: GetTextAll

지정 된 명령 ID를 가진 콤보 상자 단추의 편집 상자에 있는 텍스트를 가져옵니다.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 특정 콤보 상자 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

메서드가 성공적으로 수행 된 경우 편집 상자의 텍스트입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a> CMFCToolBarComboBoxButton:: HasFocus

콤보 상자에 현재 포커스가 있는지 여부를 나타냅니다.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>반환 값

콤보 상자에 현재 포커스가 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

콤보 상자의 자식 창에 현재 포커스가 있는 경우에도이 메서드는 TRUE를 반환 합니다.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a> CMFCToolBarComboBoxButton::IsCenterVert

응용 프로그램에서 콤보 상자 단추의 세로 위치를 반환 합니다.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>반환 값

단추가 가운데에 있으면 TRUE이 고, 그렇지 않으면입니다. 단추가 위쪽에 정렬 되 면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a> CMFCToolBarComboBoxButton::IsFlatMode

응용 프로그램에서 콤보 상자 단추의 평면 스타일 모양을 반환 합니다.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>반환 값

단추에 평면 스타일이 적용 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

콤보 상자 단추의 기본 평면 스타일은 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a> CMFCToolBarComboBoxButton::IsOwnerOf

지정 된 핸들이 콤보 상자 단추 또는 해당 자식 항목 중 하나에 연결 되어 있는지 여부를 나타냅니다.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>매개 변수

*hwnd*<br/>
진행 창 핸들입니다.

### <a name="return-value"></a>반환 값

핸들이 콤보 상자 단추를 사용 하 여 그리드의 면 TRUE이 고, 그렇지 않으면 자식 항목 중 하나입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a> CMFCToolBarComboBoxButton:: Is리본 단추

콤보 상자 단추가 리본 패널에 있는지 여부를 나타냅니다.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>반환 값

항상 FALSE입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 항상 FALSE를 반환 합니다. 즉, 콤보 상자 단추는 리본 패널에 표시 되지 않습니다.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a> CMFCToolBarComboBoxButton:: IsWindowVisible

콤보 상자 단추의 표시 상태를 반환 합니다.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>반환 값

콤보 상자 단추의 표시 상태입니다.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a> CMFCToolBarComboBoxButton::NotifyCommand

콤보 상자 단추에서 메시지를 처리할지 여부를 나타냅니다.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>매개 변수

*iNotifyCode*<br/>
진행 명령과 연결 된 알림 메시지입니다.

### <a name="return-value"></a>반환 값

콤보 상자 단추에서 메시지를 처리할지 여부를 지정 합니다.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> CMFCToolBarComboBoxButton::OnAddToCustomizePage

**사용자 지정** 대화 상자에 단추가 추가 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a> CMFCToolBarComboBoxButton::OnCalculateSize

단추의 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 콤보 상자 단추를 표시 하는 장치 컨텍스트입니다.

*sizeDefault*<br/>
진행 콤보 상자 단추의 기본 크기입니다.

*bHorz*<br/>
진행 부모 도구 모음의 도크 상태입니다. 도구 모음이 가로로 도킹 되 면 TRUE이 고, 도구 모음이 세로로 도킹 되 면 FALSE입니다.

### <a name="return-value"></a>반환 값

`SIZE`콤보 상자 단추의 크기 (픽셀)를 포함 하는 구조체입니다.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCToolBarComboBoxButton::OnChangeParentWnd

콤보 상자 단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 새 부모 도구 모음에 대 한 포인터입니다.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a> CMFCToolBarComboBoxButton:: OnClick

사용자가 콤보 상자 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 콤보 상자 단추의 부모 창에 대 한 포인터입니다.

*bDelay*<br/>
진행 파생 클래스에서 사용 하도록 예약 되어 있습니다.

### <a name="return-value"></a>반환 값

메서드가 이벤트를 처리 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a> CMFCToolBarComboBoxButton::OnCtlColor

사용자가 부모 도구 모음 색을 변경 하 여 콤보 상자 단추 색을 설정할 때 프레임 워크에서 호출 됩니다.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 콤보 상자 단추를 표시 하는 장치 컨텍스트입니다.

*nCtlColor*<br/>
진행 사용 되지 않는.

### <a name="return-value"></a>반환 값

프레임 워크가 콤보 상자 단추의 배경을 칠하는 데 사용 하는 브러시에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 콤보 상자 단추 텍스트 색도 설정 합니다.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a> CMFCToolBarComboBoxButton:: OnDraw

지정 된 스타일 및 옵션을 사용 하 여 콤보 상자 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*rect*<br/>
진행 단추의 경계 사각형입니다.

*pImages*<br/>
진행 단추와 연결 된 이미지의 컬렉션입니다.

*bHorz*<br/>
진행 부모 도구 모음의 도크 상태입니다. 도구 모음이 가로로 도킹 되 면 TRUE이 고, 도구 모음이 세로로 도킹 되 면 FALSE입니다.

*bCustomizeMode*<br/>
진행 응용 프로그램이 사용자 지정 모드에 있는지 여부입니다.

*bHighlight*<br/>
진행 콤보 상자 단추를 그릴지 여부를 나타냅니다.

*bDrawBorder*<br/>
진행 콤보 상자 단추를 테두리와 함께 그릴지 여부를 나타냅니다.

*bGrayDisabledButtons*<br/>
진행 음영 처리 되지 않은 단추를 그리려면 TRUE이 고, 비활성화 된 이미지 컬렉션을 사용 하려면 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

**사용자 지정** 대화 상자의 **명령** 창에 콤보 상자 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 콤보 상자 단추를 표시 하는 장치 컨텍스트입니다.

*rect*<br/>
진행 콤보 상자 단추의 경계 사각형입니다.

*bSelected*<br/>
진행 콤보 상자 단추가 선택 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

콤보 상자 단추의 너비 (픽셀)입니다.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a> CMFCToolBarComboBoxButton::OnGlobalFontsChanged

응용 프로그램 글꼴이 변경 될 때 콤보 상자 단추 글꼴을 설정 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a> CMFCToolBarComboBoxButton:: OnMove

부모 도구 모음이 이동 될 때 콤보 상자 단추의 위치를 변경 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a> CMFCToolBarComboBoxButton:: OnShow

콤보 상자 단추가 숨겨지거나 표시 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 콤보 상자 단추를 숨길지 표시할지 여부를 나타냅니다.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a> CMFCToolBarComboBoxButton:: OnSize

부모 도구 모음의 크기가 변경 될 때 콤보 상자 단추의 크기를 변경 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>매개 변수

*iSize*<br/>
진행 콤보 상자 단추의 새 너비입니다.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a> CMFCToolBarComboBoxButton:: OnUpdateToolTip

사용자가 콤보 상자 단추에 대 한 도구 설명을 변경할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 콤보 상자 단추의 부모 창에 대 한 포인터입니다.

*iButtonIndex*<br/>
진행 콤보 상자 단추의 ID입니다.

*wndToolTip*<br/>
진행 콤보 상자 단추와 연결할 도구 설명입니다.

*str*<br/>
진행 도구 설명 텍스트입니다.

### <a name="return-value"></a>반환 값

메서드가 이벤트를 처리 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a> CMFCToolBarComboBoxButton::RemoveAllItems

목록 및 편집 상자에서 모든 항목을 삭제 합니다.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>설명

콤보 상자의 목록 상자와 편집 컨트롤에서 모든 항목을 제거 합니다.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a> CMFCToolBarComboBoxButton:: SelectItem

목록 상자에서 항목을 선택 합니다.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

*bNotify*<br/>
진행 선택 영역에 대해 콤보 상자 단추를 알리려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*dwData*<br/>
진행 목록 상자의 항목과 연결 된 데이터입니다.

*lpszText*<br/>
진행 목록 상자에 있는 항목의 텍스트입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a> CMFCToolBarComboBoxButton::SelectItemAll

지정 된 명령 ID를 가진 콤보 상자 단추의 목록 상자에서 항목을 선택 합니다.

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 목록 상자를 포함 하는 콤보 상자 단추의 명령 ID입니다.

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다. 값-1은 목록 상자에서 현재 선택 된 항목을 제거 하 고 편집 상자를 지웁니다.

*dwData*<br/>
진행 목록 상자에 있는 항목의 데이터입니다.

*lpszText*<br/>
진행 목록 상자에 있는 항목의 텍스트입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a> CMFCToolBarComboBoxButton:: Serialize

보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
[in, out] `CArchive` Serialize 할 개체입니다.

### <a name="remarks"></a>설명

개체의 설정에 `CArchive` 따라이 메서드는 보관 파일을 읽거나 쓸 수 있습니다.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a> CMFCToolBarComboBoxButton:: SetACCData

`CAccessibilityData`콤보 상자 단추의 내게 필요한 옵션 데이터를 사용 하 여 지정 된 개체를 채웁니다.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>매개 변수

*pParent*<br/>
진행 콤보 상자 단추의 부모 창입니다.

*data*<br/>
제한이 `CAccessibilityData` 콤보 상자 단추에서 내게 필요한 옵션 데이터를 받는 개체입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a> CMFCToolBarComboBoxButton:: Setcenter 세로

응용 프로그램에서 콤보 상자 단추의 세로 위치를 설정 합니다.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>매개 변수

*bCenterVert*<br/>
진행 도구 모음에서 콤보 상자 단추를 가운데 맞춤 하려면 TRUE로 설정 합니다. FALSE 이면 콤보 상자 단추를 도구 모음의 맨 위에 맞춥니다.

### <a name="remarks"></a>설명

기본적으로 콤보 상자 단추는 위쪽에 정렬 됩니다.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a> CMFCToolBarComboBoxButton::SetContextMenuID

콤보 상자 단추에 대 한 바로 가기 메뉴 리소스 ID를 설정 합니다.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>매개 변수

*uiResID*<br/>
진행 바로 가기 메뉴 리소스 ID입니다.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a> CMFCToolBarComboBoxButton::SetDropDownHeight

목록 상자를 놓을 때 목록 상자의 높이를 설정 합니다.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>매개 변수

*nHeight*<br/>
진행 목록 상자의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

기본 높이는 150 픽셀입니다.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a> CMFCToolBarComboBoxButton::SetFlatMode

응용 프로그램에서 콤보 상자 단추의 평면 스타일 모양을 설정 합니다.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>매개 변수

*bFlat*<br/>
진행 평면 스타일 모양에 대해 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

콤보 상자 단추의 기본 평면 스타일은 FALSE입니다.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a> CMFCToolBarComboBoxButton:: System.windows.forms.control.setstyle

콤보 상자 단추의 지정 된 스타일을 설정 하 고 컨트롤을 사용할 수 없는 경우 다시 그립니다.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*nStyle*<br/>
진행 도구 모음 스타일의 비트 조합 (OR)입니다.

### <a name="remarks"></a>설명

도구 모음 단추 스타일 목록은 [Toolbar 컨트롤 스타일](../../mfc/reference/toolbar-control-styles.md) 을 참조 하세요.

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a> CMFCToolBarComboBoxButton:: SetText

콤보 상자 단추의 편집 상자에 있는 텍스트를 설정 합니다.

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
진행 편집 상자의 텍스트를 포함 하는 문자열에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 클래스](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
