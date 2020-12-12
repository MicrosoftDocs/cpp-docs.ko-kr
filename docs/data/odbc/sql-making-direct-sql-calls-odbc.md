---
description: '자세한 정보: SQL: sql 직접 호출 만들기 (ODBC)'
title: 'SQL: SQL 직접 호출(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 1cf7f20bf7de777f418c289f06878fa9ae448c12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124516"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: SQL 직접 호출(ODBC)

이 토픽에서는 다음 내용을 설명합니다.

- 직접 SQL 호출을 사용 하는 경우

- [데이터 원본에 대 한 직접 SQL 호출을 만드는 방법](#_core_making_direct_sql_function_calls)

> [!NOTE]
> 이 정보는 MFC ODBC 클래스에 적용됩니다. MFC DAO 클래스를 사용 하는 경우 DAO 도움말의 "Microsoft Jet 데이터베이스 엔진 SQL 및 ANSI SQL의 비교" 항목을 참조 하십시오.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a> SQL을 직접 호출 하는 경우

새 테이블을 만들고, 테이블을 삭제 하 고, 기존 테이블을 변경 하 고, 인덱스를 만들고, [데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md) 스키마를 변경 하는 다른 sql 함수를 수행 하려면 DDL (데이터베이스 정의 언어)을 사용 하 여 데이터 원본에 대 한 sql 문을 직접 실행 해야 합니다. 디자인 타임에 마법사를 사용 하 여 테이블에 대 한 레코드 집합을 만드는 경우 레코드 집합에 표시할 테이블의 열을 선택할 수 있습니다. 이렇게 하면 프로그램을 컴파일한 후 사용자 또는 데이터 원본의 다른 사용자가 나중에 테이블에 추가 하는 열을 사용할 수 없습니다. 데이터베이스 클래스는 DDL을 직접 지원 하지 않지만 런타임에 새 열을 레코드 집합에 동적으로 바인딩하는 코드를 작성할 수 있습니다. 이 바인딩을 수행 하는 방법에 대 한 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.

DBMS 자체를 사용 하 여 스키마를 변경 하거나 DDL 기능을 수행할 수 있는 다른 도구를 사용할 수 있습니다. 또한 레코드를 반환 하지 않는 미리 정의 된 쿼리 (저장 프로시저)를 호출 하는 등의 방법으로 ODBC 함수 호출을 사용 하 여 SQL 문을 보낼 수 있습니다.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a> 직접 SQL 함수 호출 만들기

[CDatabase 클래스](../../mfc/reference/cdatabase-class.md) 개체를 사용 하 여 SQL 호출을 직접 실행할 수 있습니다. SQL 문 문자열 (일반적으로)을 설정 `CString` 하 고 개체의 [CDatabase:: executesql](../../mfc/reference/cdatabase-class.md#executesql) 멤버 함수로 전달 `CDatabase` 합니다. ODBC 함수 호출을 사용 하 여 일반적으로 레코드를 반환 하는 SQL 문을 보내는 경우 해당 레코드는 무시 됩니다.

## <a name="see-also"></a>참고 항목

[SQL](../../data/odbc/sql.md)
