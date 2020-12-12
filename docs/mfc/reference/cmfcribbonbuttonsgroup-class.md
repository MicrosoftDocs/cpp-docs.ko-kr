---
description: '자세한 정보: Cmfc리본 Buttonsgroup 클래스'
title: CMFCRibbonButtonsGroup 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: 0b86ce6ff21bd36daaac9d68ce511ae395141170
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293834"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 클래스

`CMFCRibbonButtonsGroup`클래스를 사용 하면 리본 단추 집합을 그룹으로 구성할 수 있습니다. 그룹의 모든 단추는 가로로 서로 직접 인접해 있으며 테두리로 둘러싸여 있습니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|`CMFCRibbonButtonsGroup` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Buttonsgroup:: AddButton](#addbutton)|그룹에 단추를 추가 합니다.|
|[Cmfc리본 Buttonsgroup:: AddButtons](#addbuttons)|그룹에 단추 목록을 추가 합니다.|
|[Cmfc리본 Buttonsgroup:: GetButton](#getbutton)|지정 된 인덱스에 있는 단추에 대 한 포인터를 반환 합니다.|
|[Cmfc리본 Buttonsgroup:: GetCount](#getcount)|그룹의 단추 수를 반환 합니다.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|리본 그룹에 있는 일반 이미지의 이미지 크기를 반환 합니다 ( [Cmfcribbon Baseelement:: GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)재정의).|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|리본 요소의 일반 크기를 반환 합니다 ( [Cmfcribbon Baseelement:: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)재정의).|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|`CMFCRibbonButtonsGroup`개체에 도구 모음 이미지가 포함 되어 있는지 여부를 보고 합니다.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|단추가 정상 인지 강조 표시 되었는지 여부에 따라 지정 된 단추에 대 한 적절 한 이미지를 그립니다.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|개체에서 모든 단추를 제거 `CMFCRibbonButtonsGroup` 합니다.|
|[Cmfc리본 Buttonsgroup:: SetImages](#setimages)|이미지를 그룹에 할당 합니다.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|`CMFCRibbonCategory`개체의 부모 `CMFCRibbonButtonsGroup` 와 그 안에 있는 모든 단추를 설정 합니다 ( [CmfcSetParentCategory Baseelement::](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)재정의).|

## <a name="remarks"></a>설명

그룹은 [Cmfcbaseribbonelement](../../mfc/reference/cmfcribbonbaseelement-class.md) 에서 파생 되며 단일 엔터티로 조작할 수 있습니다. 패널 또는 팝업 메뉴에 그룹을 배치할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonButtonsGroup` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 예제에서는 개체를 생성 하 고 `CMFCRibbonButtonsGroup` , 리본 단추 그룹에 이미지를 할당 하 고, 리본 단추 그룹에 단추를 추가 하는 방법을 보여 줍니다. 이 코드 조각은 [클라이언트 그리기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonbuttonsgroup

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a> Cmfc리본 Buttonsgroup:: AddButton

그룹에 단추를 추가 합니다.

```cpp
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>매개 변수

*pButton*<br/>
진행 추가할 단추에 대 한 포인터입니다.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a> Cmfc리본 Buttonsgroup:: AddButtons

그룹에 단추 목록을 추가 합니다.

```cpp
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>매개 변수

*lstButtons*<br/>
진행 추가 하려는 단추에 대 한 포인터 목록입니다.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a> Cmfc리본 Buttonsgroup:: Cmfc리본 Buttonsgroup

`CMFCRibbonButtonsGroup` 개체를 생성합니다.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>매개 변수

*pButton*<br/>
진행 새로 만든 개체에 추가할 단추를 지정 합니다 `CMFCRibbonButtonsGroup` .

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a> Cmfc리본 Buttonsgroup:: GetButton

지정 된 인덱스에 있는 단추에 대 한 포인터를 반환 합니다.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>매개 변수

*i*<br/>
진행 반환할 단추의 0부터 시작 하는 인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 단추에 대 한 포인터입니다. 지정 된 인덱스가 범위를 벗어난 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a> Cmfc리본 Buttonsgroup:: GetCount

그룹의 단추 수를 반환 합니다.

```
int GetCount() const;
```

### <a name="return-value"></a>반환 값

그룹의 단추 수입니다.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a> Cmfc리본 Buttonsgroup:: GetImageSize

보호 된 멤버의 원본 이미지 크기를 검색 합니다 `CMFCToolBarImages` `m_Images` .

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>반환 값

도구 모음 이미지 (있는 경우)의 원본 이미지 크기를 반환 하거나, `CSize` 그렇지 않으면 0을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a> Cmfc리본 Buttonsgroup:: GetRegularSize

리본 그룹 요소의 최대 가능 크기를 검색 합니다.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 리본 그룹의 장치 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a> Cmfc리본 Buttonsgroup:: HasImages

`CMFCRibbonButtonsGroup`개체에 도구 모음 이미지가 포함 되어 있는지 여부를 보고 합니다.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>반환 값

보호 된 멤버에 이미지가 포함 된 경우 TRUE `CMFCToolBarImages` 를 반환 하 고 `m_Images` 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a> Cmfc리본 Buttonsgroup:: OnDrawImage

단추가 정상 인지 강조 표시 되었는지 여부에 따라 지정 된 단추에 대 한 적절 한 이미지를 그립니다.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 개체의 장치 컨텍스트에 대 한 포인터 `CMFCRibbonButtonsGroup` 입니다.

*rectImage*<br/>
진행 이미지를 그릴 사각형입니다.

*pButton*<br/>
진행 이미지를 그릴 단추입니다.

*nImageIndex*<br/>
진행 단추에 그릴 이미지의 인덱스입니다 (표준, 강조 표시 또는 비활성화 된 단추의 세 가지 이미지 배열 중 하나).

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a> Cmfc리본 Buttonsgroup:: RemoveAll

개체에서 모든 단추를 제거 `CMFCRibbonButtonsGroup` 합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a> Cmfc리본 Buttonsgroup:: SetImages

리본 단추 그룹에 이미지를 할당 합니다.

```cpp
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>매개 변수

*pImages*<br/>
진행 일반 이미지.

*pHotImages*<br/>
진행 핫 이미지.

*pDisabledImages*<br/>
진행 이미지를 사용할 수 없습니다.

### <a name="remarks"></a>설명

`SetImages`그룹에 단추를 추가 하기 전에를 호출 합니다. 이미지 수는 그룹에 추가할 단추 수보다 크거나 같아야 합니다.

> [!NOTE]
> 핫 이미지는 사용자가 단추를 가리킬 때 표시 되는 이미지입니다. 사용 하지 않도록 설정 된 이미지는 단추를 사용할 수 없을 때 표시 되는 이미지입니다.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a> Cmfc리본 Buttonsgroup:: SetParentCategory

`CMFCRibbonCategory`개체의 부모 `CMFCRibbonButtonsGroup` 와 그 안의 모든 단추를 설정 합니다.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>매개 변수

*pCategory*<br/>
진행 설정할 부모 범주에 대 한 포인터입니다 (리본 컨트롤의 탭 그룹을 범주 라고 함).

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
