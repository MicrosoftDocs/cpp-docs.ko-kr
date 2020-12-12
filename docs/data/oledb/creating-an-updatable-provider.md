---
description: '자세한 정보: 업데이트 가능 공급자 만들기'
title: 업데이트 가능 공급자 만들기
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 948b50f5e49ca8288e5fcf1ada75ae07d4a8b39f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305418"
---
# <a name="creating-an-updatable-provider"></a>업데이트 가능 공급자 만들기

Visual C++은 데이터 저장소를 업데이트 (쓰기) 할 수 있는 업데이트 가능한 공급자나 공급자를 지원 합니다. 이 항목에서는 OLE DB 템플릿을 사용 하 여 업데이트할 수 있는 공급자를 만드는 방법을 설명 합니다.

이 항목에서는를 사용 하는 공급자를 시작 한다고 가정 합니다. 업데이트 가능한 공급자를 만드는 두 가지 단계가 있습니다. 먼저 공급자가 데이터 저장소를 변경 하는 방법을 결정 해야 합니다. 특히 update 명령이 실행 될 때까지 변경 내용이 즉시 수행 되거나 지연 될 지 여부를 지정 합니다. "공급자를[업데이트할 수 있게 만들기](#vchowmakingprovidersupdatable)" 섹션에서는 공급자 코드에서 수행 해야 하는 변경 내용과 설정을 설명 합니다.

다음에는 소비자가 요청할 수 있는 모든 기능을 지원 하기 위한 모든 기능이 공급자에 포함 되어 있는지 확인 해야 합니다. 소비자가 데이터 저장소를 업데이트 하려는 경우 공급자는 데이터 저장소에 데이터를 유지 하는 코드를 포함 해야 합니다. 예를 들어 C Run-Time 라이브러리나 MFC를 사용 하 여 데이터 소스에서 이러한 작업을 수행할 수 있습니다. "[데이터 원본에 쓰기](#vchowwritingtothedatasource)" 섹션에서는 데이터 원본에 쓰고 NULL 및 기본값을 처리 하며 열 플래그를 설정 하는 방법을 설명 합니다.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 는 업데이트할 수 있는 공급자의 예입니다. UpdatePV는 MyProv와 같지만 업데이트할 수 있는 지원을 제공 합니다.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a> 공급자를 업데이트할 수 있도록 설정

공급자를 업데이트할 수 있도록 하기 위한 핵심은 공급자가 데이터 저장소에서 수행할 작업과 공급자가 이러한 작업을 수행 하는 방법을 이해 하는 것입니다. 특히 중요 한 문제는 업데이트 명령이 실행 될 때까지 데이터 저장소에 대 한 업데이트를 즉시 수행할지 지연 (일괄 처리) 할지 여부입니다.

먼저 `IRowsetChangeImpl` 또는 `IRowsetUpdateImpl` 행 집합 클래스에서 상속 하는지 결정 해야 합니다. 구현 하기로 선택 하는 방법에 따라 세 가지 메서드의 기능 `SetData` (, 및)이 영향을 받습니다 `InsertRows` `DeleteRows` .

- [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)에서 상속 하는 경우이 세 가지 메서드를 호출 하면 데이터 저장소가 즉시 변경 됩니다.

- [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)에서 상속 하는 경우 메서드는, 또는를 호출할 때까지 데이터 저장소에 대 한 변경 내용을 연기 `Update` `GetOriginalData` `Undo` 합니다. 업데이트에 몇 가지 변경 내용이 포함 된 경우 일괄 처리 모드에서 수행 됩니다 (변경 내용 일괄 처리가 상당한 메모리 오버 헤드를 추가할 수 있음).

는 `IRowsetUpdateImpl` 에서 파생 `IRowsetChangeImpl` 됩니다. 따라서는 `IRowsetUpdateImpl` 변경 기능 및 일괄 처리 기능을 제공 합니다.

### <a name="to-support-updatability-in-your-provider"></a>공급자에서 업데이트 기능을 지원 하려면

