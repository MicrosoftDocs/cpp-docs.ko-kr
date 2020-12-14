---
description: '자세히 알아보기: TN042: ODBC 드라이버 개발자 권장 사항'
title: 'TN042: ODBC 드라이버 개발자 권장 사항'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 896c99ffeba98f1ea38771676475c85abf13d983
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215302"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: ODBC 드라이버 개발자 권장 사항

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고는 ODBC 드라이버 작성자를 위한 지침을 설명 합니다. MFC 데이터베이스 클래스에서 수행 하는 ODBC 기능 및 예상 된 다양 한 의미 정보에 대 한 일반적인 요구 사항 및 가정을 간략하게 설명 합니다. 세 가지 `CRecordset` 오픈 모드 (**forwardonly**, **snapshot** 및 **다이너셋**)를 지 원하는 데 필요한 드라이버 기능을 설명 합니다.

## <a name="odbcs-cursor-library"></a>ODBC 커서 라이브러리

MFC 데이터베이스 클래스는 대부분의 경우에는 대부분의 수준 1 ODBC 드라이버에서 제공 하는 기능을 초과 하는 기능을 사용자에 게 제공 합니다. 다행히 ODBC의 Cursor Library는 데이터베이스 클래스와 드라이버 사이에 자동으로 계층화 되며이 추가 기능을 대부분 자동으로 제공 합니다.

예를 들어 대부분의 1.0 드라이버는 역방향 스크롤을 지원 하지 않습니다. 커서 라이브러리는이를 감지할 수 있으며, 드라이버에서 행을 캐시 하 고의 FETCH_PREV 호출에서 요청 된 대로 표시 `SQLExtendedFetch` 합니다.

커서 라이브러리 종속성의 또 다른 중요 한 예는 위치가 지정 된 업데이트입니다. 대부분의 1.0 드라이버에는 위치 지정 업데이트가 없지만 커서 라이브러리는 현재 캐시 된 데이터 값 또는 캐시 된 타임 스탬프 값을 기준으로 데이터 원본의 대상 행을 식별 하는 update 문을 생성 합니다.

클래스 라이브러리는 여러 행 집합을 사용 하지 않습니다. 따라서 일부 `SQLSetPos` 문은 항상 행 집합의 1 행에 적용 됩니다.

## <a name="cdatabases"></a>CDatabases

각 `CDatabase` 는 단일 **HDBC** 을 할당 합니다. `CDatabase`의 함수를 `ExecuteSQL` 사용 하는 경우 **HSTMT** 가 일시적으로 할당 됩니다. 따라서 여러가 `CDatabase` 필요한 경우 **HENV** 당 여러 **HDBC** s를 지원 해야 합니다.

데이터베이스 클래스에는 cursor 라이브러리가 필요 합니다. 이는 `SQLSetConnections` **SQL_ODBC_CURSORS** **SQL_CUR_USE_ODBC** 호출에 반영 됩니다.

`SQLDriverConnect`**SQL_DRIVER_COMPLETE** 는에서 `CDatabase::Open` 데이터 원본에 대 한 연결을 설정 하는 데 사용 됩니다.

드라이버는 `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1** `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM** 를 지원 해야 합니다.

및 해당 종속 레코드 집합에 대 한 트랜잭션을 지원 하려면 `CDatabase` `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` **SQL_CURSOR_ROLLBACK_BEHAVIOR** **SQL_CR_PRESERVE** 있어야 합니다. 그렇지 않으면 트랜잭션 제어를 수행 하려는 시도가 무시 됩니다.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` 지원 되어야 합니다. "Y"를 반환 하면 데이터 원본에 대해 업데이트 작업이 수행 되지 않습니다.

`CDatabase`가 ReadOnly로 열려 있는 경우 데이터 소스를 읽기 전용으로 설정 하려는 시도는 `SQLSetConnectOption SQL_ACCESS_MODE` , **SQL_MODE_READ_ONLY** 로 생성 됩니다.

식별자에 따옴표를 지정 해야 하는 경우에는 호출을 통해 드라이버에서이 정보를 반환 해야 합니다 `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` .

디버깅을 위해 `SQLGetInfo SQL_DBMS_VER` 및 **SQL_DBMS_NAME** 드라이버에서 검색 됩니다.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`및 **SQL_ASYNC_ENABLE** 은의 HDBC에서 호출 될 수 있습니다 `CDatabase` . 

`SQLError` any 또는 all 인수 NULL을 사용 하 여를 호출할 수 있습니다.

물론, 및가 지원 되어야 합니다 `SQLAllocEnv` `SQLAllocConnect` `SQLDisconnect` `SQLFreeConnect` .

## <a name="executesql"></a>ExecuteSQL

