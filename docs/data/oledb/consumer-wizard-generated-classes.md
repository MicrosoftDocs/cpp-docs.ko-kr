---
title: 소비자 마법사 생성 클래스
ms.date: 05/09/2019
helpviewer_keywords:
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
ms.openlocfilehash: 80a43446f0367acb89a04fdaa8198b5cff5a6697
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500970"
---
# <a name="consumer-wizard-generated-classes"></a>소비자 마법사 생성 클래스

::: moniker range="vs-2019"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다.

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB 소비자 마법사** 를 사용 하 여 소비자를 생성 하는 경우 OLE DB 템플릿 또는 OLE DB 특성을 사용 하도록 선택할 수 있습니다. 두 경우 모두 마법사에서 명령 클래스 및 사용자 레코드 클래스를 생성합니다. 명령 클래스는 마법사에서 지정한 데이터 원본 및 행 집합을 여는 코드를 포함합니다. 사용자 레코드 클래스는 선택한 데이터베이스 테이블에 대한 열 맵을 포함합니다. 그러나 생성된 코드는 각각의 경우마다 다릅니다.

- 템플릿 기반 소비자를 선택할 경우 마법사에서 명령 클래스 및 사용자 레코드 클래스를 생성합니다. 명령 클래스는 마법사의 **클래스** 상자에 입력 한 이름을 갖고 (예: `CProducts` ), 사용자 레코드 클래스는 "*ClassName*Accessor" 형식의 이름을 갖습니다 (예: `CProductsAccessor` ). 두 클래스 모두 소비자의 헤더 파일에 배치됩니다.

- 특성 사용 소비자를 선택할 경우 "_*ClassName*Accessor" 형식의 이름을 가진 사용자 레코드 클래스가 삽입됩니다. 즉, 명령 클래스만 텍스트 편집기에서 볼 수 있고 사용자 레코드 클래스는 삽입된 코드로만 볼 수 있습니다. 삽입된 코드를 보는 방법에 대한 자세한 내용은 [삽입된 코드 디버그](/visualstudio/debugger/how-to-debug-injected-code)를 참조하세요.

다음 예제에서는 `Northwind` 데이터베이스의 `Products` 테이블에 생성된 명령 클래스를 사용하여 명령 클래스 및 사용자 레코드 클래스에 대한 마법사 생성 소비자 코드를 보여 줍니다.

## <a name="templated-user-record-classes"></a>템플릿 기반 사용자 레코드 클래스

OLE DB 템플릿(OLE DB 특성 아님)을 사용하여 OLE DB 소비자를 만드는 경우 마법사는 이 섹션에 설명된 대로 코드를 생성합니다.

### <a name="column-data-members"></a>열 데이터 멤버

사용자 레코드 클래스의 첫 번째 부분에는 데이터 멤버 선언과 데이터 바인딩된 각 열의 상태 및 길이 데이터 멤버가 포함됩니다. 이러한 데이터 멤버에 대한 자세한 내용은 [마법사 생성 접근자의 필드 상태 데이터 멤버](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)를 참조하세요.

> [!NOTE]
> 사용자 레코드 클래스를 수정하거나 사용자 고유의 소비자를 작성하는 경우 데이터 변수가 상태 및 길이 변수 앞에 와야 합니다.

> [!NOTE]
> ATL OLE DB 소비자 마법사는 `DB_NUMERIC` 형식을 사용하여 숫자 데이터 형식을 바인딩합니다. 이전에는 `DBTYPE_VARNUMERIC`(`DB_VARNUMERIC` 형식에서 형식 설명, Oledb.h 참조)을 사용했습니다. 소비자를 만드는 데 마법사를 사용하지 않는 경우 `DB_NUMERIC`을 사용하는 것이 좋습니다.

```cpp
// Products.H : Declaration of the CProducts class

class CProductsAccessor
{
public:
   // Column data members:
   LONG m_ProductID;
   TCHAR m_ProductName[41];
   LONG m_SupplierID;
   LONG m_CategoryID;
   TCHAR m_QuantityPerUnit[21];
   CURRENCY m_UnitPrice;
   SHORT m_UnitsInStock;
   SHORT m_UnitsOnOrder;
   SHORT m_ReorderLevel;
   VARIANT_BOOL m_Discontinued;

   // Column status data members:
   DBSTATUS m_dwProductIDStatus;
   DBSTATUS m_dwProductNameStatus;
   DBSTATUS m_dwSupplierIDStatus;
   DBSTATUS m_dwCategoryIDStatus;
   DBSTATUS m_dwQuantityPerUnitStatus;
   DBSTATUS m_dwUnitPriceStatus;
   DBSTATUS m_dwUnitsInStockStatus;
   DBSTATUS m_dwUnitsOnOrderStatus;
   DBSTATUS m_dwReorderLevelStatus;
   DBSTATUS m_dwDiscontinuedStatus;

   // Column length data members:
   DBLENGTH m_dwProductIDLength;
   DBLENGTH m_dwProductNameLength;
   DBLENGTH m_dwSupplierIDLength;
   DBLENGTH m_dwCategoryIDLength;
   DBLENGTH m_dwQuantityPerUnitLength;
   DBLENGTH m_dwUnitPriceLength;
   DBLENGTH m_dwUnitsInStockLength;
   DBLENGTH m_dwUnitsOnOrderLength;
   DBLENGTH m_dwReorderLevelLength;
   DBLENGTH m_dwDiscontinuedLength;
```

