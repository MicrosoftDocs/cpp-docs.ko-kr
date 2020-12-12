---
description: '자세한 정보: Cmfc리본 Combobox 클래스'
title: Cmfc리본 Combobox 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: be4078145817d06fafddb76f2cefbd0df0083503
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293668"
---
# <a name="cmfcribboncombobox-class"></a>Cmfc리본 Combobox 클래스

클래스는 리본 `CMFCRibbonComboBox` 표시줄, 리본 패널 또는 리본 팝업 메뉴에 추가할 수 있는 콤보 상자 컨트롤을 구현 합니다.

## <a name="syntax"></a>구문

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|----------|-----------------|
|[Cmfc리본 Combobox:: Cmfc리본 콤보 상자](#cmfcribboncombobox)|Cmfc리본 콤보 상자 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Combobox:: AddItem](#additem)|목록 상자에 고유한 항목을 추가 합니다.|
|[Cmfc리본 Combobox::D eleteItem](#deleteitem)|목록 상자에서 지정 된 항목을 삭제 합니다.|
|[Cmfc리본 Combobox:: EnableDropDownListResize](#enabledropdownlistresize)|목록 상자를 놓을 때 크기를 변경할 수 있는지 여부를 지정 합니다.|
|[Cmfc리본 Combobox:: FindItem](#finditem)|목록 상자에서 지정 된 문자열과 일치 하는 첫 번째 항목의 인덱스를 반환 합니다.|
|[Cmfc리본 Combobox:: GetCount](#getcount)|목록 상자에 있는 항목 수를 반환 합니다.|
|[Cmfc리본 Combobox:: GetCurSel](#getcursel)|목록 상자에서 현재 선택 된 항목의 인덱스를 가져옵니다.|
|[Cmfc리본 Combobox:: GetDropDownHeight](#getdropdownheight)|목록 상자를 놓을 때 목록 상자의 높이를 가져옵니다.|
|[Cmfc리본 Combobox:: GetIntermediateSize](#getintermediatesize)|중간 모드에서 표시 되는 콤보 상자의 크기를 반환 합니다.|
|[Cmfc리본 Combobox:: GetItem](#getitem)|목록 상자의 지정 된 인덱스에 있는 항목과 연결 된 문자열을 반환 합니다.|
|[Cmfc리본 Combobox:: GetItemData](#getitemdata)|목록 상자의 지정 된 인덱스에 있는 항목과 연결 된 데이터를 반환 합니다.|
|[Cmfc리본 Combobox:: HasEditBox](#haseditbox)|컨트롤에 편집 상자가 포함 되는지 여부를 나타냅니다.|
|[Cmfc리본 Combobox:: IsResizeDropDownList](#isresizedropdownlist)|목록 상자의 크기를 조정할 수 있는지 여부를 나타냅니다.|
|[Cmfc리본 Combobox:: OnSelectItem](#onselectitem)|사용자가 목록 상자에서 항목을 선택할 때 프레임 워크에서 호출 됩니다.|
|[Cmfc리본 Combobox:: RemoveAllItems](#removeallitems)|목록 상자에서 모든 항목을 삭제 하 고 편집 상자를 지웁니다.|
|[Cmfc리본 Combobox:: SelectItem](#selectitem)|목록 상자에서 항목을 선택 합니다.|
|[Cmfc리본 Combobox:: SetDropDownHeight](#setdropdownheight)|목록 상자를 놓을 때 목록 상자의 높이를 설정 합니다.|

## <a name="remarks"></a>설명

리본 콤보 상자는 사용자가 편집할 수 있는 정적 레이블이나 레이블과 결합 된 목록 상자로 구성 됩니다. 리본 콤보 상자를 만들 때 원하는 형식을 지정 해야 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하 고 `CMFCRibbonComboBox` , 콤보 상자에 항목을 추가 하 고, 콤보 상자에서 항목을 선택 하 고, 패널에 콤보 상자를 추가 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribboncombobox

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a> Cmfc리본 Combobox:: AddItem

목록 상자에 고유한 항목을 추가 합니다.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>매개 변수

*lpszItem*<br/>
진행 추가할 항목의 문자열입니다.

*dwData*<br/>
진행 추가할 항목과 연결 된 데이터입니다.

### <a name="return-value"></a>반환 값

추가 된 항목의 인덱스 (0부터 시작)입니다.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a> Cmfc리본 Combobox:: Cmfc리본 콤보 상자

`CMFCRibbonComboBox` 개체를 생성합니다.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 콤보 상자의 ID입니다.

*bHasEditBox*<br/>
진행 컨트롤 내에 편집 상자를 표시 하려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*nWidth*<br/>
진행 콤보 상자의 너비 (픽셀)입니다. 기본 너비의 경우에는-1입니다.

*lpszLabel*<br/>
진행 콤보 상자의 표시 레이블입니다.

*nImage*<br/>
진행 콤보 상자의 작은 이미지 인덱스입니다.

### <a name="remarks"></a>설명

기본 너비는 108 픽셀입니다.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a> Cmfc리본 Combobox::D eleteItem

목록 상자에서 지정 된 항목을 삭제 합니다.

```cpp
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
진행 삭제할 항목의 문자열입니다. 동일한 문자열을 사용 하는 항목이 여러 개 있는 경우 첫 번째 항목이 삭제 됩니다.

### <a name="return-value"></a>반환 값

지정 된 항목이 삭제 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a> Cmfc리본 Combobox:: EnableDropDownListResize

목록 상자를 놓을 때 크기를 변경할 수 있는지 여부를 지정 합니다.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 크기 조정을 사용 하려면 TRUE입니다. 크기 조정을 사용 하지 않으려면 FALSE입니다.

### <a name="remarks"></a>설명

크기 조정을 사용 하는 경우 목록 상자는 표시 되는 항목에 맞게 크기를 변경 합니다.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a> Cmfc리본 Combobox:: FindItem

목록 상자에서 지정 된 문자열과 일치 하는 첫 번째 항목의 인덱스를 반환 합니다.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
진행 목록 상자에 있는 항목의 문자열입니다.

### <a name="return-value"></a>반환 값

항목의 인덱스 (0부터 시작)입니다. 항목을 찾을 수 없으면-1입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a> Cmfc리본 Combobox:: GetCount

목록 상자에 있는 항목 수를 반환 합니다.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

목록 상자에 있는 항목의 수 이거나, 목록 상자에 항목이 없는 경우 0입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a> Cmfc리본 Combobox:: GetCurSel

목록 상자에서 현재 선택 된 항목의 인덱스를 가져옵니다.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>반환 값

목록 상자에서 현재 선택 된 항목의 0부터 시작 하는 인덱스이 고, 그렇지 않으면입니다. 항목을 선택 하지 않은 경우에는-1입니다.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a> Cmfc리본 Combobox:: GetDropDownHeight

목록 상자를 놓을 때 목록 상자의 높이를 가져옵니다.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>반환 값

목록 상자의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a> Cmfc리본 Combobox:: GetIntermediateSize

중간 모드에서 표시 되는 콤보 상자의 크기를 반환 합니다.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 콤보 상자에 대 한 장치 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

콤보 상자의 크기입니다.

### <a name="remarks"></a>설명

반환 되는 크기는 작은 이미지를 표시할 때 콤보 상자의 크기를 기준으로 합니다.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a> Cmfc리본 Combobox:: GetItem

목록 상자의 지정 된 인덱스에 있는 항목과 연결 된 문자열을 반환 합니다.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

항목과 연결 된 문자열에 대 한 포인터입니다. 그렇지 않으면 인덱스 매개 변수가 잘못 된 경우 NULL이 고, 인덱스 매개 변수가-1이 고 콤보 상자에서 선택 된 항목이 없는 경우에는 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a> Cmfc리본 Combobox:: GetItemData

목록 상자의 지정 된 인덱스에 있는 항목과 연결 된 데이터를 반환 합니다.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

항목과 연결 된 데이터입니다. 항목이 없거나 인덱스 매개 변수가-1이 고 목록 상자에 선택 된 항목이 없는 경우에는 0입니다.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a> Cmfc리본 Combobox:: HasEditBox

컨트롤에 편집 상자가 포함 되는지 여부를 나타냅니다.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>반환 값

컨트롤에 편집 상자가 포함 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a> Cmfc리본 Combobox:: IsResizeDropDownList

목록 상자의 크기를 조정할 수 있는지 여부를 나타냅니다.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>반환 값

목록 상자의 크기를 조정할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다. [Cmfc리본 Combobox:: EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>설명

[Cmfc리본 combobox:: EnableDropDownListResize](#enabledropdownlistresize) 메서드를 사용 하 여 목록 상자 크기 조정을 사용 하도록 설정할 수 있습니다.

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a> Cmfc리본 Combobox:: OnSelectItem

사용자가 목록 상자에서 항목을 선택할 때 프레임 워크에서 호출 됩니다.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
진행 선택한 항목의 인덱스입니다.

### <a name="remarks"></a>설명

사용자 입력 선택을 처리 하려면이 메서드를 재정의 합니다.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a> Cmfc리본 Combobox:: RemoveAllItems

목록 상자에서 모든 항목을 삭제 하 고 편집 상자를 지웁니다.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a> Cmfc리본 Combobox:: SelectItem

목록 상자에서 항목을 선택 합니다.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 상자에 있는 항목의 인덱스 (0부터 시작)입니다.

*dwData*<br/>
진행 목록 상자의 항목과 연결 된 데이터입니다.

*lpszText*<br/>
진행 목록 상자에 있는 항목의 문자열입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a> Cmfc리본 Combobox:: SetDropDownHeight

목록 상자를 놓을 때 목록 상자의 높이를 설정 합니다.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>매개 변수

*nHeight*<br/>
진행 목록 상자의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

기본 높이는 150 픽셀입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 Edit 클래스](../../mfc/reference/cmfcribbonedit-class.md)
