---
description: '자세히 알아보기: IDispEventImpl 클래스'
title: IDispEventImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: 7266052da8985791bdb85682b37572241cb0535b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158389"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 클래스

이 클래스는 메서드의 구현을 제공 `IDispatch` 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>매개 변수

*nID*<br/>
원본 개체의 고유 식별자입니다. `IDispEventImpl`이 복합 컨트롤의 기본 클래스인 경우이 매개 변수에 대해 원하는 포함 된 컨트롤의 리소스 ID를 사용 합니다. 임의의 양의 정수를 사용 하는 경우도 있습니다.

*T*<br/>
에서 파생 되는 사용자의 클래스입니다 `IDispEventImpl` .

*pdiid*<br/>
이 클래스에서 구현 하는 이벤트 클래스의 IID에 대 한 포인터입니다. 이 인터페이스는 *plibid*, *Wmajor* 및 *wmajor* 로 표시 되는 형식 라이브러리에 정의 되어야 합니다.

*plibid*<br/>
*Pdiid* 가 가리키는 디스패치 인터페이스를 정의 하는 형식 라이브러리에 대 한 포인터입니다. **GUID_NULL&** 경우 형식 라이브러리가 이벤트를 소싱 하는 개체에서 로드 됩니다.

*wMajor*<br/>
형식 라이브러리의 주 버전입니다. 기본값은 0입니다.

*wMinor*<br/>
형식 라이브러리의 부 버전입니다. 기본값은 0입니다.

