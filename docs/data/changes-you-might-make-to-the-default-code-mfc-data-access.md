---
title: 기본 코드 (MFC Data Access)를 수행할 수 있는 변경 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cee9316e2bd526465b6eed735df0bb0c6d5d6593
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072995"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>기본 코드에 수행할 수 있는 변경  (MFC Data Access)

합니다 [MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 단일 테이블의 모든 레코드를 선택 하는 레코드 집합 클래스를 씁니다. 다음 방식 중 하나 이상을 사용하여 해당 동작을 수정하는 경우가 많습니다.

- 레코드 집합에 대해 필터 또는 정렬 순서를 설정합니다. 이 작업을 수행할 `OnInitialUpdate` 레코드 집합 개체 전에 생성 된 후 해당 `Open` 멤버 함수를 호출 합니다. 자세한 내용은 [레코드 집합: 레코드 필터링 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) 하 고 [레코드 집합: 레코드 정렬 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)합니다.

- 레코드 집합을 매개 변수화합니다. 이 경우 필터 후의 실제 런타임 매개 변수 값을 지정합니다. 자세한 내용은 참조 하세요. [레코드 집합: 레코드 집합 (ODBC)를 매개 변수화](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- 사용자 지정 된 SQL 문자열을 전달 하는 [열고](../mfc/reference/crecordset-class.md#open) 멤버 함수입니다. 이 기술을 사용 하 여 수행할 수 있는 작업의 자세한 내용은 참조 하세요. [SQL: 사용자 지정 레코드 집합의 SQL 문 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)합니다.

## <a name="see-also"></a>참고 항목

[레코드 뷰 사용](../data/using-a-record-view-mfc-data-access.md)