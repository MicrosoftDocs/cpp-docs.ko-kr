---
description: '자세한 정보: CMFCButton 클래스'
title: CMFCButton 클래스
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: 4e75d5238dc427b4a6543b7bc6c1c3345f0df532
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327765"
---
# <a name="cmfcbutton-class"></a>CMFCButton 클래스

`CMFCButton`클래스는 단추 텍스트 정렬, 단추 텍스트 및 이미지 결합, 커서 선택, 도구 설명 지정과 같은 [cbutton](../../mfc/reference/cbutton-class.md) 클래스에 기능을 추가 합니다.

## <a name="syntax"></a>구문

```
class CMFCButton : public CButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCButton::CMFCButton`|기본 생성자입니다.|
|`CMFCButton::~CMFCButton`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCButton:: CleanUp](#cleanup)|내부 변수를 다시 설정 하 고 이미지, 비트맵 및 아이콘과 같은 할당 된 리소스를 해제 합니다.|
|`CMFCButton::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCButton::DrawItem`|소유자가 그린 단추의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다. ( [Cbutton::D rawitem](../../mfc/reference/cbutton-class.md#drawitem)를 재정의 합니다.)|
|[CMFCButton:: EnableFullTextTooltip](#enablefulltexttooltip)|도구 설명의 전체 텍스트를 작은 도구 설명 창에 표시할지 아니면 잘린 텍스트의 작은 도구 설명 창에 표시할지 여부를 지정 합니다.|
|[CMFCButton:: EnableMenuFont](#enablemenufont)|단추 텍스트 글꼴이 응용 프로그램 메뉴 글꼴과 동일한 지 여부를 지정 합니다.|
|[CMFCButton:: EnableWindowsTheming](#enablewindowstheming)|단추 테두리의 스타일이 현재 Windows 테마에 해당 하는지 여부를 지정 합니다.|
|`CMFCButton::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCButton:: GetToolTipCtrl](#gettooltipctrl)|기본 도구 설명 컨트롤에 대 한 참조를 반환 합니다.|
|[CMFCButton:: IsAutoCheck](#isautocheck)|확인란 또는 라디오 단추가 자동 단추 인지 여부를 나타냅니다.|
|[CMFCButton:: IsAutorepeatCommandMode](#isautorepeatcommandmode)|단추가 자동 반복 모드로 설정 되어 있는지 여부를 나타냅니다.|
|[CMFCButton:: IsCheckBox](#ischeckbox)|단추가 확인란 단추 인지 여부를 나타냅니다.|
|[CMFCButton:: IsChecked](#ischecked)|현재 단추가 선택 되어 있는지 여부를 나타냅니다.|
|[CMFCButton:: IsHighlighted](#ishighlighted)|단추가 강조 표시 되는지 여부를 나타냅니다.|
|[CMFCButton:: IsPressed](#ispressed)|단추가 푸시되 고 강조 표시 되는지 여부를 나타냅니다.|
|[CMFCButton:: IsPushed](#ispushed)|단추를 눌렀는지 여부를 나타냅니다.|
|[CMFCButton:: IsRadioButton](#isradiobutton)|단추가 라디오 단추 인지 여부를 나타냅니다.|
|[CMFCButton:: Iswindows이상 Ingenabled](#iswindowsthemingenabled)|단추 테두리의 스타일이 현재 Windows 테마와 일치 하는지 여부를 나타냅니다.|
|`CMFCButton::OnDrawParentBackground`|지정 된 영역에 단추의 부모 배경을 그립니다. ( [AFX_GLOBAL_DATA 재정의::D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 재정의합니다.)|
|[CMFCButton:: SetAutorepeatMode](#setautorepeatmode)|단추를 자동 반복 모드로 설정 합니다.|
|[CMFCButton:: SetCheckedImage](#setcheckedimage)|선택 된 단추의 이미지를 설정 합니다.|
|[CMFCButton:: SetFaceColor](#setfacecolor)|단추 텍스트의 배경색을 설정 합니다.|
|[CMFCButton:: SetImage](#setimage)|단추에 대 한 이미지를 설정 합니다.|
|[CMFCButton:: SetMouseCursor](#setmousecursor)|커서 이미지를 설정 합니다.|
|[CMFCButton:: SetMouseCursorHand](#setmousecursorhand)|커서를 손 모양으로 설정 합니다.|
|[CMFCButton:: SetStdImage](#setstdimage)|개체를 사용 하 여 `CMenuImages` 단추 이미지를 설정 합니다.|
|[CMFCButton:: SetTextColor](#settextcolor)|선택 하지 않은 단추의 단추 텍스트 색을 설정 합니다.|
|[CMFCButton:: SetTextHotColor](#settexthotcolor)|선택 된 단추에 대 한 단추 텍스트의 색을 설정 합니다.|
|[CMFCButton:: SetTooltip](#settooltip)|도구 설명을 단추와 연결 합니다.|
|[CMFCButton:: System.windows.window.sizetocontent](#sizetocontent)|단추 텍스트와 이미지를 포함 하는 단추의 크기를 조정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCButton:: OnDraw](#ondraw)|단추를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCButton:: OnDrawBorder](#ondrawborder)|단추의 테두리를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCButton:: OnDrawFocusRect](#ondrawfocusrect)|단추에 대 한 포커스 영역을 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCButton:: OnDrawText](#ondrawtext)|단추 텍스트를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCButton:: OnFillBackground](#onfillbackground)|단추 텍스트의 배경을 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCButton:: SelectFont](#selectfont)|지정 된 장치 컨텍스트와 연결 된 글꼴을 검색 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCButton:: m_nAlignStyle](#m_nalignstyle)|단추 텍스트의 맞춤을 지정 합니다.|
|[CMFCButton:: m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Windows XP 테마를 사용할지 여부를 지정 합니다.|
|[CMFCButton:: m_bDrawFocus](#m_bdrawfocus)|단추 주위에 포커스 사각형을 그릴지 여부를 나타냅니다.|
|[CMFCButton:: m_nFlatStyle](#m_nflatstyle)|테두리 없는, 평면, 반 평면 또는 3D와 같은 단추의 스타일을 지정 합니다.|
|[CMFCButton:: m_bGrayDisabled](#m_bGrayDisabled)|TRUE로 설정 하면 비활성화 된 단추를 회색으로 표시할 수 있습니다.|
|[CMFCButton:: m_bHighlightChecked](#m_bhighlightchecked)|커서를 포인터로 가리킬 때 BS_CHECKBOX 스타일 단추를 강조 표시할지 여부를 나타냅니다.|
|[CMFCButton:: m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|단추 다운 이벤트에 응답할지 여부를 나타냅니다.|
|[CMFCButton:: m_bRightImage](#m_brightimage)|단추의 오른쪽에 이미지를 표시할지 여부를 나타냅니다.|
|[CMFCButton:: m_bTopImage](#m_bTopImage)| 이미지가 단추 위에 있는지 여부를 나타냅니다.|
|[CMFCButton:: m_bTransparent](#m_btransparent)|단추가 투명 한지 여부를 나타냅니다.|
|[CMFCButton:: m_bWasDblClk](#m_bWasDblClk)| 마지막 클릭 이벤트를 두 번 클릭 했는지 여부를 나타냅니다.|

## <a name="remarks"></a>설명

다른 형식의 단추는 `CMFCButton` 하이퍼링크를 지 원하는 [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) 클래스 및 `CMFCColorButton` 색 선택 대화 상자를 지 원하는 클래스와 같이 클래스에서 파생 됩니다.

개체의 스타일은 `CMFCButton` *3d*, *평면*, *반 평면* 또는 *테두리가 없을* 수 있습니다. 단추 텍스트는 단추의 왼쪽, 위쪽 또는 가운데에 맞출 수 있습니다. 런타임에 텍스트, 이미지 또는 텍스트 및 이미지를 표시할지 여부를 제어할 수 있습니다. 커서를 단추 위로 가져갈 때 특정 커서 이미지를 표시 하도록 지정할 수도 있습니다.

코드에서 직접 또는 **MFC 클래스 마법사** 도구 및 대화 상자 템플릿을 사용 하 여 단추 컨트롤을 만듭니다. 단추 컨트롤을 직접 만드는 경우 `CMFCButton` 응용 프로그램에 변수를 추가한 다음 개체의 생성자와 메서드를 호출 합니다 `Create` `CMFCButton` . **MFC 클래스 마법사** 를 사용 하는 경우 `CButton` 응용 프로그램에 변수를 추가한 다음 변수의 형식을에서 `CButton` 로 변경 `CMFCButton` 합니다.

대화 상자 응용 프로그램에서 알림 메시지를 처리 하려면 각 알림에 대 한 메시지 맵 항목과 이벤트 처리기를 추가 합니다. 개체에서 보낸 알림은 `CMFCButton` 개체에서 보낸 알림과 동일 합니다 `CButton` .

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 단추의 속성을 구성 하는 방법을 보여 줍니다 `CMFCButton` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxbutton

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a> CMFCButton:: CleanUp

내부 변수를 다시 설정 하 고 이미지, 비트맵 및 아이콘과 같은 할당 된 리소스를 해제 합니다.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a> CMFCButton:: EnableFullTextTooltip

도구 설명의 전체 텍스트를 작은 도구 설명 창에 표시할지 아니면 잘린 텍스트의 작은 도구 설명 창에 표시할지 여부를 지정 합니다.

```cpp
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>매개 변수

*"Bon*<br/>
진행 모든 텍스트를 표시 하려면 TRUE이 고, 잘린 텍스트를 표시 하려면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a> CMFCButton:: EnableMenuFont

단추 텍스트 글꼴이 응용 프로그램 메뉴 글꼴과 동일한 지 여부를 지정 합니다.

```cpp
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>매개 변수

*"Bon*<br/>
진행 응용 프로그램 메뉴 글꼴을 단추 텍스트 글꼴로 사용 하려면 TRUE로 설정 합니다. FALSE 이면 시스템 글꼴을 사용 합니다. 기본값은 TRUE입니다.

*bRedraw*<br/>
진행 화면을 즉시 다시 그리려면 TRUE이 고, 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 단추 텍스트 글꼴을 지정 하지 않는 경우 [CWnd:: setfont](../../mfc/reference/cwnd-class.md#setfont) 메서드를 사용 하 여 글꼴을 지정할 수 있습니다. 글꼴을 전혀 지정 하지 않으면 프레임 워크에서 기본 글꼴을 설정 합니다.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a> CMFCButton:: EnableWindowsTheming

단추 테두리의 스타일이 현재 Windows 테마에 해당 하는지 여부를 지정 합니다.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 현재 Windows 테마를 사용 하 여 단추 테두리를 그리려면 TRUE로 설정 합니다. FALSE 이면 Windows 테마를 사용 하지 않습니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 클래스에서 파생 된 응용 프로그램의 모든 단추에 영향을 줍니다 `CMFCButton` .

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a> CMFCButton:: GetToolTipCtrl

기본 도구 설명 컨트롤에 대 한 참조를 반환 합니다.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>반환 값

기본 도구 설명 컨트롤에 대 한 참조입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a> CMFCButton:: IsAutoCheck

확인란 또는 라디오 단추가 자동 단추 인지 여부를 나타냅니다.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>반환 값

단추에 스타일 BS_AUTOCHECKBOX 또는 BS_AUTORADIOBUTTON 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a> CMFCButton:: IsAutorepeatCommandMode

단추가 자동 반복 모드로 설정 되어 있는지 여부를 나타냅니다.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>반환 값

단추가 자동 반복 모드로 설정 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[Cmfcbutton:: SetAutorepeatMode](#setautorepeatmode) 메서드를 사용 하 여 단추를 자동 반복 모드로 설정 합니다.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a> CMFCButton:: IsCheckBox

단추가 확인란 단추 인지 여부를 나타냅니다.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>반환 값

단추에 BS_CHECKBOX 또는 BS_AUTOCHECKBOX 스타일이 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a> CMFCButton:: IsChecked

현재 단추가 선택 되어 있는지 여부를 나타냅니다.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>반환 값

현재 단추가 선택 되어 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크는 서로 다른 종류의 단추를 선택 하 여 선택 된 것으로 표시 합니다. 예를 들어, 점이 있는 경우 라디오 단추가 선택 됩니다. **X** 가 포함 되어 있으면 확인란이 선택 됩니다.

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a> CMFCButton:: IsHighlighted

단추가 강조 표시 되는지 여부를 나타냅니다.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>반환 값

단추가 강조 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

마우스로 단추를 가리키면 단추가 강조 표시 됩니다.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a> CMFCButton:: IsPressed

단추가 푸시되 고 강조 표시 되는지 여부를 나타냅니다.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>반환 값

단추를 누르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a> CMFCButton:: IsPushed

단추를 눌렀는지 여부를 나타냅니다.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>반환 값

단추가 푸시되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a> CMFCButton:: IsRadioButton

단추가 라디오 단추 인지 여부를 나타냅니다.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>반환 값

단추 스타일이 BS_RADIOBUTTON 또는 BS_AUTORADIOBUTTON 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a> CMFCButton:: Iswindows이상 Ingenabled

단추 테두리의 스타일이 현재 Windows 테마와 일치 하는지 여부를 나타냅니다.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>반환 값

단추 테두리의 스타일이 현재 Windows 테마와 일치 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton:: m_bDontUseWinXPTheme

단추를 그릴 때 Windows XP 테마를 사용할지 여부를 지정 합니다.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a> CMFCButton:: m_bDrawFocus

단추 주위에 포커스 사각형을 그릴지 여부를 나타냅니다.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>설명

`m_bDrawFocus`멤버가 포커스를 받을 때 프레임 워크에서 단추의 텍스트와 이미지 주위에 포커스 사각형을 그리도록 지정 하려면 멤버를 TRUE로 설정 합니다.

`CMFCButton`생성자는이 멤버를 TRUE로 초기화 합니다.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a> CMFCButton:: m_bGrayDisabled

TRUE로 설정 하면 비활성화 된 단추를 회색으로 표시할 수 있습니다.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a> CMFCButton:: m_bHighlightChecked

커서를 포인터로 가리킬 때 BS_CHECKBOX 스타일 단추를 강조 표시할지 여부를 나타냅니다.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>설명

멤버가 마우스로 `m_bHighlightChecked` 가리킬 때 BS_CHECKBOX 스타일 단추가 강조 표시 되도록 지정 하려면 멤버를 TRUE로 설정 합니다.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a> CMFCButton:: m_bResponseOnButtonDown

단추 다운 이벤트에 응답할지 여부를 나타냅니다.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a> CMFCButton:: m_bRightImage

단추의 오른쪽에 이미지를 표시할지 여부를 나타냅니다.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a> CMFCButton:: m_bTopImage] (#m_bTopImage)

이미지가 단추 위에 있는지 여부를 나타냅니다.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>설명

멤버를 `m_bRightImage` TRUE로 설정 하 여 프레임 워크에서 단추의 텍스트 레이블 오른쪽에 단추의 이미지를 표시 하도록 지정 합니다.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a> CMFCButton:: m_bTransparent

단추가 투명 한지 여부를 나타냅니다.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>설명

멤버를 `m_bTransparent` TRUE로 설정 하 여 프레임 워크가 단추를 투명 하 게 만들도록 지정 합니다. `CMFCButton`생성자는이 멤버를 FALSE로 초기화 합니다.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a> CMFCButton:: m_nAlignStyle

단추 텍스트의 맞춤을 지정 합니다.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>설명

다음 열거형 값 중 하나 `CMFCButton::AlignStyle` 를 사용 하 여 단추 텍스트의 맞춤을 지정 합니다.

|값|설명|
|-----------|-----------------|
|ALIGN_CENTER|기본 단추 텍스트를 단추의 가운데로 맞춥니다.|
|ALIGN_LEFT|단추 텍스트를 단추의 왼쪽에 맞춥니다.|
|ALIGN_RIGHT|단추 텍스트를 단추의 오른쪽에 맞춥니다.|

`CMFCButton`생성자는 ALIGN_CENTER이 멤버를 초기화 합니다.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a> CMFCButton:: m_bWasDblClk] (#m_bWasDblClk) |

마지막 클릭 이벤트를 두 번 클릭 했는지 여부를 나타냅니다. |

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a> CMFCButton:: m_nFlatStyle

테두리 없는, 평면, 반 평면 또는 3D와 같은 단추의 스타일을 지정 합니다.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>설명

다음 표에서는 `CMFCButton::m_nFlatStyle` 단추의 모양을 지정 하는 열거형 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|BUTTONSTYLE_3D|기본 단추가 3 차원 면이 표시 됩니다. 단추를 클릭 하면 단추가 전체 들여쓰기로 눌러져 있습니다.|
|BUTTONSTYLE_FLAT|단추가 단추 위에 표시 되지 않는 경우 단추는 2 차원으로 표시 되 고 반대쪽은 표시 되지 않습니다. 단추 위로 마우스를 가져가면 단추가 3 차원 면이 표시 됩니다. 단추를 클릭 하면 단추가 단순 들여쓰기로 눌러져 있습니다.|
|BUTTONSTYLE_SEMIFLAT|단추가 3 차원 면이 표시 됩니다. 단추를 클릭 하면 단추가 전체 들여쓰기로 눌러져 있습니다.|
|BUTTONSTYLE_NOBORDERS|이 단추에는 발생 한 측면이 없고 항상 2 차원으로 표시 됩니다. 단추를 클릭 하면 해당 단추가 들여쓰기로 눌러져 있지 않습니다.|

`CMFCButton`생성자는 BUTTONSTYLE_3D이 멤버를 초기화 합니다.

### <a name="example"></a>예제

다음 예제에서는 `m_nFlatStyle` 클래스에서 멤버 변수의 값을 설정 하는 방법을 보여 줍니다 `CMFCButton` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a> CMFCButton:: OnDraw

단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 단추를 제한 하는 사각형에 대 한 참조입니다.

*uiState*<br/>
진행 현재 단추 상태입니다. 자세한 내용은 `itemState` [Drawitemstruct 구조체](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 항목의 멤버를 참조 하십시오.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 단추를 그리려면이 메서드를 재정의 합니다.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a> CMFCButton:: OnDrawBorder

단추의 테두리를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectClient*<br/>
진행 단추를 제한 하는 사각형에 대 한 참조입니다.

*uiState*<br/>
진행 현재 단추 상태입니다. 자세한 내용은 `itemState` [Drawitemstruct 구조체](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 항목의 멤버를 참조 하십시오.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 테두리를 그리려면이 메서드를 재정의 합니다.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCButton:: OnDrawFocusRect

단추에 대 한 포커스 영역을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectClient*<br/>
진행 단추를 제한 하는 사각형에 대 한 참조입니다.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 포커스 영역을 그리도록이 메서드를 재정의 합니다.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a> CMFCButton:: OnDrawText

단추 텍스트를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 단추를 제한 하는 사각형에 대 한 참조입니다.

*strText*<br/>
진행 그릴 텍스트입니다.

*uiDTFlags*<br/>
진행 텍스트의 서식을 지정 하는 방법을 지정 하는 플래그입니다. 자세한 내용은 [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) 메서드의 *nformat* 매개 변수를 참조 하세요.

*uiState*<br/>
[in] 예약되어 있습니다.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 단추 텍스트를 그리려면이 메서드를 재정의 합니다.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a> CMFCButton:: OnFillBackground

단추 텍스트의 배경을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectClient*<br/>
진행 단추를 제한 하는 사각형에 대 한 참조입니다.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 단추의 배경을 그리려면이 메서드를 재정의 합니다.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a> CMFCButton:: SelectFont

지정 된 장치 컨텍스트와 연결 된 글꼴을 검색 합니다.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

사용자 고유의 코드를 사용 하 여 글꼴을 검색 하려면이 메서드를 재정의 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a> CMFCButton:: SetAutorepeatMode

단추를 자동 반복 모드로 설정 합니다.

```cpp
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>매개 변수

*nTimeDelay*<br/>
진행 부모 창으로 전송 되는 메시지 사이의 간격을 지정 하는 음수가 아닌 숫자입니다. 간격은 밀리초 단위로 측정 되며 기본값은 500 밀리초입니다. 자동 반복 메시지 모드를 사용 하지 않으려면 0을 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 단추가 해제 되거나 *Ntimedelay* 매개 변수가 0으로 설정 될 때까지 단추에서 부모 창으로 메시지를 지속적으로 WM_COMMAND 보냅니다.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a> CMFCButton:: SetCheckedImage

선택 된 단추의 이미지를 설정 합니다.

```cpp
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
진행 새 이미지에 대 한 비트맵과 마스크를 포함 하는 아이콘에 대 한 핸들입니다.

*bAutoDestroy*<br/>
진행 비트맵 리소스가 자동으로 제거 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

*hIconHot*<br/>
진행 선택 된 상태에 대 한 이미지를 포함 하는 아이콘에 대 한 핸들입니다.

*hBitmap*<br/>
진행 선택 되지 않은 상태의 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*hBitmapHot*<br/>
진행 선택 된 상태에 대 한 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*bMap3dColors*<br/>
진행 단추 배경의 투명 색을 지정 합니다. 즉, 단추의 얼굴입니다. RGB (192, 192, 192) 색 값을 사용 하려면 TRUE로 설정 합니다. FALSE 이면에 정의 된 색 값을 사용 `AFX_GLOBAL_DATA::clrBtnFace` 합니다.

*uiBmpResId*<br/>
진행 선택 하지 않은 이미지에 대 한 리소스 ID입니다.

*uiBmpHotResId*<br/>
진행 선택한 이미지에 대 한 리소스 ID입니다.

*hIconDisabled*<br/>
진행 비활성화 된 이미지의 아이콘에 대 한 핸들입니다.

*hBitmapDisabled*<br/>
진행 비활성화 된 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*uiBmpDsblResID*<br/>
진행 비활성화 된 비트맵의 리소스 ID입니다.

*bAlphaBlend*<br/>
진행 알파 채널을 사용 하는 32 비트 이미지만 사용 하려면 TRUE로 설정 합니다. 알파 채널 이미지만 사용 하지 않으려면 FALSE로 설정 합니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a> CMFCButton:: SetFaceColor

단추 텍스트의 배경색을 설정 합니다.

```cpp
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>매개 변수

*crFace*<br/>
진행 RGB 색 값입니다.

*bRedraw*<br/>
진행 화면을 즉시 다시 그리면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 단추 배경 (얼굴)의 새 채우기 색을 정의 합니다. [Cmfcbutton:: m_bTransparent](#m_btransparent) 멤버 변수가 TRUE 인 경우 배경은 채워지지 않습니다.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a> CMFCButton:: SetImage

단추에 대 한 이미지를 설정 합니다.

```cpp
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
진행 새 이미지에 대 한 비트맵과 마스크를 포함 하는 아이콘에 대 한 핸들입니다.

*bAutoDestroy*<br/>
진행 비트맵 리소스가 자동으로 제거 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

*hIconHot*<br/>
진행 선택 된 상태에 대 한 이미지를 포함 하는 아이콘에 대 한 핸들입니다.

*hBitmap*<br/>
진행 선택 되지 않은 상태의 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*hBitmapHot*<br/>
진행 선택 된 상태에 대 한 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*uiBmpResId*<br/>
진행 선택 하지 않은 이미지에 대 한 리소스 ID입니다.

*uiBmpHotResId*<br/>
진행 선택한 이미지에 대 한 리소스 ID입니다.

*bMap3dColors*<br/>
진행 단추 배경의 투명 색을 지정 합니다. 즉, 단추의 얼굴입니다. RGB (192, 192, 192) 색 값을 사용 하려면 TRUE로 설정 합니다. FALSE 이면에 정의 된 색 값을 사용 `AFX_GLOBAL_DATA::clrBtnFace` 합니다.

*hIconDisabled*<br/>
진행 비활성화 된 이미지의 아이콘에 대 한 핸들입니다.

*hBitmapDisabled*<br/>
진행 비활성화 된 이미지를 포함 하는 비트맵에 대 한 핸들입니다.

*uiBmpDsblResID*<br/>
진행 비활성화 된 비트맵의 리소스 ID입니다.

*bAlphaBlend*<br/>
진행 알파 채널을 사용 하는 32 비트 이미지만 사용 하려면 TRUE로 설정 합니다. 알파 채널 이미지만 사용 하지 않으려면 FALSE로 설정 합니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 버전의 메서드를 사용 하는 방법을 보여 줍니다 `SetImage` `CMFCButton` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a> CMFCButton:: SetMouseCursor

커서 이미지를 설정 합니다.

```cpp
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>매개 변수

*hcursor*<br/>
진행 커서의 핸들입니다.

### <a name="remarks"></a>설명

손 모양 커서와 같은 커서 이미지를 단추와 연결 하려면이 메서드를 사용 합니다. 커서는 응용 프로그램 리소스에서 로드 됩니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `SetMouseCursor` `CMFCButton` . 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)에서 코드의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a> CMFCButton:: SetMouseCursorHand

커서를 손 모양으로 설정 합니다.

```cpp
void SetMouseCursorHand();
```

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 손 모양 커서 이미지를 단추와 연결 합니다. 커서는 응용 프로그램 리소스에서 로드 됩니다.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a> CMFCButton:: SetStdImage

개체를 사용 하 여 `CMenuImages` 단추 이미지를 설정 합니다.

```cpp
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 열거형에 정의 된 단추 이미지 식별자 중 하나입니다 `CMenuImage::IMAGES_IDS` . 이미지 값은 화살표, 핀 및 라디오 단추와 같은 이미지를 지정 합니다.

*state*<br/>
진행 열거형에 정의 된 단추 이미지 상태 식별자 중 하나입니다 `CMenuImages::IMAGE_STATE` . 이미지 상태는 검정, 회색, 연한 회색, 흰색 및 진한 회색 등의 단추 색을 지정 합니다. 기본값은 `CMenuImages::ImageBlack`입니다.

*idDisabled*<br/>
진행 열거형에 정의 된 단추 이미지 식별자 중 하나입니다 `CMenuImage::IMAGES_IDS` . 이미지는 단추를 사용할 수 없음을 나타냅니다. 기본값은 첫 번째 단추 이미지 ()입니다 `CMenuImages::IdArrowDown` .

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a> CMFCButton:: SetTextColor

선택 하지 않은 단추의 단추 텍스트 색을 설정 합니다.

```cpp
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>매개 변수

*clrText*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a> CMFCButton:: SetTextHotColor

선택 된 단추에 대 한 단추 텍스트의 색을 설정 합니다.

```cpp
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>매개 변수

*clrTextHot*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a> CMFCButton:: SetTooltip

도구 설명을 단추와 연결 합니다.

```cpp
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>매개 변수

*lpszToolTipText*<br/>
진행 도구 설명의 텍스트에 대 한 포인터입니다. 도구 설명을 사용 하지 않도록 설정 하려면 NULL을 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCButton:: System.windows.window.sizetocontent

단추 텍스트와 이미지를 포함 하는 단추의 크기를 조정 합니다.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>매개 변수

*bCalcOnly*<br/>
진행 단추의 새 크기를 계산 하지만 변경 하지 않으려면 TRUE로 설정 합니다. FALSE 이면 단추의 크기를 변경 합니다. 기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

`CSize`단추의 새 크기를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 가로 여백이 10 픽셀이 고 세로 여백이 5 픽셀인 새 크기를 계산 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 클래스](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 클래스](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 클래스](../../mfc/reference/cmfcmenubutton-class.md)
