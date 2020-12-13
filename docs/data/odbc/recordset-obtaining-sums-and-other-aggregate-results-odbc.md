---
description: '자세한 정보: 레코드 집합: 합계 및 다른 집계 결과 가져오기 (ODBC)'
title: '레코드 집합: 합계 및 다른 집계 결과 구하기(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 10a2ef3b013d9eba0d9733cc321591ae8d6681f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136489"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>레코드 집합: 합계 및 다른 집계 결과 구하기(ODBC)

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 다음 [SQL](../../data/odbc/sql.md) 키워드를 사용하여 집계 결과를 얻는 방법을 설명합니다.

- **SUM** 숫자 데이터 형식을 사용하여 열에 있는 값의 합계를 계산합니다.

- **MIN** 숫자 데이터 형식을 사용하여 열에서 가장 작은 값을 추출합니다.

- **MAX** 숫자 데이터 형식을 사용하여 열에서 가장 큰 값을 추출합니다.

- **AVG** 숫자 데이터 형식을 사용하여 열에 있는 모든 값의 평균값을 계산합니다.

- **COUNT** 모든 데이터 형식의 열에 있는 레코드의 수를 계산합니다.

이러한 SQL 함수를 사용하여 데이터 원본에서 레코드를 추출하는 대신 데이터 원본의 레코드에 대한 통계 정보를 가져옵니다. 일반적으로 만든 레코드 집합은 값을 포함하는 단일 레코드(모든 열이 집계된 경우)로 구성됩니다. **GROUP by** 절을 사용 하는 경우 두 개 이상의 레코드가 있을 수 있습니다. 이 값은 SQL 함수에서 수행 하는 계산 또는 추출의 결과입니다.

> [!TIP]
> SQL **GROUP BY** 절(및 가능하면 **HAVING** 절)을 SQL 문에 추가하려면 `m_strFilter`의 끝에 추가합니다. 예를 들어:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

열을 필터링하고 정렬하여 집계 결과를 얻는 데 사용하는 레코드 수를 제한할 수 있습니다.

> [!CAUTION]
> 일부 집계 연산자는 집계하는 열에서 다른 데이터 형식을 반환합니다.

- **SUM** 및 **AVG** 는 다음으로 큰 데이터 형식을 반환할 수 있습니다. 예를 들어를 호출 하면 **`int`** **LONG** 또는가 반환 **`double`** 됩니다.

- **COUNT** 는 일반적으로 대상 열 유형에 관계없이 **LONG** 을 반환합니다.

- **MAX** 및 **MIN** 은 계산하는 열과 동일한 데이터 형식을 반환합니다.

     예를 들어 **클래스 추가** 마법사는 **`long`** `m_lSales` Sales 열을 수용 하기 위해를 만들지만이를 `double m_dblSumSales` 데이터 멤버로 바꿔서 집계 결과를 수용 해야 합니다. 다음 예제를 참조하세요.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>레코드 집합에 대한 집계 결과를 가져오려면

1. 집계 결과를 가져올 열이 포함된 [MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)에서 설명된 대로 레코드 집합을 만듭니다.

1. 레코드 집합에 대한 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 함수를 수정합니다. 열 이름을 나타내는 문자열([RFX](../../data/odbc/record-field-exchange-using-rfx.md) 함수 호출의 두 번째 인수)을 열의 집계 함수를 나타내는 문자열로 바꿉니다. 예를 들어 다음을 바꿉니다.

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     다음으로 바꿉니다.

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. 레코드 집합을 엽니다. 집계 작업의 결과는 `m_dblSumSales`에 남아 있습니다.

> [!NOTE]
> 마법사는 실제로 헝가리어 접두사 없이 데이터 멤버 이름을 할당합니다. 예를 들어 마법사는 앞에 그림에 사용된 `m_lSales` 이름 대신 Sales 열에 대해 `m_Sales`를 생성합니다.

[CRecordView](../../mfc/reference/crecordview-class.md) 클래스를 사용하여 데이터를 보는 경우 새 데이터 멤버 값을 표시하도록 DDX 함수 호출을 변경해야 합니다. 이 경우 다음에서 변경합니다.

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

대상:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 집합의 레코드 선택 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
