---
description: '자세히 알아보기: CRecentFileList 클래스'
title: CRecentFileList 클래스
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: 9433e65336cba1018c7bff8cf3a90e239ae5e3eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301128"
---
# <a name="crecentfilelist-class"></a>CRecentFileList 클래스

MRU(가장 최근에 사용됨) 파일 목록의 컨트롤을 지원합니다.

## <a name="syntax"></a>구문

```
class CRecentFileList
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|`CRecentFileList` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRecentFileList:: Add](#add)|MRU 파일 목록에 파일을 추가 합니다.|
|[CRecentFileList:: GetDisplayName](#getdisplayname)|MRU 파일 이름의 메뉴 표시에 대 한 표시 이름을 제공 합니다.|
|[CRecentFileList:: GetSize](#getsize)|MRU 파일 목록의 파일 수를 검색 합니다.|
|[CRecentFileList:: ReadList](#readlist)|레지스트리에서 MRU 파일 목록을 읽습니다. INI 파일.|
|[CRecentFileList:: Remove](#remove)|MRU 파일 목록에서 파일을 제거 합니다.|
|[CRecentFileList:: UpdateMenu](#updatemenu)|MRU 파일 목록의 메뉴 표시를 업데이트 합니다.|
|[CRecentFileList:: WriteList](#writelist)|는 레지스트리의 MRU 파일 목록을 작성 합니다. INI 파일.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CRecentFileList:: operator \[\]](#operator_at)|지정 된 `CString` 위치에 있는 개체를 반환 합니다.|

## <a name="remarks"></a>설명

MRU 파일 목록에서 파일을 추가 하거나 삭제할 수 있으며, 파일 목록을 레지스트리 또는에서 읽거나 쓸 수 있습니다. INI 파일을 표시 하 고 MRU 파일 목록을 표시 하는 메뉴를 업데이트할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CRecentFileList`

## <a name="requirements"></a>요구 사항

**헤더:** afxadv

## <a name="crecentfilelistadd"></a><a name="add"></a> CRecentFileList:: Add

가장 최근에 사용한 (MRU) 파일 목록에 파일을 추가 합니다.

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
목록에 추가할 경로 이름을 지정 합니다.

*lpszAppID*<br/>
응용 프로그램의 응용 프로그램 사용자 모델 ID를 지정 합니다.

*pItem*<br/>
목록에 추가할 셸 항목에 대 한 포인터를 지정 합니다.

*pLink*<br/>
목록에 추가할 셸 링크에 대 한 포인터를 지정 합니다.

*pidl*<br/>
최근 docs 폴더에 추가 해야 하는 셸 항목의 IDLIST를 지정 합니다.

### <a name="remarks"></a>설명

파일 이름이 MRU 목록의 맨 위에 추가 됩니다. 파일 이름이 MRU 목록에 이미 있는 경우 맨 위로 이동 됩니다.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a> CRecentFileList::CRecentFileList

`CRecentFileList` 개체를 생성합니다.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>매개 변수

*nStart*<br/>
MRU (가장 최근에 사용 됨) 파일 목록의 메뉴 표시에서 번호 매기기의 오프셋입니다.

*lpszSection*<br/>
는 레지스트리 또는 응용 프로그램의 섹션 이름을 가리킵니다. MRU 파일 목록을 읽고/또는 쓴 INI 파일입니다.

*lpszEntryFormat*<br/>
는 레지스트리 또는 응용 프로그램의에 저장 된 항목의 이름에 사용할 형식 문자열을 가리킵니다. INI 파일.

*nSize*<br/>
MRU 파일 목록의 최대 파일 수입니다.

*nMaxDispLen*<br/>
MRU 파일 목록에서 파일 이름의 메뉴 표시에 사용할 수 있는 최대 길이 (문자 수)입니다.

### <a name="remarks"></a>설명

*LpszEntryFormat* 가 가리키는 형식 문자열은 각 MRU 항목의 인덱스를 대체 하는 데 사용 되는 "% d"을 (를) 포함 해야 합니다. 예를 들어 형식 문자열이 이면 항목은, 등으로 `"file%d"` 이름이 지정 됩니다 `file0` `file1` .

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a> CRecentFileList:: GetDisplayName

Mru 목록의 메뉴 표시에서 사용 하기 위해 MRU 파일 목록에서 파일의 표시 이름을 가져옵니다.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>매개 변수

*strName*<br/>
MRU 파일의 메뉴 목록에 이름이 표시 될 파일의 전체 경로입니다.

*nIndex*<br/>
MRU 파일 목록에서 파일의 인덱스 (0부터 시작)입니다.

*lpszCurDir*<br/>
현재 디렉터리를 포함 하는 문자열입니다.

*nCurDir*<br/>
현재 디렉터리 문자열의 길이입니다.

*bAtLeastName*<br/>
0이 아닌 경우는 최대 표시 길이 (생성자에 *Nmaxdisplen* 매개 변수로 전달 됨)를 초과 하는 경우에도 파일의 기본 이름이 반환 되어야 함을 나타냅니다 `CRecentFileList` .

### <a name="return-value"></a>반환 값

가장 최근에 사용한 (MRU) 파일 목록의 지정 된 인덱스에 파일 이름이 없는 경우 **FALSE** 입니다.

### <a name="remarks"></a>설명

파일이 현재 디렉터리에 있는 경우 함수는 디렉터리를 표시 되지 않도록 둡니다. 파일 이름이 너무 길면 디렉터리와 확장이 제거 됩니다. 파일 이름이 여전히 너무 길면 *bAtLeastName* 가 0이 아닌 경우 표시 이름이 빈 문자열로 설정 됩니다.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a> CRecentFileList:: GetSize

MRU 파일 목록의 파일 수를 검색 합니다.

```
int GetSize() const;
```

### <a name="return-value"></a>반환 값

현재 가장 최근에 사용한 (MRU) 파일 목록의 파일 수입니다.

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a> CRecentFileList:: operator []

오버 로드 된 첨자 ( `[]` ) 연산자는 `CString` *n 인덱스* 의 인덱스 (0부터 시작)에 의해 지정 된 단일를 반환 합니다.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
집합에 있는의 0부터 시작 하는 인덱스입니다 `CString` `CString` .

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a> CRecentFileList:: ReadList

레지스트리 또는 응용 프로그램의에서 가장 최근에 사용한 (MRU) 파일 목록을 읽습니다. INI 파일.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a> CRecentFileList:: Remove

MRU 파일 목록에서 파일을 제거 합니다.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
가장 최근에 사용한 (MRU) 파일 목록에서 제거할 파일의 인덱스 (0부터 시작)입니다.

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a> CRecentFileList:: UpdateMenu

MRU 파일 목록의 메뉴 표시를 업데이트 합니다.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>매개 변수

*pCmdUI*<br/>
가장 최근에 사용한 (MRU) 파일 목록 메뉴에 대 한 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터입니다.

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a> CRecentFileList:: WriteList

가장 최근에 사용한 (MRU) 파일 목록을 레지스트리 또는 응용 프로그램의에 씁니다. INI 파일.

```
virtual void WriteList();
```

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)
