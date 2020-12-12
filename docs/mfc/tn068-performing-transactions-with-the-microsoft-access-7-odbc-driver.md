---
description: '자세히 알아보기: TN068: Microsoft Access 7 ODBC 드라이버를 사용 하 여 트랜잭션 수행'
title: 'TN068: Microsoft Access 7 ODBC 드라이버를 사용하여 트랜잭션 수행'
ms.date: 06/28/2018
f1_keywords:
- vc.data.odbc
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
ms.openlocfilehash: ebc98a0fd2bea78c0159daa9a53a11a292482257
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214548"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: Microsoft Access 7 ODBC 드라이버를 사용하여 트랜잭션 수행

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 Microsoft ODBC 데스크톱 드라이버 팩 버전 3.0에 포함 된 MFC ODBC 데이터베이스 클래스 및 Microsoft Access 7.0 ODBC 드라이버를 사용 하는 경우 트랜잭션을 수행 하는 방법을 설명 합니다.

## <a name="overview"></a>개요

데이터베이스 응용 프로그램에서 트랜잭션을 수행 하 `CDatabase::BeginTrans` `CRecordset::Open` 는 경우 응용 프로그램에서 및를 올바른 순서로 호출 해야 합니다. Microsoft Access 7.0 드라이버는 Microsoft Jet 데이터베이스 엔진을 사용 하며, Jet에서는 응용 프로그램이 열려 있는 커서를 포함 하는 데이터베이스에서 트랜잭션을 시작 하지 않습니다. MFC ODBC 데이터베이스 클래스의 경우 열린 커서는 열린 개체와 같습니다 `CRecordset` .

을 호출 하기 전에 레코드 집합을 여는 경우 `BeginTrans` 오류 메시지가 표시 되지 않을 수 있습니다. 그러나 응용 프로그램을 업데이트 하는 모든 레코드 집합은를 호출한 후 영구적으로 유지 되 `CRecordset::Update` 고를 호출 하 여 업데이트를 롤백하지 않습니다 `Rollback` . 이 문제를 방지 하려면 먼저를 호출한 `BeginTrans` 다음 레코드 집합을 열어야 합니다.

MFC는 커서 커밋 및 롤백 동작에 대 한 드라이버 기능을 확인 합니다. 클래스 `CDatabase` 는 및의 두 멤버 함수를 제공 `GetCursorCommitBehavior` `GetCursorRollbackBehavior` 하 여 열려 있는 개체에 대 한 트랜잭션의 효과를 결정 합니다 `CRecordset` . Microsoft Access 7.0 ODBC 드라이버의 경우 이러한 멤버 함수 `SQL_CB_CLOSE` 는 액세스 드라이버가 커서 유지를 지원 하지 않기 때문에를 반환 합니다. 따라서 `CRecordset::Requery` 또는 작업 다음에를 호출 해야 합니다 `CommitTrans` `Rollback` .

여러 트랜잭션을 한 번 더 수행 해야 하는 경우 `Requery` 첫 번째 트랜잭션 후에를 호출 하 고 다음 단계를 시작할 수 없습니다. Jet의 요구 사항을 충족 하기 위해에 대 한 다음 호출 전에 레코드 집합을 닫아야 합니다 `BeginTrans` . 이 기술 정보는 이러한 상황을 처리 하는 두 가지 방법을 설명 합니다.

- 각 or 작업 후에 레코드 집합을 닫는 중 `CommitTrans` `Rollback` 입니다.

- ODBC API 함수 사용 `SQLFreeStmt` .

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>각 CommitTrans 또는 Rollback 작업 후 레코드 집합 닫기

트랜잭션을 시작 하기 전에 레코드 집합 개체가 닫혀 있는지 확인 합니다. 를 호출한 후에 `BeginTrans` 는 레코드 집합의 `Open` 멤버 함수를 호출 합니다. 또는를 호출한 후 즉시 레코드 집합을 닫습니다 `CommitTrans` `Rollback` . 레코드 집합을 반복적으로 열고 닫는 경우 응용 프로그램의 성능이 저하 될 수 있습니다.

## <a name="using-sqlfreestmt"></a>SQLFreeStmt 사용

ODBC API 함수를 사용 하 여 `SQLFreeStmt` 트랜잭션을 종료 한 후 커서를 명시적으로 닫을 수도 있습니다. 다른 트랜잭션을 시작 하려면를 호출한 `BeginTrans` 다음을 호출 `CRecordset::Requery` 합니다. 를 호출할 때 `SQLFreeStmt` 레코드 집합의 HSTMT를 첫 번째 매개 변수로 지정 하 고 두 번째 매개 변수로 *SQL_CLOSE* 해야 합니다. 이 방법은 모든 트랜잭션이 시작 될 때 레코드 집합을 닫고 여는 것 보다 빠릅니다. 다음 코드에서는이 기술을 구현 하는 방법을 보여 줍니다.

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

// close the cursor
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

// start transaction 2
db.BeginTrans();
// now get the result set
rs.Requery();

// manipulate data

// end transaction 2
db.CommitTrans();

rs.Close();
db.Close();
```

이 기술을 구현 하는 또 다른 방법은 새 함수를 작성 하는 것입니다 .이 함수를 호출 하 여 `RequeryWithBeginTrans` 첫 번째 트랜잭션을 커밋하거나 롤백하는 후 다음 트랜잭션을 시작할 수 있습니다. 이러한 함수를 작성 하려면 다음 단계를 수행 합니다.

1. 의 코드를 `CRecordset::Requery( )` 새 함수에 복사 합니다.

2. 에 대 한 호출 바로 뒤에 다음 줄을 추가 합니다 `SQLFreeStmt` .

   `m_pDatabase->BeginTrans( );`

이제 각 트랜잭션 쌍 간에이 함수를 호출할 수 있습니다.

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> *M_strFilter* *m_strSort* 또는 트랜잭션 간에 레코드 집합 멤버 변수를 변경 해야 하는 경우에는이 방법을 사용 하지 마십시오. 이 경우 각 또는 작업 후에 레코드 집합을 닫아야 `CommitTrans` 합니다 `Rollback` .

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
