---
description: 'Odbc: ODBC API 함수 직접 호출에 대해 자세히 알아보세요.'
title: 'ODBC: ODBC API 함수 직접 호출'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: 3b82e0270242d59767e9d67e6eb7491a4607990f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161119"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: ODBC API 함수 직접 호출

데이터베이스 클래스는 ODBC와는 다른 [데이터 원본](../../data/odbc/data-source-odbc.md) 에 대 한 간단한 인터페이스를 제공 합니다. 따라서 클래스는 모든 ODBC API를 캡슐화 하지 않습니다. 클래스의 기능을 벗어나는 기능의 경우 ODBC API 함수를 직접 호출 해야 합니다. 예를 들어 ODBC 카탈로그 함수 ( `::SQLColumns` ,, `::SQLProcedures` `::SQLTables` 및 기타)를 직접 호출 해야 합니다.

> [!NOTE]
> ODBC 데이터 원본은이 항목에서 설명 하는 MFC ODBC 클래스 또는 MFC DAO (Data Access Object) 클래스를 통해 액세스할 수 있습니다.

ODBC API 함수를 직접 호출 하려면 프레임 워크 없이 호출을 수행 하는 경우와 동일한 단계를 수행 해야 합니다. 이러한 단계는 다음과 같습니다.

- 호출에서 반환 하는 결과에 대해 저장소를 할당 합니다.

- `HDBC` `HSTMT` 함수의 매개 변수 시그니처에 따라 ODBC 또는 핸들을 전달 합니다. [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) 매크로를 사용 하 여 ODBC 핸들을 검색 합니다.

   멤버 변수 `CDatabase::m_hdbc` 및를 `CRecordset::m_hstmt` 사용할 수 있으므로 사용자가 직접 할당 하 고 초기화할 필요가 없습니다.

- 예를 들어 추가 ODBC 함수를 호출 하 여 기본 호출을 준비 하거나 후속 작업을 수행할 수 있습니다.

- 완료 되 면 저장소 할당을 취소 합니다.

이러한 단계에 대 한 자세한 내용은 [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference)를 참조 하세요.

이러한 단계 외에도 함수 반환 값을 확인 하 고 프로그램에서 비동기 호출이 완료 될 때까지 기다리지 않도록 추가 단계를 수행 해야 합니다. AFX_SQL_ASYNC 및 AFX_SQL_SYNC 매크로를 사용 하 여 이러한 마지막 단계를 단순화할 수 있습니다. 자세한 내용은 [MFC 매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ODBC 기본 사항](../../data/odbc/odbc-basics.md)