1. 행 집합 클래스에서 또는를 상속 `IRowsetChangeImpl` `IRowsetUpdateImpl` 합니다. 이러한 클래스는 데이터 저장소를 변경 하는 데 적절 한 인터페이스를 제공 합니다.

   **IRowsetChange 추가**

   `IRowsetChangeImpl`다음 형식을 사용 하 여 상속 체인에를 추가 합니다.

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   또한 `COM_INTERFACE_ENTRY(IRowsetChange)` `BEGIN_COM_MAP` 행 집합 클래스의 섹션에를 추가 합니다.

   **IRowsetUpdate 추가**

   `IRowsetUpdate`다음 형식을 사용 하 여 상속 체인에를 추가 합니다.

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > `IRowsetChangeImpl`상속 체인에서 줄을 제거 해야 합니다. 앞에서 언급 한 지시문에 대 한이 예외는에 대 한 코드를 포함 해야 합니다 `IRowsetChangeImpl` .

1. COM 맵 ()에 다음을 추가 합니다 `BEGIN_COM_MAP ... END_COM_MAP` .

   |  을 구현 하는 경우   |           COM 맵에 추가             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 을 구현 하는 경우 | 속성 집합 맵에 추가 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 명령에서 속성 집합 맵 ()에 다음을 추가 합니다 `BEGIN_PROPSET_MAP ... END_PROPSET_MAP` .

   |  을 구현 하는 경우   |                                             속성 집합 맵에 추가                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 속성 집합 맵에서 아래에 표시 된 대로 다음 설정도 모두 포함 해야 합니다.

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   속성 Id 및 값에 대해 Atldb.h를 살펴보면 이러한 매크로 호출에 사용 되는 값을 찾을 수 있습니다. Atldb.h가 온라인 설명서와 다른 경우 Atldb.h는 설명서를 대체 합니다.

   > [!NOTE]
   > `VARIANT_FALSE`OLE DB 템플릿에는 많은 및 `VARIANT_TRUE` 설정이 필요 합니다. OLE DB 사양에서는 읽기/쓰기가 가능 하지만 OLE DB 템플릿은 하나의 값만 지원할 수 있습니다.

   **IRowsetChangeImpl을 구현 하는 경우**

   을 구현 하 `IRowsetChangeImpl` 는 경우 공급자에서 다음 속성을 설정 해야 합니다. 이러한 속성은를 통해 인터페이스를 요청 하는 데 주로 사용 됩니다 `ICommandProperties::SetProperties` .

   - `DBPROP_IRowsetChange`:이를 자동으로 설정 `DBPROP_IRowsetChange` 합니다.

   - `DBPROP_UPDATABILITY`:, 또는에서 지원 되는 메서드를 지정 하는 비트 마스크 `IRowsetChange` `SetData` `DeleteRows` `InsertRow` 입니다.

   - `DBPROP_CHANGEINSERTEDROWS`: 소비자는 `IRowsetChange::DeleteRows` `SetData` 새로 삽입 된 행에 대해 또는를 호출할 수 있습니다.

   - `DBPROP_IMMOBILEROWS`: 행 집합은 삽입 또는 업데이트 된 행의 순서를 다시 정렬 하지 않습니다.

   **IRowsetUpdateImpl을 구현 하는 경우**

   을 구현 하는 경우 `IRowsetUpdateImpl` 이전에 나열 된 모든 속성을 설정 하는 것 외에도 공급자에서 다음 속성을 설정 해야 합니다 `IRowsetChangeImpl` .

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: READ_ONLY 하 고 VARIANT_TRUE 해야 합니다.

   - `DBPROP_OWNUPDATEDELETE`: READ_ONLY 하 고 VARIANT_TRUE 해야 합니다.

   - `DBPROP_OTHERINSERT`: READ_ONLY 하 고 VARIANT_TRUE 해야 합니다.

   - `DBPROP_OTHERUPDATEDELETE`: READ_ONLY 하 고 VARIANT_TRUE 해야 합니다.

   - `DBPROP_REMOVEDELETED`: READ_ONLY 하 고 VARIANT_TRUE 해야 합니다.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > 알림을 지 원하는 경우 다른 속성도 있을 수 있습니다. `IRowsetNotifyCP` 이 목록에 대 한 섹션을 참조 하세요.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a> 데이터 원본에 쓰기

