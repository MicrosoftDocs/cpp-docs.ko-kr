---
description: '자세한 정보: 레코드 집합: 업데이트에 대 한 추가 정보 (ODBC)'
title: '레코드 집합: 업데이트에 대한 추가 정보(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: 9d125456189828d50f1fbfd4aece00a16790424f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304443"
---
# <a name="recordset-more-about-updates-odbc"></a>레코드 집합: 업데이트에 대한 추가 정보(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 토픽에서는 다음 내용을 설명합니다.

- [트랜잭션과 같은 다른 작업은 업데이트에 영향을 줍니다](#_core_how_transactions_affect_updates).

- [업데이트 및 다른 사용자의 업데이트](#_core_your_updates_and_the_updates_of_other_users)

- [Update 및 Delete 멤버 함수에 대해 자세히 알아봅니다](#_core_more_about_update_and_delete).

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 구현한 경우 일부 정보가 적용 되지 않습니다. 예를 들어,, 및 멤버 함수는 호출할 수 없습니다. `AddNew` `Edit` `Delete` `Update` 그러나 트랜잭션을 수행할 수 있습니다. 대량 행 페치에 대 한 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a> 다른 작업이 업데이트에 미치는 영향

업데이트는 업데이트 시 적용 되는 트랜잭션의 영향을 받으며, 트랜잭션을 완료 하기 전에 레코드 집합을 닫고, 트랜잭션을 완료 하기 전에 스크롤 합니다.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a> 트랜잭션이 업데이트에 미치는 영향

, 및 작업을 이해 하는 것 외에도, `AddNew` `Edit` 및 `Delete` `BeginTrans` `CommitTrans` `Rollback` 의 멤버 함수가 [CRecordset](../../mfc/reference/crecordset-class.md)의 업데이트 함수를 [](../../mfc/reference/cdatabase-class.md) 사용 하는 방식을 이해 하는 것이 중요 합니다.

기본적으로를 호출 하면 `AddNew` 및에 대 한 호출이 `Edit` 즉시 데이터 소스에 영향을 줍니다 `Update` . `Delete` 호출이 즉시 적용 됩니다. 하지만 트랜잭션을 설정 하 고 이러한 호출의 일괄 처리를 실행할 수 있습니다. 업데이트는 커밋할 때까지 영구적이 지 않습니다. 생각이 바뀌면 트랜잭션을 커밋하는 대신 롤백할 수 있습니다.

트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)을 참조 하십시오.

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a> 레코드 집합을 닫아 업데이트에 미치는 영향

`CDatabase`진행 중인 트랜잭션 ( [cdatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) 또는 [cdatabase:: Rollback](../../mfc/reference/cdatabase-class.md#rollback)이라고 함)을 사용 하 여 레코드 집합 또는 연결 된 개체를 닫으면 트랜잭션이 자동으로 롤백됩니다 (데이터베이스 백 엔드가 Microsoft Jet 데이터베이스 엔진 인 경우 제외).

> [!CAUTION]
> Microsoft Jet 데이터베이스 엔진을 사용 하는 경우 명시적 트랜잭션 내에서 레코드 집합을 닫으면 명시적 트랜잭션이 커밋되거나 롤백될 때까지 수정 되었거나 잠금이 설정 된 행이 해제 되지 않습니다. 항상 명시적 Jet 트랜잭션 내부 또는 외부에서 레코드 집합을 열고 닫는 것이 좋습니다.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a> 스크롤이 업데이트에 미치는 영향

레코드 집합의 [레코드 집합: 스크롤 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) 을 사용 하는 경우에는 편집 버퍼가 새로운 현재 레코드 (이전 레코드가 먼저 저장 되지 않음)로 채워집니다. 스크롤은 이전에 삭제 된 레코드를 건너뜁니다. `AddNew`, 또는를 호출 하지 않고 또는를 호출한 후에 스크롤하면 `Edit` `Update` `CommitTrans` `Rollback` 새 레코드가 편집 버퍼로 가져오기 때문에 모든 변경 내용이 손실 됩니다 (경고 없음). 편집 버퍼는로 스크롤 된 레코드로 채워지고, 저장 된 레코드가 해제 되 고, 데이터 원본에서 변경 내용이 발생 하지 않습니다. 이는 및에 모두 적용 됩니다 `AddNew` `Edit` .

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a> 업데이트 및 다른 사용자의 업데이트

레코드 집합을 사용 하 여 데이터를 업데이트 하는 경우 업데이트는 다른 사용자에 게 영향을 줍니다. 마찬가지로, 레코드 집합의 수명 동안 다른 사용자의 업데이트는 영향을 받습니다.

다중 사용자 환경에서 다른 사용자는 레코드 집합에서 선택한 것과 동일한 레코드 중 일부를 포함 하는 레코드 집합을 열 수 있습니다. 검색 하기 전에 레코드에 대 한 변경 내용은 레코드 집합에 반영 됩니다. 다이너셋은 스크롤할 때마다 레코드를 검색 하기 때문에, 다이너셋은 레코드로 스크롤할 때마다 변경 내용을 반영 합니다. 스냅숏은 처음 스크롤할 때 레코드를 검색 하므로 스냅숏은 처음에 레코드로 스크롤 하기 전에 발생 하는 변경 내용만 반영 합니다.

레코드 집합을 연 후 다른 사용자가 추가한 레코드는 다시 쿼리하지 않는 한 레코드 집합에 표시 되지 않습니다. 레코드 집합이 다이너셋 인 경우 영향을 받는 레코드로 스크롤하면 다른 사용자가 기존 레코드를 편집할 수 없습니다. 레코드 집합이 스냅숏이 면 스냅숏을 다시 쿼리할 때까지 편집 내용이 표시 되지 않습니다. 스냅숏의 다른 사용자가 추가 하거나 삭제 한 레코드 또는 다이너셋에서 다른 사용자가 추가한 레코드를 확인 하려면 [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) 를 호출 하 여 레코드 집합을 다시 작성 합니다. 다른 사용자의 삭제는 다이너셋에 표시 됩니다. 또한를 호출 `Requery` 하 여 추가 하는 레코드를 볼 수 있지만 삭제를 볼 수는 없습니다.

> [!TIP]
> 전체 스냅숏을 한 번에 강제로 캐시 하려면 `MoveLast` 스냅숏을 연 후 즉시를 호출 합니다. 그런 다음 `MoveFirst` 를 호출 하 여 레코드 작업을 시작 합니다. `MoveLast` 모든 레코드를 스크롤 하는 것과 동일 하지만 모든 레코드를 한 번에 검색 합니다. 그러나이로 인해 성능이 저하 될 수 있으며 일부 드라이버에는 필요 하지 않을 수 있습니다.

다른 사용자에 대 한 업데이트의 효과는 사용자에 게 미치는 영향과 비슷합니다.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a> 업데이트 및 삭제에 대 한 자세한 정보

이 섹션에서는 및를 사용 하는 데 도움이 되는 추가 정보를 제공 합니다 `Update` `Delete` .

### <a name="update-success-and-failure"></a>업데이트 성공 및 실패

이 `Update` 성공 하면 `AddNew` 또는 `Edit` 모드가 종료 됩니다. `AddNew`또는 모드를 다시 시작 하려면 `Edit` 또는를 `AddNew` 호출 `Edit` 합니다.

`Update`가 실패 하거나 (FALSE를 반환 하거나 예외를 throw 하는 경우), `AddNew` `Edit` 마지막으로 호출 된 함수에 따라 또는 모드를 유지 합니다. 그러면 다음 중 하나를 수행합니다.

- 필드 데이터 멤버를 수정한 후 다시 시도 하십시오 `Update` .

- `AddNew`을 호출 하 여 필드 데이터 멤버를 Null로 다시 설정 하 고 필드 데이터 멤버의 값을 설정한 다음를 `Update` 다시 호출 합니다.

- `Edit`또는에 대 한 첫 번째 호출 전에 레코드 집합에 있던 값을 다시 로드 하려면를 호출 하 `AddNew` `Edit` 고, 필드 데이터 멤버의 값을 설정한 다음를 `Update` 다시 호출 합니다. 호출 후를 `Update` 제외 하 고 호출 후에는 `AddNew` 필드 데이터 멤버에 새 값이 유지 됩니다.

- `Move` `Move` 모든 변경 내용을 플러시하고 적용 되는 또는 모드를 종료 하는를 호출 (AFX_MOVE_REFRESH의 매개 변수 또는 0을 포함 하 여) `AddNew` `Edit` .

### <a name="update-and-delete"></a>업데이트 및 삭제

이 섹션은 및 둘 다에 적용 됩니다 `Update` `Delete` .

또는 작업에서 한 개의 `Update` `Delete` 레코드만 업데이트 해야 합니다. 이 레코드는 레코드 집합의 필드에 있는 데이터 값에 해당 하는 현재 레코드입니다. 어떤 이유로 영향을 받는 레코드가 없거나 둘 이상의 레코드가 영향을 받는 경우 다음 **RETCODE** 값 중 하나를 포함 하는 예외가 throw 됩니다.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

이러한 예외가 throw 되 면 `AddNew` `Edit` 또는를 호출할 때의 또는 상태를 그대로 유지 합니다 `Update` `Delete` . 이러한 예외를 확인 하는 가장 일반적인 시나리오는 다음과 같습니다. 다음이 표시 될 가능성이 높습니다.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED 낙관적 잠금 모드를 사용 하 고 다른 사용자가 업데이트 또는 삭제할 올바른 레코드를 식별할 수 없도록 하는 방식으로 레코드를 수정한 경우에 사용 합니다.

- 업데이트 하는 테이블에 기본 키 또는 고유 인덱스가 없고 레코드 집합에 열이 부족 하 여 테이블 행을 고유 하 게 식별할 수 없는 경우에 AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 합니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)
