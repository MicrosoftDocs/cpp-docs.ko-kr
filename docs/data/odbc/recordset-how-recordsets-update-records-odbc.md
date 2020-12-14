---
description: '자세한 정보: 레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)'
title: '레코드 집합: 레코드 집합의 레코드 업데이트 방법(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: c5304bd30093a203efbd9ee4d02d07b2d35b4b18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304508"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>레코드 집합: 레코드 집합의 레코드 업데이트 방법(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

데이터 원본에서 레코드를 선택 하는 것 외에도, 레코드 집합은 선택한 레코드를 업데이트 또는 삭제 하거나 새 레코드를 추가할 수 있습니다 (옵션). 세 가지 요소는 레코드 집합의 업데이트를 결정 합니다. 즉, 연결 된 데이터 원본을 업데이트할 수 있는지 여부, 레코드 집합 개체를 만들 때 지정 하는 옵션 및 생성 되는 SQL을 결정 합니다.

> [!NOTE]
> 개체가 기반으로 하는 SQL은 `CRecordset` 레코드 집합의 업데이트 프로그램에 영향을 줄 수 있습니다. 예를 들어 SQL에 join 또는 **GROUP by** 절이 포함 된 경우 MFC는 업데이트 프로그램을 FALSE로 설정 합니다.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 사용 하는 경우 레코드 [집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

이 토픽에서는 다음 내용을 설명합니다.

- [레코드 집합을 업데이트](#_core_your_role_in_recordset_updating) 하는 사용자의 역할과 프레임 워크의 역할입니다.

- [레코드 집합을 편집 버퍼로](#_core_the_edit_buffer) , [다이너셋과 스냅숏의 차이점](#_core_dynasets_and_snapshots)입니다.

[레코드 집합: AddNew, Edit 및 Delete 작업 방법 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) 은 레코드 집합의 관점에서 이러한 함수의 동작을 설명 합니다.

[레코드 집합: 업데이트에 대 한 추가 정보 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) 는 트랜잭션이 업데이트에 미치는 영향, 레코드 집합 또는 스크롤을 닫는 업데이트에 미치는 영향, 업데이트가 다른 사용자의 업데이트와 상호 작용 하는 방법에 대해 설명 하 여 레코드 집합 업데이트 스토리를 완료 합니다.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a> 레코드 집합을 업데이트 하는 사용자의 역할

다음 표에서는 프레임 워크에서 사용 하는 것과 함께 레코드 집합을 사용 하 여 레코드를 추가, 편집 또는 삭제 하는 역할을 보여 줍니다.

### <a name="recordset-updating-you-and-the-framework"></a>레코드 집합 업데이트: 사용자 및 프레임 워크

|사용자|프레임워크|
|---------|-------------------|
|데이터 원본을 업데이트할 수 있는지 여부를 확인 합니다 (또는 appendable).|는 데이터 원본의 업데이트 기능 또는 appendability 기능을 테스트 하기 위한 [CDatabase](../../mfc/reference/cdatabase-class.md) 멤버 함수를 제공 합니다.|
|모든 형식의 업데이트 가능한 레코드 집합을 엽니다.||
|`CRecordset`또는와 같은 업데이트 함수를 호출 하 여 레코드 집합을 업데이트할 수 있는지 여부를 확인 합니다 `CanUpdate` `CanAppend` .||
|레코드 집합 멤버 함수를 호출 하 여 레코드를 추가, 편집 및 삭제 합니다.|레코드 집합 개체와 데이터 원본 간에 데이터를 교환 하는 메커니즘을 관리 합니다.|
|필요에 따라 트랜잭션을 사용 하 여 업데이트 프로세스를 제어 합니다.|는 `CDatabase` 트랜잭션을 지 원하는 멤버 함수를 제공 합니다.|

트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)을 참조 하십시오.

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a> 편집 버퍼

데이터 집합의 필드 데이터 멤버는 단일 레코드 (현재 레코드)를 포함 하는 편집 버퍼 역할을 합니다. 업데이트 작업에서는이 버퍼를 사용 하 여 현재 레코드에 대해 작업을 수행 합니다.

- 레코드를 추가 하는 경우 편집 버퍼를 사용 하 여 새 레코드를 작성 합니다. 레코드를 추가 하는 작업이 완료 되 면 이전에는 현재 레코드가 다시 최신 상태가 됩니다.

- 레코드를 업데이트 (편집) 할 때 편집 버퍼는 레코드 집합의 필드 데이터 멤버를 새 값으로 설정 하는 데 사용 됩니다. 업데이트를 마치면 업데이트 된 레코드가 아직 최신 상태입니다.

[AddNew](../../mfc/reference/crecordset-class.md#addnew) 또는 [Edit](../../mfc/reference/crecordset-class.md#edit)를 호출 하면 나중에 필요할 때 복원할 수 있도록 현재 레코드가 저장 됩니다. [Delete](../../mfc/reference/crecordset-class.md#delete)를 호출 하면 현재 레코드는 저장 되지 않지만 삭제 된 것으로 표시 되 고 다른 레코드로 스크롤해야 합니다.

> [!NOTE]
> 편집 버퍼는 레코드 삭제 시 역할을 수행 하지 않습니다. 현재 레코드를 삭제 하면 해당 레코드는 삭제 된 것으로 표시 되 고 다른 레코드로 스크롤할 때까지 레코드 집합은 "레코드에 없음"이 됩니다.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a> 다이너셋 및 스냅숏

[다이너셋은](../../data/odbc/dynaset.md) 레코드로 스크롤하면 레코드의 콘텐츠를 새로 고칩니다. [스냅숏은](../../data/odbc/snapshot.md) 레코드를 정적으로 표현한 것 이므로 [Requery](../../mfc/reference/crecordset-class.md#requery)를 호출 하지 않으면 레코드의 내용이 새로 고쳐지지 않습니다. 다이너셋은 모든 기능을 사용 하려면 odbc API 지원의 올바른 수준을 준수 하는 ODBC 드라이버를 사용 해야 합니다. 자세한 내용은 [ODBC](../../data/odbc/odbc-basics.md) 및 [다이너셋](../../data/odbc/dynaset.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: AddNew, Edit 및 Delete 작업 방법 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
