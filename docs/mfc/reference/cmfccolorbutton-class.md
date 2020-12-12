---
description: '자세한 정보: CMFCColorButton 클래스'
title: CMFCColorButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: b3f3e40f1e52c1a387563fde2aa1027046d557f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327694"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 클래스

`CMFCColorButton` 및 [cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 클래스는 색 선택 컨트롤을 구현하는데 함께 사용됩니다.

## <a name="syntax"></a>구문

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCColorButton:: CMFCColorButton](#cmfccolorbutton)|새 `CMFCColorButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|일반 색 단추 위에 배치 되는 "자동" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 자동 단추에는 **자동** 으로 레이블이 지정 됩니다.|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|일반 색 단추 아래에 있는 "기타" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 "기타" 단추에는 **더 많은 색** 이 지정 됩니다.|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|현재 자동 색을 검색 합니다.|
|[CMFCColorButton:: GetColor](#getcolor)|단추의 색을 검색 합니다.|
|[CMFCColorButton:: SetColor](#setcolor)|단추의 색을 설정 합니다.|
|[CMFCColorButton::SetColorName](#setcolorname)|색 이름을 설정 합니다.|
|[CMFCColorButton:: Set\colornumber](#setcolumnsnumber)|색 선택 대화 상자의 열 수를 설정 합니다.|
|[CMFCColorButton:: SetDocumentColors](#setdocumentcolors)|색 선택 대화 상자에 표시 되는 문서 특정 색 목록을 지정 합니다.|
|[CMFCColorButton:: SetPalette](#setpalette)|표준 표시 색의 색상표를 지정 합니다.|
|[CMFCColorButton:: System.windows.window.sizetocontent](#sizetocontent)|텍스트 및 이미지 크기에 따라 단추 컨트롤의 크기를 변경 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCColorButton:: IsDrawXPTheme](#isdrawxptheme)|현재 색 단추가 Windows XP의 비주얼 스타일에 표시 되는지 여부를 나타냅니다.|
|[CMFCColorButton::OnDraw](#ondraw)|단추의 이미지를 표시 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorButton:: OnDrawBorder](#ondrawborder)|단추의 테두리를 표시 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|단추에 포커스가 있을 때 포커스 사각형을 표시 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|색 선택 대화 상자가 표시 될 때 프레임 워크에서 호출 됩니다.|
|[CMFCColorButton:: RebuildPalette](#rebuildpalette)|지정 된 `m_pPalette` 색상표 또는 기본 시스템 색상표로 보호 된 데이터 멤버를 초기화 합니다.|
|[CMFCColorButton::UpdateColor](#updatecolor)|사용자가 색 선택 대화 상자의 색상표에서 색을 선택할 때 프레임 워크에서 호출 됩니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|`m_bAltColorDlg`|부울 값입니다. TRUE 이면 프레임 워크는 *다른* 단추를 클릭할 때 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 색 대화 상자를 표시 하 고, 그렇지 않으면 시스템 색 대화 상자를 표시 합니다. 기본값은 TRUE입니다. 자세한 내용은 [Cmfccolorbutton:: EnableOtherButton](#enableotherbutton)을 참조 하세요.|
|`m_bAutoSetFocus`|부울 값입니다. TRUE 이면 메뉴가 표시 될 때 프레임 워크에서 색 메뉴에 포커스를 설정 하 고, FALSE 이면 포커스를 변경 하지 않습니다. 기본값은 TRUE입니다.|
|[CMFCColorButton:: m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|색 단추에 대해 사용자 지정 모드를 사용할 수 있는지 여부를 나타냅니다.|
|`m_Color`|[Colorref](/windows/win32/gdi/colorref) 값입니다. 현재 선택한 색을 포함 합니다.|
|`m_ColorAutomatic`|[Colorref](/windows/win32/gdi/colorref) 값입니다. 현재 선택 된 기본 색을 포함 합니다.|
|`m_Colors`|[Colorref](/windows/win32/gdi/colorref) 값의 [CArray](../../mfc/reference/carray-class.md) 입니다. 현재 사용 가능한 색을 포함 합니다.|
|`m_lstDocColors`|[Colorref](/windows/win32/gdi/colorref) 값의 [CList](../../mfc/reference/clist-class.md) 입니다. 현재 문서 색을 포함 합니다.|
|`m_nColumns`|정수입니다. 색 선택 메뉴의 색 표에 표시할 열 수를 포함 합니다.|
|`m_pPalette`|[Cpalette](../../mfc/reference/cpalette-class.md)에 대 한 포인터입니다. 현재 색 선택 메뉴에서 사용할 수 있는 색을 포함 합니다.|
|`m_pPopup`|[CMFCColorPopupMenu 클래스](../../mfc/reference/cmfccolorpopupmenu-class.md) 개체에 대 한 포인터입니다. 색 단추를 클릭할 때 표시 되는 색 선택 메뉴입니다.|
|`m_strAutoColorText`|문자열 색 선택 메뉴에 있는 "자동" 단추의 레이블입니다.|
|`m_strDocColorsText`|문자열 색 선택 메뉴에서 문서 색을 표시 하는 단추의 레이블입니다.|
|`m_strOtherText`|문자열 색 선택 메뉴에 있는 "기타" 단추의 레이블입니다.|

## <a name="remarks"></a>설명

기본적으로 클래스는 `CMFCColorButton` 색 선택 대화 상자를 여는 푸시 단추로 동작 합니다. 색 선택 대화 상자에는 작은 색 단추 배열과 사용자 지정 색 선택을 표시 하는 "기타" 단추가 포함 됩니다. 표준 시스템 "기타" 단추에는 **더 많은 색** 이 지정 됩니다. 사용자가 새 색을 선택 하면 `CMFCColorButton` 개체가 변경 내용을 반영 하 고 선택한 색을 표시 합니다.

코드에서 직접 또는 **클래스 마법사** 도구와 대화 상자 템플릿을 사용 하 여 색 단추 컨트롤을 만듭니다. 색 단추 컨트롤을 직접 만드는 경우 `CMFCColorButton` 응용 프로그램에 변수를 추가한 다음 개체의 생성자와 메서드를 호출 합니다 `Create` `CMFCColorButton` . **클래스 마법사** 를 사용 하는 경우 `CButton` 응용 프로그램에 변수를 추가한 다음 변수의 형식을에서로 변경 합니다 `CButton` `CMFCColorButton` .

색 선택 대화 상자 ( [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md))는 프레임 워크가 이벤트 처리기를 호출할 때 [Cmfccolorbar:: OnShowColorPopup](#onshowcolorpopup) 메서드로 표시 됩니다 `OnLButtonDown` . [Cmfccolorbutton:: OnShowColorPopup](#onshowcolorpopup) 메서드를 재정의 하 여 사용자 지정 색 선택을 지원할 수 있습니다.

`CMFCColorButton`개체는 WM_COMMAND를 전송 하 여 색이 변경 되 고 있음을 부모에 게 알립니다. BN_CLICKED 알림. 부모가 [Cmfccolorbutton:: GetColor](#getcolor) 메서드를 사용 하 여 현재 색을 검색 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 색 단추를 구성 하는 방법을 보여 줍니다 `CMFCColorButton` . 메서드는 색 단추 및 열 수의 색을 설정 하 고 자동 및 기타 단추를 사용 하도록 설정 합니다. 이 예제는 [상태 표시줄 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxcolorbutton

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a> CMFCColorButton:: CMFCColorButton

새 `CMFCColorButton` 개체를 생성합니다.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorButton:: Enable자동 단추

색 선택 컨트롤의 "자동" 단추를 사용 하거나 사용 하지 않도록 설정 하 고 자동 (기본값) 색을 설정 합니다.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 자동 단추의 텍스트를 지정 합니다.

*colorAutomatic*<br/>
진행 자동 단추의 기본 색을 지정 하는 RGB 값입니다.

*bEnable*<br/>
진행 자동 단추를 사용할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorButton:: EnableOtherButton

일반 색 단추 아래에 표시 되는 "기타" 단추를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 단추의 텍스트를 지정 합니다.

*bAltColorDlg*<br/>
진행 사용자가 단추를 클릭할 때 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 대화 상자 또는 시스템 색 대화 상자를 열었는지 여부를 지정 합니다.

*bEnable*<br/>
진행 "기타" 단추를 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

"기타" 단추를 클릭 하 여 색 대화 상자를 표시 합니다. *BAltColorDlg* 매개 변수가 TRUE 이면 [CMFCColorDialog 클래스가](../../mfc/reference/cmfccolordialog-class.md) 표시 됩니다. 그렇지 않으면 시스템 색 대화 상자가 표시 됩니다.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorButton:: Get자동 색

현재 자동 (기본) 색을 검색 합니다.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>반환 값

현재 자동 색을 나타내는 RGB 값입니다.

### <a name="remarks"></a>설명

현재 자동 색은 [Cmfccolorbutton:: Enableautomatic button](#enableautomaticbutton) 메서드에 의해 설정 됩니다.

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a> CMFCColorButton:: GetColor

현재 선택 된 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

RGB 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a> CMFCColorButton:: IsDrawXPTheme

현재 색 단추가 Windows XP의 비주얼 스타일에 표시 되는지 여부를 나타냅니다.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>반환 값

비주얼 스타일이 지원 되 고 현재 색 단추가 Windows XP의 비주얼 스타일에 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a> CMFCColorButton:: m_bEnabledInCustomizeMode

색 단추를 사용자 지정 모드로 설정 합니다.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>설명

사용자 지정 대화 상자 페이지에 색 단추를 추가 해야 하거나 사용자 지정 중에 다른 색을 선택할 수 있도록 하려면 멤버를 TRUE로 설정 하 여 단추를 사용 하도록 설정 합니다 `m_bEnabledInCustomizeMode` . 기본적으로이 멤버는 FALSE로 설정 됩니다.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a> CMFCColorButton:: OnDraw

단추의 이미지를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추의 이미지를 렌더링 하는 데 사용 되는 장치 컨텍스트를 가리킵니다.

*rect*<br/>
진행 단추를 제한 하는 사각형입니다.

*uiState*<br/>
진행 단추의 표시 상태를 지정 합니다.

### <a name="remarks"></a>설명

렌더링 프로세스를 사용자 지정 하려면이 메서드를 재정의 합니다.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a> CMFCColorButton:: OnDrawBorder

단추의 테두리를 표시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 테두리를 그리는 데 사용 되는 장치 컨텍스트를 가리킵니다.

*rectClient*<br/>
진행 그릴 단추의 경계를 정의 하는 *pDC* 매개 변수로 지정 된 장치 컨텍스트의 사각형입니다.

*uiState*<br/>
진행 단추의 표시 상태를 지정 합니다.

### <a name="remarks"></a>설명

색 단추의 테두리 모양을 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCColorButton:: OnDrawFocusRect

단추에 포커스가 있을 때 포커스 사각형을 표시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 포커스 영역을 그리는 데 사용 되는 장치 컨텍스트를 가리킵니다.

*rectClient*<br/>
진행 *PDC* 매개 변수로 지정 된 장치 컨텍스트에서 단추의 경계를 정의 하는 사각형입니다.

### <a name="remarks"></a>설명

포커스 사각형의 모양을 사용자 지정 하려면이 메서드를 재정의 합니다.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a> CMFCColorButton:: OnShowColorPopup

팝업 색 표시줄이 표시 되기 전에 호출 됩니다.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a> CMFCColorButton:: RebuildPalette

지정 된 `m_pPalette` 색상표 또는 기본 시스템 색상표로 보호 된 데이터 멤버를 초기화 합니다.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>매개 변수

*pPal*\
진행 논리 색상표 또는 NULL에 대 한 포인터입니다. NULL 인 경우 기본 시스템 색상표가 사용 됩니다.

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a> CMFCColorButton:: SetColor

단추의 색을 지정 합니다.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 RGB 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorButton:: SetColorName

색의 이름을 지정 합니다.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 색의 RGB 값입니다.

*strName*<br/>
진행 색의 이름입니다.

### <a name="remarks"></a>설명

색 이름 목록은 응용 프로그램당 전역입니다. 결과적으로이 메서드는 해당 매개 변수를 [Cmfccolorbar:: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)으로 전송 합니다.

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorButton:: Set\colornumber

사용자의 색 선택 프로세스 중에 사용자에 게 표시 되는 색의 표에 표시 되는 열 수를 정의 합니다.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>매개 변수

*nColumns*<br/>
진행 열 수를 지정 합니다.

### <a name="remarks"></a>설명

사용자는 미리 정의 된 색 표를 표시 하는 팝업 색 표시줄에서 색을 선택할 수 있습니다. 이 메서드를 사용 하 여 테이블의 열 수를 정의 합니다.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorButton:: SetDocumentColors

색 집합과 집합의 이름을 지정 합니다. [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 개체를 사용 하 여 색 집합을 표시 합니다.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 문서 색 집합과 함께 표시할 레이블을 지정 합니다.

*lstColors*<br/>
진행 RGB 값의 목록에 대 한 참조입니다.

### <a name="remarks"></a>설명

`CMFCColorButton`개체는 [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 개체에 전송 되는 RGB 값의 목록을 유지 관리 합니다. 색 막대가 표시 되 면 이러한 색은 *lpszLabel* 매개 변수로 지정 된 레이블이 있는 특수 섹션에 표시 됩니다.

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a> CMFCColorButton:: SetPalette

팝업 색 막대에 표시할 표준 색을 지정 합니다.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>매개 변수

*pPalette*<br/>
진행 색상표에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCColorButton:: System.windows.window.sizetocontent

텍스트 및 이미지에 맞게 단추 컨트롤의 크기를 조정 합니다.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>매개 변수

*bCalcOnly*<br/>
진행 0이 아니면 새 크기의 단추 컨트롤이 계산 되지만 실제 크기는 변경 되지 않습니다.

### <a name="return-value"></a>반환 값

`CSize`새 단추 컨트롤 크기를 지정 하는 개체입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a> CMFCColorButton:: UpdateColor

사용자가 색 단추를 클릭할 때 표시 되는 색 막대에서 색을 선택할 때 프레임 워크에서 호출 됩니다.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 사용자가 선택한 색입니다.

### <a name="remarks"></a>설명

`UpdateColor`함수는 현재 선택 된 단추의 색을 변경 하 고 BN_CLICKED 표준 알림과 함께 WM_COMMAND 메시지를 보내 부모에 게 알립니다. [Cmfccolorbutton:: GetColor](#getcolor) 메서드를 사용 하 여 선택한 색을 검색 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 클래스](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette 클래스](../../mfc/reference/cpalette-class.md)<br/>
[CArray 클래스](../../mfc/reference/carray-class.md)<br/>
[CList 클래스](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
