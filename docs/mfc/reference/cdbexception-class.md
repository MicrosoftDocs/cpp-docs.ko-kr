---
description: '자세한 정보: CDBException 클래스'
title: CDBException 클래스
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 8e337cc0f66a4a281de07ba3839895096e8021d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222127"
---
# <a name="cdbexception-class"></a>CDBException 클래스

데이터베이스 클래스에서 발생하는 예외 상태를 나타냅니다.

## <a name="syntax"></a>구문

```
class CDBException : public CException
```

## <a name="members"></a>멤버

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDBException:: m_nRetCode](#m_nretcode)|RETCODE 형식의 ODBC (Open Database Connectivity) 반환 코드를 포함 합니다.|
|[CDBException:: m_strError](#m_strerror)|영숫자 용어로 오류를 설명 하는 문자열을 포함 합니다.|
|[CDBException:: m_strStateNativeOrigin](#m_strstatenativeorigin)|ODBC에서 반환 하는 오류 코드를 기준으로 오류를 설명 하는 문자열을 포함 합니다.|

## <a name="remarks"></a>설명

클래스에는 예외의 원인을 확인 하거나 예외를 설명 하는 텍스트 메시지를 표시 하는 데 사용할 수 있는 두 개의 공용 데이터 멤버가 포함 되어 있습니다. `CDBException` 개체는 데이터베이스 클래스의 멤버 함수에 의해 생성 및 throw 됩니다.

> [!NOTE]
> 이 클래스는 MFC의 ODBC (Open Database Connectivity) 클래스 중 하나입니다. 대신 최신 DAO (Data Access Objects) 클래스를 사용 하는 경우 [CDaoException](../../mfc/reference/cdaoexception-class.md) 를 대신 사용 합니다. 모든 DAO 클래스 이름에는 접두사로 "CDao"가 있습니다. 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

예외는 데이터 원본 또는 네트워크 i/o 오류와 같이 프로그램의 컨트롤 외부 조건과 관련 된 비정상적인 실행의 사례입니다. 일반적으로 프로그램을 실행 하는 과정에서 나타날 수 있는 오류는 일반적으로 예외로 간주 되지 않습니다.

이러한 개체는 **CATCH** 식의 범위 내에서 액세스할 수 있습니다. 전역 함수를 사용 하 여 사용자 `CDBException` 고유의 코드에서 개체를 throw 할 수도 있습니다 `AfxThrowDBException` .

일반적인 예외 처리 또는 개체 정보에 대 한 자세한 내용은 `CDBException` [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md) 및 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a> CDBException:: m_nRetCode

ODBC API (응용 프로그래밍 인터페이스) 함수에서 반환 하는 RETCODE 형식의 ODBC 오류 코드를 포함 합니다.

### <a name="remarks"></a>설명

이 형식에는 ODBC에 정의 된 SQL 접두사가 포함 된 코드와 데이터베이스 클래스에 의해 정의 된 AFX_SQL 접두사가 포함 됩니다. 의 경우 `CDBException` 이 멤버는 다음 값 중 하나를 포함 합니다.

- 또는 호출에 대 한 `CDatabase::OpenEx` 드라이버가 `CDatabase::Open` 필요한 ODBC API 규칙 수준 1 (SQL_OAC_LEVEL1)에 맞지 AFX_SQL_ERROR_API_CONFORMANCE.

- 데이터 원본에 대 한 연결을 AFX_SQL_ERROR_CONNECT_FAIL 하지 못했습니다. `CDatabase`레코드 집합 생성자에 NULL 포인터를 전달 하 고 실패를 기준으로 연결을 만드는 후속 시도가 `GetDefaultConnect` 실패 했습니다.

- 저장소를 제공 하는 것 보다 더 많은 데이터를 요청 AFX_SQL_ERROR_DATA_TRUNCATED 합니다. 또는 데이터 형식에 대해 제공 된 데이터 저장소를 확장 하는 방법에 대 한 자세한 내용은 `CString` `CByteArray` `nMaxLength` "매크로 및 전역"에서 [RFX_Text](record-field-exchange-functions.md#rfx_text) 및 [RFX_Binary](record-field-exchange-functions.md#rfx_binary) 에 대 한 인수를 참조 하세요.

- 다이너셋 요청에 대 한 호출이 `CRecordset::Open` 실패 했습니다. AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED 다이너셋은 드라이버가 지원 되지 않습니다.

- 테이블을 열려고 했지만 사용자가 지정한 테이블을 프로시저 호출 또는 **SELECT** 문으로 식별할 수 없는 경우에는 재정의의 RFX (레코드 필드 교환) 함수 호출에서 식별 된 열이 없습니다 `DoFieldExchange` . AFX_SQL_ERROR_EMPTY_COLUMN_LIST

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH 재정의에서 RFX 함수의 형식이 `DoFieldExchange` 레코드 집합의 열 데이터 형식과 호환 되지 않습니다.

- `CRecordset::Update`이전에 또는을 호출 하지 않고를 호출한 AFX_SQL_ERROR_ILLEGAL_MODE `CRecordset::AddNew` `CRecordset::Edit` 합니다.

- ODBC 드라이버가 잠금을 지원 하지 않으므로 업데이트에 대 한 레코드를 잠그기 위한 요청을 수행할 수 AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED.

- `CRecordset::Update` `Delete` 고유 키가 없고 여러 레코드를 변경한 테이블에 대해 또는를 호출 AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 합니다.

- 이전에 삭제 한 레코드를 편집 하거나 삭제 하려고 한 AFX_SQL_ERROR_NO_CURRENT_RECORD. 삭제 후 새 현재 레코드로 스크롤해야 합니다.

- ODBC 드라이버가 위치 지정 업데이트를 지원 하지 않으므로 다이너셋에 대 한 요청을 수행할 수 AFX_SQL_ERROR_NO_POSITIONED_UPDATES.

- `CRecordset::Update`또는 `Delete` 를 호출 했지만 작업이 시작 된 경우 레코드를 더 이상 찾을 수 AFX_SQL_ERROR_NO_ROWS_AFFECTED.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED ODBC.DLL 로드 하지 못했습니다. Windows에서이 DLL을 찾을 수 없거나 로드할 수 없습니다. 이 오류는 치명적입니다.

- 수준 2 규격 ODBC 드라이버가 필요 하므로 다이너셋에 대 한 요청을 수행할 수 AFX_SQL_ERROR_ODBC_V2_REQUIRED.

- 데이터 원본이 뒤로 스크롤을 지원 하지 않으므로 스크롤할 수 없습니다. AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY

- 스냅숏 요청에 대 한 호출이 `CRecordset::Open` 실패 했습니다. AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED 드라이버에서 스냅숏을 지원 하지 않습니다. 이는 ODBC 커서 라이브러리 ODBCCURS.DLL 없는 경우에만 발생 합니다.

- 또는 호출에 대 한 `CDatabase::OpenEx` 드라이버가 `CDatabase::Open` 필요한 ODBC SQL 규칙 수준 "최소" (SQL_OSC_MINIMUM)를 준수 하지 AFX_SQL_ERROR_SQL_CONFORMANCE 합니다.

- ODBC 드라이버가 데이터 값의 총 크기를 지정할 수 AFX_SQL_ERROR_SQL_NO_TOTAL `CLongBinary` . 전역 메모리 블록을 미리 할당 된 수 없기 때문에 작업이 실패 했을 수 있습니다.

- 읽기 전용 레코드 집합을 업데이트 하려고 했지만 데이터 원본이 읽기 전용 AFX_SQL_ERROR_RECORDSET_READONLY 경우 레코드 집합 또는 연결 된 개체를 사용 하 여 업데이트 작업을 수행할 수 없습니다 `CDatabase` .

- SQL_ERROR 함수가 실패 했습니다. ODBC 함수에서 반환 되는 오류 메시지는 `SQLError` 데이터 멤버에 저장 됩니다 `m_strError` .

- 잘못 된 환경 핸들, 연결 핸들 또는 문 핸들로 인해 SQL_INVALID_HANDLE 함수에서 오류가 발생 했습니다. 이는 프로그래밍 오류를 나타냅니다. ODBC 함수에서 사용할 수 있는 추가 정보가 없습니다 `SQLError` .

SQL 접두사가 있는 코드는 ODBC에 의해 정의 됩니다. AFX 접두사가 AFXDB에 정의 되어 있습니다. H (MFC\INCLUDE.에 있음)

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a> CDBException:: m_strError

예외를 발생 시킨 오류를 설명 하는 문자열을 포함 합니다.

### <a name="remarks"></a>설명

문자열은 영숫자 용어로 오류를 설명 합니다. 자세한 내용과 예제를 보려면을 참조 하십시오 `m_strStateNativeOrigin` .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a> CDBException:: m_strStateNativeOrigin

예외를 발생 시킨 오류를 설명 하는 문자열을 포함 합니다.

### <a name="remarks"></a>설명

문자열은 "상태:% s, 네이티브:% ld, 원본:% s" 형식입니다. 여기서 형식 코드는 순서 대로 다음을 설명 하는 값으로 대체 됩니다.

- SQLSTATE. ODBC 함수의 *Szsqlstate* 매개 변수에 반환 된 5 문자 오류 코드를 포함 하는 null로 끝나는 문자열 `SQLError` 입니다. SQLSTATE 값은 *Odbc 프로그래머 참조* 에서 부록 a, [odbc 오류 코드](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)에 나열 됩니다. 예: "S0022".

- 함수의 *pfNativeError* 매개 변수에 반환 된 데이터 소스에 해당 하는 네이티브 오류 코드 `SQLError` 입니다. 예: 207.

- 함수의 *Szerrormsg* 매개 변수에 반환 된 오류 메시지 텍스트 `SQLError` 입니다. 이 메시지는 여러 개의 대괄호로 구성 된 이름으로 구성 됩니다. 오류가 원본에서 사용자에 게 전달 되 면 각 ODBC 구성 요소 (데이터 원본, 드라이버, 드라이버 관리자)에 게 고유한 이름이 추가 됩니다. 이 정보는 오류의 원인을 파악 하는 데 도움이 됩니다. 예: [Microsoft] [ODBC SQL Server Driver] [SQL Server]

프레임 워크는 오류 문자열을 해석 하 고 해당 구성 요소를에 배치 합니다 .에 둘 `m_strStateNativeOrigin` `m_strStateNativeOrigin` 이상의 오류에 대 한 정보가 포함 된 경우 오류는 줄바꿈로 구분 됩니다. 프레임 워크는 영숫자 오류 텍스트를에 배치 합니다 `m_strError` .

이 문자열을 구성 하는 데 사용 되는 코드에 대 한 자세한 내용은 *ODBC 프로그래머 참조* 에서 [SQLError](/sql/odbc/reference/syntax/sqlerror-function) 함수를 참조 하세요.

### <a name="example"></a>예제

From ODBC: "State: S0022, Native: 207, 원본: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server] ' ColName ' 열 이름이 잘못 되었습니다.

`m_strStateNativeOrigin`: "State: S0022, Native: 207, 원본: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server]"

`m_strError`: "잘못 된 열 이름 ' ColName '"

## <a name="see-also"></a>참고 항목

[CException 클래스](../../mfc/reference/cexception-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 클래스](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset:: Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::D e)](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException 클래스](../../mfc/reference/cexception-class.md)
