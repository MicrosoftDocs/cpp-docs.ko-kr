---
description: '자세한 정보: 데이터베이스 특성을 사용 하 여 데이터 액세스 간소화'
title: 데이터베이스 특성을 사용하여 데이터 액세스 단순화
ms.date: 10/19/2018
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
ms.openlocfilehash: e265c6f59340afb86fdd59c86f78951b9e7cd0df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286490"
---
# <a name="simplifying-data-access-with-database-attributes"></a>데이터베이스 특성을 사용하여 데이터 액세스 단순화

이 항목에서는 데이터베이스 특성을 사용 하 여 데이터베이스 작업을 간소화 하는 방법을 보여 줍니다.

데이터베이스의 정보에 액세스 하는 기본적인 방법은 데이터베이스의 특정 테이블에 대 한 명령 (또는 테이블) 클래스 및 사용자 레코드 클래스를 만드는 것입니다. 데이터베이스 특성은 이전에 수행한 템플릿 선언 중 일부를 단순화 합니다.

데이터베이스 특성을 사용 하는 방법을 보여 주기 위해 다음 섹션에서는 두 개의 동일한 테이블 및 사용자 레코드 클래스 선언을 보여 줍니다. 첫 번째 사용 특성 및 두 번째는 OLE DB 템플릿을 사용 합니다. 이러한 선언 코드는 일반적으로 테이블 또는 명령 개체에 대 한 헤더 파일 (예: Authors. h)에 배치 됩니다.

두 파일을 비교 하 여 특성을 사용 하는 것이 얼마나 간단한 지 확인할 수 있습니다. 차이점은 다음과 같습니다.

- 특성을 사용 하 여 하나의 클래스만 선언 하면 됩니다. 단 `CAuthors` , 템플릿을 사용 하는 경우 두 개의 및를 선언 해야 `CAuthorsNoAttrAccessor` `CAuthorsNoAttr` 합니다.

- `db_source`특성을 사용 하는 버전의 호출은 `OpenDataSource()` 템플릿 선언에서 호출 하는 것과 같습니다.

- `db_table`특성 사용 버전의 호출은 다음 템플릿 선언과 동일 합니다.

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- 특성을 사용 하는 `db_column` 버전의 호출은 템플릿 선언의 열 맵 (참조)과 동일 합니다 `BEGIN_COLUMN_MAP ... END_COLUMN_MAP` .

특성은 사용자 레코드 클래스 선언을 삽입 합니다. 사용자 레코드 클래스는 `CAuthorsNoAttrAccessor` 템플릿 선언에서와 같습니다. 테이블 클래스가 인 경우 `CAuthors` 삽입 된 사용자 레코드 클래스의 이름은 이며 `CAuthorsAccessor` 삽입 된 코드 에서만 해당 선언을 볼 수 있습니다. 자세한 내용은 [사용자 레코드](../../data/oledb/user-records.md)에서 "특성 삽입 사용자 레코드 클래스"를 참조 하십시오.

특성 사용 및 템플릿 기반 코드 모두에서를 사용 하 여 행 집합 속성을 설정 해야 합니다 `CDBPropSet::AddProperty` .

이 항목에서 설명 하는 특성에 대 한 자세한 내용은 [OLE DB Consumer attributes](../../windows/attributes/ole-db-consumer-attributes.md)를 참조 하십시오.

> [!NOTE]
> `include`아래 예제를 컴파일하려면 다음 문이 필요 합니다.

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>특성을 사용 하는 테이블 및 접근자 선언

다음 코드에서는 `db_source` `db_table` 테이블 클래스에 대해 및를 호출 합니다. `db_source` 사용할 데이터 원본 및 연결을 지정 합니다. `db_table` 테이블 클래스를 선언 하는 데 적합 한 템플릿 코드를 삽입 합니다. `db_column` 열 맵을 지정 하 고 접근자 선언을 삽입 합니다. ATL을 지 원하는 모든 프로젝트에서 OLE DB 소비자 특성을 사용할 수 있습니다.

다음은 특성을 사용 하는 테이블 및 접근자 선언입니다.

```cpp
//////////////////////////////////////////////////////////////////////
// Table and accessor declaration using attributes
// authors.h
//////////////////////////////////////////////////////////////////////

// Table class declaration
// (Note that you must provide your own connection string for db_source.)
[
   db_source(L"your connection string"),
   db_table("Authors")
]
class CAuthors
{
public:
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>템플릿을 사용 하 여 테이블 및 접근자 선언

다음은 템플릿을 사용한 테이블 및 접근자 선언입니다.

```cpp
//////////////////////////////////////////////////////////////////////
// Table and user record class declaration using templates
// authors.h
//////////////////////////////////////////////////////////////////////

// User record class declaration
class CAuthorsNoAttrAccessor
{
public:
   DWORD m_dwAuIDStatus;
   DWORD m_dwAuthorStatus;
   DWORD m_dwYearBornStatus;
   DWORD m_dwAuIDLength;
   DWORD m_dwAuthorLength;
   DWORD m_dwYearBornLength;
   LONG m_AuID;
   TCHAR m_Author[51];
   SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
   HRESULT OpenDataSource()
   {
      CDataSource _db;

HRESULT hr;
      hr = _db.OpenFromInitializationString(L"your connection string");
      if (FAILED(hr))
      {
#ifdef _DEBUG
         AtlTraceErrorRecords(hr);
#endif
         return hr;
      }
      return m_session.Open(_db);
   }
   void CloseDataSource()
   {
      m_session.Close();
   }
   operator const CSession&()
   {
      return m_session;
   }
   CSession m_session;
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)
   END_COLUMN_MAP()
};
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
{
public:
   HRESULT OpenAll()
   {
HRESULT hr;
      hr = OpenDataSource();
      if (FAILED(hr))
         return hr;
      __if_exists(GetRowsetProperties)
      {
         CDBPropSet propset(DBPROPSET_ROWSET);
         __if_exists(HasBookmark)
         {
            propset.AddProperty(DBPROP_IRowsetLocate, true);
         }
         GetRowsetProperties(&propset);
         return OpenRowset(&propset);
      }
      __if_not_exists(GetRowsetProperties)
      {
         __if_exists(HasBookmark)
         {
            CDBPropSet propset(DBPROPSET_ROWSET);
            propset.AddProperty(DBPROP_IRowsetLocate, true);
            return OpenRowset(&propset);
         }
      }
      return OpenRowset();
   }
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
   {
HRESULT hr = Open(m_session, "Authors", pPropSet);
#ifdef _DEBUG
      if(FAILED(hr))
         AtlTraceErrorRecords(hr);
#endif
      return hr;
   }
   void CloseAll()
   {
      Close();
      CloseDataSource();
   }
};
```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 특성](../../windows/attributes/ole-db-consumer-attributes.md)
