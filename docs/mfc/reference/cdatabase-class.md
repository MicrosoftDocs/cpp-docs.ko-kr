---
description: '자세한 정보: CDatabase 클래스'
title: CDatabase 클래스
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: 82859ebcffeb833ca5afe885b0ae35916da4cf28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247984"
---
# <a name="cdatabase-class"></a>CDatabase 클래스

데이터 소스 작업을 할 수 있는 통로인 데이터 소스에 대한 연결을 나타냅니다.

## <a name="syntax"></a>구문

```
class CDatabase : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|`CDatabase` 개체를 생성합니다. 또는를 호출 하 여 개체를 초기화 해야 합니다 `OpenEx` `Open` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|`AddNew` `Edit` `Delete` 연결 된 `Update` 데이터 소스에 대 한,, 및 클래스의 멤버 함수에 대 한 일련의 해독 가능한 호출용 "트랜잭션"을 시작 `CRecordset` 합니다. 데이터 원본은의 트랜잭션을 지원 해야 `BeginTrans` 적용 됩니다.|
|[CDatabase:: BindParameters](#bindparameters)|를 호출 하기 전에 매개 변수를 바인딩할 수 있습니다 `CDatabase::ExecuteSQL` .|
|[CDatabase:: Cancel](#cancel)|비동기 작업 또는 두 번째 스레드에서 프로세스를 취소 합니다.|
|[CDatabase:: CanTransact](#cantransact)|데이터 원본이 트랜잭션을 지원 하면 0이 아닌 값을 반환 합니다.|
|[CDatabase:: CanUpdate](#canupdate)|개체를 업데이트할 수 있으면 0이 아닌 값을 반환 `CDatabase` 합니다 (읽기 전용 아님).|
|[CDatabase:: Close](#close)|데이터 원본 연결을 닫습니다.|
|[CDatabase:: CommitTrans](#committrans)|에 의해 시작 된 트랜잭션을 완료 `BeginTrans` 합니다. 데이터 원본을 변경 하는 트랜잭션의 명령은 수행 됩니다.|
|[CDatabase:: ExecuteSQL](#executesql)|SQL 문을 실행 합니다. 데이터 레코드는 반환 되지 않습니다.|
|[CDatabase:: Get책갈피 지 속성](#getbookmarkpersistence)|레코드 집합 개체에 책갈피를 유지 하는 작업을 식별 합니다.|
|[CDatabase::GetConnect](#getconnect)|개체를 데이터 원본에 연결 하는 데 사용 되는 ODBC 연결 문자열을 반환 합니다 `CDatabase` .|
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|열린 레코드 집합 개체에 대 한 트랜잭션 커밋 효과를 식별 합니다.|
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|열린 레코드 집합 개체에 대 한 트랜잭션 롤백 효과를 식별 합니다.|
|[CDatabase:: GetDatabaseName](#getdatabasename)|현재 사용 중인 데이터베이스의 이름을 반환 합니다.|
|[CDatabase:: IsOpen](#isopen)|`CDatabase`개체가 현재 데이터 소스에 연결 되어 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDatabase:: OnSetOptions](#onsetoptions)|표준 연결 옵션을 설정 하기 위해 프레임 워크에서 호출 됩니다. 기본 구현에서는 쿼리 제한 시간 값을 설정 합니다. 을 호출 하 여 이러한 옵션을 미리 설정할 수 있습니다 `SetQueryTimeout` .|
|[CDatabase:: Open](#open)|ODBC 드라이버를 통해 데이터 원본에 대 한 연결을 설정 합니다.|
|[CDatabase:: Microsoft.office.interop.visio.documents.openex](#openex)|ODBC 드라이버를 통해 데이터 원본에 대 한 연결을 설정 합니다.|
|[CDatabase:: Rollback](#rollback)|현재 트랜잭션 중에 적용 된 변경 내용을 취소 합니다. 데이터 소스는 호출에서 정의 되는 변경 되지 않은 상태로 이전 상태로 돌아갑니다 `BeginTrans` .|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|데이터 원본 연결 시도가 시간 초과 되는 시간 (초)을 설정 합니다.|
|[CDatabase:: SetQueryTimeout](#setquerytimeout)|데이터베이스 쿼리 작업의 제한 시간 (초)을 설정 합니다. 모든 후속 레코드 집합 `Open` , `AddNew` , `Edit` 및 호출에 영향을 줍니다 `Delete` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|데이터 원본에 대 한 ODBC (Open Database Connectivity) 연결 핸들입니다. *HDBC* 를 입력 합니다.|

## <a name="remarks"></a>설명

데이터 원본은 일부 DBMS (데이터베이스 관리 시스템)에서 호스트 되는 특정 데이터 인스턴스입니다. 예를 들면 Microsoft SQL Server, Microsoft Access, Borland dBASE, xBASE 등이 있습니다. 응용 프로그램에서 한 번에 하나 이상의 개체를 활성화할 수 있습니다 `CDatabase` .

> [!NOTE]
> ODBC (Open Database Connectivity) 클래스 대신 DAO (Data Access Objects) 클래스를 사용 하 여 작업 하는 경우 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 클래스를 대신 사용 합니다. 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

를 사용 하려면 `CDatabase` 개체를 생성 하 `CDatabase` 고 해당 `OpenEx` 멤버 함수를 호출 합니다. 그러면 연결이 열립니다. 그런 다음 연결 된 데이터 원본에서 작동 하는 개체를 생성 하는 경우 `CRecordset` 해당 개체에 대 한 포인터를 레코드 집합 생성자에 전달 `CDatabase` 합니다. 연결 사용을 마치면 멤버 함수를 호출 하 `Close` 고 개체를 삭제 `CDatabase` 합니다. `Close` 이전에 닫지 않은 레코드 집합을 모두 닫습니다.

에 대 한 자세한 내용은 `CDatabase` [데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md) 및 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a> CDatabase:: BeginTrans

연결 된 데이터 소스를 사용 하 여 트랜잭션을 시작 하려면이 멤버 함수를 호출 합니다.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>반환 값

호출에 성공 하 고 변경 내용을 수동으로 커밋하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

트랜잭션은 `AddNew` `Edit` 개체의,, `Delete` 및 `Update` 멤버 함수에 대 한 하나 이상의 호출로 구성 됩니다 `CRecordset` . 트랜잭션을 시작 하기 전에 `CDatabase` 개체가 `OpenEx` 또는 멤버 함수를 호출 하 여 데이터 소스에 이미 연결 되어 있어야 합니다 `Open` . 트랜잭션을 종료 하려면 [CommitTrans](#committrans) 를 호출 하 여 데이터 원본에 대 한 모든 변경 내용을 적용 하 고 (이를 수행 하는 경우) [Rollback](#rollback) 을 호출 하 여 전체 트랜잭션을 중단 합니다. `BeginTrans`트랜잭션과 관련 된 레코드 집합을 열고 가능한 한 실제 업데이트 작업에 가까운 후에를 호출 합니다.

> [!CAUTION]
> ODBC 드라이버에 따라를 호출 하기 전에 레코드 집합을 열면를 `BeginTrans` 호출할 때 문제가 발생할 수 있습니다 `Rollback` . 사용 중인 특정 드라이버를 확인 해야 합니다. 예를 들어 Microsoft ODBC Desktop Driver Pack 3.0에 포함 된 Microsoft Access 드라이버를 사용 하는 경우에는 커서가 열려 있는 데이터베이스에서 트랜잭션을 시작 하지 않아야 하는 Jet 데이터베이스 엔진의 요구 사항을 고려해 야 합니다. MFC 데이터베이스 클래스에서 열린 커서는 열린 개체를 의미 `CRecordset` 합니다. 자세한 내용은 [Technical Note 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)을 참조 하세요.

`BeginTrans` 는 요청한 동시성 및 데이터 원본의 기능에 따라 서버에서 데이터 레코드를 잠글 수도 있습니다. 데이터를 잠그는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 잠금 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)문서를 참조 하세요.

사용자 정의 트랜잭션은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서에 설명 되어 있습니다.

`BeginTrans` 트랜잭션 시퀀스를 롤백할 수 있는 상태 (역방향)를 설정 합니다. 롤백을 위한 새 상태를 설정 하려면 현재 트랜잭션을 커밋한 다음를 `BeginTrans` 다시 호출 합니다.

> [!CAUTION]
> `BeginTrans`또는를 호출 하지 않고를 다시 호출 `CommitTrans` `Rollback` 하면 오류가 발생 합니다.

[Cantransact](#cantransact) 함수를 호출 하 여 드라이버가 지정 된 데이터베이스에 대 한 트랜잭션을 지원 하는지 여부를 확인 합니다. 또한 [GetCursorCommitBehavior](#getcursorcommitbehavior) 및 [GetCursorRollbackBehavior](#getcursorrollbackbehavior) 를 호출 하 여 커서 유지를 지원 하는지 확인 해야 합니다.

트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

  [트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)문서를 참조 하세요.

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a> CDatabase:: BindParameters

`BindParameters` [CDatabase:: executesql](#executesql)을 호출 하기 전에 매개 변수를 바인딩해야 하는 경우를 재정의 합니다.

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>매개 변수

*hstmt*<br/>
매개 변수를 바인딩할 ODBC 문 핸들입니다.

### <a name="remarks"></a>설명

이 방법은 저장 프로시저의 결과 집합이 필요 하지 않은 경우에 유용 합니다.

재정의에서 `SQLBindParameters` 및 관련 ODBC 함수를 호출 하 여 매개 변수를 바인딩합니다. MFC는를 호출 하기 전에 재정의를 호출 `ExecuteSQL` 합니다. 를 호출할 필요가 없습니다 .를 `SQLPrepare` `ExecuteSQL` 호출 `SQLExecDirect` 하 고 한 번만 사용 되는 *hstmt* 를 소멸 시킵니다.

## <a name="cdatabasecancel"></a><a name="cancel"></a> CDatabase:: Cancel

이 멤버 함수를 호출 하 여 데이터 소스에서 진행 중인 비동기 작업이 나 두 번째 스레드의 프로세스를 취소 하도록 요청 합니다.

```cpp
void Cancel();
```

### <a name="remarks"></a>설명

MFC ODBC 클래스는 더 이상 비동기 처리를 사용 하지 않습니다. 비동기 작업을 수행 하려면 ODBC API 함수 [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)을 직접 호출 해야 합니다. 자세한 내용은 [비동기 실행](/sql/odbc/reference/develop-app/asynchronous-execution)을 참조 하세요.

## <a name="cdatabasecantransact"></a><a name="cantransact"></a> CDatabase:: CanTransact

데이터베이스가 트랜잭션을 허용 하는지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>반환 값

이 개체를 사용 하는 레코드 집합에서 트랜잭션을 허용 하면 0이 아니고 `CDatabase` , 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a> CDatabase:: CanUpdate

이 멤버 함수를 호출 하 여 개체가 업데이트를 허용 하는지 여부를 확인 `CDatabase` 합니다.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>반환 값

개체에서 업데이트를 허용 하는 경우 0이 아니고, 그렇지 않으면 0이 고 `CDatabase` , 그렇지 않으면 개체를 열 때 *BREADONLY* 에 TRUE를 전달 `CDatabase` 했거나 데이터 원본 자체를 읽기 전용으로 표시 합니다. SQL_DATASOURCE_READ_ONLY에 대 한 ODBC API 함수를 호출 하면 "y"가 반환 되는 경우 데이터 원본은 읽기 전용입니다 `SQLGetInfo` .

### <a name="remarks"></a>설명

모든 드라이버가 업데이트를 지 원하는 것은 아닙니다.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a> CDatabase:: CDatabase

`CDatabase` 개체를 생성합니다.

```
CDatabase();
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 해당 `OpenEx` 또는 `Open` 멤버 함수를 호출 하 여 지정 된 데이터 소스에 대 한 연결을 설정 해야 합니다.

