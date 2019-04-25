---
title: OLE DB 공급자 템플릿에 대한 매크로
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: f5cf5e8ebadcc48dbd040225496f0a437b92555c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152711"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 공급자 템플릿에 대한 매크로

OLE DB 템플릿 공급자 매크로 다음 범주에서 기능을 제공합니다.

## <a name="property-set-map-macros"></a>속성 맵 매크로

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|속성 집합의 시작을 표시 합니다.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|속성 집합의 시작을 표시 합니다.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|표시 속성의 시작 부분을 설정 하는 숨겨진 또는 공급자의 범위 외부에 정의 된 수 있습니다.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|속성 그룹을 함께 연결 합니다.|
|[END_PROPERTY_SET](#end_property_set)|속성 집합의 끝을 표시합니다.|
|[END_PROPSET_MAP](#end_propset_map)|속성 집합 map의 끝을 표시 합니다.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|기본 값으로 설정 된 속성의 특정 속성을 설정 합니다.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|사용자가 제공 하는 값으로 설정 된 속성의 특정 속성을 설정 합니다. 플래그 및 옵션을 설정할 수 있습니다.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|사용자가 제공 하는 값으로 설정 된 속성의 특정 속성을 설정 합니다.|

## <a name="column-map-macros"></a>열 맵 매크로

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|공급자 열 지도 항목의 시작을 표시 합니다.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|공급자 열 지도 항목의 끝을 표시 합니다.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|공급자가 지 원하는 특정 열을 나타냅니다.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|공급자가 지 원하는 특정 열을 나타냅니다. 열 데이터 형식을 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|공급자가 지 원하는 특정 열을 나타냅니다. 열의 크기, 데이터 형식, 정밀도, 배율 및 스키마 행 집합 GUID 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|공급자가 지 원하는 특정 열을 나타냅니다. 열 크기를 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|공급자가 지 원하는 특정 열을 나타냅니다. 열 유형이 문자열인 가정 합니다.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|공급자가 지 원하는 특정 열을 나타냅니다. PROVIDER_COLUMN_ENTRY_LENGTH, 비슷하지만 크기 뿐만 아니라 열의 데이터 형식을 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|공급자가 지 원하는 특정 열을 나타냅니다. 열 형식이 유니코드 문자열 가정 합니다.|

## <a name="schema-rowset-macros"></a>스키마 행 집합 매크로

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|스키마 맵 시작 부분을 표시합니다.|
|[END_SCHEMA_MAP](#end_schema_map)|스키마 map의 끝을 표시 합니다.|
|[SCHEMA_ENTRY](#schema_entry)|클래스를 사용 하 여 GUID를 연결합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET

속성의 시작 부분에서 속성을 설정 하는 표시 집합 매핑됩니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
[in] GUID 속성입니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

속성의 시작 부분에서 속성을 설정 하는 표시 집합 매핑됩니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
[in] GUID 속성입니다.

*flags*<br/>
[in] 를 노출 하려면 원하지 않는 모든 속성 집합 또는 공급자의 범위 외부에 정의 된 속성을 노출 하는 공급자에 대 한 UPROPSET_PASSTHROUGH UPROPSET_HIDDEN 합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

표시 된 속성의 시작 부분 맵 항목을 설정합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>매개 변수

*클래스*<br/>
[in] 이 속성이 설정 된 클래스입니다. 다음 OLE DB 개체의 속성 집합을 지정할 수 있습니다.

- [데이터 원본 개체](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [세션 개체](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [도구](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>예제

샘플 속성 집합 지도 다음과 같습니다.

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET

이 매크로 속성 그룹을 함께 연결 합니다.

#### <a name="syntax"></a>구문

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>매개 변수

*ChainClass*<br/>
[in] 체인 속성에 대 한 클래스의 이름입니다. 지도 (예: 세션, 명령 또는 데이터 원본 개체 클래스)를 이미 포함 하는 ATL 프로젝트 마법사에서 생성 하는 클래스입니다.

#### <a name="remarks"></a>설명

사용자 고유의 클래스를 다른 클래스에서 속성 집합을 연결 합니다. 다음 속성을 클래스에서 직접 액세스할 수 있습니다.

> [!CAUTION]
>  이 매크로 제한적으로 사용 합니다. 부적절 한 사용 하 여 소비자가 OLE DB 적합성 테스트 실패를 발생할 수 있습니다.

### <a name="end_property_set"></a> END_PROPERTY_SET

속성 집합의 끝을 표시합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
[in] GUID 속성입니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="end_propset_map"></a> END_PROPSET_MAP

표시 속성의 끝 맵 항목을 설정합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

#### <a name="remarks"></a>설명

이 매크로는 `DWORD` 형식의 속성 값을 ATLDB.H에 정의된 기본값으로 설정합니다. 속성을 선택한 값으로 설정하려면 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)를 사용합니다. 설정 하는 `VARTYPE` 하 고 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 동시 속성에 대 한 사용 [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

*vt*<br/>
[in] 이 속성 항목의 `VARTYPE`입니다. (Wtypes.h에 정의 됨)

*dwFlags*<br/>
[in] 이 속성 항목을 설명하는 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 값입니다.

*값*<br/>
[in] `DWORD`형식의 속성 값입니다.

*options*<br/>
Dbpropoptions_required가 아니면 또는 DBPROPOPTIONS_SETIFCHEAP 합니다. 일반적으로 공급자는 설정할 필요가 없습니다 *옵션* 소비자가 설정 되어 있기 때문입니다.

#### <a name="remarks"></a>설명

이 매크로를 사용하면 `DWORD` 형식의 속성 값뿐만 아니라 옵션 및 플래그를 직접 지정할 수 있습니다. 속성을 ATLDB.H에 정의된 기본값으로 설정하려면 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)를 사용합니다. 옵션 또는 플래그를 설정하지 않고 선택한 값으로 속성을 설정하려면 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)를 사용합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

*값*<br/>
[in] `DWORD`형식의 속성 값입니다.

#### <a name="remarks"></a>설명

이 매크로 지정할 수 있습니다 직접 형식의 속성 값을 `DWORD`입니다. ATLDB에 정의 된 기본 값으로 속성을 설정 합니다. H를 사용 하 여 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)합니다. 값, 플래그 및 속성에 대 한 옵션을 설정 하려면 [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)을 참조하세요.

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

공급자 열 지도 항목의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>매개 변수

*theClass*<br/>
[in] 이 맵은 속한 클래스의 이름입니다.

#### <a name="example"></a>예제

샘플 공급자 열 지도 다음과 같습니다.

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

공급자 열 지도 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>예제

See [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*member*<br/>
[in] 멤버 변수 `dataClass` 열에 해당 합니다.

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*dbtype*<br/>
[in] 데이터 형식이 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))합니다.

*member*<br/>
[in] 멤버 변수 `dataClass` 데이터를 저장 하는 합니다.

#### <a name="remarks"></a>설명

열 데이터 형식을 지정할 수 있습니다.

#### <a name="example"></a>예제

See [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*flags*<br/>
[in] 데이터 반환 되는 방법을 지정 합니다. 참조를 `dwFlags` 설명을 [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))합니다.

*colSize*<br/>
[in] 열 크기입니다.

*dbtype*<br/>
[in] 데이터 형식을 값을 나타냅니다. 참조를 `wType` 설명을 [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))합니다.

*precision*<br/>
[in] 경우에 데이터를 가져올 때 사용할 전체 자릿수를 나타내는 *dbType* DBTYPE_NUMERIC 인지 DBTYPE_DECIMAL 합니다. 참조를 `bPrecision` 설명을 [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))합니다.

*scale*<br/>
[in] DbType DBTYPE_NUMERIC 또는 DBTYPE_DECIMAL 이면 데이터를 가져올 때 사용할 소수 자릿수를 나타냅니다. 참조를 `bScale` 설명을 [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))합니다.

