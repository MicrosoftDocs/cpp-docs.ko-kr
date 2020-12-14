---
description: '자세한 정보: 다이너셋'
title: 다이너셋
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 3c4a8edf1d0058045affc436bb8c9ee1c7e8bf4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239677"
---
# <a name="dynaset"></a>다이너셋

이 항목에서는 다이너셋을 설명 하 고 [가용성](#_core_availability_of_dynasets)에 대해 설명 합니다.

> [!NOTE]
> 이 항목은 [CRecordset](../../mfc/reference/crecordset-class.md)를 비롯 한 MFC ODBC 클래스에 적용 됩니다. DAO 클래스의 다이너셋에 대 한 자세한 내용은 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)를 참조 하세요. DAO를 사용 하면 다이너셋 형식의 레코드 집합을 열 수 있습니다.

다이너셋은 동적 속성을 포함 하는 레코드 집합입니다. 수명이 지속 되는 동안 다이너셋 모드의 레코드 집합 개체 (일반적으로 다이너셋 이라고 함)는 다음과 같은 방식으로 데이터 소스와 동기화 된 상태를 유지 합니다. 다중 사용자 환경에서 다른 사용자는 다이너셋에 있는 레코드를 편집 또는 삭제 하거나 다이너셋이 나타내는 테이블에 레코드를 추가할 수 있습니다. 응용 프로그램이 레코드 집합에서 추가 하거나 삭제 하는 레코드는 다이너셋에 반영 됩니다. 다른 사용자가 테이블에 추가 하는 레코드는 해당 멤버 함수를 호출 하 여 다이너셋을 다시 작성할 때까지 다이너셋에 반영 되지 않습니다 `Requery` . 다른 사용자가 레코드를 삭제 하면 MFC 코드는 레코드 집합에서 삭제를 건너뜁니다. 기존 레코드에 대 한 다른 사용자의 편집 변경 내용은 영향을 받는 레코드로 스크롤하면 곧바로 다이너셋에 반영 됩니다.

마찬가지로, 다이너셋에서 레코드를 편집 하는 작업은 다른 사용자가 사용 하는 다이너셋에 반영 됩니다. 추가 하는 레코드는 다이너셋을 다시 쿼리할 때까지 다른 사용자의 다이너셋을 반영 되지 않습니다. 삭제 한 레코드는 다른 사용자의 레코드 집합에서 "삭제 됨"으로 표시 됩니다. 동일한 데이터베이스 (여러 개체)에 대 한 연결이 여러 개 있는 경우 `CDatabase` 해당 연결과 관련 된 레코드 집합은 다른 사용자의 레코드 집합과 같은 상태를 갖습니다.

다이너셋은 항공 예약 시스템에서 데이터를 동적 (예:)으로 만들어야 하는 경우에 가장 유용 합니다.

