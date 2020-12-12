---
description: '자세히 알아보기: CShellManager 클래스'
title: CShellManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 67145782432c11ed62512eb618444fa19a4909ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264650"
---
# <a name="cshellmanager-class"></a>CShellManager 클래스

PIDL(식별자 포인터 목록)에 대한 포인터를 사용하여 작업할 수 있는 몇 가지 메서드를 구현합니다.

## <a name="syntax"></a>구문

```
class CShellManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CShellManager:: CShellManager](#cshellmanager)|`CShellManager` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CShellManager:: BrowseForFolder](#browseforfolder)|사용자가 셸 폴더를 선택할 수 있는 대화 상자를 표시 합니다.|
|[CShellManager:: ConcatenateItem](#concatenateitem)|두 Pidl를 연결 합니다.|
|[CShellManager:: CopyItem](#copyitem)|새 PIDL을 만들고 제공 된 PIDL을 여기에 복사 합니다.|
|[CShellManager:: CreateItem](#createitem)|지정 된 크기의 새 PIDL을 만듭니다.|
|[CShellManager:: FreeItem](#freeitem)|제공 된 PIDL을 삭제 합니다.|
|[CShellManager:: GetItemCount](#getitemcount)|제공 된 PIDL의 항목 수를 반환 합니다.|
|[CShellManager:: GetItemSize](#getitemsize)|제공 된 PIDL의 크기를 반환 합니다.|
|[CShellManager:: GetNextItem](#getnextitem)|PIDL에서 다음 항목을 반환 합니다.|
|[CShellManager:: GetParentItem](#getparentitem)|제공 된 항목의 부모 항목을 검색 합니다.|
|[CShellManager:: ItemFromPath](#itemfrompath)|제공 된 경로로 식별 되는 항목에 대 한 PIDL을 검색 합니다.|

## <a name="remarks"></a>설명

클래스의 메서드는 `CShellManager` 모두 pidl를 처리 합니다. PIDL은 셸 개체의 고유 식별자입니다.

개체를 수동으로 만들지 마십시오 `CShellManager` . 응용 프로그램의 프레임 워크에 의해 자동으로 생성 됩니다. 그러나 응용 프로그램의 초기화 프로세스 중에 [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) 를 호출 해야 합니다. 응용 프로그램에 대 한 셸 관리자에 대 한 포인터를 가져오려면 [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)를 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxshellmanager

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a> CShellManager:: BrowseForFolder

사용자가 셸 폴더를 선택할 수 있는 대화 상자를 표시 합니다.

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>매개 변수

*strOutFolder*<br/>
제한이 메서드에서 선택한 폴더의 경로를 저장 하는 데 사용 하는 문자열입니다.

*pWndParent*<br/>
진행 부모 창에 대 한 포인터입니다.

*lplszInitialFolder*<br/>
진행 대화 상자가 표시 될 때 기본적으로 선택 되는 폴더를 포함 하는 문자열입니다.

*lpszTitle*<br/>
진행 대화 상자의 제목입니다.

*ulFlags*<br/>
진행 대화 상자에 대 한 옵션을 지정 하는 플래그입니다. 자세한 설명은 [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) 를 참조 하세요.

*piFolderImage*<br/>
제한이 메서드가 선택한 폴더의 이미지 인덱스를 쓰는 정수 값에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

사용자가 대화 상자에서 폴더를 선택 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하면 응용 프로그램에서 사용자가 폴더를 선택할 수 있는 대화 상자를 만들고 표시 합니다. 메서드는 폴더의 경로를 *strOutFolder* 매개 변수에 씁니다.

### <a name="example"></a>예제

다음 예제에서는 메서드를 사용 하 여 개체에 대 한 참조를 검색 하는 방법과 메서드를 사용 하는 방법을 보여 줍니다 `CShellManager` `CWinAppEx::GetShellManager` `BrowseForFolder` . 이 코드 조각은 [탐색기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a> CShellManager:: ConcatenateItem

두 개의 Pidl를 포함 하는 새 목록을 만듭니다.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>매개 변수

*pidl1*<br/>
진행 첫 번째 항목입니다.

*pidl2*<br/>
진행 두 번째 항목입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 새 항목 목록에 대 한 포인터이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 *pidl1* 와 *pidl2* 를 둘 다 포함할 수 있는 새 [itemidlist](/windows/win32/api/shtypes/ns-shtypes-itemidlist) 를 만듭니다. 그런 다음 *pidl1* 및 *pidl2* 를 새 목록에 복사 합니다.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a> CShellManager:: CopyItem

항목 목록을 복사 합니다.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>매개 변수

*pidlSource*<br/>
진행 원래 항목 목록입니다.

### <a name="return-value"></a>반환 값

성공 하면 새로 만든 항목 목록에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

새로 만든 항목 목록은 소스 항목 목록과 크기가 같습니다.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a> CShellManager:: CreateItem

새 PIDL을 만듭니다.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>매개 변수

*cbSize*<br/>
진행 항목 목록의 크기입니다.

### <a name="return-value"></a>반환 값

성공한 경우 만들어진 항목 목록에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a> CShellManager:: CShellManager

`CShellManager` 개체를 생성합니다.

```
CShellManager();
```

### <a name="remarks"></a>설명

대부분의 경우를 직접 만들 필요가 없습니다 `CShellManager` . 기본적으로 프레임 워크는 사용자를 위해 하나를 만듭니다. 에 대 한 포인터를 가져오려면 `CShellManager` [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)를 호출 합니다. 수동으로를 만들 경우 `CShellManager` [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)메서드를 사용 하 여 초기화 해야 합니다.

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a> CShellManager:: FreeItem

항목 목록을 삭제 합니다.

```cpp
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>매개 변수

