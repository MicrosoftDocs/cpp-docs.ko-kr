---
description: '자세히 알아보기: CMFCToolBarsCustomizeDialog 클래스'
title: CMFCToolBarsCustomizeDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
ms.openlocfilehash: d05e94f614510c264e5916404abeeb6dfc4bea9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143457"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 클래스

사용자가 응용 프로그램에서 도구 모음, 메뉴, 바로 가기 키, 사용자 정의 도구, 비주얼 스타일을 사용자 지정할 수 있는 모덜리스 탭 대화 상자 ( [CPropertySheet 클래스](../../mfc/reference/cpropertysheet-class.md)) 일반적으로 사용자가 **도구** 메뉴에서 **사용자 지정** 을 선택하여 이 대화 상자에 액세스합니다.

**사용자 지정** 대화 상자에는 **명령**, **도구 모음**, **도구**, **키보드**, **메뉴** 및 **옵션** 의 6 개 탭이 있습니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|`CMFCToolBarsCustomizeDialog` 개체를 생성합니다.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|**명령** 페이지의 명령 목록에 도구 모음 단추를 삽입 합니다.|
|[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu)|리소스에서 메뉴를 로드 하 고 [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) 를 호출 하 여 **명령** 페이지의 명령 목록에 해당 메뉴를 추가 합니다.|
|[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)|리소스에서 메뉴를 로드 하 고 [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) 를 호출 하 여 **명령** 페이지의 명령 목록에 해당 메뉴를 추가 합니다.|
|[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)|리소스에서 도구 모음을 로드 합니다. 그런 다음 메뉴의 각 명령에 대해 [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드를 호출 하 여 **명령 페이지의 명령 목록** 에 있는 단추를 지정 된 범주에 삽입 합니다.|
|[CMFCToolBarsCustomizeDialog:: Create](#create)|**사용자 지정** 대화 상자를 표시 합니다.|
|`CMFCToolBarsCustomizeDialog::EnableTools`|다음에 사용하도록 예약됩니다.|
|[CMFCToolBarsCustomizeDialog:: EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|**사용자 지정** 대화 상자를 사용 하 여 새 도구 모음 만들기를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCToolBarsCustomizeDialog:: FillAllCommandsList](#fillallcommandslist)|제공 된 `CListBox` 개체를 **All 명령** 범주의 명령으로 채웁니다.|
|[CMFCToolBarsCustomizeDialog:: Fill범주 Combobox](#fillcategoriescombobox)|제공 된 `CComboBox` 개체를 **사용자 지정** 대화 상자의 각 명령 범주 이름으로 채웁니다.|
|[CMFCToolBarsCustomizeDialog:: Fill범주 Listbox](#fillcategorieslistbox)|제공 된 `CListBox` 개체를 **사용자 지정** 대화 상자의 각 명령 범주 이름으로 채웁니다.|
|[CMFCToolBarsCustomizeDialog:: GetCommandName](#getcommandname)|지정 된 명령 ID와 연결 된 이름을 검색 합니다.|
|[CMFCToolBarsCustomizeDialog:: GetCountInCategory](#getcountincategory)|지정 된 텍스트 레이블이 있는 제공 된 목록의 항목 수를 검색 합니다.|
|[CMFCToolBarsCustomizeDialog:: GetFlags](#getflags)|대화 상자의 동작에 영향을 주는 플래그 집합을 검색 합니다.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCToolBarsCustomizeDialog:: Onedit Menuimage](#onedittoolbarmenuimage)|사용자가 도구 모음 단추 또는 메뉴 항목 아이콘을 사용자 지정할 수 있도록 이미지 편집기를 시작 합니다.|
|[CMFCToolBarsCustomizeDialog:: OnInitDialog](#oninitdialog)|속성 시트 초기화를 확대 하기 위해를 재정의 합니다. [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)를 재정의 합니다.|
|[CMFCToolBarsCustomizeDialog::P ostNcDestroy](#postncdestroy)|창이 소멸 된 후 프레임 워크에서 호출 됩니다. ( `CPropertySheet::PostNcDestroy`을 재정의합니다.)|
|[CMFCToolBarsCustomizeDialog:: RemoveButton](#removebutton)|지정 된 범주나 모든 범주에서 지정 된 명령 ID를 가진 단추를 제거 합니다.|
|[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)|**명령** 탭에 있는 범주 목록 상자에서 범주의 이름을 바꿉니다.|
|[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)|**명령** 탭의 명령 목록에 있는 단추를 새 도구 모음 단추 개체로 바꿉니다.|
|[CMFCToolBarsCustomizeDialog:: SetUserCategory](#setusercategory)|**명령** 탭에 표시 되는 범주 목록에 범주를 추가 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)|사용자 정의 도구 목록이 유효한 지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCToolBarsCustomizeDialog:: OnAfterChangeTool](#onafterchangetool)|사용자 정의 도구의 속성이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CMFCToolBarsCustomizeDialog:: On할당 키](#onassignkey)|지정 된 바로 가기 키를 동작에 할당할 수 있는지 여부를 결정 합니다.|
|[CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool](#onbeforechangetool)|사용자 정의 도구를 변경할 수 있는지 여부를 결정 합니다.|
|[CMFCToolBarsCustomizeDialog:: OnInitToolsPage](#oninittoolspage)|사용자가 **도구** 탭을 선택할 때 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

**사용자 지정** 대화 상자를 표시 하려면 개체를 만들고 `CMFCToolBarsCustomizeDialog` [CMFCToolBarsCustomizeDialog:: create](#create) 메서드를 호출 합니다.

사용자 **지정** 대화 상자가 활성화 되어 있는 동안 응용 프로그램은 사용자 지정 작업으로 제한 하는 특수 모드에서 작동 합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCToolBarsCustomizeDialog` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예에서는 **명령** 페이지의 명령 목록 상자에서 도구 모음 단추를 바꾸는 방법, **사용자 지정** 대화 상자를 사용 하 여 새 도구 모음 만들기 및 **사용자 지정** 대화 상자 표시를 사용 하도록 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [IE Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxToolBarsCustomizeDialog

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a> CMFCToolBarsCustomizeDialog:: AddButton

**명령** 페이지의 명령 목록에 도구 모음 단추를 삽입 합니다.

```cpp
void AddButton(
    UINT uiCategoryId,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);
```

### <a name="parameters"></a>매개 변수

*uiCategoryId*<br/>
진행 단추를 삽입할 범주 ID를 지정 합니다.

*단추만*<br/>
진행 삽입할 단추를 지정 합니다.

*iInsertBefore*<br/>
진행 단추가 삽입 되기 전에 도구 모음 단추의 인덱스 (0부터 시작)를 지정 합니다.

*lpszCategory*<br/>
진행 단추를 삽입할 범주 문자열을 지정 합니다.

### <a name="remarks"></a>설명

`AddButton`메서드는 표준 명령 id (예: ID_FILE_MRU_FILE1), 허용 되지 않는 명령 ( [Cmfctoolbar:: IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 및 더미 단추를 포함 하는 단추를 무시 합니다.

이 메서드는 `button` 단추의 런타임 클래스를 사용 하 여 (일반적으로 [CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md))와 같은 형식의 새 개체를 만듭니다. 그런 다음 [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) 을 호출 하 여 단추의 데이터 멤버를 복사 하 고 복사본을 지정 된 범주에 삽입 합니다.

새 단추를 삽입 하면 알림이 수신 됩니다 `OnAddToCustomizePage` .

`iInsertBefore`가-1 이면 단추가 범주 목록에 추가 되 고, 그렇지 않으면 지정 된 인덱스를 가진 항목 앞에 삽입 됩니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `AddButton` `CMFCToolBarsCustomizeDialog` . 이 코드 조각은 [슬라이더 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a> CMFCToolBarsCustomizeDialog:: AddMenu

리소스에서 메뉴를 로드 하 고 [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) 를 호출 하 여 **명령** 페이지의 명령 목록에 해당 메뉴를 추가 합니다.

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>매개 변수

*uiMenuResId*<br/>
진행 로드할 메뉴의 리소스 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

메뉴가 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

호출에서 `AddMenuCommands` *BPOPUP* 은 FALSE입니다. 따라서 해당 메서드는 하위 메뉴가 포함 된 메뉴 항목을 명령 목록에 추가 하지 않습니다. 이 메서드는 하위 메뉴에 있는 메뉴 항목을 명령 목록에 추가 합니다.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a> CMFCToolBarsCustomizeDialog:: AddMenuCommands

**명령** 페이지의 명령 목록에 항목을 추가 하 여 지정 된 메뉴의 모든 항목을 표시 합니다.

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>매개 변수

*pMenu*<br/>
진행 추가할 CMenu 개체에 대 한 포인터입니다.

*bPopup*<br/>
진행 팝업 메뉴 항목을 명령 목록에 삽입할지 여부를 지정 합니다.

*lpszCategory*<br/>
진행 메뉴를 삽입할 범주의 이름입니다.

*lpszMenuPath*<br/>
진행 **모든 범주** 목록에 명령이 표시 될 때 이름에 추가 되는 접두사입니다.

### <a name="remarks"></a>설명

`AddMenuCommands`메서드는 *pmenu* 의 모든 메뉴 항목을 반복 합니다. 하위 메뉴가 포함 되지 않은 각 메뉴 항목에 대해이 메서드는 [CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md) 개체를 만들고 [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드를 호출 하 여 메뉴 항목을 **명령** 페이지의 명령 목록에 도구 모음 단추로 추가 합니다. 이 프로세스에서는 구분 기호가 무시 됩니다.

*Bpopup* 이 TRUE 이면 하위 메뉴가 포함 된 각 메뉴 항목에 대해이 메서드는 [cmfc도구](../../mfc/reference/cmfctoolbarmenubutton-class.md) 메뉴 메뉴 개체를 만들어를 호출 하 여 명령 목록에 삽입 `AddButton` 합니다. 그렇지 않으면 하위 메뉴가 포함 된 메뉴 항목이 명령 목록에 표시 되지 않습니다. 두 경우 모두에서 `AddMenuCommands` 하위 메뉴가 포함 된 메뉴 항목이 발견 되 면이를 재귀적으로 호출 하 여 하위 메뉴에 대 한 포인터를 *pmenu* 매개 변수로 전달 하 고 하위 메뉴의 레이블을 *lpszMenuPath* 에 추가 합니다.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a> CMFCToolBarsCustomizeDialog:: AddToolBar

리소스에서 도구 모음을 로드 합니다. 그런 다음 메뉴의 각 명령에 대해 [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드를 호출 하 여 **명령 페이지의 명령 목록** 에 있는 단추를 지정 된 범주에 삽입 합니다.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>매개 변수

*uiCategoryId*<br/>
진행 도구 모음을 추가할 범주의 리소스 ID를 지정 합니다.

*uiToolbarResId*<br/>
진행 명령이 명령 목록에 삽입 되는 도구 모음의 리소스 ID를 지정 합니다.

*lpszCategory*<br/>
진행 도구 모음을 추가할 범주의 이름을 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `AddToolBar` `CMFCToolBarsCustomizeDialog` . 이 코드 조각은 [워드 패드 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>설명

각 명령을 나타내는 데 사용 되는 컨트롤은 [CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md) 개체입니다. 도구 모음을 추가한 후에는 [CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)를 호출 하 여 단추를 파생 형식의 컨트롤로 바꿀 수 있습니다.

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a> CMFCToolBarsCustomizeDialog:: CheckToolsValidity

사용자 도구 목록의 유효성을 확인 합니다.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>매개 변수

*lstTools*<br/>
진행 확인할 사용자 정의 도구 목록입니다.

### <a name="return-value"></a>반환 값

사용자 정의 도구 목록이 올바르면 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다. 기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 호출 하 여 [CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)에서 반환 하는 사용자 정의 도구를 나타내는 개체의 유효성을 확인 합니다.

사용자 `CheckToolsValidity` `CMFCToolBarsCustomizeDialog`  가 대화 상자를 닫기 전에 사용자 도구의 유효성을 검사 하려는 경우에서 파생 된 클래스의 메서드를 재정의 합니다. 사용자가 대화 상자의 오른쪽 위 모퉁이에 있는 **닫기** 단추를 클릭 하거나 대화 상자의 오른쪽 아래에 있는 **닫기** 단추를 클릭 하면이 메서드가 FALSE를 반환 하는 경우 대화 상자에는 닫는 대신 **도구** 탭이 표시 됩니다. 사용자가 탭을 클릭 하 여 **도구** 탭에서 다른 위치로 이동할 때이 메서드가 FALSE를 반환 하면 탐색이 수행 되지 않습니다. 유효성 검사 실패를 일으킨 문제를 사용자에 게 알리는 적절 한 메시지 상자를 표시 해야 합니다.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a> CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog

`CMFCToolBarsCustomizeDialog` 개체를 생성합니다.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>매개 변수

*pWndParentFrame*<br/>
진행 부모 프레임에 대 한 포인터입니다. 이 매개 변수는 NULL이 아니어야 합니다.

*bAutoSetFromMenus*<br/>
진행 모든 메뉴의 메뉴 명령을 **명령** 페이지의 명령 목록에 추가할지 여부를 지정 하는 부울 값입니다. 이 매개 변수가 TRUE 이면 메뉴 명령이 추가 됩니다. 그렇지 않으면 메뉴 명령이 추가 되지 않습니다.

*uiFlags*<br/>
진행 대화 상자의 동작에 영향을 주는 플래그의 조합입니다. 이 매개 변수는 다음 값 중 하나 이상이 될 수 있습니다.

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
진행 `CRuntimeClass` 추가 사용자 지정 페이지를 지정 하는 개체 목록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*PlistCustomPages* 매개 변수는 `CRuntimeClass` 추가 사용자 지정 페이지를 지정 하는 개체 목록을 참조 합니다. 생성자는 [CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) 메서드를 사용 하 여 대화 상자에 더 많은 페이지를 추가 합니다. **사용자 지정** 대화 상자에 페이지를 더 추가 하는 예제는 custompages 샘플을 참조 하세요.

*Uiflags* 매개 변수에 전달할 수 있는 값에 대 한 자세한 내용은 [CMFCToolBarsCustomizeDialog:: getflags](#getflags)를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCToolBarsCustomizeDialog` . 이 코드 조각은 [사용자 지정 페이지 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a> CMFCToolBarsCustomizeDialog:: Create

**사용자 지정** 대화 상자를 표시 합니다.

```
virtual BOOL Create();
```

### <a name="return-value"></a>반환 값

사용자 지정 속성 시트가 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`Create`클래스를 완전히 초기화 한 후에만 메서드를 호출 합니다.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a> CMFCToolBarsCustomizeDialog:: EnableUserDefinedToolbars

**사용자 지정** 대화 상자를 사용 하 여 새 도구 모음 만들기를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 사용자 정의 도구 모음을 사용 하려면 TRUE로 설정 합니다. FALSE 이면 도구 모음을 사용 하지 않습니다.

### <a name="remarks"></a>설명

*Benable* 이 TRUE 이면 **도구 모음** 페이지에 **새로 만들기**, **이름 바꾸기** 및 **삭제** 단추가 표시 됩니다.

기본적으로 또는 *Benable* 이 FALSE 이면 이러한 단추가 표시 되지 않고 사용자가 새 도구 모음을 정의할 수 없습니다.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a> CMFCToolBarsCustomizeDialog:: FillAllCommandsList

제공 된 `CListBox` 개체를 **All 명령** 범주의 명령으로 채웁니다.

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>매개 변수

*wndListOfCommands*<br/>
제한이 채울 개체에 대 한 참조 `CListBox` 입니다.

### <a name="remarks"></a>설명

**모든 명령** 범주에는 모든 범주의 명령이 포함 됩니다. [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드는 제공 된 단추와 연결 된 명령을 **모든 명령** 범주에 추가 합니다.

이 메서드는 `CListBox` **모든 명령** 범주의 명령으로 채우기 전에 제공 된 개체의 내용을 지웁니다.

`CMFCMousePropertyPage`클래스는이 메서드를 사용 하 여 두 번 클릭 이벤트 목록 상자를 채웁니다.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a> CMFCToolBarsCustomizeDialog:: Fill범주 Combobox

제공 된 `CComboBox` 개체를 **사용자 지정** 대화 상자의 각 명령 범주 이름으로 채웁니다.

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>매개 변수

*wndCategory*<br/>
제한이 채울 개체에 대 한 참조 `CComboBox` 입니다.

*bAddEmpty*<br/>
진행 명령을 포함 하지 않는 콤보 상자에 범주를 추가할지 여부를 지정 하는 부울 값입니다. 이 매개 변수가 TRUE 이면 빈 범주가 콤보 상자에 추가 됩니다. 그렇지 않으면 빈 범주가 추가 되지 않습니다.

### <a name="remarks"></a>설명

이 메서드는 개체에서 작동 한다는 점을 제외 하 고는 [CMFCToolBarsCustomizeDialog:: Fill범주 listbox](#fillcategorieslistbox) 메서드와 비슷합니다. `CComboBox`

이 메서드는 `CComboBox` 개체를 채우기 전에 개체의 콘텐츠를 지우지 않습니다. **모든 명령** 범주가 콤보 상자의 최종 항목이 되도록 보장 합니다.

[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드를 사용 하 여 새 명령 범주를 추가할 수 있습니다. [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) 메서드를 사용 하 여 기존 범주의 이름을 변경할 수 있습니다.

`CMFCToolBarsKeyboardPropertyPage`및 `CMFCKeyMapDialog` 클래스는이 메서드를 사용 하 여 키보드 매핑을 분류 합니다.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a> CMFCToolBarsCustomizeDialog:: Fill범주 Listbox

제공 된 `CListBox` 개체를 **사용자 지정** 대화 상자의 각 명령 범주 이름으로 채웁니다.

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>매개 변수

*wndCategory*<br/>
제한이 채울 개체에 대 한 참조 `CListBox` 입니다.

*bAddEmpty*<br/>
진행 명령이 없는 목록 상자에 범주를 추가할지 여부를 지정 하는 부울 값입니다. 이 매개 변수가 TRUE 이면 빈 범주가 목록 상자에 추가 됩니다. 그렇지 않으면 빈 범주가 추가 되지 않습니다.

### <a name="remarks"></a>설명

이 메서드는 개체에서 작동 한다는 점을 제외 하 고는 [CMFCToolBarsCustomizeDialog:: Fill범주 combobox](#fillcategoriescombobox) 메서드와 비슷합니다. `CListBox`

이 메서드는 `CListBox` 개체를 채우기 전에 개체의 콘텐츠를 지우지 않습니다. **모든 명령** 범주가 목록 상자의 최종 항목이 되도록 보장 합니다.

[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) 메서드를 사용 하 여 새 명령 범주를 추가할 수 있습니다. [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) 메서드를 사용 하 여 기존 범주의 이름을 변경할 수 있습니다.

`CMFCToolBarsCommandsPropertyPage`클래스는이 메서드를 사용 하 여 각 명령 범주와 연결 된 명령 목록을 표시 합니다.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a> CMFCToolBarsCustomizeDialog:: GetCommandName

지정 된 명령 ID와 연결 된 이름을 검색 합니다.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 검색할 명령의 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령 ID와 연결 된 이름 이거나, 명령이 없는 경우 NULL입니다.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a> CMFCToolBarsCustomizeDialog:: GetCountInCategory

지정 된 텍스트 레이블이 있는 제공 된 목록의 항목 수를 검색 합니다.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>매개 변수

*lpszItemName*<br/>
진행 일치 시킬 텍스트 레이블입니다.

*lstCommands*<br/>
진행 개체를 포함 하는 목록에 대 한 참조입니다 `CMFCToolBarButton` .

### <a name="return-value"></a>반환 값

제공 된 목록에서 텍스트 레이블이 *lpszItemName* 과 같은 항목 수입니다.

### <a name="remarks"></a>설명

제공 된 개체 목록의 각 요소는 형식 이어야 합니다 `CMFCToolBarButton` . 이 메서드는 *lpszItemName* 을 [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) 데이터 멤버와 비교 합니다.

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a> CMFCToolBarsCustomizeDialog:: GetFlags

대화 상자의 동작에 영향을 주는 플래그 집합을 검색 합니다.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>반환 값

대화 상자의 동작에 영향을 주는 플래그 집합입니다.

### <a name="remarks"></a>설명

이 메서드는 생성자에 전달 된 *Uiflags* 매개 변수의 값을 검색 합니다. 반환 값은 다음 값 중 하나 이상이 될 수 있습니다.

|Name|설명|
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|사용자가 메뉴의 그림자 모양을 지정할 수 있습니다.  |
|AFX_CUSTOMIZE_TEXT_LABELS|사용자가 도구 모음 단추 이미지 아래에 텍스트 레이블을 표시할지 여부를 지정할 수 있습니다.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|사용자가 메뉴 애니메이션 스타일을 지정할 수 있습니다.  |
|AFX_CUSTOMIZE_NOHELP|사용자 지정 대화 상자에서 도움말 단추를 제거 합니다.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|WS_EX_CONTEXTHELP 비주얼 스타일을 사용 하도록 설정 합니다.  |
|AFX_CUSTOMIZE_NOTOOLS|사용자 지정 대화 상자에서 **도구** 페이지를 제거 합니다. 이 플래그는 응용 프로그램에서 클래스를 사용 하는 경우 유효 합니다 `CUserToolsManager` .  |
|AFX_CUSTOMIZE_MENUAMPERS|단추 캡션에 앰퍼샌드 () 문자를 포함할 수 있습니다 **&** .  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|사용자 지정 대화 상자에서 **긴 아이콘** 옵션을 제거 합니다.  |

WS_EX_CONTEXTHELP 비주얼 스타일에 대 한 자세한 내용은 [확장 창 스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)을 참조 하세요.

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a> CMFCToolBarsCustomizeDialog:: OnAfterChangeTool

사용자 도구의 변경에 즉시 응답 합니다.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>매개 변수

*pSelTool*<br/>
[in, out] 변경 된 사용자 도구 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

사용자가 사용자 정의 도구의 속성을 변경할 때 프레임 워크에서이 메서드를 호출 합니다. 기본 구현은 아무 작업도 수행하지 않습니다. `CMFCToolBarsCustomizeDialog`사용자 도구를 변경한 후 처리를 수행 하려면에서 파생 된 클래스의이 메서드를 재정의 합니다.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a> CMFCToolBarsCustomizeDialog:: On할당 키

사용자가 정의 하는 바로 가기 키의 유효성을 검사 합니다.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>매개 변수

*pAccel*<br/>
[in, out] [가속](/windows/win32/api/winuser/ns-winuser-accel) 구조체로 표현 된 제안 된 키보드 할당 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

키를 할당할 수 있으면 TRUE이 고, 키를 할당할 수 없으면 FALSE입니다. 기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

사용자가 새 바로 가기 키를 할당 하거나 사용자가 정의 하는 바로 가기 키의 유효성을 검사할 때 추가 처리를 수행 하려면 파생 클래스에서이 메서드를 재정의 합니다. 바로 가기가 할당 되지 않도록 하려면 FALSE를 반환 합니다. 또한 메시지 상자를 표시 하거나 사용자에 게 바로 가기 키가 거부 된 이유를 알려 주어 야 합니다.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a> CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool

사용자가 변경 내용을 적용 하려고 할 때 사용자 도구를 변경할 때 사용자 지정 처리를 수행 합니다.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>매개 변수

*pSelTool*<br/>
[in, out] 바꾸려는 사용자 도구 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 사용자 정의 도구의 속성이 변경 될 때 프레임 워크에서 호출 됩니다. 기본 구현은 아무 작업도 수행하지 않습니다. `OnBeforeChangeTool` `CMFCToolBarsCustomizeDialog` 사용자 도구에 대 한 변경이 발생 하기 전에 처리를 수행 하려는 경우 (예: *pseltool* 에서 사용 하는 리소스 해제)에서 파생 된 클래스의 메서드를 재정의 합니다.

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a> CMFCToolBarsCustomizeDialog:: Onedit Menuimage

사용자가 도구 모음 단추 또는 메뉴 항목 아이콘을 사용자 지정할 수 있도록 이미지 편집기를 시작 합니다.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 부모 창에 대 한 포인터입니다.

*bitmap*<br/>
진행 편집할 비트맵 개체에 대 한 참조입니다.

*nBitsPerPixel*<br/>
진행 비트맵 색 해상도 (픽셀당 비트 수)입니다.

### <a name="return-value"></a>반환 값

변경이 커밋되면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다. 기본 구현에서는 대화 상자를 표시 하 고 사용자가 **확인** 을 클릭 하면 TRUE를 반환 하 고, 사용자가 **취소** 또는 **닫기** 단추를 클릭 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 사용자가 이미지 편집기를 실행할 때 프레임 워크에서 호출 됩니다. 기본 구현에서는 [Cmfcimageeditordialog 클래스](../../mfc/reference/cmfcimageeditordialog-class.md) 대화 상자가 표시 됩니다. `OnEditToolbarMenuImage`사용자 지정 이미지 편집기를 사용 하도록 파생 클래스에서를 재정의 합니다.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a> CMFCToolBarsCustomizeDialog:: OnInitDialog

속성 시트 초기화를 확대 하기 위해를 재정의 합니다.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>반환 값

[CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) 메서드를 호출한 결과입니다.

### <a name="remarks"></a>설명

이 메서드는 **닫기** 단추를 표시 하 고, 대화 상자가 현재 화면 크기에 맞는지 확인 하 고, **도움말** 단추를 대화 상자의 왼쪽 아래 모퉁이로 이동 하 여 기본 클래스 구현인 [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)를 확장 합니다.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a> CMFCToolBarsCustomizeDialog:: OnInitToolsPage

**도구** 페이지를 초기화 하려는 프레임 워크의 알림을 처리 합니다.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다. 이 알림을 처리 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a> CMFCToolBarsCustomizeDialog::P ostNcDestroy

창이 소멸 된 후 프레임 워크에서 호출 됩니다.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>설명

이 메서드는 `CPropertySheet::PostNcDestroy` 응용 프로그램을 이전 모드로 복원 하 여 기본 클래스 구현인를 확장 합니다.

[CMFCToolBarsCustomizeDialog:: Create](#create) 메서드는 응용 프로그램을 사용자 지정 작업으로 제한 하는 특수 모드로 전환 합니다.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a> CMFCToolBarsCustomizeDialog:: RemoveButton

지정 된 범주나 모든 범주에서 지정 된 명령 ID를 가진 단추를 제거 합니다.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>매개 변수

*uiCategoryId*<br/>
진행 단추를 제거할 범주 ID를 지정 합니다.

*uiCmdId*<br/>
진행 단추의 명령 ID를 지정 합니다.

*lpszCategory*<br/>
진행 단추를 제거할 범주의 이름을 지정 합니다.

### <a name="return-value"></a>반환 값

제거 된 단추의 인덱스 (0부터 시작) 이거나 지정 된 범주에 지정 된 명령 ID가 없는 경우-1입니다. *UiCategoryId* 가-1 인 경우 반환 값은 0입니다.

### <a name="remarks"></a>설명

모든 범주에서 단추를 제거 하려면이 메서드의 첫 번째 오버 로드를 호출 하 고 *uiCategoryId* 를-1로 설정 합니다.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a> CMFCToolBarsCustomizeDialog:: RenameCategory

**명령** 페이지의 범주 목록 상자에서 범주의 이름을 바꿉니다.

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>매개 변수

*lpszCategoryOld*<br/>
진행 변경할 범주 이름입니다.

*lpszCategoryNew*<br/>
진행 새 범주 이름입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

범주 이름은 고유 해야 합니다.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a> CMFCToolBarsCustomizeDialog:: ReplaceButton

**명령** 페이지의 명령 목록 상자에 있는 도구 모음 단추를 바꿉니다.

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 바꿀 단추의 명령을 지정 합니다.

*단추만*<br/>
진행 **`const`** 이전 단추를 대체 하는 도구 모음 단추 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog:: addmenucommands](#addmenucommands)또는 [CMFCToolBarsCustomizeDialog:: addtoolbar](#addtoolbar) **명령이 명령 페이지에** 명령을 추가 하는 경우이 명령은 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) 개체의 형식 (또는에 의해 추가 된 하위 메뉴가 포함 된 메뉴 항목에 대 한 [cmfc menubutton 클래스](../../mfc/reference/cmfctoolbarmenubutton-class.md) 개체 `AddMenuCommands` )입니다. 또한 프레임 워크는 이러한 세 가지 메서드를 호출 하 여 명령을 자동으로 추가 합니다. 대신 파생 된 형식으로 명령을 표시 하려면를 호출 하 `ReplaceButton` 고 파생 형식의 단추를 전달 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `ReplaceButton` `CMFCToolBarsCustomizeDialog` . 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a> CMFCToolBarsCustomizeDialog:: SetUserCategory

**명령** 페이지의 범주 목록에서 사용자 범주에 해당 하는 범주를 지정 합니다. [CMFCToolBarsCustomizeDialog:: Create](#create)를 호출 하기 전에이 함수를 호출 해야 합니다.

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>매개 변수

*lpszCategory*<br/>
진행 범주의 이름입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

사용자 범주 설정은 현재 프레임 워크에서 사용 되지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 클래스](../../mfc/reference/cpropertysheet-class.md)
