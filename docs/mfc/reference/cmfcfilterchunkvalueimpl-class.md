---
description: '자세한 정보: CMFCFilterChunkValueImpl 클래스'
title: CMFCFilterChunkValueImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: f2db7fdf6d6d24cb906b3190d34310e1f6724194
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265469"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 클래스

이 클래스는 청크 및 속성 값 쌍 논리를 단순화 하는 클래스입니다.

## <a name="syntax"></a>구문

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|개체를 Destructs 합니다.|
|[CMFCFilterChunkValueImpl:: CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCFilterChunkValueImpl:: Clear](#clear)|ChunkValue를 지웁니다.|
|[CMFCFilterChunkValueImpl:: CopyChunk](#copychunk)|청크의 특성을 설명 하는 구조체에이 청크를 복사 합니다.|
|[CMFCFilterChunkValueImpl:: CopyFrom](#copyfrom)|다른 값에서이 청크 값을 초기화 합니다.|
|[CMFCFilterChunkValueImpl:: GetChunkGUID](#getchunkguid)|청크 GUID를 검색 합니다.|
|[CMFCFilterChunkValueImpl:: GetChunkPID](#getchunkpid)|청크 PID (속성 ID)를 검색 합니다.|
|[CMFCFilterChunkValueImpl:: GetChunkType](#getchunktype)|청크 유형을 가져옵니다.|
|[CMFCFilterChunkValueImpl:: GetString](#getstring)|문자열 값을 검색 합니다.|
|[CMFCFilterChunkValueImpl:: GetValue](#getvalue)|할당 된 propvariant로 값을 검색 합니다.|
|[CMFCFilterChunkValueImpl:: GetValueNoAlloc](#getvaluenoalloc)|할당 되지 않은 (내부 값) 값을 반환 합니다.|
|[CMFCFilterChunkValueImpl:: IsValid](#isvalid)|이 속성 값이 유효한 지 여부를 확인 합니다.|
|[CMFCFilterChunkValueImpl:: SetBoolValue](#setboolvalue)|오버로드됨. 키로 속성을 부울로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetDwordValue](#setdwordvalue)|키로 속성을 DWORD로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetFileTimeValue](#setfiletimevalue)|키를 기준으로 속성을 filetime으로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetInt64Value](#setint64value)|키로 속성을 int64로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetIntValue](#setintvalue)|키로 속성을 int로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetLongValue](#setlongvalue)|키로 속성을 LONG으로 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetSystemTimeValue](#setsystemtimevalue)|SystemTime에 대 한 키로 속성을 설정 합니다.|
|[CMFCFilterChunkValueImpl:: SetTextValue](#settextvalue)|키로 속성을 유니코드 문자열로 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCFilterChunkValueImpl:: SetChunk](#setchunk)|청크의 공용 속성을 설정 하는 도우미 함수입니다.|

## <a name="remarks"></a>설명

을 사용 하려면 올바른 종류의 CMFCFilterChunkValueImpl 클래스를 만들기만 하면 됩니다.

예제:

CMFCFilterChunkValueImpl 청크;

hr = 청크. SetBoolValue (PKEY_IsAttachment, true);

또는

hr = 청크. SetFileTimeValue (PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a> CMFCFilterChunkValueImpl:: Clear

ChunkValue를 지웁니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a> CMFCFilterChunkValueImpl:: CMFCFilterChunkValueImpl

개체를 생성합니다.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a> CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl

개체를 Destructs 합니다.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a> CMFCFilterChunkValueImpl:: CopyChunk

청크의 특성을 설명 하는 구조체에이 청크를 복사 합니다.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>매개 변수

*pStatChunk*<br/>
청크의 특성을 설명 하는 대상 값에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a> CMFCFilterChunkValueImpl:: CopyFrom

다른 값에서이 청크 값을 초기화 합니다.

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>매개 변수

*pValue*<br/>
복사할 원본 값을 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a> CMFCFilterChunkValueImpl:: GetChunkGUID

청크 GUID를 검색 합니다.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>반환 값

청크를 식별 하는 GUID에 대 한 참조입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a> CMFCFilterChunkValueImpl:: GetChunkPID

청크 PID (속성 ID)를 검색 합니다.

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>반환 값

속성 ID를 포함 하는 DWORD 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a> CMFCFilterChunkValueImpl:: GetChunkType

청크 유형을 검색 합니다.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>반환 값

현재 청크가 텍스트 형식 속성 인지 또는 값 형식 속성 인지를 지정 하는 CHUNKSTATE 열거형 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a> CMFCFilterChunkValueImpl:: GetString

문자열 값을 검색 합니다.

```
CString &GetString();
```

### <a name="return-value"></a>반환 값

청크 값을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a> CMFCFilterChunkValueImpl:: GetValue

할당 된 propvariant로 값을 검색 합니다.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>매개 변수

*ppPropVariant*<br/>
함수가 반환 될 때이 매개 변수에는 청크 값이 포함 됩니다.

### <a name="return-value"></a>반환 값

PROPVARIANT가 성공적으로 할당 되었고 청크 값이 *Pppropvariant* 에 복사 되었는지 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a> CMFCFilterChunkValueImpl:: GetValueNoAlloc

할당 되지 않은 (내부 값) 값을 반환 합니다.

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>반환 값

현재 청크 값을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a> CMFCFilterChunkValueImpl:: IsValid

이 속성 값이 유효한 지 여부를 확인 합니다.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

현재 청크 값이 유효 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a> CMFCFilterChunkValueImpl:: SetBoolValue

오버로드됨. 키로 속성을 부울로 설정 합니다.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*bVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a> CMFCFilterChunkValueImpl:: SetChunk

청크의 공용 속성을 설정 하는 도우미 함수입니다.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a> CMFCFilterChunkValueImpl:: SetDwordValue

키로 속성을 DWORD로 설정 합니다.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*dwVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a> CMFCFilterChunkValueImpl:: SetFileTimeValue

키로 속성을 filetime으로 설정 합니다.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*dtVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a> CMFCFilterChunkValueImpl:: SetInt64Value

키로 속성을 int64로 설정 합니다.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*nVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a> CMFCFilterChunkValueImpl:: SetIntValue

키로 속성을 int로 설정 합니다.

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*nVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a> CMFCFilterChunkValueImpl:: SetLongValue

키로 속성을 LONG으로 설정 합니다.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*lVal*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a> CMFCFilterChunkValueImpl:: SetSystemTimeValue

SystemTime에 대 한 키로 속성을 설정 합니다.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*systemTime*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a> CMFCFilterChunkValueImpl:: SetTextValue

키로 속성을 유니코드 문자열로 설정 합니다.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>매개 변수

*pkey*<br/>
속성 키를 지정 합니다.

*pszValue*<br/>
설정할 청크 값을 지정 합니다.

*chunkType*<br/>
플래그는이 청크에 텍스트 형식 또는 값 형식 속성이 포함 되어 있는지 여부를 나타냅니다. 플래그 값은 CHUNKSTATE 열거형에서 가져옵니다.

*locale*<br/>
텍스트 청크에 연결 된 언어 및 하위 언어입니다. 청크 로캘은 문서 인덱서에 텍스트의 적절 한 단어 분리를 수행 하는 데 사용 됩니다. 청크가 텍스트 형식이 나 데이터 형식이 VT_LPWSTR, VT_LPSTR 또는 VT_BSTR 인 값 형식이 아닌 경우이 필드는 무시 됩니다.

*cwcLenSource*<br/>
현재 청크가 파생 된 소스 텍스트의 문자 길이입니다. 0 값은 소스 텍스트와 파생 된 텍스트 간의 문자별 일치를 나타냅니다. 0이 아닌 값은 이러한 직접 대응이 없다는 것을 의미 합니다.

*cwcStartSource*<br/>
파생 청크의 소스 텍스트가 소스 청크에 시작 하는 오프셋입니다.

*청크 유형*<br/>
이전 청크를 현재 청크의 분리 하는 break의 형식입니다. CHUNK_BREAKTYPE 열거형의 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