### <a name="rowset-properties"></a>행 집합 속성

다음에는 마법사에서 행 집합 속성을 설정합니다. ATL OLE DB 소비자 마법사에서 **변경**, **삽입**또는 **삭제** 를 선택한 경우 여기서 해당 속성이 설정됩니다(DBPROP_IRowsetChange는 항상 설정되고 DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT 및/또는 DBPROPVAL_UP_DELETE 중 하나 이상이 각각 설정됨).

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>명령 또는 테이블 클래스

명령 클래스를 지정하면 마법사에서 명령 클래스를 선언합니다. 템플릿 기반 코드의 경우 명령은 다음과 같습니다.

```cpp
DEFINE_COMMAND_EX(CProductsAccessor, L" \
SELECT \
   ProductID, \
   ProductName, \
   SupplierID, \
   CategoryID, \
   QuantityPerUnit, \
   UnitPrice, \
   UnitsInStock, \
   UnitsOnOrder, \
   ReorderLevel, \
   Discontinued \
   FROM dbo.Products")
```

### <a name="column-map"></a>열 맵

그런 후에 마법사는 열 바인딩 또는 열 맵을 생성합니다. 일부 공급자에서 발생하는 몇 가지 문제를 해결하기 위해 다음 코드는 공급자에서 보고한 순서와 다른 순서로 열을 바인딩할 수 있습니다.

```cpp
   BEGIN_COLUMN_MAP(CProductsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))
   END_COLUMN_MAP()
};
```

### <a name="class-declaration"></a>클래스 선언

마지막으로, 마법사는 다음과 같은 명령 클래스 선언을 생성합니다.

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>특성 삽입 사용자 레코드 클래스

데이터베이스 특성([db_command](../../windows/attributes/db-command.md) 또는 [db_table](../../windows/attributes/db-table.md))을 사용하여 OLE DB 소비자를 만드는 경우 특성은 "_*ClassName*Accessor" 형식의 이름으로 사용자 레코드 클래스를 삽입합니다. 예를 들어 명령 클래스의 이름을 `COrders`로 지정한 경우 사용자 레코드 클래스는 `_COrdersAccessor`가 됩니다. 사용자 레코드 클래스가 **클래스 뷰**에 표시 되기는 하지만 두 번 클릭 하면 헤더 파일의 명령 또는 테이블 클래스로 이동 합니다. 이 경우 특성 삽입 코드를 통해서만 사용자 레코드 클래스의 실제 선언을 볼 수 있습니다.

특성 사용 소비자에서 메서드를 추가하거나 재정의하는 경우 문제가 발생할 수 있습니다. 예를 들어 `_COrdersAccessor` 선언에 `COrders` 생성자를 추가할 수 있지만 실제로는 삽입된 `COrdersAccessor` 클래스에 생성자가 추가됩니다. 이러한 생성자는 열/매개 변수를 초기화할 수 있지만 `COrdersAccessor` 개체를 직접 인스턴스화할 수 없기 때문에 이런 방식으로 복사 생성자를 만들 수 없습니다. `COrders` 클래스에 직접 생성자(또는 다른 메서드)가 필요한 경우 `COrders`에서 파생되는 새 클래스를 정의하고 여기에 필요한 메서드를 추가하는 것이 좋습니다.

다음 예제에서는 마법사가 `COrders` 클래스 선언을 생성하지만 사용자 레코드 클래스 `COrdersAccessor`가 특성을 통해 삽입되기 때문에 표시되지 않습니다.

```cpp
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>
[
   db_source(L"your connection string"),
   db_command(L"Select ShipName from Orders;")
]
class COrders
{
public:

   // COrders()            // incorrect constructor name
   _COrdersAccessor()      // correct constructor name
   {
   }
      [db_column(1) ] TCHAR m_ShipName[41];
   };
```

삽입된 명령 클래스 선언은 다음과 같습니다.

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

삽입된 코드의 대부분은 템플릿 기반 버전과 유사하거나 동일합니다. 주요 차이점은 [소비자 마법사 생성 메서드](../../data/oledb/consumer-wizard-generated-methods.md)에서 설명하는 삽입된 메서드에 있습니다.

삽입된 코드를 보는 방법에 대한 자세한 내용은 [삽입된 코드 디버그](/visualstudio/debugger/how-to-debug-injected-code)를 참조하세요.

::: moniker-end

## <a name="see-also"></a>참고 항목

[마법사를 사용 하 여 OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
