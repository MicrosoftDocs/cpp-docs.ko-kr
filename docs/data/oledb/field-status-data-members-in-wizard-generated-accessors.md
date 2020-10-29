---
title: 마법사 생성 접근자의 필드 상태 데이터 멤버
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 476c91f55071f6d1c7f243257273a32798813cae
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924636"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>마법사 생성 접근자의 필드 상태 데이터 멤버

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

::: moniker-end

::: moniker range="<=msvc-150"

**ATL OLE DB 소비자 마법사** 를 사용하여 소비자를 만드는 경우, 열 맵에 지정한 각 필드에 대한 데이터 멤버가 사용자 레코드 클래스에 생성됩니다. 각 데이터 멤버는 `DWORD` 형식이며, 해당 필드의 상태 값을 포함합니다.

예를 들어 데이터 멤버 *m_OwnerID* 의 경우 필드 상태에 대한 추가 데이터 멤버( *dwOwnerIDStatus* )와 필드 길이에 대한 다른 데이터 멤버( *dwOwnerIDLength* )가 생성됩니다. 또한 COLUMN_ENTRY_LENGTH_STATUS 항목을 사용하여 열 맵이 생성됩니다.

이 작업은 다음 코드에서 확인할 수 있습니다.

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

   DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
   SELECT \
      AuID, \
      Author, \
      YearBorn \
      FROM dbo.Authors")

   BEGIN_COLUMN_MAP(CAuthorsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
   END_COLUMN_MAP()
...
```

> [!NOTE]
> 사용자 레코드 클래스를 수정하거나 사용자 고유의 소비자를 작성하는 경우 데이터 변수가 상태 및 길이 변수 앞에 와야 합니다.

디버깅 목적으로 상태 값을 사용할 수 있습니다. **ATL OLE DB 소비자 마법사** 에서 생성된 코드가 DB_S_ERRORSOCCURRED, DB_E_ERRORSOCCURRED 등의 컴파일 오류를 생성하는 경우 필드 상태 데이터 멤버의 현재 값을 먼저 확인해야 합니다. 값이 0이 아닌 데이터 멤버는 위반 열에 해당합니다.

상태 값을 사용하여 특정 필드에 NULL 값을 설정할 수도 있습니다. 이렇게 하면 필드 값을 0이 아닌 NULL로 구분하려는 경우에 도움이 됩니다. NULL이 유효한 값인지 또는 특수 값인지 여부와 애플리케이션에서 NULL을 처리하는 방법을 결정해야 합니다. OLE DB에서는 제네릭 NULL 값을 지정하는 올바른 수단으로 DBSTATUS_S_ISNULL을 정의합니다. 소비자가 데이터를 읽고 값이 Null이면 상태 필드가 DBSTATUS_S_ISNULL로 설정됩니다. 소비자가 NULL 값을 설정하려는 경우 공급자를 호출하기 전에 상태 값을 DBSTATUS_S_ISNULL로 설정합니다.

다음으로, Oledb.h를 열고 DBSTATUSENUM을 검색합니다. DBSTATUSENUM 열거형 값과 0이 아닌 상태의 숫자 값을 일치시킬 수 있습니다. 열거형 이름을 통해 오류를 확인할 수 없는 경우 [OLE DB 프로그래머 가이드](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)의 **데이터 값 바인딩** 섹션에서 **상태** 항목을 참조하세요. 이 항목에는 데이터를 가져오거나 설정할 때 사용되는 상태 값 표가 포함되어 있습니다. 길이 값에 대한 자세한 내용은 동일한 섹션의 **길이** 항목을 참조하세요.

## <a name="retrieving-the-length-or-status-of-a-column"></a>열의 길이 또는 상태 검색

가변 길이 열의 길이 또는 열의 상태(예: DBSTATUS_S_ISNULL 확인)를 검색할 수 있습니다.

- 길이를 가져오려면 COLUMN_ENTRY_LENGTH 매크로를 사용합니다.

- 상태를 가져오려면 COLUMN_ENTRY_STATUS 매크로를 사용합니다.

- 둘 다 가져오려면 다음과 같이 COLUMN_ENTRY_LENGTH_STATUS를 사용합니다.

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- 그런 후에 다음과 같이 길이 및 상태에 액세스합니다.

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

`CDynamicAccessor`를 사용하면 길이와 상태가 자동으로 바인딩됩니다. 길이 및 상태 값을 검색하려면 `GetLength` 및 `GetStatus` 멤버 함수를 사용합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)
