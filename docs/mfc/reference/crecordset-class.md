---
title: CRecordset 클래스
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78871656"
---
# <a name="crecordset-class"></a>CRecordset 클래스

데이터 소스에서 선택한 레코드 집합을 나타냅니다.

## <a name="syntax"></a>구문

```
class CRecordset : public CObject
```

## <a name="members"></a>구성원

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CRecordset:: CRecordset](#crecordset)|`CRecordset` 개체를 생성합니다. 파생 클래스에서이를 호출 하는 생성자를 제공 해야 합니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|새 레코드를 추가할 준비를 합니다. `Update`를 호출 하 여 더하기를 완료 합니다.|
|[CRecordset:: CanAppend](#canappend)|`AddNew` 멤버 함수를 통해 레코드 집합에 새 레코드를 추가할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: CanBookmark](#canbookmark)|레코드 집합에서 책갈피를 지 원하는 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: Cancel](#cancel)|비동기 작업 또는 두 번째 스레드에서 프로세스를 취소 합니다.|
|[CRecordset:: CancelUpdate](#cancelupdate)|`AddNew` 또는 `Edit` 작업으로 인해 보류 중인 모든 업데이트를 취소 합니다.|
|[CRecordset:: CanRestart](#canrestart)|`Requery`를 호출 하 여 레코드 집합의 쿼리를 다시 실행할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: CanScroll](#canscroll)|레코드를 스크롤할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: CanTransact](#cantransact)|데이터 원본이 트랜잭션을 지원 하면 0이 아닌 값을 반환 합니다.|
|[CRecordset:: CanUpdate](#canupdate)|레코드 집합을 업데이트할 수 있는 경우 0이 아닌 값을 반환 합니다. 레코드를 추가, 업데이트 또는 삭제할 수 있습니다.|
|[CRecordset:: CheckRowsetError](#checkrowseterror)|레코드를 인출 하는 동안 생성 된 오류를 처리 하기 위해 호출 됩니다.|
|[CRecordset:: Close](#close)|레코드 집합과 연결 된 ODBC HSTMT를 닫습니다.|
|[CRecordset::D e)](#delete)|레코드 집합에서 현재 레코드를 삭제 합니다. 삭제 한 후에는 다른 레코드로 명시적으로 스크롤해야 합니다.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|데이터 원본에서 레코드 집합으로 데이터의 대량 행을 교환 하기 위해 호출 됩니다. 대량 RFX (대량 레코드 필드 교환)를 구현 합니다.|
|[CRecordset::DoFieldExchange](#dofieldexchange)|레코드 집합의 필드 데이터 멤버와 데이터 소스에 있는 해당 레코드 사이에서 데이터를 양방향으로 교환 하기 위해 호출 됩니다. RFX (레코드 필드 교환)를 구현 합니다.|
|[CRecordset:: Edit](#edit)|현재 레코드에 대 한 변경 내용을 준비 합니다. `Update`를 호출 하 여 편집을 완료 합니다.|
|[CRecordset:: FlushResultSet](#flushresultset)|미리 정의 된 쿼리를 사용 하는 경우 검색 될 다른 결과 집합이 있는 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: GetBookmark](#getbookmark)|레코드의 책갈피 값을 매개 변수 개체에 할당 합니다.|
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|기본 연결 문자열을 가져오기 위해 호출 됩니다.|
|[CRecordset:: GetDefaultSQL](#getdefaultsql)|실행할 기본 SQL 문자열을 가져오기 위해 호출 됩니다.|
|[CRecordset:: GetFieldValue](#getfieldvalue)|레코드 집합에 있는 필드의 값을 반환 합니다.|
|[CRecordset:: GetODBCFieldCount](#getodbcfieldcount)|레코드 집합의 필드 수를 반환 합니다.|
|[CRecordset:: GetODBCFieldInfo](#getodbcfieldinfo)|레코드 집합의 필드에 대 한 특정 종류의 정보를 반환 합니다.|
|[CRecordset:: GetRecordCount](#getrecordcount)|레코드 집합의 레코드 수를 반환 합니다.|
|[CRecordset:: GetRowsetSize](#getrowsetsize)|단일 인출 중에 검색 하려는 레코드 수를 반환 합니다.|
|[CRecordset:: GetRowsFetched](#getrowsfetched)|인출 하는 동안 검색 된 행의 실제 수를 반환 합니다.|
|[CRecordset:: GetRowStatus](#getrowstatus)|인출 후 행의 상태를 반환 합니다.|
|[CRecordset:: GetSQL](#getsql)|레코드 집합에 대 한 레코드를 선택 하는 데 사용 되는 SQL 문자열을 가져옵니다.|
|[CRecordset:: GetStatus](#getstatus)|레코드 집합의 상태를 가져옵니다. 현재 레코드의 인덱스와 마지막 레코드 수를 가져왔는지 여부를 가져옵니다.|
|[CRecordset:: GetTableName](#gettablename)|레코드 집합의 기반이 되는 테이블의 이름을 가져옵니다.|
|[CRecordset:: IsBOF](#isbof)|레코드 집합이 첫 번째 레코드 앞에 배치 되 면 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.|
|[CRecordset:: IsDeleted](#isdeleted)|레코드 집합이 삭제 된 레코드에 배치 되 면 0이 아닌 값을 반환 합니다.|
|[CRecordset:: IsEOF](#iseof)|레코드 집합이 마지막 레코드 뒤에 배치 된 경우 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.|
|[CRecordset:: IsFieldDirty](#isfielddirty)|현재 레코드의 지정 된 필드가 변경 된 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: IsFieldNull](#isfieldnull)|현재 레코드의 지정 된 필드가 null (값이 없는 경우) 인 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: IsFieldNullable](#isfieldnullable)|현재 레코드의 지정 된 필드를 null로 설정할 수 있으면 0이 아닌 값을 반환 합니다.|
|[CRecordset:: IsOpen](#isopen)|`Open` 이전에 호출 된 경우 0이 아닌 값을 반환 합니다.|
|[CRecordset:: Move](#move)|현재 레코드의 지정 된 레코드 수에 레코드 집합을 두 방향으로 배치 합니다.|
|[CRecordset:: MoveFirst](#movefirst)|레코드 집합의 첫 번째 레코드에 현재 레코드를 배치 합니다. 먼저 `IsBOF`를 테스트 합니다.|
|[CRecordset:: MoveLast](#movelast)|마지막 레코드 또는 마지막 행 집합에 현재 레코드를 배치 합니다. 먼저 `IsEOF`를 테스트 합니다.|
|[CRecordset:: MoveNext](#movenext)|다음 레코드 또는 다음 행 집합에 현재 레코드를 배치 합니다. 먼저 `IsEOF`를 테스트 합니다.|
|[CRecordset:: MovePrev](#moveprev)|이전 레코드나 이전 행 집합에 현재 레코드를 배치 합니다. 먼저 `IsBOF`를 테스트 합니다.|
|[CRecordset:: OnSetOptions](#onsetoptions)|지정 된 ODBC 문에 옵션 (선택에 사용 됨)을 설정 하기 위해 호출 됩니다.|
|[CRecordset:: OnSetUpdateOptions](#onsetupdateoptions)|지정 된 ODBC 문에 대해 옵션 (update에 사용 됨)을 설정 하기 위해 호출 됩니다.|
|[CRecordset:: Open](#open)|테이블을 검색 하거나 레코드 집합에서 나타내는 쿼리를 수행 하 여 레코드 집합을 엽니다.|
|[CRecordset:: RefreshRowset](#refreshrowset)|지정 된 행의 데이터와 상태를 새로 고칩니다.|
|[CRecordset:: Requery](#requery)|레코드 집합의 쿼리를 다시 실행 하 여 선택한 레코드를 새로 고칩니다.|
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|지정 된 레코드 번호에 해당 하는 레코드에 레코드 집합을 배치 합니다.|
|[CRecordset:: SetBookmark](#setbookmark)|책갈피에 지정 된 레코드에 레코드 집합을 배치 합니다.|
|[CRecordset:: SetFieldDirty](#setfielddirty)|현재 레코드에서 지정 된 필드를 변경 된 것으로 표시 합니다.|
|[CRecordset:: SetFieldNull](#setfieldnull)|현재 레코드에서 지정 된 필드의 값을 null (값 없음)으로 설정 합니다.|
|[CRecordset:: SetLockingMode](#setlockingmode)|잠금 모드를 "낙관적" 잠금 (기본값) 또는 "비관적" 잠금으로 설정 합니다. 업데이트를 위해 레코드를 잠그는 방법을 결정 합니다.|
|[CRecordset:: SetParamNull](#setparamnull)|지정 된 매개 변수를 값이 없는 null로 설정 합니다.|
|[CRecordset:: SetRowsetCursorPosition](#setrowsetcursorposition)|행 집합 내의 지정 된 행에 커서를 놓습니다.|
|[CRecordset:: SetRowsetSize](#setrowsetsize)|인출 하는 동안 검색 하려는 레코드 수를 지정 합니다.|
|[CRecordset:: Update](#update)|새 데이터 또는 편집 된 데이터를 데이터 원본에 저장 하 여 `AddNew` 또는 `Edit` 작업을 완료 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|속성|Description|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|레코드 집합에 대 한 ODBC 문 핸들을 포함 합니다. `HSTMT`.|
|[CRecordset:: m_nFields](#m_nfields)|레코드 집합의 필드 데이터 멤버 수를 포함 합니다. `UINT`.|
|[CRecordset:: m_nParams](#m_nparams)|레코드 집합의 매개 변수 데이터 멤버 수를 포함 합니다. `UINT`.|
|[CRecordset:: m_pDatabase](#m_pdatabase)|레코드 집합을 데이터 소스에 연결 하는 `CDatabase` 개체에 대 한 포인터를 포함 합니다.|
|[CRecordset:: m_strFilter](#m_strfilter)|구조적 쿼리 언어 (SQL) `WHERE` 절을 지정 하는 `CString`을 포함 합니다. 특정 조건을 충족 하는 레코드만 선택 하는 필터로 사용 됩니다.|
|[CRecordset:: m_strSort](#m_strsort)|SQL `ORDER BY` 절을 지정 하는 `CString`을 포함 합니다. 레코드를 정렬 하는 방법을 제어 하는 데 사용 됩니다.|

## <a name="remarks"></a> 주의

"레코드 집합" 이라고 하는 `CRecordset` 개체는 일반적으로 다이너셋과 스냅숏의 두 가지 형태로 사용 됩니다. 다이너셋은 다른 사용자가 수행한 데이터 업데이트와 동기화 된 상태를 유지 합니다. 스냅숏은 데이터의 정적 뷰입니다. 각 폼은 레코드 집합을 열 때 고정 된 레코드 집합을 나타내지만, 다이너셋의 레코드로 스크롤하면 나중에 다른 사용자나 응용 프로그램의 다른 레코드 집합에서 레코드에 대 한 변경 내용을 반영 합니다.

> [!NOTE]
>  ODBC (Open Database Connectivity) 클래스 대신 DAO (Data Access Objects) 클래스를 사용 하 여 작업 하는 경우 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 클래스를 대신 사용 합니다. 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

두 종류의 레코드 집합을 사용 하려면 일반적으로 `CRecordset`에서 응용 프로그램별 레코드 집합 클래스를 파생 시킵니다. 레코드 집합 데이터 원본에서 레코드를 선택 하 고 다음을 수행할 수 있습니다.

- 레코드를 스크롤합니다.

- 레코드를 업데이트 하 고 잠금 모드를 지정 합니다.

- 레코드 집합을 필터링 하 여 데이터 원본에서 사용할 수 있는 레코드를 제약 합니다.

- 레코드 집합을 정렬 합니다.

- 런타임에 알려지지 않은 정보를 사용 하 여 선택 항목을 사용자 지정 하려면 레코드 집합을 매개 변수화 합니다.

클래스를 사용 하려면 데이터베이스를 열고 레코드 집합 개체를 생성 한 다음 생성자에 게 `CDatabase` 개체에 대 한 포인터를 전달 합니다. 그런 다음 레코드 집합의 `Open` 멤버 함수를 호출 합니다 .이 함수는 개체의 다이너셋 또는 스냅숏 여부를 지정할 수 있습니다. `Open`를 호출 하면 데이터 소스에서 데이터를 선택 합니다. 레코드 집합 개체를 연 후에는 해당 멤버 함수 및 데이터 멤버를 사용 하 여 레코드를 스크롤하고 해당 개체에 대해 작업을 수행 합니다. 사용할 수 있는 작업은 개체가 다이너셋 인지 아니면 스냅숏 인지에 따라 달라 집니다. 즉, 데이터베이스를 업데이트할 수 있는지, 아니면 읽기 전용인 지에 따라 달라 지 며, ODBC (Open Database Connectivity) 데이터 원본의 기능에 따라 달라 지 며, 대량 행 페치를 구현 했는지 여부에 따라 달라 집니다. `Open` 호출 이후 변경 되거나 추가 된 레코드를 새로 고치려면 개체의 `Requery` 멤버 함수를 호출 합니다. 개체의 `Close` 멤버 함수를 호출 하 고 완료 되 면 개체를 삭제 합니다.

파생 된 `CRecordset` 클래스에서 RFX (레코드 필드 교환) 또는 대량 RFX (대량 레코드 필드 교환)를 사용 하 여 레코드 필드의 읽기 및 업데이트를 지원할 수 있습니다.

레코드 집합 및 레코드 필드 교환에 대 한 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md), [레코드 집합 (odbc)](../../data/odbc/recordset-odbc.md), [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)및 [RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요. 다이너셋과 스냅숏에 대 한 초점은 [다이너셋](../../data/odbc/dynaset.md) 및 [스냅숏](../../data/odbc/snapshot.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

##  <a name="addnew"></a>CRecordset:: AddNew

테이블에 새 레코드를 추가할 준비를 합니다.

```
virtual void AddNew();
```

### <a name="remarks"></a>설명

[Requery](#requery) 멤버 함수를 호출 하 여 새로 추가 된 레코드를 확인 해야 합니다. 레코드의 필드는 처음에 Null입니다. (데이터베이스 용어에서 Null은 "값을 갖지 않음"을 의미 하 고의 C++null과 같지 않습니다.) 작업을 완료 하려면 [Update](#update) 멤버 함수를 호출 해야 합니다. `Update` 데이터 원본에 변경 내용을 저장 합니다.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `AddNew`를 호출할 수 없습니다. 이로 인해 어설션이 실패 합니다. 클래스 `CRecordset`는 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않지만 `SQLSetPos`ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

`AddNew`는 레코드 집합의 필드 데이터 멤버를 사용 하 여 비어 있는 새 레코드를 준비 합니다. `AddNew`호출한 후에는 레코드 집합의 필드 데이터 멤버에서 원하는 값을 설정 합니다. 이 목적을 위해 [Edit](#edit) 멤버 함수를 호출할 필요가 없습니다. 기존 레코드에 대해서만 `Edit`을 사용 합니다. 이후에 `Update`를 호출 하면 필드 데이터 멤버의 변경 된 값이 데이터 원본에 저장 됩니다.

> [!CAUTION]
>  `Update`를 호출 하기 전에 새 레코드로 스크롤하면 새 레코드가 손실 되 고 경고가 제공 되지 않습니다.

데이터 원본에서 트랜잭션을 지 원하는 경우 `AddNew` 트랜잭션 작업을 호출할 수 있습니다. 트랜잭션에 대 한 자세한 내용은 클래스 [CDatabase](../../mfc/reference/cdatabase-class.md)를 참조 하세요. `AddNew`를 호출 하기 전에 [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 를 호출 해야 합니다.

> [!NOTE]
>  다이너셋은 새 레코드가 레코드 집합에 마지막 레코드로 추가 됩니다. 추가 된 레코드는 스냅숏에 추가 되지 않습니다. `Requery`를 호출 하 여 레코드 집합을 새로 고쳐야 합니다.

`Open` 멤버 함수가 호출 되지 않은 레코드 집합에 대 한 `AddNew`를 호출할 수 없습니다. 에 추가할 수 없는 레코드 집합에 대해 `AddNew`를 호출 하는 경우 `CDBException` throw 됩니다. [CanAppend](#canappend)를 호출 하 여 레코드 집합을 업데이트할 수 있는지 여부를 확인할 수 있습니다.

자세한 내용은 레코드 집합: 레코드 집합의 레코드 [업데이트 방법 (odbc](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)), 레코드 [집합: 레코드 추가, 업데이트 및 삭제](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)(odbc) 및 [트랜잭션 (odbc)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)문서를 참조 하세요.

##  <a name="canappend"></a>CRecordset:: CanAppend

이전에 열린 레코드 집합에서 새 레코드를 추가할 수 있는지 여부를 확인 합니다.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Return Value

레코드 집합에서 새 레코드 추가를 허용 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다. 레코드 집합을 읽기 전용으로 연 경우 `CanAppend`는 0을 반환 합니다.

##  <a name="canbookmark"></a>CRecordset:: CanBookmark

레코드 집합에서 책갈피를 사용 하 여 레코드를 표시할 수 있는지 여부를 결정 합니다.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Return Value

레코드 집합에서 책갈피를 지 원하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 [Open](#open) 멤버 함수의 *dwOptions* 매개 변수에 있는 `CRecordset::useBookmarks` 옵션과는 독립적입니다. 지정 된 ODBC 드라이버와 커서 유형이 책갈피를 지원 하는지 여부를 `CanBookmark` 나타냅니다. `CRecordset::useBookmarks` 책갈피를 사용할 수 있는지 여부를 나타냅니다 (지원 되는 경우).

> [!NOTE]
>  책갈피는 앞 으로만 이동 가능한 레코드 집합에서 지원 되지 않습니다.

책갈피 및 레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 책갈피 및 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 및 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md)문서를 참조 하세요.

##  <a name="cancel"></a>CRecordset:: Cancel

데이터 소스에서 진행 중인 비동기 작업이 나 두 번째 스레드의 프로세스를 취소 하도록 요청 합니다.

```
void Cancel();
```

### <a name="remarks"></a>설명

MFC ODBC 클래스는 더 이상 비동기 처리를 사용 하지 않습니다. 보조적 작업을 수행 하려면 `SQLSetConnectOption`ODBC API 함수를 직접 호출 해야 합니다. 자세한 내용은 *ODBC SDK 프로그래머 가이드*의 "비동기적으로 함수 실행" 항목을 참조 하세요.

##  <a name="cancelupdate"></a>CRecordset:: CancelUpdate

[업데이트](#update) 를 호출 하기 전에 [편집](#edit) 또는 [AddNew](#addnew) 작업으로 인해 보류 중인 모든 업데이트를 취소 합니다.

```
void CancelUpdate();
```

### <a name="remarks"></a>설명

> [!NOTE]
>  이 멤버 함수는 대량 행 페치를 사용 하는 레코드 집합에는 적용 되지 않습니다. 이러한 레코드 집합은 `Edit`, `AddNew`또는 `Update`를 호출할 수 없기 때문입니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

변경 된 필드를 자동으로 확인 하는 경우 `CancelUpdate` `Edit` 또는 `AddNew` 호출 되기 전에 멤버 변수를 값으로 복원 합니다. 그렇지 않은 경우에는 모든 값 변경 내용이 유지 됩니다. 자동 필드 검사는 기본적으로 레코드 집합을 열 때 활성화 됩니다. 이를 사용 하지 않도록 설정 하려면 [Open](#open) 멤버 함수의 *dwOptions* 매개 변수에 `CRecordset::noDirtyFieldCheck` 지정 해야 합니다.

데이터 업데이트에 대 한 자세한 내용은 레코드 [집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)문서를 참조 하세요.

##  <a name="canrestart"></a>CRecordset:: CanRestart

레코드 집합에서 `Requery` 멤버 함수를 호출 하 여 쿼리를 다시 시작 하 여 해당 레코드를 새로 고칠 수 있는지 여부를 확인 합니다.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Return Value

Requery가 허용 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

##  <a name="canscroll"></a>CRecordset:: CanScroll

레코드 집합을 스크롤할 수 있는지 여부를 결정 합니다.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Return Value

레코드 집합에서 스크롤을 허용 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

스크롤에 대 한 자세한 내용은 [레코드 집합: 스크롤 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)문서를 참조 하세요.

##  <a name="cantransact"></a>CRecordset:: CanTransact

레코드 집합에서 트랜잭션을 허용 하는지 여부를 확인 합니다.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Return Value

레코드 집합에서 트랜잭션을 허용 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

##  <a name="canupdate"></a>CRecordset:: CanUpdate

레코드 집합을 업데이트할 수 있는지 여부를 확인 합니다.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Return Value

레코드 집합을 업데이트할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 데이터 원본이 읽기 전용 이거나 레코드 집합을 열 때 *dwOptions* 매개 변수에서 `CRecordset::readOnly` 지정한 경우에는 레코드 집합이 읽기 전용일 수 있습니다.

##  <a name="checkrowseterror"></a>CRecordset:: CheckRowsetError

레코드를 인출 하는 동안 생성 된 오류를 처리 하기 위해 호출 됩니다.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>매개 변수

*nRetCode*<br/>
ODBC API 함수 반환 코드입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

이 가상 멤버 함수는 레코드를 반입할 때 발생 하는 오류를 처리 하며 대량 행 페치 중에 유용 합니다. 사용자 고유의 오류 처리를 구현 하기 위해 `CheckRowsetError`를 재정의 하는 것을 고려해 볼 수 있습니다.

`CheckRowsetError`는 `Open`, `Requery`또는 `Move` 작업과 같은 커서 탐색 작업에서 자동으로 호출 됩니다. `SQLExtendedFetch`ODBC API 함수의 반환 값이 전달 됩니다. 다음 표에서는 *nRetCode* 매개 변수에 사용할 수 있는 값을 보여 줍니다.

|nRetCode|Description|
|--------------|-----------------|
|SQL_SUCCESS|함수가 성공적으로 완료 되었습니다. 추가 정보를 사용할 수 없습니다.|
|SQL_SUCCESS_WITH_INFO|함수가 정상적으로 완료 되었습니다. 심각 하지 않은 오류가 발생 했을 수 있습니다. `SQLError`를 호출 하 여 추가 정보를 얻을 수 있습니다.|
|SQL_NO_DATA_FOUND|결과 집합의 모든 행이 인출 되었습니다.|
|SQL_ERROR|함수가 실패 했습니다. `SQLError`를 호출 하 여 추가 정보를 얻을 수 있습니다.|
|SQL_INVALID_HANDLE|잘못 된 환경 핸들, 연결 핸들 또는 문 핸들로 인해 함수가 실패 했습니다. 이는 프로그래밍 오류를 나타냅니다. `SQLError`에서 추가 정보를 사용할 수 없습니다.|
|SQL_STILL_EXECUTING|비동기적으로 시작 된 함수가 아직 실행 되 고 있습니다. 기본적으로 MFC는 `CheckRowsetError`으로이 값을 전달 하지 않습니다. MFC는 더 이상 SQL_STILL_EXECUTING를 반환 하지 않을 때까지 `SQLExtendedFetch`를 계속 호출 합니다.|

`SQLError`에 대 한 자세한 내용은 Windows SDK을 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="close"></a>CRecordset:: Close

레코드 집합을 닫습니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

ODBC HSTMT 및 레코드 집합에 할당 된 프레임 워크의 모든 메모리가 할당 취소 됩니다. 일반적으로 `Close`를 호출한 후에는 C++ **새**로 할당 된 레코드 집합 개체를 삭제 합니다.

`Close`를 호출한 후 `Open`을 다시 호출할 수 있습니다. 이렇게 하면 레코드 집합 개체를 다시 사용할 수 있습니다. 대신 `Requery`를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset:: CRecordset

`CRecordset` 개체를 생성합니다.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>매개 변수

*pDatabase*<br/>
`CDatabase` 개체 또는 NULL 값에 대 한 포인터를 포함 합니다. NULL이 아닌 경우 데이터 원본에 연결 하기 위해 `CDatabase` 개체의 `Open` 멤버 함수를 호출 하지 않은 경우에는 레코드 집합에서 자체 `Open` 호출 중에 해당 함수를 열려고 시도 합니다. NULL을 전달 하는 경우에는 클래스 마법사를 사용 하 여 레코드 집합 클래스를 파생할 때 지정한 데이터 원본 정보를 사용 하 여 `CDatabase` 개체가 생성 되 고 연결 됩니다.

### <a name="remarks"></a>설명

`CRecordset`를 직접 사용 하거나 `CRecordset`에서 응용 프로그램별 클래스를 파생할 수 있습니다. 클래스 마법사를 사용 하 여 레코드 집합 클래스를 파생할 수 있습니다.

> [!NOTE]
>  파생 클래스는 자체 생성자를 제공 *해야 합니다* . 파생 클래스의 생성자에서 적절 한 매개 변수를 전달 하 여 `CRecordset::CRecordset`생성자를 호출 합니다.

`CDatabase` 개체가 자동으로 생성 되 고 연결 되도록 레코드 집합 생성자에 NULL을 전달 합니다. 이는 레코드 집합을 생성 하기 전에 `CDatabase` 개체를 구성 하 고 연결 하지 않아도 되는 유용한 축약형입니다.

### <a name="example"></a>예제

자세한 내용은 [레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)문서를 참조 하세요.

##  <a name="delete"></a>CRecordset::D e)

현재 레코드를 삭제합니다.

```
virtual void Delete();
```

### <a name="remarks"></a>설명

성공적으로 삭제 한 후에는 레코드 집합의 필드 데이터 멤버가 Null 값으로 설정 되 고, 삭제 된 레코드를 이동 하기 위해 `Move` 함수 중 하나를 명시적으로 호출 해야 합니다. 삭제 된 레코드를 이동한 후에는 되돌릴 수 없습니다. 데이터 원본에서 트랜잭션을 지 원하는 경우 트랜잭션의 `Delete` 호출을 수행할 수 있습니다. 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `Delete`를 호출할 수 없습니다. 이로 인해 어설션이 실패 합니다. 클래스 `CRecordset`는 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않지만 `SQLSetPos`ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

> [!CAUTION]
>  레코드 집합을 업데이트할 수 있어야 하 고 `Delete`를 호출할 때 레코드 집합에 유효한 레코드가 있어야 합니다. 그렇지 않으면 오류가 발생 합니다. 예를 들어 레코드를 삭제 하지만 `Delete`를 다시 호출 하기 전에 새 레코드로 스크롤하지 않는 경우 `Delete`는 [Cdbexception](../../mfc/reference/cdbexception-class.md)을 throw 합니다.

[AddNew](#addnew) 및 [Edit](#edit)와 달리 `Delete` 호출은 [업데이트](#update)에 대 한 호출 뒤에 오지 않습니다. `Delete` 호출이 실패 하면 필드 데이터 멤버가 변경 되지 않은 상태로 유지 됩니다.

### <a name="example"></a>예제

이 예에서는 함수의 프레임에 생성 된 레코드 집합을 보여 줍니다. 이 예제에서는 데이터 소스에 이미 연결 된 `CDatabase` 형식의 멤버 변수인 `m_dbCust`존재 한다고 가정 합니다.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset::D oBulkFieldExchange

데이터 원본에서 레코드 집합으로 데이터의 대량 행을 교환 하기 위해 호출 됩니다. 대량 RFX (대량 레코드 필드 교환)를 구현 합니다.

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 개체에 대 한 포인터입니다. 프레임 워크에는 필드 교환 작업의 컨텍스트를 지정 하는이 개체가 이미 설정 되어 있습니다.

### <a name="remarks"></a>설명

대량 행 페치를 구현 하는 경우 프레임 워크는이 멤버 함수를 호출 하 여 데이터 원본에서 레코드 집합 개체로 데이터를 자동으로 전송 합니다. 또한 `DoBulkFieldExchange`은 매개 변수 데이터 멤버 (있는 경우)를 레코드 집합의 선택에 대 한 SQL 문 문자열의 매개 변수 자리 표시자에 바인딩합니다.

대량 행 페치를 구현 하지 않는 경우 프레임 워크는 [DoFieldExchange](#dofieldexchange)를 호출 합니다. 대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수에서 *dwOptions* 매개 변수의 `CRecordset::useMultiRowFetch` 옵션을 지정 해야 합니다.

> [!NOTE]
> `DoBulkFieldExchange`은 `CRecordset`에서 파생 된 클래스를 사용 하는 경우에만 사용할 수 있습니다. `CRecordset`에서 직접 레코드 집합 개체를 만든 경우 [GetFieldValue](#getfieldvalue) 멤버 함수를 호출 하 여 데이터를 검색 해야 합니다.

대량 RFX (대량 레코드 필드 교환)는 RFX (레코드 필드 교환)와 유사 합니다. 데이터는 데이터 원본에서 레코드 집합 개체로 자동으로 전송 됩니다. 그러나 `AddNew`, `Edit`, `Delete`또는 `Update`를 호출 하 여 변경 내용을 데이터 원본으로 다시 전송할 수는 없습니다. 현재 클래스 `CRecordset`는 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않습니다. 그러나 `SQLSetPos`ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다.

클래스 마법사는 대량 레코드 필드 교환을 지원 하지 않습니다. 따라서 대량 RFX 함수에 대 한 호출을 작성 하 여 `DoBulkFieldExchange`를 수동으로 재정의 해야 합니다. 이러한 함수에 대 한 자세한 내용은 [레코드 필드 교환 함수](../../mfc/reference/record-field-exchange-functions.md)항목을 참조 하세요.

대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요. 관련 정보는 [RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

##  <a name="dofieldexchange"></a>CRecordset::D oFieldExchange

레코드 집합의 필드 데이터 멤버와 데이터 소스에 있는 해당 레코드 사이에서 데이터를 양방향으로 교환 하기 위해 호출 됩니다. RFX (레코드 필드 교환)를 구현 합니다.

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 개체에 대 한 포인터입니다. 프레임 워크에는 필드 교환 작업의 컨텍스트를 지정 하는이 개체가 이미 설정 되어 있습니다.

### <a name="remarks"></a>설명

대량 행 페치를 구현 하지 않는 경우 프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합 개체의 필드 데이터 멤버와 데이터 소스에 있는 현재 레코드의 해당 열 간에 데이터를 자동으로 교환 합니다. 또한 `DoFieldExchange`은 매개 변수 데이터 멤버 (있는 경우)를 레코드 집합의 선택에 대 한 SQL 문 문자열의 매개 변수 자리 표시자에 바인딩합니다.

대량 행 페치를 구현 하는 경우 프레임 워크는 [DoBulkFieldExchange](#dobulkfieldexchange)을 호출 합니다. 대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수에서 *dwOptions* 매개 변수의 `CRecordset::useMultiRowFetch` 옵션을 지정 해야 합니다.

> [!NOTE]
> `DoFieldExchange`은 `CRecordset`에서 파생 된 클래스를 사용 하는 경우에만 사용할 수 있습니다. `CRecordset`에서 직접 레코드 집합 개체를 만든 경우 [GetFieldValue](#getfieldvalue) 멤버 함수를 호출 하 여 데이터를 검색 해야 합니다.

RFX (레코드 필드 교환) 라고 하는 필드 데이터 교환은 레코드 집합 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드 필드, 데이터 원본의 레코드에서 레코드 집합 개체로의 양방향으로 작동 합니다.

파생 된 레코드 집합 클래스에 대 한 `DoFieldExchange`를 구현 하기 위해 일반적으로 수행 해야 하는 작업은 클래스 마법사를 사용 하 여 클래스를 만들고 필드 데이터 멤버의 이름과 데이터 형식을 지정 하는 것입니다. 매개 변수 데이터 멤버를 지정 하거나 동적으로 바인딩하는 모든 열을 처리 하기 위해 클래스 마법사에서 작성 하는 코드를 추가할 수도 있습니다. 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)문서를 참조 하세요.

클래스 마법사를 사용 하 여 파생 된 레코드 집합 클래스를 선언 하면 마법사가 다음 예제와 같이 사용자에 대 한 `DoFieldExchange` 재정의를 작성 합니다.

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

RFX 함수에 대 한 자세한 내용은 [레코드 필드 교환 함수](../../mfc/reference/record-field-exchange-functions.md)항목을 참조 하세요.

`DoFieldExchange`에 대 한 추가 예제 및 세부 정보는 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요. RFX에 대 한 일반 정보는 [레코드 필드 교환](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

##  <a name="edit"></a>CRecordset:: Edit

현재 레코드를 변경할 수 있습니다.

```
virtual void Edit();
```

### <a name="remarks"></a>설명

`Edit`를 호출한 후에는 해당 값을 직접 다시 설정 하 여 필드 데이터 멤버를 변경할 수 있습니다. 이후에 [업데이트](#update) 멤버 함수를 호출 하 여 변경 내용을 데이터 원본에 저장 하면 작업이 완료 됩니다.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `Edit`를 호출할 수 없습니다. 이로 인해 어설션이 실패 합니다. 클래스 `CRecordset`는 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않지만 `SQLSetPos`ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

`Edit`은 레코드 집합의 데이터 멤버 값을 저장 합니다. `Edit`를 호출 하 고 변경한 다음 `Edit`를 다시 호출 하는 경우 레코드의 값이 첫 번째 `Edit` 호출 이전의 값으로 복원 됩니다.

일부 경우에는 데이터를 포함 하지 않는 열을 Null로 설정 하 여 열을 업데이트 하는 것이 좋습니다. 이렇게 하려면 TRUE의 매개 변수를 사용 하 여 [SetFieldNull](#setfieldnull) 를 호출 하 여 필드를 Null로 표시 합니다. 이로 인해 열도 업데이트 됩니다. 값이 변경 되지 않은 경우에도 데이터 소스에 필드를 기록 하려면 TRUE의 매개 변수를 사용 하 여 [SetFieldDirty](#setfielddirty) 를 호출 합니다. 필드의 값이 Null 인 경우에도 작동 합니다.

데이터 원본에서 트랜잭션을 지 원하는 경우 트랜잭션의 `Edit` 호출을 수행할 수 있습니다. `Edit`를 호출 하기 전에 및 레코드 집합을 연 후에는 [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 를 호출 해야 합니다. 또한 [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) 호출은 `Edit` 작업을 완료 하기 위해 `Update`를 호출 하는 대신 사용할 수 없습니다. 트랜잭션에 대 한 자세한 내용은 클래스 [CDatabase](../../mfc/reference/cdatabase-class.md)를 참조 하세요.

현재 잠금 모드에 따라 업데이트 되는 레코드는 `Update`를 호출 하거나 다른 레코드로 스크롤할 때까지 `Edit`에 의해 잠겼거나 `Edit` 호출 중에만 잠길 수 있습니다. [SetLockingMode](#setlockingmode)를 사용 하 여 잠금 모드를 변경할 수 있습니다.

`Update`를 호출 하기 전에 새 레코드로 스크롤하면 현재 레코드의 이전 값이 복원 됩니다. 업데이트할 수 없는 레코드 집합에 대해 `Edit`를 호출 하거나 현재 레코드가 없는 경우 `CDBException` throw 됩니다.

자세한 내용은 [트랜잭션 (odbc)](../../data/odbc/transaction-odbc.md) 및 [레코드 집합: 레코드 잠금 (odbc)](../../data/odbc/recordset-locking-records-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset:: FlushResultSet

결과 집합이 여러 개 있는 경우 미리 정의 된 쿼리 (저장 프로시저)의 다음 결과 집합을 검색 합니다.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Return Value

검색할 결과 집합이 더 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

현재 결과 집합에서 커서를 완전히 완료 한 경우에만 `FlushResultSet`를 호출 해야 합니다. `FlushResultSet`를 호출 하 여 다음 결과 집합을 검색 하면 해당 결과 집합에서 커서가 유효 하지 않습니다. `FlushResultSet`를 호출한 후에는 [MoveNext](#movenext) 멤버 함수를 호출 해야 합니다.

미리 정의 된 쿼리가 출력 매개 변수 또는 입/출력 매개 변수를 사용 하는 경우 이러한 매개 변수 값을 얻기 위해 `FALSE` (값 0)을 반환할 때까지 `FlushResultSet`를 호출 해야 합니다.

`FlushResultSet`는 `SQLMoreResults`ODBC API 함수를 호출 합니다. `SQLMoreResults` SQL_ERROR 또는 SQL_INVALID_HANDLE 반환 하는 경우 `FlushResultSet`는 예외를 throw 합니다. `SQLMoreResults`에 대 한 자세한 내용은 Windows SDK을 참조 하세요.

`FlushResultSet`를 호출 하려는 경우에는 저장 프로시저에 바인딩된 필드가 있어야 합니다.

### <a name="example"></a>예제

다음 코드에서는 `COutParamRecordset`이 입력 매개 변수와 출력 매개 변수가 있는 미리 정의 된 쿼리를 기반으로 하 고 여러 결과 집합을 포함 하는 `CRecordset`파생 개체인 것으로 가정 합니다. [DoFieldExchange](#dofieldexchange) 재정의의 구조를 확인 합니다.

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset:: GetBookmark

현재 레코드에 대 한 책갈피 값을 가져옵니다.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>매개 변수

*varBookmark*<br/>
현재 레코드의 책갈피를 나타내는 [Cdbvariant](../../mfc/reference/cdbvariant-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

레코드 집합에서 책갈피가 지원 되는지 확인 하려면 [Canbookmark](#canbookmark)를 호출 합니다. 지원 되는 경우 책갈피를 사용할 수 있도록 하려면 [Open](#open) Member 함수의 *dwOptions* 매개 변수에 `CRecordset::useBookmarks` 옵션을 설정 해야 합니다.

> [!NOTE]
>  책갈피를 지원 하지 않거나 사용할 수 없는 경우 `GetBookmark`를 호출 하면 예외가 throw 됩니다. 책갈피는 앞 으로만 이동 가능한 레코드 집합에서 지원 되지 않습니다.

`GetBookmark` 현재 레코드의 책갈피 값을 `CDBVariant` 개체에 할당 합니다. 다른 레코드로 이동한 후 언제 든 지 해당 레코드로 돌아가려면 [Setbookmark](#setbookmark) 를 해당 `CDBVariant` 개체로 호출 합니다.

> [!NOTE]
>  특정 레코드 집합 작업 후 책갈피는 더 이상 유효 하지 않을 수 있습니다. 예를 들어 `GetBookmark`를 호출 하 고 그 다음에 `Requery`를 호출 하는 경우 `SetBookmark`으로 레코드에 반환 하지 못할 수 있습니다. [CDatabase:: Get책갈피 지 속성](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) 을 호출 하 여 `SetBookmark`안전 하 게 호출할 수 있는지 확인 합니다.

책갈피 및 레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 책갈피 및 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 및 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md)문서를 참조 하세요.

##  <a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect

기본 연결 문자열을 가져오기 위해 호출 됩니다.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Return Value

기본 연결 문자열을 포함 하는 `CString`입니다.

### <a name="remarks"></a>설명

프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합의 기반이 되는 데이터 원본에 대 한 기본 연결 문자열을 가져옵니다. 클래스 마법사는 테이블 및 열에 대 한 정보를 가져오기 위해 클래스 마법사에서 사용 하는 것과 동일한 데이터 원본을 식별 하 여이 함수를 구현 합니다. 응용 프로그램을 개발 하는 동안이 기본 연결을 사용 하는 것이 편리할 수 있습니다. 그러나 기본 연결은 응용 프로그램 사용자에 게 적합 하지 않을 수 있습니다. 해당 하는 경우이 함수를 다시 구현 하 여 클래스 마법사의 버전을 삭제 해야 합니다. 연결 문자열에 대 한 자세한 내용은 [데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)문서를 참조 하세요.

##  <a name="getdefaultsql"></a>CRecordset:: GetDefaultSQL

실행할 기본 SQL 문자열을 가져오기 위해 호출 됩니다.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Return Value

기본 SQL 문을 포함 하는 `CString`입니다.

### <a name="remarks"></a>설명

프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합의 기반이 되는 기본 SQL 문을 가져옵니다. 테이블 이름 또는 SQL **SELECT** 문이 될 수 있습니다.

클래스 마법사를 사용 하 여 레코드 집합 클래스를 선언 하 여 기본 SQL 문을 간접적으로 정의 하 고 클래스 마법사에서이 작업을 수행 합니다.

사용자가 사용 하는 SQL 문 문자열이 필요한 경우 열을 열 때 레코드 집합의 레코드를 선택 하는 데 사용 되는 SQL 문을 반환 하는 `GetSQL`를 호출 합니다. 클래스의 `GetDefaultSQL`재정의에서 기본 SQL 문자열을 편집할 수 있습니다. 예를 들어 **call** 문을 사용 하 여 미리 정의 된 쿼리에 대 한 호출을 지정할 수 있습니다. 그러나 `GetDefaultSQL`을 편집 하는 경우 데이터 원본의 열 수와 일치 하도록 `m_nFields` 수정 해야 합니다.

자세한 내용은 [레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)문서를 참조 하세요.

> [!CAUTION]
>  프레임 워크에서 테이블 이름을 확인할 수 없거나, 여러 테이블 이름이 제공 된 경우 또는 **CALL** 문을 해석할 수 없는 경우에는 테이블 이름이 비어 있게 됩니다. **Call** 문을 사용 하는 경우 중괄호와 **CALL** 키워드 사이에 공백을 삽입 해서는 안 되 고, 중괄호 앞 이나 **select** 문에서 **select** 키워드 앞에 공백을 삽입 하지 않아야 합니다.

##  <a name="getfieldvalue"></a>CRecordset:: GetFieldValue

현재 레코드에서 필드 데이터를 검색 합니다.

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
필드의 이름입니다.

*varValu*e 필드의 값을 저장 하는 [cdbvariant](../../mfc/reference/cdbvariant-class.md) 개체에 대 한 참조입니다.

*nFieldType*<br/>
필드의 ODBC C 데이터 형식입니다. 기본값인 DEFAULT_FIELD_TYPE를 사용 하면 `GetFieldValue`는 다음 표에 따라 SQL 데이터 형식에서 C 데이터 형식을 결정 합니다. 그렇지 않은 경우 데이터 형식을 직접 지정 하거나 호환 되는 데이터 형식을 선택할 수 있습니다. 예를 들어 모든 데이터 형식을 SQL_C_CHAR에 저장할 수 있습니다.

|C 데이터 형식|SQL 데이터 형식|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

ODBC 데이터 형식에 대 한 자세한 내용은 Windows SDK 부록 D의 "SQL 데이터 형식" 및 "C 데이터 형식" 항목을 참조 하십시오.

*nIndex*<br/>
필드의 인덱스 (0부터 시작)입니다.

*strValue*<br/>
필드의 데이터 형식에 관계 없이 텍스트로 변환 된 필드 값을 저장 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

이름 또는 인덱스를 기준으로 필드를 조회할 수 있습니다. `CDBVariant` 개체 또는 `CString` 개체 중 하나에 필드 값을 저장할 수 있습니다.

대량 행 페치를 구현한 경우 현재 레코드는 항상 행 집합의 첫 번째 레코드에 배치 됩니다. 지정 된 행 집합 내의 레코드에 `GetFieldValue`를 사용 하려면 먼저 [SetRowsetCursorPosition](#setrowsetcursorposition) 멤버 함수를 호출 하 여 커서를 해당 행 집합 내의 원하는 행으로 이동 해야 합니다. 그런 다음 해당 행에 대 한 `GetFieldValue`를 호출 합니다. 대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수에서 *dwOptions* 매개 변수의 `CRecordset::useMultiRowFetch` 옵션을 지정 해야 합니다.

`GetFieldValue`를 사용 하 여 디자인 타임에 정적으로 바인딩하는 대신 런타임에 필드를 동적으로 페치할 수 있습니다. 예를 들어 `CRecordset`에서 직접 레코드 집합 개체를 선언한 경우 `GetFieldValue`를 사용 하 여 필드 데이터를 검색 해야 합니다. RFX (레코드 필드 교환) 또는 대량 RFX (대량 레코드 필드 교환)는 구현 되지 않습니다.

> [!NOTE]
>  `CRecordset`에서 파생 하지 않고 레코드 집합 개체를 선언 하는 경우 ODBC 커서 라이브러리를 로드 하지 마십시오. 커서 라이브러리를 사용 하려면 레코드 집합에 바인딩된 열이 하나 이상 있어야 합니다. 그러나 `CRecordset`를 직접 사용 하는 경우에는 열이 바인딩되지 않습니다. 멤버 함수 [CDatabase:: microsoft.office.interop.visio.documents.openex](../../mfc/reference/cdatabase-class.md#openex) 및 [Cdatabase:: Open](../../mfc/reference/cdatabase-class.md#open) 은 커서 라이브러리를 로드할지 여부를 제어 합니다.

`GetFieldValue`는 `SQLGetData`ODBC API 함수를 호출 합니다. 드라이버가 필드 값의 실제 길이에 SQL_NO_TOTAL 값을 출력 하는 경우 `GetFieldValue`는 예외를 throw 합니다. `SQLGetData`에 대 한 자세한 내용은 Windows SDK을 참조 하세요.

### <a name="example"></a>예제

다음 샘플 코드는 `CRecordset`에서 직접 선언 된 레코드 집합 개체에 대 한 `GetFieldValue` 호출을 보여 줍니다.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  DAO 클래스 `CDaoRecordset`와 달리 `CRecordset`에는 `SetFieldValue` 멤버 함수가 없습니다. `CRecordset`에서 직접 개체를 만드는 경우 실제로는 읽기 전용입니다.

대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="getodbcfieldcount"></a>CRecordset:: GetODBCFieldCount

레코드 집합 개체의 총 필드 수를 검색 합니다.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Return Value

레코드 집합의 필드 수입니다.

### <a name="remarks"></a>설명

레코드 집합을 만드는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합 만들기 및 닫기 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)문서를 참조 하세요.

##  <a name="getodbcfieldinfo"></a>CRecordset:: GetODBCFieldInfo

레코드 집합의 필드에 대 한 정보를 가져옵니다.

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
필드의 이름입니다.

*fieldinfo*<br/>
`CODBCFieldInfo` 구조체에 대 한 참조입니다.

*nIndex*<br/>
필드의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하면 이름을 기준으로 필드를 조회할 수 있습니다. 다른 버전에서는 인덱스를 기준으로 필드를 조회할 수 있습니다.

반환 되는 정보에 대 한 설명은 [Codbcfieldinfo](../../mfc/reference/codbcfieldinfo-structure.md) 구조체를 참조 하세요.

레코드 집합을 만드는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합 만들기 및 닫기 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)문서를 참조 하세요.

##  <a name="getrecordcount"></a>CRecordset:: GetRecordCount

레코드 집합의 크기를 결정 합니다.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Return Value

레코드 집합의 레코드 수입니다. 레코드 집합이 레코드를 포함 하지 않는 경우 0입니다. 레코드 수를 확인할 수 없으면-1입니다.

### <a name="remarks"></a>설명

> [!CAUTION]
>  레코드 수는 "상위 워터 마크"로 유지 관리 되며, 사용자가 레코드를 이동할 때 가장 높은 번호의 레코드가 표시 됩니다. 총 레코드 수는 사용자가 마지막 레코드를 벗어나 이동한 후에만 알 수 있습니다. 성능상의 이유로 `MoveLast`를 호출할 때 수가 업데이트 되지 않습니다. 레코드를 직접 계산 하려면 `IsEOF`가 0이 아닌 값을 반환할 때까지 반복 해 서 `MoveNext`를 호출 합니다. `CRecordset:AddNew` 및 `Update`를 통해 레코드를 추가 하면 개수가 늘어납니다. `CRecordset::Delete`를 통해 레코드를 삭제 하면 개수가 줄어듭니다.

##  <a name="getrowsetsize"></a>CRecordset:: GetRowsetSize

지정 된 인출 중에 검색 하려는 행 수에 대 한 현재 설정을 가져옵니다.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Return Value

지정 된 인출 중에 검색할 행의 수입니다.

### <a name="remarks"></a>설명

대량 행 페치를 사용 하는 경우 레코드 집합을 열 때 기본 행 집합 크기는 25입니다. 그렇지 않으면 1입니다.

대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수의 *dwOptions* 매개 변수에 `CRecordset::useMultiRowFetch` 옵션을 지정 해야 합니다. 행 집합 크기에 대 한 설정을 변경 하려면 [SetRowsetSize](#setrowsetsize)를 호출 합니다.

대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="getrowsfetched"></a>CRecordset:: GetRowsFetched

인출 후 실제로 검색 된 레코드 수를 결정 합니다.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Return Value

지정 된 페치 후 데이터 원본에서 검색 된 행 수입니다.

### <a name="remarks"></a>설명

이는 대량 행 페치를 구현한 경우에 유용 합니다. 일반적으로 행 집합 크기는 인출에서 검색할 행 수를 나타냅니다. 그러나 레코드 집합의 총 행 수는 행 집합에서 검색 되는 행 수에도 영향을 줍니다. 예를 들어 레코드 집합에 행 집합 크기를 4로 설정 하는 10 개의 레코드가 있는 경우 `MoveNext`를 호출 하 여 레코드 집합을 반복 하면 최종 행 집합에 2 개의 레코드만 포함 됩니다.

대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수의 *dwOptions* 매개 변수에 `CRecordset::useMultiRowFetch` 옵션을 지정 해야 합니다. 행 집합 크기를 지정 하려면 [SetRowsetSize](#setrowsetsize)를 호출 합니다.

대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset:: GetRowStatus

현재 행 집합에 있는 행의 상태를 가져옵니다.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>매개 변수

*wRow*<br/>
현재 행 집합에서 한 행의 위치입니다. 이 값의 범위는 1에서 행 집합의 크기입니다.

### <a name="return-value"></a>Return Value

행의 상태 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

`GetRowStatus`는 데이터 원본에서 데이터를 마지막으로 검색 한 이후 행의 상태가 변경 되거나 *Wrow* 에 해당 하는 행이 인출 되지 않았음을 나타내는 값을 반환 합니다. 다음 표에서는 가능한 반환 값을 보여 줍니다.

|상태 값|Description|
|------------------|-----------------|
|SQL_ROW_SUCCESS|행이 변경 되지 않았습니다.|
|SQL_ROW_UPDATED|행이 업데이트 되었습니다.|
|SQL_ROW_DELETED|행 삭제 되었습니다.|
|SQL_ROW_ADDED|행이 추가 되었습니다.|
|SQL_ROW_ERROR|오류로 인해 행이 unretrievable 됩니다.|
|SQL_ROW_NOROW|*Wrow*에 해당 하는 행이 없습니다.|

자세한 내용은 Windows SDK `SQLExtendedFetch` ODBC API 함수를 참조 하십시오.

##  <a name="getstatus"></a>CRecordset:: GetStatus

레코드 집합에서 현재 레코드의 인덱스를 확인 하 고 마지막 레코드가 표시 되는지 여부를 확인 합니다.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>매개 변수

*rStatus*<br/>
`CRecordsetStatus` 개체에 대한 참조입니다. 자세한 내용은 주의 섹션을 참조하십시오.

### <a name="remarks"></a>설명

인덱스를 추적 하려고 시도 하지만 경우에 따라서는이를 `CRecordset` 수 없습니다. 설명은 [Getrecordcount](#getrecordcount) 를 참조 하세요.

`CRecordsetStatus` 구조체의 형식은 다음과 같습니다.

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

`CRecordsetStatus`의 두 멤버에는 다음과 같은 의미가 있습니다.

- `m_lCurrentRecord`은 레코드 집합에서 현재 레코드의 인덱스 (0부터 시작)를 포함 합니다 (알려진 경우). 인덱스를 확인할 수 없으면이 멤버에 AFX_CURRENT_RECORD_UNDEFINED (-2)가 포함 됩니다. `IsBOF` TRUE (빈 레코드 집합 또는 첫 번째 레코드 앞으로 스크롤 하려고 시도) 이면 `m_lCurrentRecord`는 AFX_CURRENT_RECORD_BOF (-1)로 설정 됩니다. 첫 번째 레코드의 경우 0, 두 번째 레코드 1 등으로 설정 됩니다.

- 레코드 집합의 총 레코드 수가 결정 되 면 0이 아닌 값이 `m_bRecordCountFinal`. 일반적으로이는 레코드 집합의 시작 부분에서 시작 하 여 `IsEOF` 0이 아닌 값을 반환할 때까지 `MoveNext`를 호출 하 여 수행 해야 합니다. 이 멤버가 0 이면 `GetRecordCount`에 의해 반환 되는 레코드 수가-1이 아닌 경우에는 레코드의 "상위 워터 마크" 수만 있습니다.

##  <a name="getsql"></a>CRecordset:: GetSQL

이 멤버 함수를 호출 하 여 레코드를 열 때 레코드 집합의 레코드를 선택 하는 데 사용 된 SQL 문을 가져옵니다.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Return Value

SQL 문을 포함 하는 `CString`에 대 한 **const** 참조입니다.

### <a name="remarks"></a>설명

이는 일반적으로 SQL **SELECT** 문입니다. `GetSQL`에서 반환 되는 문자열은 읽기 전용입니다.

`GetSQL`에서 반환 되는 문자열은 일반적으로 *lpszSQL* 매개 변수의 레코드 집합에 전달 했을 수 있는 문자열과 `Open` 멤버 함수에 따라 다릅니다. 이는 레코드 집합이 `Open`에 전달 된 내용, 클래스 마법사를 사용 하 여 지정한 내용, `m_strFilter` 및 `m_strSort` 데이터 멤버에서 지정한 매개 변수 및 사용자가 지정한 매개 변수를 기반으로 전체 SQL 문을 생성 하기 때문입니다. 레코드 집합에서이 SQL 문을 생성 하는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)문서를 참조 하십시오.

> [!NOTE]
>  [Open](#open)을 호출한 후에만이 멤버 함수를 호출 합니다.

##  <a name="gettablename"></a>CRecordset:: GetTableName

레코드 집합 쿼리의 기반이 되는 SQL 테이블의 이름을 가져옵니다.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Return Value

레코드 집합이 테이블을 기반으로 하는 경우 테이블 이름을 포함 하는 `CString`에 대 한 **const** 참조입니다. 그렇지 않으면 빈 문자열입니다.

### <a name="remarks"></a>설명

`GetTableName`는 레코드 집합이 여러 테이블이 나 미리 정의 된 쿼리 (저장 프로시저)의 조인이 아니라 테이블을 기반으로 하는 경우에만 유효 합니다. 이름은 읽기 전용입니다.

> [!NOTE]
>  [Open](#open)을 호출한 후에만이 멤버 함수를 호출 합니다.

##  <a name="isbof"></a>CRecordset:: IsBOF

레코드 집합이 첫 번째 레코드 앞에 배치 되 면 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Return Value

레코드 집합이 레코드를 포함 하지 않거나 첫 번째 레코드 앞으로 스크롤한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드에서 레코드로 이동 하기 전에이 멤버 함수를 호출 하 여 레코드 집합의 첫 번째 레코드 앞에 있는지 알아보세요. `IsEOF`와 함께 `IsBOF`를 사용 하 여 레코드 집합에 레코드가 포함 되어 있는지 아니면 비어 있는지를 확인할 수도 있습니다. `Open`호출 하는 즉시 레코드 집합에 레코드가 포함 되어 있지 않은 경우 `IsBOF`은 0이 아닌 값을 반환 합니다. 하나 이상의 레코드를 포함 하는 레코드 집합을 열 때 첫 번째 레코드는 현재 레코드이 고 `IsBOF`는 0을 반환 합니다.

첫 번째 레코드가 현재 레코드이 고 `MovePrev`를 호출 하는 경우 `IsBOF` 이후에 0이 아닌 값이 반환 됩니다. `IsBOF` 0이 아닌 값을 반환 하 고 `MovePrev`를 호출 하면 오류가 발생 합니다. `IsBOF`에서 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않으며 현재 레코드를 필요로 하는 모든 작업은 오류를 발생 합니다.

### <a name="example"></a>예제

이 예제에서는 `IsBOF` 및 `IsEOF`를 사용 하 여 코드에서 레코드 집합을 두 방향으로 스크롤할 때 레코드 집합의 제한을 검색 합니다.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset:: IsDeleted

현재 레코드가 삭제 되었는지 여부를 확인 합니다.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Return Value

레코드 집합을 삭제 된 레코드에 배치 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드로 스크롤하고 `IsDeleted` TRUE (0이 아님)를 반환 하는 경우 다른 레코드 집합 작업을 수행 하기 전에 다른 레코드로 스크롤해야 합니다.

`IsDeleted` 결과는 레코드 집합 형식, 레코드 집합을 업데이트할 수 있는지 여부, 레코드 집합을 열 때 `CRecordset::skipDeletedRecords` 옵션을 지정 했는지 여부, 드라이버 팩에서 레코드를 삭제 했는지 여부, 여러 사용자가 있는지 여부 등의 많은 요인에 따라 달라 집니다.

`CRecordset::skipDeletedRecords` 및 드라이버 압축에 대 한 자세한 내용은 [Open](#open) 멤버 함수를 참조 하세요.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `IsDeleted`를 호출 하면 안 됩니다. 대신 [GetRowStatus](#getrowstatus) 멤버 함수를 호출 합니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="iseof"></a>CRecordset:: IsEOF

레코드 집합이 마지막 레코드 뒤에 배치 된 경우 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Return Value

레코드 집합이 레코드를 포함 하지 않거나 마지막 레코드를 넘어 스크롤 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드에서 레코드로 스크롤할 때이 멤버 함수를 호출 하 여 레코드 집합의 마지막 레코드를 벗어났는지 여부를 알아보세요. `IsEOF`를 사용 하 여 레코드 집합에 레코드를 포함 하거나 비어 있는지 여부를 확인할 수도 있습니다. `Open`호출 하는 즉시 레코드 집합에 레코드가 포함 되어 있지 않은 경우 `IsEOF`은 0이 아닌 값을 반환 합니다. 하나 이상의 레코드를 포함 하는 레코드 집합을 열 때 첫 번째 레코드는 현재 레코드이 고 `IsEOF`는 0을 반환 합니다.

`MoveNext`를 호출할 때 마지막 레코드가 현재 레코드 이면 `IsEOF`는 0이 아닌 값을 반환 합니다. `IsEOF` 0이 아닌 값을 반환 하 고 `MoveNext`를 호출 하면 오류가 발생 합니다. `IsEOF`에서 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않으며 현재 레코드를 필요로 하는 모든 작업은 오류를 발생 합니다.

### <a name="example"></a>예제

[IsBOF](#isbof)의 예제를 참조 하세요.

##  <a name="isfielddirty"></a>CRecordset:: IsFieldDirty

[편집](#edit) 이나 [AddNew](#addnew) 가 호출 된 이후 지정 된 필드 데이터 멤버가 변경 되었는지 여부를 확인 합니다.

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, 필드가 커밋되지 않았는지 여부를 확인 하는 NULL입니다.

### <a name="return-value"></a>Return Value

`AddNew` 또는 `Edit`를 호출한 후 지정한 필드 데이터 멤버가 변경 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Edit` 또는 `AddNew`를 호출 하 여 `CRecordset`의 [업데이트](#update) 멤버 함수를 호출 하 여 현재 레코드가 업데이트 되는 경우 모든 더티 필드 데이터 멤버의 데이터는 데이터 원본에 대 한 레코드에 전송 됩니다.

> [!NOTE]
>  이 멤버 함수는 대량 행 페치를 사용 하는 레코드 집합에는 적용 되지 않습니다. 대량 행 페치를 구현한 경우 `IsFieldDirty`는 항상 FALSE를 반환 하 고 어설션이 실패 하 게 됩니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

`IsFieldDirty`를 호출 하면 필드의 더티 상태가 다시 계산 되기 때문에 [SetFieldDirty](#setfielddirty) 에 대 한 이전 호출의 결과를 다시 설정 합니다. `AddNew` 경우 현재 필드 값이 의사 null 값과 다른 경우 필드 상태는 더티로 설정 됩니다. `Edit` 경우 필드 값이 캐시 된 값과 다르면 필드 상태가 더티로 설정 됩니다.

`IsFieldDirty`는 [DoFieldExchange](#dofieldexchange)를 통해 구현 됩니다.

더티 플래그에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)문서를 참조 하세요.

##  <a name="isfieldnull"></a>CRecordset:: IsFieldNull

현재 레코드의 지정 된 필드가 Null (값이 없는 경우) 인 경우 0이 아닌 값을 반환 합니다.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, 필드가 Null 인지 여부를 확인 하는 NULL입니다.

### <a name="return-value"></a>Return Value

지정 된 필드 데이터 멤버가 Null로 플래그가 지정 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 레코드 집합의 지정 된 필드 데이터 멤버에 Null로 플래그가 지정 되었는지 여부를 확인 합니다. (데이터베이스 용어에서 Null은 "값을 갖지 않음"을 의미 하 고의 C++null과 같지 않습니다.) 필드 데이터 멤버가 Null로 플래그가 지정 된 경우 값이 없는 현재 레코드의 열로 해석 됩니다.

> [!NOTE]
>  이 멤버 함수는 대량 행 페치를 사용 하는 레코드 집합에는 적용 되지 않습니다. 대량 행 페치를 구현한 경우 `IsFieldNull`는 항상 FALSE를 반환 하 고 어설션이 실패 하 게 됩니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

`IsFieldNull`는 [DoFieldExchange](#dofieldexchange)를 통해 구현 됩니다.

##  <a name="isfieldnullable"></a>CRecordset:: IsFieldNullable

현재 레코드의 지정 된 필드를 Null로 설정할 수 있으면 0이 아닌 값을 반환 합니다.

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, Null 값으로 설정할 수 있는 필드가 있는지 여부를 확인 하는 NULL입니다.

### <a name="remarks"></a>설명

지정 된 필드 데이터 멤버가 "nullable" (Null 값으로 설정할 수 있음) 인지 여부를 확인 하려면이 멤버 함수를 호출 합니다. C++ Null은 null과 같지 않습니다 .이는 데이터베이스 용어에서 "값을 갖지 않음"을 의미 합니다.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `IsFieldNullable`를 호출할 수 없습니다. 대신 [GetODBCFieldInfo](#getodbcfieldinfo) 멤버 함수를 호출 하 여 필드를 Null 값으로 설정할 수 있는지 여부를 확인 합니다. 대량 행 페치를 구현 했는지 여부에 관계 없이 항상 `GetODBCFieldInfo`를 호출할 수 있습니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

Null 일 수 없는 필드에는 값이 있어야 합니다. 레코드를 추가 하거나 업데이트할 때 이러한 필드를 Null로 설정 하려고 하면 데이터 원본에서 추가 또는 업데이트를 거부 하 고 [update](#update) 에서 예외를 throw 합니다. [SetFieldNull](#setfieldnull)를 호출 하는 경우를 제외 하 고 `Update`를 호출할 때 예외가 발생 합니다.

함수의 첫 번째 인수에 NULL을 사용 하면 `param` 필드가 아닌 `outputColumn` 필드에만 함수가 적용 됩니다. 예를 들어

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` 필드만 NULL로 설정 됩니다. `param` 필드는 영향을 받지 않습니다.

`param` 필드에서 작업 하려면 작업할 개별 `param`의 실제 주소를 제공 해야 합니다. 예를 들어 다음과 같습니다.

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

즉, `outputColumn` 필드를 사용할 때와 마찬가지로 모든 `param` 필드를 NULL로 설정할 수 없습니다.

`IsFieldNullable`는 [DoFieldExchange](#dofieldexchange)를 통해 구현 됩니다.

##  <a name="isopen"></a>CRecordset:: IsOpen

레코드 집합이 이미 열려 있는지 여부를 확인 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Return Value

레코드 집합 개체의 [Open](#open) 또는 [Requery](#requery) 멤버 함수가 이전에 호출 되었고 레코드 집합이 닫히지 않은 경우 0이 아닙니다. 그렇지 않으면 0입니다.

##  <a name="m_hstmt"></a>CRecordset:: m_hstmt

레코드 집합과 연결 된 HSTMT 형식의 ODBC 문 데이터 구조에 대 한 핸들을 포함 합니다.

### <a name="remarks"></a>설명

ODBC 데이터 원본에 대 한 각 쿼리는 HSTMT와 연결 됩니다.

> [!CAUTION]
>  [Open](#open) 이 호출 되기 전에 `m_hstmt`을 사용 하지 마십시오.

일반적으로는 HSTMT에 직접 액세스할 필요가 없지만 SQL 문을 직접 실행 하는 데 필요할 수 있습니다. 클래스 `CDatabase`의 `ExecuteSQL` 멤버 함수는 `m_hstmt`을 사용 하는 예제를 제공 합니다.

##  <a name="m_nfields"></a>CRecordset:: m_nFields

레코드 집합 클래스의 필드 데이터 멤버 수를 포함 합니다. 즉, 데이터 원본의 레코드 집합에서 선택한 열의 수입니다.

### <a name="remarks"></a>설명

레코드 집합 클래스의 생성자는 올바른 수의 `m_nFields`을 초기화 해야 합니다. 대량 행 페치를 구현 하지 않은 경우 클래스 마법사는이 초기화를 사용 하 여 레코드 집합 클래스를 선언할 때이 초기화를 작성 합니다. 수동으로 작성할 수도 있습니다.

프레임 워크는이 숫자를 사용 하 여 필드 데이터 멤버와 데이터 소스에 있는 현재 레코드의 해당 열 간의 상호 작용을 관리 합니다.

> [!CAUTION]
>  이 숫자는 `DoFieldExchange`에 등록 된 "출력 열"의 수와 일치 해야 하며, 매개 변수 `CFieldExchange::outputColumn`를 사용 하 여 [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 를 호출한 후에 `DoBulkFieldExchange`.

"레코드 집합: 데이터 열 동적 바인딩" 문서에 설명 된 대로 열을 동적으로 바인딩할 수 있습니다. 이렇게 하려면 동적으로 바인딩된 열에 대해 `DoFieldExchange` 또는 `DoBulkFieldExchange` 멤버 함수에서 RFX 또는 Bulk RFX 함수 호출 수를 반영 하도록 `m_nFields` 수를 늘려야 합니다.

자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (odbc)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) 및 [레코드 집합: 대량 레코드 페치 (odbc)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[레코드 필드 교환: RFX 사용](../../data/odbc/record-field-exchange-using-rfx.md)문서를 참조 하세요.

##  <a name="m_nparams"></a>CRecordset:: m_nParams

레코드 집합 클래스의 매개 변수 데이터 멤버 수를 포함 합니다. 즉, 레코드 집합의 쿼리와 함께 전달 되는 매개 변수 수입니다.

### <a name="remarks"></a>설명

레코드 집합 클래스에 매개 변수 데이터 멤버가 있는 경우 클래스의 생성자는 올바른 수를 사용 하 여 `m_nParams`을 초기화 해야 합니다. `m_nParams` 기본값은 0입니다. 수동으로 수행 해야 하는 매개 변수 데이터 멤버를 추가 하는 경우에는 매개 변수 수를 반영 하도록 클래스 생성자에서 초기화를 수동으로 추가 해야 합니다 .이 값은 적어도 `m_strFilter` 또는 `m_strSort` 문자열의 ' ' 자리 표시자 수 만큼 커야 합니다.

프레임 워크는이 숫자를 사용 하 여 레코드 집합의 쿼리를 매개 변수화 합니다.

> [!CAUTION]
>  이 숫자는 `DoFieldExchange`에 등록 된 "params"의 수와 일치 해야 하며, 매개 변수 값 `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`또는 `CFieldExchange::inoutParam`로 [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 를 호출한 후에 `DoBulkFieldExchange`.

### <a name="example"></a>예제

  레코드 [집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 및 [레코드 필드 교환: RFX 사용](../../data/odbc/record-field-exchange-using-rfx.md)문서를 참조 하세요.

##  <a name="m_pdatabase"></a>CRecordset:: m_pDatabase

레코드 집합을 데이터 소스에 연결 하는 `CDatabase` 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

이 변수는 두 가지 방법으로 설정 됩니다. 일반적으로 레코드 집합 개체를 생성할 때 이미 연결 된 `CDatabase` 개체에 대 한 포인터를 전달 합니다. 대신 NULL을 전달 하면 `CRecordset` `CDatabase` 개체를 만들어 연결 합니다. 두 경우 모두 `CRecordset`는이 변수에 포인터를 저장 합니다.

일반적으로 `m_pDatabase`에 저장 된 포인터를 직접 사용 하지 않아도 됩니다. 그러나 `CRecordset`에 대 한 고유한 확장을 작성 하는 경우 포인터를 사용 해야 할 수 있습니다. 예를 들어 고유한 `CDBException`s를 throw 하는 경우 포인터가 필요할 수 있습니다. 또는 SQL 문을 직접 실행 하기 위해 트랜잭션 실행, 시간 제한 설정 또는 클래스 `CDatabase`의 `ExecuteSQL` 멤버 함수 호출과 같은 `CDatabase` 개체를 사용 하 여 작업을 수행 해야 하는 경우 필요할 수 있습니다.

##  <a name="m_strfilter"></a>CRecordset:: m_strFilter

레코드 집합 개체를 생성 한 후 해당 `Open` 멤버 함수를 호출 하기 전에이 데이터 멤버를 사용 하 여 SQL **WHERE** 절이 포함 된 `CString`를 저장 합니다.

### <a name="remarks"></a>설명

레코드 집합은이 문자열을 사용 하 여 `Open` 또는 `Requery` 호출 중에 선택 하는 레코드를 제한 (또는 필터링) 합니다. 이는 "캘리포니아 기반 모든 영업 사원의" ("state = CA")와 같이 레코드의 하위 집합을 선택 하는 데 유용 합니다. **Where** 절에 대 한 ODBC SQL 구문은

`WHERE search-condition`

문자열에 **WHERE** 키워드를 포함 하지 않습니다. 프레임 워크는이를 제공 합니다.

' ' 자리 표시자를 배치 하 고, 각 자리 표시자에 대 한 클래스에서 매개 변수 데이터 멤버를 선언 하 고, 런타임에 매개 변수를 레코드 집합에 전달 하 여 필터 문자열을 매개 변수화 할 수도 있습니다. 이렇게 하면 런타임에 필터를 생성할 수 있습니다. 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)문서를 참조 하세요.

SQL **WHERE** 절에 대 한 자세한 내용은 [sql](../../data/odbc/sql.md)문서를 참조 하세요. 레코드 선택 및 필터링에 대 한 자세한 내용은 레코드 [집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset:: m_strSort

레코드 집합 개체를 생성 한 후 `Open` 멤버 함수를 호출 하기 전에이 데이터 멤버를 사용 하 **여 SQL ORDER by** 절이 포함 된 `CString`를 저장 합니다.

### <a name="remarks"></a>설명

레코드 집합은이 문자열을 사용 하 여 `Open` 또는 `Requery` 호출 중에 선택 하는 레코드를 정렬 합니다. 이 기능을 사용 하 여 하나 이상의 열에 대 한 레코드 집합을 정렬할 수 있습니다. **ORDER by** 절에 대 한 ODBC SQL 구문은

`ORDER BY sort-specification [, sort-specification]...`

여기서 정렬 사양은 정수 또는 열 이름입니다. 정렬 문자열의 열 목록에 "ASC" 또는 "DESC"를 추가 하 여 오름차순 이나 내림차순으로 (기본적으로 순서가 오름차순) 지정할 수도 있습니다. 선택한 레코드는 먼저 나열 된 첫 번째 열, 두 번째 열 순으로 정렬 됩니다. 예를 들어 성, 이름 순으로 "고객" 레코드 집합을 정렬할 수 있습니다. 나열할 수 있는 열 수는 데이터 원본에 따라 달라 집니다. 자세한 내용은 Windows SDK를 참조 하세요.

문자열에는 **ORDER by** 키워드를 포함 하지 않습니다. 프레임 워크는이를 제공 합니다.

SQL 절에 대 한 자세한 내용은 [sql](../../data/odbc/sql.md)문서를 참조 하세요. 레코드를 정렬 하는 방법에 대 한 자세한 내용은 레코드 [집합: 레코드 정렬 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset:: Move

현재 레코드 포인터를 앞 이나 뒤로 이동 하 여 레코드 집합 내에서 이동 합니다.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>매개 변수

*nRows*<br/>
앞으로 또는 뒤로 이동 하는 행의 수입니다. 양수 값은 레코드 집합의 끝 부분으로 앞으로 이동 합니다. 음수 값은 시작 부분을 향해 뒤로 이동 합니다.

*wFetchType*<br/>
`Move` 페치할 행 집합을 결정 합니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

*Nrows*에 대해 0 값을 전달 하면 `Move` 현재 레코드를 새로 고칩니다. `Move`은 현재 `AddNew` 나 `Edit` 모드를 종료 하 고 `AddNew` 또는 `Edit`를 호출 하기 전에 현재 레코드의 값을 복원 합니다.

> [!NOTE]
>  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [CRecordset:: IsDeleted](#isdeleted) 를 참조 하세요. `skipDeletedRecords` 옵션 집합을 사용 하 여 `CRecordset`를 열면 *Nrows* 매개 변수가 0 인 경우 어설션이 `Move`. 이 동작은 동일한 데이터를 사용 하 여 다른 클라이언트 응용 프로그램에서 삭제 되는 행을 새로 고칠 수 없도록 합니다. `skipDeletedRecords`에 대 한 설명은 [Open](#open) 의 *dwoption* 매개 변수를 참조 하세요.

행 집합을 기준으로 레코드 집합의 위치를 `Move` 합니다. *Nrows* 및 *wfetchtype*의 값에 따라 `Move` 적절 한 행 집합을 페치 한 다음 해당 행 집합의 첫 번째 레코드를 현재 레코드로 만듭니다. 대량 행 페치를 구현 하지 않은 경우 행 집합 크기는 항상 1입니다. 행 집합을 인출 하는 경우 `Move`는 [CheckRowsetError](#checkrowseterror) 멤버 함수를 직접 호출 하 여 fetch로 인해 발생 하는 오류를 처리 합니다.

전달 하는 값에 따라 `Move`는 다른 `CRecordset` 멤버 함수와 동일 합니다. 특히 *Wfetchtype* 의 값은 보다 직관적이 고 종종 현재 레코드를 이동 하는 기본 방법 인 멤버 함수를 나타낼 수 있습니다.

다음 표에서는 *wfetchtype*에 사용할 수 있는 값, `Move` *wfetchtype* 및 *nrows*에 따라 페치할 행 집합 및 *wfetchtype*에 해당 하는 모든 동등 멤버 함수를 나열 합니다.

|wFetchType|인출 행 집합|동급 멤버 함수|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (기본값)|현재 행 집합의 첫 번째 행에서 *Nrows* 행을 시작 하는 행 집합입니다.||
|SQL_FETCH_NEXT|다음 행 집합 *Nrows* 는 무시 됩니다.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|이전 행 집합입니다. *Nrows* 는 무시 됩니다.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|레코드 집합의 첫 번째 행 집합입니다. *Nrows* 는 무시 됩니다.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|레코드 집합의 마지막 전체 행 집합입니다. *Nrows* 는 무시 됩니다.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|*Nrows* 가 0 > 경우 레코드 집합의 처음부터 *nrows* 행을 시작 하는 행 집합입니다. *Nrows* 가 0 < 경우 행 집합은 레코드 집합의 끝부터 *nrows* 행을 시작 합니다. *Nrows* = 0 인 경우 파일의 시작 (BOF) 조건이 반환 됩니다.|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|책갈피 값이 *Nrows*에 해당 하는 행에서 시작 하는 행 집합입니다.|[SetBookmark](#setbookmark)|

> [!NOTE]
>  전방 전용 레코드 집합의 경우 `Move`은 *Wfetchtype*에 대해 SQL_FETCH_NEXT 값만 사용할 수 있습니다.

> [!CAUTION]
>  레코드 집합에 레코드가 없는 경우 `Move`를 호출 하면 예외가 throw 됩니다. 레코드 집합에 레코드가 있는지 여부를 확인 하려면 [IsBOF](#isbof) 및 [IsEOF](#iseof)를 호출 합니다.

> [!NOTE]
>  `IsBOF` 또는 `IsEOF`에서 0이 아닌 값을 반환 하는 레코드 집합의 시작 또는 끝을 지나서 스크롤하면 `Move` 함수를 호출 하면 `CDBException`throw 될 수 있습니다. 예를 들어 `IsEOF`에서 0이 아닌 값을 반환 하 고 `IsBOF` 그렇지 않으면 `MoveNext`는 예외를 throw 하지만 `MovePrev`는 그렇지 않습니다.

> [!NOTE]
>  현재 레코드를 업데이트 하거나 추가 하는 동안 `Move`를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요. 관련 정보는 Windows SDK에서 `SQLExtendedFetch` ODBC API 함수를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset:: MoveFirst

첫 번째 행 집합의 첫 번째 레코드를 현재 레코드로 설정 합니다.

```
void MoveFirst();
```

### <a name="remarks"></a>설명

대량 행 페치가 구현 되었는지 여부에 관계 없이 항상 레코드 집합의 첫 번째 레코드가 됩니다.

레코드 집합을 연 후 즉시 `MoveFirst`를 호출할 필요가 없습니다. 이때 첫 번째 레코드 (있는 경우)가 자동으로 현재 레코드가 됩니다.

> [!NOTE]
>  이 멤버 함수는 앞 으로만 이동 가능한 레코드 집합에 사용할 수 없습니다.

> [!NOTE]
>  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [IsDeleted](#isdeleted) 멤버 함수를 참조 하십시오.

> [!CAUTION]
>  레코드 집합에 레코드가 없는 경우 `Move` 함수를 호출 하면 예외가 throw 됩니다. 레코드 집합에 레코드가 있는지 여부를 확인 하려면 `IsBOF`를 호출 하 고 `IsEOF`합니다.

> [!NOTE]
>  현재 레코드를 업데이트 하거나 추가 하는 동안 `Move` 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

### <a name="example"></a>예제

  [IsBOF](#isbof)의 예제를 참조 하세요.

##  <a name="movelast"></a>CRecordset:: MoveLast

마지막으로 완료 된 행 집합의 첫 번째 레코드를 현재 레코드로 설정 합니다.

```
void MoveLast();
```

### <a name="remarks"></a>설명

대량 행 페치를 구현 하지 않은 경우 레코드 집합의 행 집합 크기는 1 이므로 `MoveLast` 레코드 집합의 마지막 레코드로 이동 하기만 하면 됩니다.

> [!NOTE]
>  이 멤버 함수는 앞 으로만 이동 가능한 레코드 집합에 사용할 수 없습니다.

> [!NOTE]
>  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [IsDeleted](#isdeleted) 멤버 함수를 참조 하십시오.

> [!CAUTION]
>  레코드 집합에 레코드가 없는 경우 `Move` 함수를 호출 하면 예외가 throw 됩니다. 레코드 집합에 레코드가 있는지 여부를 확인 하려면 `IsBOF`를 호출 하 고 `IsEOF`합니다.

> [!NOTE]
>  현재 레코드를 업데이트 하거나 추가 하는 동안 `Move` 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

### <a name="example"></a>예제

  [IsBOF](#isbof)의 예제를 참조 하세요.

##  <a name="movenext"></a>CRecordset:: MoveNext

다음 행 집합의 첫 번째 레코드를 현재 레코드로 설정 합니다.

```
void MoveNext();
```

### <a name="remarks"></a>설명

대량 행 페치를 구현 하지 않은 경우 레코드 집합의 행 집합 크기는 1 이므로 `MoveNext`는 단순히 다음 레코드로 이동 합니다.

> [!NOTE]
>  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [IsDeleted](#isdeleted) 멤버 함수를 참조 하십시오.

> [!CAUTION]
>  레코드 집합에 레코드가 없는 경우 `Move` 함수를 호출 하면 예외가 throw 됩니다. 레코드 집합에 레코드가 있는지 여부를 확인 하려면 `IsBOF`를 호출 하 고 `IsEOF`합니다.

> [!NOTE]
>  또한 `MoveNext`를 호출 하기 전에 `IsEOF`를 호출 하는 것이 좋습니다. 예를 들어 레코드 집합의 끝을 지나서 스크롤하면 `IsEOF`는 0이 아닌 값을 반환 합니다. `MoveNext`에 대 한 후속 호출에서는 예외를 throw 합니다.

> [!NOTE]
>  현재 레코드를 업데이트 하거나 추가 하는 동안 `Move` 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

### <a name="example"></a>예제

  [IsBOF](#isbof)의 예제를 참조 하세요.

##  <a name="moveprev"></a>CRecordset:: MovePrev

이전 행 집합의 첫 번째 레코드를 현재 레코드로 설정 합니다.

```
void MovePrev();
```

### <a name="remarks"></a>설명

대량 행 페치를 구현 하지 않은 경우 레코드 집합의 행 집합 크기는 1 이므로 `MovePrev`는 단순히 이전 레코드로 이동 합니다.

> [!NOTE]
>  이 멤버 함수는 앞 으로만 이동 가능한 레코드 집합에 사용할 수 없습니다.

> [!NOTE]
>  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [IsDeleted](#isdeleted) 멤버 함수를 참조 하십시오.

> [!CAUTION]
>  레코드 집합에 레코드가 없는 경우 `Move` 함수를 호출 하면 예외가 throw 됩니다. 레코드 집합에 레코드가 있는지 여부를 확인 하려면 `IsBOF`를 호출 하 고 `IsEOF`합니다.

> [!NOTE]
>  또한 `MovePrev`를 호출 하기 전에 `IsBOF`를 호출 하는 것이 좋습니다. 예를 들어 레코드 집합의 시작 부분 앞으로 스크롤하면 `IsBOF`는 0이 아닌 값을 반환 합니다. `MovePrev`에 대 한 후속 호출에서는 예외를 throw 합니다.

> [!NOTE]
>  현재 레코드를 업데이트 하거나 추가 하는 동안 `Move` 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

### <a name="example"></a>예제

  [IsBOF](#isbof)의 예제를 참조 하세요.

##  <a name="onsetoptions"></a>CRecordset:: OnSetOptions

지정 된 ODBC 문에 옵션 (선택에 사용 됨)을 설정 하기 위해 호출 됩니다.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>매개 변수

*핸들로*<br/>
옵션을 설정할 ODBC 문의 HSTMT입니다.

### <a name="remarks"></a>설명

`OnSetOptions`를 호출 하 여 지정 된 ODBC 문에 옵션 (선택에 사용 됨)을 설정 합니다. 프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합에 대 한 초기 옵션을 설정 합니다. `OnSetOptions`는 스크롤 가능 커서 및 커서 동시성에 대 한 데이터 원본의 지원을 결정 하 고 그에 따라 레코드 집합의 옵션을 설정 합니다. `OnSetOptions`는 선택 작업에 사용 되지만 업데이트 작업에는 `OnSetUpdateOptions` 사용 됩니다.

드라이버 또는 데이터 원본에 특정 한 옵션을 설정 하려면 `OnSetOptions`를 재정의 합니다. 예를 들어 데이터 원본에서 단독 액세스용 열기를 지 원하는 경우 `OnSetOptions`를 재정의 하 여 해당 기능을 활용할 수 있습니다.

커서에 대 한 자세한 내용은 [ODBC](../../data/odbc/odbc-basics.md)문서를 참조 하세요.

##  <a name="onsetupdateoptions"></a>CRecordset:: OnSetUpdateOptions

지정 된 ODBC 문에 대해 옵션 (update에 사용 됨)을 설정 하기 위해 호출 됩니다.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>매개 변수

*핸들로*<br/>
옵션을 설정할 ODBC 문의 HSTMT입니다.

### <a name="remarks"></a>설명

지정 된 ODBC 문에 대해 옵션 (update에 사용 됨)을 설정 하려면 `OnSetUpdateOptions`를 호출 합니다. 프레임 워크는 레코드 집합의 레코드를 업데이트 하기 위해 HSTMT를 만든 후이 멤버 함수를 호출 합니다. `OnSetOptions`는 선택 작업에 사용 되지만 업데이트 작업에는 `OnSetUpdateOptions` 사용 됩니다. `OnSetUpdateOptions`는 스크롤 가능 커서 및 커서 동시성에 대 한 데이터 원본의 지원을 결정 하 고 그에 따라 레코드 집합의 옵션을 설정 합니다.

데이터베이스에 액세스 하는 데 문을 사용 하기 전에 ODBC 문의 옵션을 설정 하려면 `OnSetUpdateOptions`를 재정의 합니다.

커서에 대 한 자세한 내용은 [ODBC](../../data/odbc/odbc-basics.md)문서를 참조 하세요.

##  <a name="open"></a>CRecordset:: Open

테이블을 검색 하거나 레코드 집합에서 나타내는 쿼리를 수행 하 여 레코드 집합을 엽니다.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>매개 변수

*nOpenType*<br/>
AFX_DB_USE_DEFAULT_TYPE 기본값을 그대로 사용 하거나 `enum OpenType`에서 다음 값 중 하나를 사용 합니다.

- 양방향 스크롤을 사용 하 여 레코드 집합을 `CRecordset::dynaset` 합니다. 레코드의 멤버 자격과 순서는 레코드 집합을 열 때 결정 되지만, 다른 사용자가 데이터 값에 적용 한 변경 내용은 fetch 작업 후에 표시 됩니다. 다이너셋은 키 집합 기반 레코드 집합으로도 알려져 있습니다.

- 양방향 스크롤이 있는 정적 레코드 집합을 `CRecordset::snapshot` 합니다. 레코드의 멤버 자격과 순서는 레코드 집합을 열 때 결정 됩니다. 데이터 값은 레코드를 반입할 때 결정 됩니다. 레코드 집합을 닫은 후 다시 열 때까지 다른 사용자가 변경한 내용을 볼 수 없습니다.

- 양방향 스크롤을 사용 하 여 레코드 집합을 `CRecordset::dynamic` 합니다. 다른 사용자가 멤버 자격, 순서 지정 및 데이터 값에 적용 한 변경 내용은 fetch 작업 후에 표시 됩니다. 많은 ODBC 드라이버는 이러한 유형의 레코드 집합을 지원 하지 않습니다.

- 전방 스크롤만 있는 읽기 전용 레코드 집합을 `CRecordset::forwardOnly` 합니다.

   `CRecordset`의 경우 기본값은 `CRecordset::snapshot`입니다. 기본 값 메커니즘을 사용 하 여 시각적 C++ 마법사는 서로 다른 기본값이 있는 ODBC `CRecordset` 및 DAO `CDaoRecordset`를 상호 작용할 수 있습니다.

이러한 레코드 집합 형식에 대 한 자세한 내용은 [레코드 집합 (ODBC)](../../data/odbc/recordset-odbc.md)문서를 참조 하세요. 관련 내용은 Windows SDK의 "블록 및 스크롤 가능 커서 사용" 문서를 참조 하세요.

> [!CAUTION]
>  요청 된 형식이 지원 되지 않는 경우 프레임 워크에서 예외를 throw 합니다.

*lpszSQL*<br/>
다음 중 하나를 포함 하는 문자열 포인터입니다.

- NULL 포인터입니다.

- 테이블의 이름입니다.

- Sql **SELECT** 문 (선택적으로 sql **WHERE** 또는 **ORDER BY** 절이 있는 경우)

- 미리 정의 된 쿼리 (저장 프로시저)의 이름을 지정 하는 **CALL** 문입니다. 중괄호와 **CALL** 키워드 사이에 공백을 삽입 하지 않도록 주의 해야 합니다.

이 문자열에 대 한 자세한 내용은 테이블 및 [주의](#remarks) 섹션의 클래스 마법사 역할에 대 한 설명을 참조 하십시오.

> [!NOTE]
>  결과 집합의 열 순서는 [DoFieldExchange](#dofieldexchange) 또는 [DoBulkFieldExchange](#dobulkfieldexchange) 함수 재정의에서 rfx 또는 Bulk rfx 함수 호출의 순서와 일치 해야 합니다.

*dwOptions*<br/>
아래에 나열 된 값의 조합을 지정할 수 있는 비트 마스크입니다. 이러한 일부는 함께 사용할 수 없습니다. 기본값은 **none**입니다.

- 옵션이 설정 되지 `CRecordset::none`. 이 매개 변수 값은 다른 모든 값과 함께 사용할 수 없습니다. 기본적으로 레코드 집합은 [편집](#edit) 또는 [삭제](#delete) 를 사용 하 여 업데이트할 수 있으며 [AddNew](#addnew)를 사용 하 여 새 레코드를 추가할 수 있습니다. 업데이트 가능성은 데이터 원본 뿐만 아니라 지정한 *nOpenType* 옵션에 따라 다릅니다. 대량 추가를 위한 최적화를 사용할 수 없습니다. 대량 행 페치는 구현 되지 않습니다. 레코드 집합 탐색 중에는 삭제 된 레코드를 건너뛰지 않습니다. 책갈피를 사용할 수 없습니다. 더티 필드 자동 검사가 구현 되었습니다.

- `CRecordset::appendOnly` 레코드 집합에 대 한 `Edit` 또는 `Delete`를 허용 하지 않습니다. `AddNew`만 허용 합니다. 이 옵션은 `CRecordset::readOnly`와 함께 사용할 수 없습니다.

- `CRecordset::readOnly` 레코드 집합을 읽기 전용으로 엽니다. 이 옵션은 `CRecordset::appendOnly`와 함께 사용할 수 없습니다.

- 준비 된 SQL 문을 사용 하 여 한 번에 많은 레코드를 추가 하는 것을 최적화할 `CRecordset::optimizeBulkAdd`. `SQLSetPos` ODBC API 함수를 사용 하 여 레코드 집합을 업데이트 하지 않는 경우에만 적용 됩니다. 첫 번째 업데이트는 변경 된 것으로 표시 된 필드를 결정 합니다. 이 옵션은 `CRecordset::useMultiRowFetch`와 함께 사용할 수 없습니다.

- 대량 행 페치를 구현 `CRecordset::useMultiRowFetch` 단일 인출 작업에서 여러 행을 검색할 수 있습니다. 이는 성능을 향상 시키기 위해 설계 된 고급 기능입니다. 그러나 클래스 마법사에서는 대량 레코드 필드 교환을 지원 하지 않습니다. 이 옵션은 `CRecordset::optimizeBulkAdd`와 함께 사용할 수 없습니다. `CRecordset::useMultiRowFetch`지정 하면 `CRecordset::noDirtyFieldCheck` 옵션이 자동으로 설정 됩니다. 이중 버퍼링은 사용할 수 없습니다. 앞 으로만 이동 가능한 레코드 집합에서는 `CRecordset::useExtendedFetch` 옵션이 자동으로 설정 됩니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

- 레코드 집합을 탐색할 때 삭제 된 모든 레코드를 `CRecordset::skipDeletedRecords` 건너뜁니다. 이렇게 하면 특정 상대적 페치의 성능이 저하 됩니다. 이 옵션은 전방 전용 레코드 집합에서 유효 하지 않습니다. *Nrows* 매개 변수를 0으로 설정 하 고 `CRecordset::skipDeletedRecords` 옵션을 설정 하 여 [Move](#move) 를 호출 하면 `Move`가 어설션 됩니다. `CRecordset::skipDeletedRecords`은 *드라이버*압축과 유사 합니다. 즉, 삭제 된 행이 레코드 집합에서 제거 됩니다. 그러나 드라이버가 레코드를 압축 하는 경우 삭제 하는 레코드만 건너뜁니다. 레코드 집합이 열려 있는 동안에는 다른 사용자가 삭제 한 레코드를 건너뛰지 않습니다. `CRecordset::skipDeletedRecords`는 다른 사용자가 삭제 한 행을 건너뜁니다.

- 지원 되는 경우 `CRecordset::useBookmarks`는 레코드 집합에서 책갈피를 사용할 수 있습니다. 책갈피는 데이터 검색 속도는 느리지만 데이터 탐색의 성능은 향상 됩니다. 앞 으로만 이동 가능한 레코드 집합에서는 유효 하지 않습니다. 자세한 내용은 [레코드 집합: 책갈피 및 절대 위치 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요.

- 자동 더티 필드 검사를 해제 `CRecordset::noDirtyFieldCheck` (이중 버퍼링). 이렇게 하면 성능이 향상 됩니다. 그러나 `SetFieldDirty` 및 `SetFieldNull` 멤버 함수를 호출 하 여 필드를 변경 되지 않은 상태로 수동으로 표시 해야 합니다. 클래스 `CRecordset`의 이중 버퍼링은 클래스 `CDaoRecordset`의 이중 버퍼링과 비슷합니다. 그러나 `CRecordset`에서는 개별 필드에 이중 버퍼링을 사용 하도록 설정할 수 없습니다. 모든 필드에 대해 사용 하도록 설정 하거나 모든 필드에 대해 사용 하지 않도록 설정 합니다. `CRecordset::useMultiRowFetch`옵션을 지정 하면 `CRecordset::noDirtyFieldCheck` 자동으로 설정 됩니다. 그러나 대량 행 페치를 구현 하는 레코드 집합에서는 `SetFieldDirty` 및 `SetFieldNull`을 사용할 수 없습니다.

- `CRecordset::executeDirect`은 준비 된 SQL 문을 사용 하지 않습니다. 성능 향상을 위해 `Requery` 멤버 함수를 호출 하지 않을 경우이 옵션을 지정 합니다.

- `SQLFetch`대신 `SQLExtendedFetch`를 구현 `CRecordset::useExtendedFetch` 합니다. 이는 앞 으로만 이동 가능한 레코드 집합에서 대량 행 페치를 구현 하기 위한 것입니다. 앞 으로만 이동 가능한 레코드 집합에서 옵션 `CRecordset::useMultiRowFetch` 지정 하면 `CRecordset::useExtendedFetch` 자동으로 설정 됩니다.

- `CRecordset::userAllocMultiRowBuffers` 사용자가 데이터에 대 한 저장소 버퍼를 할당 합니다. 사용자 고유의 저장소를 할당 하려면 `CRecordset::useMultiRowFetch`와 함께이 옵션을 사용 합니다. 그렇지 않으면 프레임 워크에서 필요한 저장소를 자동으로 할당 합니다. 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조 하세요. `CRecordset::useMultiRowFetch` 지정 하지 않고 `CRecordset::userAllocMultiRowBuffers`을 지정 하면 어설션이 실패 합니다.

### <a name="return-value"></a>Return Value

`CRecordset` 개체가 성공적으로 열린 경우 0이 아닙니다. 그렇지 않으면 0입니다. [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (호출 되는 경우)은 0을 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 레코드 집합에서 정의한 쿼리를 실행 해야 합니다. `Open`를 호출 하기 전에 레코드 집합 개체를 생성 해야 합니다.

이 레코드 집합의 데이터 원본 연결은 `Open`를 호출 하기 전에 레코드 집합을 구성 하는 방법에 따라 달라 집니다. 데이터 소스에 연결 되지 않은 레코드 집합 생성자에 [CDatabase](../../mfc/reference/cdatabase-class.md) 개체를 전달 하는 경우이 멤버 함수는 [GetDefaultConnect](#getdefaultconnect) 을 사용 하 여 데이터베이스 개체를 열려고 시도 합니다. 레코드 집합 생성자에 NULL을 전달 하는 경우 생성자는 `CDatabase` 개체를 생성 하 고 `Open` 데이터베이스 개체 연결을 시도 합니다. 이러한 다양 한 상황에서 레코드 집합과 연결을 닫는 방법에 대 한 자세한 내용은 [Close](#close)를 참조 하십시오.

> [!NOTE]
>  `CRecordset` 개체를 통해 데이터 원본에 대 한 액세스는 항상 공유 됩니다. `CDaoRecordset` 클래스와 달리 `CRecordset` 개체를 사용 하 여 단독으로 액세스할 수 있는 데이터 소스를 열 수 없습니다.

`Open`를 호출 하는 경우 쿼리는 일반적으로 SQL **SELECT** 문이 고 다음 표에 표시 된 조건에 따라 레코드를 선택 합니다.

|LpszSQL 매개 변수의 값|선택한 레코드는 다음에 의해 결정 됩니다.|예제|
|------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL`에서 반환 된 문자열입니다.||
|SQL 테이블 이름|테이블 목록의 모든 열 `DoFieldExchange` 또는 `DoBulkFieldExchange`입니다.|`"Customer"`|
|미리 정의 된 쿼리 (저장 프로시저) 이름|반환 하도록 쿼리를 정의 하는 열입니다.|`"{call OverDueAccts}"`|
|테이블 목록 **에서** 열 목록 **선택**|지정 된 테이블의 지정 된 열입니다.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  SQL 문자열에 추가 공백을 삽입 하지 않도록 주의 해야 합니다. 예를 들어 중괄호와 **CALL** 키워드 사이에 공백을 삽입 하는 경우 MFC는 SQL 문자열을 테이블 이름으로 잘못 해석 하 여 **SELECT** 문에 포함 하므로 예외가 throw 됩니다. 마찬가지로 미리 정의 된 쿼리에서 output 매개 변수를 사용 하는 경우 중괄호와 ' ' 기호 사이에 공백을 삽입 하지 마십시오. 마지막으로 **CALL** 문에서 중괄호 앞에 공백을 삽입 하거나 **select** 문에서 **select** 키워드 앞에 공백을 삽입 하면 안 됩니다.

일반적인 절차는 `Open`에 NULL을 전달 하는 것입니다. 이 경우 `Open`는 [GetDefaultSQL](#getdefaultsql)를 호출 합니다. 파생 `CRecordset` 클래스를 사용 하는 경우 `GetDefaultSQL`는 클래스 마법사에서 지정한 테이블 이름을 제공 합니다. 대신 `lpszSQL` 매개 변수에서 다른 정보를 지정할 수 있습니다.

전달 하는 것과 관계 없이 쿼리에 대 한 최종 SQL 문자열을 생성 합니다. 문자열에는 전달 된 `lpszSQL` 문자열에 추가 된 SQL **WHERE** 및 **ORDER BY** 절 `Open`이 포함 될 수 있습니다. 그런 다음 쿼리를 실행 합니다. `Open`를 호출한 후 [Getsql](#getsql) 을 호출 하 여 생성 된 문자열을 검사할 수 있습니다. 레코드 집합에서 SQL 문을 생성 하 고 레코드를 선택 하는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)문서를 참조 하십시오.

레코드 집합 클래스의 필드 데이터 멤버는 선택한 데이터의 열에 바인딩됩니다. 레코드가 반환 되 면 첫 번째 레코드가 현재 레코드가 됩니다.

필터 또는 정렬과 같은 레코드 집합에 대 한 옵션을 설정 하려는 경우에는 레코드 집합 개체를 생성 한 후 `Open`를 호출 하기 전에 이러한 옵션을 지정 합니다. 레코드 집합이 이미 열려 있는 후 레코드 집합의 레코드를 새로 고치려면 [Requery](#requery)를 호출 합니다.

추가 예제를 비롯 한 자세한 내용은 [레코드 집합 (odbc)](../../data/odbc/recordset-odbc.md), 레코드 집합: 레코드 집합의 [레코드 선택 방법 (Odbc)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)및 [레코드 집합: 레코드 집합 만들기 및 닫기 (odbc)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)를 참조 하십시오.

### <a name="example"></a>예제

다음 코드 예제에서는 다양 한 형식의 `Open` 호출을 보여 줍니다.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset:: RefreshRowset

현재 행 집합의 행에 대 한 데이터와 상태를 업데이트 합니다.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>매개 변수

*wRow*<br/>
현재 행 집합에서 한 행의 위치입니다. 이 값의 범위는 0에서 행 집합의 크기입니다.

*wLockType*<br/>
행을 새로 고친 후 잠그는 방법을 나타내는 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

*Wrow*에 대해 0 값을 전달 하면 행 집합의 모든 행이 새로 고쳐집니다.

`RefreshRowset`을 사용 하려면 [Open](#open) 멤버 함수에서 `CRecordset::useMulitRowFetch` 옵션을 지정 하 여 대량 행 페치를 구현 해야 합니다.

`RefreshRowset`는 `SQLSetPos`ODBC API 함수를 호출 합니다. *Wlocktype* 매개 변수는 `SQLSetPos` 실행 된 후 행의 잠금 상태를 지정 합니다. 다음 표에서는 *Wlocktype*에 사용할 수 있는 값에 대해 설명 합니다.

|wLockType|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (기본값)|드라이버 또는 데이터 원본을 사용 하면 `RefreshRowset`가 호출 되기 전과 동일한 잠금 또는 잠금 해제 됨 상태가 됩니다.|
|SQL_LOCK_EXCLUSIVE|드라이버 또는 데이터 원본에서 행을 독점적으로 잠급니다. 일부 데이터 원본은이 유형의 잠금을 지원 하지 않습니다.|
|SQL_LOCK_UNLOCK|드라이버 또는 데이터 원본에서 행의 잠금을 해제 합니다. 일부 데이터 원본은이 유형의 잠금을 지원 하지 않습니다.|

`SQLSetPos`에 대 한 자세한 내용은 Windows SDK을 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="requery"></a>CRecordset:: Requery

레코드 집합을 다시 작성 (새로 고침) 합니다.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Return Value

레코드 집합이 성공적으로 다시 작성 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드가 반환 되 면 첫 번째 레코드가 현재 레코드가 됩니다.

사용자 또는 다른 사용자가 데이터 원본에 만드는 추가 및 삭제를 레코드 집합에 반영 하려면 `Requery`를 호출 하 여 레코드 집합을 다시 빌드해야 합니다. 레코드 집합이 다이너셋 인 경우 사용자 또는 다른 사용자가 기존 레코드에 대해 수행 하는 업데이트 (추가는 제외)가 자동으로 반영 됩니다. 레코드 집합이 스냅숏이 면 `Requery`를 호출 하 여 다른 사용자의 편집 내용과 추가 및 삭제를 반영 해야 합니다.

다이너셋 또는 스냅숏의 경우 언제 든 지 새 필터나 정렬 또는 새 매개 변수 값을 사용 하 여 레코드 집합을 다시 작성 하려는 경우 `Requery`를 호출 합니다. `Requery`를 호출 하기 전에 `m_strFilter` 및 `m_strSort`에 새 값을 할당 하 여 새 필터 또는 정렬 속성을 설정 합니다. `Requery`를 호출 하기 전에 매개 변수 데이터 멤버에 새 값을 할당 하 여 새 매개 변수를 설정 합니다. 필터 및 정렬 문자열이 변경 되지 않은 경우 쿼리를 다시 사용 하 여 성능을 향상 시킬 수 있습니다.

레코드 집합을 다시 작성 하려는 시도가 실패 하면 레코드 집합은 닫힙니다. `Requery`를 호출 하기 전에 `CanRestart` 멤버 함수를 호출 하 여 레코드 집합을 확인할 수 있는지 여부를 확인할 수 있습니다. `CanRestart`는 `Requery` 성공 하는 것을 보장 하지 않습니다.

> [!CAUTION]
>  [Open](#open)을 호출한 후에만 `Requery`를 호출 합니다.

### <a name="example"></a>예제

이 예에서는 레코드 집합을 다시 작성 하 여 다른 정렬 순서를 적용 합니다.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition

지정 된 레코드 번호에 해당 하는 레코드에 레코드 집합을 배치 합니다.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>매개 변수

*nRows*<br/>
레코드 집합에서 현재 레코드의 서 수 위치 (1부터 이동)입니다.

### <a name="remarks"></a>설명

`SetAbsolutePosition`이 서 수 위치를 기준으로 현재 레코드 포인터를 이동 합니다.

> [!NOTE]
>  이 멤버 함수는 앞 으로만 이동 가능한 레코드 집합에서 사용할 수 없습니다.

ODBC 레코드 집합의 경우 절대 위치 설정인 1은 레코드 집합의 첫 번째 레코드를 참조 합니다. 0의 설정은 파일의 시작 (BOF) 위치를 나타냅니다.

`SetAbsolutePosition`에 음수 값을 전달할 수도 있습니다. 이 경우 레코드 집합의 위치는 레코드 집합의 끝에서 계산 됩니다. 예를 들어 `SetAbsolutePosition( -1 )`는 현재 레코드 포인터를 레코드 집합의 마지막 레코드로 이동 합니다.

> [!NOTE]
>  절대 위치는 서로게이트 레코드 번호로 사용할 수 없습니다. 책갈피는 앞의 레코드가 삭제 될 때 레코드 위치가 변경 되므로 지정 된 위치를 유지 하 고 반환 하는 데 권장 되는 방법입니다. 또한 레코드 집합에 있는 개별 레코드의 순서는 **ORDER BY** 절을 사용 하 여 SQL 문으로 생성 되는 경우를 제외 하 고는 다시 생성 될 경우 지정 된 레코드는 동일한 절대 위치를 갖게 됩니다.

레코드 집합 탐색 및 책갈피에 대 한 자세한 내용은 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 및 [레코드 집합: 책갈피와 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)문서를 참조 하세요.

##  <a name="setbookmark"></a>CRecordset:: SetBookmark

지정 된 책갈피를 포함 하는 레코드에 레코드 집합을 배치 합니다.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>매개 변수

*varBookmark*<br/>
특정 레코드의 책갈피 값을 포함 하는 [Cdbvariant](../../mfc/reference/cdbvariant-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

레코드 집합에서 책갈피가 지원 되는지 확인 하려면 [Canbookmark](#canbookmark)를 호출 합니다. 지원 되는 경우 책갈피를 사용할 수 있도록 하려면 [Open](#open) Member 함수의 *dwOptions* 매개 변수에 `CRecordset::useBookmarks` 옵션을 설정 해야 합니다.

> [!NOTE]
>  책갈피를 지원 하지 않거나 사용할 수 없는 경우 `SetBookmark`를 호출 하면 예외가 throw 됩니다. 책갈피는 앞 으로만 이동 가능한 레코드 집합에서 지원 되지 않습니다.

먼저 현재 레코드에 대 한 책갈피를 검색 하려면 [Getbookmark](#getbookmark)를 호출 합니다. 그러면이 책갈피 값이 `CDBVariant` 개체에 저장 됩니다. 나중에 저장 된 책갈피 값을 사용 하 여 `SetBookmark`를 호출 하 여 해당 레코드로 돌아갈 수 있습니다.

> [!NOTE]
>  특정 레코드 집합 작업 후에는 `SetBookmark`를 호출 하기 전에 책갈피 지 속성을 확인 해야 합니다. 예를 들어 `GetBookmark`를 사용 하 여 책갈피를 검색 한 다음 `Requery`를 호출 하면 책갈피는 더 이상 유효 하지 않을 수 있습니다. [CDatabase:: Get책갈피 지 속성](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) 을 호출 하 여 `SetBookmark`안전 하 게 호출할 수 있는지 확인 합니다.

책갈피 및 레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 책갈피 및 절대 위치 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 및 [레코드 집합: 스크롤 (odbc)](../../data/odbc/recordset-scrolling-odbc.md)문서를 참조 하세요.

##  <a name="setfielddirty"></a>CRecordset:: SetFieldDirty

레코드 집합의 필드 데이터 멤버를 변경 되거나 변경 되지 않은 것으로 플래그를 만듭니다.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
레코드 집합 또는 NULL에 있는 필드 데이터 멤버의 주소를 포함 합니다. NULL 인 경우 레코드 집합의 모든 필드 데이터 멤버에 플래그가 지정 됩니다. C++ Null은 데이터베이스 용어에서 null과 같지 않습니다 .이는 "값이 없습니다."를 의미 합니다.

*bDirty*<br/>
필드 데이터 멤버를 "더티" (변경 됨)로 플래그를 지정 하려면 TRUE입니다. 필드 데이터 멤버에 "clean" (변경 되지 않음)으로 플래그를 지정 하려면 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

필드를 변경 되지 않은 것으로 표시 하면 필드가 업데이트 되지 않고 SQL 트래픽이 감소 합니다.

> [!NOTE]
>  이 멤버 함수는 대량 행 페치를 사용 하는 레코드 집합에는 적용 되지 않습니다. 대량 행 페치를 구현한 경우 `SetFieldDirty`는 어설션이 실패 합니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

프레임 워크는 변경 된 필드 데이터 멤버를 표시 하 여 RFX (레코드 필드 교환) 메커니즘으로 데이터 원본의 레코드에 기록 되도록 합니다. 필드의 값을 변경 하는 것은 일반적으로 필드를 자동으로 설정 합니다. 따라서 사용자가 직접 `SetFieldDirty`를 호출할 필요가 없지만 필드 데이터 멤버의 값에 관계 없이 열이 명시적으로 업데이트 되거나 삽입 되도록 할 수도 있습니다.

> [!CAUTION]
>  [Edit](#edit) 또는 [AddNew](#addnew)를 호출한 후에만이 멤버 함수를 호출 합니다.

함수의 첫 번째 인수에 NULL을 사용 하면 `param` 필드가 아닌 `outputColumn` 필드에만 함수가 적용 됩니다. 예를 들어

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` 필드만 NULL로 설정 됩니다. `param` 필드는 영향을 받지 않습니다.

`param` 필드에서 작업 하려면 작업할 개별 `param`의 실제 주소를 제공 해야 합니다. 예를 들어 다음과 같습니다.

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

즉, `outputColumn` 필드를 사용할 때와 마찬가지로 모든 `param` 필드를 NULL로 설정할 수 없습니다.

##  <a name="setfieldnull"></a>CRecordset:: SetFieldNull

레코드 집합의 필드 데이터 멤버에 Null (구체적으로는 값 없음) 또는 Null이 아닌 값으로 플래그를 만듭니다.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
레코드 집합 또는 NULL에 있는 필드 데이터 멤버의 주소를 포함 합니다. NULL 인 경우 레코드 집합의 모든 필드 데이터 멤버에 플래그가 지정 됩니다. C++ Null은 데이터베이스 용어에서 null과 같지 않습니다 .이는 "값이 없습니다."를 의미 합니다.

*bNull*<br/>
필드 데이터 멤버에 값이 없는 것으로 플래그가 지정 되는 경우 0이 아닌 값 (Null)입니다. 필드 데이터 멤버가 Null이 아닌 것으로 플래그가 지정 되 면 0이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드 집합에 새 레코드를 추가 하면 처음에는 모든 필드 데이터 멤버가 Null 값으로 설정 되 고 "더티" (변경 됨)로 플래그가 지정 됩니다. 데이터 원본에서 레코드를 검색 하는 경우 해당 열의 열 값이 이미 있거나 Null입니다.

> [!NOTE]
>  대량 행 페치를 사용 하는 레코드 집합에 대해서는이 멤버 함수를 호출 하지 마세요. 대량 행 페치를 구현한 경우 `SetFieldNull`를 호출 하면 어설션이 실패 합니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

현재 레코드의 필드를 값이 없는 것으로 지정 하려는 경우 *Bnull* 을 TRUE로 설정 하 여 `SetFieldNull`를 호출 하 여 null로 플래그를 지정 합니다. 이전에 Null로 표시 된 필드에 값을 지정 하려면 새 값을 설정 하기만 하면 됩니다. `SetFieldNull`를 사용 하 여 Null 플래그를 제거할 필요는 없습니다. 필드가 Null 일 수 있는지 여부를 확인 하려면 `IsFieldNullable`를 호출 합니다.

> [!CAUTION]
>  [Edit](#edit) 또는 [AddNew](#addnew)를 호출한 후에만이 멤버 함수를 호출 합니다.

함수의 첫 번째 인수에 NULL을 사용 하면 `param` 필드가 아닌 `outputColumn` 필드에만 함수가 적용 됩니다. 예를 들어

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` 필드만 NULL로 설정 됩니다. `param` 필드는 영향을 받지 않습니다.

`param` 필드에서 작업 하려면 작업할 개별 `param`의 실제 주소를 제공 해야 합니다. 예를 들어 다음과 같습니다.

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

즉, `outputColumn` 필드를 사용할 때와 마찬가지로 모든 `param` 필드를 NULL로 설정할 수 없습니다.

> [!NOTE]
>  매개 변수를 Null로 설정 하면 레코드 집합을 열기 전에 `SetFieldNull`를 호출 하면 어설션이 생성 됩니다. 이 경우 [Setparamnull](#setparamnull)을 호출 합니다.

`SetFieldNull`는 [DoFieldExchange](#dofieldexchange)를 통해 구현 됩니다.

##  <a name="setlockingmode"></a>CRecordset:: SetLockingMode

잠금 모드를 "낙관적" 잠금 (기본값) 또는 "비관적" 잠금으로 설정 합니다. 업데이트를 위해 레코드를 잠그는 방법을 결정 합니다.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>매개 변수

*nMode*<br/>
`enum LockMode`의 다음 값 중 하나를 포함 합니다.

- `optimistic` 낙관적 잠금은 `Update`를 호출 하는 동안에만 업데이트 되는 레코드를 잠급니다.

- `pessimistic` 비관적 잠금은 `Edit` 호출 되는 즉시 레코드를 잠그고 `Update` 호출이 완료 되거나 새 레코드로 이동할 때까지 잠깁니다.

### <a name="remarks"></a>설명

레코드 집합에서 업데이트에 사용 하는 두 개의 레코드 잠금 전략을 지정 해야 하는 경우이 멤버 함수를 호출 합니다. 기본적으로 레코드 집합의 잠금 모드는 `optimistic`됩니다. 이를 더 주의 `pessimistic` 잠금 전략으로 변경할 수 있습니다. 레코드 집합 개체를 생성 하 고 연 다음 `Edit`를 호출 하기 전에 `SetLockingMode`를 호출 합니다.

##  <a name="setparamnull"></a>CRecordset:: SetParamNull

매개 변수를 Null (구체적으로는 값 없음) 또는 Null이 아닌 값으로 플래그를 만듭니다.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
이 매개 변수의 0부터 시작하는 인덱스입니다.

*bNull*<br/>
TRUE (기본값) 이면 매개 변수에 Null로 플래그가 지정 됩니다. 그렇지 않으면 매개 변수는 Null이 아닌 것으로 플래그가 지정 됩니다.

### <a name="remarks"></a>설명

[SetFieldNull](#setfieldnull)와 달리 레코드 집합을 열기 전에 `SetParamNull`을 호출할 수 있습니다.

`SetParamNull`은 일반적으로 미리 정의 된 쿼리 (저장 프로시저)와 함께 사용 됩니다.

##  <a name="setrowsetcursorposition"></a>CRecordset:: SetRowsetCursorPosition

현재 행 집합 내의 행으로 커서를 이동 합니다.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>매개 변수

*wRow*<br/>
현재 행 집합에서 한 행의 위치입니다. 이 값의 범위는 1에서 행 집합의 크기입니다.

*wLockType*<br/>
행을 새로 고친 후 잠그는 방법을 나타내는 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

대량 행 페치를 구현할 때 레코드는 행 집합으로 검색 됩니다. 여기서 인출 된 행 집합의 첫 번째 레코드는 현재 레코드입니다. 행 집합 내의 다른 레코드를 현재 레코드로 만들려면 `SetRowsetCursorPosition`를 호출 합니다. 예를 들어 `SetRowsetCursorPosition`를 [GetFieldValue](#getfieldvalue) 멤버 함수와 결합 하 여 레코드 집합의 레코드에서 데이터를 동적으로 검색할 수 있습니다.

`SetRowsetCursorPosition`을 사용 하려면 [Open](#open) 멤버 함수에서 *dwOptions* 매개 변수의 `CRecordset::useMultiRowFetch` 옵션을 지정 하 여 대량 행 페치를 구현 해야 합니다.

`SetRowsetCursorPosition`는 `SQLSetPos`ODBC API 함수를 호출 합니다. *Wlocktype* 매개 변수는 `SQLSetPos` 실행 된 후 행의 잠금 상태를 지정 합니다. 다음 표에서는 *Wlocktype*에 사용할 수 있는 값에 대해 설명 합니다.

|wLockType|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (기본값)|드라이버 또는 데이터 원본을 사용 하면 `SetRowsetCursorPosition`가 호출 되기 전과 동일한 잠금 또는 잠금 해제 됨 상태가 됩니다.|
|SQL_LOCK_EXCLUSIVE|드라이버 또는 데이터 원본에서 행을 독점적으로 잠급니다. 일부 데이터 원본은이 유형의 잠금을 지원 하지 않습니다.|
|SQL_LOCK_UNLOCK|드라이버 또는 데이터 원본에서 행의 잠금을 해제 합니다. 일부 데이터 원본은이 유형의 잠금을 지원 하지 않습니다.|

`SQLSetPos`에 대 한 자세한 내용은 Windows SDK을 참조 하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="setrowsetsize"></a>CRecordset:: SetRowsetSize

인출 하는 동안 검색 하려는 레코드 수를 지정 합니다.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>매개 변수

*dwNewRowsetSize*<br/>
지정 된 인출 중에 검색할 행의 수입니다.

### <a name="remarks"></a>설명

이 가상 멤버 함수는 대량 행 페치를 사용할 때 단일 인출 중에 검색 하려는 행 수를 지정 합니다. 대량 행 페치를 구현 하려면 [Open](#open) 멤버 함수의 *dwOptions* 매개 변수에 `CRecordset::useMultiRowFetch` 옵션을 설정 해야 합니다.

> [!NOTE]
>  대량 행 페치를 구현 하지 않고 `SetRowsetSize`를 호출 하면 어설션이 실패 합니다.

`Open`를 호출 하기 전에 `SetRowsetSize`을 호출 하 여 레코드 집합에 대 한 행 집합 크기를 초기에 설정 합니다. 대량 행 페치를 구현할 때 기본 행 집합 크기는 25입니다.

> [!NOTE]
>  `SetRowsetSize`를 호출 하는 경우 주의 해야 합니다. `Open`에서 dwOptions 매개 변수의 `CRecordset::userAllocMultiRowBuffers` 옵션에 지정 된 대로 데이터의 저장소를 수동으로 할당 하는 경우에는 `SetRowsetSize`호출한 후에 커서 탐색 작업을 수행 하기 전에 이러한 저장소 버퍼를 다시 할당 해야 하는지 여부를 확인 해야 합니다.

행 집합 크기에 대 한 현재 설정을 가져오려면 [GetRowsetSize](#getrowsetsize)를 호출 합니다.

대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

##  <a name="update"></a>CRecordset:: Update

새 데이터 또는 편집 된 데이터를 데이터 원본에 저장 하 여 `AddNew` 또는 `Edit` 작업을 완료 합니다.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Return Value

하나의 레코드가 성공적으로 업데이트 된 경우 0이 아님 열이 변경 되지 않은 경우 0입니다. 업데이트 된 레코드가 없거나 둘 이상의 레코드가 업데이트 된 경우 예외가 throw 됩니다. 데이터 원본에서 다른 오류가 발생 하는 경우에도 예외가 throw 됩니다.

### <a name="remarks"></a>설명

[AddNew](#addnew) 또는 [Edit](#edit) 멤버 함수를 호출한 후이 멤버 함수를 호출 합니다. 이 호출은 `AddNew` 또는 `Edit` 작업을 완료 하는 데 필요 합니다.

> [!NOTE]
>  대량 행 페치를 구현한 경우 `Update`를 호출할 수 없습니다. 이로 인해 어설션이 실패 합니다. 클래스 `CRecordset`는 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않지만 `SQLSetPos`ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

`AddNew` 및 `Edit`는 모두 데이터 원본에 저장 하기 위해 추가 되거나 편집 된 데이터를 저장 하는 편집 버퍼를 준비 합니다. `Update`는 데이터를 저장 합니다. 변경 된 것으로 표시 되거나 검색 된 필드만 업데이트 됩니다.

데이터 원본에서 트랜잭션을 지 원하는 경우 `Update` 호출 (및 해당 `AddNew` 또는 `Edit` 호출)을 트랜잭션의 일부로 만들 수 있습니다. 트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)문서를 참조 하세요.

> [!CAUTION]
>  `AddNew` 또는 `Edit`를 먼저 호출 하지 않고 `Update`를 호출 하는 경우 `Update` `CDBException`를 throw 합니다. `AddNew` 또는 `Edit`를 호출 하는 경우 `Move` 작업을 호출 하거나 레코드 집합 또는 데이터 원본 연결을 닫기 전에 `Update`를 호출 해야 합니다. 그렇지 않으면 알림 없이 변경 내용이 손실 됩니다.

`Update` 실패를 처리 하는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 클래스](../../mfc/reference/crecordview-class.md)
