---
description: '자세히 알아보기: CMFCColorDialog 클래스'
title: CMFCColorDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 4279a92ef22253ce2909acce88d77428e3ed5495
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327685"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 클래스

`CMFCColorDialog`클래스는 색 선택 대화 상자를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|`CMFCColorDialog` 개체를 생성합니다.|
|`CMFCColorDialog::~CMFCColorDialog`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCColorDialog:: GetColor](#getcolor)|현재 선택 된 색을 반환 합니다.|
|[CMFCColorDialog:: GetPalette](#getpalette)|색의 색상표를 반환 합니다.|
|`CMFCColorDialog::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. 구문 및 자세한 내용은 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 참조 하세요. ( `CDialogEx::PreTranslateMessage`을 재정의합니다.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|시스템 색상표에서 색상표를 파생 시킵니다.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|현재 선택한 색을 설정 합니다.|
|[CMFCColorDialog:: SetNewColor](#setnewcolor)|지정 된 RGB 값에 가장 일치 하는 색을 설정 합니다.|
|[CMFCColorDialog:: SetPageOne](#setpageone)|첫 번째 속성 페이지의 RGB 값을 선택 합니다.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|두 번째 속성 페이지의 RGB 값을 선택 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|`m_bIsMyPalette`|색 선택 대화 상자에서 자체 색상표를 사용 하는 경우 TRUE이 고, 대화 상자에서 생성자에 지정 된 색상표를 사용 하는 경우 FALSE `CMFCColorDialog` 입니다.|
|`m_bPickerMode`|사용자가 선택 대화 상자에서 색을 선택 하는 동안 TRUE 그렇지 않으면 FALSE입니다.|
|`m_btnColorSelect`|사용자가 선택한 색 단추입니다.|
|`m_CurrentColor`|현재 선택한 색입니다.|
|`m_hcurPicker`|색을 선택 하는 데 사용 되는 커서입니다.|
|`m_NewColor`|선택한 예상 색으로, 영구적으로 선택 하거나 원래 색으로 되돌릴 수 있습니다.|
|`m_pColourSheetOne`|색 선택 속성 시트의 첫 번째 속성 페이지에 대 한 포인터입니다.|
|`m_pColourSheetTwo`|색 선택 속성 시트의 두 번째 속성 페이지에 대 한 포인터입니다.|
|`m_pPalette`|현재 논리 색상표입니다.|
|`m_pPropSheet`|색 선택 대화 상자의 속성 시트에 대 한 포인터입니다.|
|`m_wndColors`|색 선택 컨트롤 개체입니다.|
|`m_wndStaticPlaceHolder`|색 선택 속성 시트에 대 한 자리 표시자 인 정적 컨트롤입니다.|

## <a name="remarks"></a>설명

색 선택 대화 상자는 두 페이지가 있는 속성 시트로 표시 됩니다. 첫 번째 페이지의 시스템 팔레트에서 표준 색을 선택 합니다. 두 번째 페이지에서 사용자 지정 색을 선택 합니다.

스택에서 개체를 생성 한 다음를 호출 하 여 `CMFCColorDialog` `DoModal` 초기 색을 생성자에 매개 변수로 전달할 수 있습니다 `CMFCColorDialog` . 그러면 색 선택 대화 상자에서 각 색상표를 처리 하는 여러 [Cmfccolor Kerctrl 클래스](../../mfc/reference/cmfccolorpickerctrl-class.md) 개체를 만듭니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 색 대화 상자를 구성 하는 방법을 보여 줍니다 `CMFCColorDialog` . 이 예제에서는 대화 상자의 현재 색과 새 색을 설정 하는 방법과 색 대화 상자의 두 속성 페이지에서 선택한 색의 빨강, 녹색 및 파랑 구성 요소를 설정 하는 방법을 보여 줍니다. 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxcolordialog

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a> CMFCColorDialog::CMFCColorDialog

`CMFCColorDialog` 개체를 생성합니다.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>매개 변수

*clrInit*<br/>
진행 기본 색 선택입니다. 값을 지정 하지 않으면 기본값은 RGB (0, 0, 0) (검정)입니다.

*dwFlags*<br/>
[in] 예약되어 있습니다.

*pParentWnd*<br/>
진행 대화 상자의 부모 또는 소유자 창에 대 한 포인터입니다.

*hPal*<br/>
진행 색상표에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a> CMFCColorDialog:: GetColor

색 대화 상자에서 사용자가 선택 하는 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

색 대화 상자에서 선택한 색의 RGB 정보를 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

메서드를 호출한 후이 함수를 호출 `DoModal` 합니다.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a> CMFCColorDialog:: GetPalette

현재 색 대화 상자에서 사용할 수 있는 색상표를 검색 합니다.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>반환 값

생성자에 지정 된 개체에 대 한 포인터 `CPalette` `CMFCColorDialog` 입니다.

### <a name="remarks"></a>설명

색상표는 사용자가 선택할 수 있는 색을 지정 합니다.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a> CMFCColorDialog::RebuildPalette

시스템 색상표에서 색상표를 파생 시킵니다.

```cpp
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a> CMFCColorDialog::SetCurrentColor

대화 상자의 현재 색을 설정 합니다.

```cpp
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>매개 변수

*rgb*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a> CMFCColorDialog:: SetNewColor

현재 색을 현재 색상표에서 가장 유사한 색으로 설정 합니다.

```cpp
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>매개 변수

*rgb*<br/>
진행 RGB 색을 지정 하는 [Colorref](/windows/win32/gdi/colorref) 입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a> CMFCColorDialog:: SetPageOne

색 대화 상자의 첫 번째 속성 페이지에서 선택한 색의 빨간색, 녹색 및 파랑 구성 요소를 명시적으로 지정 합니다.

```cpp
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>매개 변수

*R*<br/>
진행 RGB 값의 빨강 구성 요소를 지정 합니다.

*Express-g*<br/>
진행 RGB 값의 녹색 구성 요소를 지정 합니다.

*B*<br/>
진행 RGB 값의 파랑 구성 요소를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a> CMFCColorDialog::SetPageTwo

색 대화 상자의 두 번째 속성 페이지에서 선택한 색의 빨간색, 녹색 및 파랑 구성 요소를 명시적으로 지정 합니다.

```cpp
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>매개 변수

*R*<br/>
진행 RGB 값의 빨강 구성 요소를 지정 합니다.

*Express-g*<br/>
진행 RGB 값의 녹색 구성 요소를 지정 합니다.

*B*<br/>
진행 RGB 값의 파랑 구성 요소를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 클래스](../../mfc/reference/cmfccolorpickerctrl-class.md)
