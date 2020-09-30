---
title: IErrorRecordsImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: cb0e236a31846e3465d76b6904a7b4c57a2b8cf4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508997"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 클래스

**CAtlArray<** 형식의 데이터 멤버 ([m_rgErrors](#rgerrors))에서 레코드를 추가 하 고 검색 하 OLE DB [ierrorrecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스를 구현 합니다 `RecordClass` **>** .

## <a name="syntax"></a>구문

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IErrorRecordsImpl` 입니다.

*RecordClass*<br/>
OLE DB 오류 개체를 나타내는 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|오류 레코드에서 오류 설명 문자열을 가져옵니다.|
|[GetErrorGUID](#geterrorguid)|오류 레코드에서 오류 GUID를 가져옵니다.|
|[GetErrorHelpContext](#geterrorhelpcontext)|오류 레코드에서 도움말 컨텍스트 ID를 가져옵니다.|
|[GetErrorHelpFile](#geterrorhelpfile)|오류 레코드에서 도움말 파일의 전체 경로 이름을 가져옵니다.|
|[GetErrorSource](#geterrorsource)|오류 레코드에서 오류 소스 코드를 가져옵니다.|

### <a name="interface-methods"></a>인터페이스 메서드

| 속성 | 설명 |
|-|-|
|[AddErrorRecord](#adderrorrecord)|OLE DB error 개체에 레코드를 추가 합니다.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|반환 코드 및 공급자별 오류 번호와 같은 오류에 대 한 기본 정보를 반환 합니다.|
|[GetCustomErrorObject](#getcustomerrorobject)|사용자 지정 오류 개체의 인터페이스에 대 한 포인터를 반환 합니다.|
|[GetErrorInfo](#geterrorinfo)|지정 된 레코드에 대 한 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스 포인터를 반환 합니다.|
|[GetErrorParameters](#geterrorparameters)|오류 매개 변수를 반환 합니다.|
|[GetRecordCount](#getrecordcount)|OLE DB record 개체의 레코드 수를 반환 합니다.|

### <a name="data-members"></a>데이터 멤버

| 속성 | 설명 |
|-|-|
|[m_rgErrors](#rgerrors)|오류 레코드의 배열입니다.|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a> IErrorRecordsImpl:: Geterrordescription 문자열

오류 레코드에서 오류 설명 문자열을 가져옵니다.

### <a name="syntax"></a>구문

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>매개 변수

*rCurError*<br/>
`ERRORINFO`인터페이스의 레코드 `IErrorInfo` 입니다.

### <a name="return-value"></a>반환 값

오류를 설명 하는 문자열에 대 한 포인터입니다.

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a> IErrorRecordsImpl:: GetErrorGUID

오류 레코드에서 오류 GUID를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>매개 변수

*rCurError*<br/>
`ERRORINFO`인터페이스의 레코드 `IErrorInfo` 입니다.

### <a name="return-value"></a>반환 값

오류의 GUID에 대 한 참조입니다.

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a> IerrorrecordGetErrorHelpContext Pl::

오류 레코드에서 도움말 컨텍스트 ID를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>매개 변수

*rCurError*<br/>
`ERRORINFO`인터페이스의 레코드 `IErrorInfo` 입니다.

### <a name="return-value"></a>반환 값

오류에 대 한 도움말 컨텍스트 ID입니다.

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a> IerrorrecordGetErrorHelpFile Pl::

오류 레코드에서 도움말 파일의 경로 이름을 가져옵니다.

### <a name="syntax"></a>구문

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>매개 변수

*rCurError*<br/>
`ERRORINFO`인터페이스의 레코드 `IErrorInfo` 입니다.

### <a name="return-value"></a>반환 값

오류에 대 한 도움말 파일의 경로 이름을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a> IerrorrecordGetErrorSource Pl::

오류 레코드에서 오류를 발생 시킨 소스 코드를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>매개 변수

*rCurError*<br/>
`ERRORINFO`인터페이스의 레코드 `IErrorInfo` 입니다.

### <a name="return-value"></a>반환 값

오류에 대 한 소스 코드를 포함 하는 문자열에 대 한 포인터입니다.

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a> IerrorrecordAddErrorRecord Pl::

OLE DB error 개체에 레코드를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Ierrorrecords:: AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> IErrorRecordsImpl:: GetBasicErrorInfo

반환 코드 및 공급자별 오류 번호와 같은 오류에 대 한 기본 정보를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Ierrorrecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a> IerrorrecordGetCustomErrorObject Pl::

사용자 지정 오류 개체의 인터페이스에 대 한 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Ierrorrecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a> IErrorRecordsImpl:: GetErrorInfo

지정 된 레코드에 대 한 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Ierrorrecords:: geterrorinfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a> IErrorRecordsImpl:: GetErrorParameters

오류 매개 변수를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*의 [Ierrorrecords:: geterrorparameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a> IErrorRecordsImpl:: GetRecordCount

OLE DB record 개체의 레코드 수를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Ierrorrecords:: getrecordcount](/previous-versions/windows/desktop/ms722724(v=vs.85)) 를 참조 하세요.

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a> IErrorRecordsImpl:: m_rgErrors

오류 레코드의 배열입니다.

### <a name="syntax"></a>구문

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
