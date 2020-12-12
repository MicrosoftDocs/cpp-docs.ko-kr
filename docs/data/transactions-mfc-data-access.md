---
description: '자세한 정보: 트랜잭션 (MFC Data Access)'
title: 트랜잭션  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: bd04e1c8f1b5ef11e66a3c2c3f1e391f409b4892
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116485"
---
# <a name="transactions--mfc-data-access"></a>트랜잭션  (MFC Data Access)

트랜잭션의 개념은 데이터베이스의 결과 상태가 일련의 작업에 성공한 총 횟수에 따라 달라지는 사례를 처리하기 위해 개발되었습니다. 연속적인 작업을 수행하면 이전 작업의 결과가 수정될 수 있기 때문입니다. 이러한 경우 한 작업이 실패하면 결과 상태가 비활성화 상태가 될 수 있습니다.

이 문제를 해결하기 위해 트랜잭션은 최종 결과의 무결성을 보장할 수 있는 방식으로 일련의 작업을 그룹화합니다. 모든 작업이 성공한 후 커밋(데이터베이스에 기록)되어야 합니다. 그렇지 않으면 전체 트랜잭션이 실패합니다. 트랜잭션을 취소하는 것을 롤백이라고 합니다. 롤백을 수행하면 변경으로부터 데이터베이스를 복구하고 트랜잭션 이전의 상태로 데이터베이스를 되돌릴 수 있습니다.

자동화된 은행 거래를 예로 들자면, A 계좌에서 B 계좌로 송금을 할 때는 A 계좌로부터의 출금과 B 계좌로의 입금이 둘 다 성공해야 송금이 정상적으로 처리되며 그렇지 않으면 전체 거래가 실패해야 합니다.

트랜잭션은 ACID 속성을 포함해야 합니다. 여기서 ACID는 다음을 의미합니다.

- **원자성** 트랜잭션은 작업의 원자성 단위 이며 한 번만 실행 됩니다. 모든 작업을 수행 하거나 모든 작업을 수행 하지는 않습니다.

- **일관성** 트랜잭션은 데이터의 일관성을 유지 하 고 일관 된 데이터 상태를 데이터의 다른 일관 된 상태로 변환 합니다. 즉, 트랜잭션으로 바인딩된 데이터의 의미 체계가 유지되어야 합니다.

- **격리** 트랜잭션은 격리 단위 이며 각각은 동시 트랜잭션과 독립적으로 발생 합니다. 트랜잭션은 다른 트랜잭션의 중간 단계를 확인할 수 없습니다.

- **내구성** 트랜잭션은 복구 단위입니다. 트랜잭션이 성공하면 시스템이 충돌하거나 종료되어도 해당 업데이트는 유지됩니다. 트랜잭션이 실패하면 시스템은 트랜잭션을 커밋하기 전의 상태로 유지됩니다.

OLE DB ( [OLE DB의 트랜잭션 지원](../data/oledb/supporting-transactions-in-ole-db.md)참조) 또는 ODBC ( [트랜잭션 (ODBC)](../data/odbc/transaction-odbc.md)참조)에서 트랜잭션을 지원할 수 있습니다.

분산 트랜잭션은 분산된 데이터, 즉 네트워크로 연결된 둘 이상의 컴퓨터 시스템에 있는 데이터를 업데이트하는 트랜잭션입니다. 분산 시스템을 통해 트랜잭션을 지원 하려면 OLE DB 트랜잭션 지원 대신 ADO.NET를 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[데이터 액세스 프로그래밍 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
