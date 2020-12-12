---
description: '자세히 알아보기: 매개 변수가 있는 쿼리 실행'
title: 매개 변수가 있는 쿼리 실행
ms.date: 10/19/2018
helpviewer_keywords:
- parameter queries, running using CCommand class
ms.assetid: aedb0fce-52a4-4c97-a5c9-b2114be6c3b0
ms.openlocfilehash: 2d3f03a359fe3ce079239fdcb9603b2d30299c33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317235"
---
# <a name="issuing-a-parameterized-query"></a>매개 변수가 있는 쿼리 실행

다음 예에서는 Microsoft Access 데이터베이스의 테이블에서 age 필드가 30 보다 큰 레코드를 검색 하는 매개 변수가 있는 단순 쿼리를 실행 합니다. 매개 변수를 지원 하려면 사용자 레코드에 추가 맵이 있어야 합니다. 다음 코드는 ATL 프로젝트에서 `CCommand` 앞의 예제에서 사용 된 클래스 대신 클래스를 사용 하 여 `CTable` [간단한 행 집합을 트래버스](../../data/oledb/traversing-a-simple-rowset.md)합니다.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CCommand<CAccessor<CArtists>> artists;
    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    // Set the parameter for the query
    artists.m_nAge = 30;
    artists.Open(session, "select * from artists where age > ?");

    // Get data from the rowset
    while (artists.MoveNext() == S_OK)
    {
        cout << artists.m_szFirstName;
        cout << artists.m_szLastName;
    }

    return 0;
}
```

사용자 레코드는 `CArtists` 다음 예제와 같습니다.

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)
