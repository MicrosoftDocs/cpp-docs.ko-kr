---
title: CComPolyObject 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3518fd5936c4871e99eaf597f12fb3ab7cc8aff6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="ccompolyobject-class"></a>CComPolyObject 클래스
이 클래스는 구현 **IUnknown** 집계 또는 집계 되지 않은 원시 개체에 대 한 합니다.  
  
## <a name="syntax"></a>구문  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>매개 변수  
 `contained`  
 파생 된 클래스에 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), 개체에서 지원할 하려는 다른 인터페이스와도 합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|생성자입니다.|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|소멸자입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|개체의 참조 횟수를 증가 시킵니다.|  
|[CComPolyObject::CreateInstance](#createinstance)|(정적) 새로 만들 수 있습니다. **CComPolyObject <** `contained`  **>**  개체는 오버 헤드 없이 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)합니다.|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|최종 초기화를 수행 `m_contained`합니다.|  
|[CComPolyObject::FinalRelease](#finalrelease)|최종 소멸 수행 `m_contained`합니다.|  
|[CComPolyObject::QueryInterface](#queryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|  
|[CComPolyObject::Release](#release)|개체의 참조 횟수를 감소 시킵니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|대리자 **IUnknown** 개체가 집계 되는 경우 또는를 알 수 없는 외부를 호출 하는 **IUnknown** 개체가 집계 되지 않은 경우 개체의 합니다.|  
  
## <a name="remarks"></a>설명  
 `CComPolyObject`구현 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 집계 또는 집계 되지 않은 원시 개체에 대 한 합니다.  
  
 인스턴스가 `CComPolyObject` 만들어지면 값 외부의 알 수 없음이 확인 됩니다. 이 경우 **NULL**, **IUnknown** 집계 되지 않은 원시 개체에 대 한 구현 됩니다. 알 수 없는 외부 없으면 **NULL**, **IUnknown** 집계 개체에 대 한 구현 됩니다.  
  
 사용 시의 이점은 `CComPolyObject` 두는 것을 방지 하는 [CComAggObject](../../atl/reference/ccomaggobject-class.md) 및 [CComObject](../../atl/reference/ccomobject-class.md) 모듈 집계 및 집계 되지 않은 원시 경우를 처리 합니다. 단일 `CComPolyObject` 두 경우 모두 처리 하는 개체입니다. 이 모듈에 존재 하 vtable의 복사본이 한 개만 및 함수 중 하나의 복사본을 의미 합니다. Vtable이 큰 경우 모듈 크기가 상당히 줄어들 수 있습니다이 있습니다. 그러나 vtable 작으면를 사용 하 여 `CComPolyObject` 조금 더 큰 모듈 크기는 집계 또는 집계 되지 않은 원시 개체에 대 한 최적화 되어 있지 않으므로 발생할 수 있습니다는 `CComAggObject` 및 `CComObject`합니다.  
  
 경우는 `DECLARE_POLY_AGGREGATABLE` 매크로 개체의 클래스 정의에 지정 된 `CComPolyObject` 개체를 만드는 사용할 수 있습니다. `DECLARE_POLY_AGGREGATABLE`자동으로 선언 됩니다 ATL 프로젝트 마법사를 사용 하 여 모든 권한 또는 Internet Explorer 컨트롤을 만드는 경우.  
  
 집계는 경우는 `CComPolyObject` 개체에는 자체 **IUnknown**외부 개체의와 별도로 **IUnknown**을 자체 참조 횟수를 유지 관리 합니다. `CComPolyObject`사용 하 여 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 알 수 없는 외부에 위임할 수 있습니다.  
  
 집계에 대 한 자세한 내용은 문서 참조 [ATL COM 개체 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcom.h  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 개체에서 참조 횟수를 증가 시킵니다.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>반환 값  
 진단에 대 한 유용한 또는 테스트 수 있는 값입니다.  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 생성자입니다.  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>매개 변수  
 `pv`  
 [in] 알 수 없는 외부 개체를 집계할 수 하는 경우에 대 한 포인터 또는 **NULL** 경우 개체는 개체가 집계 되지 않은 경우.  
  
### <a name="remarks"></a>설명  
 초기화는 `CComContainedObject` 데이터 멤버 [m_contained](#m_contained), 모듈 잠금 횟수를 증가 시킵니다.  
  
 모듈 잠금 횟수를 소멸자 줄입니다.  
  
##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 소멸자입니다.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>설명  
 호출 하는 할당 된 모든 리소스를 해제 [FinalRelease](#finalrelease), 및 모듈 잠금 횟수를 줄입니다.  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 새로 만들 수 있습니다. **CComPolyObject <** `contained`  **>**  개체는 오버 헤드 없이 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)합니다.  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>매개 변수  
 `pp`  
 [out] 에 대 한 포인터는 **CComPolyObject <** `contained`  **>**  포인터입니다. 경우 `CreateInstance` 실패 `pp` 로 설정 된 **NULL**합니다.  
  
### <a name="return-value"></a>반환 값  
 표준 `HRESULT` 값입니다.  
  
### <a name="remarks"></a>설명  
 반환 되는 개체에는 참조 횟수가 0, 없으므로 호출 `AddRef` 즉시을 사용 하 여 **릴리스** 를 마치면 개체 포인터에 대 한 참조를 해제 합니다.  
  
 개체에 대 한 액세스를 직접 필요 하지 않지만 여전히 오버 헤드 없이 새 개체를 만들려고 할 경우 `CoCreateInstance`를 사용 하 여 [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 대신 합니다.  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 개체 생성의 최종 단계 중 호출이 메서드는 최종 초기화에 대해 수행 된 [m_contained](#m_contained) 데이터 멤버입니다.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>반환 값  
 표준 `HRESULT` 값입니다.  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 이 메서드 해제 개체 소멸 하는 동안 호출 된 [m_contained](#m_contained) 데이터 멤버입니다.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 클래스에서 파생 된 개체입니다.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>매개 변수  
 `contained`  
 [in] 파생 된 클래스에 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), 개체에서 지원할 하려는 다른 인터페이스와도 합니다.  
  
### <a name="remarks"></a>설명  
 **IUnknown** 통해 호출 `m_contained` 개체가 집계 되는, 또는에 알 수 없는 외부에 위임 되며는 **IUnknown** 개체가 집계 되지 않은 경우이 개체의 합니다.  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 요청된 인터페이스에 대한 포인터를 검색합니다.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>매개 변수  
 `Q`  
 COM 인터페이스입니다.  
  
 `iid`  
 [in] 요청 된 인터페이스의 식별자입니다.  
  
 `ppvObject`  
 [out] 로 식별 되는 인터페이스 포인터에 대 한 포인터 `iid`합니다. 개체가이 인터페이스를 지원 하지 않는 경우 `ppvObject` 로 설정 된 **NULL**합니다.  
  
 `pp`  
 [out] 로 식별 된 인터페이스에 대 한 포인터 **__uuidof(Q)**합니다.  
  
### <a name="return-value"></a>반환 값  
 표준 `HRESULT` 값입니다.  
  
### <a name="remarks"></a>설명  
 요청한 인터페이스가 집계 개체에 대 한 **IUnknown**, `QueryInterface` 집계 된 개체의 자체에 대 한 포인터를 반환 **IUnknown** 참조 횟수를 증가 시킵니다. 그렇지 않으면이 메서드를 통해 인터페이스에 대 한 쿼리는 `CComContainedObject` 데이터 멤버 [m_contained](#m_contained)합니다.  
  
##  <a name="release"></a>CComPolyObject::Release  
 개체에 대 한 참조 횟수를 줄입니다.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>반환 값  
 디버그 빌드에서 **릴리스** 진단에 대 한 유용한 또는 테스트 수 있는 값을 반환 합니다. 비디버그 빌드에서 **릴리스** 항상 0을 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [클래스 개요](../../atl/atl-class-overview.md)