*pidl*<br/>
진행 삭제할 항목 목록입니다.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a> CShellManager:: GetItemCount

항목 목록의 항목 수를 반환 합니다.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>매개 변수

*pidl*<br/>
진행 항목 목록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

항목 목록의 항목 수입니다.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a> CShellManager:: GetItemSize

항목 목록의 크기를 반환 합니다.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>매개 변수

*pidl*<br/>
진행 항목 목록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

항목 목록의 크기입니다.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a> CShellManager:: GetNextItem

PIDL (항목 식별자 목록)에 대 한 포인터에서 다음 항목을 검색 합니다.

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>매개 변수

*pidl*<br/>
진행 반복할 항목의 목록입니다.

### <a name="return-value"></a>반환 값

목록의 다음 항목에 대 한 포인터입니다.

### <a name="remarks"></a>설명

목록에 항목이 더 이상 없으면이 메서드는 NULL을 반환 합니다.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a> CShellManager:: GetParentItem

PIDL (항목 식별자 목록)에 대 한 포인터의 부모를 검색 합니다.

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>매개 변수

*lpidl*<br/>
진행 부모를 검색할 PIDL입니다.

*lpidlParent*<br/>
제한이 메서드가 결과를 저장 하는 PIDL에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

부모 PIDL의 수준입니다.

### <a name="remarks"></a>설명

PIDL의 수준은 바탕 화면을 기준으로 합니다. 데스크톱 PIDL은 수준이 0 인 것으로 간주 됩니다.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a> CShellManager:: ItemFromPath

문자열 경로로 식별 된 항목에서 PIDL (항목 식별자 목록)에 대 한 포인터를 검색 합니다.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>매개 변수

*lpszPath*<br/>
진행 항목의 경로를 지정 하는 문자열입니다.

*pidl*<br/>
제한이 PIDL에 대 한 참조입니다. 메서드는이 PIDL을 사용 하 여 포인터를 반환 값에 저장 합니다.

### <a name="return-value"></a>반환 값

성공 하면 NOERROR를 반환 합니다. OLE 정의 오류 값입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
