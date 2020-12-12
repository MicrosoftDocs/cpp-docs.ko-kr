---
description: '자세히 알아보기: 소비자 Wizard-Generated 메서드'
title: 소비자 마법사 생성 메서드
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 29d586a46f91e9244a09fce5628d0f3b274c554c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323289"
---
# <a name="consumer-wizard-generated-methods"></a>소비자 마법사 생성 메서드

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다.

::: moniker-end

::: moniker range="<=msvc-150"

**ATL OLE DB 소비자 마법사** 및 **MFC 애플리케이션 마법사** 는 특정 함수를 생성하며, 이러한 함수에 대해 알고 있어야 합니다. 일부 메서드는 특성 사용 프로젝트에서 다르게 구현되므로 몇 가지 주의할 사항이 있습니다. 아래에서 각각의 경우에 대해 설명합니다. 삽입된 코드를 보는 방법에 대한 자세한 내용은 [삽입된 코드 디버그](/visualstudio/debugger/how-to-debug-injected-code)를 참조하세요.

- `OpenAll` - 데이터 소스와 행 집합을 열고, 사용 가능한 경우 책갈피를 켭니다.

- `CloseAll` - 열려 있는 행 집합을 모두 닫고, 모든 명령 실행을 해제합니다.

- `OpenRowset` - `OpenAll`에서 하나 이상의 소비자 행 집합을 열기 위해 호출됩니다.

- `GetRowsetProperties` - 속성 설정에 사용할 수 있는 행 집합의 속성 집합에 대한 포인터를 검색합니다.

- `OpenDataSource` - **데이터 연결 속성** 대화 상자에서 지정한 초기화 문자열을 사용하여 데이터 소스를 엽니다.

- `CloseDataSource` - 데이터 소스를 적절한 방식으로 닫습니다.

## <a name="openall-and-closeall"></a>OpenAll 및 CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

다음 예제에서는 동일한 명령을 반복해서 실행할 때 `OpenAll` 및 `CloseAll`을 호출할 수 있는 방법을 보여 줍니다. `CloseAll` 대신 `Close` 및 `ReleaseCommand`를 호출하는 변형을 보여 주는 [CCommand::Close](./ccommand-class.md#close)의 코드 예제와 비교합니다.

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>설명

`HasBookmark` 메서드를 정의하는 경우 `OpenAll` 코드에서 `DBPROP_IRowsetLocate` 속성을 설정합니다. 공급자가 해당 속성을 지원하는 경우에만 이 작업을 수행합니다.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll`은 이 메서드를 호출하여 소비자에서 하나 이상의 행 집합을 엽니다. 일반적으로, 여러 데이터 소스/세션/행 집합을 사용하려는 경우가 아니면 `OpenRowset`를 호출할 필요가 없습니다. `OpenRowset`는 명령 또는 테이블 클래스 헤더 파일에서 선언합니다.

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

특성은 이 메서드를 다르게 구현합니다. 이 버전에서는 세션 개체와 명령 문자열을 사용합니다. 명령 문자열은 기본적으로 db_command에 지정된 명령 문자열로 설정되지만, 다른 명령 문자열을 전달할 수 있습니다. `HasBookmark` 메서드를 정의하는 경우 `OpenRowset` 코드에서 `DBPROP_IRowsetLocate` 속성을 설정합니다. 공급자가 해당 속성을 지원하는 경우에만 이 작업을 수행합니다.

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

이 메서드는 행 집합의 속성 집합에 대한 포인터를 검색합니다. 이 포인터를 사용하여 `DBPROP_IRowsetChange` 등의 속성을 설정할 수 있습니다. `GetRowsetProperties`는 사용자 레코드 클래스에서 다음과 같이 사용됩니다. 이 코드를 수정하여 추가적인 행 집합 속성을 설정할 수 있습니다.

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>설명

전역 `GetRowsetProperties` 메서드는 마법사에서 정의된 메서드와 충돌할 수 있으므로 정의하면 안 됩니다. 템플릿 및 특성 사용 프로젝트에서 제공되는 메서드는 마법사 생성 메서드입니다. 특성은 이 코드를 삽입하지 않습니다.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 및 CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>설명

마법사에서는 `OpenDataSource` 및 `CloseDataSource` 메서드를 정의합니다. `OpenDataSource`는 [CDataSource::OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring)을 호출합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[마법사를 사용 하 여 OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
