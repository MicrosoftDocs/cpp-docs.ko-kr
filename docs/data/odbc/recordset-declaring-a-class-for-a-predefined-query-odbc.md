---
description: '자세한 정보: 레코드 집합: 미리 정의 된 쿼리에 대 한 클래스 선언 (ODBC)'
title: '레코드 집합: 미리 정의된 쿼리에 대한 클래스 선언(ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: e2071270bbff92e56b7fc3a2064e7e2f99f2044b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210948"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>레코드 집합: 미리 정의된 쿼리에 대한 클래스 선언(ODBC)

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 미리 정의된 쿼리(Microsoft SQL Server에서 처럼 저장 프로시저라고도 함)에 대한 레코드 집합 클래스를 만드는 방법을 설명합니다.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 구현하는 경우 프로세스가 매우 비슷합니다. 대량 행 페치를 구현 하는 레코드 집합과 그렇지 않은 레코드 집합 간의 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

일부 DBMS(데이터베이스 관리 시스템)를 사용하면 미리 정의된 쿼리를 만들고 함수처럼 프로그램에서 호출할 수 있습니다. 쿼리는 이름이 있고 매개 변수를 사용할 수 있으며 레코드를 반환할 수 있습니다. 이 항목의 절차에서는 레코드를 반환하는 미리 정의된 쿼리를 호출하고 매개 변수를 사용하는 방법을 설명합니다.

데이터베이스 클래스는 미리 정의된 쿼리 업데이트를 지원하지 않습니다. 미리 정의된 쿼리 스냅샷과 미리 정의된 쿼리 다이너셋 간의 차이점은 업데이트 가능성이 아니라 다른 사용자(또는 프로그램의 다른 레코드 집합)가 변경한 내용이 레코드 집합에 표시되는지 여부입니다.

> [!TIP]
> 레코드를 반환하지 않는 미리 정의된 쿼리를 호출하기 위해 레코드 집합이 필요하지 않습니다. 아래 설명된 대로 SQL 문을 준비하지만 `CDatabase` 멤버 함수 [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)을 호출하여 실행합니다.

단일 레코드 집합 클래스를 만들어 미리 정의된 쿼리를 호출하는 것을 관리할 수 있지만 일부 작업은 직접 수행해야 합니다. 마법사는 특별히 이 목적을 위한 클래스를 만드는 것을 지원하지 않습니다.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>미리 정의된 쿼리(저장 프로시저)를 호출하기 위한 클래스를 만들려면

1. **클래스 추가** 에서 [MFC ODBC 소비자 마법사](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 사용하여 쿼리에서 반환되는 대부분의 열을 제공하는 테이블의 레코드 집합 클래스를 만듭니다. 이렇게 하면 시작할 수 있습니다.

1. 쿼리가 반환하지만 마법사가 생성하지 않은 테이블의 모든 열에 대해 필드 데이터 멤버를 수동으로 추가합니다.

   예를 들어 쿼리가 두 개의 테이블에서 각각 세 개의 열을 반환하는 경우, 적절한 데이터 형식의 여섯 개의 필드 데이터 멤버를 클래스에 추가합니다.

1. 추가된 각 필드 데이터 멤버의 데이터 형식에 해당하는 클래스의 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 멤버 함수에 [RFX](../../data/odbc/record-field-exchange-rfx.md) 함수 호출을 수동으로 추가합니다.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  결과 집합에 반환되는 데이터 형식과 열 순서를 알고 있어야 합니다. `DoFieldExchange`의 RFX 함수 호출 순서는 결과 집합 열의 순서와 일치해야 합니다.

1. 새 필드 데이터 멤버에 대한 초기화를 레코드 집합 클래스 생성자에 수동으로 추가합니다.

   또한 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 데이터 멤버에 대한 초기화 값을 증분해야 합니다. 마법사는 초기화를 작성하지만 추가한 필드 데이터 멤버만 다룹니다. 예를 들어:

    ```cpp
    m_nFields += 6;
    ```

   일부 데이터 형식(예 `CLongBinary` 또는 바이트 배열)은 여기서 초기화하면 안됩니다.

1. 쿼리 매개 변수를 사용하는 경우 각 매개 변수에 대한 매개 변수 데이터 멤버, 각 매개 변수에 대한 RFX 함수 호출 및 각각에 대한 초기화를 추가합니다.

1. 이 절차의 4단계에서 추가된 필드에 대해 `m_nFields`를 수행한 것처럼 추가된 각 매개 변수에 대해 `m_nParams`를 증분해야 합니다. 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

1. 다음 양식을 사용하여 SQL 문 문자열을 수동으로 작성합니다.

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   여기서 **CALL** 은 ODBC 키워드이고, **proc-name** 은 데이터 원본에 알려진 쿼리 이름이고 "?" 항목은 런타임 시 레코드 집합에 제공하는 매개 변수 값(있는 경우)의 자리 표시자입니다. 다음 예제에서는 하나의 매개 변수에 대한 자리 표시자를 준비합니다.

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. 레코드 집합을 여는 코드에서 레코드 집합의 매개 변수 데이터 멤버 값을 설정한 다음, `Open` 멤버 함수를 호출하여 *lpszSQL* 매개 변수에 대한 SQL 문자열을 전달합니다. 또는 대신 클래스의 `GetDefaultSQL` 멤버 함수에 의해 반환된 문자열을 바꿉니다.

다음 예제에서는 판매 지역 번호에 대해 하나의 매개 변수를 사용하는 `Delinquent_Accts`라는 미리 정의된 쿼리를 호출하는 절차를 보여줍니다. 이 쿼리는 세 개의 열(`Acct_No`, `L_Name`, `Phone`)을 반환합니다. 모든 열은 Customers 테이블에서 가져온 것입니다.

다음 레코드 집합은 쿼리가 반환하는 열의 필드 데이터 멤버와 런타임 시 요청된 판매 구역 번호의 매개 변수를 지정합니다.

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

이 클래스 선언은 수동으로 추가된 `m_lDistParam` 멤버를 제외하고 마법사가 작성하는 것과 같습니다. 다른 멤버는 여기에 표시되지 않습니다.

다음 예제에서는 `CDelinquents` 생성자의 데이터 멤버에 대한 초기화를 보여줍니다.

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 및 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)에 대한 초기화를 참고하세요. 마법사가 `m_nFields`를 초기화하고 사용자가 `m_nParams`를 초기화합니다.

다음 예제에서는 `CDelinquents::DoFieldExchange`의 RFX 함수를 보여줍니다.

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

반환된 세 개의 열에 대한 RFX를 호출하는 것 외에도 이 코드는 런타임에 전달되는 매개 변수 바인딩을 관리합니다. 매개 변수는 `Dist_No`(구역 번호) 열에 입력됩니다.

다음 예제에서는 SQL 문자열을 설정하는 방법과 레코드 집합을 여는 데 사용하는 방법을 보여줍니다.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

이 코드는 스냅샷을 생성하고, 사용자로부터 이전에 가져온 매개 변수를 전달하고, 미리 정의된 쿼리를 호출 합니다. 쿼리를 실행하는 경우 지정된 판매 구역에 대한 레코드를 반환합니다. 각 레코드에는 계정 번호, 고객 성 및 고객의 전화 번호에 대한 열이 있습니다.

> [!TIP]
> 저장 프로시저에서 반환된 값(출력 매개 변수)을 처리할 수 있습니다. 자세한 내용과 예제는 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)을 참조하세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 집합 다시 쿼리 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
