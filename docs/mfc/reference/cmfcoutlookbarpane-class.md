---
title: CMFCOutlookBarPane 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2d468ded9db1d21fd19bc553ed2a0c3227725a0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075556"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 클래스

자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.

파생 되는 컨트롤 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md) Outlook 표시줄에 삽입할 수 있는 ( [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)). Outlook 표시줄 창에 큰 단추의 열이 포함되어 있습니다. 단추 목록이 창보다 크면 위 아래로 스크롤할 수 있습니다. 사용자가 Outlook 표시줄 창을 Outlook 표시줄에서 분리하면 기본 프레임 창에서 이동하거나 도킹할 수 있습니다.

## <a name="syntax"></a>구문

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|기본 생성자입니다.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Outlook 표시줄 창에 단추를 추가합니다.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|창의 다른 창이 나 프레임 창에 도킹할 수 있는지 여부를 결정 합니다. (재정의 [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|여부를 시스템 후 복원할 수는 도구 모음을 원래 상태로 사용자 지정을 결정 합니다. (재정의 [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Outlook 표시줄 창에 이미지를 사용 하는 리소스를 해제 합니다.|
|[CMFCOutlookBarPane::Create](#create)|Outlook 표시줄 창을 만듭니다.|
|`CMFCOutlookBarPane::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCOutlookBarPane::Dock`|Outlook 표시줄 창을 도킹 프레임 워크에서 호출 됩니다. ( `CPane::Dock`을 재정의합니다.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Outlook 표시줄 창에 있는 스크롤 화살표 단추 또는 페이지에서 단추 목록을 이동 하는지 여부를 지정 합니다.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Outlook 표시줄 창입니다 (선택 되지 않은) 하는 일반 텍스트 색을 반환합니다.|
|`CMFCOutlookBarPane::GetThisClass`|에 대 한 포인터를 가져오는 데 프레임 워크에 의해 합니다 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 이 클래스 형식과 연결 된 개체입니다.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Outlook 표시줄 창에 대 한 로드 배경 이미지 인지 확인 합니다.|
|`CMFCOutlookBarPane::IsChangeState`|부동 창에 도킹할 수 있는지 여부를 결정 합니다. ( `CPane::IsChangeState`을 재정의합니다.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|단추가 강조 표시 하 고 배경 이미지에 표시 되 면 단추 테두리 음영 처리 된 인지 확인 합니다.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Float에 대 한이 되 면 프레임 워크에서 호출 됩니다. (재정의 [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|지정 된 명령 ID가 있는 단추를 제거 합니다.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|도구 모음의 원래 상태를 복원합니다. (재정의 [cmfctoolbar:: Restoreoriginalstate](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|배경색을 설정 합니다.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|배경 이미지를 설정합니다.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Outlook 표시줄 창에는 원래 일련의 단추를 다시 설정합니다.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Outlook 표시줄 창에 단추 주위에 사용 되는 패딩 픽셀 수를 설정 합니다.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Outlook 표시줄 창에 일반 및 강조 표시 된 텍스트의 색을 설정합니다.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Outlook 표시줄 창에 대 한 투명 한 색을 설정합니다.|
|`CMFCOutlookBarPane::SmartUpdate`|Outlook 표시줄을 업데이트 하려면 내부적으로 사용 합니다. ( `CMFCToolBar::SmartUpdate`을 재정의합니다.)|

### <a name="protected-methods"></a>보호된 메서드

|이름|설명|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|사용자 지정 모드에 표시 되는 바로 가기 메뉴 항목을 지정 합니다.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Outlook 표시줄 창에서 모든 단추를 제거합니다. (재정의 [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>설명

Outlook 표시줄을 구현 하는 방법에 대 한 자세한 내용은 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)합니다.

Outlook 표시줄의 예로, OutlookDemo 샘플 프로젝트를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는의 다양 한 메서드를 사용 하는 방법에 설명 합니다 `CMFCOutlookBarPane` 클래스입니다. Outlook 표시줄 창을 만들, 페이지 스크롤 모드를 사용 하도록 설정, 도킹을 사용 하도록 설정 하 고 Outlook 표시줄의 배경색을 설정 하는 방법을 보여 줍니다. 이 코드 조각은의 일부인 합니다 [Outlook 다중 뷰 샘플](../../visual-cpp-samples.md)합니다.

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxoutlookbarpane.h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

Outlook 표시줄 창에 단추를 추가합니다.

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>매개 변수

*uiImage*<br/>
[in] 비트맵의 리소스 식별자를 지정합니다.

*lpszLabel*<br/>
[in] 단추의 텍스트를 지정합니다.

*iIdCommand*<br/>
[in] 단추 컨트롤의 ID를 지정합니다.

*iInsertAt*<br/>
[in] Outlook 표시줄 페이지 단추를 삽입할 0부터 시작 인덱스를 지정 합니다.

*uiLabel*<br/>
[in] 문자열 리소스 id입니다.

*szBmpFileName*<br/>
[in] 로드할 디스크 이미지 파일의 이름을 지정 합니다.

*szLabel*<br/>
[in] 단추의 텍스트를 지정합니다.

*hBmp*<br/>
[in] 단추의 비트맵 핸들입니다.

*hIcon*<br/>
[in] 버튼의 아이콘에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

TRUE 이면 단추를 추가 했습니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Outlook 표시줄의 페이지에 새 단추를 삽입 하려면이 메서드를 사용 합니다. 디스크 파일 또는 응용 프로그램 리소스에서 단추의 이미지를 로드할 수 있습니다.

페이지 ID를 지정 하면 *uiPageID* 가-1 이면 첫 번째 페이지에 단추 삽입 됩니다.

으로 지정 된 인덱스 *iInsertAt* 가-1 이면 단추를 페이지의 끝에 추가 됩니다.

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

Outlook 표시줄 창에 이미지를 사용 하는 리소스를 해제 합니다.

```
void ClearAll();
```

### <a name="remarks"></a>설명

이 메서드를 직접 호출 [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), Outlook 표시줄 창에 사용 되는 이미지에 이라고 합니다.

##  <a name="create"></a>  CMFCOutlookBarPane::Create

Outlook 표시줄 창을 만듭니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
[in] Outlook 표시줄 창 컨트롤의 부모 창을 지정합니다. NULL이 아니어야 합니다.

*dwStyle*<br/>
[in] 창 스타일입니다.  창 스타일의 목록은 참조 하세요 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)합니다.

*uiID*<br/>
[in] 컨트롤 id입니다. 사용할 수 있도록 고유 컨트롤의 상태를 저장 합니다.

*dwControlBarStyle*<br/>
[in] Outlook 표시줄에서 분리 될 때 Outlook 표시줄 창 컨트롤의 동작을 정의 하는 특별 한 스타일을 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

생성 하는 `CMFCOutlookBarPane` 개체 먼저 생성자를 호출 하 고, 호출 하 `Create`, Outlook 표시줄 창 컨트롤을 만들고 연결 하는 `CMFCOutlookBarPane` 개체입니다.

에 대 한 자세한 내용은 `dwControlBarStyle` 참조 [cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)합니다.

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

사용자 지정 모드에 표시 되는 바로 가기 메뉴 항목을 지정 합니다.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>매개 변수

*pButton*<br/>
[in] 사용자를 클릭 하는 도구 모음 단추에 대 한 포인터입니다.

*pPopup*<br/>
[in] 바로 가기 메뉴에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

TRUE를 반환 하는 경우 바로 가기 메뉴를 표시할; 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크를 사용자 지정 모드로 표시 하는 프레임 워크 표준 바로 가기 메뉴를 수정 하려면이 메서드를 재정의 합니다.

사용자 지정 모드를 확인 하는 기본 구현 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) 하는 경우 모든 바로 가기 메뉴 항목 TRUE 이면 사용 하지 않도록 설정 하려면 설정 제외 **삭제**합니다. 그런 다음 입력된 매개 변수를 방금 전달 `CMFCToolBar::EnableContextMenuItems`합니다.

> [!NOTE]
> *상황에 맞는 메뉴* 바로 가기 메뉴의 동의어입니다.

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

Outlook 표시줄 창에 있는 스크롤 화살표 단추를 페이지 별로 또는 단추에서 목록 이동 하는지 여부를 지정 합니다.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>매개 변수

*bPageScroll*<br/>
[in] TRUE 이면 페이지 스크롤 모드를 사용 하도록 설정 합니다. FALSE 이면 페이지 스크롤 모드를 사용 하지 않도록 설정 합니다.

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

일반 반환 (즉, 선택 되지 않은) Outlook 표시줄 창의 텍스트 색입니다.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>반환 값

RGB 색 값으로 현재 텍스트 색입니다.

### <a name="remarks"></a>설명

사용 하 여 [CMFCOutlookBarPane::SetTextColor](#settextcolor) Outlook 표시줄의 현재 (일반 및 선택한) 텍스트 색을 설정 합니다. 호출 하 여 기본 텍스트 색을 가져올 수 있습니다 합니다 [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) COLOR_WINDOW 인덱스를 사용 하 여 함수입니다.

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

Outlook 표시줄 창에 대 한 로드 배경 이미지 인지 확인 합니다.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>반환 값

TRUE 이면; 표시할 배경 이미지 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

호출 하 여 배경 이미지를 추가할 수 있습니다 [CMFCOutlookBarPane::SetBackImage](#setbackimage) 함수입니다.

배경 이미지가 없는 경우 배경을 사용 하 여 지정 된 색을 사용 하 여 그려집니다 [CMFCOutlookBarPane::SetBackColor](#setbackcolor)합니다.

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

단추가 강조 표시 하 고 배경 이미지에 표시 되 면 단추 테두리 음영 처리 된 인지 확인 합니다.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>반환 값

단추의 테두리; 음영 처리 된 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

Outlook 표시줄 창에서 모든 단추를 제거합니다.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

지정 된 명령 ID가 있는 단추를 제거 합니다.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>매개 변수

*iIdCommand*<br/>
[in] 제거할 단추의 명령 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

단추 제거 되었으면 TRUE 지정된 된 명령 ID 유효 하지 않은 경우 FALSE입니다.

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

Outlook 표시줄의 배경색을 설정합니다.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*색*<br/>
[in] 새 배경색을 지정합니다.

### <a name="remarks"></a>설명

Outlook 표시줄의 현재 배경색을 설정 하려면이 함수를 호출 합니다. 배경 색상 배경 이미지가 없는 경우에 사용 됩니다.

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

배경 이미지를 설정합니다.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>매개 변수

*uiImageID*<br/>
[in] 이미지 리소스 ID를 지정합니다.

### <a name="remarks"></a>설명

Outlook을 설정 하려면이 메서드를 호출 막대의 배경 이미지입니다. 배경 이미지의 목록 관리를 포함 하 여 [CMFCToolBarImages 클래스](../../mfc/reference/cmfctoolbarimages-class.md) 개체입니다.

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

Outlook 표시줄 창에는 원래 일련의 단추를 다시 설정합니다.

```
void SetDefaultState();
```

### <a name="remarks"></a>설명

이 메서드는 원래 집합에 Outlook 표시줄 단추를 복원합니다. 이 메서드는 `CMFCOutlookBarPane::RestoreOriginalstate`Outlook 표시줄 창 다시 그리기를 트리거하지 않는다는 점을 제외 하 고, 합니다.

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

Outlook 표시줄 창에 단추 주위에 사용 되는 패딩 픽셀 수를 설정 합니다.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

Outlook 표시줄 창에 일반 및 강조 표시 된 텍스트의 색을 설정합니다.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>매개 변수

*clrRegText*<br/>
[in] 선택 되지 않은 텍스트에 대 한 새 색을 지정합니다.

*clrSelText*<br/>
[in] 선택한 텍스트에 대 한 새 색을 지정합니다.

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

Outlook 표시줄 창에 대 한 투명 한 색을 설정합니다.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*색*<br/>
새 투명 한 색을 지정합니다.

### <a name="remarks"></a>설명

투명 한 색은 투명 이미지를 표시 해야 합니다. 모든 이미지에서이 색이 발생 하는 대신 배경색을 사용 하 여 그려집니다.  배경 및 전경 이미지를 혼합 하 없습니다 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 클래스](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
