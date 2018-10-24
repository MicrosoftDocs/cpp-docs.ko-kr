---
title: 단순 행 집합 검색 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 62a1b6c0aa164e6b564c505873fbc85f38b9febf
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808318"
---
# <a name="traversing-a-simple-rowset"></a>단순 행 집합 검색

다음 예제에서는 명령을 포함 하지 않습니다 하는 쉽고 빠르게 데이터베이스 액세스를 보여 줍니다. 라는 테이블에서 레코드를 검색 하는 ATL 프로젝트에서 다음 소비자 코드 *아티스트* Microsoft Access에서 Microsoft OLE DB Provider for ODBC 사용 하 여 데이터베이스입니다. 이 코드에서는 만듭니다는 [CTable](../../data/oledb/ctable-class.md) 사용자 레코드 클래스를 기반으로 한 접근자를 사용 하 여 테이블 개체 `CArtists`합니다. 연결, 연결에서 세션을 열고 열리고 세션에서 테이블을 엽니다.  
  
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
  
사용자 레코드 `CArtists`, 다음과 같은이 예제:  
  
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

[OLE DB 소비자 템플릿 작업](../../data/oledb/working-with-ole-db-consumer-templates.md)