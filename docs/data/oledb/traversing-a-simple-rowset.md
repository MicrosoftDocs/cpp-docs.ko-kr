---
description: '자세한 정보: 간단한 행 집합 트래버스'
title: 단순 행 집합 검색
ms.date: 10/19/2018
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
ms.openlocfilehash: f2e0c1f9647e168d8de2a10eaea6425bf9ad5a88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272632"
---
# <a name="traversing-a-simple-rowset"></a>단순 행 집합 검색

다음 예에서는 명령을 포함 하지 않는 빠르고 쉬운 데이터베이스 액세스를 보여 줍니다. 다음 소비자 코드는 ATL 프로젝트의 Microsoft OLE DB Provider for ODBC를 사용 하 여 Microsoft Access 데이터베이스의 *아티스트* 라는 테이블에서 레코드를 검색 합니다. 이 코드는 사용자 레코드 클래스를 기반으로 하는 접근자를 사용 하 여 [CTable](../../data/oledb/ctable-class.md) 테이블 개체를 만듭니다 `CArtists` . 연결을 열고 연결에서 세션을 연 다음 세션에서 테이블을 엽니다.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CTable<CAccessor<CArtists>> artists;

    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    artists.Open(session, "Artists");

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
};
```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)
