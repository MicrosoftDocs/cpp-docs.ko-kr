---
title: '트랜잭션: 트랜잭션이 미치는 영향 (ODBC) 업데이트 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 21e6511a66129cb172ff10fedfa563bc4d663d19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078519"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>트랜잭션: 트랜잭션이 업데이트에 미치는 영향(ODBC)

업데이트를 [데이터 원본](../../data/odbc/data-source-odbc.md) 편집 버퍼 (트랜잭션 외부에서 사용 되는 것과 동일한 방법)를 사용 하 여 트랜잭션 동안 관리 됩니다. 레코드 집합의 필드 데이터 멤버는 전체적으로 레코드 집합을 중에 일시적으로 백업 되는 현재 레코드를 포함 하는 편집 버퍼 역할을 `AddNew` 또는 `Edit`합니다. 중를 `Delete` 작업을 현재 레코드는 트랜잭션 내에서 백업 되지 않습니다. 업데이트에서 현재 레코드를 저장 하는 방법 및 편집 버퍼에 대 한 자세한 내용은 참조 하세요. [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)합니다.  
  
> [!NOTE]
>  대량 행 페치를 구현한 경우 호출할 수 없습니다 `AddNew`하십시오 `Edit`, 또는 `Delete`합니다. 대신 데이터 원본에 대 한 업데이트를 수행 하기 위해 사용자 고유의 함수를 작성 해야 합니다. 대량 행 페치에 대 한 자세한 내용은 참조 하십시오 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)합니다.  
  
트랜잭션 중 `AddNew`, `Edit`, 및 `Delete` 작업을 커밋 또는 롤백될 수 있습니다. 미치는 `CommitTrans` 고 `Rollback` 현재 레코드를 편집 버퍼에 복원 하지 않을 수 있습니다. 현재 레코드가 올바르게 복원 되었는지 확인 하려면 반드시 알아야 하는 방법을 `CommitTrans` 하 고 `Rollback` 의 멤버 함수 `CDatabase` 의 업데이트 기능을 사용 하 여 회사 `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans 업데이트에 미치는 영향  

다음 표에서 미치는 `CommitTrans` 트랜잭션에서 합니다.  
  
### <a name="how-committrans-affects-updates"></a>CommitTrans 업데이트에 미치는 영향  
  
|작업|데이터 원본 상태|  
|---------------|---------------------------|  
|`AddNew` 및 `Update`, 한 다음 `CommitTrans`|데이터 원본에 새 레코드가 추가 됩니다.|  
|`AddNew` (없이 `Update`)를 선택한 다음 `CommitTrans`|새 레코드가 손실 됩니다. 레코드를 데이터 원본에 추가 되지 않습니다.|  
|`Edit` 및 `Update`, 한 다음 `CommitTrans`|데이터 원본에 커밋된 편집 합니다.|  
|`Edit` (없이 `Update`)를 선택한 다음 `CommitTrans`|레코드에 편집 내용이 손실 됩니다. 레코드는 데이터 원본에 변경 되지 않은 상태로 유지 됩니다.|  
|`Delete` 그런 다음 `CommitTrans`|레코드를 데이터 소스에서 삭제 합니다.|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Rollback 트랜잭션에 미치는 영향  

다음 표에서 미치는 `Rollback` 트랜잭션에서 합니다.  
  
### <a name="how-rollback-affects-transactions"></a>Rollback 트랜잭션에 미치는 영향  
  
|작업|현재 레코드의 상태|필요한 작업|데이터 원본 상태|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew` 및 `Update`, 한 다음 `Rollback`|현재 레코드의 콘텐츠는 새 레코드에 대 한 공간을 만들기 위해 일시적으로 저장 됩니다. 새 레코드 편집 버퍼에 입력 됩니다. 후 `Update` 호출 되는 현재 레코드 편집 버퍼 복원 됩니다.||수행한 데이터 소스에 추가 `Update` 반전 됩니다.|  
|`AddNew` (없이 `Update`), 한 다음 `Rollback`|현재 레코드의 콘텐츠는 새 레코드에 대 한 공간을 만들기 위해 일시적으로 저장 됩니다. 편집할 새 레코드를 포함 하는 버퍼입니다.|호출 `AddNew` 편집 버퍼는 빈, 새 레코드를 복원 하려면 다시 합니다. 호출 또는 `Move`편집 버퍼를 이전 값을 복원 하려면 (0).|때문에 `Update` 가 호출 되지 데이터 소스에 대 한 변경 내용은 없습니다.|  
|`Edit` 및 `Update`, 한 다음 `Rollback`|현재 레코드를 편집 되지 않은 버전은 일시적으로 저장 됩니다. 편집 버퍼의 콘텐츠를 편집 했습니다. 후 `Update` 호출 되는 편집 되지 않은 레코드의 버전도 임시로 저장 됩니다.|*다이너셋*: 현재 레코드를 편집 버퍼 레코드의 편집 되지 않은 버전을 복원 하려면 다시 스크롤합니다.<br /><br /> *스냅숏*: 호출 `Requery` 데이터 원본에서 레코드 집합을 새로 고쳐야 합니다.|수행한 데이터 원본에 변경 `Update` 반대가 됩니다.|  
|`Edit` (없이 `Update`), 한 다음 `Rollback`|현재 레코드를 편집 되지 않은 버전은 일시적으로 저장 됩니다. 편집 버퍼의 콘텐츠를 편집 했습니다.|호출 `Edit` 편집 버퍼 레코드의 편집 되지 않은 버전을 복원 하려면 다시 합니다.|때문에 `Update` 가 호출 되지 데이터 소스에 대 한 변경 내용은 없습니다.|  
|`Delete` 그런 다음 `Rollback`|현재 레코드의 내용이 삭제 됩니다.|호출 `Requery` 데이터 소스의 현재 레코드의 콘텐츠를 복원 합니다.|데이터 원본에서 데이터 삭제 반전 됩니다.|  
  
## <a name="see-also"></a>참고 항목  

[트랜잭션(ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[트랜잭션(ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[트랜잭션: 레코드 집합에서 트랜잭션 수행(ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)