---
description: '자세한 정보: 레코드 집합 (ODBC)'
title: 레코드 집합(ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: edbad5851db6f5ac9e1fddcc769c4f860ee5478e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204539"
---
# <a name="recordset-odbc"></a>레코드 집합(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

[CRecordset](../../mfc/reference/crecordset-class.md) 개체는 데이터 원본에서 선택한 레코드 세트를 나타냅니다. 레코드는 다음에서 제공될 수 있습니다.

- 테이블입니다.

- 쿼리.

- 하나 이상의 테이블에 액세스하는 저장 프로시저입니다.

테이블을 기반으로 하는 레코드 집합의 예는 Customer 테이블에 액세스하는 "모든 고객"입니다. 쿼리의 예는 "Joe Smith에 대한 모든 청구서"입니다. 저장 프로시저(미리 정의된 쿼리라고도 함)를 기반으로 하는 레코드 집합의 예는 백 엔드 데이터베이스에 저장 프로시저를 호출하는 "모든 연체 계정"입니다. 레코드 집합은 동일한 데이터 원본의 두 개 이상의 테이블을 조인할 수 있지만 다른 데이터 원본의 테이블은 조인하지 않습니다.

> [!NOTE]
> 일부 ODBC 드라이버는 데이터베이스 보기 지원합니다. 이러한 관점에서 보기는 원래 SQL `CREATE VIEW` 문으로 생성된 쿼리입니다.

## <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a> 레코드 집합 기능

모든 레코드 집합 개체는 다음 기능을 공유합니다.

- 데이터 원본이 읽기 전용이 아닌 경우 레코드 집합을 [업데이트 가능](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [추가 가능](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) 또는 읽기 전용으로 지정할 수 있습니다. 레코드 집합을 업데이트할 수 있는 경우 드라이버가 적절한 잠금 지원을 제공하면 비관적 또는 낙관적인 [잠금](../../data/odbc/recordset-locking-records-odbc.md) 메서드를 선택할 수 있습니다. 데이터 원본이 읽기 전용이면 레코드 세트도 읽기 전용이 됩니다.

- 선택한 레코드를 통해 [스크롤](../../data/odbc/recordset-scrolling-odbc.md)하도록 멤버 함수를 호출할 수 있습니다.

- 사용 가능한 레코드 중에서 선택한 레코드를 제한하도록 레코드를 [필터링](../../data/odbc/recordset-filtering-records-odbc.md)할 수 있습니다.

- 하나 이상의 열을 기준으로 오름차순 또는 내림차순으로 레코드를 [정렬](../../data/odbc/recordset-sorting-records-odbc.md)할 수 있습니다.

- 런타임 시 레코드 집합 선택을 한정하기 위해 레코드 집합을 [매개 변수화](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)할 수 있습니다.

## <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a> 스냅샷 및 다이너셋

레코드 집합에는 두 가지([스냅샷](../../data/odbc/snapshot.md) 및 [다이너셋](../../data/odbc/dynaset.md)) 주요 유형이 있습니다. 둘 다 클래스 `CRecordset`에서 지원됩니다. 각각은 모든 레코드 집합의 공통된 특성을 공유하지만, 각각은 고유의 전문화된 방법으로 공통 기능을 확장하기도 합니다. 스냅샷은 데이터의 정적 뷰를 제공하며 특정 시간에 존재했던 데이터를 보고자 하는 보고서 및 기타 상황에 유용합니다. 다이너셋은 레코드 집합을 다시 쿼리하거나 새로 고칠 필요 없이 다른 사용자가 만든 업데이트를 레코드 집합에 표시하려는 경우에 유용합니다. 스냅샷 및 다이너셋은 업데이트 가능이거나 읽기 전용일 수 있습니다. 다른 사용자가 추가 또는 삭제한 레코드를 반영하려면 [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery)를 호출합니다.

`CRecordset`은 동적 레코드 집합과 정방향 전용 집합의 두 가지 다른 유형의 레코드 집합도 허용합니다. 동적 레코드 집합은 다이너셋과 유사하지만 동적 레코드 집합은 `CRecordset::Requery`를 호출하지 않고 추가되거나 삭제된 모든 레코드를 반영합니다. 이러한 이유로 동적 레코드 집합은 일반적으로 DBMS의 처리 시간과 관련하여 비용이 많이 들고 많은 ODBC 드라이버가 이를 지원하지 않습니다. 반면, 정방향 전용 레코드 집합은 업데이트 또는 역방향 스크롤이 필요 없는 레코드 집합에 가장 효율적인 데이터 액세스 방법을 제공합니다. 예를 들어 정방향 전용 레코드 집합을 사용하여 데이터 원본 간에 데이터를 마이그레이션할 수 있습니다. 이 경우 전방 방향으로만 데이터를 이동하면 됩니다. 정방향 전용 레코드 집합을 사용하려면 다음 두 가지 작업을 수행해야 합니다.

- `CRecordset::forwardOnly` 옵션을 [열기](../../mfc/reference/crecordset-class.md#open) 멤버 함수의 *nOpenType* 매개 변수로 전달합니다.

- `Open`의 *dwOptions* 매개 변수에 `CRecordset::readOnly`를 지정합니다.

    > [!NOTE]
    >  다이너셋 지원에 대한 ODBC 드라이버 요구 사항에 대한 자세한 내용은 [ODBC](../../data/odbc/odbc-basics.md)를 참조하세요. 이 버전의 Visual C++에 포함된 ODBC 드라이버 목록과 추가 드라이버를 가져오는 방법에 대한 자세한 내용은 [ODBC 드라이버 목록](../../data/odbc/odbc-driver-list.md)을 참조하세요.

## <a name="your-recordsets"></a><a name="_core_your_recordsets"></a> 레코드 집합

액세스하려는 모든 개별 테이블, 보기 또는 저장 프로시저에 대해 일반적으로 `CRecordset`에서 파생된 클래스를 정의합니다. 단, 한 레코드 집합은 둘 이상의 테이블에서 열을 나타내는 데이터베이스 조인입니다. 레코드 집합 클래스를 파생 시킬 때는 DDX (대화 상자 데이터 교환) 메커니즘과 유사한 RFX (레코드 필드 교환) 메커니즘 또는 대량 RFX (대량 레코드 필드 교환) 메커니즘을 사용 하도록 설정 합니다. RFX 및 Bulk RFX는 데이터 원본에서 레코드 집합으로 데이터를 간단하게 전송합니다. 또한 RFX는 레코드 집합에서 데이터 원본으로 데이터를 추가로 전송합니다. 자세한 내용은 [RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md) 및 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

레코드 집합 개체를 사용하면 선택한 모든 레코드에 액세스할 수 있습니다. `CRecordset` 멤버 함수(예: `MoveNext` 및 `MovePrev`)를 사용하여 선택한 여러 레코드를 스크롤합니다. 동시에, 레코드 집합 개체는 선택한 레코드 중 하나의 현재 레코드만 나타냅니다. 테이블의 열 또는 데이터베이스 쿼리에서 발생하는 레코드에 해당하는 레코드 집합 클래스 멤버 변수를 선언하여 현재 레코드의 필드를 검사할 수 있습니다. 레코드 집합 데이터 멤버에 대 한 자세한 내용은 [레코드 집합: 아키텍처 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)를 참조 하세요.

다음 항목에서는 레코드 집합 개체 사용에 대한 세부 정보를 설명합니다. 이 항목은 기능 범주 및 순차적 읽기를 허용하는 자연스러운 탐색 순서로 나열되어 있습니다.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>레코드 열기, 읽기 및 닫기의 메커니즘에 대한 항목

- [레코드 집합: 아키텍처 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [레코드 집합: 레코드 집합 만들기 및 닫기 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [레코드 집합: 스크롤(ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [레코드 집합: 책갈피 및 절대 위치 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [레코드 집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [레코드 집합: 레코드 정렬 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>레코드 집합 수정 메커니즘에 대한 항목

- [레코드 집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [레코드 집합: 레코드 잠금 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [레코드 집합: 레코드 집합 다시 쿼리 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>약간 더 고급 기술에 대한 항목

- [레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [레코드 집합: 미리 정의 된 쿼리에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [레코드 집합: 대량 데이터 항목 작업 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [레코드 집합: 합계 및 다른 집계 결과 구하기 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>레코드 집합의 작동 방법에 대한 항목

- [레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC 사용](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[트랜잭션(ODBC)](../../data/odbc/transaction-odbc.md)
