---
description: '자세히 알아보기: CJumpList 클래스'
title: CJumpList 클래스
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 07e896c5b3a205a44850d45dcc4876103a48f2fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236908"
---
# <a name="cjumplist-class"></a>CJumpList 클래스

는 `CJumpList` 작업 표시줄에서 아이콘을 마우스 오른쪽 단추로 클릭할 때 표시 되는 바로 가기 목록입니다.

## <a name="syntax"></a>구문

```
class CJumpList;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|`CJumpList` 개체를 생성합니다.|
|[CJumpList:: ~ CJumpList](#_dtorcjumplist)|`CJumpList` 개체를 제거합니다.|

|Name|설명|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|커밋하지 않고 목록 작성 트랜잭션을 중단 합니다.|
|[CJumpList:: AddDestination](#adddestination)|오버로드됨. 목록에 대상을 추가 합니다.|
|[CJumpList:: AddKnownCategory](#addknowncategory)|목록에 알려진 범주를 추가 합니다.|
|[CJumpList:: AddTask](#addtask)|오버로드됨. 정식 작업 범주에 항목을 추가 합니다.|
|[CJumpList:: AddTasks](#addtasks)|정식 작업 범주에 항목을 추가 합니다.|
|[CJumpList:: AddTaskSeparator](#addtaskseparator)|작업 사이에 구분 기호를 추가 합니다.|
|[CJumpList:: ClearAll](#clearall)|지금까지 현재 인스턴스에 추가 된 모든 작업과 대상을 제거 `CJumpList` 합니다.|
|[CJumpList:: ClearAllDestinations](#clearalldestinations)|지금까지 현재 인스턴스에 추가 된 모든 대상을 제거 `CJumpList` 합니다.|
|[CJumpList:: CommitList](#commitlist)|목록 작성 트랜잭션을 종료 하 고 보고 된 목록을 연결 된 저장소 (이 경우에는 레지스트리)에 커밋합니다.|
|[CJumpList:: GetDestinationList](#getdestinationlist)|대상 목록에 대 한 인터페이스 포인터를 검색 합니다.|
|[CJumpList:: GetMaxSlots](#getmaxslots)|호출 응용 프로그램의 대상 메뉴에 표시할 수 있는 범주 헤더를 포함 하 여 최대 항목 수를 검색 합니다.|
|[CJumpList::GetRemovedItems](#getremoveditems)|제거 된 대상을 나타내는 항목의 배열을 반환 합니다.|
|[CJumpList:: InitializeList](#initializelist)|목록 작성 트랜잭션을 시작 합니다.|
|[CJumpList:: SetAppID](#setappid)|빌드 될 목록의 응용 프로그램 사용자 모델 ID를 설정 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxadv

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a> CJumpList:: ~ CJumpList

`CJumpList` 개체를 제거합니다.

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a> CJumpList::AbortList

커밋하지 않고 목록 작성 트랜잭션을 중단 합니다.

```cpp
void AbortList();
```

### <a name="remarks"></a>설명

이 메서드를 호출 하면를 호출 하지 않고 제거 하는 것과 동일한 효과가 `CJumpList` `CommitList` 있습니다.

## <a name="cjumplistadddestination"></a><a name="adddestination"></a> CJumpList:: AddDestination

목록에 대상을 추가 합니다.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>매개 변수

*lpcszCategoryName*<br/>
범주 이름을 지정 합니다. 지정 된 범주가 없으면 생성 됩니다.

*strDestinationPath*<br/>
대상 파일의 경로를 지정 합니다.

*strCategoryName*<br/>
범주 이름을 지정 합니다. 지정 된 범주가 없으면 생성 됩니다.

*pShellItem*<br/>
추가할 대상을 나타내는 셸 항목을 지정 합니다.

*pShellLink*<br/>
추가할 대상을 나타내는 셸 링크를 지정 합니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

인스턴스는 `CJumpList` 내부적으로 추가 된 대상을 누적 한 다음에서 커밋합니다 `CommitList` .

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a> CJumpList:: AddKnownCategory

목록에 알려진 범주를 추가 합니다.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>매개 변수

*category*<br/>
알려진 범주 유형을 지정 합니다. KDC_RECENT 또는 KDC_KNOWN 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

알려진 범주는 자주 사용 하는 모든 응용 프로그램에 대해 자동으로 계산 되는 항목을 자동으로 계산 합니다 `SHAddToRecentDocs` . (또는 셸에서는 일부 시나리오에서 응용 프로그램을 대신 하 여이를 호출 하는 경우에는 간접적으로 사용 합니다.)

## <a name="cjumplistaddtask"></a><a name="addtask"></a> CJumpList:: AddTask

정식 작업 범주에 항목을 추가 합니다.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>매개 변수

*strTargetExecutablePath*<br/>
대상 작업 경로를 지정 합니다.

*strCommandLineArgs*<br/>
*StrTargetExecutablePath* 로 지정 된 실행 파일의 명령줄 인수를 지정 합니다.

*strTitle*<br/>
대상 목록에 표시 되는 작업 이름입니다.

*strIconLocation*<br/>
제목과 함께 대상 목록에 표시 되는 아이콘의 위치입니다.

*iIconIndex*<br/>
아이콘 인덱스입니다.

*pShellLink*<br/>
추가할 작업을 나타내는 셸 링크입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

인스턴스는 `CJumpList` 지정 된 작업을 누적 하 고를 실행 하는 동안 대상 목록에 추가 `CommitList` 합니다. 작업 항목은 응용 프로그램의 대상 메뉴 아래쪽에 있는 범주에 표시 됩니다. 이 범주는 UI에 채워질 때 다른 모든 범주 보다 우선적으로 적용 됩니다.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a> CJumpList:: AddTasks

정식 작업 범주에 항목을 추가 합니다.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>매개 변수

*pObjectCollection*<br/>
추가할 작업의 컬렉션입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

CJumpList의 인스턴스는 지정 된 작업을 누적 하 고를 실행 하는 동안 대상 목록에 추가 `CommitList` 합니다. 작업 항목은 응용 프로그램의 대상 메뉴 아래쪽에 있는 범주에 표시 됩니다. 이 범주는 UI에 채워질 때 다른 모든 범주 보다 우선적으로 적용 됩니다.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a> CJumpList:: AddTaskSeparator

작업 사이에 구분 기호를 추가 합니다.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a> CJumpList::CJumpList

`CJumpList` 개체를 생성합니다.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>매개 변수

*bAutoCommit 커밋*<br/>
이 매개 변수가 FALSE 이면 목록이 소멸자에서 자동으로 커밋되지 않습니다.

## <a name="cjumplistclearall"></a><a name="clearall"></a> CJumpList:: ClearAll

지금까지 현재 인스턴스에 추가 된 모든 작업과 대상을 제거 `CJumpList` 합니다.

```cpp
void ClearAll();
```

### <a name="remarks"></a>설명

이 메서드는 모든 데이터 및 내부 인터페이스를 지우고 해제 합니다.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a> CJumpList:: ClearAllDestinations

지금까지 CJumpList의 현재 인스턴스에 추가 된 모든 대상을 제거 합니다.

```cpp
void ClearAllDestinations();
```

### <a name="remarks"></a>설명

대상 목록 작성의 현재 세션에서 지금까지 추가 된 모든 대상을 제거 하 고 다른 대상을 다시 추가 해야 하는 경우이 함수를 호출 합니다. 내부가 초기화 된 경우에는 활성 상태로 유지 `ICustomDestinationList` 됩니다.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a> CJumpList:: CommitList

목록 작성 트랜잭션을 종료 하 고 보고 된 목록을 연결 된 저장소 (이 경우에는 레지스트리)에 커밋합니다.

```
BOOL CommitList();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