*tihclass*<br/>
*T* 의 형식 정보를 관리 하는 데 사용 되는 클래스입니다. 기본값은 형식의 클래스 이지만 `CComTypeInfoHolder` 이외의 형식 클래스를 제공 하 여이 템플릿 매개 변수를 재정의할 수 있습니다 `CComTypeInfoHolder` .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[IDispEventImpl:: _tihclass](../../atl/reference/idispeventimpl-class.md)|형식 정보를 관리 하는 데 사용 되는 클래스입니다. 기본적으로 `CComTypeInfoHolder`입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[IDispEventImpl:: IDispEventImpl](#idispeventimpl)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IDispEventImpl:: GetFuncInfoFromId](#getfuncinfofromid)|지정 된 디스패치 식별자에 대 한 함수 인덱스를 찾습니다.|
|[IDispEventImpl:: Idispatch.getidsofnames](#getidsofnames)|단일 멤버와 선택적 인수 이름 집합을 해당 하는 정수 Dispid 집합에 매핑합니다.|
|[IDispEventImpl:: GetTypeInfo](#gettypeinfo)|개체에 대 한 형식 정보를 검색 합니다.|
|[IDispEventImpl:: GetTypeInfoCount](#gettypeinfocount)|형식 정보 인터페이스의 수를 검색 합니다.|
|[IDispEventImpl:: GetUserDefinedType](#getuserdefinedtype)|사용자 정의 형식의 기본 형식을 검색 합니다.|

## <a name="remarks"></a>설명

`IDispEventImpl` 해당 인터페이스의 모든 메서드/이벤트에 대해 구현 코드를 제공할 필요 없이 이벤트 인터페이스를 구현 하는 방법을 제공 합니다. `IDispEventImpl` 메서드의 구현을 제공 `IDispatch` 합니다. 처리 하는 데 관심이 있는 이벤트에 대 한 구현을 제공 하기만 하면 됩니다.

`IDispEventImpl` 는 클래스의 이벤트 싱크 맵과 함께 작동 하 여 이벤트를 적절 한 처리기 함수로 라우팅합니다. 이 클래스를 사용 하려면 다음을 수행 합니다.

처리 하려는 각 개체의 각 이벤트에 대 한 이벤트 싱크 맵에 [SINK_ENTRY](composite-control-macros.md#sink_entry) 또는 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) 매크로를 추가 합니다. `IDispEventImpl`복합 컨트롤의 기본 클래스로를 사용 하는 경우 [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) 를 호출 하 여 이벤트 싱크 맵의 모든 항목에 대 한 이벤트 원본과의 연결을 설정 하 고 중단할 수 있습니다. 다른 경우 또는 더 높은 제어를 위해 [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) 를 호출 하 여 소스 개체와 기본 클래스 간의 연결을 설정 합니다. [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) 를 호출 하 여 연결을 중단 합니다.

`IDispEventImpl`이벤트를 처리 해야 하는 각 개체에 대해 ( *nID* 에 고유한 값을 사용 하 여)에서 파생 해야 합니다. 한 소스 개체에 대해 unadvising 하 여 기본 클래스를 다시 사용할 수 있습니다. 그런 다음 다른 소스 개체에 대해 알려 주지만 단일 개체에서 한 번에 처리할 수 있는 최대 소스 개체 수는 기본 클래스 수에 의해 제한 됩니다 `IDispEventImpl` .

`IDispEventImpl`[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)와 동일한 기능을 제공 합니다. 단, 형식 라이브러리에서 인터페이스에 대 한 형식 정보를 [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) 구조체에 대 한 포인터로 제공 하지 않고 가져옵니다. `IDispEventSimpleImpl`이벤트 인터페이스를 설명 하는 형식 라이브러리가 없거나 형식 라이브러리를 사용 하 여와 관련 된 오버 헤드를 방지 하려는 경우에 사용 합니다.

> [!NOTE]
> `IDispEventImpl` 및는 `IDispEventSimpleImpl` `IUnknown::QueryInterface` `IDispEventImpl` `IDispEventSimpleImpl` 기본 com 개체의 클래스 멤버에 직접 액세스할 수 있도록 하는 동시에 각 및 기본 클래스가 별도의 COM id 역할을 할 수 있도록 하는 고유한 구현을 제공 합니다.

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

자세한 내용은 [IDispEventImpl 지원](../../atl/supporting-idispeventimpl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a> IDispEventImpl:: GetFuncInfoFromId

지정 된 디스패치 식별자에 대 한 함수 인덱스를 찾습니다.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 함수 ID에 대 한 참조입니다.

*dispidMember*<br/>
진행 함수의 디스패치 ID입니다.

*lcid*<br/>
진행 함수 ID의 로캘 컨텍스트입니다.

*나타납니다*<br/>
진행 함수가 호출 되는 방법을 나타내는 구조체입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a> IDispEventImpl:: Idispatch.getidsofnames

단일 멤버와 선택적 인수 이름 집합을 해당 하는 정수 Dispid 집합에 매핑합니다 .이는 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)에 대 한 후속 호출에 사용할 수 있습니다.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 를 참조 하세요.

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispEventImpl:: GetTypeInfo

인터페이스의 형식 정보를 가져오는 데 사용할 수 있는 개체의 형식 정보를 검색합니다.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>설명

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispEventImpl:: GetTypeInfoCount

개체에서 제공하는 형식 정보 인터페이스의 수를 검색합니다(0 또는 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 를 참조 하세요.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a> IDispEventImpl:: GetUserDefinedType

사용자 정의 형식의 기본 형식을 검색 합니다.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>매개 변수

*pTI*<br/>
진행 사용자 정의 형식을 포함 하는 [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) 인터페이스에 대 한 포인터입니다.

*hrt*<br/>
진행 검색할 형식 설명에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

변형 유형입니다.

### <a name="remarks"></a>설명

[ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)를 참조 하세요.

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a> IDispEventImpl:: IDispEventImpl

생성자입니다. 클래스 템플릿 매개 변수 *plibid*, *pdiid*, *wmajor* 및 *wmajor* 의 값을 저장 합니다.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a> IDispEventImpl:: tihclass

이 typedef는 클래스 템플릿 매개 변수 *tihclass* 의 인스턴스입니다.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>설명

기본적으로 클래스는 `CComTypeInfoHolder` 입니다. `CComTypeInfoHolder` 클래스에 대 한 형식 정보를 관리 합니다.

## <a name="see-also"></a>참고 항목

[_ATL_FUNC_INFO 구조체](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 클래스](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 클래스](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
