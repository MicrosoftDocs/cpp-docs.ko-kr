---
description: '자세히 알아보기: CComClassFactoryAutoThread 클래스'
title: CComClassFactoryAutoThread 클래스
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 9d25303d4d40f695c68fdf09aae7d56e6f1e5fb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152284"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 클래스

이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 하 고 여러 아파트에서 개체를 만들 수 있도록 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComClassFactoryAutoThread:: CreateInstance](#createinstance)|지정 된 CLSID의 개체를 만듭니다.|
|[CComClassFactoryAutoThread:: LockServer](#lockserver)|메모리의 클래스 팩터리를 잠급니다.|

## <a name="remarks"></a>설명

`CComClassFactoryAutoThread` 는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)와 유사 하지만 여러 아파트에서 개체를 만들 수 있습니다. 이 지원을 활용 하려면 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)에서 EXE 모듈을 파생 시키십시오.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 을 기본 클래스 팩터리로 선언 하는 매크로 [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)포함 되어 있습니다. 을 사용 하려면 `CComClassFactoryAutoThread` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a> CComClassFactoryAutoThread:: CreateInstance

지정 된 CLSID의 개체를 만들고이 개체에 대 한 인터페이스 포인터를 검색 합니다.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>설명

모듈이 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)에서 파생 되는 경우는 `CreateInstance` 먼저 스레드를 선택 하 여 연결 된 아파트에서 개체를 만듭니다.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a> CComClassFactoryAutoThread:: LockServer

`_Module::Lock`및를 각각 호출 하 여 모듈 잠금 수를 증가 및 감소 시킵니다 `_Module::Unlock` .

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>매개 변수

*fLock*<br/>
진행 TRUE 이면 잠금 수가 증가 합니다. 그렇지 않으면 잠금 수가 감소 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

를 사용 하는 경우는 `CComClassFactoryAutoThread` `_Module` 일반적으로 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)의 전역 인스턴스를 참조 합니다.

를 호출 `LockServer` 하면 클라이언트가 클래스 팩터리를 포함 하 여 여러 개체를 신속 하 게 만들 수 있습니다.

## <a name="see-also"></a>참고 항목

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 클래스](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton 클래스](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
