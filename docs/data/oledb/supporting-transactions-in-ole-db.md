---
description: 자세히 알아보기:에서 트랜잭션 지원 OLE DB
title: OLE DB에서 트랜잭션 지원
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: f8d01a0d359a3d33fbe4b88877d8a4452f257c16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272723"
---
# <a name="supporting-transactions-in-ole-db"></a>OLE DB에서 트랜잭션 지원

[트랜잭션은](../../data/transactions-mfc-data-access.md) 데이터 원본에 대 한 일련의 업데이트를 그룹화 하거나 일괄 처리 하 여 한 번에 모두 성공 하 고 커밋 (실패 한 경우) 하거나 커밋되지 않고 전체 트랜잭션을 롤백하는 방법입니다. 이 프로세스는 데이터 원본에 대 한 결과의 무결성을 보장 합니다.

OLE DB는 다음 세 가지 방법으로 트랜잭션을 지원 합니다.

- [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>세션과 트랜잭션 관계

단일 데이터 원본 개체는 하나 이상의 세션 개체를 만들 수 있으며, 각각은 지정 된 시간에 트랜잭션 범위 내부 또는 외부에 있을 수 있습니다.

세션이 트랜잭션을 시작 하지 않는 경우 데이터 저장소에서 해당 세션 내에 수행 된 모든 작업은 각 메서드 호출에서 즉시 커밋됩니다. (이를 자동 커밋 모드나 암시적 모드가 라고도 합니다.)

세션이 트랜잭션으로 들어가면 데이터 저장소에서 해당 세션 내에 수행 된 모든 작업이 해당 트랜잭션의 일부 이며 단일 단위로 커밋되거나 중단 됩니다. 이를 수동 커밋 모드가 라고도 합니다.

트랜잭션 지원은 공급자별로 다릅니다. 사용 중인 공급자가 트랜잭션을 지원 하는 경우 및를 지 원하는 세션 개체를 사용 하 여 `ITransaction` `ITransactionLocal` 중첩 되지 않은 트랜잭션을 시작할 수 있습니다. OLE DB Templates 클래스 [Csession](../../data/oledb/csession-class.md) 은 이러한 인터페이스를 지원 하 고 Visual C++에서 트랜잭션 지원을 구현 하는 데 권장 되는 방법입니다.

## <a name="starting-and-ending-the-transaction"></a>트랜잭션 시작 및 종료

`StartTransaction` `Commit` `Abort` 소비자의 행 집합 개체에서, 및 메서드를 호출 합니다.

`ITransactionLocal::StartTransaction`를 호출 하면 새 로컬 트랜잭션이 시작 됩니다. 트랜잭션을 시작 하는 경우 트랜잭션을 커밋할 때까지 이후 작업에 의해 위임 된 변경 내용이 데이터 저장소에 적용 되지 않습니다.

`ITransaction::Commit`트랜잭션을 호출 하거나 `ITransaction::Abort` 종료 합니다. `Commit` 트랜잭션의 범위 내에 있는 모든 변경 내용이 데이터 저장소에 적용 됩니다. `Abort` 트랜잭션의 범위 내에 있는 모든 변경 내용이 취소 되 고 데이터 저장소가 트랜잭션이 시작 되기 전의 상태로 유지 됩니다.

## <a name="nested-transactions"></a>중첩 된 트랜잭션

[중첩 된 트랜잭션은](/previous-versions/windows/desktop/ms716985(v=vs.85)) 세션에 활성 트랜잭션이 이미 있는 경우 새 로컬 트랜잭션을 시작할 때 발생 합니다. 새 트랜잭션은 현재 트랜잭션 아래 중첩 트랜잭션으로 시작 됩니다. 공급자가 중첩 트랜잭션을 지원 하지 않는 경우 `StartTransaction` 세션에 활성 트랜잭션이 이미 있는 경우를 호출 하면 XACT_E_XTIONEXISTS 반환 됩니다.

## <a name="distributed-transactions"></a>분산 트랜잭션

분산 트랜잭션은 분산 데이터를 업데이트 하는 트랜잭션입니다. 즉, 둘 이상의 네트워크로 연결 된 컴퓨터 시스템에 있는 데이터입니다. 분산 시스템을 통해 트랜잭션을 지원 하려면 OLE DB 트랜잭션 지원 대신 .NET Framework를 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
