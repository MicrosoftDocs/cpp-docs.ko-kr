---
title: "IConnectionPointImpl 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c49057153a23f0e17d09032df8781b64cef8677
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 클래스
이 클래스는 연결 지점을 구현합니다.  
  
## <a name="syntax"></a>구문  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 파생 된 클래스에 `IConnectionPointImpl`합니다.  
  
 `piid`  
 연결 지점 개체를 나타내는 인터페이스의 IID에 대 한 포인터입니다.  
  
 `CDV`  
 연결을 관리 하는 클래스입니다. 기본값은 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), 무제한 연결을 허용 하는 합니다. 사용할 수도 있습니다 [CComUnkArray](../../atl/reference/ccomunkarray-class.md), 고정된 된 수의 연결을 지정 하는 합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|연결 지점 및 싱크 간에 연결을 설정 합니다.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|연결 지점에 대 한 연결을 반복 하는 열거자를 만듭니다.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|연결 지점에서이 나타내는 인터페이스의 IID를 검색 합니다.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|연결 가능 개체에 대 한 인터페이스 포인터를 검색합니다.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|통해 이전에 설정 된 연결을 종료 `Advise`합니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|연결 지점에 대 한 연결을 관리합니다.|  
  
## <a name="remarks"></a>설명  
 `IConnectionPointImpl`연결 지점이 클라이언트에 송신 인터페이스를 노출 하는 개체 수 있도록 구현 합니다. 클라이언트는 싱크 라는 개체에이 인터페이스를 구현 합니다.  
  
 ATL 사용 하 여 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 연결 가능 개체를 구현 하려면. 연결 가능 개체 내에서 각 연결 지점으로 식별 하는 송신 인터페이스를 나타내는 `piid`합니다. 클래스 *CDV* 연결 지점 및 싱크 간의 연결을 관리 합니다. 각 연결 고유 하 게 식별 하 여 "쿠키"입니다.  
  
 Atl에서 연결 지점을 사용 하는 방법에 대 한 자세한 내용은 문서 참조 [연결점](../../atl/atl-connection-points.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcom.h  
  
##  <a name="advise"></a>IConnectionPointImpl::Advise  
 연결 지점 및 싱크 간에 연결을 설정 합니다.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>설명  
 사용 하 여 [Unadvise](#unadvise) 연결 호출을 종료 합니다.  
  
 참조 [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) in the Windows SDK입니다.  
  
##  <a name="enumconnections"></a>IConnectionPointImpl::EnumConnections  
 연결 지점에 대 한 연결을 반복 하는 열거자를 만듭니다.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>설명  
 참조 [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) in the Windows SDK입니다.  
  
##  <a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface  
 연결 지점에서이 나타내는 인터페이스의 IID를 검색 합니다.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>설명  
 참조 [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) in the Windows SDK입니다.  
  
##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer  
 연결 가능 개체에 대 한 인터페이스 포인터를 검색합니다.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>설명  
 참조 [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) in the Windows SDK입니다.  
  
##  <a name="m_vec"></a>IConnectionPointImpl::m_vec  
 연결 지점 개체와 싱크 간의 연결을 관리 합니다.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>설명  
 기본적으로 `m_vec` 유형의 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)합니다.  
  
##  <a name="unadvise"></a>IConnectionPointImpl::Unadvise  
 통해 이전에 설정 된 연결을 종료 [Advise](#advise)합니다.  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>설명  
 참조 [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) in the Windows SDK입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [클래스 개요](../../atl/atl-class-overview.md)