> [!NOTE]
> 다이너셋을 사용 하려면 다이너셋을 지 원하는 데이터 원본에 대 한 ODBC 드라이버가 있어야 하며 ODBC 커서 라이브러리를 로드 하지 않아야 합니다. 자세한 내용은 [다이너셋을 사용 가능](#_core_availability_of_dynasets)을 참조 하세요.

레코드 집합이 다이너셋 임을 지정 하려면 `CRecordset::dynaset` `Open` 레코드 집합 개체의 멤버 함수에 대 한 첫 번째 매개 변수로를 전달 합니다.

> [!NOTE]
> 업데이트할 수 있는 다이너셋은 ODBC 드라이버는 위치 지정 update 문 또는 odbc API 함수를 지원 해야 합니다 `::SQLSetPos` . 둘 다 지원 되는 경우 MFC는 `::SQLSetPos` 효율성을 위해를 사용 합니다.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a> 다이너셋은 사용 가능

MFC 데이터베이스 클래스는 다음 요구 사항이 충족 되는 경우 다이너셋을 지원 합니다.

- ODBC 커서 라이브러리 DLL은이 데이터 원본에 사용 되 고 있지 않아야 합니다.

   커서 라이브러리를 사용 하는 경우에는 다이너셋 지원에 필요한 기본 ODBC 드라이버의 일부 기능을 마스크 합니다. 이 단원의 나머지 부분에 설명 된 대로 다이너셋을 사용 하려는 경우 ODBC 드라이버에 다이너셋에 필요한 기능이 있는 경우 개체를 만들 때 MFC가 커서 라이브러리를 로드 하지 않도록 할 수 있습니다 `CDatabase` . 자세한 내용은 [ODBC](../../data/odbc/odbc-basics.md) 및 클래스의 [microsoft.office.interop.visio.documents.openex](../../mfc/reference/cdatabase-class.md#openex) 또는 [Open](../../mfc/reference/cdatabase-class.md#open) 멤버 함수를 참조 하세요 `CDatabase` .

   ODBC 용어로 다이너셋과 스냅숏은 커서 라고 합니다. 커서는 레코드 집합에서의 위치를 추적 하는 데 사용 되는 메커니즘입니다.

- 데이터 원본에 대 한 ODBC 드라이버는 키 집합 커서를 지원 해야 합니다.

   키 집합 커서는 키 집합을 가져오고 저장 하 여 테이블의 데이터를 관리 합니다. 키는 사용자가 특정 레코드로 스크롤할 때 테이블에서 현재 데이터를 가져오는 데 사용 됩니다. 드라이버가이 지원을 제공 하는지 확인 하려면 `::SQLGetInfo` *SQL_SCROLL_OPTIONS* 매개 변수를 사용 하 여 ODBC API 함수를 호출 합니다.

   키 집합을 지원 하지 않고 다이너셋을 열려고 하면 `CDBException` AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED 반환 코드 값이 포함 된이 반환 됩니다.

- 데이터 원본에 대 한 ODBC 드라이버는 확장 페치를 지원 해야 합니다.

   확장 페치는 SQL 쿼리의 결과 레코드를 앞뒤로 스크롤할 수 있는 기능입니다. 드라이버가이 기능을 지원 하는지 확인 하려면 `::SQLGetFunctions` *SQL_API_SQLEXTENDEDFETCH* 매개 변수를 사용 하 여 ODBC API 함수를 호출 합니다.

업데이트 가능한 다이너셋 (또는 스냅숏)을 원하는 경우 ODBC 드라이버는 `::SQLSetPos` ODBC API 함수 또는 위치 지정 업데이트도 지원 해야 합니다. `::SQLSetPos`함수를 사용 하면 MFC에서 SQL 문을 전송 하지 않고 데이터 원본을 업데이트할 수 있습니다. 이 지원을 사용할 수 있는 경우 MFC는 기본 설정에 따라 SQL을 사용 하 여 업데이트를 수행 합니다. 드라이버가를 지원 하는지 확인 하려면 `::SQLSetPos` `::SQLGetInfo` *SQL_POS_OPERATIONS* 매개 변수를 사용 하 여를 호출 합니다.

위치 지정 업데이트는 SQL 구문 ( **의 현재 위치** \<cursorname> )을 사용 하 여 데이터 원본에 있는 테이블의 특정 행을 식별 합니다. 드라이버가 배치 된 업데이트를 지원 하는지 확인 하려면 `::SQLGetInfo` *SQL_POSITIONED_STATEMENTS* 매개 변수를 사용 하 여를 호출 합니다.

일반적으로 MFC 다이너셋 (전방 전용 레코드 집합 아님)에는 수준 2 API 규칙을 사용 하는 ODBC 드라이버가 필요 합니다. 데이터 원본에 대 한 드라이버가 수준 1 API 집합을 따르는 경우에도 업데이트 가능 하 고 읽기 전용 스냅숏과 전방 전용 레코드 집합을 모두 사용할 수 있지만 다이너셋은 사용할 수 없습니다. 그러나 확장 된 가져오기 및 키 집합 커서를 지 원하는 경우에는 수준 1 드라이버가 다이너셋을 지원할 수 있습니다. ODBC 규칙 수준에 대 한 자세한 내용은 [odbc](../../data/odbc/odbc-basics.md)를 참조 하십시오.

> [!NOTE]
> 스냅숏과 다이너셋을 모두 사용 하려면 서로 다른 두 개의 `CDatabase` 개체 (두 개의 다른 연결)에 기반 해야 합니다.

ODBC 커서 라이브러리에 의해 유지 관리 되는 중간 저장소를 사용 하는 스냅숏과 달리 다이너셋은 스크롤하면 데이터 원본에서 직접 레코드를 가져옵니다. 그러면 다이너셋에서 원래 선택한 레코드를 데이터 원본과 동기화 된 상태로 유지 합니다.

이 버전의 Visual C++에 포함된 ODBC 드라이버 목록과 추가 드라이버를 가져오는 방법에 대한 자세한 내용은 [ODBC 드라이버 목록](../../data/odbc/odbc-driver-list.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)
