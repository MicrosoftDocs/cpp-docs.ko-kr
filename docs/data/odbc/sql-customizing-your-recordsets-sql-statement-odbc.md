---
description: '자세한 정보: SQL: 레코드 집합의 SQL 문 사용자 지정 (ODBC)'
title: 'SQL: 레코드 집합의 SQL 문 사용자 지정(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: 73765ed66dacbc017cca6236ae5a90388390fa45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278690"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: 레코드 집합의 SQL 문 사용자 지정(ODBC)

이 토픽에서는 다음 내용을 설명합니다.

- 프레임 워크가 SQL 문을 생성 하는 방법

- SQL 문을 재정의 하는 방법

> [!NOTE]
> 이 정보는 MFC ODBC 클래스에 적용됩니다. MFC DAO 클래스를 사용 하는 경우 DAO 도움말의 "Microsoft Jet 데이터베이스 엔진 SQL 및 ANSI SQL의 비교" 항목을 참조 하십시오.

## <a name="sql-statement-construction"></a>SQL 문 생성

레코드 집합은 주로 SQL **SELECT** 문에서 레코드 선택 항목을 기반으로 합니다. 마법사를 사용 하 여 클래스를 선언 하면이 클래스는 `GetDefaultSQL` 호출 된 레코드 집합 클래스에 대해 다음과 같은 멤버 함수의 재정의 버전을 작성 `CAuthors` 합니다.

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

기본적으로이 재정의는 마법사에서 지정한 테이블 이름을 반환 합니다. 이 예에서 테이블 이름은 "AUTHORS"입니다. 나중에 레코드 집합의 멤버 함수를 호출 하는 경우는 `Open` `Open` 폼의 최종 **SELECT** 문을 생성 합니다.

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

여기서 `table-name` 는를 호출 하 여 가져오고 `GetDefaultSQL` `rfx-field-list` 의 RFX 함수 호출에서 가져옵니다 `DoFieldExchange` . 이는 매개 변수 또는 필터를 사용 하 여 기본 문을 수정할 수도 있지만 런타임 시 재정의 버전으로 대체 하지 않는 한 **SELECT** 문에 대해 얻을 수 있습니다.

> [!NOTE]
> 공백을 포함 하거나 포함할 수 있는 열 이름을 지정 하는 경우 이름을 대괄호로 묶어야 합니다. 예를 들어 이름 "First name"은 "[First Name]" 이어야 합니다.

기본 **select** 문을 재정의 하려면를 호출할 때 전체 **select** 문을 포함 하는 문자열을 전달 `Open` 합니다. 자체 기본 문자열을 생성 하는 대신, 레코드 집합은 사용자가 제공 하는 문자열을 사용 합니다. 대체 문에 **WHERE** 절이 포함 된 경우에는 `m_strFilter` 두 개의 필터 문이 있으므로에서 필터를 지정 하지 마십시오. 마찬가지로 바꾸기 문에 **ORDER by** 절이 포함 되어 있는 경우에는 `m_strSort` 두 개의 sort 문이 없도록에서 정렬을 지정 하지 마십시오.

> [!NOTE]
> 필터 (또는 SQL 문의 다른 부분)에서 리터럴 문자열을 사용 하는 경우 DBMS 관련 리터럴 접두사 및 리터럴 접미사 문자 (또는 문자)를 사용 하 여 문자열을 "인용" (지정 된 구분 기호로 묶기) 해야 할 수 있습니다.

또한 DBMS에 따라 외부 조인과 같은 작업에 대 한 특별 한 구문 요구 사항이 발생할 수 있습니다. ODBC 함수를 사용 하 여 DBMS에 대 한 드라이버에서이 정보를 가져옵니다. 예를 들어 `::SQLGetTypeInfo` `SQL_VARCHAR` LITERAL_PREFIX 및 LITERAL_SUFFIX 문자를 요청 하는 등의 특정 데이터 형식에 대해를 호출 합니다. 데이터베이스 독립적 코드를 작성 하는 경우 자세한 구문 정보는 [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference) 에서 [부록 C: SQL 문법](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) 을 참조 하세요.

