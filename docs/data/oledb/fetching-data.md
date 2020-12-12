---
description: '자세히 알아보기: 데이터 가져오기'
title: 데이터 페치
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 4d98a3d804688447f8f7073d20371a098b2bfa11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287530"
---
# <a name="fetching-data"></a>데이터 페치

데이터 원본, 세션 및 행 집합 개체를 연 후 데이터를 페치할 수 있습니다. 사용 중인 접근자의 유형에 따라 열을 바인딩해야 할 수도 있습니다.

## <a name="to-fetch-data"></a>데이터를 페치 하려면

1. 적절 한 **열기** 명령을 사용 하 여 행 집합을 엽니다.

1. 를 사용 하 `CManualAccessor` 는 경우 출력 열을 아직 바인딩하지 않았다면 바인딩합니다. 다음 예제는 [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) 샘플에서 가져온 것입니다. 열을 바인딩하려면를 호출한 `GetColumnInfo` 다음, 다음 예제와 같이 바인딩을 사용 하 여 접근자를 만듭니다.

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. 데이터를 **`while`** 검색 하는 루프를 작성 합니다. 루프에서를 호출 `MoveNext` 하 여 커서를 이동 하 고 다음 예제와 같이 S_OK에 대해 반환 값을 테스트 합니다.

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. 루프 내에서 **`while`** 접근자 형식에 따라 데이터를 페치할 수 있습니다.

   - [CAccessor](../../data/oledb/caccessor-class.md) 클래스를 사용 하는 경우 데이터 멤버를 포함 하는 사용자 레코드가 있어야 합니다. 다음 예제와 같이 해당 데이터 멤버를 사용 하 여 데이터에 액세스할 수 있습니다.

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - 또는 클래스를 사용 하는 경우 `CDynamicAccessor` `CDynamicParameterAccessor` 다음 예제와 같이 액세스 함수 및를 사용 하 여 데이터를 페치할 수 있습니다 `GetValue` `GetColumn` . 사용 중인 데이터 형식을 확인 하려면를 사용 `GetType` 합니다.

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - 를 사용 하 `CManualAccessor` 는 경우 다음 예제와 같이 고유한 데이터 멤버를 지정 하 고 직접 바인딩하고 직접 액세스 해야 합니다.

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)