임시 **HSTMT** 를 할당 하 고 해제 하는 것 외에도, `ExecuteSQL` 및를 호출 `SQLExecDirect` `SQLFetch` `SQLNumResultCol` `SQLMoreResults` 합니다. `SQLCancel`**HSTMT** 에서 호출 될 수 있습니다.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` 가 호출 됩니다.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, 롤백

`SQLSetConnectOption SQL_AUTOCOMMIT``SQLTransact SQL_COMMIT`트랜잭션 요청이 수행 되는 경우에는 **SQL_ROLLBACK** 및 **SQL_AUTOCOMMIT** 호출 됩니다.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare` , `SQLExecute` (및의 경우), `Open` `Requery` `SQLExecDirect` (업데이트 작업의 경우)은 `SQLFreeStmt` 지원 되어야 합니다. `SQLNumResultCols` 및 `SQLDescribeCol` 는 다양 한 시간에 결과 집합에서 호출 됩니다.

`SQLSetParam` 는 매개 변수 데이터 및 **DATA_AT_EXEC** 기능을 바인딩하는 데 광범위 하 게 사용 됩니다.

`SQLBindCol` 는 ODBC를 사용 하 여 출력 열 데이터 저장소 위치를 등록 하는 데 광범위 하 게 사용 됩니다.

두 `SQLGetData` 호출은 **SQL_LONG_VARCHAR** 및 **SQL_LONG_VARBINARY** 데이터를 검색 하는 데 사용 됩니다. 첫 번째 호출은 cbMaxValue가 0 인를 호출 하 고 유효한 pcbValue를 사용 하 여 열 값의 전체 길이를 찾으려고 시도 합니다 `SQLGetData` . PcbValue가 **SQL_NO_TOTAL** 을 보유 하는 경우 예외가 throw 됩니다. 그렇지 않으면 **HGLOBAL** 가 할당 되 고 다른 `SQLGetData` 호출에서 전체 결과를 검색 합니다.

## <a name="updating"></a>업데이트

비관적 잠금이 요청 되 면이 `SQLGetInfo SQL_LOCK_TYPES` 쿼리 됩니다. **SQL_LCK_EXCLUSIVE** 지원 되지 않는 경우 예외가 throw 됩니다.

`CRecordset`(**스냅숏** 또는 **다이너셋**)를 업데이트 하려고 하면 두 번째 **HSTMT** 가 할당 됩니다. 두 번째 **HSTMT** 를 지원 하지 않는 드라이버의 경우 커서 라이브러리는이 기능을 시뮬레이트합니다. 불행 하 게도 두 번째 **hstmt** 의 요청을 처리 하기 전에 첫 번째 **hstmt** 의 현재 쿼리를 완료에 강제로 적용 하는 것을 의미할 수 있습니다.

`SQLFreeStmt SQL_CLOSE` 및 **SQL_RESET_PARAMS** 는 `SQLGetCursorName` 업데이트 작업 중에 호출 됩니다.

**Outputcolumns** 에 **CLongBinarys** 이 있는 경우 ODBC의 **DATA_AT_EXEC** 기능이 지원 되어야 합니다. 여기에는의 반환 **SQL_NEED_DATA** , 및가 포함 됩니다 `SQLExecDirect` `SQLParamData` `SQLPutData` .

`SQLRowCount` 는를 실행 한 후에 호출 되어 1 개의 레코드만에서 업데이트 되었는지 확인 `SQLExecDirect` 합니다.

## <a name="forwardonly-cursors"></a>ForwardOnly 커서

`SQLFetch`작업에만 필요 `Move` 합니다. **Forwardonly** 커서는 업데이트를 지원 하지 않습니다.

## <a name="snapshot-cursors"></a>스냅숏 커서

스냅숏 기능을 사용 하려면 `SQLExtendedFetch` 지원이 필요 합니다. 위에서 설명한 것 처럼 ODBC 커서 라이브러리는 드라이버가 지원 하지 않는 경우 `SQLExtendedFetch` 를 검색 하 고 필요한 지원을 제공 합니다.

`SQLGetInfo`**SQL_SCROLL_OPTIONS** **SQL_SO_STATIC** 를 지원 해야 합니다.

## <a name="dynaset-cursors"></a>다이너셋 커서

다음은 다이너셋을 여는 데 필요한 최소한의 지원입니다.

`SQLGetInfo`**SQL_ODBC_VER** > "01"을 반환 해야 합니다.

`SQLGetInfo`**SQL_SCROLL_OPTIONS** **SQL_SO_KEYSET_DRIVEN** 를 지원 해야 합니다.

`SQLGetInfo`**SQL_ROW_UPDATES** "Y"를 반환 해야 합니다.

`SQLGetInfo`**SQL_POSITIONED_UPDATES** **SQL_PS_POSITIONED_DELETE** 및 **SQL_PS_POSITIONED_UPDATE** 를 지원 해야 합니다.

또한 비관적 잠금이 요청 되 면 `SQLSetPos` irow 1, fRefresh FALSE 및 fLock **SQL_LCK_EXCLUSIVE** 를 사용 하 여에 대 한 호출이 수행 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