Commit은 원자성입니다. 커밋이 실패할 경우 오류가 반환 됩니다.  `CommitList`가 호출 되 면 제거 된 항목의 현재 목록이 정리 됩니다. 이 메서드를 호출 하면 활성 목록 작성 트랜잭션이 없는 개체를 다시 설정 합니다. 목록을 업데이트 하려면를 `BeginList` 다시 호출 해야 합니다.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a> CJumpList:: GetDestinationList

대상 목록에 대 한 인터페이스 포인터를 검색 합니다.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

점프 목록이 초기화 되지 않았거나 커밋되거나 중단 된 경우 반환 되는 값은 NULL입니다.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a> CJumpList:: GetMaxSlots

호출 응용 프로그램의 대상 메뉴에 표시할 수 있는 범주 헤더를 포함 하 여 최대 항목 수를 검색 합니다.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

응용 프로그램은이 값까지 결합 된 항목 및 범주 헤더만 보고할 수 있습니다. , 또는에 대 한 호출이 `AppendCategory` `AppendKnownCategory` `AddUserTasks` 이 숫자를 초과 하면 오류가 반환 됩니다.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a> CJumpList::GetRemovedItems

제거 된 대상을 나타내는 항목의 배열을 반환 합니다.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

제거 된 대상은 점프 목록을 초기화 하는 동안 검색 됩니다. 새 대상 목록을 생성할 때 응용 프로그램은 제거 된 대상 목록을 먼저 처리 하 여 제거 된 목록 열거자에서 반환 하는 항목에 대 한 추적 데이터를 지워야 합니다. 응용 프로그램에서 현재 호출이 시작 된 트랜잭션에서 방금 제거 된 항목을 제공 하려고 하면 `BeginList` 해당 항목을 다시 추가 하는 메서드 호출이 실패 하 여 응용 프로그램이 제거 된 목록을 유지 하 게 됩니다.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a> CJumpList:: InitializeList

목록 작성 트랜잭션을 시작 합니다.

```
BOOL InitializeList();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

를 사용 하 여 포인터를 검색 하거나를 사용 하 여 사용 `ICustomDestinationList` `GetDestinationList` 가능한 슬롯의 수 `GetMaxSlots` 또는를 사용 하 여 제거 된 항목의 목록을 검색 하려는 경우가 아니면이 메서드를 명시적으로 호출할 필요가 없습니다 `GetRemovedItems` .

## <a name="cjumplistsetappid"></a><a name="setappid"></a> CJumpList:: SetAppID

빌드 될 목록의 응용 프로그램 사용자 모델 ID를 설정 합니다.

```cpp
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>매개 변수

*strAppID*<br/>
응용 프로그램 사용자 모델 ID를 지정 하는 문자열입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
