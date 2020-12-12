---
description: '자세히 알아보기: CDaoQueryDefInfo Structure'
title: CDaoQueryDefInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: 46b9b49d91d3d005d941eb585663c205fe30b2da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271813"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 구조체

구조에는 `CDaoQueryDefInfo` DAO (data access objects)에 대해 정의 된 쿼리 정의 개체에 대 한 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
Querydef 개체의 이름을 고유 하 게 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오. [CDaoQueryDef:: GetName](../../mfc/reference/cdaoquerydef-class.md#getname) 를 호출 하 여이 속성을 직접 검색 합니다.

*m_nType*<br/>
Querydef 개체의 작업 유형을 나타내는 값입니다. 값은 다음 중 하나일 수 있습니다.

- `dbQSelect` Select-쿼리에서 레코드를 선택 합니다.

- `dbQAction` Action-쿼리가 데이터를 이동 또는 변경 하지만 레코드를 반환 하지 않습니다.

- `dbQCrosstab` 크로스탭-쿼리가 스프레드시트와 비슷한 형식으로 데이터를 반환 합니다.

- `dbQDelete` Delete-쿼리에서 지정 된 행 집합을 삭제 합니다.

- `dbQUpdate` Update-쿼리가 레코드 집합을 변경 합니다.

- `dbQAppend` Append-쿼리는 테이블이 나 쿼리의 끝에 새 레코드를 추가 합니다.

- `dbQMakeTable` 테이블 만들기-쿼리는 레코드 집합에서 새 테이블을 만듭니다.

- `dbQDDL` 데이터 정의-쿼리는 테이블이 나 해당 파트의 구조에 영향을 줍니다.

- `dbQSQLPassThrough` 통과-SQL 문이 중간 처리 없이 데이터베이스 백 엔드로 직접 전달 됩니다.

- `dbQSetOperation` Union-쿼리는 중복 레코드가 제거 된 두 개 이상의 테이블에 있는 모든 지정 된 레코드의 데이터를 포함 하는 스냅숏 형식의 레코드 집합 개체를 만듭니다. 중복 항목을 포함 하려면 querydef의 SQL 문에 **ALL** 키워드를 추가 합니다.

- `dbQSPTBulk` 에서 `dbQSQLPassThrough` 레코드를 반환 하지 않는 쿼리를 지정 하는 데 사용 됩니다.

> [!NOTE]
> SQL 통과 쿼리를 만들려면 상수를 설정 하지 않습니다 `dbQSQLPassThrough` . 이는 querydef 개체를 만들고 Connect 속성을 설정할 때 Microsoft Jet 데이터베이스 엔진에 의해 자동으로 설정 됩니다.

자세한 내용은 DAO 도움말의 "형식 속성" 항목을 참조 하십시오.

*m_dateCreated*<br/>
Querydef를 만든 날짜와 시간입니다. Querydef를 만든 날짜를 직접 검색 하려면 해당 테이블과 연결 된 개체의 [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) 멤버 함수를 호출 합니다 `CDaoTableDef` . 자세한 내용은 아래 주석을 참조 하세요. 또한 DAO 도움말의 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

*m_dateLastUpdated*<br/>
Querydef의 최근 변경 내용에 대 한 날짜와 시간입니다. 테이블이 마지막으로 업데이트 된 날짜를 직접 검색 하려면 querydef의 [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) 멤버 함수를 호출 합니다. 자세한 내용은 아래 주석을 참조 하세요. DAO 도움말의 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

*m_bUpdatable*<br/>
Querydef 개체를 변경할 수 있는지 여부를 나타냅니다. 이 속성이 TRUE 이면 querydef를 업데이트할 수 있습니다. 그렇지 않은 경우에는 그렇지 않습니다. 업데이트 가능은 쿼리 정의 개체의 쿼리 정의를 변경할 수 있음을 의미 합니다. 쿼리 정의를 업데이트할 수 있으면 결과 레코드 집합을 업데이트할 수 없는 경우에도 querydef 개체의 업데이트 가능 속성이 TRUE로 설정 됩니다. 이 속성을 직접 검색 하려면 querydef의 [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) 멤버 함수를 호출 합니다. 자세한 내용은 DAO 도움말의 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

*m_bReturnsRecords*<br/>
외부 데이터베이스에 대 한 SQL 통과 쿼리가 레코드를 반환 하는지 여부를 나타냅니다. 이 속성이 TRUE 이면 쿼리가 레코드를 반환 합니다. 이 속성을 직접 검색 하려면 [CDaoQueryDef:: GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)를 호출 합니다. 외부 데이터베이스에 대 한 모든 SQL 통과 쿼리는 레코드를 반환 하지 않습니다. 예를 들어 SQL **UPDATE** 문은 레코드를 반환 하지 않고 레코드를 업데이트 하지만 sql **SELECT** 문은 레코드를 반환 합니다. 자세한 내용은 DAO 도움말의 "ReturnsRecords 속성" 항목을 참조 하십시오.

*m_strSQL*<br/>
Querydef 개체에 의해 실행 되는 쿼리를 정의 하는 SQL 문입니다. SQL 속성에는 쿼리를 실행할 때 레코드를 선택, 그룹화 및 정렬 하는 방법을 결정 하는 SQL 문이 포함 되어 있습니다. 쿼리를 사용 하 여 다이너셋 또는 스냅숏 형식의 레코드 집합 개체에 포함할 레코드를 선택할 수 있습니다. 대량 쿼리를 정의 하 여 레코드를 반환 하지 않고 데이터를 수정할 수도 있습니다. Querydef의 [Getsql](../../mfc/reference/cdaoquerydef-class.md#getsql) 멤버 함수를 호출 하 여이 속성의 값을 직접 검색할 수 있습니다.

*m_strConnect*<br/>
통과 쿼리에서 사용 되는 데이터베이스의 원본에 대 한 정보를 제공 합니다. 이 정보는 연결 문자열의 형식을 사용 합니다. 연결 문자열에 대 한 자세한 내용과이 속성의 값을 직접 검색 하는 방법에 대 한 자세한 내용은 [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) 멤버 함수를 참조 하세요.

*m_nODBCTimeout*<br/>
Microsoft Jet 데이터베이스 엔진이 ODBC 데이터베이스에서 쿼리를 실행할 때 시간 초과 오류가 발생 하기 전까지 대기 하는 시간 (초)입니다. Microsoft SQL Server와 같은 ODBC 데이터베이스를 사용 하는 경우 네트워크 트래픽 또는 ODBC 서버의 과도 한 사용으로 인해 지연이 발생할 수 있습니다. 무기한 대기 하는 대신 Microsoft Jet 엔진이 오류를 생성 하기 전까지 대기 하는 기간을 지정할 수 있습니다. 기본 시간 제한 값은 60 초입니다. Querydef의 [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) 멤버 함수를 호출 하 여이 속성의 값을 직접 검색할 수 있습니다. 자세한 내용은 DAO 도움말의 "ODBCTimeout 속성" 항목을 참조 하십시오.

## <a name="remarks"></a>설명

Querydef는 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)클래스의 개체입니다. 위의 기본, 보조 및 모든에 대 한 참조는 클래스의 [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다 `CDaoDatabase` .

[CDaoDatabase:: GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoQueryDefInfo` . `GetQueryDefInfo`Querydef 개체가 저장 된 쿼리 정의 컬렉션의 데이터베이스 개체에 대해를 호출 합니다. `CDaoQueryDefInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoQueryDefInfo` . 또한 클래스는 `CDaoDatabase` 개체에 반환 된 모든 속성에 직접 액세스 하는 멤버 함수 `CDaoQueryDefInfo` 를 제공 하므로를 호출 하지 않아도 되는 경우가 있습니다 `GetQueryDefInfo` .

새 필드 또는 매개 변수 개체를 querydef 개체의 필드 또는 매개 변수 컬렉션에 추가 하면 기본 데이터베이스가 새 개체에 대해 지정 된 데이터 형식을 지원 하지 않는 경우 예외가 throw 됩니다.

날짜 및 시간 설정은 querydef가 만들어지거나 마지막으로 업데이트 된 컴퓨터에서 파생 됩니다. 다중 사용자 환경에서는 DateCreated 및 LastUpdated 속성 설정의 불일치를 방지 하기 위해 **net time** 명령을 사용 하 여 파일 서버에서 이러한 설정을 직접 가져와야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 클래스](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)