*guid*<br/>
스키마 행 집합 GUID입니다. 참조 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 에 *OLE DB Programmer's Reference* 스키마 행 집합 목록과 해당 Guid에 대 한 합니다.

#### <a name="remarks"></a>설명

열의 크기, 데이터 형식, 정밀도, 배율 및 스키마 행 집합 GUID 지정할 수 있습니다.

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*size*<br/>
[in] 열 크기 (바이트)입니다.

*member*<br/>
[in] 멤버 변수 `dataClass` 열 데이터를 저장 합니다.

#### <a name="remarks"></a>설명

열 크기를 지정할 수 있습니다.

#### <a name="example"></a>예제

See [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*member*<br/>
[in] 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 데이터는 것으로 간주 되는 경우이 매크로 사용 하 여 [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))합니다.

#### <a name="example"></a>예제

See [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*dbtype*<br/>
[in] 데이터 형식이 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))합니다.

*size*<br/>
[in] 열 크기 (바이트)입니다.

*member*<br/>
[in] 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

비슷합니다 [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) 크기 뿐만 아니라 열의 데이터 형식을 지정할 수 있습니다.

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
[in] 열 이름입니다.

*ordinal*<br/>
[in] 열 번호입니다. 열 책갈피 열이 아닌 열 번호를 0 아니어야 합니다.

