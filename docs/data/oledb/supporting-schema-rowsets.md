---
title: 스키마 행 집합 지원
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 156fe9c7a2b15f7254fb0c83f8b25982aa5ad09a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924312"
---
# <a name="supporting-schema-rowsets"></a>스키마 행 집합 지원

스키마 행 집합을 사용하면 소비자가 기본 구조 또는 스키마를 몰라도 데이터 저장소에 대한 정보를 가져올 수 있습니다. 예를 들어 데이터 저장소의 테이블이 사용자 정의 계층 구조로 구성되었을 수 있으므로 읽지 않으면 스키마를 알 수가 없습니다. 또 다른 예로 Visual C++ 마법사는 스키마 행 집합을 사용 하 여 소비자에 대 한 접근자를 생성 합니다. 소비자가이 작업을 수행할 수 있도록 공급자의 세션 개체가 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 인터페이스에 메서드를 노출 합니다. Visual C++ 애플리케이션에서 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 클래스를 사용하여 `IDBSchemaRowset`를 구현합니다.

`IDBSchemaRowsetImpl`에서는 다음 메서드를 지원합니다.

- [CheckRestrictions](./idbschemarowsetimpl-class.md#checkrestrictions) - 스키마 행 집합에 대한 제한의 유효성을 검사합니다.

- [CreateSchemaRowset](./idbschemarowsetimpl-class.md#createschemarowset) - 템플릿 매개 변수에 지정된 개체의 COM 개체 작성자 함수를 구현합니다.

- [SetRestrictions](./idbschemarowsetimpl-class.md#setrestrictions) - 특정 스키마 행 집합에서 지원되는 제한을 지정합니다.

- [IDBSchemaRowset::GetRowset](./idbschemarowsetimpl-class.md#getrowset) - 스키마 행 집합을 반환합니다(인터페이스에서 상속됨).

- [GetSchemas](./idbschemarowsetimpl-class.md#getschemas) - `IDBSchemaRowsetImpl::GetRowset`에서 액세스할 수 있는 스키마 행 집합 목록을 반환합니다(인터페이스에서 상속됨).

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 공급자 마법사 지원

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

**ATL OLE DB 공급자 마법사** 에서는 세션 헤더 파일에 다음 세 개의 스키마 클래스를 만듭니다.

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

이 클래스는 스키마 정보에 대한 소비자 요청에 응답합니다. OLE DB 사양에 따라 다음 세 개의 스키마 행 집합을 지원해야 합니다.

- **C**<em>ShortName</em>**SessionTRSchemaRowset** - 테이블 정보(DBSCHEMA_TABLES 스키마 행 집합) 요청을 처리합니다.

- **C**<em>ShortName</em>**SessionColSchemaRowset** - 열 정보(DBSCHEMA_COLUMNS 스키마 행 집합) 요청을 처리합니다. 마법사는 DOS 공급자의 스키마 정보를 반환하는 이러한 클래스의 샘플 구현을 제공합니다.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** - 공급자 유형(DBSCHEMA_PROVIDER_TYPES 스키마 행 집합)의 스키마 정보 요청을 처리합니다. 마법사에서 제공하는 기본 구현은 S_OK를 반환합니다.

이러한 클래스를 사용자 지정하여 해당 공급자에 적합한 스키마 정보를 처리할 수 있습니다.

- **C**<em>ShortName</em>**SessionTRSchemaRowset** 에서 카탈로그, 테이블 및 설명 필드(`trData.m_szType`, `trData.m_szTable` 및 `trData.m_szDesc`)에 정보를 입력해야 합니다. 마법사 생성 예제에서는 하나의 행(테이블)만 사용합니다. 다른 공급자는 둘 이상의 테이블을 반환할 수 있습니다.

- **C**<em>ShortName</em>**SessionColSchemaRowset** 에서 테이블 이름을 `DBID`로 전달합니다.

::: moniker-end

## <a name="setting-restrictions"></a>제한 설정

스키마 행 집합 지원에서 중요한 개념은 제한 설정으로, `SetRestrictions`를 사용하여 수행합니다. 제한을 통해 소비자는 일치하는 행만 페치할 수 있습니다. 예를 들어 "MyTable" 테이블의 모든 열을 찾을 수 있습니다. 제한은 선택 사항이므로 지원되는 제한이 없는 경우(기본값) 항상 모든 데이터가 반환됩니다. 제한을 지원하는 공급자 예제는 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플을 참조하세요.

## <a name="setting-up-the-schema-map"></a>스키마 맵 설정

UpdatePV의 Session.h에서 다음과 같은 스키마 맵을 설정합니다.

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

`IDBSchemaRowset`를 지원하려면 DBSCHEMA_TABLES, DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES를 지원해야 합니다. 임의로 스키마 행 집합을 더 추가할 수 있습니다.

`Execute` 메서드를 사용하여 `UpdatePV`의 `CUpdateSessionTRSchemaRowset`와 같은 스키마 행 집합 클래스를 선언합니다.

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession`은 `IDBSchemaRowsetImpl`에서 상속받으므로 모든 제한 처리 메서드가 있습니다. `CSchemaRowsetImpl`을 사용하여 위의 스키마 맵에 나열된 세 개의 자식 클래스(`CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, `CUpdateSessionPTSchemaRowset`)를 선언합니다. 각 자식 클래스에는 해당 제한 집합(검색 조건)을 처리하는 `Execute` 메서드가 있습니다. 각 `Execute` 메서드는 *cRestrictions* 및 *rgRestrictions* 매개 변수의 값을 비교합니다. 이러한 매개 변수에 대한 자세한 내용은 [SetRestrictions](./idbschemarowsetimpl-class.md#setrestrictions)를 참조하세요.

특정 스키마 행 집합에 해당하는 제한에 대한 자세한 내용은 Windows SDK의 **OLE DB 프로그래머 참조** 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))의 스키마 행 집합 GUID 표를 참조하세요.

예를 들어 DBSCHEMA_TABLES의 TABLE_NAME 제한을 지원하는 경우 다음을 수행합니다.

먼저 DBSCHEMA_TABLES를 조회하고 네 가지 제한을 순서대로 지원함을 확인합니다.

|스키마 행 집합 제한|제한 값|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1(이진 1)|
|TABLE_SCHEMA|0x2(이진 10)|
|TABLE_NAME|0x4(이진 100)|
|TABLE_TYPE|0x8(이진 1000)|

다음으로, 제한마다 1비트가 있습니다. TABLE_NAME만 지원하려고 하기 때문에 `rgRestrictions` 요소에 0x4를 반환합니다. TABLE_CATALOG 및 TABLE_NAME을 지원하는 경우 0x5(이진 101)를 반환합니다.

기본적으로, 이 구현에서는 모든 요청에 대해 0(제한 지원 안 함)을 반환합니다. UpdatePV는 제한을 지원하는 공급자 예제입니다.

### <a name="example"></a>예제

이 코드는 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플에서 가져온 것입니다. `UpdatePv` 에서는 DBSCHEMA_TABLES, DBSCHEMA_COLUMNS 및 DBSCHEMA_PROVIDER_TYPES의 세 가지 필수 스키마 행 집합을 지원 합니다. 공급자에서 스키마 지원을 구현하는 방법의 예제로, 이 항목에서는 DBSCHEMA_TABLE 행 집합을 구현하는 과정을 안내합니다.

> [!NOTE]
> 샘플 코드가 여기에 표시된 것과 다를 수도 있습니다. 샘플 코드가 더 최신 버전입니다.

스키마 지원을 추가하는 첫 번째 단계는 지원할 제한을 결정하는 것입니다. 해당 스키마 행 집합에 사용할 수 있는 제한을 확인하려면 OLE DB 사양에서 `IDBSchemaRowset`의 정의를 살펴봅니다. 기본 정의 다음에 스키마 행 집합 이름, 제한 수, 제한 열을 포함하는 표가 표시됩니다. 지원하려는 스키마 행 집합을 선택하고 제한 수와 제한 열을 적어둡니다. 예를 들어 DBSCHEMA_TABLES는 네 가지 제한(TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, TABLE_TYPE)을 지원합니다.

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

1비트가 각 제한 열을 나타냅니다. 제한을 지원하려면(즉, 제한으로 쿼리할 수 있음) 해당 비트를 1로 설정합니다. 제한을 지원하지 않으려면 해당 비트를 0으로 설정합니다. 위의 코드 줄에서는 `UpdatePV`가 DBSCHEMA_TABLES 행 집합에서 TABLE_NAME 및 TABLE_TYPE 제한을 지원합니다. 세 번째(비트 마스크 100) 제한과 네 번째(비트 마스크 1000) 제한입니다. 따라서 `UpdatePv`의 비트 마스크는 1100(또는 0x0C)입니다.

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

다음 `Execute` 함수는 일반 행 집합의 함수와 비슷합니다. *pcRowsAffected* , *cRestrictions* , *rgRestrictions* 등 세 개의 인수가 있습니다. *pcRowsAffected* 변수는 공급자가 스키마 행 집합의 행 수를 반환할 수 있는 출력 매개 변수입니다. *cRestrictions* 매개 변수는 소비자가 공급자에 전달하는 제한 수를 보유하는 입력 매개 변수입니다. *rgRestrictions* 매개 변수는 제한 값을 보유하는 VARIANT 값 배열입니다.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*cRestrictions* 변수는 공급자의 지원 여부에 관계없이 스키마 행 집합에 대한 총 제한 수를 기반으로 합니다. UpdatePv가 두 개의 제한(세 번째와 네 번째)을 지원하므로, 이 코드에서는 3보다 크거나 같은 *cRestrictions* 값만 찾습니다.

TABLE_NAME 제한의 값은 *rgRestrictions[2]* 에 저장됩니다(0부터 시작하는 배열의 세 번째 제한은 2임). 제한이 실제로 이 제한을 지원하는 VT_EMPTY가 아님을 확인합니다. VT_NULL은 VT_EMPTY와 다릅니다. VT_NULL은 유효한 제한 값을 지정합니다.

테이블 이름의 `UpdatePv` 정의는 텍스트 파일의 정규화된 경로 이름입니다. 제한 값을 추출하고 파일 열기를 시도하여 파일이 실제로 존재하는지 확인합니다. 파일이 없으면 S_OK를 반환합니다. 약간 역방향으로 진행하는 것처럼 보일 수도 있지만, 코드에서 실제로 소비자에게 알리는 내용은 지정한 이름으로 지원되는 테이블이 없다는 것입니다. S_OK가 반환되면 코드가 올바르게 실행된 것입니다.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

네 번째 제한(TABLE_TYPE) 지원은 세 번째 제한과 비슷합니다. 값이 VT_EMPTY가 아님을 확인합니다. 이 제한은 테이블 형식인 TABLE만 반환합니다. DBSCHEMA_TABLES에 유효한 값을 확인하려면 **OLE DB 프로그래머 참조** 의 **부록 B** 에서 TABLES 행 집합 섹션을 살펴봅니다.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

여기서 실제로 행 집합의 행 항목을 만듭니다. `trData` 변수는 OLE DB 공급자 템플릿에 정의된 구조체인 `CTABLESRow`에 해당합니다. `CTABLESRow`는 OLE DB 사양의 **부록 B** 에 있는 TABLES 행 집합 정의에 해당합니다. 한 번에 하나의 테이블만 지원할 수 있기 때문에 추가할 행은 하나뿐입니다.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` TABLE_NAME, TABLE_TYPE 및 설명의 3 개 열만 설정 합니다. 정보를 반환하는 열을 적어둡니다. 이 정보는 `GetDBStatus`를 구현할 때 필요합니다.

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` 함수는 스키마 행 집합이 올바르게 작동하는 데 중요합니다. TABLES 행 집합에 있는 모든 열의 데이터를 반환하지는 않으므로, 데이터를 반환하는 열과 반환하지 않는 열을 지정해야 합니다.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

`Execute` 함수는 TABLES 행 집합에서 TABLE_NAME, TABLE_TYPE 및 DESCRIPTION 필드의 데이터를 반환하기 때문에 OLE DB 사양의 **부록 B** 를 살펴보고 위에서 아래로 개수를 계산하여 서수 3, 4, 6인지 확인할 수 있습니다. 해당 열에 대해 각각 DBSTATUS_S_OK를 반환합니다. 다른 모든 열에 대해서는 DBSTATUS_S_ISNULL을 반환합니다. 소비자가 반환된 값이 NULL 또는 다른 값인지 이해하지 못할 수 있기 때문에 이 상태를 반환하는 것이 중요합니다. 다시 강조하지만, NULL은 빈 값이 아닙니다.

OLE DB 스키마 행 집합 인터페이스에 대한 자세한 내용은 **OLE DB 프로그래머 참조** 에서 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) 인터페이스를 참조하세요.

소비자가 `IDBSchemaRowset` 메서드를 사용할 수 있는 방법에 대한 자세한 내용은 [스키마 행 집합을 사용하여 메타데이터 구하기](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)를 참조하세요.

스키마 행 집합을 지원하는 공급자 예제는 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플을 참조하세요.

## <a name="see-also"></a>참고 항목

[고급 공급자 기술](../../data/oledb/advanced-provider-techniques.md)
