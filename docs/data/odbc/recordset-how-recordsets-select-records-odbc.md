---
description: '자세한 정보: 레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)'
title: '레코드 집합: 레코드 집합의 레코드 선택 방법(ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 25032c1901513e0c99ddcf8018fb108eb7c1fbd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304469"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>레코드 집합: 레코드 집합의 레코드 선택 방법(ODBC)

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 토픽에서는 다음 내용을 설명합니다.

- [레코드 선택 시 개발자의 역할 및 옵션](#_core_your_options_in_selecting_records)

- [레코드 집합에서 자체 SQL 명령문을 생성하고 레코드를 선택하는 방법](#_core_how_a_recordset_constructs_its_sql_statement)

- [선택을 사용자 지정하기 위해 할 수 있는 작업](#_core_customizing_the_selection)

레코드 집합은 SQL 명령문을 드라이버에 보내서 ODBC 드라이버를 통해 데이터 소스에서 레코드를 선택합니다. 보내는 SQL은 레코드 집합 클래스를 디자인하고 여는 방법에 따라 달라집니다.

## <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> 레코드 선택 시 개발자의 옵션

다음 표는 레코드 선택 시 개발자의 옵션을 보여줍니다.

### <a name="how-and-when-you-can-affect-a-recordset"></a>레코드 집합에 영향을 줄 수 있는 방법 및 경우

|다음과 같은 경우|이 문서의 설명에 따라 Azure Automation Hybrid Runbook Worker를 제거할 수 있습니다.|
|--------------|-------------|
|**클래스 추가** 마법사를 사용하여 레코드 집합 클래스 선언|선택할 테이블을 지정합니다.<br /><br /> 포함할 열을 지정합니다.<br /><br /> [MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 참조하세요.|
|레코드 집합 클래스 구현 완료|`OnSetOptions`(고급)와 같은 멤버 함수를 재정의하여 애플리케이션 고유 옵션을 설정하거나 기본값을 변경합니다. 매개 변수화 레코드 집합을 원하는 경우 매개 변수 데이터 멤버를 지정합니다.|
|레코드 집합 개체 생성(`Open` 호출 전)|레코드를 필터링하는 **WHERE** 절에 사용할 검색 조건(복합 조건 가능)을 지정합니다. 레코드 [집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)을 참조 하세요.<br /><br /> 레코드를 정렬하는 **ORDER BY** 절에 사용할 정렬 순서를 지정합니다. 레코드 [집합: 레코드 정렬 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)을 참조 하세요.<br /><br /> 클래스에 추가한 매개 변수에 대한 매개 변수 값을 지정합니다. [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.|

|`Open`을 호출하여 레코드 집합의 쿼리 실행|마법사에서 설정한 기본 SQL 문자열을 바꿀 사용자 지정 SQL 문자열을 지정합니다. *클래스 라이브러리 참조* 에서 [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) 및 [SQL: 레코드 집합의 SQL 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하세요. |

|`Requery`를 호출하여 데이터 원본에 대한 최신 값을 사용하여 레코드 집합을 다시 쿼리|새 매개 변수, 필터 또는 정렬을 지정합니다. [레코드 집합: 레코드 집합 다시 쿼리 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)를 참조 하세요.

## <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 레코드 집합에서 자체 SQL 명령문을 생성하는 방법

개체의 [Open](../../mfc/reference/crecordset-class.md#open) 멤버 함수를 호출할 때 `Open`은 다음 요소 중 일부 또는 전부를 사용하여 SQL 명령문을 생성합니다.

- `Open`에 전달된 *lpszSQL* 매개 변수. NULL이 아닌 경우 이 매개 변수는 사용자 지정 SQL 문자열 또는 그 일부를 지정합니다. 프레임워크는 문자열을 구문 분석합니다. 문자열이 SQL **SELECT** 문 또는 ODBC **CALL** 문인 경우 프레임워크는 해당 문자열을 레코드 집합의 SQL 명령문으로 사용합니다. 문자열이 "SELECT" 또는 "{CALL"로 시작하지 않으면 프레임워크는 제공된 내용을 사용하여 SQL **FROM** 절을 생성합니다.

- [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)에서 반환된 문자열. 기본적으로 이는 마법사에서 레코드 집합에 대해 지정한 테이블의 이름이지만 함수가 반환하는 내용을 변경할 수 있습니다. 프레임워크는 `GetDefaultSQL`을 호출합니다. — 문자열이 "SELECT" 또는 "{CALL"로 시작하지 않으면 SQL 문자열을 생성하는 데 사용되는 테이블 이름이라고 가정합니다.

- 테이블의 특정 열에 바인딩된 레코드 집합의 필드 데이터 멤버. 프레임워크는 해당 멤버를 버퍼로 사용하여 레코드 열을 해당 멤버의 주소에 바인딩합니다. 프레임워크는 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 또는 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 멤버 함수에서 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 또는 Bulk RFX 함수 호출의 테이블 열과 필드 데이터 멤버의 상관 관계를 결정합니다.

- [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 데이터 멤버에 포함된 레코드 집합에 대한 [필터](../../data/odbc/recordset-filtering-records-odbc.md)(있는 경우). 프레임워크는 이 문자열을 사용하여 SQL **WHERE** 절을 생성합니다.

- [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) 데이터 멤버에 포함된 레코드 집합에 대한 [정렬](../../data/odbc/recordset-sorting-records-odbc.md) 순서(있는 경우). 프레임워크는 이 문자열을 사용하여 SQL **ORDER BY** 절을 생성합니다.

   > [!TIP]
   > SQL **GROUP BY** 절(및 **HAVING** 절도 사용 가능)을 사용하려면 이 절을 필터 문자열의 끝에 추가합니다.

- 클래스에 대해 지정하는 [매개 변수 데이터 멤버](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)의 값. `Open` 또는 `Requery`를 호출하기 직전에 매개 변수 값을 설정했습니다. 프레임워크는 매개 변수 값을 SQL 문자열의 "?" 자리 표시자에 바인딩합니다. 컴파일 시간에 자리 표시자를 사용하여 이 문자열을 지정합니다. 런타임에 프레임워크는 전달된 매개 변수 값을 기반으로 세부 정보를 채웁니다.

`Open`은 이 요소에서 SQL **SELECT** 문을 생성합니다. 프레임워크가 이 요소를 사용하는 방법에 대한 자세한 내용은 [선택 사용자 지정](#_core_customizing_the_selection)을 참조하세요.

명령문을 생성한 후 `Open`은 SQL을 ODBC 드라이버 관리자(및 메모리에 있는 경우 ODBC 커서 라이브러리)에 보내서 특정 DBMS용 ODBC 드라이버에 해당 SQL을 보내도록 합니다. 드라이버는 DBMS와 통신하여 데이터 원본에 대해 선택을 수행하고 첫 번째 레코드를 페치합니다. 프레임워크는 레코드를 레코드 집합의 필드 데이터 멤버에 로드합니다.

이 방법들의 조합을 사용하여 [테이블](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)을 열고 여러 테이블의 [조인](../../data/odbc/recordset-performing-a-join-odbc.md)을 기반으로 쿼리를 생성합니다. 추가 사용자 지정을 사용하면 [미리 정의된 쿼리](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)(저장 프로시저)를 호출하고 디자인 타임에 알려지지 않은 테이블 열을 선택하고 이들을 레코드 집합 필드에 [바인딩](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)하거나 대부분의 다른 데이터 액세스 작업을 수행할 수 있습니다. 레코드 집합을 사용자 지정하여 수행할 수 없는 작업은 [ODBC API 함수](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)에 의해 수행하거나 [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)을 통해 SQL 명령문을 직접 실행하여 수행할 수 있습니다.

## <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> 선택 사용자 지정

필터, 정렬 순서 또는 매개 변수를 제공하는 것 이외에 다음 작업을 수행하여 레코드 집합의 선택을 사용자 지정할 수 있습니다.

- 레코드 집합에 대해 [Open](../../mfc/reference/crecordset-class.md#open)을 호출할 때 *lpszSQL* 에 사용자 지정 SQL 문자열을 전달합니다. *lpsqSQL* 에 전달하는 내용은 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 멤버 함수가 반환하는 내용보다 우선적으로 적용됩니다.

   자세한 내용은 [sql: 레코드 집합의 Sql 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하세요. 여기서는 전달할 수 있는 sql 문 (또는 부분 문) 유형과 `Open` 프레임 워크에서 수행 하는 작업을 설명 합니다.

    > [!NOTE]
    >  전달하는 사용자 지정 문자열이 "SELECT" 또는 "{CALL"로 시작하지 않는 경우 MFC는 테이블 이름을 포함한다고 가정합니다. 이 원칙은 다음 글머리표 항목에도 적용됩니다.

- 마법사가 레코드 집합의 `GetDefaultSQL` 멤버 함수에 쓰는 문자열을 변경합니다. 함수의 코드를 편집하여 반환하는 내용을 변경합니다. 기본적으로 마법사는 단일 테이블 이름을 반환하는 `GetDefaultSQL` 함수를 씁니다.

   `GetDefaultSQL`이 `Open`에 *lpszSQL* 매개 변수를 전달할 수 있는 어떤 항목도 반환하도록 지정할 수 있습니다. *lpszSQL* 에 사용자 지정 SQL 문자열을 전달하지 않으면 프레임워크는 `GetDefaultSQL`이 반환하는 문자열을 사용합니다. 적어도 `GetDefaultSQL`은 단일 테이블 이름을 반환해야 합니다. 그러나 여러 테이블 이름, 전체 **SELECT** 문, ODBC **CALL** 문 등을 반환하도록 지정할 수 있습니다. *LpszSQL* 에 전달 하거나 반환 하는 항목의 목록은 `GetDefaultSQL` [SQL: 레코드 집합의 sql 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하세요.

   둘 이상의 테이블에 대해 조인을 수행하는 경우 `GetDefaultSQL`을 다시 작성하여 SQL **FROM** 절에 사용한 테이블 목록을 사용자 지정합니다. 자세한 내용은 [레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)을 참조 하세요.

- 아마도 런타임에 데이터 원본의 스키마에 관하여 획득하는 정보를 기반으로 추가 필드 데이터 멤버를 수동으로 바인딩합니다. 레코드 집합 클래스, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 또는 이들에 대한 Bulk RFX 함수 호출을 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 또는 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) 멤버 함수 및 클래스 생성자의 데이터 멤버 초기화에 추가합니다. 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.

- `OnSetOptions`와 같은 레코드 집합 멤버 함수를 재정의하여 애플리케이션 고유 옵션을 설정하거나 기본값을 재정의합니다.

레코드 집합이 복잡한 SQL 문을 기반으로 하도록 하려면 이러한 사용자 지정 방법들을 조합하여 사용해야 합니다. 예를 들어 아마도 레코드 집합에서 직접 지원하지 않는 SQL 절 및 키워드를 사용하려 하거나 여러 테이블을 조인하는 경우가 있습니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC 기본 사항](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[레코드 집합: 레코드 잠금 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
