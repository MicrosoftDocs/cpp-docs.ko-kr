---
title: 행 집합 업데이트
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: 134ab73428b7535bb34094b7d5b1952fd61a3d69
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509447"
---
# <a name="updating-rowsets"></a>행 집합 업데이트

기본 데이터베이스 작업은 데이터 저장소를 업데이트하거나 데이터 저장소에 데이터를 쓰는 것입니다. OLE DB에서 업데이트 메커니즘은 간단합니다. 소비자 애플리케이션이 바인딩된 데이터 멤버의 값을 설정하고 행 집합에 해당 값을 쓴 다음 소비자가 공급자에게 데이터 저장소를 업데이트하도록 요청합니다.

소비자는 행 내의 열 값 설정, 행 삽입, 행 삭제 등의 업데이트를 행 집합 데이터에서 완료할 수 있습니다. 이러한 작업을 완료하기 위해 OLE DB 템플릿 클래스 [CRowset](../../data/oledb/crowset-class.md)는 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 인터페이스를 구현하고 다음 인터페이스 메서드를 재정의합니다.

- [SetData](./crowset-class.md#setdata)는 행 집합의 한 행에서 열 값을 변경하며, SQL UPDATE 명령과 같습니다.

- [Insert](./crowset-class.md#insert)는 행 집합에 한 행을 삽입하며, SQL INSERT 명령과 같습니다.

- [Delete](./crowset-class.md#delete)는 행 집합에서 행을 삭제하며, SQL DELETE 명령과 같습니다.

## <a name="supporting-update-operations"></a>업데이트 작업 지원

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

**ATL OLE DB 소비자 마법사**를 사용 하 여 소비자를 만드는 경우 **변경**, **삽입**및 **삭제**의 세 확인란 중 하나 이상을 선택 하 여 업데이트 작업을 지원할 수 있습니다. 이러한 옵션을 선택하면, 선택한 변경 유형을 지원하도록 코드가 적절하게 수정됩니다. 그러나 마법사를 사용하지 않는 경우 업데이트를 지원하려면 다음 행 집합 속성을 `VARIANT_TRUE`로 설정해야 합니다.

- `DBPROPVAL_UP_CHANGE`를 사용하면 한 행의 데이터 값을 변경할 수 있습니다.

- `DBPROPVAL_UP_INSERT`를 사용하면 한 행을 삽입할 수 있습니다.

- `DBPROPVAL_UP_DELETE`를 사용하면 한 행을 삭제할 수 있습니다.

속성을 다음과 같이 설정합니다.

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

하나 이상의 열이 쓰기 가능하지 않으면 변경, 삽입 또는 삭제 작업이 실패할 수 있습니다. 이 문제를 해결하려면 커서 맵을 수정합니다.

## <a name="setting-data-in-rows"></a>행의 데이터 설정

[Crowset:: Setdata](./crowset-class.md#setdata) 는 현재 행의 하나 이상 열에 데이터 값을 설정합니다. 다음 코드에서는 `Products` 테이블의 `Name` 및 `Units in Stock` 열에 바인딩된 데이터 멤버의 값을 설정하고 `SetData`를 호출하여 행 집합의 100번째 행에 해당 값을 씁니다.

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>행 집합에 행 삽입

[Crowset:: Insert](./crowset-class.md#insert) 는 접근자의 데이터를 사용하여 새 행을 만들고 초기화합니다. `Insert`는 현재 행 뒤에 완전히 새로운 행을 만듭니다. 현재 행을 다음 행으로 증가할지 또는 변경하지 않고 그대로 유지할지를 지정해야 합니다. 이렇게 하려면 *bGetRow* 매개 변수를 설정합니다.

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **`false`** 기본값은 현재 행이 다음 행으로 증가 하도록 지정 합니다 .이 경우 삽입 된 행을 가리킵니다.

- **`true`** 현재 행이 그대로 유지 되도록 지정 합니다.

다음 코드에서는 `Products` 테이블의 열에 바인딩된 데이터 멤버의 값을 설정하고 `Insert`를 호출하여 행 집합의 100번째 행 뒤에 해당 값으로 새 행을 삽입합니다. 새 행에 정의되지 않은 데이터가 포함되지 않도록 모든 열 값을 설정하는 것이 좋습니다.

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

자세한 예제는 [CRowset::Insert](./crowset-class.md#insert)를 참조하세요.

상태 및 길이 데이터 멤버를 설정하는 방법에 대한 자세한 내용은 [마법사 생성 접근자의 필드 상태 데이터 멤버](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)를 참조하세요.

## <a name="deleting-rows-from-rowsets"></a>행 집합에서 행 삭제

[Crowset:: Delete](./crowset-class.md#delete) 는 행 집합에서 현재 행을 삭제합니다. 다음 코드에서는 `Delete`를 호출하여 행 집합의 100번째 행을 제거합니다.

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>즉시 업데이트 및 지연된 업데이트

달리 지정하지 않은 경우 `SetData`, `Insert` 및 `Delete` 메서드를 호출하면 데이터 저장소가 즉시 업데이트됩니다. 그러나 소비자가 모든 변경 내용을 로컬 캐시에 저장한 후 다음 업데이트 메서드 중 하나가 호출될 때 데이터 저장소에 전송하도록 업데이트를 연기할 수 있습니다.

- [Crowset::Update](./crowset-class.md#update)는 마지막 페치 또는 `Update` 호출 이후 현재 행의 보류 중인 변경 내용을 모두 전송합니다.

- [Crowset::UpdateAll](./crowset-class.md#updateall)은 마지막 페치 또는 `Update` 호출 이후 모든 행의 보류 중인 변경 내용을 모두 전송합니다.

update 메서드에서 사용되는 업데이트는 명령을 변경하는 특별한 의미가 있으며 SQL **UPDATE** 명령과 혼동해서는 안 됩니다(`SetData`가 SQL **UPDATE** 명령과 같음).

지연된 업데이트는 일련의 뱅킹 트랜잭션과 같은 상황에서 유용합니다. 마지막 트랜잭션이 커밋되기 전에는 일련의 변경 내용을 보내지 않으므로 한 트랜잭션이 취소될 경우 변경 내용을 취소할 수 있습니다. 또한 공급자는 보다 효율적으로 변경 내용을 하나의 네트워크 호출에 포함할 수 있습니다.

지연된 업데이트를 지원하려면 **업데이트 작업 지원**에 설명된 속성과 함께 `DBPROP_IRowsetChange` 속성도 설정해야 합니다.

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

`Update` 또는 `UpdateAll`을 호출할 경우 메서드는 로컬 캐시의 변경 내용을 데이터 저장소로 전송한 다음, 로컬 캐시를 지웁니다. 업데이트는 현재 행에 대해서만 변경 내용을 전송하기 때문에 애플리케이션에서 업데이트할 행과 업데이트 시기를 추적하는 것이 중요합니다. 다음 예제에서는 두 개의 연속 행을 업데이트하는 방법을 보여 줍니다.

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

보류 중인 변경 내용을 전송하려면 다른 행으로 이동하기 전에 `Update`를 호출해야 합니다. 그러나 이 작업이 길거나 비효율적인 경우(예: 애플리케이션에서 수백 개의 행을 업데이트해야 하는 경우) `UpdateAll` 을 사용하여 한 번에 모든 행을 업데이트할 수 있습니다.

예를 들어 위의 코드에서 첫 번째 `Update` 호출을 누락하면 100행은 변경되지 않지만 101행은 변경됩니다. 이후에 해당 행을 업데이트하려면 애플리케이션에서 `UpdateAll`을 호출하거나, 100행으로 돌아가서 `Update`를 호출해야 합니다.

마지막으로, 변경 내용을 연기하는 주요 이유는 변경 내용을 취소할 수 있기 때문입니다. [CRowset::Undo](./crowset-class.md#undo) 를 호출하면 로컬 변경 캐시의 상태가 보류 중인 변경 전의 데이터 저장소 상태로 롤백됩니다. `Undo`는 로컬 캐시의 상태를 한 단계(최신 변경 바로 이전 상태) 롤백하는 대신에 해당 행의 로컬 캐시를 지웁니다. 또한 `Undo`는 현재 행에만 영향을 줍니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 클래스](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
