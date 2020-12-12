---
description: '자세히 알아보기: CComClassFactory 클래스'
title: CComClassFactory 클래스
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 36233abf13c6ff6963d02bc5431286ca6c783235
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152297"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory 클래스

이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 합니다.

## <a name="syntax"></a>구문

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|지정 된 CLSID의 개체를 만듭니다.|
|[CComClassFactory:: LockServer](#lockserver)|메모리의 클래스 팩터리를 잠급니다.|

## <a name="remarks"></a>설명

`CComClassFactory` 특정 CLSID의 개체를 만드는 메서드를 포함 하는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 하 고, 새 개체를 보다 신속 하 게 만들 수 있도록 메모리의 클래스 팩터리를 잠그는 방법을 포함 합니다. `IClassFactory` 는 시스템 레지스트리에 등록 하 고 CLSID를 할당 하는 모든 클래스에 대해 구현 되어야 합니다.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 `CComClassFactory`를 기본 클래스 팩터리로 선언하는 매크로 [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) 포함되어 있습니다. 이 기본값을 재정의 하려면 `DECLARE_CLASSFACTORY` 클래스 정의에서 *XXX* 매크로 중 하나를 지정 합니다. 예를 들어 [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) 매크로는 클래스 팩터리에 대해 지정 된 클래스를 사용 합니다.

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

위의 클래스 정의는 `CMyClassFactory` 가 개체의 기본 클래스 팩터리로 사용 되도록 지정 합니다. `CMyClassFactory` 에서 파생 되 `CComClassFactory` 고를 재정의 해야 합니다 `CreateInstance` .

ATL은 클래스 팩터리를 선언 하는 세 가지 다른 매크로를 제공 합니다.

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) 라이선스를 통해 생성을 제어 하는 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)을 사용 합니다.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 는 여러 아파트에서 개체를 만드는 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)를 사용 합니다.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) 단일 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 개체를 생성 하는 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)을 사용 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a> CComClassFactory:: CreateInstance

지정 된 CLSID의 개체를 만들고이 개체에 대 한 인터페이스 포인터를 검색 합니다.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
진행 개체가 집계의 일부로 생성 되는 경우 *pUnkOuter* 은 알 수 없는 외부 여야 합니다. 그렇지 않으면 *pUnkOuter* 가 NULL 이어야 합니다.

*riid*<br/>
진행 요청 된 인터페이스의 IID입니다. *PUnkOuter* 가 NULL이 아닌 경우 *riid* 는 여야 합니다 `IID_IUnknown` .

*ppvObj*<br/>
제한이 *Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobj* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a> CComClassFactory:: LockServer

`_Module::Lock`및를 각각 호출 하 여 모듈 잠금 수를 증가 및 감소 시킵니다 `_Module::Unlock` .

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>매개 변수

*fLock*<br/>
진행 TRUE 이면 잠금 수가 증가 합니다. 그렇지 않으면 잠금 수가 감소 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`_Module`[CComModule](../../atl/reference/ccommodule-class.md) 의 전역 인스턴스 또는 여기에서 파생 된 클래스를 참조 합니다.

를 호출 `LockServer` 하면 클라이언트가 클래스 팩터리를 포함 하 여 여러 개체를 신속 하 게 만들 수 있습니다.

## <a name="see-also"></a>참고 항목

[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