문서 클래스에 개체를 포함 하는 것이 편리할 수 있습니다 `CDatabase` .

### <a name="example"></a>예제

이 예제에서는 `CDatabase` 파생 클래스에서를 사용 하는 방법을 보여 줍니다 `CDocument` .

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a> CDatabase:: Close

데이터 원본에서 연결을 끊으려면이 멤버 함수를 호출 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

`CDatabase`이 멤버 함수를 호출 하기 전에 개체와 연결 된 모든 레코드 집합을 닫아야 합니다. `Close`는 개체를 삭제 하지 않으므로 `CDatabase` 동일한 데이터 원본이 나 다른 데이터 원본에 대 한 새 연결을 열어 개체를 다시 사용할 수 있습니다.

`AddNew`데이터베이스를 사용 하는 보류 중인 모든 또는 `Edit` 레코드 집합의 문이 취소 되 고 보류 중인 모든 트랜잭션이 롤백됩니다. 개체에 종속 된 모든 레코드 집합 `CDatabase` 은 정의 되지 않은 상태로 유지 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a> CDatabase:: CommitTrans

트랜잭션을 완료할 때이 멤버 함수를 호출 합니다.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>반환 값

업데이트가 성공적으로 커밋되면 0이 아닙니다. 그렇지 않으면 0입니다. `CommitTrans`가 실패 하면 데이터 원본의 상태는 정의 되지 않습니다. 데이터를 확인 하 여 상태를 확인 해야 합니다.

