---
description: '자세한 정보: CMFCShellListCtrl 클래스'
title: CMFCShellListCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: b5efc8f336c5958ad7a7f510c7f2b69e83ca6bca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339685"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 클래스

`CMFCShellListCtrl`클래스는 Windows 목록 컨트롤 기능을 제공 하 고 셸 항목 목록을 표시 하는 기능을 포함 하 여 확장 합니다.

## <a name="syntax"></a>구문

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCShellListCtrl::D isplayFolder](#displayfolder)|제공 된 폴더에 포함 된 항목의 목록을 표시 합니다.|
|[CMFCShellListCtrl::D isplayParentFolder](#displayparentfolder)|현재 표시 된 폴더의 부모인 폴더에 포함 된 항목의 목록을 표시 합니다.|
|[CMFCShellListCtrl:: EnableShellContextMenu](#enableshellcontextmenu)|바로 가기 메뉴를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCShellListCtrl:: GetCurrentFolder](#getcurrentfolder)|현재 폴더의 경로를 검색 합니다.|
|[CMFCShellListCtrl:: GetCurrentFolderName](#getcurrentfoldername)|현재 폴더의 이름을 검색 합니다.|
|[CMFCShellListCtrl:: GetCurrentItemIdList](#getcurrentitemidlist)|현재 목록 컨트롤 항목의 PIDL을 반환 합니다.|
|[CMFCShellListCtrl:: GetCurrentShellFolder](#getcurrentshellfolder)|현재 셸 폴더에 대 한 포인터를 반환 합니다.|
|[CMFCShellListCtrl:: GetItemPath](#getitempath)|항목의 텍스트 경로를 반환 합니다.|
|[CMFCShellListCtrl:: GetItemTypes](#getitemtypes)|목록 컨트롤에 의해 표시 되는 셸 항목 형식을 반환 합니다.|
|[CMFCShellListCtrl:: IsDesktop](#isdesktop)|현재 선택 된 폴더가 바탕 화면 폴더 인지 확인 합니다.|
|[CMFCShellListCtrl:: OnCompareItems](#oncompareitems)|프레임 워크는 두 항목을 비교할 때이 메서드를 호출 합니다. [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)를 재정의 합니다.|
|[CMFCShellListCtrl:: OnFormatFileDate](#onformatfiledate)|프레임 워크에서 목록 컨트롤이 표시 하는 파일 날짜를 검색할 때 호출 됩니다.|
|[CMFCShellListCtrl:: OnFormatFileSize](#onformatfilesize)|프레임 워크가 목록 컨트롤의 파일 크기를 변환할 때 호출 됩니다.|
|[CMFCShellListCtrl:: OnGetItemIcon](#ongetitemicon)|프레임 워크가 목록 컨트롤 항목의 아이콘을 검색할 때 호출 됩니다.|
|[CMFCShellListCtrl:: OnGetItemText](#ongetitemtext)|프레임 워크가 목록 컨트롤 항목의 텍스트를 변환할 때 호출 됩니다.|
|[CMFCShellListCtrl:: OnSetColumns](#onsetcolumns)|열 이름을 설정 하는 경우 프레임 워크에서 호출 됩니다.|
|[CMFCShellListCtrl:: Refresh](#refresh)|목록 컨트롤을 새로 고치고 다시 그립니다.|
|[CMFCShellListCtrl:: SetItemTypes](#setitemtypes)|목록 컨트롤에 표시 되는 항목의 형식을 설정 합니다.|

## <a name="remarks"></a>설명

`CMFCShellListCtrl`클래스는 프로그램에서 Windows 셸 항목을 나열할 수 있도록 하 여 [CMFCListCtrl 클래스](../../mfc/reference/cmfclistctrl-class.md) 의 기능을 확장 합니다. 사용 되는 표시 형식은 탐색기 창에 대 한 목록 보기의 경우와 같습니다.

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) 개체를 개체에 연결 하 여 `CMFCShellListCtrl` 전체 탐색기 창을 만들 수 있습니다. 그런 다음에서 항목을 선택 하면 `CMFCShellTreeCtrl` `CMFCShellListCtrl` 개체가 선택한 항목의 내용을 나열 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 만드는 방법과 `CMFCShellListCtrl` 현재 표시 된 폴더의 부모 폴더를 표시 하는 방법을 보여 줍니다. 이 코드 조각은 [탐색기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxshelllistCtrl

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a> CMFCShellListCtrl::D isplayFolder

제공 된 폴더에 포함 된 항목의 목록을 표시 합니다.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>매개 변수

*lpszPath*<br/>
진행 폴더의 경로를 포함 하는 문자열입니다.

*lpItemInfo*<br/>
진행 `LPAFX_SHELLITEMINFO` 표시할 폴더를 설명 하는 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a> CMFCShellListCtrl::D isplayParentFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체를 업데이트 하 여 현재 표시 된 폴더의 부모 폴더를 표시 합니다.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a> CMFCShellListCtrl:: EnableShellContextMenu

바로 가기 메뉴를 사용 하도록 설정 합니다.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 프레임 워크에서 바로 가기 메뉴를 사용할 수 있는지 여부를 지정 하는 부울입니다.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a> CMFCShellListCtrl:: GetCurrentFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에서 현재 선택 된 폴더의 경로를 검색 합니다.

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>매개 변수

*strPath*<br/>
제한이 메서드가 경로를 쓰는 문자열 매개 변수에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아닌 값입니다. 그렇지 않은 경우 0입니다.

### <a name="remarks"></a>설명

에서 선택한 폴더가 없으면이 메서드는 실패 `CMFCShellListCtrl` 합니다.

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a> CMFCShellListCtrl:: GetCurrentFolderName

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에서 현재 선택 된 폴더의 이름을 검색 합니다.

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>매개 변수

*strName*<br/>
제한이 메서드가 이름을 쓰는 문자열 매개 변수에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아닌 값입니다. 그렇지 않은 경우 0입니다.

### <a name="remarks"></a>설명

에서 선택한 폴더가 없으면이 메서드는 실패 `CMFCShellListCtrl` 합니다.

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a> CMFCShellListCtrl:: GetCurrentItemIdList

현재 선택 된 항목의 PIDL을 반환 합니다.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>반환 값

현재 항목의 PIDL입니다.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a> CMFCShellListCtrl:: GetCurrentShellFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에서 현재 선택 된 항목에 대 한 포인터를 가져옵니다.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>반환 값

선택한 개체에 대 한 [IShellFolder 인터페이스](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) 에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 개체가 선택 되어 있지 않으면이 메서드는 NULL을 반환 합니다.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a> CMFCShellListCtrl:: GetItemPath

항목의 경로를 검색 합니다.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>매개 변수

*strPath*<br/>
제한이 경로를 받는 문자열에 대 한 참조입니다.

*iItem*<br/>
진행 목록 항목의 인덱스입니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*IItem* 에서 제공 하는 인덱스는 현재 [Cmfcshelllistctrl 클래스](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 의해 표시 된 항목을 기반으로 합니다.

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a> CMFCShellListCtrl:: GetItemTypes

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 표시 되는 항목의 유형을 반환 합니다.

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>반환 값

에 나열 된 항목의 형식을 포함 하는 [Shcontf](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) 값입니다 `CMFCShellListCtrl` .

### <a name="remarks"></a>설명

에 나열 된 항목의 유형을 설정 하려면 `CMFCShellListCtrl` [Cmfcshelllistctrl:: SetItemTypes](#setitemtypes)를 호출 합니다.

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a> CMFCShellListCtrl:: IsDesktop

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 표시 되는 폴더가 바탕 화면 폴더 인지 여부를 확인 합니다.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>반환 값

표시 된 폴더가 바탕 화면 폴더 이면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a> CMFCShellListCtrl:: OnCompareItems

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>매개 변수

진행 *lParam1*<br/>
진행 *lParam2*<br/>
진행 *iColumn*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a> CMFCShellListCtrl:: OnFormatFileDate

프레임 워크는 개체와 관련 된 날짜를 문자열로 변환 해야 할 때이 메서드를 호출 합니다.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>매개 변수

*tmFile*<br/>
진행 파일과 연결 된 날짜입니다.

*str*<br/>
제한이 형식이 지정 된 파일 날짜를 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

[Cmfcshelllistctrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) 개체가 파일에 연결 된 날짜를 표시 하는 경우 해당 날짜를 문자열 형식으로 변환 해야 합니다. 는 `CMFCShellListCtrl` 이 메서드를 사용 하 여 변환을 수행 합니다. 기본적으로이 메서드는 현재 로캘을 사용 하 여 날짜를 문자열로 지정 합니다.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a> CMFCShellListCtrl:: OnFormatFileSize

프레임 워크는 개체의 크기를 문자열로 변환할 때이 메서드를 호출 합니다.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>매개 변수

*lFileSize*<br/>
진행 프레임 워크에 표시 되는 파일의 크기입니다.

*str*<br/>
제한이 형식이 지정 된 파일 크기를 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

[Cmfcshelllistctrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) 개체가 파일 크기를 표시 해야 하는 경우 파일 크기를 문자열 형식으로 변환 해야 합니다. 는 `CMFCShellListCtrl` 이 메서드를 사용 하 여 변환을 수행 합니다. 기본적으로이 메서드는 파일 크기를 바이트에서 kb로 변환한 다음 현재 로캘을 사용 하 여 크기를 문자열 형식으로 지정 합니다.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a> CMFCShellListCtrl:: OnGetItemIcon

프레임 워크는이 메서드를 호출 하 여 셸 목록 항목과 연결 된 아이콘을 검색 합니다.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>매개 변수

*iItem*<br/>
진행 항목 인덱스입니다.

*pItem*<br/>
진행 항목을 설명 하는 LPAFX_SHELLITEMINFO 매개 변수입니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 아이콘 이미지의 인덱스입니다. 함수가 실패 하면-1입니다.

### <a name="remarks"></a>설명

아이콘 이미지 인덱스는 시스템 이미지 목록을 기반으로 합니다.

기본적으로이 메서드는 *Pitem* 매개 변수를 사용 합니다. *IItem* 의 값은 기본 구현에서 사용 되지 않습니다. *IItem* 를 사용 하 여 사용자 지정 동작을 구현할 수 있습니다.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a> CMFCShellListCtrl:: OnGetItemText

프레임 워크는 셸 항목의 텍스트를 검색 해야 할 때이 메서드를 호출 합니다.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>매개 변수

*iItem*<br/>
진행 항목 인덱스입니다.

*iColumn*<br/>
진행 관심 있는 열입니다.

*pItem*<br/>
진행 항목을 설명 하는 LPAFX_SHELLITEMINFO 매개 변수입니다.

### <a name="return-value"></a>반환 값

`CString`항목과 연결 된 텍스트를 포함 하는입니다.

### <a name="remarks"></a>설명

개체의 각 항목에는 `CMFCShellListCtrl` 하나 이상의 열에 텍스트가 있을 수 있습니다. 프레임 워크는이 메서드를 호출할 때 관심이 있는 열을 지정 합니다. 이 함수를 수동으로 호출 하는 경우에는 관심 있는 열도 지정 해야 합니다.

기본적으로이 메서드는 *Pitem* 매개 변수를 사용 하 여 처리할 항목을 결정 합니다. *IItem* 의 값은 기본 구현에서 사용 되지 않습니다.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a> CMFCShellListCtrl:: OnSetColumns

프레임 워크는 열 이름을 설정 하면이 메서드를 호출 합니다.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>설명

기본적으로 프레임 워크는 개체에 4 개의 열을 만듭니다 `CMFCShellListCtrl` . 이러한 열의 이름은 **이름**, **크기**, **형식** 및 **수정** 됨입니다. 이 메서드를 재정의 하 여 열 수와 열 이름을 사용자 지정할 수 있습니다.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a> CMFCShellListCtrl:: Refresh

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체를 새로 고치고 다시 그립니다.

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>반환 값

`S_OK` 성공 하는 경우 그렇지 않으면 오류 값입니다.

### <a name="remarks"></a>설명

개체에 표시 되는 항목 목록을 새로 고치려면이 메서드를 호출 `CMFCShellListCtrl` 합니다.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a> CMFCShellListCtrl:: SetItemTypes

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) 개체에 나열 된 항목의 유형을 설정 합니다.

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>매개 변수

*nTypes*<br/>
진행 개체가 지 원하는 항목 종류의 목록입니다 `CMFCShellListCtrl` .

### <a name="remarks"></a>설명

항목 종류 목록에 대 한 자세한 내용은 [Shcontf](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 클래스](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 클래스](../../mfc/reference/cmfcshelltreectrl-class.md)
