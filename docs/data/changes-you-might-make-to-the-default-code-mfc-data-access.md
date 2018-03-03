---
title: "기본 코드 (데이터 액세스)에 대해 수행할 수 있는 변경 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 197277a68131c9d63e3eab2f1404cf97169be1f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>기본 코드에 수행할 수 있는 변경  (MFC Data Access)
[MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 단일 테이블의 모든 레코드를 선택 하는 레코드 집합 클래스를 작성 합니다. 다음 방식 중 하나 이상을 사용하여 해당 동작을 수정하는 경우가 많습니다.  
  
-   레코드 집합에 대해 필터 또는 정렬 순서를 설정합니다. 이 작업을 수행할 `OnInitialUpdate` recordset 개체 하기 전에 생성 된 후 해당 **열려** 멤버 함수를 호출 합니다. 자세한 내용은 참조 [레코드 집합: 레코드 필터링 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) 및 [레코드 집합: 레코드 정렬 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)합니다.  
  
-   레코드 집합을 매개 변수화합니다. 이 경우 필터 후의 실제 런타임 매개 변수 값을 지정합니다. 자세한 내용은 참조 [레코드 집합: 레코드 집합 (ODBC)를 매개 변수화](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   사용자 지정 된 SQL 문자열을 전달는 [열려](../mfc/reference/crecordset-class.md#open) 멤버 함수입니다. 이 기술을 사용 하 여 수행할 수 있는 작업의 논의 알려면 [SQL: 사용자 지정 레코드 집합의 SQL 문 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레코드 뷰 사용](../data/using-a-record-view-mfc-data-access.md)