레코드 집합 개체는 사용자 지정 SQL 문을 전달 하지 않는 한 레코드를 선택 하는 데 사용 하는 SQL 문을 생성 합니다. 이 작업을 수행 하는 방법은 주로 멤버 함수의 *lpszSQL* 매개 변수에 전달 하는 값에 따라 달라 집니다 `Open` .

SQL **SELECT** 문의 일반적인 형태는 다음과 같습니다.

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

레코드 집합의 SQL 문에 **DISTINCT** 키워드를 추가 하는 한 가지 방법은의 첫 번째 RFX 함수 호출에 키워드를 포함 하는 것입니다 `DoFieldExchange` . 예를 들어:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> 읽기 전용으로 열린 레코드 집합에만이 기법을 사용 합니다.

## <a name="overriding-the-sql-statement"></a>SQL 문 재정의

다음 표에서는 *lpszSQL* 매개 변수에 대 한 가능성을 보여 줍니다 `Open` . 테이블의 사례는 표 다음에 설명 되어 있습니다.

**LpszSQL 매개 변수 및 결과 SQL 문자열**

|사례|LpszSQL에서 전달 하는 내용|결과 SELECT 문|
|----------|------------------------------|------------------------------------|
|1|NULL|*테이블 이름* 에서 *rfx-필드 목록* **을** **선택** 합니다.<br /><br /> `CRecordset::Open``GetDefaultSQL`을 호출 하 여 테이블 이름을 가져옵니다. 결과 문자열은에서 반환 하는 항목에 따라 2 ~ 5 개의 사례 중 하나입니다 `GetDefaultSQL` .|
|2|테이블 이름|*테이블 이름* 에서 *rfx-필드 목록* **을** **선택** 합니다.<br /><br /> 필드 목록은의 RFX 문에서 가져옵니다 `DoFieldExchange` . `m_strFilter`및 `m_strSort` 가 비어 있지 않은 경우 **WHERE** 및/또는 **ORDER BY** 절을 추가 합니다.|
|3 \*|**WHERE** 또는 **ORDER BY** 절이 없는 완전 한 **SELECT** 문|전달 됩니다. `m_strFilter`및 `m_strSort` 가 비어 있지 않은 경우 **WHERE** 및/또는 **ORDER BY** 절을 추가 합니다.|
|3-4 \*|**Where** 및/또는 **ORDER BY** 절이 있는 전체 **SELECT** 문|전달 됩니다. `m_strFilter` 및/또는 `m_strSort` 는 비워 두거나 필터 및/또는 정렬 문이 두 개 생성 됩니다.|
|5 \*|저장 프로시저에 대 한 호출입니다.|전달 됩니다.|

\*`m_nFields` **SELECT** 문에 지정 된 열 수보다 작거나 같아야 합니다. **SELECT** 문에 지정 된 각 열의 데이터 형식은 해당 하는 RFX 출력 열의 데이터 형식과 동일 해야 합니다.

### <a name="case-1---lpszsql--null"></a>사례 1 lpszSQL = NULL

레코드 집합 선택은가 `GetDefaultSQL` 호출 될 때 반환 되는 내용에 따라 달라 집니다 `CRecordset::Open` . 사례 2 ~ 5는 가능한 문자열을 설명 합니다.

### <a name="case-2---lpszsql--a-table-name"></a>사례 2 lpszSQL = a 테이블 이름

레코드 집합은 RFX (레코드 필드 교환)를 사용 하 여 레코드 집합 클래스의 재정의에서 RFX 함수 호출에 제공 된 열 이름으로 열 목록을 작성 합니다 `DoFieldExchange` . 마법사를 사용 하 여 레코드 집합 클래스를 선언한 경우이 사례는 사례 1과 동일한 결과를 제공 합니다 (마법사에서 지정한 것과 동일한 테이블 이름을 전달 하는 경우). 마법사를 사용 하 여 클래스를 작성 하지 않는 경우 사례 2는 SQL 문을 생성 하는 가장 간단한 방법입니다.

