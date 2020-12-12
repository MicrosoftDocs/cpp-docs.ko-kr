---
description: '자세한 정보: 레코드 집합: 레코드 필터링 (ODBC)'
title: '레코드 집합: 레코드 필터링(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 15cf191f7a5a037c032726bc4f16a5774fb2857b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322340"
---
# <a name="recordset-filtering-records-odbc"></a>레코드 집합: 레코드 필터링(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 사용 가능한 레코드의 특정 하위 집합만 선택 하도록 레코드 집합을 필터링 하는 방법에 대해 설명 합니다. 예를 들어 MATH101와 같은 특정 과정에 대 한 클래스 섹션만 선택할 수 있습니다. 필터는 SQL **WHERE** 절의 내용으로 정의 된 검색 조건입니다. 프레임 워크에서이를 레코드 집합의 SQL 문에 추가 하면 **where** 절이 선택 항목을 제한 합니다.

개체를 생성 한 후 멤버 함수를 호출 하기 전에 `Open` (또는 `Requery` `Open` 멤버 함수가 이미 호출 된 기존 레코드 집합 개체에 대해 멤버 함수를 호출 하기 전에) 레코드 집합 개체의 필터를 설정 해야 합니다.

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>레코드 집합 개체에 대 한 필터를 지정 하려면

1. 새 레코드 집합 개체를 생성 하거나 `Requery` 기존 개체에 대 한 호출을 준비 합니다.

1. 개체 [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 데이터 멤버의 값을 설정 합니다.

   필터는 SQL **where** 절의 내용을 포함 하지만 키워드는 포함 하지 않는 null로 끝나는 **문자열입니다.** 예를 들어 이에 해당하는 서비스는 다음과 같습니다.

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  리터럴 문자열 "MATH101"은 위의 작은따옴표로 표시 됩니다. ODBC SQL 사양에서 작은따옴표는 문자열 리터럴을 나타내는 데 사용 됩니다. 이러한 상황에서 DBMS의 인용 요구 사항은 ODBC 드라이버 설명서를 참조 하세요. 이 구문은이 항목의 끝 부분에도 설명 되어 있습니다.

1. 정렬 순서, 잠금 모드 또는 매개 변수와 같이 필요한 다른 옵션을 설정 합니다. 매개 변수를 지정 하는 것이 특히 유용 합니다. 필터 매개 변수화에 대 한 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

1. `Open`새 개체 또는 이전에 열린 개체에 대해를 호출 `Requery` 합니다.

> [!TIP]
> 필터에서 매개 변수를 사용 하는 것은 레코드를 검색 하는 가장 효율적인 방법일 수 있습니다.

> [!TIP]
> 레코드 집합 필터는 런타임에 얻거나 계산 된 정보를 기반으로 하는 [매개 변수](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 를 사용 하 여 테이블을 [조인](../../data/odbc/recordset-performing-a-join-odbc.md) 하는 데 유용 합니다.

레코드 집합은 지정한 검색 조건을 충족 하는 레코드만 선택 합니다. 예를 들어 위에 설명 된 과정 필터를 지정 하려면 (예 `strCourseID` : 현재 변수를 "MATH101"로 설정 했다고 가정) 다음을 수행 합니다.

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

레코드 집합에는 MATH101의 모든 클래스 섹션에 대 한 레코드가 포함 되어 있습니다.

문자열 변수를 사용 하 여 위의 예제에서 필터 문자열이 설정 된 방식을 확인 합니다. 일반적인 사용법입니다. 하지만 강좌 ID에 대해 리터럴 값 100을 지정 하려고 한다고 가정 합니다. 다음 코드에서는 리터럴 값을 사용 하 여 필터 문자열을 올바르게 설정 하는 방법을 보여 줍니다.

```
m_strFilter = "StudentID = '100'";   // correct
```

작은따옴표 문자를 사용 합니다. 필터 문자열을 직접 설정 하는 경우 필터 문자열 **은 다음과 같습니다**.

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

위에 표시 된 따옴표가 ODBC 사양을 따르지만 일부 Dbms는 다른 따옴표 문자를 요구할 수도 있습니다. 자세한 내용은 [sql: 레코드 집합의 Sql 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하세요.

> [!NOTE]
> 사용자 고유의 SQL 문자열을에 전달 하 여 레코드 집합의 기본 SQL 문자열을 재정의 하도록 선택 하는 경우 `Open` 사용자 지정 문자열에 **where** 절이 있는 경우 필터를 설정 하면 안 됩니다. 기본 SQL을 재정의 하는 방법에 대 한 자세한 내용은 [sql: 레코드 집합의 Sql 문 사용자 지정 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 정렬 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[레코드 집합: 레코드 잠금 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
