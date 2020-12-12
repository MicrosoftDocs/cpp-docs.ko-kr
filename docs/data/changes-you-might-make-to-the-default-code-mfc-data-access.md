---
description: '자세한 정보: 기본 코드에 수행할 수 있는 변경 내용 (MFC Data Access)'
title: 기본 코드에 수행할 수 있는 변경  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 431144eeaf7ef0a2413e4d9e3931016c2505d338
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181451"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>기본 코드에 수행할 수 있는 변경  (MFC Data Access)

[MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 는 단일 테이블의 모든 레코드를 선택 하는 레코드 집합 클래스를 작성 합니다. 다음 방식 중 하나 이상을 사용하여 해당 동작을 수정하는 경우가 많습니다.

- 레코드 집합에 대해 필터 또는 정렬 순서를 설정합니다. `OnInitialUpdate`레코드 집합 개체가 생성 된 후 멤버 함수가 호출 되기 전에에서이 작업을 수행 `Open` 합니다. 자세한 내용은 레코드 [집합: 레코드 필터링 (odbc)](../data/odbc/recordset-filtering-records-odbc.md) 및 레코드 [집합: 레코드 정렬 (odbc)](../data/odbc/recordset-sorting-records-odbc.md)을 참조 하세요.

- 레코드 집합을 매개 변수화합니다. 이 경우 필터 후의 실제 런타임 매개 변수 값을 지정합니다. 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 를 참조 하세요.

- 사용자 지정 된 SQL 문자열을 [Open](../mfc/reference/crecordset-class.md#open) 멤버 함수에 전달 합니다. 이 기법을 사용 하 여 수행할 수 있는 작업에 대 한 자세한 내용은 [sql: 레코드 집합의 Sql 문 사용자 지정 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 뷰 사용](../data/using-a-record-view-mfc-data-access.md)