다음 예에서는 MFC 데이터베이스 응용 프로그램에서 레코드를 선택 하는 SQL 문을 생성 합니다. 프레임 워크에서 멤버 함수를 호출 하는 경우 `GetDefaultSQL` 함수는 테이블의 이름을 반환 `SECTION` 합니다.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

SQL **SELECT** 문에 대 한 열의 이름을 가져오기 위해 프레임 워크는 멤버 함수를 호출 합니다 `DoFieldExchange` .

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

완료 되 면 SQL 문은 다음과 같습니다.

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Case 3 lpszSQL = SELECT/FROM 문

자동으로 생성 하기 위해 RFX에 의존 하지 않고 열 목록을 직접 지정 합니다. 다음과 같은 경우에이 작업을 수행할 수 있습니다.

- **SELECT** 다음에 **DISTINCT** 키워드를 지정 하려고 합니다.

   열 목록은에 나열 된 순서와 동일한 순서로 열 이름 및 유형과 일치 해야 합니다 `DoFieldExchange` .

- RFX를 사용 하 여 열을 바인딩하고 검색 하는 대신 ODBC 함수를 사용 하 여 열 값을 수동으로 검색 해야 하는 이유가 있습니다 `::SQLGetData` .

   예를 들어 응용 프로그램을 배포한 후 응용 프로그램의 고객이 데이터베이스 테이블에 추가한 새 열을 수용할 수 있습니다. 마법사를 사용 하 여 클래스를 선언할 때 알려지지 않은 이러한 추가 필드 데이터 멤버를 추가 해야 합니다.

   열 목록은에 나열 된 순서와 동일한 순서로 열 이름 및 유형과 일치 하 고 `DoFieldExchange` , 수동으로 바인딩된 열의 이름 앞에와 야 합니다. 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.

- **From** 절에 여러 테이블을 지정 하 여 테이블을 조인 하려고 합니다.

   자세한 내용과 예제는 [레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)을 참조 하세요.

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Case 4 lpszSQL = SELECT/FROM 플러스 WHERE and/or ORDER BY

열 목록 (의 RFX 호출 기반 `DoFieldExchange` ), 테이블 목록 및 **WHERE** 및/또는 **ORDER BY** 절의 내용을 모두 지정 합니다. 이러한 방식으로 **WHERE** 및/또는 **ORDER by** 절을 지정 하는 경우 `m_strFilter` and/or를 사용 하지 마십시오 `m_strSort` .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Case 5 lpszSQL = 저장 프로시저 호출

Microsoft SQL Server 데이터베이스의 저장 프로시저와 같은 미리 정의 된 쿼리를 호출 해야 하는 경우 *lpszSQL* 에 전달 하는 문자열에 **call** 문을 작성 해야 합니다. 마법사는 미리 정의 된 쿼리를 호출 하기 위한 레코드 집합 클래스 선언을 지원 하지 않습니다. 미리 정의 된 모든 쿼리가 레코드를 반환 하는 것은 아닙니다.

미리 정의 된 쿼리가 레코드를 반환 하지 않는 경우 멤버 함수를 직접 사용할 수 있습니다 `CDatabase` `ExecuteSQL` . 레코드를 반환 하는 미리 정의 된 쿼리의 경우 `DoFieldExchange` 프로시저에서 반환 하는 모든 열에 대해에서 RFX 호출을 수동으로 작성 해야 합니다. 미리 정의 된 쿼리와 동일한 형식을 반환 하는 RFX 호출은 동일한 순서 여야 합니다. 자세한 내용은 [레코드 집합: 미리 정의 된 쿼리에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[SQL: SQL 및 c + + 데이터 형식 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: SQL 직접 호출 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
