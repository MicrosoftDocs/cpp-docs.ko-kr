---
title: OLE DB 공급자 템플릿에 대한 매크로
ms.date: 02/11/2019
f1_keywords:
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
ms.openlocfilehash: e72204102bfa47a9dd162499030a38c07bbfe46c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504006"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 공급자 템플릿에 대한 매크로

OLE DB 템플릿 공급자 매크로는 다음 범주의 기능을 제공 합니다.

## <a name="property-set-map-macros"></a>속성 집합 맵 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|속성 집합의 시작을 표시 합니다.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|속성 집합의 시작을 표시 합니다.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|속성 집합의 시작을 표시 합니다 .이는 공급자의 범위 외부에서 숨겨지거나 정의할 수 있습니다.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|속성 그룹을 함께 연결 합니다.|
|[END_PROPERTY_SET](#end_property_set)|속성 집합의 끝을 표시 합니다.|
|[END_PROPSET_MAP](#end_propset_map)|속성 집합 맵의 끝을 표시 합니다.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|속성을 기본값으로 설정 하 여 특정 속성을 설정 합니다.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|속성 집합의 특정 속성을 사용자가 제공한 값으로 설정 합니다. 플래그와 옵션을 설정할 수도 있습니다.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|속성 집합의 특정 속성을 사용자가 제공한 값으로 설정 합니다.|

## <a name="column-map-macros"></a>열 맵 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|공급자 열 맵 항목의 시작을 표시 합니다.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|공급자 열 맵 항목의 끝을 표시 합니다.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|공급자가 지 원하는 특정 열을 나타냅니다.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|공급자가 지 원하는 특정 열을 나타냅니다. 열 데이터 형식을 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|공급자가 지 원하는 특정 열을 나타냅니다. 열의 크기, 데이터 형식, 전체 자릿수, 소수 자릿수 및 스키마 행 집합 GUID를 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|공급자가 지 원하는 특정 열을 나타냅니다. 열 크기를 지정할 수 있습니다.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|공급자가 지 원하는 특정 열을 나타냅니다. 열 유형이 문자열인 것으로 가정 합니다.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|공급자가 지 원하는 특정 열을 나타냅니다. PROVIDER_COLUMN_ENTRY_LENGTH와 같지만 열의 데이터 형식 및 크기를 지정할 수도 있습니다.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|공급자가 지 원하는 특정 열을 나타냅니다. 열 유형이 유니코드 문자열 이라고 가정 합니다.|

## <a name="schema-rowset-macros"></a>스키마 행 집합 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|스키마 맵의 시작을 표시 합니다.|
|[END_SCHEMA_MAP](#end_schema_map)|스키마 맵의 끝을 표시 합니다.|
|[SCHEMA_ENTRY](#schema_entry)|GUID를 클래스와 연결 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a> BEGIN_PROPERTY_SET

속성 집합 맵에서 속성 집합의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 속성 GUID입니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

속성 집합 맵에서 속성 집합의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 속성 GUID입니다.

*flags*<br/>
진행 공급자의 범위를 벗어난 속성을 노출 하는 공급자에 대 한 UPROPSET_PASSTHROUGH를 표시 하지 않으려는 속성 집합에 대해 UPROPSET_HIDDEN 합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

속성 집합 맵 항목의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>매개 변수

*클래스*<br/>
진행 이 속성이 설정 된 클래스입니다. 다음 OLE DB 개체에서 속성 집합을 지정할 수 있습니다.

- [데이터 원본 개체](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [세션 개체](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [명령](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>예제

다음은 샘플 속성 집합 맵입니다.

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a> CHAIN_PROPERTY_SET

이 매크로는 속성 그룹을 함께 연결 합니다.

#### <a name="syntax"></a>구문

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>매개 변수

*ChainClass*<br/>
진행 속성을 연결할 클래스의 이름입니다. 이 클래스는 이미 맵을 포함 하는 ATL 프로젝트 마법사에 의해 생성 된 클래스입니다 (예: 세션, 명령 또는 데이터 원본 개체 클래스).

#### <a name="remarks"></a>설명

다른 클래스의 속성 집합을 고유한 클래스에 연결한 다음 클래스에서 직접 속성에 액세스할 수 있습니다.

> [!CAUTION]
> 이 매크로를 사용 하는 경우에만 사용 합니다. 잘못 사용 하면 소비자가 OLE DB 규칙 테스트를 실패할 수 있습니다.

### <a name="end_property_set"></a><a name="end_property_set"></a> END_PROPERTY_SET

속성 집합의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 속성 GUID입니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="end_propset_map"></a><a name="end_propset_map"></a> END_PROPSET_MAP

속성 집합 맵 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="property_info_entry"></a><a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

#### <a name="remarks"></a>설명

이 매크로는 `DWORD` 형식의 속성 값을 ATLDB.H에 정의된 기본값으로 설정합니다. 속성을 선택한 값으로 설정하려면 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)를 사용합니다. `VARTYPE`속성에 대 한 및 [Dbpropflags](/previous-versions/windows/desktop/ms724342(v=vs.85)) 를 동시에 설정 하려면 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)을 사용 합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

*vt*<br/>
[in] 이 속성 항목의 `VARTYPE`입니다. (Wtypes .h에 정의 됨)

*dwFlags*<br/>
[in] 이 속성 항목을 설명하는 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 값입니다.

*value*<br/>
[in] `DWORD`형식의 속성 값입니다.

*options*<br/>
DBPROPOPTIONS_REQUIRED 또는 DBPROPOPTIONS_SETIFCHEAP입니다. 일반적으로 공급자는 소비자가 설정 하므로 *옵션* 을 설정할 필요가 없습니다.

#### <a name="remarks"></a>설명

이 매크로를 사용하면 `DWORD` 형식의 속성 값뿐만 아니라 옵션 및 플래그를 직접 지정할 수 있습니다. 속성을 ATLDB.H에 정의된 기본값으로 설정하려면 [PROPERTY_INFO_ENTRY](#property_info_entry)를 사용합니다. 옵션 또는 플래그를 설정하지 않고 선택한 값으로 속성을 설정하려면 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)를 사용합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

속성 집합의 특정 속성을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>매개 변수

*dwPropID*<br/>
[in] 속성 집합 GUID와 함께 사용하여 속성을 식별할 수 있는 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 값입니다.

*value*<br/>
[in] `DWORD`형식의 속성 값입니다.

#### <a name="remarks"></a>설명

이 매크로를 사용 하면 형식의 속성 값을 직접 지정할 수 있습니다 `DWORD` . 속성을 ATLDB.H에 정의 된 기본값으로 설정 합니다. H, [PROPERTY_INFO_ENTRY](#property_info_entry)을 사용 합니다. 속성의 값, 플래그 및 옵션을 설정 하려면 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)을 사용 합니다.

#### <a name="example"></a>예제

[BEGIN_PROPSET_MAP](#begin_propset_map)을 참조하세요.

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

공급자 열 맵 항목의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>매개 변수

*theClass*<br/>
진행 이 맵이 속한 클래스의 이름입니다.

#### <a name="example"></a>예제

예제 공급자 열 맵은 다음과 같습니다.

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

공급자 열 맵 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>예제

[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)를 참조 하세요.

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*구성원과*<br/>
진행 열에 해당 하는의 멤버 변수 `dataClass` 입니다.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*dbtype*<br/>
진행 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))의 데이터 형식입니다.

*구성원과*<br/>
진행 `dataClass` 데이터를 저장 하는의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 데이터 형식을 지정할 수 있습니다.

#### <a name="example"></a>예제

[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)를 참조 하세요.

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*flags*<br/>
진행 데이터가 반환 되는 방법을 지정 합니다. `dwFlags` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))의 설명을 참조 하세요.

*colSize*<br/>
진행 열 크기입니다.

*dbtype*<br/>
진행 값의 데이터 형식을 나타냅니다. `wType` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))의 설명을 참조 하세요.

*전체 자릿수*<br/>
진행 *DbType* 이 DBTYPE_NUMERIC 또는 DBTYPE_DECIMAL 경우 데이터를 가져올 때 사용할 전체 자릿수를 나타냅니다. `bPrecision` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))의 설명을 참조 하세요.

