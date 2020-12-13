---
description: '자세한 정보: 트랜잭션 (ODBC)'
title: 트랜잭션(ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: a7b769c37b58b34433939a18cb0dccf5fb4a798d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333872"
---
# <a name="transaction-odbc"></a>트랜잭션(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

트랜잭션은 모든 [데이터 원본](../../data/odbc/data-source-odbc.md) 에 대 한 일련의 업데이트를 그룹화 하거나 일괄 처리 하는 방법으로, 트랜잭션을 롤백하는 경우 모든 항목이 한 번에 커밋되거나 none이 커밋됩니다. 트랜잭션을 사용 하지 않는 경우 데이터 원본에 대 한 변경 내용은 요청 시 커밋되지 않고 자동으로 커밋됩니다.

> [!NOTE]
> 일부 ODBC 데이터베이스 드라이버도 트랜잭션을 지원 하지 않습니다. `CanTransact` [CDatabase](../../mfc/reference/cdatabase-class.md) 또는 [CRecordset](../../mfc/reference/crecordset-class.md) 개체의 멤버 함수를 호출 하 여 드라이버가 지정 된 데이터베이스에 대 한 트랜잭션을 지원 하는지 여부를 확인 합니다. `CanTransact`에서는 데이터 원본이 전체 트랜잭션 지원을 제공 하는지 여부를 알 수 없습니다. 또한 및 이후에 및 `CDatabase::GetCursorCommitBehavior` `CDatabase::GetCursorRollbackBehavior` 를 호출 `CommitTrans` 하 여 `Rollback` 열린 개체의 트랜잭션 효과를 확인 `CRecordset` 해야 합니다.

`AddNew`개체의 및 멤버 함수에 대 한 호출은를 `Edit` `CRecordset` 호출할 때 데이터 소스에 즉시 영향을 줍니다 `Update` . `Delete` 호출도 즉시 적용 됩니다. 이와 대조적으로,, 및에 대 한 여러 호출로 구성 된 트랜잭션을 사용할 수 있습니다 .이는 `AddNew` `Edit` `Update` `Delete` 수행 되지만 명시적으로를 호출할 때까지 커밋되지 않습니다 `CommitTrans` . 트랜잭션을 설정 하면 해당 호출을 롤백하는 기능을 유지 하면서 일련의 이러한 호출을 실행할 수 있습니다. 중요 한 리소스를 사용할 수 없거나 다른 조건으로 인해 전체 트랜잭션이 완료 되지 않는 경우 트랜잭션을 커밋하는 대신 롤백할 수 있습니다. 이 경우 트랜잭션에 속하는 변경 내용이 데이터 원본에 영향을 주지 않습니다.

> [!NOTE]
> 현재는 `CRecordset` 대량 행 페치를 구현한 경우 클래스는 데이터 원본에 대 한 업데이트를 지원 하지 않습니다. 즉,, 또는에 대 한 호출을 수행할 수 없습니다 `AddNew` `Edit` `Delete` `Update` . 그러나 사용자 고유의 함수를 작성 하 여 업데이트를 수행한 다음 지정 된 트랜잭션 내에서 해당 함수를 호출할 수 있습니다. 대량 행 페치에 대 한 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

> [!NOTE]
> 레코드 집합에 영향을 주는 것 외에도 트랜잭션은  `CDatabase` 해당 **HDBC** 를 기반으로 하는 odbc HDBC 또는 개체와 연결 된 odbc를 사용  하는 경우 직접 실행 하는 SQL 문에 영향을 줍니다.

트랜잭션은 여러 레코드를 동시에 업데이트 해야 하는 경우에 특히 유용 합니다. 이 경우 마지막 업데이트를 수행 하기 전에 예외가 throw 된 경우에 발생할 수 있는 경우와 같이 반 완료 된 트랜잭션을 방지 하려고 합니다. 이러한 업데이트를 트랜잭션으로 그룹화 하면 변경 내용 으로부터 복구 (롤백) 하 고 레코드를 pretransaction 상태로 되돌립니다. 예를 들어 은행이 계정 A에서 계정 B로 비용을 전송 하는 경우 A의 출금 및 B에 대 한 입금은 모두 자금을 올바르게 처리 하는 데 성공 하거나 전체 트랜잭션이 실패 해야 합니다.

데이터베이스 클래스에서는 개체를 통해 트랜잭션을 수행 `CDatabase` 합니다. `CDatabase`개체는 데이터 원본에 대 한 연결을 나타내고 해당 개체와 연결 된 하나 이상의 레코드 집합은 `CDatabase` 레코드 집합 멤버 함수를 통해 데이터베이스의 테이블에 대해 작동 합니다.

> [!NOTE]
> 한 수준의 트랜잭션만 지원 됩니다. 트랜잭션을 중첩할 수 없으며 트랜잭션이 여러 데이터베이스 개체에 걸쳐 있을 수도 없습니다.

다음 항목에서는 트랜잭션이 수행 되는 방법에 대 한 자세한 정보를 제공 합니다.

- [트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [트랜잭션: 트랜잭션이 업데이트에 미치는 영향 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)
