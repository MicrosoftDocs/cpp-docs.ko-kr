---
description: '자세한 정보: CMFCColorMenuButton 클래스'
title: CMFCColorMenuButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 4ba0934e872adc4e4b33c2ae5700ecb0fc46e6d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327675"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 클래스

`CMFCColorMenuButton`클래스는 색 선택 대화 상자를 시작 하는 메뉴 명령 또는 도구 모음 단추를 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCColorMenuButton:: CMFCColorMenuButton](#cmfccolormenubutton)|`CMFCColorMenuButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCColorMenuButton:: Enable자동 단추](#enableautomaticbutton)|일반 색 단추 위에 배치 되는 "자동" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 자동 단추에는 **자동** 으로 레이블이 지정 됩니다.|
|[CMFCColorMenuButton:: EnableDocumentColors](#enabledocumentcolors)|시스템 색 대신 문서 특정 색을 표시할 수 있도록 합니다.|
|[CMFCColorMenuButton:: EnableOtherButton](#enableotherbutton)|일반 색 단추 아래에 있는 "기타" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 "기타" 단추에는 **더 많은 색** 이 지정 됩니다.|
|[CMFCColorMenuButton:: EnableTearOff](#enabletearoff)|색 창을 분리할 수 있습니다.|
|[CMFCColorMenuButton:: Get자동 색](#getautomaticcolor)|현재 자동 색을 검색 합니다.|
|[CMFCColorMenuButton:: GetColor](#getcolor)|현재 단추의 색을 검색 합니다.|
|[CMFCColorMenuButton:: GetColorByCmdID](#getcolorbycmdid)|지정 된 명령 ID에 해당 하는 색을 검색 합니다.|
|[CMFCColorMenuButton:: OnChangeParentWnd](#onchangeparentwnd)|부모 창이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CMFCColorMenuButton:: OpenColorDialog](#opencolordialog)|색 선택 대화 상자를 엽니다.|
|[CMFCColorMenuButton:: SetColor](#setcolor)|현재 색 단추의 색을 설정 합니다.|
|[CMFCColorMenuButton:: SetColorByCmdID](#setcolorbycmdid)|지정 된 색 메뉴 단추의 색을 설정 합니다.|
|[CMFCColorMenuButton:: SetColorName](#setcolorname)|지정 된 색의 새 이름을 설정 합니다.|
|[CMFCColorMenuButton:: SetColumnsNumber](#setcolumnsnumber)|개체에 의해 표시 되는 열 수를 설정 합니다 `CMFCColorBar` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCColorMenuButton:: CopyFrom](#copyfrom)|다른 도구 모음 단추를 현재 단추에 복사 합니다.|
|[CMFCColorMenuButton:: CreatePopupMenu](#createpopupmenu)|색 선택 대화 상자를 만듭니다.|
|[CMFCColorMenuButton:: IsEmptyMenuAllowed](#isemptymenuallowed)|빈 메뉴가 지원 되는지 여부를 나타냅니다.|
|[CMFCColorMenuButton:: OnDraw](#ondraw)|단추에 이미지를 표시 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCColorMenuButton:: OnDrawOnCustomizeList](#ondrawoncustomizelist)|`CMFCColorMenuButton`도구 모음 사용자 지정 대화 상자의 목록에 개체가 표시 되기 전에 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

원래 메뉴 명령 또는 도구 모음 단추를 `CMFCColorMenuButton` 개체로 바꾸려면 개체를 만들고 `CMFCColorMenuButton` 적절 한 [Cmfccolorbar 클래스](../../mfc/reference/cmfccolorbar-class.md) 스타일을 설정한 다음 `ReplaceButton` [cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md) 클래스의 메서드를 호출 합니다. 도구 모음을 사용자 지정 하는 경우 [CMFCToolBarsCustomizeDialog:: ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) 메서드를 호출 합니다.

색 선택 대화 상자는 [Cmfccolormenubutton:: CreatePopupMenu](#createpopupmenu) 이벤트 처리기를 처리 하는 동안 만들어집니다. 이벤트 처리기는 WM_COMMAND 메시지를 사용 하 여 부모 프레임에 알립니다. `CMFCColorMenuButton`개체는 원래 메뉴 명령 또는 도구 모음 단추에 할당 된 컨트롤 ID를 보냅니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 색 메뉴 단추를 만들고 구성 하는 방법을 보여 줍니다 `CMFCColorMenuButton` . 이 예제에서는 개체를 `CPalette` 먼저 만든 다음 클래스의 개체를 생성 하는 데 사용 `CMFCColorMenuButton` 합니다. `CMFCColorMenuButton`그런 다음 자동 및 기타 단추를 사용 하도록 설정 하 고 색과 열의 수를 설정 하 여 개체를 구성 합니다. 이 코드는 [Word 패드 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcolormenubutton

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a> CMFCColorMenuButton:: CMFCColorMenuButton

`CMFCColorMenuButton` 개체를 생성합니다.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>매개 변수

*uiCmdID*<br/>
진행 단추 명령 ID입니다.

*lpszText*<br/>
진행 단추 텍스트입니다.

*pPalette*<br/>
진행 단추의 색상표에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

첫 번째 생성자는 기본 생성자입니다. 개체의 현재 색과 자동 색은 black (RGB (0, 0, 0))으로 초기화 됩니다.

두 번째 생성자는 지정 된 명령 ID에 해당 하는 색으로 단추를 초기화 합니다.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a> CMFCColorMenuButton:: CopyFrom

하나의 [Cmfc기능 Menubutton 클래스](../../mfc/reference/cmfctoolbarmenubutton-class.md)파생 개체를 다른 개체에 복사 합니다.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 복사할 원본 단추입니다.

### <a name="remarks"></a>설명

개체에서 파생 된 개체를 복사 하려면이 메서드를 재정의 `CMFCColorMenuButton` 합니다.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a> CMFCColorMenuButton:: CreatePopupMenu

색 선택 대화 상자를 만듭니다.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>반환 값

색 선택 대화 상자를 나타내는 개체입니다.

### <a name="remarks"></a>설명

이 메서드는 사용자가 색 메뉴 단추를 누를 때 프레임 워크에서 호출 됩니다.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorMenuButton:: Enable자동 단추

일반 색 단추 위에 배치 되는 "자동" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 자동 단추에는 **자동** 으로 레이블이 지정 됩니다.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 단추가 자동이 될 때 표시 되는 단추 텍스트를 지정 합니다.

*colorAutomatic*<br/>
진행 새 자동 색을 지정 합니다.

*bEnable*<br/>
진행 단추가 자동 인지 여부를 지정 합니다.

### <a name="remarks"></a>설명

자동 단추가 현재 기본 색을 적용 합니다.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a> CMFCColorMenuButton:: EnableDocumentColors

시스템 색 대신 문서 특정 색을 표시할 수 있도록 합니다.

```cpp
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 단추 텍스트를 지정 합니다.

*bEnable*<br/>
진행 문서 특정 색 이나 FALSE를 표시 하 여 시스템 색을 표시 하려면 TRUE로 설정 합니다.

### <a name="remarks"></a>설명

사용자가 색 메뉴 단추를 클릭할 때 현재 문서 색 또는 시스템 색상표 색을 표시 하려면이 메서드를 사용 합니다.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorMenuButton:: EnableOtherButton

일반 색 단추 아래에 있는 "기타" 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 표준 시스템 "기타" 단추에는 **더 많은 색** 이 지정 됩니다.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 단추 텍스트를 지정 합니다.

*bAltColorDlg*<br/>
진행 대화 상자를 표시 하려면 TRUE를 지정 하 고 `CMFCColorDialog` 표준 시스템 색 대화 상자를 표시 하려면 FALSE를 지정 합니다.

*bEnable*<br/>
진행 "기타" 단추를 표시 하려면 TRUE를 지정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a> CMFCColorMenuButton:: EnableTearOff

색 창을 분리할 수 있습니다.

```cpp
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 분리 창의 ID를 지정 합니다.

*nVertDockColumns*<br/>
진행 분리 상태에 있는 동안 세로로 도킹 된 색 창의 열 수를 지정 합니다.

*nHorzDockRows*<br/>
진행 분리 상태에 있는 동안 가로로 도킹 된 색 창의 행 수를 지정 합니다.

### <a name="remarks"></a>설명

단추를 누를 때 표시 되는 색 창에 대해 "분리" 기능을 사용 하도록 설정 하려면이 메서드를 호출 합니다 `CMFCColorMenuButton` .

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorMenuButton:: Get자동 색

현재 자동 색을 검색 합니다.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>반환 값

현재 자동 색을 나타내는 RGB 색 값입니다.

### <a name="remarks"></a>설명

[Cmfccolormenubutton:: enableautomatic 단추](#enableautomaticbutton)에 의해 설정 되는 자동 색을 가져오려면이 메서드를 호출 합니다.

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a> CMFCColorMenuButton:: GetColor

현재 단추의 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

단추의 색입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a> CMFCColorMenuButton:: GetColorByCmdID

지정 된 명령 ID에 해당 하는 색을 검색 합니다.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>매개 변수

*uiCmdID*<br/>
진행 명령 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령 ID에 해당 하는 색입니다.

### <a name="remarks"></a>설명

응용 프로그램에 여러 색 단추가 있는 경우이 방법을 사용 합니다. 사용자가 색 단추를 클릭 하면 단추는 WM_COMMAND 메시지의 해당 명령 ID를 부모로 보냅니다. `GetColorByCmdID`메서드는 명령 ID를 사용 하 여 해당 색을 검색 합니다.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a> CMFCColorMenuButton:: IsEmptyMenuAllowed

빈 메뉴가 지원 되는지 여부를 나타냅니다.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>반환 값

빈 메뉴가 허용 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

빈 메뉴는 기본적으로 지원 됩니다. 파생 클래스에서이 동작을 변경 하려면이 메서드를 재정의 합니다.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCColorMenuButton:: OnChangeParentWnd

부모 창이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 새 부모 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a> CMFCColorMenuButton:: OnDraw

단추에 이미지를 표시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 다시 그릴 영역을 제한 하는 사각형입니다.

*pImages*<br/>
진행 도구 모음 이미지 목록을 가리킵니다.

*bHorz*<br/>
진행 도구 모음이 가로 도킹 된 상태임을 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

*bCustomizeMode*<br/>
진행 응용 프로그램이 사용자 지정 모드에 있음을 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

*bHighlight*<br/>
진행 단추가 강조 표시 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

*bDrawBorder*<br/>
진행 단추의 테두리가 표시 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

*bGrayDisabledButtons*<br/>
진행 비활성화 된 단추가 회색 (흐리게 표시) 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> CMFCColorMenuButton:: OnDrawOnCustomizeList

`CMFCColorMenuButton`도구 모음 사용자 지정 대화 상자의 목록에 개체가 표시 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 그릴 단추를 제한 하는 사각형입니다.

*bSelected*<br/>
진행 TRUE 이면 단추가 선택 됨 상태를 나타냅니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

단추의 너비입니다.

### <a name="remarks"></a>설명

이 메서드는 `CMFCColorMenuButton` 도구 모음 사용자 지정 프로세스 중에 목록 상자에 개체가 표시 될 때 프레임 워크에서 호출 됩니다.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a> CMFCColorMenuButton:: OpenColorDialog

색 선택 대화 상자를 엽니다.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>매개 변수

*colorDefault*<br/>
진행 색 대화 상자에서 선택 하는 기본 색입니다.

*colorRes*<br/>
제한이 색 대화 상자에서 사용자가 선택 하는 색을 반환 합니다.

### <a name="return-value"></a>반환 값

사용자가 새 색을 선택 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴 단추를 클릭 하면이 메서드를 호출 하 여 색 대화 상자를 엽니다. 반환 값이 0이 아닌 경우 사용자가 선택 하는 색은 *Colorres* 매개 변수에 저장 됩니다. [Cmfccolormenubutton:: EnableOtherButton](#enableotherbutton) 메서드를 사용 하 여 표준 색 대화 상자와 [CMFCColorDialog 클래스](../../mfc/reference/cmfccolordialog-class.md) 대화 상자 사이를 전환 합니다.

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a> CMFCColorMenuButton:: SetColor

현재 색 단추의 색을 설정 합니다.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
진행 RGB 색 값입니다.

*bNotify*<br/>
진행 연결 된 메뉴 단추나 도구 모음 단추에 *clr* 매개 변수 색을 적용 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

현재 색 단추의 색을 변경 하려면이 메서드를 호출 합니다. *Bnotify* 매개 변수가 0이 아니면 연결 된 팝업 메뉴 또는 도구 모음의 해당 단추 색이 *clr* 매개 변수로 지정 된 색으로 변경 됩니다.

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a> CMFCColorMenuButton:: SetColorByCmdID

지정 된 색 메뉴 단추의 색을 설정 합니다.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>매개 변수

*uiCmdID*<br/>
진행 색 메뉴 단추의 리소스 ID입니다.

*color*<br/>
진행 RGB 색 값입니다.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorMenuButton:: SetColorName

지정 된 색의 새 이름을 설정 합니다.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 이름이 변경 되는 색의 RGB 값입니다.

*strName*<br/>
진행 색의 새 이름입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorMenuButton:: SetColumnsNumber

색 선택 컨트롤 ( [Cmfccolorbar](../../mfc/reference/cmfccolorbar-class.md) 개체)에 표시할 열 수를 설정 합니다.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>매개 변수

*nColumns*<br/>
진행 표시할 열의 수입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton 클래스](../../mfc/reference/cmfccolorbutton-class.md)