데이터 소스에서 읽으려면 함수를 호출 `Execute` 합니다. 데이터 소스에 쓰려면 함수를 호출 `FlushData` 합니다. 일반적으로 플러시는 테이블이 나 인덱스에 대 한 수정 사항을 디스크에 저장 하는 것을 의미 합니다.

```cpp
FlushData(HROW, HACCESSOR);
```

행 핸들 (HROW) 및 접근자 핸들 (HACCESSOR) 인수를 사용 하 여 쓸 영역을 지정할 수 있습니다. 일반적으로 한 번에 하나의 데이터 필드를 작성 합니다.

`FlushData`메서드는 원래 저장 된 형식으로 데이터를 씁니다. 이 함수를 재정의 하지 않으면 공급자가 제대로 작동 하지만 변경 내용이 데이터 저장소에 플러시되지 않습니다.

### <a name="when-to-flush"></a>플러시하는 경우

공급자 템플릿은 데이터를 데이터 저장소에 써야 할 때마다 FlushData를 호출 합니다. 이는 일반적으로 다음 함수 호출의 결과로 발생 합니다.

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (행에 삽입할 새 데이터가 있는 경우)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>작동 방법

소비자는 플러시를 필요로 하는 호출을 수행 합니다 (예: Update) .이 호출은 공급자에 전달 되며이는 항상 다음 작업을 수행 합니다.

- `SetDBStatus`상태 값이 바인딩될 때마다를 호출 합니다.

- 열 플래그를 확인 합니다.

- `IsUpdateAllowed`.

이 세 단계는 보안을 제공 하는 데 도움이 됩니다. 그런 다음 공급자가를 호출 `FlushData` 합니다.

### <a name="how-to-implement-flushdata"></a>FlushData을 구현 하는 방법

를 구현 하려면 `FlushData` 다음과 같은 몇 가지 문제를 고려해 야 합니다.

데이터 저장소에서 변경 내용을 처리할 수 있는지 확인 합니다.

NULL 값 처리

### <a name="handling-default-values"></a>기본값을 처리 합니다.

사용자 고유의 `FlushData` 메서드를 구현 하려면 다음을 수행 해야 합니다.

- 행 집합 클래스로 이동 합니다.

- 행 집합 클래스에서의 선언을 배치 합니다.

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 의 구현을 제공 `FlushData` 합니다.

의 올바른 구현은 `FlushData` 실제로 업데이트 된 행과 열만 저장 합니다. HROW 및 HACCESSOR 매개 변수를 사용 하 여 최적화를 위해 저장 되는 현재 행과 열을 확인할 수 있습니다.

일반적으로 가장 큰 문제는 고유한 네이티브 데이터 저장소로 작업 하는 것입니다. 가능 하면 다음을 시도 합니다.

- 데이터 저장소에 쓰는 방법을 최대한 단순하게 유지 합니다.

- NULL 값을 처리 합니다 (선택 사항 이지만 권장).

- 기본값을 처리 합니다 (선택 사항 이지만 권장).

가장 좋은 방법은 데이터 저장소에 NULL 및 기본값에 대 한 실제 값을 지정 하는 것입니다. 이 데이터를 예측할 수 있는 것이 좋습니다. 그렇지 않으면 NULL 및 기본값을 허용 하지 않는 것이 좋습니다.

다음 예제에서는 `FlushData` 샘플의 클래스에서가 구현 되는 방법을 보여 줍니다 `RUpdateRowset` `UpdatePV` (샘플 코드의 Rowset 참조).

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>변경 내용 처리

공급자가 변경 내용을 처리 하려면 먼저 데이터 저장소 (예: 텍스트 파일 또는 비디오 파일)에 변경 내용을 적용할 수 있는 기능이 있는지 확인 해야 합니다. 그렇지 않으면 공급자 프로젝트와 별도로 해당 코드를 만들어야 합니다.

### <a name="handling-null-data"></a>NULL 데이터 처리

