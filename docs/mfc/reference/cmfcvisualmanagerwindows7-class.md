---
description: '자세히 알아보기: CMFCVisualManagerWindows7 클래스'
title: CMFCVisualManagerWindows7 클래스
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 108d4144bbcfbfcb82d91678611435f14365302e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331640"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 클래스

는 `CMFCVisualManagerWindows7` Windows 7 응용 프로그램의 모양을 응용 프로그램에 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|기본 생성자입니다.|
|[CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7](#_dtorcmfcvisualmanagerwindows7)|기본 소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|현재 비주얼 스타일을 지우고 기본 비주얼 스타일을 다시 설정 합니다.|
|`CMFCVisualManagerWindows7::CleanUp`|사용자 인터페이스에서 개체를 모두 지우고 메뉴를 다시 설정 합니다.|
|`CMFCVisualManagerWindows7::DrawNcBtn`|비클라이언트 영역에서 프레임의 단추를 그립니다. 프레임 워크는이 메서드를 사용 하 여 창 프레임의 오른쪽 위 모퉁이에 최소화, 최대화, 닫기 및 복원 단추를 그립니다. 이 메서드는 프로그램에서 테마를 사용 하는 경우에만 호출 됩니다 `Aero` .|
|`CMFCVisualManagerWindows7::DrawNcText`|프레임의 비클라이언트 영역에 텍스트를 그립니다. 프레임 워크는이 메서드를 사용 하 여 프레임 창의 위쪽에 있는 제목 표시줄에 응용 프로그램 제목을 그립니다.|
|`CMFCVisualManagerWindows7::DrawSeparator`|[Cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md)에 구분 기호를 그립니다.|
|`CMFCVisualManagerWindows7::GetRibbonBar`|사용자 인터페이스와 연결 된 [Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md) 를 검색 합니다.|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|리본 편집 상자 배경색을 가져옵니다.|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|[Cmfcvisualmanager:: GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|[Cmfcvisualmanager:: GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|[Cmfcvisualmanager:: GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|[Cmfcvisualmanagerwindows:: IsHighlightWholeMenuItem를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem) 재정의 합니다.|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|[Cmfcvisualmanager:: IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|가 있고 표시 되는지 여부를 확인 `CMFCRibbonBar` 합니다.|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|[Cmfcvisualmanagerwindows:: OnDrawButtonBorder를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|[Cmfcvisualmanagerwindows:: OnDrawCheckBoxEx를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|[Cmfcvisualmanagerwindows:: OnDrawComboDropButton를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|[Cmfcvisualmanager:: OnDrawDefaultRibbonImage를](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|[Cmfcvisualmanagerwindows:: OnDrawMenuBorder를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|[Cmfcvisualmanager:: OnDrawMenuCheck를](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|[Cmfcvisualmanager:: OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|`CMFCVisualManager::OnDrawRadioButton`를 재정의합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|[Cmfcvisualmanager:: Ondraw리본 Applicationbutton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|[Cmfcvisualmanager:: Ondraw리본 Buttonborder를](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|[Cmfcvisualmanager:: Ondraw리본 캡션을](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|[Cmfcvisualmanager:: Ondraw리본 Captionbutton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|[Cmfcvisualmanager:: Ondraw리본 범주를](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|[Cmfcvisualmanager:: Ondraw리본 Categorytab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|[Cmfcvisualmanager:: OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|[Cmfcvisualmanager:: OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|`CMFCVisualManager::OnDrawRibbonLaunchButton`를 재정의합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|[Cmfcvisualmanager:: Ondraw리본 Menucheckframe](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|[Cmfcvisualmanager:: Ondraw리본 패널](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|[Cmfcvisualmanager:: OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|[Cmfcvisualmanager:: Ondraw리본 progressbar를](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|[Cmfcvisualmanager:: OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|[Cmfcvisualmanager:: OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|[Cmfcvisualmanager:: OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|[Cmfcvisualmanager:: OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|[Cmfcvisualmanager:: OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|[Cmfcvisualmanager:: Ondraw리본 Tabsframe](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe) 을 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|[Cmfcvisualmanagerwindows:: OnDrawStatusBarSizeBox를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|[Cmfcvisualmanagerwindows:: Onfill바 배경을](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|[Cmfcvisualmanagerwindows:: OnFillButtonInterior를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior) 재정의 합니다.|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|프레임 워크는 메뉴 항목 이미지 주위에 영역을 채울 때이 메서드를 호출 합니다.|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|[Cmfcvisualmanager:: Onfill리본 단추를](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|[Cmfcvisualmanager:: OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|[Cmfcvisualmanagerwindows:: OnHighlightMenuItem를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem) 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnNcActivate`|[Cmfcvisualmanager:: OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnNcPaint`|[Cmfcvisualmanager:: OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint) 를 재정의 합니다.|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|[Cmfcvisualmanagerwindows:: OnUpdateSystemColors를](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors) 재정의 합니다.|
|`CMFCVisualManagerWindows7::SetResourceHandle`|비주얼 관리자의 특성을 설명 하는 리소스 핸들을 설정 합니다.|
|`CMFCVisualManagerWindows7::SetStyle`|GUI의 색 구성표를 설정 합니다 `CMFCVisualManagerWindows7` .|

## <a name="remarks"></a>설명

클래스를 사용 하 여 `CMFCVisualManagerWindows7` 기본 Windows 7 응용 프로그램을 모방 하도록 응용 프로그램의 모양을 변경 합니다. 응용 프로그램이 Windows 7 이전 버전의 Windows에서 실행 되는 경우에는이 클래스가 유효 하지 않을 수 있습니다. 이 시나리오에서 응용 프로그램은 [Cmfcvisualmanager](../../mfc/reference/cmfcvisualmanager-class.md)에 정의 된 기본 visual manager를 사용 합니다.

CMFCVisualManagerWindows7는 [Cmfcvisualmanagerwindows 클래스](../../mfc/reference/cmfcvisualmanagerwindows-class.md) 와 클래스의 여러 메서드를 상속 합니다 `CMFCVisualManager` . 이전 섹션에 나열 된 메서드는 클래스에 대 한 새로운 메서드입니다 `CMFCVisualManagerWindows7` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>요구 사항

**헤더:** afxvisualmanagerwindows7

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7

기본 소멸자입니다.

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

기본 생성자입니다.

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a> CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

리본 편집 상자의 배경색을 가져옵니다.

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>매개 변수

*pEdit*<br/>
진행 편집 컨트롤에 대 한 포인터입니다. 이 값은 NULL 일 수 없습니다.

*bIsHighlighted*<br/>
제한이 리본 상자를 강조 표시할지 여부를 반환 합니다.

*bIsPaneHighlighted*<br/>
제한이 *Pedit* 가 포함 된 리본 패널이 강조 표시 되 면 TRUE를 반환 합니다.

*bIsDisabled*<br/>
제한이 *Pedit* 가 사용 하지 않도록 설정 되었는지 여부를 반환 합니다.

### <a name="return-value"></a>반환 값

편집 상자 *Pedit* 의 배경색입니다.

### <a name="remarks"></a>설명

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a> CMFCVisualManagerWindows7::OnFillMenuImageRect

프레임 워크는 메뉴 항목 이미지 주위에 영역을 채울 때이 메서드를 호출 합니다.

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 메뉴 단추의 장치 컨텍스트에 대 한 포인터입니다.

*pButton*<br/>
진행 에 대 한 포인터 `CMFCToolBarButton` 입니다. 프레임 워크는이 단추의 배경을 채웁니다.

*사각형*<br/>
진행 메뉴 단추 이미지 영역의 경계를 지정 하는 사각형입니다.

*state*<br/>
진행 단추 상태입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 클래스](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows 클래스](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
