---
description: '자세히 알아보기: CDaoQueryDef 클래스'
title: CDaoQueryDef 클래스
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
ms.openlocfilehash: cb07457746f6fc569823917bc47d43a3e0b41078
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250722"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 클래스

일반적으로 데이터베이스에 저장되는 쿼리 정의 또는 "querydef"를 나타냅니다.

## <a name="syntax"></a>구문

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|`CDaoQueryDef` 개체를 생성합니다. 다음 호출 `Open` 또는 `Create` 요구 사항에 따라 또는입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoQueryDef:: Append](#append)|쿼리 정의를 데이터베이스의 쿼리 정의 컬렉션에 저장 된 쿼리로 추가 합니다.|
|[CDaoQueryDef::CanUpdate](#canupdate)|쿼리에서 데이터베이스를 업데이트할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoQueryDef:: Close](#close)|Querydef 개체를 닫습니다. 완료 되 면 c + + 개체를 삭제 합니다.|
|[CDaoQueryDef:: Create](#create)|기본 DAO 쿼리 정의 개체를 만듭니다. 쿼리 정의를 임시 쿼리로 사용 하거나를 호출 `Append` 하 여 데이터베이스에 저장 합니다.|
|[CDaoQueryDef:: Execute](#execute)|Querydef 개체로 정의 된 쿼리를 실행 합니다.|
|[CDaoQueryDef:: GetConnect](#getconnect)|Querydef와 연결 된 연결 문자열을 반환 합니다. 연결 문자열은 데이터 원본을 식별 합니다. SQL 통과 쿼리만 해당 하는 경우이 고, 그렇지 않으면 빈 문자열입니다.|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|저장 된 쿼리를 만든 날짜를 반환 합니다.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|저장 된 쿼리를 마지막으로 업데이트 한 날짜를 반환 합니다.|
|[CDaoQueryDef:: GetFieldCount](#getfieldcount)|Querydef에서 정의한 필드의 수를 반환 합니다.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|쿼리에 정의 된 지정 된 필드에 대 한 정보를 반환 합니다.|
|[CDaoQueryDef:: GetName](#getname)|Querydef의 이름을 반환 합니다.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|쿼리 정의가 실행 될 때 odbc (ODBC 쿼리의 경우)에서 사용 하는 제한 시간 값을 반환 합니다. 쿼리 작업이 완료 될 때까지 허용 되는 기간을 결정 합니다.|
|[CDaoQueryDef:: GetParameterCount](#getparametercount)|쿼리에 대해 정의 된 매개 변수의 수를 반환 합니다.|
|[CDaoQueryDef:: GetParameterInfo](#getparameterinfo)|쿼리에 대해 지정 된 매개 변수에 대 한 정보를 반환 합니다.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|쿼리에 대해 지정 된 매개 변수의 값을 반환 합니다.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|작업 쿼리의 영향을 받는 레코드 수를 반환 합니다.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Querydef에서 정의한 쿼리가 레코드를 반환 하는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoQueryDef:: GetSQL](#getsql)|Querydef에서 정의한 쿼리를 지정 하는 SQL 문자열을 반환 합니다.|
|[CDaoQueryDef:: GetType](#gettype)|삭제, 업데이트, 추가, 테이블 작성 등 쿼리 유형을 반환 합니다.|
|[CDaoQueryDef:: IsOpen](#isopen)|Querydef가 열려 있고 실행할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoQueryDef:: Open](#open)|데이터베이스의 쿼리 정의 컬렉션에 저장 된 기존 쿼리 정의를 엽니다.|
|[CDaoQueryDef:: SetConnect](#setconnect)|ODBC 데이터 원본에 대 한 SQL 통과 쿼리에 대 한 연결 문자열을 설정 합니다.|
|[CDaoQueryDef:: SetName](#setname)|쿼리 정의를 만들 때 사용 중인 이름을 바꿔서 저장 된 쿼리의 이름을 설정 합니다.|
|[CDaoQueryDef:: SetODBCTimeout](#setodbctimeout)|쿼리 정의가 실행 될 때 odbc (ODBC 쿼리의 경우)에서 사용 하는 제한 시간 값을 설정 합니다.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|쿼리에 대해 지정 된 매개 변수의 값을 설정 합니다.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Querydef가 레코드를 반환 하는지 여부를 지정 합니다. 이 특성을 TRUE로 설정 하는 것은 SQL 통과 쿼리에만 유효 합니다.|
|[CDaoQueryDef:: SetSQL](#setsql)|Querydef에서 정의한 쿼리를 지정 하는 SQL 문자열을 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoQueryDef:: m_pDAOQueryDef](#m_pdaoquerydef)|기본 DAO querydef 개체의 OLE 인터페이스에 대 한 포인터입니다.|
|[CDaoQueryDef:: m_pDatabase](#m_pdatabase)|Querydef가 연결 된 개체에 대 한 포인터 `CDaoDatabase` 입니다. 쿼리 정의는 데이터베이스에 저장 될 수도 있고 그렇지 않을 수도 있습니다.|

## <a name="remarks"></a>설명

Querydef는 쿼리를 설명 하는 SQL 문 및 해당 속성 (예: "작성일" 및 "ODBC Timeout")을 포함 하는 데이터 액세스 개체입니다. 임시 querydef 개체를 저장 하지 않고 만들 수도 있지만 자주 다시 사용 되는 쿼리를 데이터베이스에 저장 하는 것이 편리 하 고 훨씬 효율적입니다. [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체는 저장 된 쿼리를 포함 하는 쿼리 정의 컬렉션 이라는 컬렉션을 유지 관리 합니다.

> [!NOTE]
> DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 여전히 DAO 클래스를 사용 하 여 ODBC 데이터 원본에 액세스할 수 있습니다. 일반적으로 DAO 기반의 MFC 클래스는 ODBC를 기반으로 하는 MFC 클래스 보다 더 사용할 수 있습니다. DAO 기반 클래스는 자체 데이터베이스 엔진을 통해 ODBC 드라이버를 포함 하 여 데이터에 액세스할 수 있습니다. 또한 dao 기반 클래스는 DAO를 직접 호출 하지 않고도 클래스를 통해 테이블을 추가 하는 등의 DDL (데이터 정의 언어) 작업을 지원 합니다.

## <a name="usage"></a>사용

기존에 저장 된 쿼리로 작업 하거나 새 저장 된 쿼리 또는 임시 쿼리를 만들려면 쿼리 정의 개체를 사용 합니다.

1. 모든 경우에는 먼저 `CDaoQueryDef` 쿼리가 속한 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터를 제공 하 여 개체를 생성 합니다.

1. 그런 다음 원하는 항목에 따라 다음을 수행 합니다.

   - 기존에 저장 된 쿼리를 사용 하려면 저장 된 쿼리의 이름을 제공 하 여 querydef 개체의 [Open](#open) 멤버 함수를 호출 합니다.

   - 새 저장 된 쿼리를 만들려면 쿼리 이름을 제공 하 여 querydef 개체의 [create](#create) member 함수를 호출 합니다. 그런 다음 [Append](#append) 를 호출 하 여 쿼리를 데이터베이스의 쿼리 정의 컬렉션에 추가 하 여 쿼리를 저장 합니다. `Create` 는 쿼리 정의를 열린 상태로 전환 하므로를 호출한 후에는를 `Create` 호출 하지 않습니다 `Open` .

   - 임시 querydef를 만들려면를 호출 `Create` 합니다. 쿼리 이름에 대해 빈 문자열을 전달 합니다. `Append`를 호출하지 마세요.

Querydef 개체 사용을 마치면 [Close](#close) 멤버 함수를 호출 합니다. 그런 다음 쿼리 정의 개체를 삭제 합니다.

> [!TIP]
> 저장 된 쿼리를 만드는 가장 쉬운 방법은이를 만들어 Microsoft Access를 사용 하 여 데이터베이스에 저장 하는 것입니다. 그런 다음 MFC 코드에서 열고 사용할 수 있습니다.

## <a name="purposes"></a>것

다음 용도로는 querydef 개체를 사용할 수 있습니다.

- 개체를 만들려면 `CDaoRecordset`

- 개체의 멤버 함수를 호출 하 여 `Execute` 동작 쿼리 또는 SQL 통과 쿼리를 직접 실행 하려면

Select, action, 크로스탭, delete, update, append, 테이블 형식, 데이터 정의, SQL 통과, 공용 구조체 및 대량 쿼리를 비롯 한 모든 유형의 쿼리에 대해 querydef 개체를 사용할 수 있습니다. 쿼리 형식은 사용자가 제공 하는 SQL 문의 내용에 따라 결정 됩니다. 쿼리 유형에 대 한 자세한 내용은 `Execute` 및 [GetType](#gettype) 멤버 함수를 참조 하세요. 레코드 집합은 일반적으로 SELECT ...를 사용 하 여 행을 반환 하는 쿼리에 사용 됩니다. **FROM** 키워드. `Execute` 는 대량 작업에 가장 일반적으로 사용 됩니다. 자세한 내용은 [Execute](#execute) 및 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)을 참조 하세요.

## <a name="querydefs-and-recordsets"></a>쿼리 및 레코드 집합

Querydef 개체를 사용 하 여 개체를 만들려면 `CDaoRecordset` 일반적으로 위에서 설명한 대로 쿼리를 만들거나 엽니다. 그런 다음 [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)을 호출할 때 쿼리 정의 개체에 대 한 포인터를 전달 하 여 레코드 집합 개체를 생성 합니다. 전달 하는 querydef는 열린 상태 여야 합니다. 자세한 내용은 클래스 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)를 참조 하세요.

열 정의를 사용 하 여 열린 상태가 아닌 경우에는 레코드 집합을 만들 수 없습니다 (쿼리 정의에 가장 일반적으로 사용 됨). 또는 중 하나를 호출 하 여 쿼리 정의를 열린 상태로 전환 합니다 `Open` `Create` .

## <a name="external-databases"></a>외부 데이터베이스

쿼리 정의 개체는 외부 데이터베이스 엔진의 기본 SQL 언어를 사용 하는 기본 방법입니다. 예를 들어 Microsoft SQL Server에 사용 되는 Transact-sql 쿼리를 만들고이를 querydef 개체에 저장할 수 있습니다. Microsoft Jet 데이터베이스 엔진을 기반으로 하지 않는 SQL 쿼리를 사용 해야 하는 경우 외부 데이터 원본을 가리키는 연결 문자열을 제공 해야 합니다. 유효한 연결 문자열이 있는 쿼리는 데이터베이스 엔진을 무시 하 고 처리를 위해 쿼리를 외부 데이터베이스 서버에 직접 전달 합니다.

> [!TIP]
> ODBC 테이블로 작업 하는 기본 방법은 Microsoft Jet ()에 연결 하는 것입니다. MDB) 데이터베이스입니다.

관련 정보는 DAO SDK의 "QueryDef 개체", "QueryDef 컬렉션" 및 "CdbDatabase 개체" 항목을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaoquerydefappend"></a><a name="append"></a> CDaoQueryDef:: Append

[Create](#create) 를 호출 하 여 새 querydef 개체를 만든 후이 멤버 함수를 호출 합니다.

```
virtual void Append();
```

### <a name="remarks"></a>설명

`Append` 데이터베이스의 쿼리 정의 컬렉션에 개체를 추가 하 여 쿼리 정의를 데이터베이스에 저장 합니다. Querydef를 추가 하지 않고 임시 개체로 사용할 수 있지만 유지 하려면를 호출 해야 `Append` 합니다.

임시 querydef 개체를 추가 하려고 하면 MFC에서 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다.

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a> CDaoQueryDef::CanUpdate

이 멤버 함수를 호출 하 여 이름 또는 SQL 문자열 변경과 같은 쿼리 정의를 수정할 수 있는지 여부를 확인 합니다.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>반환 값

Querydef를 수정할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

다음과 같은 경우 쿼리 정의를 수정할 수 있습니다.

- 읽기 전용으로 열려 있는 데이터베이스를 기반으로 하지 않습니다.

- 데이터베이스에 대 한 업데이트 권한이 있습니다.

   이는 보안 기능을 구현 했는지 여부에 따라 달라 집니다. MFC는 보안에 대 한 지원을 제공 하지 않습니다. 직접 DAO를 호출 하거나 Microsoft Access를 사용 하 여 직접 구현 해야 합니다. DAO 도움말의 "사용 권한 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a> CDaoQueryDef::CDaoQueryDef

`CDaoQueryDef` 개체를 생성합니다.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>매개 변수

*pDatabase*<br/>
열린 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

개체는 데이터베이스의 쿼리 정의 컬렉션에 저장 된 기존 쿼리 정의, 컬렉션에 저장할 새 쿼리 또는 저장 하지 않을 임시 쿼리를 나타낼 수 있습니다. 다음 단계는 쿼리 정의의 유형에 따라 달라 집니다.

- 개체가 기존 쿼리 정의를 나타내는 경우 개체의 [Open](#open) 멤버 함수를 호출 하 여이를 초기화 합니다.

- 개체가 저장할 새 쿼리 정의를 나타내는 경우 개체의 [Create](#create) member 함수를 호출 합니다. 그러면 데이터베이스의 쿼리 정의 컬렉션에 개체가 추가 됩니다. 그런 다음 `CDaoQueryDef` 멤버 함수를 호출 하 여 개체의 특성을 설정 합니다. 마지막으로 [Append](#append)를 호출 합니다.

- 개체가 임시 쿼리 정의 (데이터베이스에 저장 하지 않음)를 나타내는 경우을 호출 하 여 `Create` 쿼리 이름에 대해 빈 문자열을 전달 합니다. 를 호출한 후에는 `Create` 해당 특성을 직접 설정 하 여 querydef를 초기화 합니다. `Append`를 호출하지 마세요.

Querydef의 특성을 설정 하려면 [SetName](#setname), [setsql](#setsql), [setsql](#setconnect), [setodbctimeout](#setodbctimeout)및 [SetReturnsRecords](#setreturnsrecords) 멤버 함수를 사용할 수 있습니다.

Querydef 개체가 완료 되 면 해당 [Close](#close) 멤버 함수를 호출 합니다. 쿼리 정의에 대 한 포인터가 있는 경우 연산자를 사용 **`delete`** 하 여 c + + 개체를 제거 합니다.

## <a name="cdaoquerydefclose"></a><a name="close"></a> CDaoQueryDef:: Close

Querydef 개체 사용을 마치면이 멤버 함수를 호출 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

Querydef를 닫으면 기본 DAO 개체가 해제 되지만 저장 된 DAO 쿼리 정의 개체 또는 c + + 개체는 삭제 되지 않습니다 `CDaoQueryDef` . 이는 DAO의 데이터베이스의 쿼리 정의 컬렉션에서 쿼리를 삭제 하는 [CDaoDatabase::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)와 다릅니다 (임시 querydef가 아닌 경우).

## <a name="cdaoquerydefcreate"></a><a name="create"></a> CDaoQueryDef:: Create

이 멤버 함수를 호출 하 여 새 저장 된 쿼리나 새 임시 쿼리를 만듭니다.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
데이터베이스에 저장 된 쿼리의 고유한 이름입니다. 문자열에 대 한 자세한 내용은 DAO 도움말에서 "CreateQueryDef 메서드" 항목을 참조 하십시오. 기본값을 적용 하는 경우 빈 문자열은 임시 querydef가 만들어집니다. 이러한 쿼리는 쿼리 정의 컬렉션에 저장 되지 않습니다.

*lpszSQL*<br/>
쿼리를 정의 하는 SQL 문자열입니다. 기본값 NULL을 허용 하는 경우 나중에 [Setsql](#setsql) 을 호출 하 여 문자열을 설정 해야 합니다. 그때 까지는 쿼리가 정의 되지 않습니다. 그러나 정의 되지 않은 쿼리를 사용 하 여 레코드 집합을 열 수 있습니다. 자세한 내용은 설명 부분을 참조 하십시오. 쿼리 정의를 쿼리 정의 컬렉션에 추가 하려면 먼저 SQL 문을 정의 해야 합니다.

### <a name="remarks"></a>설명

*LpszName* 에 이름을 전달 하는 경우 [Append](#append) 를 호출 하 여 데이터베이스의 쿼리 정의 컬렉션에 쿼리 정의를 저장할 수 있습니다. 그렇지 않으면 개체가 임시 querydef 이며 저장 되지 않습니다. 두 경우 모두 쿼리 정의는 열린 상태 이며이를 사용 하 여 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 만들거나 Querydef의 [Execute](#execute) 멤버 함수를 호출할 수 있습니다.

*LpszSQL* 에 SQL 문을 제공 하지 않으면를 사용 하 여 쿼리를 실행할 수 `Execute` 없지만이를 사용 하 여 레코드 집합을 만들 수 있습니다. 이 경우 MFC는 레코드 집합의 기본 SQL 문을 사용 합니다.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a> CDaoQueryDef:: Execute

이 멤버 함수를 호출 하 여 querydef 개체로 정의 된 쿼리를 실행 합니다.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>매개 변수

*nOptions*<br/>
쿼리의 특성을 결정 하는 정수입니다. 관련 내용은 DAO 도움말의 "메서드 실행" 항목을 참조 하십시오. 비트 or 연산자 ( **&#124;**)를 사용 하 여이 인수에 대해 다음 상수를 결합할 수 있습니다.

- `dbDenyWrite` 다른 사용자에 게 쓰기 권한을 거부 합니다.

- `dbInconsistent` 일관 되지 않은 업데이트

- `dbConsistent` 일관성 있는 업데이트.

- `dbSQLPassThrough` SQL 통과. SQL 문이 처리를 위해 ODBC 데이터베이스로 전달 되도록 합니다.

- `dbFailOnError` 기본값입니다. 오류가 발생 하면 업데이트를 롤백하고 사용자에 게 오류를 보고 합니다.

- `dbSeeChanges` 다른 사용자가 편집 중인 데이터를 변경 하는 경우 런타임 오류를 생성 합니다.

> [!NOTE]
> "일관성이 없는" 및 "일관적인" 용어에 대 한 설명은 DAO 도움말의 "메서드 실행" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

이러한 방식으로 실행 하는 데 사용 되는 쿼리 정의 개체는 다음 쿼리 유형 중 하나만 나타낼 수 있습니다.

- 작업 쿼리

- SQL 통과 쿼리

`Execute` select 쿼리와 같이 레코드를 반환 하는 쿼리에는 사용할 수 없습니다. `Execute` 는 **UPDATE**, **INSERT** 또는 **SELECT INTO** 와 같은 대량 작업 쿼리 또는 DDL (데이터 정의 언어) 작업에 일반적으로 사용 됩니다.

> [!TIP]
> ODBC 데이터 원본에 대 한 작업을 수행 하는 기본 방법은 Microsoft Jet (에 테이블을 연결 하는 것입니다. MDB) 데이터베이스입니다. 자세한 내용은 DAO 도움말의 "DAO를 사용 하 여 외부 데이터베이스 액세스" 항목을 참조 하십시오.

Querydef 개체의 [GetRecordsAffected](#getrecordsaffected) 멤버 함수를 호출 하 여 가장 최근 호출의 영향을 받는 레코드 수를 확인 합니다 `Execute` . 예를 들어은 `GetRecordsAffected` 동작 쿼리를 실행할 때 삭제, 업데이트 또는 삽입 된 레코드 수에 대 한 정보를 반환 합니다. 연속 업데이트 또는 삭제가 적용 되는 경우 반환 되는 개수는 관련 테이블의 변경 내용을 반영 하지 않습니다.

및를 모두 포함 하는 경우 또는를 모두 포함 하는 경우 `dbInconsistent` `dbConsistent` 결과는 기본값입니다 `dbInconsistent` .

`Execute` 는 레코드 집합을 반환 하지 않습니다. `Execute`레코드를 선택 하는 쿼리에서를 사용 하면 MFC에서 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다.

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a> CDaoQueryDef:: GetConnect

이 멤버 함수를 호출 하 여 querydef의 데이터 소스와 연결 된 연결 문자열을 가져옵니다.

```
CString GetConnect();
```

### <a name="return-value"></a>반환 값

쿼리 정의에 대 한 연결 문자열을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

이 함수는 ODBC 데이터 원본 및 특정 ISAM 드라이버 에서만 사용 됩니다. Microsoft Jet ()와 함께 사용 되지 않습니다. MDB) 데이터베이스 이 경우는 `GetConnect` 빈 문자열을 반환 합니다. 자세한 내용은 [Setconnect](#setconnect)를 참조 하세요.

> [!TIP]
> ODBC 테이블로 작업 하는 기본 방법은에 연결 하는 것입니다. MDB 데이터베이스. 자세한 내용은 DAO 도움말의 "DAO를 사용 하 여 외부 데이터베이스 액세스" 항목을 참조 하십시오.

연결 문자열에 대 한 자세한 내용은 DAO 도움말의 "연결 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a> CDaoQueryDef::GetDateCreated

이 멤버 함수를 호출 하 여 querydef 개체가 만들어진 날짜를 가져옵니다.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>반환 값

Querydef를 만든 날짜와 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다.

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoQueryDef::GetDateLastUpdated

해당 속성 (예: 이름, SQL 문자열 또는 연결 문자열)이 변경 된 경우이 멤버 함수를 호출 하 여 querydef 개체가 마지막으로 업데이트 된 날짜를 가져옵니다.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>반환 값

Querydef가 마지막으로 업데이트 된 날짜와 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다.

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a> CDaoQueryDef:: GetFieldCount

쿼리에서 필드 수를 검색 하려면이 멤버 함수를 호출 합니다.

```
short GetFieldCount();
```

### <a name="return-value"></a>반환 값

쿼리에 정의 된 필드 수입니다.

### <a name="remarks"></a>설명

`GetFieldCount` 는 querydef의 모든 필드를 반복 하는 데 유용 합니다. 이러한 목적을 위해 `GetFieldCount` [getfieldinfo](#getfieldinfo)와 함께를 사용 합니다.

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoQueryDef:: GetFieldInfo

이 멤버 함수를 호출 하 여 querydef에 정의 된 필드에 대 한 다양 한 종류의 정보를 가져옵니다.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 querydef의 Fields 컬렉션에서 원하는 필드의 인덱스 (0부터 시작)입니다.

*fieldinfo*<br/>
`CDaoFieldInfo`요청 된 정보를 반환 하는 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 필드에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 작업과 함께 여기에 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 형식, 크기, 특성

- AFX_DAO_SECONDARY_INFO 기본 정보 더하기: 서 수 위치, 필수, 0 길이 허용, 원본 필드, 외래 이름, 원본 테이블, 정렬 순서

- 기본 및 보조 정보와 AFX_DAO_ALL_INFO 기본값, 유효성 검사 텍스트, 유효성 검사 규칙을 추가 합니다.

*lpszName*<br/>
이름으로 조회 하기 위해 원하는 필드의 이름을 포함 하는 문자열입니다. [CString](../../atl-mfc-shared/reference/cstringt-class.md)을 사용할 수 있습니다.

### <a name="remarks"></a>설명

*Fieldinfo* 에 반환 되는 정보에 대 한 설명은 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조체를 참조 하세요. 이 구조에는 위의 *Dwinfooptions* 에 설명 된 정보에 해당 하는 멤버가 있습니다. 한 수준의 정보를 요청 하는 경우 모든 이전 수준의 정보를 얻을 수 있습니다.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a> CDaoQueryDef:: GetName

이 멤버 함수를 호출 하 여 querydef가 나타내는 쿼리 이름을 검색 합니다.

```
CString GetName();
```

### <a name="return-value"></a>반환 값

쿼리의 이름입니다.

### <a name="remarks"></a>설명

Querydef 이름은 고유한 사용자 정의 이름입니다. 쿼리 정의 이름에 대 한 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a> CDaoQueryDef::GetODBCTimeout

ODBC 데이터 원본에 대 한 쿼리 시간이 초과 되기 전에 현재 시간 제한을 검색 하려면이 멤버 함수를 호출 합니다.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>반환 값

쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다.

### <a name="remarks"></a>설명

이 시간 제한에 대 한 자세한 내용은 DAO 도움말의 "ODBCTimeout 속성" 항목을 참조 하십시오.

> [!TIP]
> ODBC 테이블로 작업 하는 기본 방법은 Microsoft Jet ()에 연결 하는 것입니다. MDB) 데이터베이스입니다. 자세한 내용은 DAO 도움말의 "DAO를 사용 하 여 외부 데이터베이스 액세스" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a> CDaoQueryDef:: GetParameterCount

이 멤버 함수를 호출 하 여 저장 된 쿼리의 매개 변수 수를 검색 합니다.

```
short GetParameterCount();
```

### <a name="return-value"></a>반환 값

쿼리에 정의 된 매개 변수의 수입니다.

### <a name="remarks"></a>설명

`GetParameterCount` 는 쿼리 정의의 모든 매개 변수를 반복 하는 데 유용 합니다. 이러한 목적을 위해 `GetParameterCount` [GetParameterInfo](#getparameterinfo)와 함께를 사용 합니다.

관련 정보는 DAO 도움말의 "매개 변수 개체", "매개 변수 컬렉션" 및 "매개 변수 선언 (SQL)" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a> CDaoQueryDef:: GetParameterInfo

이 멤버 함수를 호출 하 여 querydef에 정의 된 매개 변수에 대 한 정보를 가져옵니다.

```cpp
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 querydef의 Parameters 컬렉션에서 원하는 매개 변수의 인덱스 (0부터 시작)입니다.

*paraminfo*<br/>
요청 된 정보를 반환 하는 [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 매개 변수에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 항목과 함께 여기에 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 형식

*lpszName*<br/>
이름으로 조회 하기 위해 원하는 매개 변수의 이름을 포함 하는 문자열입니다. [CString](../../atl-mfc-shared/reference/cstringt-class.md)을 사용할 수 있습니다.

### <a name="remarks"></a>설명

*Paraminfo* 에 반환 되는 정보에 대 한 설명은 [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) 구조체를 참조 하세요. 이 구조에는 위의 *Dwinfooptions* 에 설명 된 정보에 해당 하는 멤버가 있습니다.

관련 내용은 DAO 도움말의 "PARAMETERS 선언 (SQL)" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a> CDaoQueryDef::GetParamValue

이 멤버 함수를 호출 하 여 querydef의 Parameters 컬렉션에 저장 된 지정 된 매개 변수의 현재 값을 검색 합니다.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
이름을 기준으로 조회 하는 데 사용할 값이 있는 매개 변수의 이름입니다.

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 querydef의 Parameters 컬렉션에 있는 매개 변수의 인덱스 (0부터 시작)입니다. [Getparametercount](#getparametercount) 및 [GetParameterInfo](#getparameterinfo)에 대 한 호출을 사용 하 여이 값을 가져올 수 있습니다.

### <a name="return-value"></a>반환 값

매개 변수의 값을 포함 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 클래스의 개체입니다.

### <a name="remarks"></a>설명

이름 또는 컬렉션의 서 수 위치를 기준으로 매개 변수에 액세스할 수 있습니다.

관련 내용은 DAO 도움말의 "PARAMETERS 선언 (SQL)" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a> CDaoQueryDef::GetRecordsAffected

이 멤버 함수를 호출 하 여 마지막 [실행](#execute)호출의 영향을 받은 레코드 수를 확인 합니다.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>반환 값

영향을 받은 레코드 수입니다.

### <a name="remarks"></a>설명

연속 업데이트 또는 삭제가 적용 되는 경우 반환 되는 개수는 관련 테이블의 변경 내용을 반영 하지 않습니다.

관련 정보는 DAO 도움말의 "RecordsAffected 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a> CDaoQueryDef::GetReturnsRecords

이 멤버 함수를 호출 하 여 쿼리 정의가 레코드를 반환 하는 쿼리를 기반으로 하는지 여부를 확인 합니다.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>반환 값

Querydef가 레코드를 반환 하는 쿼리를 기반으로 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 SQL 통과 쿼리에만 사용 됩니다. SQL 쿼리에 대 한 자세한 내용은 [Execute](#execute) member 함수를 참조 하세요. SQL 통과 쿼리를 사용 하는 방법에 대 한 자세한 내용은 [SetReturnsRecords](#setreturnsrecords) 멤버 함수를 참조 하세요.

관련 내용은 DAO 도움말의 "ReturnsRecords 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a> CDaoQueryDef:: GetSQL

이 멤버 함수를 호출 하 여 querydef의 기반이 되는 쿼리를 정의 하는 SQL 문을 검색 합니다.

```
CString GetSQL();
```

### <a name="return-value"></a>반환 값

Querydef의 기반이 되는 쿼리를 정의 하는 SQL 문입니다.

### <a name="remarks"></a>설명

그러면 키워드, 테이블 이름 등의 문자열을 구문 분석할 수 있습니다.

관련 내용은 DAO 도움말의 "SQL 속성", "Microsoft Jet 데이터베이스 엔진 SQL 및 ANSI SQL의 비교" 및 "코드에서 SQL을 사용 하 여 데이터베이스 쿼리" 항목을 참조 하십시오.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a> CDaoQueryDef:: GetType

이 멤버 함수를 호출 하 여 쿼리 정의의 쿼리 유형을 결정 합니다.

```
short GetType();
```

### <a name="return-value"></a>반환 값

Querydef에서 정의한 쿼리 유형입니다. 값은 주의를 참조 하세요.

### <a name="remarks"></a>설명

쿼리 형식은 쿼리 정의를 만들거나 기존 querydef의 [setsql](#setsql) 멤버 함수를 호출할 때 QUERYDEF의 SQL 문자열에 지정 하는 내용에 의해 설정 됩니다. 이 함수에서 반환 하는 쿼리 형식은 다음 값 중 하나일 수 있습니다.

- `dbQSelect` [

- `dbQAction` 동작

- `dbQCrosstab` 세부

- `dbQDelete` Delete

- `dbQUpdate` Update

- `dbQAppend` 추가할

- `dbQMakeTable` 테이블 만들기

- `dbQDDL` 데이터 정의

- `dbQSQLPassThrough` 통과

- `dbQSetOperation` 부분

- `dbQSPTBulk` 에서 `dbQSQLPassThrough` 레코드를 반환 하지 않는 쿼리를 지정 하는 데 사용 됩니다.

> [!NOTE]
> SQL 통과 쿼리를 만들려면 상수를 설정 하지 마십시오 `dbSQLPassThrough` . 이는 querydef 개체를 만들고 연결 문자열을 설정할 때 Microsoft Jet 데이터베이스 엔진에 의해 자동으로 설정 됩니다.

SQL 문자열에 대 한 자세한 내용은 [Getsql](#getsql)을 참조 하세요. 쿼리 유형에 대 한 자세한 내용은 [Execute](#execute)를 참조 하십시오.

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a> CDaoQueryDef:: IsOpen

이 멤버 함수를 호출 하 여 개체가 현재 열려 있는지 여부를 확인 `CDaoQueryDef` 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

개체가 현재 열려 있으면 0이 아니고 `CDaoQueryDef` , 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Querydef를 사용 하 여 [Execute](#execute) 를 호출 하거나 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 만들려면 먼저 querydef가 열린 상태 여야 합니다. Open (새 querydef의 경우) 또는 [open](#open) (기존 쿼리 정의의 경우 [) 중 하나](#create) 를 열린 상태 호출에 삽입 합니다.

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a> CDaoQueryDef:: m_pDatabase

Querydef 개체와 연결 된 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

데이터베이스에 직접 액세스 해야 하는 경우 (예: 데이터베이스의 컬렉션에 있는 다른 쿼리 정의 또는 레코드 집합 개체에 대 한 포인터를 얻기 위해)이 포인터를 사용 합니다.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a> CDaoQueryDef:: m_pDAOQueryDef

기본 DAO querydef 개체의 OLE 인터페이스에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

이 포인터는 다른 클래스와의 완전성 및 일관성을 위해 제공 됩니다. 그러나 MFC는 DAO 쿼리 정의를 완전히 캡슐화 하기 때문에 필요 하지 않습니다. 이를 사용 하는 경우 주의 해야 합니다. 특히, 수행 하 고 있는 작업을 알고 있지 않으면 포인터 값을 변경 하지 마십시오.

## <a name="cdaoquerydefopen"></a><a name="open"></a> CDaoQueryDef:: Open

이 멤버 함수를 호출 하 여 이전에 데이터베이스의 쿼리 정의 컬렉션에 저장 된 쿼리 정의를 엽니다.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
열려는 저장 된 쿼리 정의의 이름을 포함 하는 문자열입니다. [CString](../../atl-mfc-shared/reference/cstringt-class.md)을 사용할 수 있습니다.

### <a name="remarks"></a>설명

Querydef가 열리면 해당 [Execute](#execute) 멤버 함수를 호출 하거나 querydef를 사용 하 여 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 만들 수 있습니다.

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a> CDaoQueryDef:: SetConnect

이 멤버 함수를 호출 하 여 querydef 개체의 연결 문자열을 설정 합니다.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>매개 변수

*lpszConnect*<br/>
연결 된 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 연결 문자열을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

연결 문자열은 필요에 따라 ODBC 및 특정 ISAM 드라이버에 추가 정보를 전달 하는 데 사용 됩니다. Microsoft Jet ()에는 사용 되지 않습니다. MDB) 데이터베이스.

> [!TIP]
> ODBC 테이블로 작업 하는 기본 방법은에 연결 하는 것입니다. MDB 데이터베이스.

ODBC 데이터 원본에 대 한 SQL 통과 쿼리를 나타내는 querydef를 실행 하기 전에 연결 문자열을로 설정 하 `SetConnect` 고 [SetReturnsRecords](#setreturnsrecords) 를 호출 하 여 쿼리가 레코드를 반환 하는지 여부를 지정 합니다.

연결 문자열의 구조와 연결 문자열 구성 요소의 예에 대 한 자세한 내용은 DAO 도움말의 "연결 속성" 항목을 참조 하십시오.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a> CDaoQueryDef:: SetName

임시가 아닌 querydef의 이름을 변경 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
연결 된 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체의 임시 쿼리가 아닌 새 이름을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

Querydef 이름은 고유한 사용자 정의 이름입니다. `SetName`Querydef 개체를 쿼리 정의 컬렉션에 추가 하기 전에를 호출할 수 있습니다.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a> CDaoQueryDef:: SetODBCTimeout

이 멤버 함수를 호출 하 여 ODBC 데이터 원본에 대 한 쿼리가 시간 초과 되기 전의 시간 제한을 설정 합니다.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>매개 변수

*nODBCTimeout*<br/>
쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 사용 하면 연결 된 데이터 원본에 대 한 후속 작업의 "제한 시간"을 기준으로 기본 시간 (초)을 재정의할 수 있습니다. 네트워크 액세스 문제, 과도 한 쿼리 처리 시간 등으로 인해 작업 시간이 초과 될 수 있습니다. `SetODBCTimeout`쿼리 제한 시간 값을 변경 하려는 경우이 querydef를 사용 하 여 쿼리를 실행 하기 전에를 호출 합니다. ODBC가 연결을 다시 사용할 때 동일한 연결의 모든 클라이언트에 대 한 시간 제한 값은 동일 합니다.

쿼리 시간 제한의 기본값은 60 초입니다.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a> CDaoQueryDef::SetParamValue

런타임에 쿼리 정의의 매개 변수 값을 설정 하려면이 멤버 함수를 호출 합니다.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
값을 설정 하려는 매개 변수의 이름입니다.

*varValue*<br/>
설정할 값입니다. 설명을 참조 하세요.

*nIndex*<br/>
Querydef의 Parameters 컬렉션에 있는 매개 변수의 서 수 위치입니다. [Getparametercount](#getparametercount) 및 [GetParameterInfo](#getparameterinfo)에 대 한 호출을 사용 하 여이 값을 가져올 수 있습니다.

### <a name="remarks"></a>설명

매개 변수가 이미 querydef의 SQL 문자열의 일부로 설정 되어 있어야 합니다. 이름 또는 컬렉션의 서 수 위치를 기준으로 매개 변수에 액세스할 수 있습니다.

개체로 설정할 값을 지정 합니다 `COleVariant` . 개체에서 원하는 값 및 형식을 설정 하는 방법에 대 한 자세한 내용은 `COleVariant` 클래스 [COleVariant](../../mfc/reference/colevariant-class.md)를 참조 하세요.

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a> CDaoQueryDef::SetReturnsRecords

외부 데이터베이스에 대 한 SQL 통과 쿼리를 설정 하는 프로세스의 일부로이 멤버 함수를 호출 합니다.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>매개 변수

*bReturnsRecords*<br/>
외부 데이터베이스에 대 한 쿼리에서 레코드를 반환 하는 경우 TRUE를 전달 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이러한 경우에는 쿼리 정의를 만들고 다른 멤버 함수를 사용 하 여 해당 속성을 설정 해야 합니다 `CDaoQueryDef` . 외부 데이터베이스에 대 한 설명은 [Setconnect](#setconnect)를 참조 하세요.

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a> CDaoQueryDef:: SetSQL

이 멤버 함수를 호출 하 여 querydef가 실행 하는 SQL 문을 설정 합니다.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>매개 변수

*lpszSQL*<br/>
실행에 적합 한 전체 SQL 문을 포함 하는 문자열입니다. 이 문자열의 구문은 쿼리에서 대상으로 하는 DBMS에 따라 다릅니다. Microsoft Jet 데이터베이스 엔진에서 사용 하는 구문에 대 한 설명은 DAO 도움말의 "코드에서 SQL 문 작성" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

의 일반적인 용도는 `SetSQL` SQL 통과 쿼리에서 사용할 쿼리 정의 개체를 설정 하는 것입니다. 대상 DBMS에 대 한 SQL 통과 쿼리의 구문은 DBMS에 대 한 설명서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException 클래스](../../mfc/reference/cdaoexception-class.md)