### <a name="remarks"></a>설명

트랜잭션은 `AddNew` `Edit` `Delete` `Update` `CRecordset` [BeginTrans](#begintrans) 멤버 함수를 호출 하 여 시작 된 개체의,, 및 멤버 함수에 대 한 일련의 호출로 구성 됩니다. `CommitTrans` 트랜잭션을 커밋합니다. 기본적으로 업데이트는 즉시 커밋됩니다. `BeginTrans` 를 호출 하면가 호출 될 때까지 업데이트 커밋이 지연 됩니다 `CommitTrans` .

을 호출 하 `CommitTrans` 여 트랜잭션을 종료할 때까지 [Rollback](#rollback) 멤버 함수를 호출 하 여 트랜잭션을 중단 하 고 데이터 원본을 원래 상태로 유지할 수 있습니다. 새 트랜잭션을 시작 하려면를 다시 호출 `BeginTrans` 합니다.

트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

  [트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)문서를 참조 하세요.

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a> CDatabase:: ExecuteSQL

SQL 명령을 직접 실행 해야 하는 경우이 멤버 함수를 호출 합니다.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>매개 변수

*lpszSQL*<br/>
실행할 유효한 SQL 명령을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다. [CString](../../atl-mfc-shared/reference/cstringt-class.md)을 전달할 수 있습니다.

### <a name="remarks"></a>설명

명령을 null로 종료 되는 문자열로 만듭니다. `ExecuteSQL` 데이터 레코드를 반환 하지 않습니다. 레코드에 대해 작업을 수행 하려는 경우에는 레코드 집합 개체를 대신 사용 합니다.

데이터 원본에 대 한 대부분의 명령은 데이터를 선택 하 고, 새 레코드를 삽입 하 고, 레코드를 삭제 하 고, 레코드를 편집 하는 명령을 지 원하는 레코드 집합 개체를 통해 실행 됩니다. 그러나 데이터베이스 클래스에서 모든 ODBC 기능을 직접 지원 하지는 않으므로를 사용 하 여 직접 SQL 호출을 수행 해야 하는 경우가 있을 수 있습니다 `ExecuteSQL` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a> CDatabase:: Get책갈피 지 속성

특정 작업 후 레코드 집합 개체에 책갈피가 유지되는지 확인하려면 이 멤버 함수를 호출합니다.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>반환 값

레코드 집합 개체에 책갈피를 유지하는 작업을 식별하는 비트 마스크입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

예를 들어 `CRecordset::GetBookmark`와 `CRecordset::Requery`를 차례로 호출하면 `GetBookmark`에서 가져온 책갈피가 더 이상 유효하지 않게 될 수 있습니다. `GetBookmarkPersistence`를 호출하기 전에 `CRecordset::SetBookmark`를 호출해야 합니다.

다음 테이블에는 `GetBookmarkPersistence`의 반환 값에 대해 결합할 수 있는 비트 마스크 값이 나와 있습니다.

|비트 마스크 값|책갈피 유지|
|-------------------|--------------------------|
|SQL_BP_CLOSE|작업 후 책갈피를 사용할 수 `Requery` 있습니다.|
|SQL_BP_DELETE|행에 대 한 작업을 수행한 후에는 행에 대 한 책갈피가 유효 합니다 `Delete` .|
|SQL_BP_DROP|작업 후 책갈피를 사용할 수 `Close` 있습니다.|
|SQL_BP_SCROLL|책갈피는 모든 작업 후에 유효 `Move` 합니다. 따라서 `CRecordset::CanBookmark`에서 반환되는 책갈피가 레코드 집합에서 지원되는지를 쉽게 파악할 수 있습니다.|
|SQL_BP_TRANSACTION|트랜잭션이 커밋되거나 롤백된 후에 책갈피가 유효합니다.|
|SQL_BP_UPDATE|행에 대 한 작업을 수행한 후에는 행에 대 한 책갈피가 유효 합니다 `Update` .|
|SQL_BP_OTHER_HSTMT|레코드 집합 개체 하나와 연결된 책갈피가 두 번째 레코드 집합에서도 유효합니다.|

이 반환 값에 대 한 자세한 내용은 Windows SDK의 ODBC API 함수를 참조 하십시오 `SQLGetInfo` . 책갈피에 대 한 자세한 내용은 [레코드 집합: 책갈피 및 절대 위치 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요.

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a> CDatabase:: GetConnect

이 멤버 함수를 호출 하 여 또는를 호출 하는 동안 사용 된 연결 문자열을 검색 `OpenEx` 하거나 `Open` 개체를 `CDatabase` 데이터 소스에 연결 합니다.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>반환 값

**`const`** 또는가 호출 된 경우 연결 문자열을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) `OpenEx` 이거나 `Open` , 그렇지 않으면 빈 문자열입니다.

### <a name="remarks"></a>설명

연결 문자열을 만드는 방법에 대 한 설명은 [CDatabase:: Open](#open) 을 참조 하세요.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a> CDatabase:: GetCursorCommitBehavior

이 멤버 함수를 호출 하 여 열려 있는 레코드 집합 개체에서 [CommitTrans](#committrans) 연산이 커서에 주는 영향을 확인 합니다.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>반환 값

열린 레코드 집합 개체에 대 한 트랜잭션의 효과를 나타내는 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

다음 표에서는에 대 한 가능한 반환 값 `GetCursorCommitBehavior` 과 열려 있는 레코드 집합에 해당 하는 영향을 보여 줍니다.

|반환 값|CRecordset 개체에 대 한 영향|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`트랜잭션 커밋 바로 다음에 호출 합니다.|
|SQL_CB_DELETE|`CRecordset::Close`트랜잭션 커밋 바로 다음에 호출 합니다.|
|SQL_CB_PRESERVE|작업을 정상적으로 진행 `CRecordset` 합니다.|

이 반환 값에 대 한 자세한 내용은 Windows SDK의 ODBC API 함수를 참조 하십시오 `SQLGetInfo` . 트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a> CDatabase:: GetCursorRollbackBehavior

이 멤버 함수를 호출 하 여 열려 있는 레코드 집합 개체에서 [롤백](#rollback) 작업이 커서에 주는 영향을 확인 합니다.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>반환 값

열린 레코드 집합 개체에 대 한 트랜잭션의 효과를 나타내는 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

다음 표에서는에 대 한 가능한 반환 값 `GetCursorRollbackBehavior` 과 열려 있는 레코드 집합에 해당 하는 영향을 보여 줍니다.

|반환 값|CRecordset 개체에 대 한 영향|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`트랜잭션 롤백 바로 다음에 호출 합니다.|
|SQL_CB_DELETE|`CRecordset::Close`트랜잭션 롤백 바로 다음에 호출 합니다.|
|SQL_CB_PRESERVE|작업을 정상적으로 진행 `CRecordset` 합니다.|

이 반환 값에 대 한 자세한 내용은 Windows SDK의 ODBC API 함수를 참조 하십시오 `SQLGetInfo` . 트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a> CDatabase:: GetDatabaseName

이 멤버 함수를 호출 하 여 현재 연결 된 데이터베이스의 이름을 검색 합니다 (데이터 소스가 "database" 라는 명명 된 개체를 정의 하는 경우).

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 데이터베이스 이름이 포함 된 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 그렇지 않으면 빈 `CString` 입니다.

### <a name="remarks"></a>설명

이는 또는 호출에 지정 된 DSN (데이터 원본 이름)과 다릅니다 `OpenEx` `Open` . 반환 되는 항목은 `GetDatabaseName` ODBC에 따라 다릅니다. 일반적으로 데이터베이스는 테이블의 컬렉션입니다. 이 엔터티에 이름이 있으면에서 `GetDatabaseName` 반환 합니다.

예를 들어 제목에이 이름을 표시 하려는 경우가 있습니다. ODBC에서 이름을 검색 하는 동안 오류가 발생 하는 경우는 `GetDatabaseName` 빈을 반환 `CString` 합니다.

## <a name="cdatabaseisopen"></a><a name="isopen"></a> CDatabase:: IsOpen

이 멤버 함수를 호출 하 여 `CDatabase` 개체가 현재 데이터 소스에 연결 되어 있는지 여부를 확인 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

`CDatabase`개체가 현재 연결 되어 있으면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a> CDatabase:: m_hdbc

ODBC 데이터 원본 연결에 대 한 공용 핸들 ("연결 핸들")을 포함 합니다.

### <a name="remarks"></a>설명

일반적으로이 멤버 변수에 직접 액세스할 필요는 없습니다. 대신, 또는를 호출할 때 프레임 워크에서 핸들을 할당 합니다 `OpenEx` `Open` . 프레임 워크는 개체에서 연산자를 호출할 때 핸들의 할당을 취소 합니다 **`delete`** `CDatabase` . `Close`멤버 함수는 핸들의 할당을 취소 하지 않습니다.

그러나 경우에 따라 핸들을 직접 사용 해야 할 수도 있습니다. 예를 들어 클래스를 통하지 않고 직접 ODBC API 함수를 호출 해야 하는 경우 `CDatabase` 매개 변수로 전달 하는 연결 핸들이 필요할 수 있습니다. 아래 코드 예제를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a> CDatabase:: OnSetOptions

멤버 함수를 사용 하 여 SQL 문을 직접 실행 하는 경우 프레임 워크는이 멤버 함수를 호출 `ExecuteSQL` 합니다.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>매개 변수

*hstmt*<br/>
옵션이 설정 되는 ODBC 문 핸들입니다.

### <a name="remarks"></a>설명

`CRecordset::OnSetOptions` 는 또한이 멤버 함수를 호출 합니다.

`OnSetOptions` 로그인 제한 시간 값을 설정 합니다. 및 멤버 함수에 대 한 이전 호출이 있으면 `SetQueryTimeout` 에서 현재 값을 반영 하 고, `OnSetOptions` 그렇지 않으면 기본값을 설정 합니다.

> [!NOTE]
> MFC 4.2 이전에 `OnSetOptions` 는 처리 모드를 snychronous 또는 비동기로 설정 합니다. MFC 4.2부터 모든 작업은 동기적으로 수행 됩니다. 비동기 작업을 수행 하려면 ODBC API 함수에 대 한 직접 호출을 수행 해야 합니다 `SQLSetPos` .

`OnSetOptions`제한 시간 값을 변경 하기 위해를 재정의할 필요가 없습니다. 대신, 쿼리 제한 시간 값을 사용자 지정 하려면 `SetQueryTimeout` 레코드 집합을 만들기 전에를 호출 하 고, `OnSetOptions` 는 새 값을 사용 합니다. 설정 된 값은 모든 레코드 집합에 대 한 후속 작업 또는 직접 SQL 호출에 적용 됩니다.

`OnSetOptions`추가 옵션을 설정 하려면를 재정의 합니다. 재정의는 `OnSetOptions` ODBC API 함수를 호출 하기 전이나 후에 기본 클래스를 호출 해야 합니다 `SQLSetStmtOption` . 의 프레임 워크의 기본 구현에 설명 된 메서드를 따릅니다 `OnSetOptions` .

## <a name="cdatabaseopen"></a><a name="open"></a> CDatabase:: Open

이 멤버 함수를 호출 하 여 새로 생성 된 개체를 초기화 `CDatabase` 합니다.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszDSN*<br/>
ODBC 관리자 프로그램을 통해 ODBC에 등록 된 이름인 데이터 원본 이름을 지정 합니다. DSN 값이 *lpszConnect* 에 지정 된 경우 ("dsn = \<data-source> " 형식) *lpszDSN* 에서 다시 지정 하면 안 됩니다. 이 경우 *lpszDSN* 는 NULL 이어야 합니다. 그렇지 않으면 사용자가 데이터 원본을 선택할 수 있는 데이터 원본 대화 상자를 제공 하려는 경우 NULL을 전달할 수 있습니다. 자세한 내용은 설명 부분을 참조 하십시오.

*bExclusive*<br/>
이 버전의 클래스 라이브러리에서는 지원 되지 않습니다. 현재이 매개 변수가 TRUE 이면 어설션이 실패 합니다. 데이터 원본은 항상 공유 (제외)로 열립니다.

*bReadOnly*<br/>
연결을 읽기 전용으로 설정 하 고 데이터 원본에 대 한 업데이트를 금지 하려면 TRUE입니다. 모든 종속 레코드 집합은이 특성을 상속 합니다. 기본값은 FALSE입니다.

*lpszConnect*<br/>
연결 문자열을 지정 합니다. 연결 문자열은 데이터 원본 이름, 데이터 원본에서 유효한 사용자 ID, 사용자 인증 문자열 (암호, 데이터 원본에 필요한 경우) 및 기타 정보를 비롯 한 정보를 연결 합니다. 전체 연결 문자열 앞에는 "ODBC;" 문자열이와 야 합니다. (대문자 또는 소문자). "ODBC;" 문자열은 ODBC 데이터 원본에 대 한 연결을 나타내는 데 사용 됩니다. 이후 버전의 클래스 라이브러리에서는 비 ODBC 데이터 원본을 지원할 수 있는 경우에는이 기능이 상향 호환성을 위한 것입니다.

*bUseCursorLib*<br/>
ODBC 커서 라이브러리 DLL을 로드 하려면 TRUE로 설정 합니다. 커서 라이브러리는 기본 ODBC 드라이버의 일부 기능을 마스크 하 여 다이너셋을 사용 하지 않는 것을 효과적으로 방지 합니다 (드라이버에서 지 원하는 경우). 커서 라이브러리가 로드 된 경우에만 지원 되는 커서는 정적 스냅숏과 앞 으로만 이동 가능한 커서입니다. 기본값은 TRUE입니다. 에서 파생 하지 않고 직접 레코드 집합 개체를 만들 계획인 경우에는 `CRecordset` 커서 라이브러리를 로드 하면 안 됩니다.

### <a name="return-value"></a>반환 값

연결이 설정 되 면 0이 아닌 값으로 설정 됩니다. 그렇지 않으면 사용자가 추가 연결 정보를 요구 하는 대화 상자가 표시 되 면 취소를 선택 하는 경우 0입니다. 다른 모든 경우에는 프레임 워크에서 예외를 throw 합니다.

### <a name="remarks"></a>설명

데이터베이스 개체를 사용 하 여 레코드 집합 개체를 생성 하려면 먼저 데이터베이스 개체를 초기화 해야 합니다.

> [!NOTE]
> [Microsoft.office.interop.visio.documents.openex](#openex) 멤버 함수를 호출 하는 것이 데이터 원본에 연결 하 고 데이터베이스 개체를 초기화 하는 기본 방법입니다.

호출의 매개 변수에 `Open` 연결을 설정 하는 데 충분 한 정보가 포함 되어 있지 않은 경우 ODBC 드라이버는 사용자 로부터 필요한 정보를 가져올 수 있는 대화 상자를 엽니다. 를 호출할 때 `Open` 연결 문자열 *lpszConnect* 는 전용으로 개체에 저장 되며 `CDatabase` [getconnect](#getconnect) 멤버 함수를 호출 하 여 사용할 수 있습니다.

원할 경우를 호출 하기 전에 사용자에 게 암호와 같은 정보를 가져오기 위해 자신의 대화 상자를 연 `Open` 다음 해당 정보를 전달 하는 연결 문자열에 추가할 수 있습니다 `Open` . 또는 다음에 응용 프로그램에서 개체를 호출할 때 다시 사용할 수 있도록 전달 하는 연결 문자열을 저장 하려고 할 수 있습니다 `Open` `CDatabase` .

여러 수준의 로그인 권한 부여 (각각 다른 개체의 경우)에 대 한 연결 문자열을 사용 `CDatabase` 하거나 다른 데이터 원본 관련 정보를 전달할 수도 있습니다. 연결 문자열에 대 한 자세한 내용은 Windows SDK의 5 장을 참조 하십시오.

예를 들어 DBMS 호스트를 사용할 수 없는 경우 연결 시도가 시간 초과 될 수 있습니다. 연결 시도가 실패 하면이 `Open` throw `CDBException` 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a> CDatabase:: Microsoft.office.interop.visio.documents.openex

이 멤버 함수를 호출 하 여 새로 생성 된 개체를 초기화 `CDatabase` 합니다.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>매개 변수

*lpszConnectString*<br/>
ODBC 연결 문자열을 지정 합니다. 여기에는 사용자 ID 및 암호와 같은 기타 선택적 정보 뿐만 아니라 데이터 원본 이름도 포함 됩니다. 예: "DSN = SQLServer_Source; UID = SA; PWD = abc123 "은 가능한 연결 문자열입니다. *LpszConnectString* 에 대해 NULL을 전달 하면 데이터 원본 대화 상자에 사용자에 게 데이터 원본을 선택 하 라는 메시지가 표시 됩니다.

*dwOptions*<br/>
다음 값의 조합을 지정 하는 비트 마스크입니다. 기본값은 0입니다. 즉, 데이터베이스가 쓰기 권한으로 공유 되는 것으로 열리며, ODBC 커서 라이브러리 DLL이 로드 되지 않고, 연결을 설정 하는 데 충분 한 정보가 없는 경우에만 ODBC 연결 대화 상자가 표시 됩니다.

- `CDatabase::openExclusive` 이 버전의 클래스 라이브러리에서는 지원 되지 않습니다. 데이터 원본은 항상 공유 (제외)로 열립니다. 현재이 옵션을 지정 하면 어설션이 실패 합니다.

- `CDatabase::openReadOnly` 데이터 원본을 읽기 전용으로 엽니다.

- `CDatabase::useCursorLib` ODBC 커서 라이브러리 DLL을 로드 합니다. 커서 라이브러리는 기본 ODBC 드라이버의 일부 기능을 마스크 하 여 다이너셋을 사용 하지 않는 것을 효과적으로 방지 합니다 (드라이버에서 지 원하는 경우). 커서 라이브러리가 로드 된 경우에만 지원 되는 커서는 정적 스냅숏과 앞 으로만 이동 가능한 커서입니다. 에서 파생 하지 않고 직접 레코드 집합 개체를 만들 계획인 경우에는 `CRecordset` 커서 라이브러리를 로드 하면 안 됩니다.

- `CDatabase::noOdbcDialog` 충분 한 연결 정보가 제공 되는지 여부에 관계 없이 ODBC 연결 대화 상자를 표시 하지 않습니다.

- `CDatabase::forceOdbcDialog` 항상 ODBC 연결 대화 상자를 표시 합니다.

### <a name="return-value"></a>반환 값

연결이 설정 되 면 0이 아닌 값으로 설정 됩니다. 그렇지 않으면 사용자가 추가 연결 정보를 요구 하는 대화 상자가 표시 되 면 취소를 선택 하는 경우 0입니다. 다른 모든 경우에는 프레임 워크에서 예외를 throw 합니다.

### <a name="remarks"></a>설명

데이터베이스 개체를 사용 하 여 레코드 집합 개체를 생성 하려면 먼저 데이터베이스 개체를 초기화 해야 합니다.

호출의 *lpszConnectString* 매개 변수에 `OpenEx` 연결을 설정 하는 데 충분 한 정보가 포함 되어 있지 않으면 ODBC 드라이버는 사용자가 설정 하지 않았거나 `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` *dwOptions* 매개 변수에서 필요한 정보를 가져올 수 있는 대화 상자를 엽니다. 를 호출할 때 `OpenEx` 연결 문자열 *lpszConnectString* 는 전용으로 개체에 저장 되며 `CDatabase` [getconnect](#getconnect) 멤버 함수를 호출 하 여 사용할 수 있습니다.

원할 경우를 호출 하기 전에 사용자의 대화 상자를 열고 `OpenEx` 암호와 같은 사용자 정보를 가져온 다음에 전달 하는 연결 문자열에 해당 정보를 추가할 수 있습니다 `OpenEx` . 또는 다음에 응용 프로그램에서 개체를 호출할 때 다시 사용할 수 있도록 전달 하는 연결 문자열을 저장 하려고 할 수 있습니다 `OpenEx` `CDatabase` .

여러 수준의 로그인 권한 부여 (각각 다른 개체의 경우)에 대 한 연결 문자열을 사용 `CDatabase` 하거나 다른 데이터 원본 관련 정보를 전달할 수도 있습니다. 연결 문자열에 대 한 자세한 내용은 *ODBC 프로그래머 참조* 의 6 장을 참조 하세요.

예를 들어 DBMS 호스트를 사용할 수 없는 경우 연결 시도가 시간 초과 될 수 있습니다. 연결 시도가 실패 하면이 `OpenEx` throw `CDBException` 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a> CDatabase:: Rollback

트랜잭션 중에 변경 된 내용을 취소 하려면이 멤버 함수를 호출 합니다.

```
BOOL Rollback();
```

### <a name="return-value"></a>반환 값

트랜잭션이 성공적으로 반전 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다. 호출에 `Rollback` 실패 하면 데이터 원본 및 트랜잭션 상태가 정의 되지 않습니다. `Rollback`가 0을 반환 하는 경우 데이터 소스를 확인 하 여 상태를 확인 해야 합니다.

### <a name="remarks"></a>설명

`CRecordset` `AddNew` `Edit` `Delete` 마지막 BeginTrans 이후 실행 된 모든,, 및 `Update` 호출은 [](#begintrans) 해당 호출 시 존재 했던 상태로 롤백됩니다.

를 호출한 후에는 `Rollback` 트랜잭션이 초과 되므로 `BeginTrans` 다른 트랜잭션에 대해를 다시 호출 해야 합니다. 를 호출 하기 전에 현재 레코드는 `BeginTrans` 이후 현재 레코드가 됩니다 `Rollback` .

롤백 후에는 롤백이 이전에 있던 레코드가 최신 상태로 유지 됩니다. 롤백 후의 레코드 집합과 데이터 원본의 상태에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

  [트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)문서를 참조 하세요.

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a> CDatabase:: SetLoginTimeout

또는를 호출 하기 전에이 멤버 함수를 호출 `OpenEx` `Open` 하 여 시도 된 데이터 소스 연결의 제한 시간이 초과 되기 전까지 허용 되는 기본 시간 (초)을 재정의 합니다.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>매개 변수

*dwSeconds*<br/>
연결 시도 시간이 초과 되기 전까지 허용 되는 시간 (초)입니다.

### <a name="remarks"></a>설명

예를 들어 DBMS를 사용할 수 없는 경우 연결 시도가 시간 초과 될 수 있습니다. `SetLoginTimeout`초기화 되지 않은 개체를 만든 후 `CDatabase` 또는를 호출 하기 전에를 호출 `OpenEx` `Open` 합니다.

로그인 시간 제한의 기본값은 15 초입니다. 모든 데이터 원본이 로그인 제한 시간 값을 지정 하는 기능을 지원 하지는 않습니다. 데이터 원본에서 시간 제한을 지원 하지 않는 경우 추적 출력을 가져오지만 예외는 발생 하지 않습니다. 값 0은 "infinite"를 의미 합니다.

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a> CDatabase:: SetQueryTimeout

연결 된 데이터 소스에 대 한 후속 작업이 시간 초과 될 때까지 허용 되는 기본 시간 (초)을 재정의 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>매개 변수

*dwSeconds*<br/>
쿼리 시도 시간이 초과 될 때까지 허용 되는 시간 (초)입니다.

### <a name="remarks"></a>설명

네트워크 액세스 문제, 과도 한 쿼리 처리 시간 등으로 인해 작업 시간이 초과 될 수 있습니다. `SetQueryTimeout`레코드 집합을 열기 전이나 레코드 집합의, 또는 멤버 함수를 호출 하기 전에를 호출 하 여 `AddNew` `Update` `Delete` 쿼리 제한 시간 값을 변경 합니다. 설정은 `Open` `AddNew` `Update` `Delete` 이 개체와 연결 된 모든 레코드 집합에 대 한 모든 후속,, 및 호출에 영향을 줍니다 `CDatabase` . 열을 연 후 레코드 집합에 대 한 쿼리 제한 시간 값을 변경 해도 레코드 집합에 대 한 값은 변경 되지 않습니다. 예를 들어 후속 `Move` 작업에서는 새 값을 사용 하지 않습니다.

쿼리 시간 제한의 기본값은 15 초입니다. 모든 데이터 원본에서 쿼리 제한 시간 값을 설정 하는 기능을 지원 하지는 않습니다. 쿼리 제한 시간 값을 0으로 설정 하면 시간 제한이 발생 하지 않습니다. 데이터 원본과의 통신이 응답 하지 않을 수 있습니다. 이 동작은 개발 중에 유용할 수 있습니다. 데이터 원본에서 시간 제한을 지원 하지 않는 경우 추적 출력을 가져오지만 예외는 발생 하지 않습니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