*member*<br/>
[in] 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 데이터가 null 종료 유니코드 문자열 하는 경우이 매크로 사용 하 여 [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))합니다.

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

스키마 맵 시작 부분을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>매개 변수

*SchemaClass*<br/>
맵을 포함 하는 클래스입니다. 일반적으로 세션 클래스가 됩니다.

#### <a name="remarks"></a>설명

참조 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 스키마 행 집합에 대 한 자세한 내용은 Windows SDK에 있습니다.

### <a name="end_schema_map"></a> END_SCHEMA_MAP

스키마 맵 끝을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>설명

자세한 내용은 [IDBSchemaRowsetImpl 클래스](../../data/oledb/idbschemarowsetimpl-class.md)합니다.

### <a name="schema_entry"></a> SCHEMA_ENTRY

클래스를 사용 하 여 GUID를 연결합니다.

#### <a name="syntax"></a>구문

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
스키마 행 집합 GUID입니다. 참조 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 에 *OLE DB Programmer's Reference* 스키마 행 집합 목록과 해당 Guid에 대 한 합니다.

*rowsetClass*<br/>
스키마 행 집합을 나타내는 데 생성 되는 클래스입니다.

#### <a name="remarks"></a>설명

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 다음 맵을 Guid의 목록을 쿼리할 수 있습니다 또는 GUID를 지정 하는 경우 행 집합을 만들 수 있습니다. 스키마 행 집합 `IDBSchemaRowsetImpl` 만듭니다 표준 비슷합니다 `CRowsetImpl`-파생 클래스를 제공 해야 하는 제외는 `Execute` 다음 서명이 있는 메서드:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

이 `Execute` 함수 행 집합의 데이터를 채웁니다. 에 설명 된 대로 ATL 프로젝트 마법사를 만듭니다 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 에 *OLE DB Programmer's Reference*, 프로젝트에서 스키마 행 집합의 각 세 가지 필수 OLE DB 스키마에 대 한 초기 3:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

마법사는 또한 스키마 구조의 세 해당 항목을 추가합니다. 참조 [OLE DB 템플릿 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md) 마법사를 사용 하 여 공급자를 만드는 데 대 한 자세한 내용은 합니다.

## <a name="see-also"></a>참고자료

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 공급자 템플릿 참조](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 공급자 템플릿에 대한 매크로](../../data/oledb/macros-for-ole-db-provider-templates.md)