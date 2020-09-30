---
title: OLE DB 소비자 템플릿에 대한 매크로 및 전역 함수
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 60f642366589bb13b15665331a81d440322eb13f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504036"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 소비자 템플릿에 대한 매크로 및 전역 함수

OLE DB Consumer 템플릿에는 다음과 같은 매크로 및 전역 함수가 포함 되어 있습니다.

## <a name="global-functions"></a>전역 함수

| 속성 | 설명 |
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|오류가 반환 되 면 덤프 장치에 OLE DB 오류 레코드 정보를 덤프 합니다.|

## <a name="accessor-map-macros"></a>접근자 맵 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|접근자 항목의 시작을 표시 합니다.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|접근자 맵 항목의 시작을 표시합니다.|
|[END_ACCESSOR](#end_accessor)|접근자 항목의 끝을 표시 합니다.|
|[END_ACCESSOR_MAP](#end_accessor_map)|접근자 맵 항목의 끝을 표시 합니다.|

## <a name="column-map-macros"></a>열 맵 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|사용자 레코드 클래스에서 열 맵 항목의 시작을 표시 합니다.|
|[BLOB_ENTRY](#blob_entry)|BLOB (binary large object)를 바인딩하는 데 사용 됩니다.|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|BLOB 데이터 열의 길이를 보고 합니다.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|BLOB 데이터 열의 길이와 상태를 보고 합니다.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|BLOB 데이터 열의 상태를 보고 합니다.|
|[BLOB_NAME](#blob_name)|Blob (binary large object)을 열 이름으로 바인딩하는 데 사용 됩니다.|
|[BLOB_NAME_LENGTH](#blob_name_length)|BLOB 데이터 열의 길이를 보고 합니다.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|BLOB 데이터 열의 길이와 상태를 보고 합니다.|
|[BLOB_NAME_STATUS](#blob_name_status)|BLOB 데이터 열의 상태를 보고 합니다.|
|[BOOKMARK_ENTRY](#bookmark_entry)|행 집합의 책갈피 항목을 나타냅니다. 책갈피 항목은 특별 한 종류의 열 항목입니다.|
|[COLUMN_ENTRY](#column_entry)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *형식*, *길이*, *전체 자릿수*, *소수 자릿수*및 *상태* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *길이* 변수를 지원 합니다.|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *상태* 및 *길이* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_PS](#column_entry_ps)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *전체 자릿수* 및 *소수 자릿수* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *길이* 변수, *전체 자릿수* 및 *소수 자릿수* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *상태* 및 *길이* 변수, *전체 자릿수* 및 *소수* 자릿수 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *상태* 변수, *전체 자릿수* 및 *소수 자릿수* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *상태* 변수를 지원 합니다.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *형식* 매개 변수를 지원 합니다.|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *형식* 및 *크기* 매개 변수를 지원 합니다.|
|[COLUMN_NAME](#column_name)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다.|
|[COLUMN_NAME_EX](#column_name_ex)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 에서는 데이터 형식, 크기, 전체 자릿수, 소수 자릿수, 열 길이 및 열 상태를 지정할 수 있습니다.|
|[COLUMN_NAME_LENGTH](#column_name_length)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 열 길이 지정을 지원 합니다.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 열 길이 및 상태 지정을 지원 합니다.|
|[COLUMN_NAME_PS](#column_name_ps)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 전체 자릿수 및 소수 자릿수 지정을 지원 합니다.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 전체 자릿수, 소수 자릿수 및 열 길이 지정을 지원 합니다.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 전체 자릿수, 소수 자릿수, 열 길이 및 열 상태의 사양을 지원 합니다.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 전체 자릿수, 소수 자릿수 및 열 상태의 사양을 지원 합니다.|
|[COLUMN_NAME_STATUS](#column_name_status)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 열 상태 지정을 지원 합니다.|
|[COLUMN_NAME_TYPE](#column_name_type)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 데이터 형식의 사양을 지원 합니다.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 데이터 형식, 전체 자릿수 및 소수 자릿수의 사양을 지원 합니다.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 데이터 형식 및 크기의 사양을 지원 합니다.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|이름을 기준으로 데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 데이터 형식 및 열 상태의 사양을 지원 합니다.|
|[END_COLUMN_MAP](#end_column_map)|열 맵 항목의 끝을 표시 합니다.|

## <a name="command-macros"></a>명령 매크로

| 속성 | 설명 |
|-|-|
|[DEFINE_COMMAND](#define_command)|[CCommand](../../data/oledb/ccommand-class.md) 클래스를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령을 지정 합니다. 지정 된 응용 프로그램 유형과 일치 하는 문자열 유형 (ANSI 또는 유니코드)만 허용 합니다. DEFINE_COMMAND 대신 [DEFINE_COMMAND_EX](#define_command_ex) 를 사용 하는 것이 좋습니다.|
|[DEFINE_COMMAND_EX](#define_command_ex)|[CCommand](../../data/oledb/ccommand-class.md) 클래스를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령을 지정 합니다. 는 ANSI 및 유니코드 응용 프로그램을 지원 합니다.|

## <a name="parameter-map-macros"></a>매개 변수 맵 매크로

| 속성 | 설명 |
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|사용자 레코드 클래스에서 매개 변수 맵 항목의 시작을 표시 합니다.|
|[END_PARAM_MAP](#end_param_map)|매개 변수 맵 항목의 끝을 표시 합니다.|
|[SET_PARAM_TYPE](#set_param_type)|SET_PARAM_TYPE 매크로를 수행 하는 매크로를 입력, 출력 또는 입/출력으로 COLUMN_ENTRY 지정 합니다.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

오류가 반환 되 면 덤프 장치에 OLE DB 오류 레코드 정보를 덤프 합니다.

#### <a name="syntax"></a>구문

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>매개 변수

*hErr*<br/>
진행 OLE DB 소비자 템플릿 멤버 함수에서 반환 된 HRESULT입니다.

#### <a name="remarks"></a>설명

*HErr* 가 S_OK 되지 않으면 `AtlTraceErrorRecords` OLE DB 오류 레코드 정보를 덤프 장치 (출력 창 또는 파일의 **디버그** 탭)에 덤프 합니다. 공급자에서 가져온 오류 레코드 정보에는 각 오류 레코드 항목의 행 번호, 원본, 설명, 도움말 파일, 컨텍스트 및 GUID가 포함 됩니다. `AtlTraceErrorRecords` 이 정보를 디버그 빌드에서만 덤프 합니다. 릴리스 빌드에서는 최적화 된 빈 스텁이 있습니다. 자세한 내용은 [Cdberrorinfo 클래스](../../data/oledb/cdberrorinfo-class.md)를 참조 하세요.

### <a name="begin_accessor"></a><a name="begin_accessor"></a> BEGIN_ACCESSOR

접근자 항목의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>매개 변수

*num*<br/>
진행 이 접근자 맵에 있는 접근자의 0 오프셋 번호입니다.

*bAuto*<br/>
진행 이 접근자가 자동 접근자 또는 수동 접근자 인지 여부를 지정 합니다. 이면 **`true`** 접근자가 자동이 고, 이면 **`false`** 접근자가 수동입니다. Auto 접근자는 이동 작업 시 데이터가 사용자에 게 인출 됨을 의미 합니다.

#### <a name="remarks"></a>설명

행 집합에 여러 접근자가 있는 경우 BEGIN_ACCESSOR_MAP를 지정 하 고 각 개별 접근자에 대해 BEGIN_ACCESSOR 매크로를 사용 해야 합니다. BEGIN_ACCESSOR 매크로는 END_ACCESSOR 매크로를 사용 하 여 완료 됩니다. BEGIN_ACCESSOR_MAP 매크로는 END_ACCESSOR_MAP 매크로를 사용 하 여 완료 됩니다.

#### <a name="example"></a>예제

[BEGIN_ACCESSOR_MAP](#begin_accessor_map)를 참조 하세요.

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

접근자 맵 항목의 시작을 표시합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>매개 변수

*x*<br/>
[in] 사용자 레코드 클래스의 이름입니다.

*num*<br/>
[in] 이 접근자 맵에 있는 접근자 수입니다.

#### <a name="remarks"></a>설명

행 집합에 여러 접근자가 있는 경우 처음에 BEGIN_ACCESSOR_MAP를 지정 하 고 각 개별 접근자에 대해 BEGIN_ACCESSOR 매크로를 사용 해야 합니다. BEGIN_ACCESSOR 매크로는 END_ACCESSOR 매크로를 사용 하 여 완료 됩니다. 접근자 맵은 END_ACCESSOR_MAP 매크로를 사용 하 여 완료 됩니다.

사용자 레코드에 접근자가 하나만 있는 경우 [BEGIN_COLUMN_MAP](#begin_column_map)매크로를 사용합니다.

#### <a name="example"></a>예제

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a> END_ACCESSOR

접근자 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>설명

행 집합에 대 한 여러 접근자의 경우 BEGIN_ACCESSOR_MAP 지정 하 고 각 개별 접근자에 대해 BEGIN_ACCESSOR 매크로를 사용 해야 합니다. BEGIN_ACCESSOR 매크로는 END_ACCESSOR 매크로를 사용 하 여 완료 됩니다. BEGIN_ACCESSOR_MAP 매크로는 END_ACCESSOR_MAP 매크로를 사용 하 여 완료 됩니다.

#### <a name="example"></a>예제

[BEGIN_ACCESSOR_MAP](#begin_accessor_map)를 참조 하세요.

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a> END_ACCESSOR_MAP

접근자 맵 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>설명

행 집합에 대 한 여러 접근자의 경우 BEGIN_ACCESSOR_MAP 지정 하 고 각 개별 접근자에 대해 BEGIN_ACCESSOR 매크로를 사용 해야 합니다. BEGIN_ACCESSOR 매크로는 END_ACCESSOR 매크로를 사용 하 여 완료 됩니다. BEGIN_ACCESSOR_MAP 매크로는 END_ACCESSOR_MAP 매크로를 사용 하 여 완료 됩니다.

#### <a name="example"></a>예제

[BEGIN_ACCESSOR_MAP](#begin_accessor_map)를 참조 하세요.

### <a name="begin_column_map"></a><a name="begin_column_map"></a> BEGIN_COLUMN_MAP

열 맵 항목의 시작을 표시합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>매개 변수

*x*<br/>
[in] `CAccessor`에서 파생된 사용자 레코드 클래스의 이름입니다.

#### <a name="remarks"></a>설명

이 매크로는 행 집합에 단일 접근자가 있는 경우에 사용됩니다. 행 집합에 여러 접근자가 있는 경우 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)을 사용합니다.

BEGIN_COLUMN_MAP 매크로는 END_COLUMN_MAP 매크로를 사용 하 여 완료 됩니다. 이 매크로는 사용자 레코드에 하나의 접근자만 필요한 경우에 사용됩니다.

열은 바인딩하려면 행 집합의 필드에 해당합니다.

#### <a name="example"></a>예제

다음은 열 및 매개 변수 맵의 샘플입니다.

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a> BLOB_ENTRY

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="example"></a>예제

[BLOB을 검색 하려면 어떻게 해야 하나요?를](../../data/oledb/retrieving-a-blob.md)참조 하세요.

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. [BLOB_ENTRY](#blob_entry)와 유사 합니다. 단,이 매크로는 BLOB 열의 길이 (바이트)도 가져옵니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
제한이 BLOB 열의 (실제) 길이 (바이트)입니다.

#### <a name="example"></a>예제

[BLOB을 검색 하려면 어떻게 해야 하나요?를](../../data/oledb/retrieving-a-blob.md)참조 하세요.

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. [BLOB_ENTRY](#blob_entry)와 유사 합니다. 단,이 매크로는 BLOB 열의 길이와 상태를 가져옵니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
제한이 BLOB 열의 (실제) 길이 (바이트)입니다.

*status*<br/>
제한이 BLOB 데이터 열의 상태입니다.

#### <a name="example"></a>예제

[BLOB을 검색 하려면 어떻게 해야 하나요?를](../../data/oledb/retrieving-a-blob.md)참조 하세요.

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

BEGIN_COLUMN_MAP 또는 BEGIN_ACCESSOR_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. [BLOB_ENTRY](#blob_entry)와 유사 합니다. 단,이 매크로는 BLOB 열의 상태도 가져옵니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
제한이 BLOB 필드의 상태입니다.

#### <a name="example"></a>예제

[BLOB을 검색 하려면 어떻게 해야 하나요?를](../../data/oledb/retrieving-a-blob.md)참조 하세요.

### <a name="blob_name"></a><a name="blob_name"></a> BLOB_NAME

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. 이 매크로는 열 번호 대신 열 이름을 사용 한다는 점을 제외 하 고 [BLOB_ENTRY](#blob_entry)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="example"></a>예제

[BLOB을 검색 하려면 어떻게 해야 하나요?를](../../data/oledb/retrieving-a-blob.md)참조 하세요.

### <a name="blob_name_length"></a><a name="blob_name_length"></a> BLOB_NAME_LENGTH

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. [BLOB_NAME](#blob_name)와 유사 합니다. 단,이 매크로는 BLOB 데이터 열의 길이 (바이트)도 가져옵니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
제한이 BLOB 열의 (실제) 길이 (바이트)입니다.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. [BLOB_NAME](#blob_name)와 유사 합니다. 단,이 매크로는 BLOB 데이터 열의 길이와 상태도 가져옵니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
제한이 BLOB 열의 (실제) 길이 (바이트)입니다.

*status*<br/>
제한이 BLOB 필드의 상태입니다.

### <a name="blob_name_status"></a><a name="blob_name_status"></a> BLOB_NAME_STATUS

BEGIN_COLUMN_MAP 및 END_COLUMN_MAP와 함께 사용 되어[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))(binary large object)을 바인딩합니다. 이 매크로는 BLOB 데이터 열의 상태도 가져오는 점을 제외 하 고 [BLOB_NAME](#blob_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*IID*<br/>
진행 `IDD_ISequentialStream`BLOB을 검색 하는 데 사용 되는와 같은 인터페이스 GUID입니다.

*flags*<br/>
진행 OLE 구조적 저장소 모델 (예:)에 정의 된 저장소 모드 플래그 `STGM_READ` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
제한이 BLOB 필드의 상태입니다.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a> BOOKMARK_ENTRY

책갈피 열을 바인딩합니다.

#### <a name="syntax"></a>구문

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>매개 변수

*variable*<br/>
진행 책갈피 열에 바인딩할 변수입니다.

#### <a name="example"></a>예제

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

자세한 내용은 [Using Bookmarks](using-bookmarks.md) And [CBookmark Class](../../data/oledb/cbookmark-class.md)를 참조 하세요.

### <a name="column_entry"></a><a name="column_entry"></a> COLUMN_ENTRY

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_ENTRY 매크로는 다음 위치에서 사용 됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

#### <a name="example"></a>예제

[BEGIN_COLUMN_MAP](#begin_column_map) 및 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)매크로 항목의 예제를 참조 하세요.

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a> COLUMN_ENTRY_EX

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*wType*<br/>
진행 데이터 형식입니다.

*nLength*<br/>
진행 데이터 크기 (바이트)입니다.

*nPrecision*<br/>
진행 데이터를 가져올 때 사용할 최대 전체 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 입니다. 그렇지 않으면이 매개 변수는 무시 됩니다.

*nScale*<br/>
진행 데이터를 가져올 때 사용할 소수 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 또는 `DBTYPE_DECIMAL` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_ENTRY_EX 매크로는 다음 위치에서 사용 됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

#### <a name="example"></a>예제

[BOOKMARK_ENTRY](#bookmark_entry)를 참조 하세요.

### <a name="column_entry_length"></a><a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
진행 1부터 시작 하는 열 번호입니다. 책갈피는 열 0에 해당 합니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

이 매크로는 *길이* 변수를 지원 합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

이 매크로는 길이 및 상태 변수를 지원하려는 경우에 사용합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a> COLUMN_ENTRY_PS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

바인딩할 열의 정밀도 및 배율을 지정할 수 있습니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
진행 1부터 시작 하는 열 번호입니다. 책갈피는 열 0에 해당 합니다.

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

바인딩할 열의 정밀도 및 배율을 지정할 수 있습니다. 이 매크로는 *길이* 변수를 지원 합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

바인딩할 열의 정밀도 및 배율을 지정할 수 있습니다. 이 매크로는 길이 및 상태 변수를 지원하려는 경우에 사용합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

바인딩할 열의 정밀도 및 배율을 지정할 수 있습니다. 이 매크로는 *상태* 변수를 지원 합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_status"></a><a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

데이터베이스에서 특정 열에 대한 행 집합의 바인딩을 나타냅니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
[in] 열 번호입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

이 매크로는 *상태* 변수를 지원 합니다. 다음과 같은 위치에 사용됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_entry_type"></a><a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. *형식* 매개 변수를 지원 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*wType*<br/>
진행 열 항목의 데이터 형식입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

이 매크로는 데이터 형식을 지정 하는 방법을 제공 하는 [COLUMN_ENTRY](#column_entry) 매크로의 특수 한 변형입니다.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

데이터베이스의 특정 열에 대 한 바인딩을 나타냅니다. 는 *형식* 및 *크기* 매개 변수를 지원 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>매개 변수

*nOrdinal*<br/>
[in] 열 번호입니다.

*wType*<br/>
진행 열 항목의 데이터 형식입니다.

*nLength*<br/>
진행 열 항목의 크기 (바이트)입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

이 매크로는 데이터 크기와 형식을 지정 하는 방법을 제공 하는 [COLUMN_ENTRY](#column_entry) 매크로의 특수 한 변형입니다.

### <a name="column_name"></a><a name="column_name"></a> COLUMN_NAME

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로는 열 번호 대신 열 이름을 사용 한다는 점을 제외 하 고 [COLUMN_ENTRY](#column_entry)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로는 [COLUMN_ENTRY](#column_entry)와 동일한 위치에서 사용 됩니다.

- [BEGIN_COLUMN_MAP](#begin_column_map) 와 [END_COLUMN_MAP](#end_column_map) 매크로 사이.

- [BEGIN_ACCESSOR](#begin_accessor) 와 [END_ACCESSOR](#end_accessor) 매크로 사이.

- [BEGIN_PARAM_MAP](#begin_param_map) 와 [END_PARAM_MAP](#end_param_map) 매크로 사이.

### <a name="column_name_ex"></a><a name="column_name_ex"></a> COLUMN_NAME_EX

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 데이터 형식, 크기, 전체 자릿수, 소수 자릿수, 열 길이 및 열 상태를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*wType*<br/>
진행 데이터 형식입니다.

*nLength*<br/>
진행 데이터 크기 (바이트)입니다.

*nPrecision*<br/>
진행 데이터를 가져올 때 사용할 최대 전체 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 입니다. 그렇지 않으면이 매개 변수는 무시 됩니다.

*nScale*<br/>
진행 데이터를 가져올 때 사용할 소수 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 또는 `DBTYPE_DECIMAL` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_length"></a><a name="column_name_length"></a> COLUMN_NAME_LENGTH

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 열 길이가 사용 된다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 열 길이와 열 상태를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_ps"></a><a name="column_name_ps"></a> COLUMN_NAME_PS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로는 전체 자릿수와 소수 자릿수를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 비슷합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 전체 자릿수, 소수 자릿수 및 열 길이를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 전체 자릿수, 소수 자릿수, 열 길이 및 열 상태를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*length*<br/>
[in] 열 길이에 바인딩할 변수입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 전체 자릿수, 소수 자릿수 및 열 상태를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*nPrecision*<br/>
[in] 바인딩하려는 열의 최대 정밀도입니다.

*nScale*<br/>
[in] 바인딩할 열의 배율입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_status"></a><a name="column_name_status"></a> COLUMN_NAME_STATUS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 열 상태를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_type"></a><a name="column_name_type"></a> COLUMN_NAME_TYPE

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 데이터 형식을 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*wType*<br/>
진행 데이터 형식입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 데이터 형식, 전체 자릿수 및 소수 자릿수를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*wType*<br/>
진행 데이터 형식입니다.

*nPrecision*<br/>
진행 데이터를 가져올 때 사용할 최대 전체 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 입니다. 그렇지 않으면이 매개 변수는 무시 됩니다.

*nScale*<br/>
진행 데이터를 가져올 때 사용할 소수 자릿수와 *Wtype* 은 `DBTYPE_NUMERIC` 또는 `DBTYPE_DECIMAL` 입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로 에서도 데이터 형식과 크기를 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*wType*<br/>
진행 데이터 형식입니다.

*nLength*<br/>
진행 데이터 크기 (바이트)입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

행 집합에서 행 집합의 특정 열에 대 한 바인딩을 나타냅니다. 이 매크로는 데이터 형식과 열 상태도 함께 사용 한다는 점을 제외 하 고 [COLUMN_NAME](#column_name)와 유사 합니다.

#### <a name="syntax"></a>구문

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>매개 변수

*pszName*<br/>
진행 열 이름에 대 한 포인터입니다. 이름은 유니코드 문자열 이어야 합니다. 이름 앞에 ' L '을 추가 하 여이 작업을 수행할 수 있습니다. 예를 들면와 같습니다 `L"MyColumn"` .

*wType*<br/>
진행 데이터 형식입니다.

*status*<br/>
[in] 열 상태에 바인딩할 변수입니다.

*data*<br/>
[in] 사용자 레코드에서 해당 데이터 멤버입니다.

#### <a name="remarks"></a>설명

COLUMN_NAME_ * 매크로가 사용 되는 위치에 대 한 자세한 내용은 [COLUMN_NAME](#column_name) 를 참조 하세요.

### <a name="end_column_map"></a><a name="end_column_map"></a> END_COLUMN_MAP

열 맵 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>설명

이는 행 집합에서 단일 접근자와 함께 사용 됩니다. BEGIN_COLUMN_MAP 매크로는 END_COLUMN_MAP 매크로를 사용 하 여 완료 됩니다.

#### <a name="example"></a>예제

[BEGIN_COLUMN_MAP](#begin_column_map)를 참조 하세요.

### <a name="define_command"></a><a name="define_command"></a> DEFINE_COMMAND

[CCommand](../../data/oledb/ccommand-class.md) 클래스를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령을 지정 합니다. 지정 된 응용 프로그램 유형과 일치 하는 문자열 유형 (ANSI 또는 유니코드)만 허용 합니다.

> [!NOTE]
> DEFINE_COMMAND 대신 [DEFINE_COMMAND_EX](#define_command_ex) 를 사용 하는 것이 좋습니다.

#### <a name="syntax"></a>구문

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>매개 변수

*x*<br/>
진행 사용자 레코드 (명령) 클래스의 이름입니다.

*szCommand*<br/>
진행 [CCommand](../../data/oledb/ccommand-class.md)를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령 문자열입니다.

#### <a name="remarks"></a>설명

[CCommand:: Open](./ccommand-class.md#open) 메서드에서 명령 텍스트를 지정 하지 않으면 지정 하는 명령 문자열이 기본값으로 사용 됩니다.

응용 프로그램을 ANSI로 빌드하는 경우이 매크로는 ANSI 문자열을, 응용 프로그램을 유니코드로 빌드하는 경우에는 유니코드 문자열을 허용 합니다. ANSI 또는 유니코드 응용 프로그램 형식에 관계 없이 이전에 유니코드 문자열을 허용 하기 때문에 DEFINE_COMMAND 대신 [DEFINE_COMMAND_EX](#define_command_ex) 를 사용 하는 것이 좋습니다.

#### <a name="example"></a>예제

[BOOKMARK_ENTRY](#bookmark_entry)를 참조 하세요.

### <a name="define_command_ex"></a><a name="define_command_ex"></a> DEFINE_COMMAND_EX

[CCommand](../../data/oledb/ccommand-class.md) 클래스를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령을 지정 합니다. 는 유니코드 및 ANSI 응용 프로그램을 지원 합니다.

#### <a name="syntax"></a>구문

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>매개 변수

*x*<br/>
진행 사용자 레코드 (명령) 클래스의 이름입니다.

*wszCommand*<br/>
진행 [CCommand](../../data/oledb/ccommand-class.md)를 사용 하는 경우 행 집합을 만드는 데 사용 되는 명령 문자열입니다.

#### <a name="remarks"></a>설명

[CCommand:: Open](./ccommand-class.md#open) 메서드에서 명령 텍스트를 지정 하지 않으면 지정 하는 명령 문자열이 기본값으로 사용 됩니다.

이 매크로는 응용 프로그램 형식에 관계 없이 유니코드 문자열을 허용 합니다. 이 매크로는 ANSI 응용 프로그램 뿐만 아니라 유니코드를 지원 하기 때문에 [DEFINE_COMMAND](#define_command) 보다 좋습니다.

#### <a name="example"></a>예제

[BOOKMARK_ENTRY](#bookmark_entry)를 참조 하세요.

### <a name="begin_param_map"></a><a name="begin_param_map"></a> BEGIN_PARAM_MAP

매개 변수 맵 항목의 시작을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>매개 변수

*x*<br/>
[in] 사용자 레코드 클래스의 이름입니다.

#### <a name="remarks"></a>설명

매개 변수는 [명령](/previous-versions/windows/desktop/ms724608(v=vs.85))에 사용 됩니다.

#### <a name="example"></a>예제

[BEGIN_COLUMN_MAP](#begin_column_map) 매크로에 대 한 예제를 참조 하십시오.

### <a name="end_param_map"></a><a name="end_param_map"></a> END_PARAM_MAP

매개 변수 맵 항목의 끝을 표시 합니다.

#### <a name="syntax"></a>구문

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>예제

[BEGIN_PARAM_MAP](#begin_param_map) 매크로에 대 한 예제를 참조 하십시오.

### <a name="set_param_type"></a><a name="set_param_type"></a> SET_PARAM_TYPE

SET_PARAM_TYPE 매크로 입력, 출력 또는 입/출력 다음에 COLUMN_ENTRY 매크로를 지정 합니다.

#### <a name="syntax"></a>구문

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>매개 변수

*type*<br/>
[in] 매개 변수에 대해 설정할 형식입니다.

#### <a name="remarks"></a>설명

공급자는 기본 데이터 소스에서 지원되는 매개 변수 입력/출력 형식만 지원합니다. 형식은 하나 이상의 값의 조합입니다 `DBPARAMIO` ( *OLE DB 프로그래머 참조*에서 [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 참조).

- `DBPARAMIO_NOTPARAM` 접근자에는 매개 변수가 없습니다. 일반적으로 `eParamIO` 사용자에 게 매개 변수가 무시 됨을 알리기 위해 행 접근자에서이 값을로 설정 합니다.

- `DBPARAMIO_INPUT` 입력 매개 변수입니다.

- `DBPARAMIO_OUTPUT` 출력 매개 변수입니다.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` 매개 변수는 입력 및 출력 매개 변수입니다.

#### <a name="example"></a>예제

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿에 대 한 매크로 및 전역 함수](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
