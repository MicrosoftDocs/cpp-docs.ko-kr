---
description: '자세히 알아보기: IDispEventSimpleImpl 클래스'
title: IDispEventSimpleImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 4b581f4e5714f595a29fb27bd6dbd45c7d5e401c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139505"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 클래스

이 클래스는 `IDispatch` 형식 라이브러리에서 형식 정보를 가져오지 않고 메서드의 구현을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>매개 변수

*nID*<br/>
원본 개체의 고유 식별자입니다. `IDispEventSimpleImpl`이 복합 컨트롤의 기본 클래스인 경우이 매개 변수에 대해 원하는 포함 된 컨트롤의 리소스 ID를 사용 합니다. 임의의 양의 정수를 사용 하는 경우도 있습니다.

*T*<br/>
에서 파생 되는 사용자의 클래스입니다 `IDispEventSimpleImpl` .

*pdiid*<br/>
이 클래스에서 구현 하는 이벤트 클래스의 IID에 대 한 포인터입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IDispEventSimpleImpl:: Advise](#advise)|기본 이벤트 원본에 대 한 연결을 설정 합니다.|
|[IDispEventSimpleImpl::D ispEventAdvise](#dispeventadvise)|이벤트 원본에 대 한 연결을 설정 합니다.|
|[IDispEventSimpleImpl::D ispEventUnadvise](#dispeventunadvise)|이벤트 원본에 대 한 연결을 중단 합니다.|
|[IDispEventSimpleImpl:: Idispatch.getidsofnames](#getidsofnames)|E_NOTIMPL을 반환합니다.|
|[IDispEventSimpleImpl:: GetTypeInfo](#gettypeinfo)|E_NOTIMPL을 반환합니다.|
|[IDispEventSimpleImpl:: GetTypeInfoCount](#gettypeinfocount)|E_NOTIMPL을 반환합니다.|
|[IDispEventSimpleImpl:: Invoke](#invoke)|이벤트 싱크 맵에 나열 된 이벤트 처리기를 호출 합니다.|
|[IDispEventSimpleImpl:: Unadvise](#unadvise)|기본 이벤트 원본에 대 한 연결을 중단 합니다.|

## <a name="remarks"></a>설명

`IDispEventSimpleImpl` 해당 인터페이스의 모든 메서드/이벤트에 대해 구현 코드를 제공할 필요 없이 이벤트 인터페이스를 구현 하는 방법을 제공 합니다. `IDispEventSimpleImpl` 메서드의 구현을 제공 `IDispatch` 합니다. 처리 하는 데 관심이 있는 이벤트에 대 한 구현을 제공 하기만 하면 됩니다.

`IDispEventSimpleImpl` 는 클래스의 이벤트 싱크 맵과 함께 작동 하 여 이벤트를 적절 한 처리기 함수로 라우팅합니다. 이 클래스를 사용 하려면 다음을 수행 합니다.

- 처리 하려는 각 개체의 각 이벤트에 대 한 이벤트 싱크 맵에 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) 매크로를 추가 합니다.

- [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) 구조체에 대 한 포인터를 각 항목에 대 한 매개 변수로 전달 하 여 각 이벤트에 대 한 형식 정보를 제공 합니다. X86 플랫폼에서 `_ATL_FUNC_INFO.cc` 값은 __stdcall의 콜백 함수를 호출 하 여 CC_CDECL 해야 합니다.

- [DispEventAdvise](#dispeventadvise) 를 호출 하 여 원본 개체와 기본 클래스 간의 연결을 설정 합니다.

- [DispEventUnadvise](#dispeventunadvise) 를 호출 하 여 연결을 중단 합니다.

`IDispEventSimpleImpl`이벤트를 처리 해야 하는 각 개체에 대해 ( *nID* 에 고유한 값을 사용 하 여)에서 파생 해야 합니다. 한 소스 개체에 대해 unadvising 하 여 기본 클래스를 다시 사용할 수 있습니다. 그런 다음 다른 소스 개체에 대해 알려 주지만 단일 개체에서 한 번에 처리할 수 있는 최대 소스 개체 수는 기본 클래스 수에 의해 제한 됩니다 `IDispEventSimpleImpl` .

`IDispEventSimplImpl` 는 형식 라이브러리에서 인터페이스에 대 한 형식 정보를 가져오지 않는다는 점만 제외 하 고 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)와 동일한 기능을 제공 합니다. 마법사는에만 기반 하 여 코드를 생성 `IDispEventImpl` 하지만 `IDispEventSimpleImpl` 코드를 직접 추가 하 여를 사용할 수 있습니다. `IDispEventSimpleImpl`이벤트 인터페이스를 설명 하는 형식 라이브러리가 없거나 형식 라이브러리를 사용 하 여와 관련 된 오버 헤드를 방지 하려는 경우에 사용 합니다.

> [!NOTE]
> `IDispEventImpl` 및는 `IDispEventSimpleImpl` `IUnknown::QueryInterface` `IDispEventImpl` `IDispEventSimpleImpl` 기본 com 개체의 클래스 멤버에 대 한 직접 액세스를 허용 하는 동시에 각 또는 기본 클래스가 별도의 COM id 역할을 할 수 있도록 하는 고유한 구현을 제공 합니다.

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

자세한 내용은 [IDispEventImpl 지원](../../atl/supporting-idispeventimpl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a> IDispEventSimpleImpl:: Advise

이 메서드를 호출 하 여 *pUnk* 으로 표시 되는 이벤트 소스와의 연결을 설정 합니다.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 이벤트 소스 개체의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

S_OK 또는 오류 HRESULT 값입니다.

### <a name="remarks"></a>설명

연결이 설정 되 면 *pUnk* 에서 발생 하는 이벤트는 이벤트 싱크 맵을 통해 클래스의 처리기로 라우팅됩니다.

> [!NOTE]
> 클래스가 여러 클래스에서 파생 되는 경우 `IDispEventSimpleImpl` 관심이 있는 특정 기본 클래스를 사용 하 여 호출 범위를 지정 하 여이 메서드에 대 한 호출을 명확 하 게 구분 해야 합니다.

`Advise` 기본 이벤트 원본에 대 한 연결을 설정 하 고 [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)에 의해 결정 된 대로 개체의 기본 이벤트 원본에 대 한 IID를 가져옵니다.

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a> IDispEventSimpleImpl::D ispEventAdvise

이 메서드를 호출 하 여 *pUnk* 으로 표시 되는 이벤트 소스와의 연결을 설정 합니다.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 이벤트 소스 개체의 인터페이스에 대 한 포인터입니다.

*piid*<br/>
이벤트 소스 개체의 IID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

S_OK 또는 오류 HRESULT 값입니다.

### <a name="remarks"></a>설명

이후에 *pUnk* 에서 발생 하는 이벤트는 이벤트 싱크 맵을 통해 클래스의 처리기로 라우팅됩니다.

> [!NOTE]
> 클래스가 여러 클래스에서 파생 되는 경우 `IDispEventSimpleImpl` 관심이 있는 특정 기본 클래스를 사용 하 여 호출 범위를 지정 하 여이 메서드에 대 한 호출을 명확 하 게 구분 해야 합니다.

`DispEventAdvise` 에 지정 된 이벤트 소스에 대 한 연결을 설정 `pdiid` 합니다.

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a> IDispEventSimpleImpl::D ispEventUnadvise

*PUnk* 로 표시 되는 이벤트 원본에 대 한 연결을 중단 합니다.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 이벤트 소스 개체의 인터페이스에 대 한 포인터입니다.

*piid*<br/>
이벤트 소스 개체의 IID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

S_OK 또는 오류 HRESULT 값입니다.

### <a name="remarks"></a>설명

연결이 끊어지면 이벤트는 더 이상 이벤트 싱크 맵에 나열 된 처리기 함수로 라우팅되지 않습니다.

> [!NOTE]
> 클래스가 여러 클래스에서 파생 되는 경우 `IDispEventSimpleImpl` 관심이 있는 특정 기본 클래스를 사용 하 여 호출 범위를 지정 하 여이 메서드에 대 한 호출을 명확 하 게 구분 해야 합니다.

`DispEventAdvise` 에 지정 된 이벤트 소스를 사용 하 여 설정 된 연결을 중단 `pdiid` 합니다.

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a> IDispEventSimpleImpl:: Idispatch.getidsofnames

이 구현에서는 `IDispatch::GetIDsOfNames` E_NOTIMPL을 반환 합니다.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 를 참조 하세요.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispEventSimpleImpl:: GetTypeInfo

이 구현에서는 `IDispatch::GetTypeInfo` E_NOTIMPL을 반환 합니다.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 를 참조 하세요.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispEventSimpleImpl:: GetTypeInfoCount

이 구현에서는 `IDispatch::GetTypeInfoCount` E_NOTIMPL을 반환 합니다.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 를 참조 하세요.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a> IDispEventSimpleImpl:: Invoke

이 구현은 `IDispatch::Invoke` 이벤트 싱크 맵에 나열 된 이벤트 처리기를 호출 합니다.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>설명

[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)를 참조 하세요.

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a> IDispEventSimpleImpl:: Unadvise

*PUnk* 로 표시 되는 이벤트 원본에 대 한 연결을 중단 합니다.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 이벤트 소스 개체의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

S_OK 또는 오류 HRESULT 값입니다.

### <a name="remarks"></a>설명

연결이 끊어지면 이벤트는 더 이상 이벤트 싱크 맵에 나열 된 처리기 함수로 라우팅되지 않습니다.

> [!NOTE]
> 클래스가 여러 클래스에서 파생 되는 경우 `IDispEventSimpleImpl` 관심이 있는 특정 기본 클래스를 사용 하 여 호출 범위를 지정 하 여이 메서드에 대 한 호출을 명확 하 게 구분 해야 합니다.

`Unadvise` 에 지정 된 기본 이벤트 소스를 사용 하 여 설정 된 연결을 중단 `pdiid` 합니다.

`Unavise` 기본 이벤트 원본에 대 한 연결을 중단 하 고 [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)에 의해 결정 된 대로 개체의 기본 이벤트 원본에 대 한 IID를 가져옵니다.

## <a name="see-also"></a>참고 항목

[_ATL_FUNC_INFO 구조체](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 클래스](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 클래스](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
