---
description: '자세히 알아보기: CComClassFactorySingleton 클래스'
title: CComClassFactorySingleton 클래스
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: eaf09f823a6d8d62f102e6e36116b56270248f9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146863"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 클래스

이 클래스는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되며 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 를 사용 하 여 단일 개체를 생성 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
클래스입니다.

`CComClassFactorySingleton`[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되 고 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 를 사용 하 여 단일 개체를 생성 합니다. 메서드를 호출할 때마다 `CreateInstance` 인터페이스 포인터에 대해이 개체를 쿼리 하기만 합니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|`m_spObj`인터페이스 포인터에 대 한 쿼리입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|`CComClassFactorySingleton`에 의해 생성된 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 개체입니다.|

## <a name="remarks"></a>설명

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 `CComClassFactory`를 기본 클래스 팩터리로 선언하는 매크로 [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) 포함되어 있습니다. 을 사용 하려면 `CComClassFactorySingleton` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a> CComClassFactorySingleton:: CreateInstance

[M_spObj](#m_spobj)를 통해 `QueryInterface`를 호출하여 인터페이스 포인터를 검색합니다.

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

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a> CComClassFactorySingleton:: m_spObj

`CComClassFactorySingleton`에 의해 생성된 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 개체입니다.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>설명

[CreateInstance](#createinstance) 메서드를 호출할 때마다 인터페이스 포인터에 대해이 개체를 쿼리 합니다.

의 현재 형태는 `m_spObj` `CComClassFactorySingleton` 이전 버전의 ATL에서 작동 하 던 것과 같은 주요 변경 내용을 제공 합니다. 이전 버전에서는 `CComClassFactorySingleton` 서버를 초기화 하는 동안 개체를 클래스 팩터리와 동시에 만들었습니다. Visual C++ .NET 2003 이상에서 개체는 첫 번째 요청에서 지연 되어 생성 됩니다. 이러한 변경으로 인해 초기 초기화를 사용 하는 프로그램에서 오류가 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 클래스](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread 클래스](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
