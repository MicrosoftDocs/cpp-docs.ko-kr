---
description: '자세한 정보: 레코드 집합: 레코드 집합 매개 변수화 (ODBC)'
title: '레코드 집합: 레코드 집합 매개 변수화(ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 0801e503992204ac24bff2e9378f4e1d24f9864d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204526"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>레코드 집합: 레코드 집합 매개 변수화(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

계산하거나 최종 사용자로부터 획득한 정보를 사용하여 런타임에 레코드를 선택할 수 있으면 좋겠다고 생각할 때가 간혹 있습니다. 레코드 집합 매개 변수를 사용하면 바로 그런 작업을 할 수 있습니다.

이 토픽에서는 다음 내용을 설명합니다.

- [매개 변수화 레코드 집합의 목적](#_core_parameterized_recordsets)

- [레코드 집합을 매개 변수화하는 경우 및 이유](#_core_when_to_use_parameters)

- [레코드 집합 클래스에서 매개 변수 데이터 멤버를 선언하는 방법](#_core_parameterizing_your_recordset_class)

- [런타임에 레코드 집합 개체에 매개 변수 정보를 전달하는 방법](#_core_passing_parameter_values_at_run_time)

## <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a> 매개 변수화 레코드 집합

매개 변수화 레코드 집합을 사용하면 런타임에 매개 변수 정보를 전달할 수 있습니다. 이 기능은 두 가지 중요한 효과가 있습니다.

- 실행 속도가 더 빨라질 수 있습니다.

- 디자인 타임에 사용할 수 없던 정보(예: 런타임에 사용자로부터 획득하거나 계산한 정보)를 바탕으로 런타임에 쿼리를 작성할 수 있습니다.

`Open`을 호출하여 쿼리를 실행하는 경우 레코드 집합은 매개 변수 정보를 사용하여 자체의 **SQL SELECT** 문을 완료합니다. 어떤 레코드 집합도 매개 변수화할 수 있습니다.

## <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a> 매개 변수를 사용하는 경우

매개 변수의 일반적인 사용은 다음을 포함합니다.

- 미리 정의된 쿼리에 런타임 인수 전달

   저장 프로시에 매개 변수를 전달하려면 `Open`을 호출할 때 매개 변수 자리 표시자를 통해 완전한 사용자 지정 ODBC **CALL** 문을 지정하여 레코드 집합의 기본 SQL 문을 재정의해야 합니다. 자세한 내용은 *클래스 라이브러리 참조* 에서 [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) 및 [SQL: 레코드 집합의 SQL 문 사용자 지정 (odbc)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) 및 [레코드 집합: 미리 정의 된 쿼리에 대 한 클래스 선언 (odbc)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)을 참조 하세요.

- 서로 다른 매개 변수 정보를 사용하여 수많은 다시 쿼리를 효율적으로 수행합니다.

   예를 들어 최종 사용자가 학생 등록 데이터베이스에서 특정 학생에 대한 정보를 조회할 때마다 해당 학생의 이름 또는 ID를 사용자로부터 획득한 매개 변수로 지정할 수 있습니다. 그런 다음, 레코드 집합의 `Requery` 멤버 함수를 호출하면 쿼리에서 해당 학생의 레코드만 선택합니다.

   `m_strFilter`에 저장된 레코드 집합의 필터 문자열은 다음과 같을 수 있습니다.

    ```cpp
    "StudentID = ?"
    ```

   변수 `strInputID`에서 학생 ID를 가져온다고 가정합니다. 매개 변수를 `strInputID`(예를 들어 학생 ID 100)로 설정하면 변수의 값은 필터 문자열에 "?"로 표시된 매개 변수 자리 표시자에 바인딩됩니다.

   매개 변수 값을 다음과 같이 할당합니다.

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   필터 문자열은 이 방법으로 설정하기를 원하지 않을 것입니다.

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   필터 문자열에 따옴표를 올바르게 사용 하는 방법에 대 한 자세한 내용은 레코드 [집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)을 참조 하세요.

   매개 변수 값은 레코드 집합에 대해 새 학생 ID를 다시 쿼리할 때마다 다릅니다.

   > [!TIP]
   > 매개 변수 사용은 단순한 필터보다 더 효율적입니다. 매개 변수화 레코드 집합의 경우 데이터베이스는 SQL **SELECT** 문을 한 번만 처리해야 합니다. 매개 변수 없이 필터링된 레코드 집합의 경우 새 필터 값을 사용하여 `Requery`할 때마다 **SELECT** 문을 처리해야 합니다.

필터에 대 한 자세한 내용은 레코드 [집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)을 참조 하세요.

## <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a> 레코드 집합 클래스 매개 변수화

> [!NOTE]
> 이 섹션은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 사용하는 경우 매개 변수 구현은 유사한 프로세스입니다. 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

레코드 집합을 만들기 전에 필요한 매개 변수, 해당 매개 변수의 데이터 형식 및 레코드 집합에서 해당 매개 변수를 사용하는 방법을 결정합니다.

#### <a name="to-parameterize-a-recordset-class"></a>레코드 집합 클래스를 매개 변수화하려면 다음을 수행합니다.

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 수동으로 이 기능을 만들 수는 있습니다.

1. **클래스 추가** 에서 [MFC ODBC 소비자 마법사](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 실행하여 클래스를 만듭니다.

1. 레코드 집합의 열에 대한 필드 데이터 멤버를 지정합니다.

1. 마법사가 프로젝트의 파일에 클래스를 쓴 후 .h 파일로 이동하고 수동으로 하나 이상의 매개 변수 데이터 멤버를 클래스 선언에 추가합니다. 추가는 다음 예제와 같으며, 이는 "센서 클래스에 어느 학생이 있나요?" 쿼리에 답하도록 디자인된 스냅샷 클래스의 일부입니다.

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   매개 변수 데이터 멤버를 마법사가 생성한 필드 데이터 멤버 뒤에 추가합니다. 규칙은 각 사용자 정의 매개 변수 이름에 단어 "Param"을 추가하는 것입니다.

1. .cpp 파일의 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 멤버 함수 정의를 수정합니다. 클래스에 추가한 각 매개 변수 데이터 멤버에 대해 RFX 함수 호출을 추가합니다. RFX 함수를 작성 하는 방법에 대 한 자세한 내용은 [레코드 필드 교환: Rfx 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)을 참조 하세요. 매개 변수에 대한 RFX 호출을 다음 단일 호출의 앞에 추가합니다.

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. 레코드 집합 클래스의 생성자에서 매개 변수 개수 `m_nParams`를 증가합니다.

   자세한 내용은 [레코드 필드 교환: 마법사 코드 작업](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)을 참조 하세요.

1. 이 클래스의 레코드 집합 개체를 만드는 코드를 작성할 때 매개 변수로 바꿀 SQL 명령문 문자열의 각 자리에 "?"(물음표)를 넣습니다.

   런타임에 "?" 자리 표시자가 전달된 매개 변수 값으로 차례로 채워집니다. [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 호출 뒤에 설정한 첫 번째 매개 변수 데이터 멤버는 SQL 문자열의 첫 번째 "?"를 바꾸고 두 번째 매개 변수 데이터 멤버는 두 번째 "?"를 바꾸는 식입니다.

> [!NOTE]
> 매개 변수 순서는 중요합니다. 즉, `DoFieldExchange` 함수에서 매개 변수에 대한 RFX 호출의 순서는 SQL 문자열의 매개 변수 자리 표시자의 순서와 일치해야 합니다.

> [!TIP]
> 작업할 가능성이 가장 높은 문자열은 클래스의 [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 데이터 멤버에 대해 지정한 문자열(있는 경우)이지만 일부 ODBC 드라이버는 다른 SQL 절에 매개 변수를 허용할 수 있습니다.

## <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a> 런타임에 매개 변수 값 전달

`Open`(새 레코드 집합 개체) 또는 `Requery`(기존 레코드 집합 개체)를 호출하기 전에 매개 변수 값을 지정해야 합니다.

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>런타임에 레코드 집합 개체에 매개 변수 값을 전달하려면 다음을 수행합니다.

1. 레코드 집합 개체를 생성합니다.

1. 문자열(예: SQL 문 또는 해당 문의 일부를 포함하는 `m_strFilter` 문자열)을 준비합니다. 매개 변수 정보가 들어갈 위치에 "?" 자리 표시자를 넣습니다.

1. 런타임 매개 변수 값을 개체의 각 매개 변수 데이터 멤버에 할당합니다.

1. `Open` 멤버 함수(또는 기존 레코드 집합의 경우 `Requery`)를 호출합니다.

예를 들어 런타임에 획득한 정보를 사용하여 레코드 집합에 대한 필터 문자열을 지정한다고 가정합니다. 이전에 클래스 `CStudentSet`의 레코드 집합(`rsStudents`)을 생성했는데 이제 특정 종류의 학생 정보를 요청하려 한다고 가정합니다.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

레코드 집합은 해당 기록이 런타임 매개 변수에서 생성된 필터로 지정한 조건을 만족하는 학생에 대한 레코드를 포함합니다. 이 경우 레코드 집합은 모든 고학년 학생에 대한 기록을 포함합니다.

> [!NOTE]
> 필요한 경우 [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull)을 사용하여 매개 변수 데이터 멤버의 값을 Null로 설정할 수 있습니다. 마찬가지로 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)을 사용하여 매개 변수 데이터 멤버가 Null인지 여부를 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
