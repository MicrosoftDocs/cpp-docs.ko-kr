---
description: '자세히 알아보기: CMFCOutlookBarPane 클래스'
title: CMFCOutlookBarPane 클래스
ms.date: 11/04/2016
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
ms.openlocfilehash: f1bcae298a9541920f6deeb9a3bce22e49222cb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265027"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 클래스

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

Outlook 표시줄 ( [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md))에 삽입할 수 있는 [cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md) 에서 파생 된 컨트롤입니다. Outlook 표시줄 창에 큰 단추의 열이 포함되어 있습니다. 단추 목록이 창보다 크면 위 아래로 스크롤할 수 있습니다. 사용자가 Outlook 표시줄 창을 Outlook 표시줄에서 분리하면 기본 프레임 창에서 이동하거나 도킹할 수 있습니다.

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
|[CMFCOutlookBarPane:: AddButton](#addbutton)|Outlook 표시줄 창에 단추를 추가 합니다.|
|[CMFCOutlookBarPane:: CanBeAttached](#canbeattached)|창을 다른 창이 나 프레임 창에 도킹할 수 있는지 여부를 결정 합니다. [Cbasepane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)를 재정의 합니다.|
|`CMFCOutlookBarPane::CanBeRestored`|사용자 지정 후 시스템에서 도구 모음을 원래 상태로 복원할 수 있는지 여부를 결정 합니다. [Cmfctoolbar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)를 재정의 합니다.|
|[CMFCOutlookBarPane:: ClearAll](#clearall)|Outlook 표시줄 창에서 이미지에 사용 되는 리소스를 해제 합니다.|
|[CMFCOutlookBarPane:: Create](#create)|Outlook 표시줄 창을 만듭니다.|
|`CMFCOutlookBarPane::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCOutlookBarPane::Dock`|Outlook 표시줄 창을 도킹 하기 위해 프레임 워크에서 호출 됩니다. ( `CPane::Dock`을 재정의합니다.)|
|[CMFCOutlookBarPane:: EnablePageScrollMode](#enablepagescrollmode)|Outlook 표시줄 창의 스크롤 화살표를 페이지 별로 단추나 단추를 클릭 하 여 이동할 것인지 지정 합니다.|
|[CMFCOutlookBarPane:: GetRegularColor](#getregularcolor)|Outlook 표시줄 창의 일반 (선택 되지 않은) 텍스트 색을 반환 합니다.|
|`CMFCOutlookBarPane::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCOutlookBarPane:: IsBackgroundTexture](#isbackgroundtexture)|Outlook 표시줄 창에 대해 로드 된 배경 이미지가 있는지 여부를 확인 합니다.|
|`CMFCOutlookBarPane::IsChangeState`|부동 창이 도킹 될 수 있는지 여부를 확인 합니다. ( `CPane::IsChangeState`을 재정의합니다.)|
|[CMFCOutlookBarPane:: IsDrawShadedHighlight](#isdrawshadedhighlight)|단추가 강조 표시 되 고 배경 이미지가 표시 될 때 단추 테두리가 음영 처리 되는지 여부를 결정 합니다.|
|`CMFCOutlookBarPane::OnBeforeFloat`|창에서 부동이 될 때 프레임 워크에서 호출 됩니다. ( [Cpane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)를 재정의 합니다.)|
|[CMFCOutlookBarPane:: RemoveButton](#removebutton)|지정 된 명령 ID를 가진 단추를 제거 합니다.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|도구 모음의 원래 상태를 복원합니다. [Cmfctoolbar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)를 재정의 합니다.|
|[CMFCOutlookBarPane:: SetBackColor](#setbackcolor)|배경색을 설정 합니다.|
|[CMFCOutlookBarPane:: SetBackImage](#setbackimage)|배경 이미지를 설정 합니다.|
|[CMFCOutlookBarPane:: SetDefaultState](#setdefaultstate)|Outlook 표시줄 창을 원래 단추 집합으로 다시 설정 합니다.|
|[CMFCOutlookBarPane:: SetExtraSpace](#setextraspace)|Outlook 표시줄 창에서 단추 주위에 사용 되는 안쪽 여백 픽셀의 수를 설정 합니다.|
|[CMFCOutlookBarPane:: SetTextColor](#settextcolor)|Outlook 표시줄 창에서 일반 텍스트와 강조 표시 된 텍스트의 색을 설정 합니다.|
|[CMFCOutlookBarPane:: SetTransparentColor](#settransparentcolor)|Outlook 표시줄 창에 투명 한 색을 설정 합니다.|
|`CMFCOutlookBarPane::SmartUpdate`|Outlook 표시줄을 업데이트 하기 위해 내부적으로 사용 됩니다. ( `CMFCToolBar::SmartUpdate`을 재정의합니다.)|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCOutlookBarPane:: EnableContextMenuItems](#enablecontextmenuitems)|사용자 지정 모드에서 표시 되는 바로 가기 메뉴 항목을 지정 합니다.|
|[CMFCOutlookBarPane:: RemoveAllButtons](#removeallbuttons)|Outlook 표시줄 창에서 모든 단추를 제거 합니다. [Cmfctoolbar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)를 재정의 합니다.|

## <a name="remarks"></a>설명

Outlook 표시줄을 구현 하는 방법에 대 한 자세한 내용은 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)를 참조 하세요.

Outlook 표시줄의 예는 OutlookDemo 샘플 프로젝트를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스의 여러 메서드를 사용 하는 방법을 보여 줍니다 `CMFCOutlookBarPane` . 이 예제에서는 Outlook 표시줄 창을 만들고, 페이지 스크롤 모드를 사용 하도록 설정 하 고, 도킹을 사용 하도록 설정 하 고, Outlook 표시줄의 배경색을 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [Outlook 다중 보기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxoutlookbarpane

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a> CMFCOutlookBarPane:: AddButton

Outlook 표시줄 창에 단추를 추가 합니다.

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
진행 비트맵의 리소스 식별자를 지정 합니다.

*lpszLabel*<br/>
진행 단추의 텍스트를 지정 합니다.

*iIdCommand*<br/>
진행 단추 컨트롤의 ID를 지정 합니다.

*iInsertAt*<br/>
진행 Outlook 표시줄 페이지에서 단추를 삽입할 인덱스 (0부터 시작)를 지정 합니다.

*uiLabel*<br/>
진행 문자열 리소스 ID입니다.

*szBmpFileName*<br/>
진행 로드할 디스크 이미지 파일의 이름을 지정 합니다.

*szLabel*<br/>
진행 단추의 텍스트를 지정 합니다.

*hBmp*<br/>
진행 단추 비트맵에 대 한 핸들입니다.

*hIcon*<br/>
진행 단추의 아이콘에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

단추가 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 Outlook 표시줄의 페이지에 새 단추를 삽입할 수 있습니다. 단추의 이미지는 응용 프로그램 리소스 또는 디스크 파일에서 로드할 수 있습니다.

*UiPageID* 에서 지정한 페이지 ID가-1 인 경우 단추가 첫 번째 페이지에 삽입 됩니다.

*Iinsertat에* 지정 된 인덱스가-1 이면 페이지 끝에 단추가 추가 됩니다.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a> CMFCOutlookBarPane:: CanBeAttached

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a> CMFCOutlookBarPane:: ClearAll

Outlook 표시줄 창에서 이미지에 사용 되는 리소스를 해제 합니다.

```cpp
void ClearAll();
```

### <a name="remarks"></a>설명

이 메서드는 [Cmfc도구 모음 images:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)를 직접 호출 합니다 .이는 Outlook 표시줄 창에서 사용 되는 이미지에서 호출 됩니다.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a> CMFCOutlookBarPane:: Create

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
진행 Outlook 표시줄 창 컨트롤의 부모 창을 지정 합니다. NULL이 아니어야 합니다.

*dwStyle*<br/>
진행 창 스타일입니다.  창 스타일의 목록은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*uiID*<br/>
진행 컨트롤 ID입니다. 컨트롤의 상태를 저장할 수 있도록 하려면 고유 해야 합니다.

*Dwcontrol바 스타일*<br/>
진행 Outlook 표시줄에서 Outlook 표시줄 창을 분리할 때 해당 컨트롤의 동작을 정의 하는 특수 스타일을 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

개체를 생성 하려면 `CMFCOutlookBarPane` 먼저 생성자를 호출한 다음을 호출 하 여 `Create` Outlook 표시줄 창 컨트롤을 만들고이를 개체에 연결 `CMFCOutlookBarPane` 합니다.

에 대 한 자세한 `dwControlBarStyle` 내용은 [Cbasepane:: createex](../../mfc/reference/cbasepane-class.md#createex)를 참조 하십시오.

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a> CMFCOutlookBarPane:: EnableContextMenuItems

사용자 지정 모드에서 표시 되는 바로 가기 메뉴 항목을 지정 합니다.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>매개 변수

*pButton*<br/>
진행 사용자가 클릭 한 도구 모음 단추에 대 한 포인터입니다.

*pPopup*<br/>
진행 바로 가기 메뉴에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

바로 가기 메뉴를 표시 해야 하면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크가 사용자 지정 모드에서 표시 하는 프레임 워크 표준 바로 가기 메뉴를 수정 하려면이 메서드를 재정의 합니다.

기본 구현에서는 사용자 지정 모드 ( [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))를 확인 하 고 TRUE로 설정 된 경우 **삭제** 를 제외 하 고 모든 바로 가기 메뉴 항목을 사용 하지 않도록 설정 합니다. 그런 다음 입력 매개 변수를에 전달 하기만 하면 `CMFCToolBar::EnableContextMenuItems` 됩니다.

> [!NOTE]
> *상황에 맞는 메뉴* 는 바로 가기 메뉴의 동의어입니다.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a> CMFCOutlookBarPane:: EnablePageScrollMode

Outlook 표시줄 창의 스크롤 화살표를 페이지 별로 이동 하거나 단추를 클릭 하 여 이동할 것인지 지정 합니다.

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>매개 변수

*bPageScroll*<br/>
진행 TRUE 이면 페이지 스크롤 모드를 사용 하도록 설정 합니다. FALSE 이면 페이지 스크롤 모드를 사용 하지 않도록 설정 합니다.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a> CMFCOutlookBarPane:: GetRegularColor

Outlook 표시줄 창의 일반 (선택 되지 않은) 텍스트 색을 반환 합니다.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>반환 값

RGB 색 값으로 된 현재 텍스트 색입니다.

### <a name="remarks"></a>설명

[CMFCOutlookBarPane:: SetTextColor](#settextcolor) 를 사용 하 여 Outlook 표시줄의 현재 (일반 및 선택 된) 텍스트 색을 설정 합니다. COLOR_WINDOW 인덱스를 사용 하 여 [Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor) 함수를 호출 하 여 기본 텍스트 색을 가져올 수 있습니다.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a> CMFCOutlookBarPane:: IsBackgroundTexture

Outlook 표시줄 창에 대해 로드 된 배경 이미지가 있는지 여부를 확인 합니다.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>반환 값

표시할 배경 이미지가 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CMFCOutlookBarPane:: SetBackImage](#setbackimage) 함수를 호출 하 여 배경 이미지를 추가할 수 있습니다.

배경 이미지가 없는 경우 [CMFCOutlookBarPane:: SetBackColor](#setbackcolor)를 사용 하 여 지정 된 색으로 배경을 그립니다.

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a> CMFCOutlookBarPane:: IsDrawShadedHighlight

단추가 강조 표시 되 고 배경 이미지가 표시 될 때 단추 테두리가 음영 처리 되는지 여부를 결정 합니다.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>반환 값

단추의 테두리가 회색으로 표시 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a> CMFCOutlookBarPane:: RemoveAllButtons

Outlook 표시줄 창에서 모든 단추를 제거 합니다.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a> CMFCOutlookBarPane:: RemoveButton

지정 된 명령 ID를 가진 단추를 제거 합니다.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>매개 변수

*iIdCommand*<br/>
진행 제거할 단추의 명령 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

단추가 성공적으로 제거 되었으면 TRUE이 고, 그렇지 않으면입니다. 지정 된 명령 ID가 유효 하지 않으면 FALSE입니다.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a> CMFCOutlookBarPane:: SetBackColor

Outlook 표시줄의 배경색을 설정 합니다.

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
[in] 새 배경색을 지정합니다.

### <a name="remarks"></a>설명

Outlook 표시줄의 현재 배경색을 설정 하려면이 함수를 호출 합니다. 배경색은 배경 이미지가 없는 경우에만 사용 됩니다.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a> CMFCOutlookBarPane:: SetBackImage

배경 이미지를 설정 합니다.

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>매개 변수

*uiImageID*<br/>
진행 이미지 리소스 ID를 지정 합니다.

### <a name="remarks"></a>설명

Outlook 표시줄의 배경 이미지를 설정 하려면이 메서드를 호출 합니다. 배경 이미지 목록은 포함 된 [Cmfc지 이미지 클래스](../../mfc/reference/cmfctoolbarimages-class.md) 개체에서 관리 합니다.

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a> CMFCOutlookBarPane:: SetDefaultState

Outlook 표시줄 창을 원래 단추 집합으로 다시 설정 합니다.

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>설명

이 메서드는 Outlook 표시줄 단추를 원래 집합으로 복원 합니다. 이 메서드는 `CMFCOutlookBarPane::RestoreOriginalstate` Outlook 표시줄 창의 다시 그리기를 트리거하지 않는다는 점을 제외 하 고와 비슷합니다.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a> CMFCOutlookBarPane:: SetExtraSpace

Outlook 표시줄 창에서 단추 주위에 사용 되는 안쪽 여백 픽셀의 수를 설정 합니다.

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a> CMFCOutlookBarPane:: SetTextColor

Outlook 표시줄 창에서 일반 텍스트와 강조 표시 된 텍스트의 색을 설정 합니다.

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>매개 변수

*clrRegText*<br/>
진행 선택 하지 않은 텍스트의 새 색을 지정 합니다.

*clrSelText*<br/>
진행 선택한 텍스트의 새 색을 지정 합니다.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a> CMFCOutlookBarPane:: SetTransparentColor

Outlook 표시줄 창에 투명 한 색을 설정 합니다.

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
새 투명 색을 지정 합니다.

### <a name="remarks"></a>설명

투명 이미지를 표시 하려면 투명 한 색이 필요 합니다. 이미지에서이 색의 발생은 배경색으로 그려집니다.  배경 이미지와 전경 이미지는 혼합 되어 있지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 클래스](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