*scale*<br/>
진행 DbType이 DBTYPE_NUMERIC 또는 DBTYPE_DECIMAL 경우 데이터를 가져올 때 사용할 소수 자릿수를 나타냅니다. `bScale` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85))의 설명을 참조 하세요.

*guid*<br/>
스키마 행 집합 GUID입니다. 스키마 행 집합 및 해당 Guid 목록은 *OLE DB 프로그래머 참조* 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

#### <a name="remarks"></a>설명

열의 크기, 데이터 형식, 전체 자릿수, 소수 자릿수 및 스키마 행 집합 GUID를 지정할 수 있습니다.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*size*<br/>
진행 열 크기 (바이트)입니다.

*구성원과*<br/>
진행 `dataClass` 열 데이터를 저장 하는의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 크기를 지정할 수 있습니다.

#### <a name="example"></a>예제

[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)를 참조 하세요.

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*구성원과*<br/>
진행 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 데이터를 [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))하는 것으로 간주 되는 경우이 매크로를 사용 합니다.

#### <a name="example"></a>예제

[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)를 참조 하세요.

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*dbtype*<br/>
진행 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))의 데이터 형식입니다.

*size*<br/>
진행 열 크기 (바이트)입니다.

*구성원과*<br/>
진행 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length) 와 비슷하며 열의 데이터 형식 및 크기를 지정할 수도 있습니다.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

