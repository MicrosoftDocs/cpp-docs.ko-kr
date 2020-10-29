---
title: 단순 소비자 구현
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 2d59989f8afd180b39153eed1ad0a20435aad9d4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923908"
---
# <a name="implementing-a-simple-consumer"></a>단순 소비자 구현

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

::: moniker-end

::: moniker range="<=msvc-150"

다음 항목에서는 **MFC 애플리케이션 마법사** 및 **ATL OLE DB 소비자 마법사** 를 통해 만든 파일을 편집하여 간단한 소비자를 만드는 방법을 보여 줍니다. 이 예제는 다음 부분으로 이루어져 있습니다.

- [소비자를 사용하여 데이터 검색](#retrieve)에서는 데이터베이스 테이블의 모든 데이터를 행 단위로 읽는 코드를 소비자에 구현하는 방법을 보여 줍니다.

- [소비자에 책갈피 지원 추가](#bookmark)에서는 소비자에 책갈피 지원을 추가하는 방법을 보여 줍니다.

> [!NOTE]
> 이 섹션에 설명된 소비자 애플리케이션을 사용하여 `MyProv` 및 `Provider` 샘플 공급자를 테스트할 수 있습니다.

> [!NOTE]
> `MyProv`([단순한 읽기 전용 공급자의 기능 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md)에 설명된 공급자와 같음)를 테스트할 소비자 애플리케이션을 빌드하려면 [소비자에 책갈피 지원 추가](#bookmark)에 설명된 대로 책갈피 지원을 포함해야 합니다.

## <a name="retrieving-data-with-the-consumer"></a><a name="retrieve" ></a> 소비자를 사용하여 데이터 검색

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>OLE DB 소비자를 사용하도록 콘솔 애플리케이션을 수정하려면 다음을 수행합니다.

1. `MyCons.cpp`에서 다음과 같이 굵은 텍스트를 삽입하여 주 코드를 변경합니다.

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="adding-bookmark-support-to-the-consumer"></a><a name="bookmark" ></a> 소비자에 책갈피 지원 추가

책갈피는 테이블에서 행을 고유하게 식별하는 열입니다. 일반적으로 키 열이지만 항상 그런 것은 아니며, 공급자별로 다릅니다. 이 섹션에서는 책갈피 지원을 추가하는 방법을 보여 줍니다. 책갈피 지원을 추가하려면 사용자 레코드 클래스에서 다음 단계를 수행해야 합니다.

- 책갈피를 인스턴스화합니다. [CBookmark](../../data/oledb/cbookmark-class.md) 형식의 개체입니다.

- `DBPROP_IRowsetLocate` 속성을 설정하여 공급자의 책갈피 열을 요청합니다.

- [BOOKMARK_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#bookmark_entry) 매크로를 사용하여 열 맵에 책갈피 항목을 추가합니다.

이전 단계에서는 책갈피 지원과 사용할 책갈피 개체를 제공합니다. 이 코드 예제에서는 다음과 같이 책갈피를 보여 줍니다.

- 파일을 쓰기용으로 엽니다.

- 행 집합 데이터를 파일에 행 단위로 출력합니다.

- [MoveToBookmark](./crowset-class.md#movetobookmark)를 호출하여 행 집합 커서를 책갈피로 이동합니다.

- 책갈피가 지정된 행을 출력하고 파일의 끝에 추가합니다.

> [!NOTE]
> 이 소비자 애플리케이션을 사용하여 `Provider` 샘플 공급자 애플리케이션을 테스트하는 경우 이 섹션에 설명된 책갈피 지원을 생략합니다.

### <a name="to-instantiate-the-bookmark"></a>책갈피를 인스턴스화하려면 다음을 수행합니다.

1. 접근자가 [CBookmark](../../data/oledb/cbookmark-class.md) 형식의 개체를 보유해야 합니다. *nSize* 매개 변수는 책갈피 버퍼의 크기를 바이트 단위로 지정합니다(일반적으로 32비트 플랫폼은 4바이트, 64비트 플랫폼은 8바이트임). 사용자 레코드 클래스의 열 데이터 멤버에 다음 선언을 추가합니다.

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>공급자의 책갈피 열을 요청하려면 다음을 수행합니다.

1. 사용자 레코드 클래스의 `GetRowsetProperties` 메서드에 다음 코드를 추가합니다.

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>열 맵에 책갈피 항목을 추가하려면 다음을 수행합니다.

1. 사용자 레코드 클래스의 열 맵에 다음 항목을 추가합니다.

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>주 코드에서 책갈피를 사용하려면 다음을 수행합니다.

1. 이전에 만든 콘솔 애플리케이션의 `MyCons.cpp` 파일에서 주 코드를 다음과 같이 변경합니다. 책갈피를 사용하려면 주 코드에서 자체 책갈피 개체(`myBookmark`)를 인스턴스화해야 합니다. 이 책갈피는 접근자의 책갈피(`m_bookmark`)와 다릅니다.

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

책갈피에 대한 자세한 내용은 [책갈피 사용](../../data/oledb/using-bookmarks.md)을 참조하세요. 책갈피 예제는 [행 집합 업데이트](../../data/oledb/updating-rowsets.md)에도 나와 있습니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[마법사를 사용 하 여 OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