최종 사용자가 NULL 데이터를 보낼 수 있습니다. 데이터 원본의 필드에 NULL 값을 쓰면 잠재적 문제가 발생할 수 있습니다. 도시 및 우편 번호에 대 한 값을 허용 하는 주문 적용 응용 프로그램이 있다고 가정 합니다. 이 경우 두 값 중 하나 또는 둘 모두를 사용할 수 있지만,이 경우에는 배달 하지 못할 수 있습니다. 따라서 응용 프로그램에 적합 한 필드에서 NULL 값의 특정 조합을 제한 해야 합니다.

공급자 개발자는 해당 데이터를 저장 하는 방법, 데이터 저장소에서 데이터를 읽는 방법 및 사용자에 게 지정 하는 방법을 고려해 야 합니다. 특히 데이터 원본에서 행 집합 데이터의 데이터 상태를 변경 하는 방법을 고려해 야 합니다 (예: DataStatus = NULL). 소비자가 NULL 값을 포함 하는 필드에 액세스 하는 경우 반환할 값을 결정 합니다.

UpdatePV 샘플의 코드를 확인 합니다. 공급자가 NULL 데이터를 처리 하는 방법을 보여 줍니다. UpdatePV에서 공급자는 데이터 저장소에 문자열 "NULL"을 기록 하 여 NULL 데이터를 저장 합니다. 데이터 저장소에서 NULL 데이터를 읽으면 해당 문자열을 확인 한 다음 버퍼를 비우고 NULL 문자열을 만듭니다. 또한 `IRowsetImpl::GetDBStatus` 해당 데이터 값이 비어 있는 경우 DBSTATUS_S_ISNULL을 반환 하는의 재정의가 있습니다.

### <a name="marking-nullable-columns"></a>Nullable 열 표시

스키마 행 집합을 구현 하는 경우 (참조 `IDBSchemaRowsetImpl` ), 구현에서 열이 null을 허용 하는 DBSCHEMA_COLUMNS 행 집합 (일반적으로 공급자에 의해 CxxxSchemaColSchemaRowset로 표시 됨)에서를 지정 해야 합니다.

또한 모든 nullable 열에 버전의 DBCOLUMNFLAGS_ISNULLABLE 값이 포함 되도록 지정 해야 합니다 `GetColumnInfo` .

OLE DB 템플릿 구현에서 열을 null 허용으로 표시 하지 못하면 공급자는 값을 포함 해야 하며 소비자가 null 값을 보낼 수 없습니다.

다음 예에서는 `CommonGetColInfo` UpdatePV의 CUpdateCommand (UpProvRS 참조)에서 함수를 구현 하는 방법을 보여 줍니다. Null을 허용 하는 열에 대해이 DBCOLUMNFLAGS_ISNULLABLE 열에 대 한 정보를 확인 합니다.

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>기본값

NULL 데이터와 마찬가지로 기본값을 변경 하는 것을 처리 해야 합니다.

및의 기본값 `FlushData` 은 `Execute` S_OK를 반환 하는 것입니다. 따라서이 함수를 재정의 하지 않으면 변경 내용이 성공한 것 처럼 보이지만 (S_OK 반환 됨) 데이터 저장소로 전송 되지 않습니다.

`UpdatePV`이 샘플 (Rowset)에서 메서드는 기본값을 다음과 `SetDBStatus` 같이 처리 합니다.

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>열 플래그

열에 기본값을 지 원하는 경우 t 클래스에서 메타 데이터를 사용 하 여 값을 설정 해야 \<provider class\> 합니다. `m_bColumnHasDefault = VARIANT_TRUE`을 설정합니다.

DBCOLUMNFLAGS 열거 형식을 사용 하 여 지정 된 열 플래그를 설정 해야 할 수도 있습니다. 열 플래그는 열 특징을 설명 합니다.

예를 들어 `CUpdateSessionColSchemaRowset` 의 클래스 `UpdatePV` (세션 .h)에서 첫 번째 열은 다음과 같이 설정 됩니다.

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

이 코드는 열이 기본값 0을 지원 하 고, 쓰기 가능 하 고, 열의 모든 데이터가 같은 길이를 갖도록 지정 합니다. 열의 데이터에 가변 길이를 지정 하려면이 플래그를 설정 하지 않습니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](creating-an-ole-db-provider.md)
