---
description: '자세히 알아보기: CMFCShellTreeCtrl 클래스'
title: CMFCShellTreeCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 86b18d1cb919eaa36c3aed0d6e1623bab530a0aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339672"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 클래스

`CMFCShellTreeCtrl`클래스는 셸 항목의 계층을 표시 하 여 [CTreeCtrl 클래스](../../mfc/reference/ctreectrl-class.md) 기능을 확장 합니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|바로 가기 메뉴를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCShellTreeCtrl:: GetFlags](#getflags)|[IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)에 전달 되는 플래그의 조합을 반환 합니다.|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|항목에 대 한 경로를 검색 합니다.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|이 개체와 함께 사용 되어 탐색기와 같은 창을 만드는 [Cmfcshelllistctrl 클래스](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 대 한 포인터를 반환 합니다 `CMFCShellTreeCtrl` .|
|[CMFCShellTreeCtrl:: OnChildNotify](#onchildnotify)|이 멤버 함수는이 창에 적용 되는 알림 메시지를 받을 때이 창의 부모 창에서 호출 됩니다. ( [CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)를 재정의 합니다.)|
|[CMFCShellTreeCtrl:: OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl:: OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl:: Refresh](#refresh)|현재 개체를 새로 고치고 다시 그립니다 `CMFCShellTreeCtrl` .|
|[CMFCShellTreeCtrl:: SelectPath](#selectpath)|제공 된 PIDL 또는 문자열 경로를 기반으로 적절 한 트리 컨트롤 항목을 선택 합니다.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|에서 사용 하는 플래그와 유사 하 게 트리 컨텍스트를 필터링 할 플래그를 설정 `IShellFolder::EnumObjects` 합니다.|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|현재 개체와 개체 간의 관계를 설정 합니다 `CMFCShellTreeCtrl` `CMFCShellListCtrl` .|

## <a name="remarks"></a>설명

이 클래스는 `CTreeCtrl` 프로그램에서 트리에 Windows 셸 항목을 포함 하도록 설정 하 여 클래스를 확장 합니다. 이 클래스는 개체와 연결 `CMFCShellListCtrl` 하 여 전체 탐색기 창을 만들 수 있습니다. 그런 다음 트리에서 항목을 선택 하면 연결 된 목록에 Windows 셸 항목의 목록이 표시 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxshelltreeCtrl

## <a name="example"></a>예제

다음 예제에서는 `CMFCShellTreeCtrl` 클래스의 개체를 만드는 방법을 보여 줍니다. 이 코드 조각은 [탐색기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a> CMFCShellTreeCtrl::EnableShellContextMenu

바로 가기 메뉴를 사용 하도록 설정 합니다.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 바로 가기 메뉴를 사용할지 여부를 지정 하는 부울입니다.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a> CMFCShellTreeCtrl:: GetFlags

[CMFCShellTreeCtrl 클래스](../../mfc/reference/cmfcshelltreectrl-class.md) 개체에 대해 설정 된 플래그를 반환 합니다.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>반환 값

현재 설정 된 플래그의 조합을 지정 하는 DWORD 값입니다.

### <a name="remarks"></a>설명

에 설정 된 플래그는 `CMFCShellTreeCtrl` 개체를 새로 고칠 때마다 [IShellFolder:: enumobjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) 메서드로 전송 됩니다. [CMFCShellTreeCtrl:: SetFlags](#setflags) 메서드를 사용 하 여 플래그를 변경할 수 있습니다.

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a> CMFCShellTreeCtrl::GetItemPath

[CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md) 개체의 항목 경로를 검색 합니다.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>매개 변수

*strPath*<br/>
제한이 문자열 매개 변수에 대 한 참조입니다. 메서드는 항목의 경로를이 매개 변수에 씁니다.

*htreeItem*<br/>
진행 메서드는이 트리 컨트롤 항목의 경로를 검색 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아닌 값입니다. 그렇지 않은 경우 0입니다.

### <a name="remarks"></a>설명

이 메서드가 실패 하면 *Strpath* 에 빈 문자열이 포함 됩니다.

*HTreeItem* 를 지정 하지 않으면이 메서드는 현재 선택 된 항목에 대 한 문자열을 가져오려고 시도 합니다. 항목을 선택 하지 않고 *hTreeItem* 가 NULL 이면이 메서드는 실패 합니다.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a> CMFCShellTreeCtrl::GetRelatedList

이 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) 개체와 연결 된 [Cmfcshelllistctrl 클래스](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 대 한 포인터를 반환 합니다.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>반환 값

`CMFCShellListCtrl`이 트리 컨트롤 개체와 연결 된 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

개체와 개체를 함께 사용 하 여 `CMFCShellListCtrl` `CMFCShellTreeCtrl` 탐색기와 같은 창을 만들 수 있습니다. [CMFCShellTreeCtrl:: SetRelatedList](#setrelatedlist) 메서드를 사용 하 여 두 클래스를 연결 합니다. 연결 된 후 프레임 워크는의 선택 항목이 변경 되 면 자동으로를 업데이트 합니다 `CMFCShellListCtrl` `CMFCShellTreeCtrl` .

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a> CMFCShellTreeCtrl:: OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>매개 변수

진행 *메시지*<br/>
진행 *wParam*<br/>
진행 *lParam*<br/>
진행 *Plresult*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a> CMFCShellTreeCtrl:: OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>매개 변수

진행 *Pitem*<br/>
진행 *Bselected*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a> CMFCShellTreeCtrl:: OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>매개 변수

진행 *Pitem*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a> CMFCShellTreeCtrl:: Refresh

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)를 새로 고치고 다시 그립니다.

```cpp
void Refresh();
```

### <a name="remarks"></a>설명

에 표시 된 항목의 계층 구조를 새로 고치려면이 메서드를 호출 `CMFCShellTreeCtrl` 합니다.

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a> CMFCShellTreeCtrl:: SelectPath

제공 된 경로를 기반으로 [CMFCShellTreeCtrl 클래스](../../mfc/reference/cmfcshelltreectrl-class.md) 에서 항목을 선택 합니다.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>매개 변수

*lpszPath*<br/>
진행 항목의 경로를 지정 하는 문자열입니다.

*lpidl*<br/>
진행 항목을 지정 하는 PIDL

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a> CMFCShellTreeCtrl::SetFlags

트리 컨텍스트를 필터링 할 플래그를 설정 합니다.

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
진행 설정할 플래그입니다.

*bRefresh*<br/>
진행 을 즉시 새로 고칠지 여부를 지정 하는 부울입니다 `CMFCShellTreeCtrl`  .

### <a name="remarks"></a>설명

는 `CMFCShellTreeCtrl` 모든 set 플래그를 [IShellFolder:: enumobjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)에 전달 합니다. 다른 플래그의 값에 대 한 자세한 내용은 [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)를 참조 하세요.

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a> CMFCShellTreeCtrl::SetRelatedList

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체를 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) 개체와 연결 합니다.

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>매개 변수

*pShellList*<br/>
진행 개체에 대 한 포인터 `CMFCShellListCtrl` 입니다.

### <a name="remarks"></a>설명

이 메서드는를 `CMFCShellListCtrl` 와 연결 `CMFCShellTreeCtrl` 합니다. 이러한 개체는 탐색기와 같은 창으로 표시 될 수 있습니다. 사용자가에서 개체를 선택 하면의 `CMFCShellTreeCtrl` 연결 된 항목이 `CMFCShellListCtrl` 자동으로 업데이트 됩니다.

[CMFCShellTreeCtrl:: GetRelatedList](#getrelatedlist) 메서드를 사용 하 여와 연결 된를 검색 `CMFCShellListCtrl` `CMFCShellTreeCtrl` 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 클래스](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 클래스](../../mfc/reference/cmfcshelllistctrl-class.md)
