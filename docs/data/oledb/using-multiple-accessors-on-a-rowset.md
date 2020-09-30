---
title: 행 집합에서 여러 접근자 사용
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 48772539b4dda9262a244506a36932d1e752949e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509401"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>행 집합에서 여러 접근자 사용

여러 접근자를 사용 해야 하는 세 가지 기본 시나리오는 다음과 같습니다.

- **읽기/쓰기 행 집합이 여러 개 있습니다.** 이 시나리오에는 기본 키가 있는 테이블이 있습니다. 기본 키를 포함 하 여 행의 모든 열을 읽을 수 있게 하려고 합니다. 기본 키 열에 쓸 수 없기 때문에 기본 키를 제외 하 고 모든 열에 데이터를 쓸 수도 있습니다. 이 경우 두 접근자를 설정 합니다.

  - 접근자 0은 모든 열을 포함 합니다.

  - 접근자 1은 기본 키를 제외한 모든 열을 포함 합니다.

- **성능.** 이 시나리오에서는 하나 이상의 열에 그래픽, 소리 또는 비디오 파일 등의 많은 양의 데이터가 있습니다. 행으로 이동할 때마다 응용 프로그램의 성능이 저하 될 수 있으므로 많은 데이터 파일을 사용 하 여 열을 검색 하는 것을 원하지 않을 수 있습니다.

  첫 번째 접근자에 데이터를 포함 하는 열을 제외한 모든 열을 포함 하 고 이러한 열에서 데이터를 자동으로 검색 하는 별도의 접근자를 설정할 수 있습니다. 첫 번째 접근자는 auto 접근자입니다. 두 번째 접근자는 대량 데이터를 보유 하는 열만 검색 하지만이 열에서 데이터를 자동으로 검색 하지는 않습니다. 다른 메서드를 통해 요청 시 대량 데이터를 업데이트 하거나 페치할 수 있습니다.

  - 접근자 0은 자동 접근자입니다. 데이터가 많은 열을 제외 하 고 모든 열을 검색 합니다.

  - 접근자 1은 자동 접근자가 아닙니다. 데이터가 많은 열을 검색 합니다.

  Auto 인수를 사용 하 여 접근자가 auto 접근자 인지 여부를 지정 합니다.

- **여러 ISequentialStream 열** 이 시나리오에서는 데이터를 보유 하는 열이 두 개 이상 있습니다 `ISequentialStream` . 그러나 각 접근자는 하나의 `ISequentialStream` 데이터 스트림으로 제한 됩니다. 이 문제를 해결 하려면 각각 하나의 포인터가 있는 여러 접근자를 설정 `ISequentialStream` 합니다.

일반적으로 [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) 및 [END_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) 매크로를 사용 하 여 접근자를 만듭니다. [Db_accessor](../../windows/attributes/db-accessor.md) 특성을 사용할 수도 있습니다. 접근자는 [사용자 레코드](../../data/oledb/user-records.md)에 추가로 설명 되어 있습니다. 매크로 또는 특성은 접근자가 자동 또는 자동이 아닌 접근자 인지 여부를 지정 합니다.

- 자동 접근자에서,,와 같은 메서드를 `MoveFirst` 이동 `MoveLast` `MoveNext` 하 고 `MovePrev` 지정 된 모든 열에 대 한 데이터를 자동으로 검색 합니다. 접근자 0은 자동 접근자 여야 합니다.

- 자동이 아닌 접근자에서,, 또는와 같은 메서드를 명시적으로 호출할 때까지 검색은 발생 하지 않습니다 `Update` `Insert` `Fetch` `Delete` . 위에서 설명한 시나리오에서 모든 열을 이동할 때마다 검색 하지 않으려고 할 수 있습니다. 다음과 같이 별도의 접근자에 하나 이상의 열을 추가 하 고 자동이 아닌 접근자를 만들 수 있습니다.

다음 예제에서는 여러 접근자를 사용 하 여 여러 접근자를 사용 하는 SQL Server pubs 데이터베이스의 작업 테이블을 읽고 씁니다. 이 예제는 여러 접근자를 사용 하는 가장 일반적인 방법입니다. 위의 "여러 읽기/쓰기 행 집합" 시나리오를 참조 하십시오.

사용자 레코드 클래스는 다음과 같습니다. 두 접근자를 설정 합니다. 접근자 0에는 기본 키 열 (ID)만 포함 되 고 접근자 1에는 다른 열이 포함 됩니다.

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

주 코드는 다음과 같습니다. 를 호출 하면 `MoveNext` 접근자 0을 사용 하 여 기본 키 열 ID에서 데이터가 자동으로 검색 됩니다. `Insert`End 근처의 메서드가 접근자 1을 사용 하 여 기본 키 열에 쓰지 않도록 하는 방법을 확인 합니다.

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[사용자 레코드](../../data/oledb/user-records.md)
