---
description: '자세한 정보: 레코드 집합: 레코드 정렬 (ODBC)'
title: '레코드 집합: 레코드 정렬(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: fbf2ef3c42061bac9b41550a0c44a20f68c099b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204422"
---
# <a name="recordset-sorting-records-odbc"></a>레코드 집합: 레코드 정렬(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 레코드 집합을 정렬 하는 방법을 설명 합니다. 정렬 기준으로 사용할 열을 하나 이상 지정할 수 있으며, 오름차순 이나 내림차순 (**ASC** 또는 **DESC**)을 지정할 수 있습니다. **ASC** 는 지정 된 각 열에 대 한 기본값입니다. 예를 들어 두 개의 열을 지정 하는 경우 레코드는 라는 첫 번째 열에서 먼저 정렬 된 다음 이라는 두 번째 열에 정렬 됩니다. SQL **ORDER by** 절은 정렬을 정의 합니다. 프레임 워크에서 레코드 집합의 SQL 쿼리에 **ORDER by** 절을 추가 하면 절에서 선택의 순서를 제어 합니다.

개체를 구성한 후 멤버 함수를 호출 하기 전에 `Open` (또는 `Requery` `Open` 멤버 함수가 이미 호출 된 기존 레코드 집합 개체에 대해 멤버 함수를 호출 하기 전에) 레코드 집합의 정렬 순서를 설정 해야 합니다.

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>레코드 집합 개체에 대 한 정렬 순서를 지정 하려면

1. 새 레코드 집합 개체를 생성 하거나 `Requery` 기존 개체에 대 한 호출을 준비 합니다.

1. 개체 [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) 데이터 멤버의 값을 설정 합니다.

   정렬은 null로 끝나는 문자열입니다. 이 파일에는 **order** by 절의 내용이 포함 되지만 키워드 **order by** 는 포함 되지 않습니다. 예를 들어 이에 해당하는 서비스는 다음과 같습니다.

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. 필터, 잠금 모드 또는 매개 변수와 같은 필요한 다른 옵션을 설정 합니다.

1. `Open`새 개체 또는 기존 개체에 대해를 호출 `Requery` 합니다.

선택한 레코드는 지정 된 대로 정렬 됩니다. 예를 들어 학생 레코드 집합을 성을 기준으로 내림차순으로 정렬 하려면 다음을 수행 합니다.

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

레코드 집합은 성을 기준으로 내림차순으로 정렬 된 다음 이름으로 정렬 된 모든 학생 레코드를 포함 합니다.

> [!NOTE]
> 사용자 고유의 SQL 문자열을에 전달 하 여 레코드 집합의 기본 SQL 문자열을 재정의 하도록 선택 하는 경우 `Open` 사용자 지정 문자열에 **ORDER by** 절이 있는 경우 정렬을 설정 하지 마세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[레코드 집합: 레코드 필터링 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