공급자가 지 원하는 특정 열을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
진행 열 이름입니다.

*순서로*<br/>
[in] 열 번호입니다. 열이 책갈피 열이 아닌 경우 열 번호는 0이 아니어야 합니다.

*구성원과*<br/>
진행 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.

#### <a name="remarks"></a>설명

열 데이터가 null로 끝나는 유니코드 문자열이 [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))경우이 매크로를 사용 합니다.

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

스키마 맵의 시작을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>매개 변수

*SchemaClass*<br/>
맵을 포함 하는 클래스입니다. 일반적으로 세션 클래스가 됩니다.

#### <a name="remarks"></a>설명

스키마 행 집합에 대 한 자세한 내용은 Windows SDK의 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

### <a name="end_schema_map"></a><a name="end_schema_map"></a> END_SCHEMA_MAP

스키마 맵의 끝을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>설명

자세한 내용은 [IDBSchemaRowsetImpl 클래스](../../data/oledb/idbschemarowsetimpl-class.md)를 참조 하세요.

### <a name="schema_entry"></a><a name="schema_entry"></a> SCHEMA_ENTRY

GUID를 클래스와 연결 합니다.

#### <a name="syntax"></a>구문

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
스키마 행 집합 GUID입니다. 스키마 행 집합 및 해당 Guid 목록은 *OLE DB 프로그래머 참조* 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

*rowsetClass*<br/>
스키마 행 집합을 나타내기 위해 생성 되는 클래스입니다.

#### <a name="remarks"></a>설명

그런 다음 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 는 맵을 쿼리하여 guid 목록을 쿼리 하거나, guid가 지정 된 경우 행 집합을 만들 수 있습니다. 스키마 행 집합은 `IDBSchemaRowsetImpl` `CRowsetImpl` 다음 서명이 있는 메서드를 제공 해야 한다는 점을 제외 하 고는 표준 파생 클래스와 유사 합니다 `Execute` .

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

이 `Execute` 함수는 행 집합의 데이터를 채웁니다. ATL 프로젝트 마법사는 다음의 세 가지 필수 OLE DB 스키마 각각에 대 한 프로젝트의 세 가지 초기 스키마 행 집합 *OLE DB 프로그래머 참조*에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 에 설명 된 대로를 만듭니다.

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

또한 마법사는 스키마 맵에 3 개의 해당 항목을 추가 합니다. 마법사를 사용 하 여 공급자를 만드는 방법에 대 한 자세한 내용은 [OLE DB 템플릿 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 공급자 템플릿 참조](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 공급자 템플릿에 대 한 매크로](../../data/oledb/macros-for-ole-db-provider-templates.md)
