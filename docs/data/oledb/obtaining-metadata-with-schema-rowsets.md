---
title: 스키마 행 집합을 사용하여 메타데이터 구하기
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 37418cc91913ed840d1601aab9005b476bf29ee0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508988"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>스키마 행 집합을 사용하여 메타데이터 구하기

행 집합을 열지 않고 공급자, 행 집합, 테이블, 열에 대한 정보나 다른 데이터베이스 정보를 구해야 하는 경우가 있습니다. 데이터베이스 구조에 대한 데이터는 메타데이터라고 하며 다양한 방법으로 검색할 수 있습니다. 한 가지 방법은 스키마 행 집합을 사용하는 것입니다.

OLE DB 템플릿은 스키마 정보를 검색 하는 클래스 집합을 제공 합니다. 이러한 클래스는 미리 정의 된 스키마 행 집합을 만들며 [스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)에 나열 됩니다.

> [!NOTE]
> OLAP를 사용 중이며 일부 행 집합이 스키마 행 집합 클래스에서 지원되지 않는 경우(예: 다양한 수의 열이 있는 경우) `CManualAccessor` 또는 `CDynamicAccessor`를 사용하는 것이 좋습니다. 열을 스크롤하고 case 문을 사용하여 각 열에 대한 가능한 데이터 형식을 처리할 수 있습니다.

## <a name="catalogschema-model"></a>카탈로그/스키마 모델

ANSI SQL은 데이터 저장소에 대한 카탈로그/스키마 모델을 정의합니다. OLE DB는 이 모델을 사용합니다. 이 모델에서 카탈로그 (데이터베이스)에는 스키마와 스키마가 있습니다.

- **카탈로그** 카탈로그는 데이터베이스의 또 다른 이름입니다. 관련 된 스키마의 컬렉션입니다. 지정 된 데이터 원본에 속하는 카탈로그 (데이터베이스)를 나열 하려면 [Ccatalog](./schema-rowset-classes-and-typedef-classes.md#catalog)를 사용 합니다. 많은 데이터베이스에는 하나의 카탈로그만 있으므로 메타 데이터를 스키마 정보 라고도 합니다.

- **스키마** 스키마는 특정 사용자가 소유 하거나 만든 데이터베이스 개체의 컬렉션입니다. 지정 된 사용자가 소유한 스키마를 나열 하려면 [CSchemata](./schema-rowset-classes-and-typedef-classes.md#schemata)을 사용 합니다.

   Microsoft SQL Server 및 ODBC 2.x 측면에서 스키마는 소유자입니다(예: dbo는 일반적인 스키마 이름임). SQL Server는 테이블 집합에 메타데이터를 저장합니다. 한 테이블에는 모든 테이블의 목록이 포함되고, 다른 테이블에는 모든 열의 목록이 포함됩니다. Microsoft Access 데이터베이스에는 스키마에 해당 하는 항목이 없습니다.

- **테이블** 테이블은 특정 순서로 정렬 된 열의 컬렉션입니다. 지정 된 카탈로그 (데이터베이스)에 정의 된 테이블과 해당 테이블에 대 한 정보를 나열 하려면 [Ctables](./schema-rowset-classes-and-typedef-classes.md#table)를 사용 합니다.

## <a name="restrictions"></a>제한

스키마 정보를 쿼리 하는 경우 제한 사항을 사용 하 여 관심 있는 정보 유형을 지정할 수 있습니다. 제한을 쿼리의 필터나 한정자로 생각할 수 있습니다. 예를 들어 다음 쿼리에서

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name`이 제한 사항입니다. 제한 사항이 하나뿐인 간단한 예제입니다. 스키마 행 집합 클래스는 몇 가지 제한 사항을 지원 합니다.

[스키마 행 집합 typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 는 모든 OLE DB 스키마 행 집합을 캡슐화 하 여 다른 행 집합을 인스턴스화하고 열어 스키마 행 집합에 액세스할 수 있도록 합니다. 예를 들어 typedef 클래스 [Ccolumns](./schema-rowset-classes-and-typedef-classes.md#columns) 는 다음과 같이 정의 됩니다.

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md) 클래스는 제한 지원을 제공 합니다. 스키마 행 집합의 인스턴스를 만든 후 [CRestrictions:: Open](./crestrictions-class.md#open)을 호출 합니다. 이 메서드는 지정하는 제한을 기반으로 결과 집합을 반환합니다.

제한을 지정 하려면 [부록 B: 스키마 행 집합](/previous-versions/windows/desktop/ms712921(v=vs.85)) 을 참조 하 고 사용 중인 행 집합을 조회 합니다. 예를 들어 `CColumns` 은 [Columns 행 집합](/previous-versions/windows/desktop/ms723052(v=vs.85))에 해당 합니다 .이 항목은 columns 행 집합: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME의 제한 열을 나열 합니다. 제한을 지정할 때 이 순서를 따라야 합니다.

따라서 예를 들어 테이블 이름으로 제한 하려는 경우 다음 예제와 같이 TABLE_NAME를 호출 하 고, 다음 예제와 같이를 호출 하 여 `Open` 원하는 테이블 이름을 세 번째 제한 매개 변수로 지정 합니다.

### <a name="to-use-schema-rowsets"></a>스키마 행 집합을 사용하려면

1. 헤더 파일을 포함 `Atldbsch.h` `Atldbcli.h` 합니다 (소비자 지원에도 필요).

1. 소비자의 헤더 파일이나 문서의 헤더 파일에서 스키마 행 집합 개체를 인스턴스화합니다. 테이블 정보를 원하는 경우 개체를 선언 `CTables` 합니다. 열 정보를 원하는 경우 개체를 선언 `CColumns` 합니다. 이 예제에서는 authors 테이블의 열을 검색하는 방법을 보여 줍니다.

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. 정보를 가져오려면 스키마 행 집합 개체의 적절한 데이터 멤버에 액세스합니다(예: `ColumnSchemaRowset.m_szColumnName`). 이 데이터 멤버는 COLUMN_NAME에 해당 합니다. 각 데이터 멤버가 해당 하는 OLE DB 열을 확인 하려면 [Ccolumns](./schema-rowset-classes-and-typedef-classes.md#columns)를 참조 하세요.

스키마 행 집합에 대 한 참조 인 경우 OLE DB 템플릿에 제공 된 typedef 클래스 ( [스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)참조).

제한 열을 포함 하 여 OLE DB 스키마 행 집합에 대 한 자세한 내용은 **OLE DB 프로그래머 참조**에서 [부록 B: 스키마 행 집합](/previous-versions/windows/desktop/ms712921(v=vs.85)) 을 참조 하세요.

스키마 행 집합 클래스를 사용 하는 방법에 대 한 더 복잡 한 예제는 [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 및 [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 샘플을 참조 하세요.

스키마 행 집합에 대 한 공급자 지원에 대 한 자세한 내용은 [스키마 행 집합 지원](../../data/oledb/supporting-schema-rowsets.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
