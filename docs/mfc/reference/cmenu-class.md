---
description: '자세히 알아보기: CMenu 클래스'
title: CMenu 클래스
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: e1f0caea839e0660db10d055adf2af5fc7deb353
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341583"
---
# <a name="cmenu-class"></a>CMenu 클래스

Windows `HMENU`의 캡슐화입니다.

## <a name="syntax"></a>구문

```
class CMenu : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMenu:: CMenu](#cmenu)|`CMenu` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|이 메뉴의 끝에 새 항목을 추가 합니다.|
|[CMenu:: Attach](#attach)|Windows 메뉴 핸들을 개체에 연결 `CMenu` 합니다.|
|[CMenu:: CheckMenuItem](#checkmenuitem)|팝업 메뉴에서 옆에 확인 표시를 배치 하거나 메뉴 항목에서 확인 표시를 제거 합니다.|
|[CMenu:: CheckMenuRadioItem](#checkmenuradioitem)|메뉴 항목 옆에 라디오 단추를 배치 하 고 그룹에 있는 다른 모든 메뉴 항목에서 라디오 단추를 제거 합니다.|
|[CMenu:: CreateMenu](#createmenu)|빈 메뉴를 만들고 개체에 연결 `CMenu` 합니다.|
|[CMenu:: CreatePopupMenu](#createpopupmenu)|빈 팝업 메뉴를 만들고 개체에 연결 `CMenu` 합니다.|
|[CMenu::D eleteMenu](#deletemenu)|메뉴에서 지정 된 항목을 삭제 합니다. 메뉴 항목에 연결 된 팝업 메뉴가 있으면에서 팝업 메뉴에 대 한 핸들을 제거 하 고 사용 하는 메모리를 해제 합니다.|
|[CMenu::D eleteTempMap](#deletetempmap)|`CMenu`멤버 함수에서 만든 임시 개체를 모두 삭제 `FromHandle` 합니다.|
|[CMenu::D estroyMenu](#destroymenu)|개체에 연결 된 메뉴를 소멸 `CMenu` 하 고 메뉴가 차지한 모든 메모리를 해제 합니다.|
|[CMenu::D etach](#detach)|개체에서 Windows 메뉴 핸들을 분리 `CMenu` 하 고 핸들을 반환 합니다.|
|[CMenu::D rawItem](#drawitem)|소유자가 그린 메뉴의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CMenu:: EnableMenuItem](#enablemenuitem)|메뉴 항목을 사용 하거나 사용 하지 않도록 설정 하거나 희미하게 (회색) 합니다.|
|[CMenu:: FromHandle](#fromhandle)|`CMenu`Windows 메뉴 핸들이 지정 된 개체에 대 한 포인터를 반환 합니다.|
|[CMenu:: GetDefaultItem](#getdefaultitem)|지정 된 메뉴의 기본 메뉴 항목을 결정 합니다.|
|[CMenu:: GetMenuContextHelpId](#getmenucontexthelpid)|메뉴와 연결 된 도움말 컨텍스트 ID를 검색 합니다.|
|[CMenu:: GetMenuInfo](#getmenuinfo)|특정 메뉴에 대 한 정보를 검색 합니다.|
|[CMenu:: GetMenuItemCount](#getmenuitemcount)|팝업 또는 최상위 메뉴의 항목 수를 결정 합니다.|
|[CMenu:: GetMenuItemID](#getmenuitemid)|지정 된 위치에 있는 메뉴 항목의 메뉴 항목 식별자를 가져옵니다.|
|[CMenu:: GetMenuItemInfo](#getmenuiteminfo)|메뉴 항목에 대 한 정보를 검색 합니다.|
|[CMenu:: GetMenuState](#getmenustate)|지정 된 메뉴 항목의 상태 또는 팝업 메뉴의 항목 수를 반환 합니다.|
|[CMenu:: GetMenuString](#getmenustring)|지정 된 메뉴 항목의 레이블을 검색 합니다.|
|[CMenu:: GetSafeHmenu](#getsafehmenu)|`m_hMenu`이 개체로 래핑된를 반환 합니다 `CMenu` .|
|[CMenu:: GetSubMenu 메뉴](#getsubmenu)|팝업 메뉴에 대 한 포인터를 검색 합니다.|
|[CMenu::InsertMenu](#insertmenu)|지정 된 위치에 새 메뉴 항목을 삽입 하 고 다른 항목을 메뉴 아래로 이동 합니다.|
|[CMenu:: InsertMenuItem](#insertmenuitem)|메뉴의 지정 된 위치에 새 메뉴 항목을 삽입 합니다.|
|[CMenu:: LoadMenu](#loadmenu)|실행 파일에서 메뉴 리소스를 로드 하 여 개체에 연결 `CMenu` 합니다.|
|[CMenu:: LoadMenuIndirect](#loadmenuindirect)|메모리의 메뉴 템플릿에서 메뉴를 로드 하 여 개체에 연결 `CMenu` 합니다.|
|[CMenu:: MeasureItem](#measureitem)|소유자가 그린 메뉴가 만들어질 때 메뉴 크기를 결정 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMenu::ModifyMenu](#modifymenu)|지정 된 위치에 있는 기존 메뉴 항목을 변경 합니다.|
|[CMenu:: RemoveMenu](#removemenu)|지정 된 메뉴에서 연결 된 팝업 메뉴를 사용 하 여 메뉴 항목을 삭제 합니다.|
|[CMenu:: SetDefaultItem](#setdefaultitem)|지정 된 메뉴에 대 한 기본 메뉴 항목을 설정 합니다.|
|[CMenu:: SetMenuContextHelpId](#setmenucontexthelpid)|메뉴와 연결할 도움말 컨텍스트 ID를 설정 합니다.|
|[CMenu:: SetMenuInfo](#setmenuinfo)|특정 메뉴에 대 한 정보를 설정 합니다.|
|[CMenu:: SetMenuItemBitmaps](#setmenuitembitmaps)|지정 된 확인 표시 비트맵과 메뉴 항목을 연결 합니다.|
|[CMenu:: SetMenuItemInfo](#setmenuiteminfo)|메뉴 항목에 대 한 정보를 변경 합니다.|
|[CMenu:: TrackPopupMenu](#trackpopupmenu)|지정 된 위치에 부동 팝업 메뉴를 표시 하 고 팝업 메뉴에서 항목 선택을 추적 합니다.|
|[CMenu:: TrackPopupMenuEx](#trackpopupmenuex)|지정 된 위치에 부동 팝업 메뉴를 표시 하 고 팝업 메뉴에서 항목 선택을 추적 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMenu:: operator HMENU](#operator_hmenu)|메뉴 개체의 핸들을 검색 합니다.|
|[CMenu:: operator! =](#operator_neq)|두 메뉴 개체가 같지 않은 지 여부를 확인 합니다.|
|[CMenu:: operator = =](#operator_eq_eq)|두 메뉴 개체가 같은지 여부를 확인 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMenu:: m_hMenu](#m_hmenu)|개체에 연결 된 Windows 메뉴에 대 한 핸들을 지정 합니다 `CMenu` .|

## <a name="remarks"></a>설명

메뉴를 만들고, 추적 하 고, 업데이트 하 고, 삭제 하기 위한 멤버 함수를 제공 합니다.

`CMenu`스택 프레임에서 로컬으로 개체를 만든 다음 `CMenu` 의 멤버 함수를 호출 하 여 필요에 따라 새 메뉴를 조작 합니다. 그런 다음 [CWnd:: SetMenu](../../mfc/reference/cwnd-class.md#setmenu) 를 호출 하 여 메뉴를 창으로 설정 하 고 바로 다음에 `CMenu` 개체의 [Detach](#detach) 멤버 함수를 호출 합니다. `CWnd::SetMenu`멤버 함수는 창의 메뉴를 새 메뉴로 설정 하 고, 메뉴 변경 내용을 반영 하기 위해 창이 다시 그려져, 메뉴의 소유권을 창으로 전달 합니다. 호출을 통해 `Detach` 개체에서 HMENU를 분리 `CMenu` 하므로 지역 `CMenu` 변수가 범위를 벗어나는 경우 `CMenu` 개체 소멸자는 더 이상 소유 하지 않는 메뉴를 제거 하려고 시도 하지 않습니다. 창이 소멸 되 면 메뉴 자체가 자동으로 소멸 됩니다.

[Loadmenuindirect](#loadmenuindirect) 멤버 함수를 사용 하 여 메모리의 템플릿에서 메뉴를 만들 수 있지만 [loadmenu](#loadmenu) 에 대 한 호출을 통해 리소스에서 만든 메뉴는 더 쉽게 유지 관리할 수 있으며 메뉴 리소스 자체는 메뉴 편집기를 사용 하 여 만들고 수정할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a> CMenu:: AppendMenu

메뉴의 끝에 새 항목을 추가 합니다.

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>매개 변수

*nFlags*<br/>
메뉴에 추가 될 때 새 메뉴 항목의 상태에 대 한 정보를 지정 합니다. 설명 섹션에 나열 된 하나 이상의 값으로 구성 됩니다.

*nIDNewItem*<br/>
새 메뉴 항목의 명령 ID를 지정 하거나 *n 플래그가* MF_POPUP로 설정 된 경우 팝업 메뉴의 메뉴 핸들 ()을 지정 합니다 `HMENU` . *Nflags* 가 MF_SEPARATOR로 설정 된 경우 *nIDNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).

*lpszNewItem*<br/>
새 메뉴 항목의 내용을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방식으로 *lpszNewItem* 을 해석 하는 데 사용 됩니다.

|nFlags|LpszNewItem 해석|
|------------|-----------------------------------|
|MF_OWNERDRAW|응용 프로그램이 메뉴 항목과 연결 된 추가 데이터를 유지 관리 하는 데 사용할 수 있는 응용 프로그램에서 제공 하는 32 비트 값을 포함 합니다. 이 32 비트 값은 WM_MEASUREITEM 및 WM_DRAWITEM 메시지를 처리할 때 응용 프로그램에서 사용할 수 있습니다. 값은 `itemData` 해당 메시지와 함께 제공 된 구조체의 멤버에 저장 됩니다.|
|MF_STRING|Null로 끝나는 문자열에 대 한 포인터를 포함 합니다. 이는 기본 해석입니다.|
|MF_SEPARATOR|*LpszNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).|

*.Pbmp*<br/>
`CBitmap`메뉴 항목으로 사용 되는 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 *Nflags* 에서 값을 설정 하 여 메뉴 항목의 상태를 지정할 수 있습니다. *NIDNewItem* 가 팝업 메뉴를 지정 하는 경우이 메뉴는 추가 된 메뉴의 일부가 됩니다. 해당 메뉴가 제거 되 면 추가 된 메뉴도 제거 됩니다. 충돌을 방지 하려면 추가 된 메뉴를 개체에서 분리 해야 합니다 `CMenu` . MF_STRING 및 MF_OWNERDRAW은의 비트맵 버전에 대해 유효 하지 않습니다 `AppendMenu` .

다음 목록에서는 *nflags* 에 설정 될 수 있는 플래그에 대해 설명 합니다.

- MF_CHECKED은 MF_UNCHECKED를 사용 하 여 항목 옆에 기본 확인 표시를 설정 합니다. 응용 프로그램에서 확인 표시 비트맵을 제공 하면 ( [SetMenuItemBitmaps](#setmenuitembitmaps) 멤버 함수 참조) "확인 표시 설정" 비트맵이 표시 됩니다.

- MF_UNCHECKED는 항목 옆에 있는 확인 표시를 제거 하는 MF_CHECKED으로 전환 됩니다. 응용 프로그램에서 확인 표시 비트맵을 제공 하면 ( `SetMenuItemBitmaps` 멤버 함수 참조) "확인 표시 해제" 비트맵이 표시 됩니다.

- 메뉴 항목을 사용 하지 않도록 설정 하 여 메뉴 항목을 선택할 수는 없지만 dim을 사용 하지는 MF_DISABLED.

- MF_ENABLED 메뉴 항목을 선택 하 여 흐리게 표시 된 상태에서 해당 항목을 복원할 수 있습니다.

- 메뉴 항목을 선택할 수 없도록 메뉴 항목을 사용 하지 않도록 MF_GRAYED 합니다.

- MF_MENUBARBREAK 정적 메뉴의 새 줄 이나 팝업 메뉴의 새 열에 항목을 배치 합니다. 새 팝업 메뉴 열이 이전 열과 수직 분할 선으로 구분 됩니다.

- MF_MENUBREAK 정적 메뉴의 새 줄 이나 팝업 메뉴의 새 열에 항목을 배치 합니다. 열 사이에 분할 선이 배치 되지 않습니다.

- MF_OWNERDRAW 항목이 소유자 그리기 항목 임을 지정 합니다. 메뉴가 처음으로 표시 되 면 메뉴를 소유 하는 창에 WM_MEASUREITEM 메시지가 수신 되어 메뉴 항목의 높이와 너비를 검색 합니다. WM_DRAWITEM 메시지는 소유자가 메뉴 항목의 시각적 모양을 업데이트 해야 할 때마다 전송 되는 메시지입니다. 최상위 메뉴 항목에는이 옵션이 유효 하지 않습니다.

- MF_POPUP 메뉴 항목에 연결 된 팝업 메뉴가 있음을 지정 합니다. ID 매개 변수는 항목과 연결 될 팝업 메뉴에 대 한 핸들을 지정 합니다. 이는 팝업 메뉴 항목에 최상위 팝업 메뉴 또는 계층적 팝업 메뉴를 추가 하는 데 사용 됩니다.

- MF_SEPARATOR 가로 분할 선을 그립니다. 는 팝업 메뉴 에서만 사용할 수 있습니다. 이 줄은 흐리게 표시 하거나 사용 하지 않도록 설정 하거나 강조 표시할 수 없습니다. 다른 매개 변수는 무시 됩니다.

- MF_STRING는 메뉴 항목이 문자열 임을 지정 합니다.

다음 그룹은 함께 사용할 수 없는 플래그를 나열 합니다.

- MF_DISABLED, MF_ENABLED 및 MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR 및 비트맵 버전

- MF_MENUBARBREAK 및 MF_MENUBREAK

- MF_CHECKED 및 MF_UNCHECKED

창에 있는 메뉴가 변경 될 때마다 (창이 표시 되는지 여부에 관계 없이) 응용 프로그램은 [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)를 호출 해야 합니다.

### <a name="example"></a>예제

  [CMenu:: CreateMenu](#createmenu)의 예제를 참조 하세요.

## <a name="cmenuattach"></a><a name="attach"></a> CMenu:: Attach

기존 Windows 메뉴를 개체에 연결 `CMenu` 합니다.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>매개 변수

*hMenu*<br/>
Windows 메뉴에 대 한 핸들을 지정 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴가 개체에 이미 연결 되어 있는 경우에는이 함수를 호출 하면 안 됩니다 `CMenu` . 메뉴 핸들은 데이터 멤버에 저장 됩니다 `m_hMenu` .

조작 하려는 메뉴가 이미 창과 연결 되어 있으면 [CWnd:: getmenu](../../mfc/reference/cwnd-class.md#getmenu) 함수를 사용 하 여 메뉴에 대 한 핸들을 가져올 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a> CMenu:: CheckMenuItem

팝업 메뉴의 메뉴 항목에서 확인 표시를 추가 하거나 제거 합니다.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>매개 변수

*nIDCheckItem*<br/>
*N* 에 의해 결정 된 대로 확인할 메뉴 항목을 지정 합니다.

*nCheck*<br/>
메뉴 항목을 확인 하는 방법과 메뉴에서 항목의 위치를 확인 하는 방법을 지정 합니다. *N* 매개 변수는 MF_CHECKED 또는 MF_UNCHECKED MF_BYPOSITION 또는 MF_BYCOMMAND 플래그의 조합일 수 있습니다. 비트 OR 연산자를 사용 하 여 이러한 플래그를 결합할 수 있습니다. 이러한 작업에는 다음과 같은 의미가 있습니다.

- MF_BYCOMMAND 매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. 이것이 기본값입니다.

- MF_BYPOSITION 매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.

- MF_CHECKED은 MF_UNCHECKED를 사용 하 여 항목 옆에 기본 확인 표시를 설정 합니다.

- MF_UNCHECKED는 항목 옆에 있는 확인 표시를 제거 하는 MF_CHECKED으로 전환 됩니다.

### <a name="return-value"></a>반환 값

항목의 이전 상태: MF_CHECKED 또는 MF_UNCHECKED 또는 메뉴 항목이 존재 하지 않는 경우 0xFFFFFFFF입니다.

### <a name="remarks"></a>설명

*NIDCheckItem* 매개 변수는 수정할 항목을 지정 합니다.

*NIDCheckItem* 매개 변수는 메뉴 항목 뿐만 아니라 팝업 메뉴 항목도 식별할 수 있습니다. 팝업 메뉴 항목을 확인 하는 데 필요한 특별 한 단계는 없습니다. 최상위 메뉴 항목을 확인할 수 없습니다. 팝업 메뉴 항목에는 연결 된 메뉴-항목 식별자가 없으므로 해당 항목을 위치에 따라 확인 해야 합니다.

### <a name="example"></a>예제

  [CMenu:: GetMenuState](#getmenustate)의 예제를 참조 하세요.

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a> CMenu:: CheckMenuRadioItem

지정 된 메뉴 항목을 확인 하 고 라디오 항목으로 만듭니다.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*nIDFirst*<br/>
라디오 단추 그룹의 첫 번째 메뉴 항목 ( *Nflags* 의 값에 따라 ID 또는 오프셋)을 지정 합니다.

*nIDLast*<br/>
라디오 단추 그룹의 마지막 메뉴 항목 ( *Nflags* 의 값에 따라 ID 또는 오프셋)을 지정 합니다.

*nIDItem*<br/>
라디오 단추를 사용 하 여 확인할 그룹의 항목을 ID 또는 오프셋 ( *Nflags* 의 값에 따라)으로 지정 합니다.

*nFlags*<br/>
*NIDFirst*, *nIDLast* 및 *nIDItem* 의 해석을 다음과 같은 방식으로 지정 합니다.

|nFlags|해석|
|------------|--------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 0

### <a name="remarks"></a>설명

동시에이 함수는 연결 된 그룹의 다른 모든 메뉴 항목을 선택한 다음 해당 항목에 대 한 라디오 항목 형식 플래그를 지웁니다. 확인 표시 비트맵이 아닌 라디오 단추 (또는 글머리 기호)를 사용 하 여 선택한 항목을 표시 합니다.

### <a name="example"></a>예제

  [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)의 예제를 참조 하세요.

## <a name="cmenucmenu"></a><a name="cmenu"></a> CMenu:: CMenu

빈 메뉴를 만들고 개체에 연결 `CMenu` 합니다.

```
CMenu();
```

### <a name="remarks"></a>설명

메뉴는의 create 또는 load 멤버 함수 중 하나를 호출할 때까지 생성 되지 않습니다. `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [연결](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a> CMenu:: CreateMenu

메뉴를 만들고 개체에 연결 `CMenu` 합니다.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>반환 값

메뉴가 성공적으로 만들어졌으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

처음에는 메뉴가 비어 있습니다. `AppendMenu`또는 멤버 함수를 사용 하 여 메뉴 항목을 추가할 수 있습니다 `InsertMenu` .

창에 메뉴를 할당 하면 창이 소멸 될 때 자동으로 소멸 됩니다.

응용 프로그램은 종료 하기 전에 메뉴가 창에 할당 되지 않은 경우 메뉴와 연결 된 시스템 리소스를 해제 해야 합니다. 응용 프로그램은 [DestroyMenu](#destroymenu) 멤버 함수를 호출 하 여 메뉴를 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a> CMenu:: CreatePopupMenu

팝업 메뉴를 만들고 개체에 연결 `CMenu` 합니다.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>반환 값

팝업 메뉴가 성공적으로 만들어진 경우에는 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

처음에는 메뉴가 비어 있습니다. `AppendMenu`또는 멤버 함수를 사용 하 여 메뉴 항목을 추가할 수 있습니다 `InsertMenu` . 응용 프로그램은 팝업 메뉴를 기존 메뉴 또는 팝업 메뉴에 추가할 수 있습니다. `TrackPopupMenu`멤버 함수는이 메뉴를 부동 팝업 메뉴로 표시 하 고 팝업 메뉴에서 선택 항목을 추적 하는 데 사용할 수 있습니다.

창에 메뉴를 할당 하면 창이 소멸 될 때 자동으로 소멸 됩니다. 메뉴가 기존 메뉴에 추가 되 면 해당 메뉴가 제거 되 면 자동으로 제거 됩니다.

메뉴를 창에 할당 하지 않은 경우 종료 하기 전에 응용 프로그램에서 팝업 메뉴와 연결 된 시스템 리소스를 해제 해야 합니다. 응용 프로그램은 [DestroyMenu](#destroymenu) 멤버 함수를 호출 하 여 메뉴를 해제 합니다.

### <a name="example"></a>예제

  [CMenu:: CreateMenu](#createmenu)의 예제를 참조 하세요.

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a> CMenu::D eleteMenu

메뉴에서 항목을 삭제 합니다.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*위치*<br/>
*Nflags* 에 의해 결정 된 대로 삭제할 메뉴 항목을 지정 합니다.

*nFlags*<br/>
는 다음과 같은 방식으로 *Nposition* 을 해석 하는 데 사용 됩니다.

|nFlags|NPosition의 해석|
|------------|---------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴 항목에 연결 된 팝업 메뉴가 있으면에서 `DeleteMenu` 팝업 메뉴에 대 한 핸들을 제거 하 고 팝업 메뉴에서 사용 되는 메모리를 해제 합니다.

창에 있는 메뉴가 변경 될 때마다 (창이 표시 되는지 여부에 관계 없이) 응용 프로그램은 [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)를 호출 해야 합니다.

### <a name="example"></a>예제

  [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu)의 예제를 참조 하세요.

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a> CMenu::D eleteTempMap

유휴 시간 처리기에서 자동으로 호출 `CWinApp` 되며 `CMenu` [fromhandle](#fromhandle) 멤버 함수에 의해 생성 된 모든 임시 개체를 삭제 합니다.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>설명

`DeleteTempMap` 개체를 삭제 하기 전에 임시 개체에 연결 된 Windows 메뉴 개체를 분리 `CMenu` `CMenu` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a> CMenu::D estroyMenu

사용 된 메뉴 및 모든 Windows 리소스를 소멸 시킵니다.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>반환 값

메뉴가 소멸 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴가 `CMenu` 제거 되기 전에 개체에서 분리 됩니다. Windows `DestroyMenu` 함수는 소멸자에서 자동으로 호출 됩니다 `CMenu` .

### <a name="example"></a>예제

  [CMenu:: CreateMenu](#createmenu)의 예제를 참조 하세요.

## <a name="cmenudetach"></a><a name="detach"></a> CMenu::D etach

개체에서 Windows 메뉴를 분리 `CMenu` 하 고 핸들을 반환 합니다.

```
HMENU Detach();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 Windows 메뉴에 대 한 HMENU 형식의 핸들 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`m_hMenu`데이터 멤버가 NULL로 설정 된 경우

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a> CMenu::D rawItem

소유자가 그린 메뉴의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
필요한 그리기 형식에 대 한 정보를 포함 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CMenu` 합니다. 응용 프로그램은이 멤버 함수를 종료 하기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

구조체에 대 한 설명은 [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 를 참조 하세요 `DRAWITEMSTRUCT` .

### <a name="example"></a>예제

다음 코드는 MFC [CTRLTEST](../../overview/visual-cpp-samples.md) 샘플에서 가져온 것입니다.

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a> CMenu:: EnableMenuItem

메뉴 항목을 사용 하거나 사용 하지 않도록 설정 하거나 희미하게 만듭니다.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>매개 변수

*nIDEnableItem*<br/>
*NEnable* 에 의해 결정 된 대로 사용할 메뉴 항목을 지정 합니다. 이 매개 변수는 팝업 메뉴 항목 뿐만 아니라 표준 메뉴 항목도 지정할 수 있습니다.

*nEnable*<br/>
수행할 동작을 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION와 MF_DISABLED, MF_ENABLED 또는 MF_GRAYED를 조합 하 여 사용할 수 있습니다. 비트 OR 연산자를 사용 하 여 이러한 값을 조합할 수 있습니다. 이러한 값에는 다음과 같은 의미가 있습니다.

- MF_BYCOMMAND 매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. 이것이 기본값입니다.

- MF_BYPOSITION 매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.

- 메뉴 항목을 사용 하지 않도록 설정 하 여 메뉴 항목을 선택할 수는 없지만 dim을 사용 하지는 MF_DISABLED.

- MF_ENABLED 메뉴 항목을 선택 하 여 흐리게 표시 된 상태에서 해당 항목을 복원할 수 있습니다.

- 메뉴 항목을 선택할 수 없도록 메뉴 항목을 사용 하지 않도록 MF_GRAYED 합니다.

### <a name="return-value"></a>반환 값

이전 상태 (MF_DISABLED, MF_ENABLED 또는 MF_GRAYED) 이거나, 유효 하지 않은 경우-1입니다.

### <a name="remarks"></a>설명

[CreateMenu](#createmenu), [insertmenu](#insertmenu), [ModifyMenu](#modifymenu)및 [loadmenuindirect](#loadmenuindirect) 멤버 함수는 메뉴 항목의 상태 (사용, 사용 안 함 또는 희미하게)를 설정할 수도 있습니다.

MF_BYPOSITION 값을 사용 하려면 응용 프로그램에서 올바른를 사용 해야 `CMenu` 합니다. `CMenu`메뉴 모음의를 사용 하는 경우 최상위 메뉴 항목 (메뉴 모음의 항목)이 영향을 받습니다. 팝업 또는 중첩 된 팝업 메뉴의 항목 상태를 위치 별로 설정 하려면 응용 프로그램에서 팝업 메뉴의를 지정 해야 합니다 `CMenu` .

응용 프로그램에서 MF_BYCOMMAND 플래그를 지정 하는 경우 Windows는에 종속 된 모든 팝업 메뉴 항목을 확인 합니다 `CMenu` . 따라서 중복 된 메뉴 항목이 없으면 메뉴 모음의를 사용 하는 `CMenu` 것 만으로 충분 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a> CMenu:: FromHandle

`CMenu`메뉴에 대 한 창 핸들을 지정 하 여 개체에 대 한 포인터를 반환 합니다.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>매개 변수

*hMenu*<br/>
메뉴에 대 한 창 핸들입니다.

### <a name="return-value"></a>반환 값

`CMenu`일시적 이거나 영구적 일 수 있는에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CMenu`개체가 Windows 메뉴 개체에 아직 연결 되지 않은 경우 임시 `CMenu` 개체가 생성 되 고 연결 됩니다.

이 임시 `CMenu` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 개체가 삭제 될 때 까지만 유효 합니다.

### <a name="example"></a>예제

  [CMenu:: CreateMenu](#createmenu)의 예제를 참조 하세요.

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a> CMenu:: GetDefaultItem

지정 된 메뉴의 기본 메뉴 항목을 결정 합니다.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>매개 변수

*gmdiFlags*<br/>
함수가 메뉴 항목을 검색 하는 방법을 지정 하는 값입니다. 이 매개 변수는 없음, 하나 또는 다음 값의 조합일 수 있습니다.

|값|의미|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|기본 항목이 하위 메뉴를 여는 경우 함수는 해당 하위 메뉴에서 재귀적으로 검색 하도록 지정 합니다. 하위 메뉴에 기본 항목이 없는 경우 반환 값은 하위 메뉴를 여는 항목을 식별 합니다.<br /><br /> 기본적으로이 함수는 하위 메뉴를 여는 항목 인지 여부에 관계 없이 지정 된 메뉴의 첫 번째 기본 항목을 반환 합니다.|
|GMDI_USEDISABLED|함수를 사용할 수 없는 경우에도 기본 항목을 반환 하도록 지정 합니다.<br /><br /> 기본적으로이 함수는 비활성화 되거나 회색으로 표시 된 항목을 건너뜁니다.|

*fByPos*<br/>
메뉴 항목의 식별자 또는 해당 위치를 검색할지 여부를 지정 하는 값입니다. 이 매개 변수가 FALSE 이면 식별자가 반환 됩니다. 그렇지 않으면 위치가 반환 됩니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 메뉴 항목의 식별자 또는 위치입니다. 함수가 실패 하면 반환 값은-1입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 Win32 함수 [Getmenudefaultitem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)의 동작을 구현 합니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a> CMenu:: GetMenuContextHelpId

와 연결 된 컨텍스트 도움말 ID를 검색 `CMenu` 합니다.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>반환 값

현재 연결 된 컨텍스트 도움말 ID입니다 (있는 `CMenu` 경우). 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a> CMenu:: GetMenuInfo

메뉴에 대 한 정보를 검색 합니다.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>매개 변수

*lpcmi*<br/>
메뉴에 대 한 정보를 포함 하는 [Menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값이 반환 됩니다. 그렇지 않으면 반환 값은 0입니다.

### <a name="remarks"></a>설명

메뉴에 대 한 정보를 검색 하려면이 함수를 호출 합니다.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a> CMenu:: GetMenuItemCount

팝업 또는 최상위 메뉴의 항목 수를 결정 합니다.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 메뉴의 항목 수입니다. 그렇지 않으면-1입니다.

### <a name="example"></a>예제

  [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu)의 예제를 참조 하세요.

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a> CMenu:: GetMenuItemID

*Npos* 에 의해 정의 된 위치에 있는 메뉴 항목의 메뉴 항목 식별자를 가져옵니다.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
ID를 검색할 메뉴 항목의 위치 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 팝업 메뉴에서 지정 된 항목의 항목 ID입니다. 지정 된 항목이 팝업 메뉴에 있는 항목과 달리 팝업 메뉴 이면 반환 값은-1입니다. *Npos* 가 구분 기호 메뉴 항목에 해당 하는 경우 반환 값은 0입니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a> CMenu:: GetMenuItemInfo

메뉴 항목에 대 한 정보를 검색 합니다.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>매개 변수

*uItem*<br/>
정보를 가져올 메뉴 항목의 식별자 또는 위치입니다. 이 매개 변수의 의미는의 값에 따라 달라 집니다 `ByPos` .

*lpMenuItemInfo*<br/>
Windows SDK에 설명 된 대로 메뉴에 대 한 정보를 포함 하는 [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)에 대 한 포인터입니다.

*fByPos*<br/>
의 의미를 지정 하는 값입니다 `nIDItem` . 기본적으로는 `ByPos` FALSE 이며 uItem은 메뉴 항목 식별자 임을 나타냅니다. `ByPos`가 FALSE로 설정 되어 있지 않으면 메뉴 항목 위치를 나타냅니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 반환 값이 0이 아닙니다. 함수가 실패하면 반환 값은 0입니다. 확장 오류 정보를 가져오려면 Windows SDK에 설명 된 대로 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 사용 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 함수 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)의 동작을 구현 합니다. 의 MFC 구현에서는 `GetMenuItemInfo` 메뉴에 핸들을 사용 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a> CMenu:: GetMenuState

지정 된 메뉴 항목의 상태 또는 팝업 메뉴의 항목 수를 반환 합니다.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
*Nflags* 에 의해 결정 된 메뉴 항목 ID를 지정 합니다.

*nFlags*<br/>
*NID* 의 특성을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- MF_BYCOMMAND 매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. 이것이 기본값입니다.

- MF_BYPOSITION 매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.

### <a name="return-value"></a>반환 값

지정 된 항목이 없으면 0xFFFFFFFF 값입니다. *NId* 가 팝업 메뉴를 식별 하는 경우 상위 바이트는 팝업 메뉴의 항목 수를 포함 하 고 하위 바이트는 팝업 메뉴와 연결 된 메뉴 플래그를 포함 합니다. 그렇지 않으면 반환 값은 다음 목록에 있는 값의 마스크 (부울 또는)입니다 .이 마스크는 *nId* 에서 식별 하는 메뉴 항목의 상태를 설명 합니다.

- MF_CHECKED은 MF_UNCHECKED를 사용 하 여 항목 옆에 기본 확인 표시를 설정 합니다. 응용 프로그램에서 확인 표시 비트맵을 제공 하면 ( `SetMenuItemBitmaps` 멤버 함수 참조) "확인 표시 설정" 비트맵이 표시 됩니다.

- 메뉴 항목을 사용 하지 않도록 설정 하 여 메뉴 항목을 선택할 수는 없지만 dim을 사용 하지는 MF_DISABLED.

- MF_ENABLED 메뉴 항목을 선택 하 여 흐리게 표시 된 상태에서 해당 항목을 복원할 수 있습니다. 이 상수의 값은 0입니다. 이 값을 사용 하는 경우 응용 프로그램에서 실패에 대해 0에 대해 테스트 해서는 안 됩니다.

- 메뉴 항목을 선택할 수 없도록 메뉴 항목을 사용 하지 않도록 MF_GRAYED 합니다.

- MF_MENUBARBREAK 정적 메뉴의 새 줄 이나 팝업 메뉴의 새 열에 항목을 배치 합니다. 새 팝업 메뉴 열이 이전 열과 수직 분할 선으로 구분 됩니다.

- MF_MENUBREAK 정적 메뉴의 새 줄 이나 팝업 메뉴의 새 열에 항목을 배치 합니다. 열 사이에 분할 선이 배치 되지 않습니다.

- MF_SEPARATOR 가로 분할 선을 그립니다. 는 팝업 메뉴 에서만 사용할 수 있습니다. 이 줄은 흐리게 표시 하거나 사용 하지 않도록 설정 하거나 강조 표시할 수 없습니다. 다른 매개 변수는 무시 됩니다.

- MF_UNCHECKED는 항목 옆에 있는 확인 표시를 제거 하는 MF_CHECKED으로 전환 됩니다. 응용 프로그램에서 확인 표시 비트맵을 제공 하면 ( `SetMenuItemBitmaps` 멤버 함수 참조) "확인 표시 해제" 비트맵이 표시 됩니다. 이 상수의 값은 0입니다. 이 값을 사용 하는 경우 응용 프로그램에서 실패에 대해 0에 대해 테스트 해서는 안 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a> CMenu:: GetMenuString

지정 된 메뉴 항목의 레이블을 지정 된 버퍼에 복사 합니다.

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>매개 변수

*nIDItem*<br/>
*Nflags* 의 값에 따라 메뉴 항목의 정수 식별자 또는 메뉴 항목의 오프셋을 지정 합니다.

*lpString*<br/>
레이블을 받을 버퍼를 가리킵니다.

*rString*<br/>
`CString`복사 된 메뉴 문자열을 받을 개체에 대 한 참조입니다.

*nMaxCount*<br/>
복사할 레이블의 최대 길이 (문자 수)를 지정 합니다. 레이블이 *nMaxCount* 에 지정 된 최대값 보다 길면 추가 문자가 잘립니다.

*nFlags*<br/>
*NIDItem* 매개 변수의 해석을 지정 합니다. 다음 값 중 하나일 수 있습니다.

|nFlags|NIDItem 해석|
|------------|-------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

### <a name="return-value"></a>반환 값

Null 종결자를 포함 하지 않고 버퍼에 복사 된 실제 문자 수를 지정 합니다.

### <a name="remarks"></a>설명

*NMaxCount* 매개 변수는 문자열을 종료 하는 null 문자를 수용할 수 있도록 레이블의 문자 수보다 커야 합니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a> CMenu:: GetSafeHmenu

이 개체가 래핑된 HMENU `CMenu` 또는 NULL 포인터를 반환 합니다 `CMenu` .

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>예제

  [CMenu:: LoadMenu](#loadmenu)의 예제를 참조 하세요.

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a> CMenu:: GetSubMenu 메뉴

`CMenu`팝업 메뉴의 개체를 검색 합니다.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
메뉴에 포함 된 팝업 메뉴의 위치를 지정 합니다. 첫 번째 메뉴 항목의 위치 값은 0부터 시작 합니다. 이 함수에는 팝업 메뉴의 식별자를 사용할 수 없습니다.

### <a name="return-value"></a>반환 값

`CMenu` `m_hMenu` 지정 된 위치에 팝업 메뉴가 있는 경우 해당 멤버에 팝업 메뉴에 대 한 핸들이 들어 있는 개체에 대 한 포인터이 고, 그렇지 않으면 NULL입니다. 개체가 없으면 `CMenu` 임시 개체가 생성 됩니다. 반환 된 포인터를 저장 하면 안 됩니다 `CMenu` .

### <a name="example"></a>예제

  [CMenu:: TrackPopupMenu](#trackpopupmenu)의 예제를 참조 하세요.

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a> CMenu:: InsertMenu

*N 위치* 에 지정 된 위치에 새 메뉴 항목을 삽입 하 고 다른 항목을 메뉴 아래로 이동 합니다.

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>매개 변수

*위치*<br/>
새 메뉴 항목을 삽입할 때 기준이 되는 메뉴 항목을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방법으로 *nflags* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|NPosition의 해석|
|------------|---------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다. *N 위치가* -1 이면 새 메뉴 항목이 메뉴의 끝에 추가 됩니다.|

*nFlags*<br/>
*N 위치* 를 해석 하는 방법을 지정 하 고 메뉴에 추가 될 때 새 메뉴 항목의 상태에 대 한 정보를 지정 합니다. 설정할 수 있는 플래그 목록은 [Appendmenu](#appendmenu) 멤버 함수를 참조 하세요. 둘 이상의 값을 지정 하려면 비트 OR 연산자를 사용 하 여 MF_BYCOMMAND 또는 MF_BYPOSITION 플래그와 결합 합니다.

*nIDNewItem*<br/>
새 메뉴 항목의 명령 ID를 지정 하거나 *n 플래그가* MF_POPUP로 설정 된 경우 팝업 메뉴의 메뉴 핸들 (HMENU)을 지정 합니다. *Nflags* 가 MF_SEPARATOR로 설정 된 경우 *nIDNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).

*lpszNewItem*<br/>
새 메뉴 항목의 내용을 지정 합니다. *Nflags* 는 다음과 같은 방법으로 *lpszNewItem* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|LpszNewItem 해석|
|------------|-----------------------------------|
|MF_OWNERDRAW|응용 프로그램이 메뉴 항목과 연결 된 추가 데이터를 유지 관리 하는 데 사용할 수 있는 응용 프로그램에서 제공 하는 32 비트 값을 포함 합니다. 이 32 비트 값은 `itemData` [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) 및 [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) 메시지에서 제공 하는 구조의 멤버에 있는 응용 프로그램에 사용할 수 있습니다. 이러한 메시지는 메뉴 항목이 처음 표시 되거나 변경 될 때 전송 됩니다.|
|MF_STRING|Null로 끝나는 문자열에 대 한 긴 포인터를 포함 합니다. 이는 기본 해석입니다.|
|MF_SEPARATOR|*LpszNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).|

*.Pbmp*<br/>
`CBitmap`메뉴 항목으로 사용 되는 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 *Nflags* 에서 값을 설정 하 여 메뉴 항목의 상태를 지정할 수 있습니다.

창에 있는 메뉴가 변경 될 때마다 (창이 표시 되는지 여부에 관계 없이) 응용 프로그램은를 호출 해야 합니다 `CWnd::DrawMenuBar` .

*NIDNewItem* 가 팝업 메뉴를 지정 하는 경우이 메뉴는 삽입 되는 메뉴의 일부가 됩니다. 해당 메뉴가 제거 되 면 삽입 된 메뉴도 제거 됩니다. 충돌을 방지 하려면 삽입 된 메뉴를 개체에서 분리 해야 합니다 `CMenu` .

활성 MDI (다중 문서 인터페이스) 자식 창이 최대화 되어 있고 응용 프로그램에서이 함수를 호출 하 고 MF_BYPOSITION 플래그를 지정 하 여 MDI 응용 프로그램의 메뉴에 팝업 메뉴를 삽입 하는 경우 메뉴는 예상 보다 왼쪽으로 한 위치에 삽입 됩니다. 이는 활성 MDI 자식 창의 컨트롤 메뉴가 MDI 프레임 창의 메뉴 모음에서 첫 번째 위치에 삽입 되기 때문에 발생 합니다. 메뉴를 올바르게 배치 하려면 응용 프로그램에서 다른 방법으로 사용할 수 있는 위치 값에 1을 추가 해야 합니다. 응용 프로그램은 WM_MDIGETACTIVE 메시지를 사용 하 여 현재 활성화 된 자식 창이 최대화 되었는지 여부를 확인할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a> CMenu:: InsertMenuItem

메뉴의 지정 된 위치에 새 메뉴 항목을 삽입 합니다.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>매개 변수

*uItem*<br/>
Windows SDK [Insertmenuitem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) 의 *uitem* 에 대 한 설명을 참조 하세요.

*lpMenuItemInfo*<br/>
Windows SDK의 *lpmii* 에 대 한 설명을 참조 `InsertMenuItem` 하세요.

*fByPos*<br/>
Windows SDK의 *fByPosition* 에 대 한 설명을 참조 `InsertMenuItem` 하세요.

### <a name="remarks"></a>설명

이 함수는 Windows SDK에 설명 된 [Insertmenuitem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)을 래핑합니다.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a> CMenu:: LoadMenu

응용 프로그램의 실행 파일에서 메뉴 리소스를 로드 하 여 개체에 연결 `CMenu` 합니다.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
로드할 메뉴 리소스의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다.

*nIDResource*<br/>
로드할 메뉴 리소스의 메뉴 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

메뉴 리소스가 성공적으로 로드 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 종료 하기 전에 메뉴가 창에 할당 되지 않은 경우 메뉴와 연결 된 시스템 리소스를 해제 해야 합니다. 응용 프로그램은 [DestroyMenu](#destroymenu) 멤버 함수를 호출 하 여 메뉴를 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a> CMenu:: LoadMenuIndirect

메모리의 메뉴 템플릿에서 리소스를 로드 하 여 개체에 연결 `CMenu` 합니다.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>매개 변수

*lpMenuTemplate*<br/>
메뉴 템플릿 (단일 [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) 구조체 및 하나 이상의 [menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) 구조 컬렉션)을 가리킵니다. 이러한 두 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

### <a name="return-value"></a>반환 값

메뉴 리소스가 성공적으로 로드 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴 템플릿은 헤더 다음에 하나 이상의 메뉴 항목과 팝업 메뉴가 포함 될 수 있는 하나 이상의 [Menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) 구조 컬렉션을 포함 합니다.

버전 번호는 0 이어야 합니다.

`mtOption`플래그는 팝업 목록의 마지막 항목에 대 한 MF_END 및 주 목록의 마지막 항목에 대 한를 포함 해야 합니다. `AppendMenu`다른 플래그는 멤버 함수를 참조 하세요. `mtId`에서 MF_POPUP가 지정 된 경우에는 MENUITEMTEMPLATE 구조에서 멤버를 생략 해야 합니다 `mtOption` .

`mtString`메뉴 항목의 이름을 null로 종료 되는 문자열로 포함할 수 있도록 MENUITEMTEMPLATE 구조에 할당 된 공간이 충분히 커야 합니다.

응용 프로그램은 종료 하기 전에 메뉴가 창에 할당 되지 않은 경우 메뉴와 연결 된 시스템 리소스를 해제 해야 합니다. 응용 프로그램은 [DestroyMenu](#destroymenu) 멤버 함수를 호출 하 여 메뉴를 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a> CMenu:: m_hMenu

개체에 연결 된 Windows 메뉴의 HMENU 핸들을 지정 합니다 `CMenu` .

```
HMENU m_hMenu;
```

### <a name="example"></a>예제

  [CMenu:: LoadMenu](#loadmenu)의 예제를 참조 하세요.

## <a name="cmenumeasureitem"></a><a name="measureitem"></a> CMenu:: MeasureItem

소유자 그리기 스타일을 사용 하는 메뉴가 생성 될 때 프레임 워크에서 호출 됩니다.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpMeasureItemStruct*<br/>
구조체에 대 한 포인터 `MEASUREITEMSTRUCT` 입니다.

### <a name="remarks"></a>설명

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 이 멤버 함수를 재정의 하 고 구조를 채워서 `MEASUREITEMSTRUCT` 메뉴의 크기를 창에 알립니다.

구조체에 대 한 설명은 [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 를 참조 하세요 `MEASUREITEMSTRUCT` .

### <a name="example"></a>예제

다음 코드는 MFC [CTRLTEST](../../overview/visual-cpp-samples.md) 샘플에서 가져온 것입니다.

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a> CMenu:: ModifyMenu

*Nposition* 에 지정 된 위치에서 기존 메뉴 항목을 변경 합니다.

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>매개 변수

*위치*<br/>
변경할 메뉴 항목을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방법으로 *nflags* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|NPosition의 해석|
|------------|---------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

*nFlags*<br/>
*N 위치* 를 해석 하는 방법을 지정 하 고 메뉴 항목에 적용 되는 변경 내용에 대 한 정보를 제공 합니다. 설정할 수 있는 플래그 목록은 [Appendmenu](#appendmenu) 멤버 함수를 참조 하세요.

*nIDNewItem*<br/>
수정 된 메뉴 항목의 명령 ID를 지정 하거나 *n 플래그가* MF_POPUP로 설정 된 경우 팝업 메뉴의 메뉴 핸들 (HMENU)을 지정 합니다. *Nflags* 가 MF_SEPARATOR로 설정 된 경우 *nIDNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).

*lpszNewItem*<br/>
새 메뉴 항목의 내용을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방법으로 *lpszNewItem* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|LpszNewItem 해석|
|------------|-----------------------------------|
|MF_OWNERDRAW|응용 프로그램이 메뉴 항목과 연결 된 추가 데이터를 유지 관리 하는 데 사용할 수 있는 응용 프로그램에서 제공 하는 32 비트 값을 포함 합니다. 이 32 비트 값은 MF_MEASUREITEM 및 MF_DRAWITEM를 처리할 때 응용 프로그램에서 사용할 수 있습니다.|
|MF_STRING|Null로 끝나는 문자열 또는에 대 한 긴 포인터를 포함 `CString` 합니다.|
|MF_SEPARATOR|*LpszNewItem* 매개 변수는 무시 됩니다 (필요 하지 않음).|

*.Pbmp*<br/>
`CBitmap`메뉴 항목으로 사용 되는 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 *Nflags* 에서 값을 설정 하 여 메뉴 항목의 새 상태를 지정 합니다. 이 함수는 메뉴 항목과 연결 된 팝업 메뉴를 대체 하는 경우 이전 팝업 메뉴를 제거 하 고 팝업 메뉴에서 사용 되는 메모리를 해제 합니다.

*NIDNewItem* 가 팝업 메뉴를 지정 하는 경우이 메뉴는 삽입 되는 메뉴의 일부가 됩니다. 해당 메뉴가 제거 되 면 삽입 된 메뉴도 제거 됩니다. 충돌을 방지 하려면 삽입 된 메뉴를 개체에서 분리 해야 합니다 `CMenu` .

창에 있는 메뉴가 변경 될 때마다 (창이 표시 되는지 여부에 관계 없이) 응용 프로그램은를 호출 해야 합니다 `CWnd::DrawMenuBar` . 기존 메뉴 항목의 특성을 변경 하려면 `CheckMenuItem` 및 멤버 함수를 사용 하는 것이 훨씬 빠릅니다 `EnableMenuItem` .

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a> CMenu:: operator HMENU

이 연산자를 사용 하 여 개체의 핸들을 검색 `CMenu` 합니다.

```
operator HMENU() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체의 핸들이 고, `CMenu` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

핸들을 사용 하 여 Windows Api를 직접 호출할 수 있습니다.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a> CMenu:: operator! =

두 메뉴가 논리적으로 같지 않은 지 여부를 확인 합니다.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>매개 변수

*메뉴가*<br/>
비교를 위한 `CMenu` 개체입니다.

### <a name="remarks"></a>설명

좌 변에 있는 메뉴 개체가 우변에 있는 메뉴 개체와 같지 않은 지 테스트 합니다.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a> CMenu:: operator = =

두 메뉴가 논리적으로 같은지 여부를 확인 합니다.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>매개 변수

*메뉴가*<br/>
비교를 위한 `CMenu` 개체입니다.

### <a name="remarks"></a>설명

좌 변에 있는 메뉴 개체가 오른쪽에 있는 메뉴 개체와 같은지 여부를 테스트 합니다 (HMENU 값 기준).

## <a name="cmenuremovemenu"></a><a name="removemenu"></a> CMenu:: RemoveMenu

메뉴에서 연결 된 팝업 메뉴를 사용 하 여 메뉴 항목을 삭제 합니다.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*위치*<br/>
제거할 메뉴 항목을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방법으로 *nflags* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|NPosition의 해석|
|------------|---------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

*nFlags*<br/>
*N 위치* 를 해석 하는 방법을 지정 합니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

팝업 메뉴에 대 한 핸들을 소멸 하지 않으므로 메뉴를 다시 사용할 수 있습니다. 이 함수를 호출 하기 전에 응용 프로그램은 `GetSubMenu` 멤버 함수를 호출 하 여 다시 사용할 팝업 개체를 검색할 수 있습니다 `CMenu` .

창에 있는 메뉴가 변경 될 때마다 (창이 표시 되는지 여부에 관계 없이) 응용 프로그램은를 호출 해야 합니다 `CWnd::DrawMenuBar` .

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a> CMenu:: SetDefaultItem

지정 된 메뉴에 대 한 기본 메뉴 항목을 설정 합니다.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>매개 변수

*uItem*<br/>
새 기본 메뉴 항목의 식별자 또는 위치 이거나 기본 항목이 없는 경우-1입니다. 이 매개 변수의 의미는 *fByPos* 의 값에 따라 달라 집니다.

*fByPos*<br/>
*Uitem* 의 의미를 지정 하는 값입니다. 이 매개 변수가 FALSE 이면 *Uitem* 은 메뉴 항목 식별자입니다. 그렇지 않으면 메뉴 항목 위치입니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 반환 값이 0이 아닙니다. 함수가 실패하면 반환 값은 0입니다. 확장 오류 정보를 가져오려면 Windows SDK에 설명 된 대로 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 사용 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 Win32 함수 [Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)의 동작을 구현 합니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a> CMenu:: SetMenuContextHelpId

컨텍스트 도움말 ID를와 연결 `CMenu` 합니다.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>매개 변수

*dwContextHelpId*<br/>
와 연결할 컨텍스트 도움말 ID `CMenu` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 0

### <a name="remarks"></a>설명

메뉴의 모든 항목은이 식별자를 공유 하므로 도움말 컨텍스트 식별자를 개별 메뉴 항목에 연결할 수 없습니다.

### <a name="example"></a>예제

  [CMenu:: InsertMenu](#insertmenu)의 예제를 참조 하세요.

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a> CMenu:: SetMenuInfo

메뉴에 대 한 정보를 설정 합니다.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>매개 변수

*lpcmi*<br/>
메뉴에 대 한 정보를 포함 하는 [Menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값이 반환 됩니다. 그렇지 않으면 반환 값은 0입니다.

### <a name="remarks"></a>설명

메뉴에 대 한 특정 정보를 설정 하려면이 함수를 호출 합니다.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a> CMenu:: SetMenuItemBitmaps

지정 된 비트맵과 메뉴 항목을 연결 합니다.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>매개 변수

*위치*<br/>
변경할 메뉴 항목을 지정 합니다. *Nflags* 매개 변수는 다음과 같은 방법으로 *nflags* 을 해석 하는 데 사용할 수 있습니다.

|nFlags|NPosition의 해석|
|------------|---------------------------------|
|MF_BYCOMMAND|매개 변수가 기존 메뉴 항목의 명령 ID를 제공 하도록 지정 합니다. MF_BYCOMMAND 또는 MF_BYPOSITION가 설정 되어 있지 않은 경우 기본값입니다.|
|MF_BYPOSITION|매개 변수가 기존 메뉴 항목의 위치를 제공 하도록 지정 합니다. 첫 번째 항목의 위치는 0입니다.|

*nFlags*<br/>
*N 위치* 를 해석 하는 방법을 지정 합니다.

*pBmpUnchecked*<br/>
확인 되지 않은 메뉴 항목에 사용할 비트맵을 지정 합니다.

*pBmpChecked*<br/>
선택 된 메뉴 항목에 사용할 비트맵을 지정 합니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메뉴 항목을 선택 하거나 선택 취소 하면 메뉴 항목 옆에 적절 한 비트맵이 표시 됩니다.

*Pbmpunchecked* 또는 *PBMPUNCHECKED* 가 NULL 이면 Windows는 해당 특성에 대 한 메뉴 항목 옆에 아무 것도 표시 하지 않습니다. 두 매개 변수가 모두 NULL 이면 항목을 선택 하면 Windows에서 기본 확인 표시를 사용 하 고, 항목을 선택 취소 하면 확인 표시를 제거 합니다.

메뉴가 제거 되 면 이러한 비트맵이 제거 되지 않습니다. 응용 프로그램에서 해당 응용 프로그램을 제거 해야 합니다.

Windows `GetMenuCheckMarkDimensions` 함수는 메뉴 항목에 사용 되는 기본 확인 표시의 크기를 검색 합니다. 응용 프로그램은 이러한 값을 사용 하 여이 함수에서 제공 하는 비트맵의 적절 한 크기를 결정 합니다. 크기를 가져오고 비트맵을 만든 다음 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a> CMenu:: SetMenuItemInfo

메뉴 항목에 대 한 정보를 변경 합니다.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>매개 변수

*uItem*<br/>
Windows SDK의 *Uitem* [에 대](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) 한 설명을 참조 하세요.

*lpMenuItemInfo*<br/>
Windows SDK의 *lpmii* 에 대 한 설명을 참조 `SetMenuItemInfo` 하세요.

*fByPos*<br/>
Windows SDK의 *fByPosition* 에 대 한 설명을 참조 `SetMenuItemInfo` 하세요.

### <a name="remarks"></a>설명

이 함수는 Windows SDK에 설명 된 [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)를 래핑합니다.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a> CMenu:: TrackPopupMenu

지정 된 위치에 부동 팝업 메뉴를 표시 하 고 팝업 메뉴에서 항목 선택을 추적 합니다.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>매개 변수

*nFlags*<br/>
화면 위치 및 마우스 위치 플래그를 지정 합니다. 사용 가능한 플래그 목록은 [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) 를 참조 하세요.

*x*<br/>
팝업 메뉴의 화면 좌표에서 가로 위치를 지정 합니다. *Nflags* 매개 변수의 값에 따라 메뉴를 왼쪽 맞춤, 오른쪽 맞춤 또는이 위치를 기준으로 가운데에 맞출 수 있습니다.

*y*<br/>
화면에서 메뉴 위쪽의 세로 위치를 화면 좌표로 지정 합니다.

*pWnd*<br/>
팝업 메뉴를 소유 하는 창을 식별 합니다. TPM_NONOTIFY 플래그가 지정 된 경우에도이 매개 변수는 NULL 일 수 없습니다. 이 창은 메뉴에서 모든 WM_COMMAND 메시지를 받습니다. Windows 버전 3.1 이상에서는이 창이 반환 될 때까지 WM_COMMAND 메시지를 수신 하지 않습니다 `TrackPopupMenu` . Windows 3.0에서는이 창이 반환 되기 전에 WM_COMMAND 메시지를 받습니다 `TrackPopupMenu` .

*lpRect*<br/>
무시됩니다.

### <a name="return-value"></a>반환 값

이 메서드는 Windows SDK [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) 호출 결과를 반환 합니다.

### <a name="remarks"></a>설명

부동 팝업 메뉴는 화면의 아무 곳에 나 나타날 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a> CMenu:: TrackPopupMenuEx

지정 된 위치에 부동 팝업 메뉴를 표시 하 고 팝업 메뉴에서 항목 선택을 추적 합니다.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>매개 변수

*fuFlags*<br/>
확장 된 메뉴에 대 한 다양 한 함수를 지정 합니다. 모든 값 및 해당 의미의 목록은 [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)를 참조 하세요.

*x*<br/>
팝업 메뉴의 화면 좌표에서 가로 위치를 지정 합니다.

*y*<br/>
화면에서 메뉴 위쪽의 세로 위치를 화면 좌표로 지정 합니다.

*pWnd*<br/>
팝업 메뉴를 소유 하 고 있는 창에 대 한 포인터로, 만든 메뉴에서 메시지를 받습니다. 이 창은 현재 응용 프로그램의 모든 창이 될 수 있지만 NULL 일 수는 없습니다. *FuFlags* 매개 변수에서 TPM_NONOTIFY 지정 하는 경우 함수는 *pWnd* 로 메시지를 보내지 않습니다. 함수는 *pWnd* 가 가리키는 창에 대해를 반환 하 여 WM_COMMAND 메시지를 수신 해야 합니다.

*lptpm*<br/>
화면 영역을 지정 하는 [Tpmparams](/windows/win32/api/winuser/ns-winuser-tpmparams) 구조에 대 한 포인터입니다. 메뉴가 겹치지 않아야 합니다. 이 매개 변수는 NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

*FuFlags* 매개 변수에서 TPM_RETURNCMD 지정 하는 경우 반환 값은 사용자가 선택한 항목의 메뉴 항목 식별자입니다. 사용자가 선택 하지 않고 메뉴를 취소 하거나 오류가 발생 하는 경우 반환 값은 0입니다.

*FuFlags* 매개 변수에서 TPM_RETURNCMD 지정 하지 않으면 함수가 성공 하는 경우 반환 값은 0이 아니고, 실패 하면 0입니다. 확장 오류 정보를 가져오려면 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출합니다.

### <a name="remarks"></a>설명

부동 팝업 메뉴는 화면의 아무 곳에 나 나타날 수 있습니다. 팝업 메뉴를 만들 때 발생 하는 오류를 처리 하는 방법에 대 한 자세한 내용은 [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)
