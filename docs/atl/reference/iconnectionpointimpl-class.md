---
description: '자세히 알아보기: IConnectionPointImpl 클래스'
title: IConnectionPointImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: d87eb0821a3a48d171c196c891b5f5c7aacb9cdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139583"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 클래스

이 클래스는 연결 지점을 구현 합니다.

## <a name="syntax"></a>구문

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IConnectionPointImpl` 입니다.

*piid*<br/>
연결 지점 개체가 나타내는 인터페이스의 IID에 대 한 포인터입니다.

*CDV*<br/>
연결을 관리 하는 클래스입니다. 기본값은 무제한 연결을 허용 하는 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)입니다. 고정 된 수의 연결을 지정 하는 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)를 사용할 수도 있습니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IConnectionPointImpl:: Advise](#advise)|연결 지점과 싱크 간에 연결을 설정 합니다.|
|[IConnectionPointImpl:: EnumConnections](#enumconnections)|연결 지점에 대 한 연결을 반복 하는 열거자를 만듭니다.|
|[IConnectionPointImpl:: GetConnectionInterface](#getconnectioninterface)|연결 지점에서 나타내는 인터페이스의 IID를 검색 합니다.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|연결할 수 있는 개체에 대 한 인터페이스 포인터를 검색 합니다.|
|[IConnectionPointImpl:: Unadvise](#unadvise)|이전에를 통해 설정 된 연결을 종료 `Advise` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[IConnectionPointImpl:: m_vec](#m_vec)|연결 지점에 대 한 연결을 관리 합니다.|

## <a name="remarks"></a>설명

`IConnectionPointImpl` 개체에서 나가는 인터페이스를 클라이언트에 노출할 수 있도록 하는 연결 지점을 구현 합니다. 클라이언트는 싱크 라는 개체에서이 인터페이스를 구현 합니다.

ATL은 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 를 사용 하 여 연결 가능 개체를 구현 합니다. 연결 가능 개체 내의 각 연결 지점은 *piid* 로 식별 되는 송신 인터페이스를 나타냅니다. *Cdv* 클래스는 연결 지점과 싱크 간의 연결을 관리 합니다. 각 연결은 "쿠키"로 고유 하 게 식별 됩니다.

ATL에서 연결 지점의 사용에 대 한 자세한 내용은 [연결 요소](../../atl/atl-connection-points.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a> IConnectionPointImpl:: Advise

연결 지점과 싱크 간에 연결을 설정 합니다.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>설명

[Unadvise](#unadvise) 를 사용 하 여 연결 호출을 종료 합니다.

Windows SDK [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) 를 참조 하세요.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a> IConnectionPointImpl:: EnumConnections

연결 지점에 대 한 연결을 반복 하는 열거자를 만듭니다.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>설명

Windows SDK [IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) 를 참조 하세요.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a> IConnectionPointImpl:: GetConnectionInterface

연결 지점에서 나타내는 인터페이스의 IID를 검색 합니다.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>설명

Windows SDK [IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) 를 참조 하세요.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a> IConnectionPointImpl::GetConnectionPointContainer

연결할 수 있는 개체에 대 한 인터페이스 포인터를 검색 합니다.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) 를 참조 하세요.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a> IConnectionPointImpl:: m_vec

연결 지점 개체와 싱크 간의 연결을 관리 합니다.

```
CDV m_vec;
```

### <a name="remarks"></a>설명

기본적으로 `m_vec` 는 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)형식입니다.

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a> IConnectionPointImpl:: Unadvise

[Advise](#advise)를 통해 이전에 설정 된 연결을 종료 합니다.

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
