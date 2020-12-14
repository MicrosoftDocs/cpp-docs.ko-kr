---
description: '자세히 알아보기: CContextMenuManager 클래스'
title: CContextMenuManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: f026b493ae5f7ae90eccc416d8920d8b699e975d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227821"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 클래스

`CContextMenuManager`개체는 상황에 맞는 메뉴 라고도 하는 바로 가기 메뉴를 관리 합니다.

## <a name="syntax"></a>구문

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|`CContextMenuManager` 개체를 생성합니다.|
|`CContextMenuManager::~CContextMenuManager`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CContextMenuManager:: AddMenu](#addmenu)|새 바로 가기 메뉴를 추가 합니다.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|제공 된 리소스 ID와 연결 된 메뉴에 대 한 핸들을 반환 합니다.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|제공 된 메뉴 이름과 일치 하는 메뉴에 대 한 핸들을 반환 합니다.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|메뉴 이름 목록을 반환 합니다.|
|[CContextMenuManager:: LoadState](#loadstate)|Windows 레지스트리에 저장 된 바로 가기 메뉴를 로드 합니다.|
|[CContextMenuManager:: ResetState](#resetstate)|상황에 맞는 메뉴 관리자에서 바로 가기 메뉴를 지웁니다.|
|[CContextMenuManager:: SaveState](#savestate)|Windows 레지스트리에 바로 가기 메뉴를 저장 합니다.|
|[CContextMenuManager:: SetDontCloseActiveMenu](#setdontcloseactivemenu)|가 `CContextMenuManager` 새 바로 가기 메뉴를 표시 하는 경우 활성 바로 가기 메뉴를 닫을 것인지를 제어 합니다.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|지정 된 바로 가기 메뉴를 표시 합니다.|
|[CContextMenuManager:: TrackPopupMenu](#trackpopupmenu)|지정 된 바로 가기 메뉴를 표시 합니다. 선택한 메뉴 명령의 인덱스를 반환 합니다.|

## <a name="remarks"></a>설명

`CContextMenuManager` 바로 가기 메뉴를 관리 하 고 일관 된 모양을 사용 하도록 합니다.

개체를 수동으로 만들지 마십시오 `CContextMenuManager` . 응용 프로그램의 프레임 워크에서 개체를 만듭니다 `CContextMenuManager` . 그러나 응용 프로그램이 초기화 될 때 [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 를 호출 해야 합니다. 컨텍스트 관리자를 초기화 한 후에는 [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) 메서드를 사용 하 여 응용 프로그램에 대 한 컨텍스트 관리자에 대 한 포인터를 가져옵니다.

을 호출 하 여 런타임에 바로 가기 메뉴를 만들 수 있습니다 `AddMenu` . 사용자 입력을 먼저 받지 않고 메뉴를 표시 하려면를 호출 `ShowPopupMenu` 합니다. `TrackPopupMenu` 는 메뉴를 만들고 사용자 입력을 대기 하려는 경우에 사용 됩니다. `TrackPopupMenu` 선택한 명령의 인덱스를 반환 하거나, 사용자가 아무것도 선택 하지 않고 종료 한 경우 0을 반환 합니다.

는 `CContextMenuManager` Windows 레지스트리에 상태를 저장 하 고 로드할 수도 있습니다.

## <a name="example"></a>예제

다음 예제에서는 개체에 메뉴를 추가 하는 방법과 `CContextMenuManager` `CContextMenuManager` 개체가 새 팝업 메뉴를 표시 하는 경우 활성 팝업 메뉴를 닫지 않는 방법을 보여 줍니다. 이 코드 조각은 [사용자 지정 페이지 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxcontextmenumanager

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a> CContextMenuManager:: AddMenu

[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)에 새 바로 가기 메뉴를 추가 합니다.

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>매개 변수

*uiMenuNameResId*<br/>
진행 새 메뉴의 이름을 포함 하는 문자열에 대 한 리소스 ID입니다.

*uiMenuResId*<br/>
진행 메뉴 리소스 ID입니다.

*lpszName*<br/>
진행 새 메뉴의 이름을 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 메서드가 실패 하는 경우 0입니다.

### <a name="remarks"></a>설명

*UiMenuResId* 이 잘못 되었거나 이름이 같은 다른 메뉴가에 이미 있는 경우이 메서드는 실패 합니다 `CContextMenuManager` .

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a> CContextMenuManager::CContextMenuManager

[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) 개체를 생성 합니다.

```
CContextMenuManager();
```

### <a name="remarks"></a>설명

대부분의 경우를 수동으로 만들지 마십시오 `CContextMenuManager` . 응용 프로그램의 프레임 워크에서 개체를 만듭니다 `CContextMenuManager` . 응용 프로그램을 초기화 하는 동안 [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 를 호출 해야 합니다. 컨텍스트 관리자에 대 한 포인터를 가져오려면 [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)를 호출 합니다.

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a> CContextMenuManager::GetMenuById

지정 된 리소스 ID와 연결 된 메뉴에 대 한 핸들을 반환 합니다.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>매개 변수

*nMenuResId*<br/>
진행 메뉴의 리소스 ID입니다.

### <a name="return-value"></a>반환 값

연결 된 메뉴에 대 한 핸들 또는 `NULL` 메뉴를 찾을 수 없는 경우입니다.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a> CContextMenuManager::GetMenuByName

특정 메뉴에 대 한 핸들을 반환 합니다.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 검색할 메뉴의 이름을 포함 하는 문자열입니다.

*puiOrigResID*<br/>
제한이 UINT에 대 한 포인터입니다. 이 매개 변수에는 지정 된 메뉴의 리소스 ID (있는 경우)가 포함 됩니다.

### <a name="return-value"></a>반환 값

*LpszName* 으로 지정 된 이름과 일치 하는 메뉴 핸들입니다. *LpszName* 라는 메뉴가 없으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드가 *lpszName* 일치 하는 메뉴를 찾은 경우는 `GetMenuByName` *puiOrigResID* 매개 변수에 메뉴 리소스 ID를 저장 합니다.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a> CContextMenuManager::GetMenuNames

[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)에 추가 된 메뉴 이름 목록을 반환 합니다.

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>매개 변수

*listOfNames*<br/>
제한이 [CStringList](../../mfc/reference/cstringlist-class.md) 매개 변수에 대 한 참조입니다. 이 메서드는 메뉴 이름 목록을이 매개 변수에 씁니다.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a> CContextMenuManager:: LoadState

Windows 레지스트리에서 [CContextMenuManager 클래스](../../mfc/reference/ccontextmenumanager-class.md) 와 관련 된 정보를 로드 합니다.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 레지스트리 키의 상대 경로를 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*LpszProfileName* 매개 변수는 레지스트리 항목의 절대 경로가 아닙니다. 응용 프로그램에 대 한 기본 레지스트리 키의 끝에 추가 되는 상대 경로입니다. 기본 레지스트리 키를 가져오거나 설정 하려면 [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) 및 [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) 메서드를 각각 사용 합니다.

[CContextMenuManager:: SaveState](#savestate) 메서드를 사용 하 여 바로 가기 메뉴를 레지스트리에 저장 합니다.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a> CContextMenuManager:: ResetState

[CContextMenuManager 클래스](../../mfc/reference/ccontextmenumanager-class.md)와 연결 된 바로 가기 메뉴에서 모든 항목을 지웁니다.

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 오류가 발생 하면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 팝업 메뉴를 지우고에서 제거 합니다 `CContextMenuManager` .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a> CContextMenuManager:: SaveState

[CContextMenuManager 클래스](../../mfc/reference/ccontextmenumanager-class.md) 와 관련 된 정보를 Windows 레지스트리에 저장 합니다.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 레지스트리 키의 상대 경로를 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*LpszProfileName* 매개 변수는 레지스트리 항목의 절대 경로가 아닙니다. 응용 프로그램에 대 한 기본 레지스트리 키의 끝에 추가 되는 상대 경로입니다. 기본 레지스트리 키를 가져오거나 설정 하려면 [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) 및 [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) 메서드를 각각 사용 합니다.

[CContextMenuManager:: LoadState](#loadstate) 메서드를 사용 하 여 레지스트리에서 바로 가기 메뉴를 로드 합니다.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a> CContextMenuManager:: SetDontCloseActiveMenu

[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) 가 새 팝업 메뉴를 표시할 때 활성 팝업 메뉴를 닫도록 할지 여부를 제어 합니다.

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSet*<br/>
진행 활성 팝업 메뉴를 닫을지 여부를 제어 하는 부울 매개 변수입니다. TRUE 값은 활성 팝업 메뉴가 닫혀 있지 않음을 나타냅니다. FALSE 이면 활성 팝업 메뉴가 닫혀 있음을 나타냅니다.

### <a name="remarks"></a>설명

기본적으로는 `CContextMenuManager` 활성 팝업 메뉴를 닫습니다.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a> CContextMenuManager::ShowPopupMenu

지정 된 바로 가기 메뉴를 표시 합니다.

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>매개 변수

*uiMenuResId*<br/>
진행 이 메서드에 표시 되는 메뉴의 리소스 ID입니다.

*x*<br/>
진행 클라이언트 좌표에서 바로 가기 메뉴의 가로 오프셋입니다.

*y*<br/>
진행 클라이언트 좌표에서 바로 가기 메뉴의 세로 오프셋입니다.

*pWndOwner*<br/>
진행 바로 가기 메뉴의 부모 창에 대 한 포인터입니다.

*bOwnMessage*<br/>
진행 메시지를 라우팅하는 방법을 나타내는 부울 매개 변수입니다. *Bownmessage* 가 FALSE 이면 표준 MFC 라우팅이 사용 됩니다. 그렇지 않으면 *메시지를 수신 합니다* .

*hmenuPopup*<br/>
진행 이 메서드에 표시 되는 메뉴의 핸들입니다.

*bAutoDestroy*<br/>
진행 메뉴가 자동으로 제거 되는지 여부를 나타내는 부울 매개 변수입니다.

*bRightAlign*<br/>
진행 메뉴 항목이 정렬 되는 방법을 나타내는 부울 매개 변수입니다. *BRightAlign* 가 TRUE 이면 오른쪽에서 왼쪽 읽기 순서로 메뉴가 오른쪽에 맞춰집니다.

### <a name="return-value"></a>반환 값

메서드가 메뉴를 성공적으로 표시 하는 경우 첫 번째 메서드 오버 로드는 0이 아닌 값을 반환 합니다. 그렇지 않으면 0입니다. 두 번째 메서드 오버 로드는 바로 가기 메뉴가 올바르게 표시 되는 경우 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) 에 대 한 포인터를 반환 합니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 [CContextMenuManager:: TrackPopupMenu](#trackpopupmenu) 메서드와 비슷하며 두 메서드는 모두 바로 가기 메뉴를 표시 합니다. 그러나는 `TrackPopupMenu` 선택한 메뉴 명령의 인덱스를 반환 합니다.

*Bautodestroy* 매개 변수가 FALSE 인 경우 상속 된 메서드를 수동으로 호출 `DestroyMenu` 하 여 메모리 리소스를 해제 해야 합니다. 의 기본 구현에서는 `ShowPopupMenu` 매개 변수 *Bautodestroy* 를 사용 하지 않습니다. 나중에 사용 하거나 클래스에서 파생 된 사용자 지정 클래스에 대해 제공 됩니다 `CContextMenuManager` .

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a> CContextMenuManager:: TrackPopupMenu

지정 된 바로 가기 메뉴를 표시 하 고 선택한 바로 가기 메뉴 명령의 인덱스를 반환 합니다.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>매개 변수

*hmenuPopup*<br/>
진행 이 메서드가 표시 하는 바로 가기 메뉴의 핸들입니다.

*x*<br/>
진행 클라이언트 좌표에서 바로 가기 메뉴의 가로 오프셋입니다.

*y*<br/>
진행 클라이언트 좌표에서 바로 가기 메뉴의 세로 오프셋입니다.

*pWndOwner*<br/>
진행 바로 가기 메뉴의 부모 창에 대 한 포인터입니다.

*bRightAlign*<br/>
진행 메뉴 항목이 정렬 되는 방법을 나타내는 부울 매개 변수입니다. *BRightAlign* 가 TRUE 이면 오른쪽에서 왼쪽 읽기 순서로 메뉴가 오른쪽에 맞춰집니다. *BRightAlign* 가 FALSE 이면 왼쪽에서 오른쪽 읽기 순서로 메뉴가 왼쪽 맞춤 됩니다.

### <a name="return-value"></a>반환 값

사용자가 선택 하는 명령의 메뉴 명령 ID입니다. 사용자가 메뉴 명령을 선택 하지 않고 바로 가기 메뉴를 닫으면 0이 됩니다.

### <a name="remarks"></a>설명

이 메서드는 바로 가기 메뉴를 표시 하는 모달 호출로 작동 합니다. 사용자가 바로 가기 메뉴를 닫거나 명령을 선택할 때까지 응용 프로그램은 코드에서 다음 줄로 계속 이동 하지 않습니다. 바로 가기 메뉴를 표시 하는 데 사용할 수 있는 대체 방법은 [CContextMenuManager:: ShowPopupMenu](#showpopupmenu)입니다. 해당 메서드는 모달 호출이 아니므로 선택한 명령의 ID를 반환 하지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)
