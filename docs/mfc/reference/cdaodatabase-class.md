---
description: '자세히 알아보기: CDaoDatabase 클래스'
title: CDaoDatabase 클래스
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 2044f24c2485071e0fa8930956e8ea15753047ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250974"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase 클래스

DAO (Data Access Objects)를 사용 하는 Access 데이터베이스에 대 한 연결을 나타냅니다. DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|`CDaoDatabase` 개체를 생성합니다. `Open`을 호출 하 여 개체를 데이터베이스에 연결 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|데이터베이스가 트랜잭션을 지원 하면 0이 아닌 값을 반환 합니다.|
|[CDaoDatabase::CanUpdate](#canupdate)|개체를 업데이트할 수 있으면 0이 아닌 값을 반환 `CDaoDatabase` 합니다 (읽기 전용 아님).|
|[CDaoDatabase::Close](#close)|데이터베이스 연결을 닫습니다.|
|[CDaoDatabase:: Create](#create)|기본 DAO 데이터베이스 개체를 만들고 개체를 초기화 `CDaoDatabase` 합니다.|
|[CDaoDatabase:: CreateRelation](#createrelation)|데이터베이스의 테이블 간에 새 관계를 정의 합니다.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|데이터베이스의 쿼리 정의 컬렉션에 저장 된 쿼리 정의 개체를 삭제 합니다.|
|[CDaoDatabase::D eleteRelation](#deleterelation)|데이터베이스의 테이블 간 기존 관계를 삭제 합니다.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|데이터베이스의 테이블 정의를 삭제 합니다. 이렇게 하면 실제 테이블과 모든 데이터가 삭제 됩니다.|
|[CDaoDatabase:: Execute](#execute)|작업 쿼리를 실행 합니다. `Execute`결과를 반환 하는 쿼리에 대해를 호출 하면 예외가 throw 됩니다.|
|[CDaoDatabase::GetConnect](#getconnect)|개체를 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 반환 합니다 `CDaoDatabase` . ODBC에 사용 됩니다.|
|[CDaoDatabase::GetName](#getname)|현재 사용 중인 데이터베이스의 이름을 반환 합니다.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|데이터베이스에 대해 정의 된 쿼리 수를 반환 합니다.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|데이터베이스에 정의 된 지정 된 쿼리에 대 한 정보를 반환 합니다.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|데이터베이스 쿼리 작업의 제한 시간 (초)을 반환 합니다. 모든 후속 열기, 추가 새로 고침, 업데이트 및 편집 작업과 ODBC 데이터 원본 (예: 호출)에 대 한 기타 작업에 영향을 줍니다 `Execute` .|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|마지막 업데이트, 편집 또는 추가 작업 또는에 대 한 호출의 영향을 받는 레코드 수를 반환 합니다 `Execute` .|
|[CDaoDatabase:: GetRelationCount](#getrelationcount)|데이터베이스의 테이블 간에 정의 된 관계의 수를 반환 합니다.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|데이터베이스의 테이블 간에 정의 된 지정 된 관계에 대 한 정보를 반환 합니다.|
|[CDaoDatabase:: GetTableDefCount](#gettabledefcount)|데이터베이스에 정의 된 테이블의 수를 반환 합니다.|
|[CDaoDatabase:: GetTableDefInfo](#gettabledefinfo)|데이터베이스의 지정 된 테이블에 대 한 정보를 반환 합니다.|
|[CDaoDatabase:: GetVersion](#getversion)|데이터베이스와 연결 된 데이터베이스 엔진의 버전을 반환 합니다.|
|[CDaoDatabase::IsOpen](#isopen)|`CDaoDatabase`개체가 현재 데이터베이스에 연결 되어 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoDatabase::Open](#open)|데이터베이스에 대 한 연결을 설정 합니다.|
|[CDaoDatabase:: SetQueryTimeout](#setquerytimeout)|데이터베이스 쿼리 작업 (ODBC 데이터 원본에만 해당)이 제한 시간을 초과 하는 시간 (초)을 설정 합니다. 모든 후속 열기, 새로 추가, 업데이트 및 삭제 작업에 영향을 줍니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoDatabase:: m_pDAODatabase](#m_pdaodatabase)|기본 DAO 데이터베이스 개체에 대 한 포인터입니다.|
|[CDaoDatabase:: m_pWorkspace](#m_pworkspace)|데이터베이스를 포함 하 고 해당 트랜잭션 공간을 정의 하는 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 개체에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

지원 되는 데이터베이스 형식에 대 한 자세한 내용은 [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) 멤버 함수를 참조 하세요. [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 개체로 표시되는 지정된 "작업 영역"에서 한 번에 하나 이상의 `CDaoDatabase` 개체를 활성화할 수 있습니다. 작업 영역은 Databases 컬렉션 이라고 하는 open database 개체의 컬렉션을 유지 관리 합니다.

## <a name="usage"></a>사용

레코드 집합 개체를 만들 때 데이터베이스 개체를 암시적으로 만들 수 있습니다. 그러나 데이터베이스 개체를 명시적으로 만들 수도 있습니다. 에서 기존 데이터베이스를 명시적으로 사용 하려면 `CDaoDatabase` 다음 중 하나를 수행 합니다.

- `CDaoDatabase` 개체를 생성하여 열려 있는 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 개체에 대한 포인터를 전달합니다.

- 또는 `CDaoDatabase` 작업 영역을 지정 하지 않고 개체를 생성 합니다. (MFC는 임시 작업 영역 개체를 만듭니다.)

새 Microsoft Jet (. MDB) 데이터베이스를 생성 하 `CDaoDatabase` 고, 개체를 생성 하 고, 해당 [Create](#create) member 함수를 호출 합니다. 이후에를 호출 *하지* 마세요 `Open` `Create` .

기존 데이터베이스를 열려면 개체를 생성 하 `CDaoDatabase` 고 해당 개체의 [open](#open) 멤버 함수를 호출 합니다.

이러한 방법 중 하나는 작업 영역 데이터베이스 컬렉션에 DAO 데이터베이스 개체를 추가 하 고 데이터에 대 한 연결을 엽니다. 그런 다음 연결 된 데이터베이스에서 작동 하는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)또는 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 개체를 구성 하는 경우 이러한 개체의 생성자를 개체에 대 한 포인터로 전달 합니다 `CDaoDatabase` . 연결 사용을 마치면 [Close](#close) 멤버 함수를 호출 하 고 개체를 삭제 `CDaoDatabase` 합니다. `Close` 이전에 닫지 않은 레코드 집합을 모두 닫습니다.

## <a name="transactions"></a>트랜잭션

데이터베이스 트랜잭션 처리는 작업 영역 수준에서 제공 됩니다. 클래스의 [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)및 [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) 멤버 함수를 참조 하세요 `CDaoWorkspace` .

## <a name="odbc-connections"></a>ODBC 연결

ODBC 데이터 원본에 대 한 작업을 수행 하는 데 권장 되는 방법은 외부 테이블을 Microsoft Jet (에 연결 하는 것입니다. MDB) 데이터베이스입니다.

## <a name="collections"></a>컬렉션

각 데이터베이스는 고유한 테이블 정의, 쿼리 정의, 레코드 집합 및 관계 개체의 컬렉션을 유지 합니다. 클래스 `CDaoDatabase` 는 이러한 개체를 조작 하기 위한 멤버 함수를 제공 합니다.

> [!NOTE]
> 개체는 MFC 데이터베이스 개체가 아닌 DAO에 저장 됩니다. MFC는 테이블 정의, 쿼리 정의 및 레코드 집합 개체에 대 한 클래스를 제공 하지만 관계 개체는 제공 하지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a> CDaoDatabase:: CanTransact

데이터베이스가 트랜잭션을 허용 하는지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL CanTransact();
```

### <a name="return-value"></a>반환 값

데이터베이스가 트랜잭션을 지 원하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

트랜잭션은 데이터베이스의 작업 영역에서 관리 됩니다.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a> CDaoDatabase:: CanUpdate

이 멤버 함수를 호출 하 여 개체가 업데이트를 허용 하는지 여부를 확인 `CDaoDatabase` 합니다.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>반환 값

개체에서 업데이트를 허용 하는 경우 0이 아니고, `CDaoDatabase` 그렇지 않으면 0입니다 .이 값은 개체를 열 때 *BREADONLY* 에 TRUE를 전달 `CDaoDatabase` 했거나 데이터베이스 자체를 읽기 전용으로 지정 했음을 나타냅니다. [Open](#open) 멤버 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터베이스 업데이트 가능성에 대 한 자세한 내용은 DAO 도움말의 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a> CDaoDatabase:: CDaoDatabase

`CDaoDatabase` 개체를 생성합니다.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>매개 변수

*pWorkspace*<br/>
새 데이터베이스 개체를 포함 하는 개체에 대 한 포인터입니다 `CDaoWorkspace` . 기본값 NULL을 적용 하면 생성자는 `CDaoWorkspace` 기본 DAO 작업 영역을 사용 하는 임시 개체를 만듭니다. [M_pWorkspace](#m_pworkspace) 데이터 멤버를 통해 작업 영역 개체에 대 한 포인터를 가져올 수 있습니다.

### <a name="remarks"></a>설명

개체를 생성 한 후 새 Microsoft Jet (. MDB) 데이터베이스에서 개체의 [Create](#create) member 함수를 호출 합니다. 사용자가 아닌 경우 기존 데이터베이스를 열 때 개체의 [Open](#open) 멤버 함수를 호출 합니다.

개체를 마치면 [Close](#close) 멤버 함수를 호출 하 고 개체를 제거 해야 합니다 `CDaoDatabase` .

문서 클래스에 개체를 포함 하는 것이 편리할 수 있습니다 `CDaoDatabase` .

> [!NOTE]
> `CDaoDatabase`기존 개체에 대 한 포인터를 전달 하지 않고 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 여는 경우에도 개체를 암시적으로 만듭니다 `CDaoDatabase` . 이 데이터베이스 개체는 레코드 집합 개체를 닫을 때 닫힙니다.

## <a name="cdaodatabaseclose"></a><a name="close"></a> CDaoDatabase:: Close

이 멤버 함수를 호출 하 여 데이터베이스에서 연결을 끊고 데이터베이스와 연결 된 열려 있는 모든 레코드 집합, 테이블 정의 및 쿼리 정의를 닫습니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하기 전에 이러한 개체를 직접 닫는 것이 좋습니다. 개체를 닫으면 `CDaoDatabase` 연결 된 [작업 영역의](../../mfc/reference/cdaoworkspace-class.md)데이터베이스 컬렉션에서 개체가 제거 됩니다. `Close`는 개체를 삭제 하지 않으므로 `CDaoDatabase` 동일한 데이터베이스 또는 다른 데이터베이스를 열어 개체를 다시 사용할 수 있습니다.

> [!CAUTION]
> 데이터베이스를 닫기 전에 [업데이트](../../mfc/reference/cdaorecordset-class.md#update) 멤버 함수 (보류 중인 편집 내용이 있는 경우)를 호출 하 고 `Close` 열려 있는 모든 레코드 집합 개체에 대해 멤버 함수를 호출 합니다. 스택에서 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 또는 개체를 선언 하는 함수를 종료 하면 `CDaoDatabase` 데이터베이스가 닫히고 저장 되지 않은 변경 내용이 모두 손실 되며, 보류 중인 모든 트랜잭션이 롤백되고 보류 중인 데이터 편집 내용이 모두 손실 됩니다.

> [!CAUTION]
> 레코드 집합 개체가 열려 있는 동안 데이터베이스 개체를 닫거나 해당 특정 작업 영역에 속하는 데이터베이스 개체가 열려 있는 상태에서 작업 영역 개체를 닫으려고 하면 해당 레코드 집합 개체가 닫히고 보류 중인 업데이트나 편집 내용이 롤백됩니다. 작업 영역 개체에 속한 데이터베이스 개체가 열려 있는 동안 작업 영역 개체를 닫으려고 하면 해당 작업 영역 개체에 속하는 모든 데이터베이스 개체가 닫히고이로 인해 닫히지 않은 레코드 집합 개체가 닫힐 수 있습니다. 데이터베이스 개체를 닫지 않으면 MFC는 디버그 빌드에서 어설션 오류를 보고 합니다.

데이터베이스 개체가 함수 범위 외부에서 정의 되 고 함수를 닫지 않고 종료 하는 경우 데이터베이스 개체는 명시적으로 닫히거나 정의 된 모듈이 범위를 벗어날 때까지 열린 상태로 유지 됩니다.

## <a name="cdaodatabasecreate"></a><a name="create"></a> CDaoDatabase:: Create

새 Microsoft Jet (. MDB) 데이터베이스에서 개체를 생성 한 후이 멤버 함수를 호출 `CDaoDatabase` 합니다.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
만들려는 데이터베이스 파일의 이름인 문자열 식입니다. 전체 경로 및 파일 이름 (예: "C: \\ \MYDB. MDB ". 이름을 제공 해야 합니다. 파일 이름 확장명을 제공 하지 않으면입니다. MDB가 추가 됩니다. 네트워크에서 UNC (uniform 명명 규칙)를 지 원하는 경우 " \\ \\ \\ \myserver \\ \MYSHARE \\ \MYDIR \\ \MYDB"와 같은 네트워크 경로를 지정할 수도 있습니다. Microsoft Jet만 (. MDB)이 멤버 함수를 사용 하 여 데이터베이스 파일을 만들 수 있습니다. " \\ "은 c + + 이스케이프 문자 이므로 문자열 리터럴에 이중 백슬래시가 필요 합니다.

*lpszLocale*<br/>
데이터베이스를 만들기 위한 정렬 순서를 지정 하는 데 사용 되는 문자열 식입니다. 기본값은 `dbLangGeneral`입니다. 가능한 값은 다음과 같습니다.

- `dbLangGeneral` 영어, 독일어, 프랑스어, 포르투갈어, 이탈리아어 및 현대 스페인어

- `dbLangArabic` 아랍어

- `dbLangCyrillic` 러시아어

- `dbLangCzech` 체코어

- `dbLangDutch` 네덜란드어

- `dbLangGreek` 그리스어

- `dbLangHebrew` 히브리어

- `dbLangHungarian` 헝가리어

- `dbLangIcelandic` 아이슬란드어

- `dbLangNordic` 북유럽어 언어 (Microsoft Jet 데이터베이스 엔진 버전 1.0에만 해당)

- `dbLangNorwdan` 노르웨이어 및 덴마크어

- `dbLangPolish` 폴란드어

- `dbLangSpanish` 전통 스페인어

- `dbLangSwedfin` 스웨덴어 및 핀란드어

- `dbLangTurkish` 터키어

*dwOptions*<br/>
하나 이상의 옵션을 나타내는 정수입니다. 가능한 값은 다음과 같습니다.

- `dbEncrypt` 암호화 된 데이터베이스를 만듭니다.

- `dbVersion10` Microsoft Jet 데이터베이스 버전 1.0을 사용 하 여 데이터베이스를 만듭니다.

- `dbVersion11` Microsoft Jet 데이터베이스 버전 1.1을 사용 하 여 데이터베이스를 만듭니다.

- `dbVersion20` Microsoft Jet 데이터베이스 버전 2.0을 사용 하 여 데이터베이스를 만듭니다.

- `dbVersion30` Microsoft Jet 데이터베이스 버전 3.0을 사용 하 여 데이터베이스를 만듭니다.

암호화 상수를 생략 하면 암호화 되지 않은 데이터베이스가 만들어집니다. 하나의 버전 상수만 지정할 수 있습니다. 버전 상수를 생략 하면 Microsoft Jet 데이터베이스 버전 3.0을 사용 하는 데이터베이스가 만들어집니다.

> [!CAUTION]
> 데이터베이스가 암호화 되지 않은 경우 사용자/암호 보안을 구현 하는 경우에도 데이터베이스를 구성 하는 이진 디스크 파일을 직접 읽을 수 있습니다.

### <a name="remarks"></a>설명

`Create` 데이터베이스 파일 및 기본 DAO 데이터베이스 개체를 만들고 c + + 개체를 초기화 합니다. 연결 된 작업 영역의 데이터베이스 컬렉션에 개체가 추가 됩니다. 데이터베이스 개체가 열려 있는 상태입니다. 이후에를 호출 하지 마세요 `Open*` `Create` .

> [!NOTE]
> 을 사용 하 여 `Create` Microsoft Jet만 만들 수 있습니다. MDB) 데이터베이스. ISAM 데이터베이스 또는 ODBC 데이터베이스를 만들 수 없습니다.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a> CDaoDatabase:: CreateRelation

이 멤버 함수를 호출 하 여 데이터베이스의 기본 테이블에 있는 하나 이상의 필드와 외래 테이블 (데이터베이스의 다른 테이블)에 있는 하나 이상의 필드 간의 관계를 설정 합니다.

```cpp
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
관계 개체의 고유 이름입니다. 이름은 문자로 시작 해야 하며 최대 40 자를 포함할 수 있습니다. 숫자 및 밑줄 문자를 포함할 수 있지만 문장 부호 또는 공백을 포함할 수 없습니다.

*lpszTable*<br/>
관계에 있는 기본 테이블의 이름입니다. 테이블이 없는 경우 MFC에서 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다.

*lpszForeignTable*<br/>
관계에 있는 외래 테이블의 이름입니다. 테이블이 없는 경우 MFC는 형식의 예외를 throw `CDaoException` 합니다.

*lAttributes*<br/>
관계 형식에 대 한 정보를 포함 하는 long 값입니다. 다른 작업 중에이 값을 사용 하 여 참조 무결성을 적용할 수 있습니다. 비트 or 연산자 ( **&#124;**)를 사용 하 여 다음 값을 결합할 수 있습니다 (조합이 적합 한 경우).

- `dbRelationUnique` 일 대 일 관계입니다.

- `dbRelationDontEnforce` 관계는 적용 되지 않습니다 (참조 무결성 없음).

- `dbRelationInherited` 연결 된 두 테이블을 포함 하는 아닌 스레드의 데이터베이스에 관계가 있습니다.

- `dbRelationUpdateCascade` 업데이트는 계단식으로 표시 됩니다 (계단식 배열에 대 한 자세한 내용은 설명 참조).

- `dbRelationDeleteCascade` 삭제는 cascade입니다.

*lpszField*<br/>
*LpszTable* 로 명명 된 기본 테이블의 필드 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*lpszForeignField*<br/>
*LpszForeignTable* 로 명명 된 외래 테이블의 필드 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*relinfo*<br/>
만들려는 관계에 대 한 정보를 포함 하는 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

관계는 외부 데이터베이스의 쿼리 또는 연결 된 테이블을 포함할 수 없습니다.

관계에 두 테이블 각각의 한 필드가 포함 된 경우 첫 번째 버전의 함수를 사용 합니다. 관계에 여러 필드가 포함 되는 경우 두 번째 버전을 사용 합니다. 관계의 최대 필드 수는 14입니다.

이 작업을 수행 하면 기본 DAO 관계 개체가 만들어지지만 mfc 구현에 대 한 정보는 mfc의 관계 개체 캡슐화가 클래스 내에 포함 되기 때문입니다 `CDaoDatabase` . MFC는 관계에 대 한 클래스를 제공 하지 않습니다.

관계 개체의 특성을 설정 하 여 cascade 작업을 활성화 하는 경우 관련 기본 키 테이블이 변경 되 면 데이터베이스 엔진에서 하나 이상의 다른 테이블의 레코드를 자동으로 업데이트 하거나 삭제 합니다.

예를 들어 Customers 테이블과 Orders 테이블 간에 cascade delete 관계를 설정 한다고 가정 합니다. Customers 테이블에서 레코드를 삭제 하면 해당 고객과 관련 된 Orders 테이블의 레코드도 삭제 됩니다. 또한 Orders 테이블과 다른 테이블 간의 하위 삭제 관계를 설정 하는 경우 Customers 테이블에서 레코드를 삭제 하면 해당 테이블의 레코드가 자동으로 삭제 됩니다.

관련 내용은 DAO 도움말의 "CreateRelation 메서드" 항목을 참조 하십시오.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a> CDaoDatabase::D eleteQueryDef

이 멤버 함수를 호출 하 여 `CDaoDatabase` 개체의 쿼리 정의 컬렉션에서 지정 된 querydef (저장 된 쿼리)를 삭제 합니다.

```cpp
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
삭제할 저장 된 쿼리의 이름입니다.

### <a name="remarks"></a>설명

그런 다음이 쿼리는 데이터베이스에서 더 이상 정의 되지 않습니다.

Querydef 개체를 만드는 방법에 대 한 자세한 내용은 클래스 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)를 참조 하세요. 개체를 생성 하 여 `CDaoDatabase` `CDaoQueryDef` 데이터베이스 개체에 대 한 포인터를 전달 하면 querydef 개체가 특정 개체와 연결 됩니다.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a> CDaoDatabase::D eleteRelation

이 멤버 함수를 호출 하 여 데이터베이스 개체의 관계 컬렉션에서 기존 관계를 삭제 합니다.

```cpp
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
삭제할 관계의 이름입니다.

### <a name="remarks"></a>설명

그런 다음, 관계가 더 이상 존재 하지 않습니다.

관련 내용은 DAO 도움말의 "Delete 메서드" 항목을 참조 하십시오.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a> CDaoDatabase::D eleteTableDef

이 멤버 함수를 호출 하 여 개체의 테이블 컬렉션에서 지정 된 테이블 및 모든 데이터를 삭제 `CDaoDatabase` 합니다.

```cpp
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
삭제할 테이블 정의의 이름입니다.

### <a name="remarks"></a>설명

그런 다음 해당 테이블이 더 이상 데이터베이스에 정의 되어 있지 않습니다.

> [!NOTE]
> 시스템 테이블을 삭제 하지 않도록 주의 해야 합니다.

테이블 정의 개체를 만드는 방법에 대 한 자세한 내용은 클래스 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)를 참조 하세요. 개체를 생성 하 고 `CDaoDatabase` `CDaoTableDef` 데이터베이스 개체에 대 한 포인터를 전달 하면 테이블 정의 개체가 특정 개체와 연결 됩니다.

관련 내용은 DAO 도움말의 "Delete 메서드" 항목을 참조 하십시오.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a> CDaoDatabase:: Execute

이 멤버 함수를 호출 하 여 동작 쿼리를 실행 하거나 데이터베이스에서 SQL 문을 실행 합니다.

```cpp
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>매개 변수

*lpszSQL*<br/>
실행할 유효한 SQL 명령을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*nOptions*<br/>
쿼리의 무결성과 관련 된 옵션을 지정 하는 정수입니다. 비트 or 연산자 ( **&#124;**)를 사용 하 여 다음 상수 중 하나를 결합할 수 있습니다. 조합이 적합 한 경우 (예:와 결합 하지 않음 `dbInconsistent` `dbConsistent` )

- `dbDenyWrite` 다른 사용자에 게 쓰기 권한을 거부 합니다.

- `dbInconsistent` 기본 일관 되지 않은 업데이트

- `dbConsistent` 일관성 있는 업데이트.

- `dbSQLPassThrough` SQL 통과. SQL 문이 처리를 위해 ODBC 데이터 원본에 전달 되도록 합니다.

- `dbFailOnError` 오류가 발생 하는 경우 업데이트를 롤백합니다.

- `dbSeeChanges` 다른 사용자가 편집 중인 데이터를 변경 하는 경우 런타임 오류를 생성 합니다.

> [!NOTE]
> 과를 모두 포함 하거나 둘 다 포함 하지 않을 경우 `dbInconsistent` `dbConsistent` 결과는 기본값입니다. 이러한 상수에 대 한 설명은 DAO 도움말의 "메서드 실행" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

`Execute` 결과를 반환 하지 않는 동작 쿼리 또는 SQL 통과 쿼리에서만 사용할 수 있습니다. 레코드를 반환 하는 select 쿼리에는 적용 되지 않습니다.

작업 쿼리에 대 한 정의 및 정보는 DAO 도움말의 "작업 쿼리" 및 "메서드 실행" 항목을 참조 하십시오.

> [!TIP]
> 구문적으로 올바른 SQL 문과 적절 한 사용 권한이 지정 된 `Execute` 경우 단일 행을 수정 하거나 삭제할 수 없는 경우에도 멤버 함수는 실패 하지 않습니다. 따라서 항상 `dbFailOnError` 멤버 함수를 사용 하 여 `Execute` update 또는 delete 쿼리를 실행할 때 옵션을 사용 합니다. 이 옵션을 선택 하면 MFC가 [CDaoException](../../mfc/reference/cdaoexception-class.md) 형식의 예외를 throw 하 고 영향을 받는 레코드가 모두 잠기고 업데이트 하거나 삭제할 수 없는 경우 성공한 모든 변경 내용을 롤백합니다. 언제 든 지 `GetRecordsAffected` 를 호출 하 여 영향을 받은 레코드 수를 확인할 수 있습니다.

데이터베이스 개체의 [GetRecordsAffected](#getrecordsaffected) 멤버 함수를 호출 하 여 가장 최근 호출의 영향을 받는 레코드 수를 확인 합니다 `Execute` . 예를 들어은 `GetRecordsAffected` 동작 쿼리를 실행할 때 삭제, 업데이트 또는 삽입 된 레코드 수에 대 한 정보를 반환 합니다. 연속 업데이트 또는 삭제가 적용 되는 경우 반환 되는 개수는 관련 테이블의 변경 내용을 반영 하지 않습니다.

`Execute` 는 레코드 집합을 반환 하지 않습니다. `Execute`레코드를 선택 하는 쿼리에서를 사용 하면 MFC에서 형식의 예외가 throw `CDaoException` 됩니다. 와 `ExecuteSQL` 유사한 멤버 함수가 없습니다 `CDatabase::ExecuteSQL` .

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a> CDaoDatabase:: GetConnect

이 멤버 함수를 호출 하 여 `CDaoDatabase` 개체를 ODBC 또는 ISAM 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 검색 합니다.

```
CString GetConnect();
```

### <a name="return-value"></a>반환 값

ODBC 데이터 원본에서 [Open](#open) 이 성공적으로 호출 된 경우 연결 문자열은입니다. 그렇지 않으면 빈 문자열입니다. Microsoft Jet (. MDB) 데이터베이스를 사용 하도록 설정 `dbSQLPassThrough` 하거나 레코드 집합을 열 때 사용 [하는](#execute) 옵션과 함께 사용 하도록 설정 하지 않는 한 문자열은 항상 비어 있습니다.

### <a name="remarks"></a>설명

문자열은 통과 쿼리에 사용 되는 데이터베이스 또는 열린 데이터베이스의 원본에 대 한 정보를 제공 합니다. 연결 문자열은 데이터베이스 유형 지정자와 0 개 이상의 매개 변수를 세미콜론으로 구분 하 여 구성 됩니다.

> [!NOTE]
> MFC DAO 클래스를 사용 하 여 ODBC를 통해 데이터 원본에 연결 하는 것은 연결 된 테이블을 통해 연결 하는 것 보다 효율성이 낮습니다.

> [!NOTE]
> 연결 문자열은 필요에 따라 ODBC 및 특정 ISAM 드라이버에 추가 정보를 전달 하는 데 사용 됩니다. 에는 사용 되지 않습니다. MDB 데이터베이스. Microsoft Jet 데이터베이스 기본 테이블의 경우 연결 문자열은 위의 반환 값에 설명 된 대로 SQL 통과 쿼리에 사용 하는 경우를 제외 하 고는 빈 문자열 ("")입니다.

연결 문자열을 만드는 방법에 대 한 설명은 [Open](#open) member 함수를 참조 하세요. 호출에서 연결 문자열을 설정한 후에는 `Open` 나중에이를 사용 하 여 데이터베이스의 유형, 경로, 사용자 ID, 암호 또는 ODBC 데이터 원본을 결정 하는 설정을 확인할 수 있습니다.

## <a name="cdaodatabasegetname"></a><a name="getname"></a> CDaoDatabase:: GetName

이 멤버 함수를 호출 하 여 현재 열려 있는 데이터베이스의 이름 (기존 데이터베이스 파일의 이름 또는 등록 된 ODBC 데이터 원본의 이름)을 검색 합니다.

```
CString GetName();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 데이터베이스의 전체 경로 및 파일 이름입니다. 그렇지 않으면 빈 [CString](../../atl-mfc-shared/reference/cstringt-class.md)이 됩니다.

### <a name="remarks"></a>설명

네트워크에서 UNC (uniform 명명 규칙)를 지 원하는 경우 네트워크 경로 (예: " \\ \\ \\ \myserver \\ \MYSHARE \\ \MYDIR \\ \MYDB.")를 지정할 수도 있습니다. MDB ". " \\ "은 c + + 이스케이프 문자 이므로 문자열 리터럴에 이중 백슬래시가 필요 합니다.

예를 들어 제목에이 이름을 표시 하려는 경우가 있습니다. 이름을 검색 하는 동안 오류가 발생 하는 경우 MFC에서 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다.

> [!NOTE]
> 외부 데이터베이스에 액세스 하는 경우 성능을 향상 시키려면 외부 데이터베이스 테이블을 Microsoft Jet 데이터베이스 ()에 연결 하는 것이 좋습니다. MDB)를 연결 하는 것이 아니라 데이터 원본에 직접 연결 합니다.

데이터베이스 유형은 경로가 가리키는 파일이 나 디렉터리에 의해 다음과 같이 표시 됩니다.

|Pathname은를 가리킵니다.|데이터베이스 유형|
|--------------------------|-------------------|
|. MDB 파일|Microsoft Jet 데이터베이스 (Microsoft Access)|
|을 포함 하는 디렉터리입니다. DBF 파일|dBASE 데이터베이스|
|을 포함 하는 디렉터리입니다. XLS 파일|Microsoft Excel 데이터베이스|
|을 포함 하는 디렉터리입니다. PDX 파일|Paradox 데이터베이스|
|적절 한 형식의 텍스트 데이터베이스 파일이 들어 있는 디렉터리입니다.|텍스트 형식 데이터베이스|

SQL Server 및 Oracle과 같은 ODBC 데이터베이스의 경우 데이터베이스의 연결 문자열은 ODBC에서 등록 된 DSN (데이터 원본 이름)을 식별 합니다.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a> CDaoDatabase:: GetQueryDefCount

이 멤버 함수를 호출 하 여 데이터베이스의 쿼리 정의 컬렉션에 정의 된 쿼리 수를 검색 합니다.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>반환 값

데이터베이스에 정의 된 쿼리 수입니다.

### <a name="remarks"></a>설명

`GetQueryDefCount` 는 쿼리 정의 컬렉션의 모든 쿼리 정의를 반복 해야 하는 경우에 유용 합니다. 컬렉션에서 지정 된 쿼리에 대 한 정보를 얻으려면 [GetQueryDefInfo](#getquerydefinfo)를 참조 하세요.

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a> CDaoDatabase:: GetQueryDefInfo

이 멤버 함수를 호출 하 여 데이터베이스에 정의 된 쿼리에 대 한 다양 한 종류의 정보를 얻을 수 있습니다.

```cpp
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 데이터베이스의 쿼리 정의 컬렉션에 있는 미리 정의 된 쿼리의 인덱스입니다.

*querydefinfo*<br/>
요청 된 정보를 반환 하는 [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 레코드 집합에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 레코드 집합에 대해 반환 하는 작업과 함께 여기에 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 형식

- 기본 정보 및 AFX_DAO_SECONDARY_INFO 만든 날짜, 마지막 업데이트 날짜, 레코드를 반환 하 고 업데이트할 수 있습니다.

- 기본 및 보조 정보를 비롯 하 여 SQL, Connect, ODBCTimeout AFX_DAO_ALL_INFO

*lpszName*<br/>
이름으로 조회 하기 위해 데이터베이스에 정의 된 쿼리 이름을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

데이터베이스의 쿼리 정의 컬렉션에서 인덱스 또는 쿼리 이름을 기준으로 쿼리를 선택할 수 있도록 두 가지 버전의 함수가 제공 됩니다.

*Querydefinfo* 에 반환 되는 정보에 대 한 설명은 [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준의 정보를 요청 하는 경우 모든 이전 수준의 정보를 얻을 수 있습니다.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a> CDaoDatabase:: GetQueryTimeout

연결 된 데이터베이스에 대 한 후속 작업이 시간 초과 될 때까지 허용 되는 현재 시간 (초)을 검색 하려면이 멤버 함수를 호출 합니다.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>반환 값

제한 시간 값 (초)을 포함 하는 정수 (short)입니다.

### <a name="remarks"></a>설명

네트워크 액세스 문제, 과도 한 쿼리 처리 시간 등으로 인해 작업 시간이 초과 될 수 있습니다. 설정이 적용 되는 동안이 개체와 연결 된 모든 레코드 집합에 대 한 모든 열기, 새로 추가, 업데이트 및 삭제 작업에 영향을 줍니다 `CDaoDatabase` . [SetQueryTimeout](#setquerytimeout)을 호출 하 여 현재 제한 시간 설정을 변경할 수 있습니다. 열을 연 후 레코드 집합에 대 한 쿼리 제한 시간 값을 변경 해도 레코드 집합에 대 한 값은 변경 되지 않습니다. 예를 들어 후속 [이동](../../mfc/reference/cdaorecordset-class.md#move) 작업에서는 새 값을 사용 하지 않습니다. 기본값은 데이터베이스 엔진이 초기화 될 때 초기에 설정 됩니다.

쿼리 시간 제한의 기본값은 Windows 레지스트리에서 가져옵니다. 레지스트리 설정이 없는 경우 기본값은 60 초입니다. 모든 데이터베이스에서 쿼리 제한 시간 값을 설정 하는 기능을 지원 하지는 않습니다. 쿼리 제한 시간 값을 0으로 설정 하면 시간 제한이 발생 하지 않습니다. 그리고 데이터베이스와의 통신이 응답 하지 않을 수 있습니다. 이 동작은 개발 중에 유용할 수 있습니다. 호출에 실패 하면 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외가 throw 됩니다.

관련 내용은 DAO 도움말의 "QueryTimeout 속성" 항목을 참조 하십시오.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a> CDaoDatabase:: GetRecordsAffected

이 멤버 함수를 호출 하 여 [Execute](#execute) 멤버 함수의 가장 최근 호출에 의해 영향을 받는 레코드 수를 확인 합니다.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>반환 값

영향을 받는 레코드 수를 포함 하는 정수 (long)입니다.

### <a name="remarks"></a>설명

반환 되는 값에는를 사용 하 여 실행 되는 작업 쿼리를 통해 삭제, 업데이트 또는 삽입 된 레코드 수가 포함 됩니다 `Execute` . 연속 업데이트 또는 삭제가 적용 되는 경우 반환 되는 개수는 관련 테이블의 변경 내용을 반영 하지 않습니다.

관련 내용은 DAO 도움말의 "RecordsAffected 속성" 항목을 참조 하십시오.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a> CDaoDatabase:: GetRelationCount

이 멤버 함수를 호출 하 여 데이터베이스의 테이블 간에 정의 된 관계 수를 가져옵니다.

```
short GetRelationCount();
```

### <a name="return-value"></a>반환 값

데이터베이스의 테이블 간에 정의 된 관계의 수입니다.

### <a name="remarks"></a>설명

`GetRelationCount` 는 데이터베이스의 관계 컬렉션에 정의 된 모든 관계를 반복 해야 하는 경우에 유용 합니다. 컬렉션에서 지정 된 관계에 대 한 정보를 얻으려면 [GetRelationInfo](#getrelationinfo)를 참조 하세요.

관계의 개념을 설명 하기 위해 일 대 다 관계를 가질 수 있는 Suppliers 테이블과 Products 테이블을 고려 합니다. 이 관계에서 한 공급 업체는 둘 이상의 제품을 제공할 수 있습니다. 다른 관계는 일 대 일 및 다대다입니다.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a> CDaoDatabase:: GetRelationInfo

이 멤버 함수를 호출 하 여 데이터베이스의 관계 컬렉션에서 지정 된 관계에 대 한 정보를 가져옵니다.

```cpp
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 데이터베이스의 관계 컬렉션에 있는 관계 개체의 인덱스입니다.

*relinfo*<br/>
요청 된 정보를 반환 하는 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 관계에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 관계에 대해 반환 하는 것과 함께 다음과 같이 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 테이블, 외래 테이블

- AFX_DAO_SECONDARY_INFO 특성, 필드 정보

필드 정보는 관계와 관련 된 기본 테이블의 필드를 포함 하는 [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) 개체입니다.

*lpszName*<br/>
이름으로 조회 하는 데 사용할 관계 개체의 이름을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

이 함수의 두 버전은 인덱스 또는 이름으로 액세스를 제공 합니다. *Relinfo* 에서 반환 되는 정보에 대 한 설명은 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 구조체를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준 에서도 정보를 얻을 수 있습니다.

> [!NOTE]
> 관계 개체의 특성을 설정 하 여 cascade 작업 (또는)을 활성화 하는 경우 `dbRelationUpdateCascades` `dbRelationDeleteCascades` 관련 기본 키 테이블이 변경 되 면 Microsoft Jet 데이터베이스 엔진에서 하나 이상의 다른 테이블의 레코드를 자동으로 업데이트 하거나 삭제 합니다. 예를 들어 Customers 테이블과 Orders 테이블 간에 cascade delete 관계를 설정 한다고 가정 합니다. Customers 테이블에서 레코드를 삭제 하면 해당 고객과 관련 된 Orders 테이블의 레코드도 삭제 됩니다. 또한 Orders 테이블과 다른 테이블 간의 하위 삭제 관계를 설정 하는 경우 Customers 테이블에서 레코드를 삭제 하면 해당 테이블의 레코드가 자동으로 삭제 됩니다.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a> CDaoDatabase:: GetTableDefCount

이 멤버 함수를 호출 하 여 데이터베이스에 정의 된 테이블 수를 검색 합니다.

```
short GetTableDefCount();
```

### <a name="return-value"></a>반환 값

데이터베이스에 정의 된 테이블 정의의 수입니다.

### <a name="remarks"></a>설명

`GetTableDefCount` 는 데이터베이스의 테이블 컬렉션에 있는 모든 테이블을 반복 해야 하는 경우에 유용 합니다. 컬렉션의 지정 된 테이블에 대 한 정보를 얻으려면 [GetTableDefInfo](#gettabledefinfo)를 참조 하세요.

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a> CDaoDatabase:: GetTableDefInfo

이 멤버 함수를 호출 하 여 데이터베이스에 정의 된 테이블에 대 한 다양 한 종류의 정보를 얻을 수 있습니다.

```cpp
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 데이터베이스의 테이블 정의 컬렉션에 있는 테이블 정의 개체의 인덱스입니다.

*tabledefinfo*<br/>
요청 된 정보를 반환 하는 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 테이블에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 관계에 대해 반환 하는 것과 함께 다음과 같이 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 업데이트할 수 있는 특성

- 기본 정보 및 AFX_DAO_SECONDARY_INFO 만든 날짜, 마지막으로 업데이트 한 날짜, 원본 테이블 이름, 연결을 포함 합니다.

- 기본 및 보조 정보를 추가 하 고 유효성 검사 규칙, 유효성 검사 텍스트, 레코드 수를 AFX_DAO_ALL_INFO 합니다.

*lpszName*<br/>
이름으로 조회 하기 위한 테이블 정의 개체의 이름입니다.

### <a name="remarks"></a>설명

데이터베이스의 테이블 테이블 컬렉션에서 인덱스 또는 테이블 이름을 기준으로 테이블을 선택할 수 있도록 두 가지 버전의 함수가 제공 됩니다.

*Tabledefinfo* 에 반환 되는 정보에 대 한 설명은 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

> [!NOTE]
> AFX_DAO_ALL_INFO 옵션은 얻을 수 있는 정보를 제공 합니다. 이 경우 레코드 수가 많은 경우 테이블의 레코드 수를 계산 하는 데 시간이 많이 걸릴 수 있습니다.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a> CDaoDatabase:: GetVersion

Microsoft Jet 데이터베이스 파일의 버전을 확인 하려면이 멤버 함수를 호출 합니다.

```
CString GetVersion();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 데이터베이스 파일의 버전을 나타내는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

반환 되는 값은 "major. minor" 형식의 버전 번호를 나타냅니다. 예를 들면 "3.0"입니다. 제품 버전 번호 (예: 3.0)는 버전 번호 (3), 마침표 및 릴리스 번호 (0)로 구성 됩니다. 최신 버전은 1.0, 1.1, 2.0 및 3.0입니다.

관련 내용은 DAO 도움말의 "버전 속성" 항목을 참조 하십시오.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a> CDaoDatabase:: IsOpen

이 멤버 함수를 호출 하 여 `CDaoDatabase` 개체가 데이터베이스에 현재 열려 있는지 여부를 확인 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

개체가 현재 열려 있으면 0이 아니고 `CDaoDatabase` , 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a> CDaoDatabase:: m_pDAODatabase

개체를 기반으로 하는 DAO 데이터베이스 개체의 OLE 인터페이스에 대 한 포인터를 포함 `CDaoDatabase` 합니다.

### <a name="remarks"></a>설명

DAO 인터페이스에 직접 액세스 해야 하는 경우이 포인터를 사용 합니다.

DAO를 직접 호출 하는 방법에 대 한 자세한 내용은 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)를 참조 하십시오.

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a> CDaoDatabase:: m_pWorkspace

데이터베이스 개체를 포함 하는 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

작업 영역에 직접 액세스 해야 하는 경우 (예: 작업 영역의 데이터베이스 컬렉션에 있는 다른 데이터베이스 개체에 대 한 포인터를 가져오기 위해)이 포인터를 사용 합니다.

## <a name="cdaodatabaseopen"></a><a name="open"></a> CDaoDatabase:: Open

기존 데이터베이스를 나타내는 새로 생성 된 개체를 초기화 하려면이 멤버 함수를 호출 해야 합니다 `CDaoDatabase` .

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
기존 Microsoft Jet의 이름인 문자열 식입니다 (. MDB) 데이터베이스 파일입니다. 파일 이름에 확장명이 있으면 필수입니다. 네트워크에서 UNC (uniform 명명 규칙)를 지 원하는 경우 " \\ \\ \\ \myserver \\ \MYSHARE \\ \MYDIR \\ \MYDB.와 같은 네트워크 경로를 지정할 수도 있습니다. MDB ". " \\ "은 c + + 이스케이프 문자 이므로 문자열 리터럴에 이중 백슬래시가 필요 합니다.

*LpszName* 를 사용 하는 경우 몇 가지 고려 사항이 적용 됩니다. 있는 경우:

- 는 다른 사용자가 단독으로 액세스 하기 위해 이미 열려 있는 데이터베이스를 참조 하며, MFC는 [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다. 해당 예외를 트래핑 하 여 데이터베이스를 사용할 수 없음을 사용자에 게 알립니다.

- 가 빈 문자열 ("")이 고 *lpszConnect* 가 "odbc;" 이면 등록 된 모든 ODBC 데이터 원본 이름이 나열 된 대화 상자가 표시 되어 사용자가 데이터베이스를 선택할 수 있습니다. ODBC 데이터 원본에 대 한 직접 연결을 사용 하지 않아야 합니다. 대신 연결 된 테이블을 사용 합니다.

- 그렇지 않으면 기존 데이터베이스 또는 유효한 ODBC 데이터 원본 이름을 참조 하지 않고, MFC에서 형식의 예외를 throw `CDaoException` 합니다.

> [!NOTE]
> DAO 오류 코드에 대 한 자세한 내용은 DAOERR를 참조 하세요. H 파일. 관련 정보는 DAO 도움말의 "잡을 수 있는 데이터 액세스 오류" 항목을 참조 하십시오.

*bExclusive*<br/>
데이터베이스를 단독 (비공유) 액세스를 위해 열 수 있으면 TRUE이 고, 공유 액세스를 위해 데이터베이스를 열어야 하는 경우 FALSE 인 부울 값입니다. 이 인수를 생략 하면 데이터베이스가 공유 액세스용으로 열립니다.

*bReadOnly*<br/>
읽기 전용 액세스를 위해 데이터베이스를 열어야 하는 경우 TRUE이 고 읽기/쓰기 액세스를 위해 데이터베이스를 열려면 FALSE 인 부울 값입니다. 이 인수를 생략 하면 읽기/쓰기 액세스를 위해 데이터베이스가 열립니다. 모든 종속 레코드 집합은이 특성을 상속 합니다.

*lpszConnect*<br/>
데이터베이스를 여는 데 사용 되는 문자열 식입니다. 이 문자열은 ODBC connect 인수를 구성 합니다. 원본 문자열을 제공 하려면 전용 및 읽기 전용 인수를 제공 해야 합니다. 데이터베이스가 Microsoft Jet 데이터베이스 이면이 고, 그렇지 않으면입니다. MDB),이 문자열은 비어 있습니다 (""). 기본값 ( **_T**("")의 구문은 응용 프로그램의 ANSI 빌드 뿐만 아니라 유니코드에 대 한 이식성을 제공 합니다.

### <a name="remarks"></a>설명

`Open` 데이터베이스를 기본 DAO 개체와 연결 합니다. 데이터베이스 개체를 사용 하 여 초기화 될 때까지 recordset, tabledef 또는 querydef 개체를 생성할 수 없습니다. `Open` 연결 된 작업 영역의 데이터베이스 컬렉션에 데이터베이스 개체를 추가 합니다.

다음과 같이 매개 변수를 사용 합니다.

- Microsoft Jet (. MDB) 데이터베이스를 사용 하 여 *lpszName* 매개 변수를 사용 하 고 *lpszConnect* 매개 변수에 빈 문자열을 전달 하거나 형식의 암호 문자열을 전달 합니다. "; PWD = password "데이터베이스가 암호로 보호 된 경우 (. MDB 데이터베이스만 해당).

- ODBC 데이터 원본을 여는 경우 *lpszConnect* 에 유효한 ODBC 연결 문자열을 전달 하 고 *lpszName* 에 빈 문자열을 전달 합니다.

관련 내용은 DAO 도움말의 "OpenDatabase 메서드" 항목을 참조 하십시오.

> [!NOTE]
> ISAM 데이터베이스 및 ODBC 데이터 원본을 비롯 하 여 외부 데이터베이스에 액세스할 때 성능을 향상 시키려면 외부 데이터베이스 테이블을 Microsoft Jet 엔진 데이터베이스 ()에 연결 하는 것이 좋습니다. MDB)를 연결 하는 것이 아니라 데이터 원본에 직접 연결 합니다.

예를 들어 DBMS 호스트를 사용할 수 없는 경우 연결 시도가 시간 초과 될 수 있습니다. 연결 시도가 실패 하면에서 `Open` [CDaoException](../../mfc/reference/cdaoexception-class.md)형식의 예외를 throw 합니다.

나머지 설명은 ODBC 데이터베이스에만 적용 됩니다.

데이터베이스가 ODBC 데이터베이스이 고 호출의 매개 변수가 `Open` 연결을 설정 하는 데 충분 한 정보를 포함 하지 않는 경우 ODBC 드라이버는 사용자에 게 필요한 정보를 가져올 수 있는 대화 상자를 엽니다. 를 호출 하면 `Open` 연결 문자열 *lpszConnect* 가 비공개로 저장 되며 [getconnect](#getconnect) 멤버 함수를 호출 하 여 사용할 수 있습니다.

원할 경우를 호출 하기 전에 사용자에 게 암호와 같은 정보를 가져오기 위해 자신의 대화 상자를 연 `Open` 다음 해당 정보를 전달 하는 연결 문자열에 추가할 수 있습니다 `Open` . 또는 Windows 레지스트리에 전달 하는 연결 문자열을 저장 하 여 다음에 응용 프로그램에서 개체를 호출할 때 다시 사용할 수 있도록 할 수 있습니다 `Open` `CDaoDatabase` .

여러 수준의 로그인 권한 부여 (각각 다른 개체의 경우)에 대 한 연결 문자열을 사용 `CDaoDatabase` 하거나 다른 데이터베이스 관련 정보를 전달할 수도 있습니다.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a> CDaoDatabase:: SetQueryTimeout

이 멤버 함수를 호출 하 여 연결 된 데이터베이스에 대 한 후속 작업이 시간 초과 될 때까지 허용 되는 기본 시간 (초)을 재정의할 수 있습니다.

```cpp
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>매개 변수

*nSeconds*<br/>
쿼리 시도 시간이 초과 될 때까지 허용 되는 시간 (초)입니다.

### <a name="remarks"></a>설명

네트워크 액세스 문제, 과도 한 쿼리 처리 시간 등으로 인해 작업 시간이 초과 될 수 있습니다. `SetQueryTimeout`쿼리 제한 시간 값을 변경 하려면 레코드 집합을 열기 전에 또는 레코드 집합의 [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)또는 [Delete](../../mfc/reference/cdaorecordset-class.md#delete) 멤버 함수를 호출 하기 전에를 호출 합니다. 설정은 [](../../mfc/reference/cdaorecordset-class.md#open) `AddNew` `Update` `Delete` 이 개체와 연결 된 모든 레코드 집합에 대 한 모든 후속,, 및 호출에 영향을 줍니다 `CDaoDatabase` . 열을 연 후 레코드 집합에 대 한 쿼리 제한 시간 값을 변경 해도 레코드 집합에 대 한 값은 변경 되지 않습니다. 예를 들어 후속 [이동](../../mfc/reference/cdaorecordset-class.md#move) 작업에서는 새 값을 사용 하지 않습니다.

쿼리 시간 제한의 기본값은 60 초입니다. 모든 데이터베이스에서 쿼리 제한 시간 값을 설정 하는 기능을 지원 하지는 않습니다. 쿼리 제한 시간 값을 0으로 설정 하면 시간 제한이 발생 하지 않습니다. 데이터베이스와의 통신이 응답 하지 않을 수 있습니다. 이 동작은 개발 중에 유용할 수 있습니다.

관련 내용은 DAO 도움말의 "QueryTimeout 속성" 항목을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace 클래스](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 클래스](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException 클래스](../../mfc/reference/cdaoexception-class.md)
