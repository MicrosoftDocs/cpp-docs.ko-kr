---
description: '자세한 정보: CPropExchange 클래스'
title: CPropExchange 클래스
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: 3e95940a6ba649b134df3cfc79abcf85e03f7e8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343313"
---
# <a name="cpropexchange-class"></a>CPropExchange 클래스

OLE 컨트롤의 지속성 구현을 지원합니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPropExchange:: ExchangeBlobProp](#exchangeblobprop)|BLOB (binary large object) 속성을 교환 합니다.|
|[CPropExchange:: ExchangeFontProp](#exchangefontprop)|Font 속성을 교환 합니다.|
|[CPropExchange:: ExchangePersistentProp](#exchangepersistentprop)|컨트롤과 파일 간에 속성을 교환 합니다.|
|[CPropExchange:: ExchangeProp](#exchangeprop)|기본 제공 형식의 속성을 교환 합니다.|
|[CPropExchange:: ExchangeVersion](#exchangeversion)|OLE 컨트롤의 버전 번호를 교환 합니다.|
|[CPropExchange:: GetVersion](#getversion)|OLE 컨트롤의 버전 번호를 검색 합니다.|
|[CPropExchange:: IsAsynchronous](#isasynchronous)|속성 교환이 비동기적으로 수행 되는지 여부를 결정 합니다.|
|[CPropExchange:: IsLoading](#isloading)|속성이 컨트롤에 로드 되는지 또는 해당 컨트롤에서 저장 되는지 여부를 나타냅니다.|

## <a name="remarks"></a>설명

`CPropExchange` 에 기본 클래스가 없습니다.

속성 교환의 컨텍스트 및 방향을 설정 합니다.

지 속성은 컨트롤의 상태 정보 (일반적으로 컨트롤 자체와 미디어 사이에 속성으로 표시 됨)의 교환입니다.

프레임 워크는 `CPropExchange` OLE 컨트롤의 속성을 영구 저장소에서 로드 하거나 영구 저장소에 저장 해야 한다는 알림이 표시 될 때에서 파생 된 개체를 생성 합니다.

프레임 워크는이 개체에 대 한 포인터를 `CPropExchange` 컨트롤의 `DoPropExchange` 함수에 전달 합니다. 마법사를 사용 하 여 컨트롤에 대 한 시작 파일을 만든 경우 컨트롤의 함수는를 `DoPropExchange` 호출 `COleControl::DoPropExchange` 합니다. 기본 클래스 버전은 컨트롤의 스톡 속성을 교환 합니다. 파생 클래스의 버전을 컨트롤에 추가한 속성을 교환 합니다.

`CPropExchange` 컨트롤을 로드 하거나 만들 때 컨트롤의 속성을 serialize 하거나 컨트롤의 속성을 초기화 하는 데 사용할 수 있습니다. `ExchangeProp`의 및 `ExchangeFontProp` 멤버 함수는 `CPropExchange` 다른 미디어에서 속성을 저장 하 고 로드할 수 있습니다.

사용에 대 한 자세한 내용은 `CPropExchange` [MFC ActiveX 컨트롤: 속성 페이지](../../mfc/mfc-activex-controls-property-pages.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CPropExchange`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a> CPropExchange:: ExchangeBlobProp

BLOB (binary large object) 데이터를 저장 하는 속성을 직렬화 합니다.

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>매개 변수

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*phBlob*<br/>
속성이 저장 된 위치를 가리키는 변수에 대 한 포인터입니다. 일반적으로 변수는 클래스의 멤버입니다.

*hBlobDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *Phblob* 에서 참조 하는 변수를 적절 하 게 읽거나 쓸 수 있습니다. *Hblobdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization이 실패 하는 경우이 값이 사용 됩니다.

`CArchivePropExchange::ExchangeBlobProp`, 및 함수는 `CResetPropExchange::ExchangeBlobProp` `CPropsetPropExchange::ExchangeBlobProp` 이 순수 가상 함수를 재정의 합니다.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a> CPropExchange:: ExchangeFontProp

저장소 미디어와 컨트롤 간에 font 속성을 교환 합니다.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>매개 변수

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*굵게*<br/>
Font 속성을 포함 하는 [Cfontholder](../../mfc/reference/cfontholder-class.md) 개체에 대 한 참조입니다.

*pFontDesc*<br/>
*PFontDispAmbient* 가 NULL 일 때 font 속성의 기본 상태를 초기화 하는 값을 포함 하는 글꼴에 [대 한 포인터](/windows/win32/api/olectl/ns-olectl-fontdesc) 입니다.

*pFontDispAmbient*<br/>
`IFontDisp`글꼴 속성의 기본 상태를 초기화 하는 데 사용 되는 글꼴의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

글꼴 속성이 중간에서 컨트롤로 로드 되는 경우 글꼴의 특징이 미디어에서 검색 되 고 `CFontHolder` *글꼴* 에서 참조 하는 개체는이를 사용 하 여 초기화 됩니다. Font 속성을 저장 하는 경우 글꼴 개체의 특성이 미디어에 기록 됩니다.

`CArchivePropExchange::ExchangeFontProp`, 및 함수는 `CResetPropExchange::ExchangeFontProp` `CPropsetPropExchange::ExchangeFontProp` 이 순수 가상 함수를 재정의 합니다.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a> CPropExchange:: ExchangePersistentProp

컨트롤과 파일 간에 속성을 교환 합니다.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>매개 변수

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*ppUnk*<br/>
속성의 인터페이스에 대 한 포인터를 포함 하는 변수에 대 한 포인터 `IUnknown` 입니다 .이 변수는 일반적으로 클래스의 멤버입니다.

*iid*<br/>
컨트롤에서 사용할 속성의 인터페이스 ID입니다.

*pUnkDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성이 파일에서 컨트롤로 로드 되는 경우 속성은 파일에서 만들어지고 초기화 됩니다. 속성을 저장 하는 경우 해당 값이 파일에 기록 됩니다.

`CArchivePropExchange::ExchangePersistentProp`, 및 함수는 `CResetPropExchange::ExchangePersistentProp` `CPropsetPropExchange::ExchangePersistentProp` 이 순수 가상 함수를 재정의 합니다.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a> CPropExchange:: ExchangeProp

저장소 미디어와 컨트롤 간에 속성을 교환 합니다.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>매개 변수

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*vtProp*<br/>
교환할 속성의 형식을 지정 하는 기호입니다. 가능한 값은 다음과 같습니다.

|기호|속성 유형|
|------------|-------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_BOOL|**BOOL**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|

*pvProp*<br/>
속성의 값에 대 한 포인터입니다.

*pvDefault*<br/>
속성의 기본값에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성이 중간에서 컨트롤로 로드 되는 경우 속성의 값은 중간에서 검색 되 고 *pvProp* 가 가리키는 개체에 저장 됩니다. 속성이 중간에 저장 되는 경우 *pvProp* 가 가리키는 개체의 값이 미디어에 기록 됩니다.

`CArchivePropExchange::ExchangeProp`, 및 함수는 `CResetPropExchange::ExchangeProp` `CPropsetPropExchange::ExchangeProp` 이 순수 가상 함수를 재정의 합니다.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a> CPropExchange:: ExchangeVersion

버전 번호의 지 속성을 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>매개 변수

*dwVersionLoaded 됨*<br/>
로드 되는 영구 데이터의 버전 번호가 저장 되는 변수에 대 한 참조입니다.

*dwVersionDefault*<br/>
컨트롤의 현재 버전 번호입니다.

*bConvert*<br/>
영구 데이터를 현재 버전으로 변환할지 아니면 로드 된 버전과 동일한 버전으로 유지할지를 나타냅니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a> CPropExchange:: GetVersion

컨트롤의 버전 번호를 검색 하려면이 함수를 호출 합니다.

```
DWORD GetVersion();
```

### <a name="return-value"></a>반환 값

컨트롤의 버전 번호입니다.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a> CPropExchange:: IsAsynchronous

속성 교환이 비동기적으로 수행 되는지 여부를 결정 합니다.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>반환 값

속성이 비동기적으로 교환 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a> CPropExchange:: IsLoading

이 함수를 호출 하 여 속성을 컨트롤에 로드 하 고 있는지 여부를 확인 합니다.

```
BOOL IsLoading();
```

### <a name="return-value"></a>반환 값

속성이 로드 되 고 있으면 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
