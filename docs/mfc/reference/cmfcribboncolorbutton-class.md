---
description: '자세한 정보: Cmfc리본 Colorbutton 클래스'
title: CMFCRibbonColorButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: a350339559febdc9346dcf8b342d274d00bab391
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293718"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 클래스

`CMFCRibbonColorButton` 클래스는 리본 표시줄에 추가할 수 있는 색 단추를 구현합니다. 리본 색 단추는 하나 이상의 색상표가 포함된 드롭다운 메뉴를 표시합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Colorbutton:: AddColorsGroup](#addcolorsgroup)|일반 색 영역에 색 그룹을 추가합니다.|
|[Cmfc리본 Colorbutton:: Enable자동 단추](#enableautomaticbutton)|**자동** 단추를 사용할지 여부를 지정합니다.|
|[Cmfc리본 Colorbutton:: EnableOtherButton](#enableotherbutton)|**기타** 단추를 사용하도록 설정합니다.|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[Cmfc리본 Colorbutton:: GetColor](#getcolor)|현재 선택된 색을 반환합니다.|
|[Cmfc리본 Colorbutton:: GetColorBoxSize](#getcolorboxsize)|색 막대에 표시되는 색 요소의 크기를 반환합니다.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[Cmfc리본 Colorbutton:: GetHighlightedColor](#gethighlightedcolor)|팝업 색상표에서 현재 선택된 요소의 색을 반환합니다.|
|[Cmfc리본 Colorbutton:: RemoveAllColorGroups](#removeallcolorgroups)|일반 색 영역에서 모든 색 그룹을 제거합니다.|
|[Cmfc리본 Colorbutton:: SetColor](#setcolor)|일반 색 영역에서 색을 선택합니다.|
|[Cmfc리본 Colorbutton:: SetColorBoxSize](#setcolorboxsize)|색 막대에 표시되는 모든 색 요소의 크기를 설정합니다.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[Cmfc리본 Colorbutton:: SetDocumentColors](#setdocumentcolors)|문서 색 영역에 표시할 RGB 값의 목록을 지정합니다.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>설명

리본 색 단추는 사용자가 누를 때 색 막대를 표시합니다. 기본적으로 이 색 막대에는 일반 색 영역이라는 색 선택 색상표가 포함되어 있습니다. 필요에 따라 색 막대에 기본 색을 선택할 수 있는 **자동** 단추와 추가 색이 포함된 팝업 색상표를 표시하는 **기타** 단추가 표시될 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonColorButton` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 `CMFCRibbonColorButton` 개체 생성, 큰 이미지 설정, **자동** 단추 사용, **기타** 단추 사용, 열 수 설정, 색 막대에 표시되는 모든 색 요소의 크기 설정, 일반 색 영역에 색 그룹 추가, 문서 색 영역에 표시할 RGB 값 목록 지정 등을 수행하는 방법을 보여 줍니다. 이 코드 조각은 [클라이언트 그리기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a> Cmfc리본 Colorbutton:: AddColorsGroup

일반 색 영역에 색 그룹을 추가합니다.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 그룹 이름입니다.

*lstColors*<br/>
진행 색 목록입니다.

*bContiguousColumns*<br/>
진행 그룹에 색 항목이 표시 되는 방식을 제어 합니다. TRUE 이면 색 항목이 세로 간격 없이 그려집니다. FALSE 이면 색 항목이 세로 간격으로 그려집니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 색 팝업에 여러 색 그룹이 표시 되도록 합니다. 그룹에 색이 표시 되는 방식을 제어할 수 있습니다.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a> Cmfc리본 Colorbutton:: Cmfc리본 Colorbutton

`CMFCRibbonColorButton` 개체를 생성합니다.

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 사용자가 단추를 클릭할 때 실행할 명령의 명령 ID를 지정 합니다.

*lpszText*<br/>
진행 단추에 표시할 텍스트를 지정 합니다.

*nSmallImageIndex*<br/>
진행 단추에 표시할 작은 이미지의 인덱스 (0부터 시작)입니다.

*color*<br/>
진행 단추의 색입니다 (기본값은 black).

*bSimpleButtonLook*<br/>
진행 TRUE 이면 단추가 간단한 사각형으로 그려집니다.

*nLargeImageIndex*<br/>
진행 단추에 표시할 커다란 이미지의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> Cmfc리본 Colorbutton:: Enable자동 단추

**자동** 단추를 사용할지 여부를 지정합니다.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 **자동** 단추의 레이블입니다.

*colorAutomatic*<br/>
진행 **자동** 단추의 기본 색을 지정 하는 RGB 값입니다.

*bEnable*<br/>
진행 **자동** 단추를 사용할 수 있으면 TRUE이 고, 비활성화 된 경우 FALSE입니다.

*lpszToolTip*<br/>
진행 **자동** 단추의 도구 설명입니다.

*bOnTop*<br/>
진행 **자동** 단추가 색상표 앞에 오도록 할지 여부를 지정 합니다.

*bDrawBorder*<br/>
진행 응용 프로그램이 리본 색 단추에서 색 막대 주위에 테두리를 그리면 TRUE이 고, 색 막대 현재 선택한 색을 표시 합니다. 응용 프로그램에서 테두리를 그리지 않으면 FALSE입니다.

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> Cmfc리본 Colorbutton:: EnableOtherButton

**기타** 단추를 사용하도록 설정합니다.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
단추의 레이블입니다.

*lpszToolTip*<br/>
**다른** 단추에 대 한 도구 설명 텍스트입니다.

### <a name="remarks"></a>설명

**다른** 단추는 색 그룹 아래에 표시 되는 단추입니다. 사용자가 **다른** 단추를 클릭 하면 색 대화 상자가 표시 됩니다.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> Cmfc리본 Colorbutton:: Get자동 색

현재 자동 단추 색을 검색 합니다.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>반환 값

현재 자동 단추 색을 나타내는 RGB 색 값입니다.

### <a name="remarks"></a>설명

자동 단추 색은 `colorAutomatic` 메서드에 전달 된 매개 변수에 의해 설정 됩니다 `CMFCRibbonColorButton::EnableAutomaticButton` .

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a> Cmfc리본 Colorbutton:: GetColor

현재 선택된 색을 반환합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

단추를 클릭 하 여 선택한 색입니다.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a> Cmfc리본 Colorbutton:: GetColorBoxSize

색 막대에 표시되는 색 요소의 크기를 반환합니다.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>반환 값

드롭다운 색상표에 있는 색 단추의 크기입니다.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a> Cmfc리본 Colorbutton:: GetColumns

리본 색 단추 갤러리 표시의 행에 있는 항목의 수를 가져옵니다.

```
int GetColumns() const;
```

### <a name="return-value"></a>반환 값

각 행의 아이콘 수를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a> Cmfc리본 Colorbutton:: GetHighlightedColor

팝업 색상표에서 현재 선택 된 요소의 색을 반환 합니다.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>반환 값

팝업 색상표에서 현재 선택 된 요소의 색입니다.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a> Cmfc리본 Colorbutton:: RemoveAllColorGroups

일반 색 영역에서 모든 색 그룹을 제거합니다.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a> Cmfc리본 Colorbutton:: SetColor

일반 색 영역에서 색을 선택합니다.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 설정할 색입니다.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a> Cmfc리본 Colorbutton:: SetColorBoxSize

색 막대에 표시되는 모든 색 요소의 크기를 설정합니다.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>매개 변수

*sizeBox*<br/>
진행 색상표에 있는 색 단추의 새 크기입니다.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a> Cmfc리본 Colorbutton:: SetColorName

지정 된 색의 새 이름을 설정 합니다.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 색의 RGB 값입니다.

*strName*<br/>
진행 지정 된 색의 새 이름입니다.

### <a name="remarks"></a>설명

`CMFCColorBar::SetColorName`이 메서드는를 호출 하므로 응용 프로그램의 모든 개체에서 지정 된 색의 이름을 변경 합니다 `CMFCColorBar` .

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a> Cmfc리본 Colorbutton:: SetColumns

사용자의 색 선택 프로세스 중에 사용자에 게 표시 되는 색의 테이블에 표시 되는 열 수를 설정 합니다.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>매개 변수

*nColumns*<br/>
진행 각 행에 표시할 색 아이콘의 수입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> Cmfc리본 Colorbutton:: SetDocumentColors

문서 색 영역에 표시할 RGB 값의 목록을 지정합니다.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 문서 색으로 표시 될 텍스트입니다.

*lstColors*<br/>
진행 RGB 값의 목록에 대 한 참조입니다.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a> Cmfc리본 Colorbutton:: SetPalette

색 단추에 표시 되는 색 표에 표시할 표준 색을 지정 합니다.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>매개 변수

*pPalette*<br/>
진행 색상표에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a> Cmfc리본 Colorbutton:: UpdateColor

사용자가 색 단추를 클릭할 때 표시 되는 색 표에서 색을 선택할 때 프레임 워크에서 호출 됩니다.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 사용자가 선택한 색입니다.

### <a name="remarks"></a>설명

`CMFCRibbonColorButton::UpdateColor`메서드는 현재 선택 된 단추의 색을 변경 하 고 BN_CLICKED 표준 알림과 함께 WM_COMMAND 메시지를 보내 부모에 게 알립니다. [Cmfc리본 Colorbutton:: GetColor](#getcolor) 메서드를 사용 하 여 선택한 색을 검색 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 갤러리 클래스](../../mfc/reference/cmfcribbongallery-class.md)
