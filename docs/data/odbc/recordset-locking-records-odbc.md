---
description: '자세한 정보: 레코드 집합: 레코드 잠금 (ODBC)'
title: '레코드 집합: 레코드 잠금(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: 1833aff2a1a68affe02cdcf5294007802452bbf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304482"
---
# <a name="recordset-locking-records-odbc"></a>레코드 집합: 레코드 잠금(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 토픽에서는 다음 내용을 설명합니다.

- [사용할 수 있는 레코드 잠금의 종류](#_core_record.2d.locking_modes)입니다.

- [업데이트 중에 레코드 집합의 레코드를 잠그는 방법](#_core_locking_records_in_your_recordset)

레코드 집합을 사용 하 여 데이터 원본에 대 한 레코드를 업데이트 하는 경우 다른 사용자가 동시에 레코드를 업데이트할 수 없도록 응용 프로그램에서 레코드를 잠글 수 있습니다. 시스템에서 두 사용자가 동시에 레코드를 업데이트할 수 없도록 하는 경우를 제외 하 고 두 사용자가 동시에 업데이트 한 레코드의 상태는 정의 되지 않습니다.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 구현한 경우 일부 정보가 적용 되지 않습니다. 예를 들어 `Edit` 및 멤버 함수를 호출할 수 없습니다 `Update` . 대량 행 페치에 대 한 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a> Record-Locking 모드

데이터베이스 클래스는 다음과 같은 두 개의 [레코드 잠금 모드](../../mfc/reference/crecordset-class.md#setlockingmode)를 제공 합니다.

- 낙관적 잠금 (기본값)

- 비관적 잠금

레코드 업데이트는 다음 세 단계로 수행 됩니다.

1. [Edit](../../mfc/reference/crecordset-class.md#edit) member 함수를 호출 하 여 작업을 시작 합니다.

1. 현재 레코드의 적절 한 필드를 변경 합니다.

1. [업데이트](../../mfc/reference/crecordset-class.md#update) 멤버 함수를 호출 하 여 작업을 종료 하 고 일반적으로 업데이트를 커밋합니다.

낙관적 잠금은 호출 하는 동안에만 데이터 원본에 대 한 레코드를 잠급니다 `Update` . 다중 사용자 환경에서 낙관적 잠금을 사용 하는 경우 응용 프로그램에서 오류 조건을 처리 해야 합니다 `Update` . 비관적 잠금은를 호출 하는 즉시 레코드를 잠그고를 `Edit` 호출할 때까지 해제 하지 않습니다 `Update` . 오류는 `CDBException` 에서 반환 된 FALSE 값이 아니라 메커니즘을 통해 표시 됩니다 `Update` . 비관적 잠금은 응용 프로그램의 프로세스가 완료 될 때까지 동일한 레코드에 대 한 동시 액세스를 기다려야 할 수 있으므로 다른 사용자에 대 한 성능 저하가 발생할 수 있습니다 `Update` .

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a> 레코드 집합에서 레코드 잠그기

레코드 집합 개체의 [잠금 모드](#_core_record.2d.locking_modes) 를 기본값에서 변경 하려면를 호출 하기 전에 모드를 변경 해야 합니다 `Edit` .

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>레코드 집합에 대 한 현재 잠금 모드를 변경 하려면

1. 또는 중 하나를 지정 하 여 [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) 멤버 함수를 호출 합니다 `CRecordset::pessimistic` `CRecordset::optimistic` .

새 잠금 모드는 다시 변경 하거나 레코드 집합을 닫을 때까지 적용 된 상태로 유지 됩니다.

> [!NOTE]
> 현재 일부 ODBC 드라이버는 비관적 잠금을 지원 합니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[레코드 집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
