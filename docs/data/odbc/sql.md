---
description: '자세한 내용: SQL'
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 01a559b959d0f9a8c37f13a79855d55c5890f20e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333915"
---
# <a name="sql"></a>SQL

SQL(구조적 쿼리 언어)은 데이터를 정의, 쿼리, 수정 및 제어할 수 있는 관계형 데이터베이스와 통신하는 방법입니다. SQL 구문을 사용하면 지정한 기준에 따라 레코드를 추출하는 명령문을 구성할 수 있습니다.

> [!NOTE]
> 이 정보는 MFC ODBC 클래스에 적용됩니다. MFC DAO 클래스를 사용하여 작업하는 경우 DAO 도움말의 Microsoft Jet Database Engine SQL과 ANSI SQL 비교 항목을 참조하세요.

SQL 문은 **CREATE** 또는 **SELECT** 와 같은 키워드 동사로 시작합니다. SQL은 매우 강력한 언어입니다. 단일 명령문이 전체 테이블에 영향을 줄 수 있습니다.

여러 버전의 SQL이 있으며 각각은 특정 DBMS를 염두에 두고 개발되었습니다. MFC 데이터베이스 클래스는 X/Open 및 SQL Access Group CAE(공통 애플리케이션 환경) SQL 초안 사양(1991)에 해당하는 SQL 문 세트를 인식합니다. 이러한 문의 구문에 대 한 자세한 내용은 [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference) 설명서의 부록 C를 참조 하십시오.

이 토픽에서는 다음 내용을 설명합니다.

- [ODBC와 SQL 간의 관계](#_core_open_database_connectivity_.28.odbc.29).

- [데이터베이스 클래스에서 사용되는 가장 일반적인 SQL 키워드](#_core_the_database_classes).

- [데이터베이스 클래스에서 SQL을 사용 하는 방법](#_core_how_the_database_classes_use_sql)

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a> ODBC (Open Database Connectivity)

데이터베이스 클래스는 ODBC에서 구현되며 코드에 SQL 명령을 포함하는 대신 호출 수준 인터페이스에서 SQL을 사용합니다. ODBC는 SQL을 사용하여 ODBC 드라이버를 통해 [데이터 원본](../../data/odbc/data-source-odbc.md)과 통신합니다. 이러한 드라이버는 SQL을 해석하고 필요한 경우 Microsoft Access와 같은 특정 데이터베이스 형식으로 사용하기 위해 변환합니다. ODBC에서 SQL을 사용 하는 방법에 대 한 자세한 내용은 [odbc](../../data/odbc/odbc-basics.md) 및 [odbc 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference) 설명서를 참조 하십시오.

## <a name="database-classes"></a><a name="_core_the_database_classes"></a> 데이터베이스 클래스

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

데이터베이스 클래스는 기존 [데이터 원본](../../data/odbc/data-source-odbc.md)의 데이터를 조작하고 업데이트할 수 있도록 설계되었습니다. [MFC 애플리케이션 마법사](../../mfc/reference/database-support-mfc-application-wizard.md), [MFC ODBC 소비자 마법사](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(**클래스 추가** 를 통해 액세스됨) 및 데이터베이스 클래스가 대부분의 SQL 문을 구성합니다.

데이터베이스 클래스는 DML(데이터 조작 언어)로 알려진 SQL 부분을 사용합니다. 이러한 명령을 사용하면 데이터 원본의 전체 또는 일부를 작업하고, 새 레코드를 추가하고, 레코드를 편집하고, 레코드를 삭제할 수 있습니다. 다음 표에는 가장 일반적인 SQL 키워드 및 데이터베이스 클래스에서 사용하는 방법이 나열되어 있습니다.

### <a name="some-common-sql-keywords"></a>몇 가지 공통 SQL 키워드

|SQL 키워드|마법사 및 데이터베이스 클래스에서 사용|
|-----------------|---------------------------------------------|
|**SELECT**|데이터 원본에서 사용할 테이블 및 열을 식별하는 방법.|
|**WHERE**|선택 항목을 좁히는 필터를 적용하는 방법.|
|**ORDER BY**|레코드 집합에 정렬 순서를 적용하는 방법.|
|**INSERT**|레코드 집합에 새 레코드를 추가하는 방법.|
|**DELETE**|레코드 집합에서 레코드를 삭제하는 방법.|
|**UPDATE**|레코드의 필드를 수정하는 방법.|

또한 데이터베이스 클래스는 일부 데이터 원본에서 미리 정의된 쿼리(또는 저장 프로시저)를 호출하는 데 사용할 수 있는 ODBC **CALL** 문을 인식합니다. ODBC 데이터베이스 드라이버는 이러한 명령문을 해석하고 각 DBMS에 적절한 명령을 대체합니다.

> [!NOTE]
> 모든 DBMS가 **CALL** 문을 지원하는 것은 아닙니다.

클래스가 `CRecordset::Open`에서 사용자 제공 명령문을 인식할 수 없는 경우 테이블 이름으로 해석됩니다.

프레임 워크에서 SQL 문을 생성 하는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 선택 방법 (odbc)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 및 [Sql: 레코드 집합의 Sql 문 사용자 지정 (odbc)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하십시오.

SQL 데이터베이스는 C 및 C++에서 사용되는 것과 유사한 데이터 형식을 사용합니다. 이러한 유사성에 대 한 설명은 [sql: sql 및 c + + 데이터 형식 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)을 참조 하세요.

Sql에 대 한 자세한 내용은 [MICROSOFT sql](/sql/) 설명서에서 지원 되는 sql 문, 데이터 형식, sql core 문법 및 sql에 대 한 권장 되는 게시 목록을 포함 하 여 확인할 수 있습니다.

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> 데이터베이스 클래스가 SQL을 사용하는 방법

데이터베이스 클래스에서 파생된 레코드 집합은 ODBC를 사용하여 데이터 원본과 통신하고 ODBC는 SQL 문을 전송하여 데이터 원본에서 레코드를 검색합니다. 이 항목에서는 데이터베이스 클래스와 SQL 간의 관계를 설명합니다.

레코드 집합은 SQL 문의 여러 부분을 `CString`으로 빌드하여 SQL 문을 구성합니다. 문자열은 레코드 세트를 반환하는 **SELECT** 문으로 구성됩니다.

레코드 집합이 ODBC를 호출하여 SQL 문을 데이터 원본으로 보내면 ODBC 드라이버 관리자는 명령문을 ODBC 드라이버에 전달하고 드라이버는 이를 기본 DBMS에 보냅니다. DBMS는 레코드의 결과 집합을 반환하고 ODBC 드라이버는 레코드를 애플리케이션에 반환합니다. 데이터베이스 클래스를 통해 프로그램이 `CRecordset`에서 파생된 형식이 안전한 C++ 클래스의 결과 집합에 액세스할 수 있습니다.

다음 항목에서는 데이터베이스 클래스에서 SQL을 사용하는 방법에 대한 자세한 정보를 제공합니다.

- [SQL: 레코드 집합의 SQL 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: SQL 및 c + + 데이터 형식 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: SQL 직접 호출 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC 기본 사항](../../data/odbc/odbc-basics.md)
