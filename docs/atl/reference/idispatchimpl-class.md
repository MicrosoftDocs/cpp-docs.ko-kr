---
description: '자세히 알아보기: IDispatchImpl 클래스'
title: IDispatchImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 709b703bf610776191b2587d11a0c5be651c4938
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139557"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 클래스

이중 인터페이스 파트에 대 한 기본 구현을 제공 합니다 `IDispatch` .

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
진행 이중 인터페이스입니다.

*piid*<br/>
진행 *T* 의 IID에 대 한 포인터입니다.

*plibid*<br/>
진행 인터페이스에 대 한 정보를 포함 하는 형식 라이브러리의 LIBID에 대 한 포인터입니다. 기본적으로 서버 수준 형식 라이브러리가 전달 됩니다.

*wMajor*<br/>
진행 형식 라이브러리의 주 버전입니다. 기본적으로이 값은 1입니다.

*wMinor*<br/>
진행 형식 라이브러리의 부 버전입니다. 기본적으로이 값은 0입니다.

*tihclass*<br/>
진행 *T* 의 형식 정보를 관리 하는 데 사용 되는 클래스입니다. 기본적으로이 값은 `CComTypeInfoHolder` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|생성자입니다. `AddRef`이중 인터페이스에 대 한 형식 정보를 관리 하는 보호 된 멤버 변수를 호출 합니다. 이 소멸자는 `Release`을 호출합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IDispatchImpl:: Idispatch.getidsofnames](#getidsofnames)|이름 집합을 해당하는 디스패치 식별자 집합에 매핑합니다.|
|[IDispatchImpl:: GetTypeInfo](#gettypeinfo)|이중 인터페이스에 대 한 형식 정보를 검색 합니다.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|이중 인터페이스에 사용할 수 있는 형식 정보가 있는지 여부를 확인 합니다.|
|[IDispatchImpl:: Invoke](#invoke)|이중 인터페이스에 의해 노출 되는 메서드 및 속성에 대 한 액세스를 제공 합니다.|

## <a name="remarks"></a>설명

`IDispatchImpl` 개체의 이중 인터페이스 부분에 대 한 기본 구현을 제공 `IDispatch` 합니다. 이중 인터페이스는에서 파생 `IDispatch` 되 고 자동화 호환 형식만 사용 합니다. 인터페이스와 마찬가지로 이중 인터페이스는 초기 바인딩과 런타임에 바인딩을 지원 합니다. 그러나 이중 인터페이스는 vtable 바인딩도 지원 합니다.

다음 예제에서는 일반적인 구현은 `IDispatchImpl`합니다.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

기본적으로 클래스는 `IDispatchImpl` 레지스트리의 *T* 에 대 한 형식 정보를 조회 합니다. 등록 되지 않은 인터페이스를 구현 하려면 `IDispatchImpl` 미리 정의 된 버전 번호를 사용 하 여 레지스트리에 액세스 하지 않고도 클래스를 사용할 수 있습니다. `IDispatchImpl`0xffff가 *wmajor* 및 0xffff 값으로 *wmajor* 의 값으로 포함 된 개체를 만드는 경우 `IDispatchImpl` 클래스는 레지스트리 대신 .dll 파일에서 형식 라이브러리를 검색 합니다.

`IDispatchImpl``CComTypeInfoHolder`이중 인터페이스에 대 한 형식 정보를 관리 하는 형식의 정적 멤버를 포함 합니다. 동일한 이중 인터페이스를 구현 하는 개체가 여러 개 있는 경우 하나의 인스턴스만 `CComTypeInfoHolder` 사용 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`T`

`IDispatchImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a> IDispatchImpl:: Idispatch.getidsofnames

이름 집합을 해당하는 디스패치 식별자 집합에 매핑합니다.

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

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispatchImpl:: GetTypeInfo

이중 인터페이스에 대 한 형식 정보를 검색 합니다.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 를 참조 하세요.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispatchImpl::GetTypeInfoCount

이중 인터페이스에 사용할 수 있는 형식 정보가 있는지 여부를 확인 합니다.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>설명

`IDispatch::GetTypeInfoCount`Windows SDK에서을 참조 하세요.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a> IDispatchImpl::IDispatchImpl

생성자입니다. `AddRef`이중 인터페이스에 대 한 형식 정보를 관리 하는 보호 된 멤버 변수를 호출 합니다. 이 소멸자는 `Release`을 호출합니다.

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a> IDispatchImpl:: Invoke

이중 인터페이스에 의해 노출 되는 메서드 및 속성에 대 한 액세스를 제공 합니다.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
