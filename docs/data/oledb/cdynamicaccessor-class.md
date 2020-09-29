---
title: CDynamicAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 31cc996b8beedadf9cba5a46b3b4da20e19268b0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498681"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 클래스

데이터베이스 스키마(데이터베이스의 내부 구조)에 대해 모를 때 데이터 소스에 액세스할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>요구 사항

**헤더**: atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddBindEntry](#addbindentry)|기본 접근자를 재정의할 때 출력 열에 바인드 항목을 추가 합니다.|
|[CDynamicAccessor](#cdynamicaccessor)|개체를 인스턴스화하고 초기화 `CDynamicAccessor` 합니다.|
|[닫기](#close)|모든 열을 바인딩 해제 하 고 할당 된 메모리를 해제 하며 클래스에서 [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) 인터페이스 포인터를 해제 합니다.|
|[GetBlobHandling](#getblobhandling)|현재 행에 대 한 BLOB 처리 값을 검색 합니다.|
|[GetBlobSizeLimit](#getblobsizelimit)|최대 BLOB 크기 (바이트)를 검색 합니다.|
|[GetBookmark](#getbookmark)|현재 행에 대 한 책갈피를 검색 합니다.|
|[GetColumnCount](#getcolumncount)|행 집합의 열 수를 검색 합니다.|
|[GetColumnFlags](#getcolumnflags)|열 특징을 검색 합니다.|
|[GetColumnInfo](#getcolumninfo)|열 메타 데이터를 검색 합니다.|
|[GetColumnName](#getcolumnname)|지정 된 열의 이름을 검색 합니다.|
|[GetColumnType](#getcolumntype)|지정 된 열의 데이터 형식을 검색 합니다.|
|[GetLength](#getlength)|열의 최대 가능한 길이 (바이트)를 검색 합니다.|
|[GetOrdinal](#getordinal)|열 이름이 지정 된 경우 열 인덱스를 검색 합니다.|
|[GetStatus](#getstatus)|지정 된 열의 상태를 검색 합니다.|
|[GetValue](#getvalue)|버퍼에서 데이터를 검색 합니다.|
|[SetBlobHandling](#setblobhandling)|현재 행에 대 한 BLOB 처리 값을 설정 합니다.|
|[SetBlobSizeLimit](#setblobsizelimit)|최대 BLOB 크기 (바이트)를 설정 합니다.|
|[SetLength](#setlength)|열의 길이 (바이트)를 설정 합니다.|
|[SetStatus](#setstatus)|지정 된 열의 상태를 설정 합니다.|
|[SetValue](#setvalue)|데이터를 버퍼에 저장 합니다.|

## <a name="remarks"></a>설명

메서드를 사용 하 여 열 `CDynamicAccessor` 이름, 열 수, 데이터 형식 등의 열 정보를 가져올 수 있습니다. 그런 다음이 열 정보를 사용 하 여 런타임에 동적으로 접근자를 만듭니다.

열 정보는이 클래스로 만들고 관리 하는 버퍼에 저장 됩니다. [GetValue](#getvalue)를 사용 하 여 버퍼에서 데이터를 가져옵니다.

동적 접근자 클래스 사용에 대 한 설명 및 예제는 [동적 접근자 사용](../../data/oledb/using-dynamic-accessors.md)을 참조 하세요.

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a> CDynamicAccessor:: AddBindEntry

출력 열에 바인드 항목을 추가 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>매개 변수

*나타납니다*<br/>
진행 `DBCOLUMNINFO` 열 정보를 포함 하는 구조체입니다. *OLE DB 프로그래머 참조*에서 [IColumnsInfo:: GETCOLUMNINFO](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 의 "DBCOLUMNINFO 구조체"를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

로 만든 기본 접근자를 재정의할 때이 메서드를 사용 `CDynamicAccessor` 합니다 ( [데이터를 인출 하려면 어떻게 해야 하나요?](../../data/oledb/fetching-data.md)참조).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a> CDynamicAccessor:: CDynamicAccessor

개체를 인스턴스화하고 초기화 `CDynamicAccessor` 합니다.

### <a name="syntax"></a>구문

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>매개 변수

*Eblob 처리*<br/>
BLOB (binary large object) 데이터를 처리 하는 방법을 지정 합니다. 기본값은 DBBLOBHANDLING_DEFAULT입니다. DBBLOBHANDLINGENUM 값에 대 한 설명은 [Setblobhandling](#setblobhandling) 를 참조 하세요.

*nBlobSize*<br/>
최대 BLOB 크기 (바이트)입니다. 이 값에 대 한 열 데이터는 BLOB으로 처리 됩니다. 기본값은 8000입니다. 자세한 내용은 [Setblobsizelimit](#setblobsizelimit) 를 참조 하세요.

### <a name="remarks"></a>설명

생성자를 사용 하 여 개체를 초기화 하는 경우 `CDynamicAccessor` blob을 바인딩하는 방법을 지정할 수 있습니다. Blob은 그래픽, 소리 또는 컴파일된 코드와 같은 이진 데이터를 포함할 수 있습니다. 기본 동작은 8000 바이트를 초과 하는 열을 Blob으로 처리 하 고 개체에 바인딩하는 것입니다 `ISequentialStream` . 그러나 다른 값을 BLOB 크기로 지정할 수 있습니다.

에서 blob 데이터로 한정 되는 열 데이터를 처리 하는 방법을 지정할 수도 있습니다 .이는 blob 데이터를 기본 방식으로 처리할 수 있습니다. 즉, blob 데이터는 `CDynamicAccessor` 무시 (바인딩하지 않음) 하거나 공급자가 할당 한 메모리에 blob 데이터를 바인딩할 수 있습니다.

## <a name="cdynamicaccessorclose"></a><a name="close"></a> CDynamicAccessor:: Close

모든 열을 바인딩 해제 하 고 할당 된 메모리를 해제 하며 클래스에서 [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) 인터페이스 포인터를 해제 합니다.

### <a name="syntax"></a>구문

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a> CDynamicAccessor:: GetBlobHandling

현재 행에 대 한 BLOB 처리 값을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>설명

[Setblobhandling](#setblobhandling)에 의해 설정 된 대로 BLOB 처리 값 *eblob* 처리를 반환 합니다.

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a> CDynamicAccessor:: GetBlobSizeLimit

최대 BLOB 크기 (바이트)를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>설명

[Setblobsizelimit](#setblobsizelimit)로 설정 된 대로 BLOB 처리 값 *nBlobSize* 를 반환 합니다.

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a> CDynamicAccessor:: GetBookmark

현재 행에 대 한 책갈피를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>매개 변수

*pBookmark*<br/>
제한이 [CBookmark](../../data/oledb/cbookmark-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

`DBPROP_IRowsetLocate`책갈피를 검색 하려면 VARIANT_TRUE으로 설정 해야 합니다.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a> CDynamicAccessor:: GetColumnCount

열 수를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Return Value

검색 된 열의 수입니다.

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a> CDynamicAccessor:: GetColumnFlags

열 특징을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pFlags*<br/>
제한이 열 특징을 설명 하는 비트 마스크에 대 한 포인터입니다. *OLE DB 프로그래머 참조*의 [IColumnsInfo:: GETCOLUMNINFO](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 에서 "DBCOLUMNFLAGS 열거 형식"을 참조 하세요.

### <a name="return-value"></a>반환 값

**`true`** 열 특징이 성공적으로 검색 되 면를 반환 합니다. 그렇지 않으면를 반환 **`false`** 합니다.

### <a name="remarks"></a>설명

열 번호는 1에서 오프셋 됩니다. 열 0은 특수 한 경우입니다. 사용 가능한 경우 책갈피입니다.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a> CDynamicAccessor:: GetColumnInfo

대부분의 소비자에 필요한 열 메타데이터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>매개 변수

*pRowset*<br/>
진행 [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) 인터페이스에 대 한 포인터입니다.

*pColumns*<br/>
제한이 행 집합의 열 수를 반환할 메모리에 대 한 포인터입니다. 이 숫자에는 책갈피 열 (있는 경우)이 포함 됩니다.

*ppColumnInfo*<br/>
제한이 구조체의 배열을 반환할 메모리에 대 한 포인터 `DBCOLUMNINFO` 입니다. *OLE DB 프로그래머 참조*에서 [IColumnsInfo:: GETCOLUMNINFO](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 의 "DBCOLUMNINFO 구조체"를 참조 하세요.

*ppStringsBuffer*<br/>
제한이 단일 할당 블록 내에서 모든 문자열 값 ( *columnid* 또는 for *pwszName*내에서 사용 되는 이름)의 저장소에 대 한 포인터를 반환할 메모리에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

데이터 형식, 및에 대 한 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 를 참조 하세요 `DBORDINAL` `DBCOLUMNINFO` `OLECHAR` .

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a> CDynamicAccessor:: GetColumnName

지정 된 열의 이름을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

### <a name="return-value"></a>반환 값

지정된 열의 이름입니다.

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a> CDynamicAccessor:: GetColumnType

지정 된 열의 데이터 형식을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pType*<br/>
제한이 지정 된 열의 데이터 형식에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 성공 시 또는 실패 시 반환 **`false`** 됩니다.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a> CDynamicAccessor:: GetLength

지정 된 열의 길이를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pLength*<br/>
제한이 열의 길이 (바이트)를 포함 하는 정수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 열이 있으면를 반환 합니다. 그렇지 않으면이 함수는을 반환 **`false`** 합니다.

### <a name="remarks"></a>설명

첫 번째 재정의는 열 번호를 사용 하 고 두 번째와 세 번째 재정의는 각각 ANSI 또는 유니코드 형식으로 열 이름을 사용 합니다.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a> CDynamicAccessor:: GetOrdinal

열 이름이 지정 된 경우 열 번호를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>매개 변수

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pOrdinal*<br/>
제한이 열 번호에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 이름의 열이 있으면를 반환 합니다. 그렇지 않으면이 함수는을 반환 **`false`** 합니다.

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a> CDynamicAccessor:: GetStatus

지정 된 열의 상태를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pStatus*<br/>
제한이 열 상태를 포함 하는 변수에 대 한 포인터입니다. 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [dbstatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 열이 있으면를 반환 합니다. 그렇지 않으면이 함수는을 반환 **`false`** 합니다.

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a> CDynamicAccessor:: GetValue

지정 된 열에 대 한 데이터를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>매개 변수

*ctype*<br/>
진행 특수 처리를 필요로 하는 문자열 형식 ( `CHAR*` ,)을 제외한 모든 데이터 형식을 처리 하는 템플릿 매개 변수입니다 `WCHAR*` . `GetValue` 는 여기에서 지정한 내용에 따라 적절 한 데이터 형식을 사용 합니다.

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pColumnName*<br/>
진행 열 이름입니다.

*pData*<br/>
제한이 지정 된 열의 내용에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

문자열 데이터를 전달 하려는 경우 템플릿이 아닌 버전의를 사용 `GetValue` 합니다. 이 메서드의 템플릿이 아닌 버전은 지정 된 **`void*`** 열 데이터를 포함 하는 버퍼의 일부를 가리키는을 반환 합니다. 열을 찾을 수 없는 경우 NULL을 반환 합니다.

다른 모든 데이터 형식의 경우 템플릿 버전의를 사용 하는 것이 더 간단 합니다 `GetValue` . 템플릿 버전은 **`true`** 성공 시 또는 실패 시 반환 **`false`** 됩니다.

### <a name="remarks"></a>설명

비 템플릿 버전을 사용 하 여 문자열을 포함 하는 열과 다른 데이터 형식이 포함 된 열에 대 한 템플릿 버전을 반환 합니다.

디버그 모드에서는 *.pdata* 의 크기가 가리키는 열의 크기와 같지 않은 경우 어설션을 받게 됩니다.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a> CDynamicAccessor:: SetBlobHandling

현재 행에 대 한 BLOB 처리 값을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>매개 변수

*Eblob 처리*<br/>
BLOB 데이터를 처리 하는 방법을 지정 합니다. 사용되는 값은 다음과 같습니다.

- DBBLOBHANDLING_DEFAULT: BLOB 데이터로 *nBlobSize* (로 설정 됨) 보다 큰 열 데이터 `SetBlobSizeLimit` 를 처리 하 고 또는 개체를 통해 검색 `ISequentialStream` `IStream` 합니다. 이 옵션은 *nBlobSize* 보다 큰 데이터를 포함 하는 모든 열을 바인딩하거나 BLOB 데이터로 DBTYPE_IUNKNOWN로 나열 하려고 합니다.

- DBBLOBHANDLING_NOSTREAMS: *nBlobSize* (로 설정 됨) 보다 큰 열 데이터를 `SetBlobSizeLimit` BLOB 데이터로 처리 하 고 공급자가 할당 한 소비자 소유의 메모리에서 참조를 통해 검색 합니다. 이 옵션은 둘 이상의 BLOB 열이 있는 테이블에 유용 하며, 공급자는 `ISequentialStream` 접근자 당 하나의 개체만 지원 합니다.

- DBBLOBHANDLING_SKIP: 포함 하는 Blob으로 한정 된 (바인딩하지 않음) 열 (접근자는 열 값을 바인딩하거나 검색 하지는 않지만 열 상태 및 길이는 검색) 합니다.

### <a name="remarks"></a>설명

`SetBlobHandling`를 호출하기 전에 `Open`를 호출해야 합니다.

생성자 메서드 [Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 는 DBBLOBHANDLING_DEFAULT BLOB 처리 값을 설정 합니다.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a> CDynamicAccessor:: SetBlobSizeLimit

최대 BLOB 크기 (바이트)를 설정 합니다.

### <a name="syntax"></a>구문

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>매개 변수

*nBlobSize*<br/>
BLOB 크기 제한을 지정 합니다.

### <a name="remarks"></a>설명

최대 BLOB 크기 (바이트)를 설정 합니다. 이 값 보다 큰 열 데이터는 BLOB으로 처리 됩니다. 일부 공급자는 열에 대해 매우 큰 크기 (예: 2gb)를 제공 합니다. 이 크기의 열에 메모리를 할당 하는 대신 일반적으로 이러한 열을 Blob로 바인딩합니다. 이렇게 하면 모든 메모리를 할당할 필요가 없지만 잘림에 대 한 걱정 없이 모든 데이터를 계속 읽을 수 있습니다. 그러나 `CDynamicAccessor` 원시 데이터 형식에서 많은 열을 강제로 바인딩하려는 경우도 있습니다. 이렇게 하려면를 호출 `SetBlobSizeLimit` 하기 전에를 호출 `Open` 합니다.

생성자 메서드 [Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 는 최대 BLOB 크기를 기본값인 8000 바이트로 설정 합니다.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a> CDynamicAccessor:: SetLength

지정 된 열의 길이를 설정 합니다.

### <a name="syntax"></a>구문

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*nLength*<br/>
진행 열의 길이 (바이트)입니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 열 길이가 성공적으로 설정 되 면를 반환 합니다. 그렇지 않으면이 함수는을 반환 **`false`** 합니다.

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a> CDynamicAccessor:: SetStatus

지정 된 열의 상태를 설정 합니다.

### <a name="syntax"></a>구문

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*status*<br/>
진행 열 상태입니다. 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [dbstatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) 를 참조 하세요.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 열 상태가 성공적으로 설정 된 경우를 반환 합니다. 그렇지 않으면이 함수는을 반환 **`false`** 합니다.

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a> CDynamicAccessor:: SetValue

지정 된 열에 데이터를 저장 합니다.

### <a name="syntax"></a>구문

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>매개 변수

*ctype*<br/>
진행 특수 처리를 필요로 하는 문자열 형식 ( `CHAR*` ,)을 제외한 모든 데이터 형식을 처리 하는 템플릿 매개 변수입니다 `WCHAR*` . `GetValue` 는 여기에서 지정한 내용에 따라 적절 한 데이터 형식을 사용 합니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

*data*<br/>
진행 데이터를 포함 하는 메모리에 대 한 포인터입니다.

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

### <a name="return-value"></a>반환 값

문자열 데이터를 설정 하려는 경우 템플릿이 아닌 버전의를 사용 `GetValue` 합니다. 이 메서드의 템플릿이 아닌 버전은 지정 된 **`void*`** 열 데이터를 포함 하는 버퍼의 일부를 가리키는을 반환 합니다. 열을 찾을 수 없는 경우 NULL을 반환 합니다.

다른 모든 데이터 형식의 경우 템플릿 버전의를 사용 하는 것이 더 간단 합니다 `GetValue` . 템플릿 버전은 **`true`** 성공 시 또는 실패 시 반환 **`false`** 됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 클래스](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 클래스](../../data/oledb/cmanualaccessor-class.md)
