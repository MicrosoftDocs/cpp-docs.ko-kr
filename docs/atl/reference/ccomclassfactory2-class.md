---
description: '자세히 알아보기: CComClassFactory2 클래스'
title: CComClassFactory2 클래스
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 7aebf09616c7fc4e85f6c44aee4db84886033f8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146889"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 클래스

이 클래스는 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 인터페이스를 구현 합니다.

## <a name="syntax"></a>구문

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>매개 변수

*사용권이*<br/>
다음 정적 함수를 구현 하는 클래스입니다.

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComClassFactory2:: CreateInstance](#createinstance)|지정 된 CLSID의 개체를 만듭니다.|
|[CComClassFactory2:: CreateInstanceLic](#createinstancelic)|라이선스 키가 지정 된 경우 지정 된 CLSID의 개체를 만듭니다.|
|[CComClassFactory2:: GetLicInfo](#getlicinfo)|클래스 팩터리의 라이선스 기능을 설명 하는 정보를 검색 합니다.|
|[CComClassFactory2:: LockServer](#lockserver)|메모리의 클래스 팩터리를 잠급니다.|
|[CComClassFactory2:: RequestLicKey](#requestlickey)|라이선스 키를 만들어 반환 합니다.|

## <a name="remarks"></a>설명

`CComClassFactory2`[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)의 확장인 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 인터페이스를 구현 합니다. `IClassFactory2` 라이선스를 통해 개체 생성을 제어 합니다. 사용이 허가 된 컴퓨터에서 실행 되는 클래스 팩터리는 런타임 라이선스 키를 제공할 수 있습니다. 이 라이선스 키를 사용 하면 전체 컴퓨터 라이선스가 없는 경우 응용 프로그램에서 개체를 인스턴스화할 수 있습니다.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 을 기본 클래스 팩터리로 선언 하는 매크로 [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)포함 되어 있습니다. 을 사용 하려면 `CComClassFactory2` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`의 템플릿 매개 변수는 `CComClassFactory2` 정적 함수, 및를 구현 해야 합니다 `VerifyLicenseKey` `GetLicenseKey` `IsLicenseValid` . 다음은 간단한 라이선스 클래스의 예제입니다.

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2``CComClassFactory2Base`및 *라이선스* 모두에서 파생 됩니다. `CComClassFactory2Base`그러면는 및에서 파생 `IClassFactory2` `CComObjectRootEx< CComGlobalsThreadModel >` 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a> CComClassFactory2:: CreateInstance

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

### <a name="remarks"></a>설명

컴퓨터를 완전히 사용 허가 해야 합니다. 전체 컴퓨터 라이선스가 없는 경우 [Createinstancelic](#createinstancelic)를 호출 합니다.

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a> CComClassFactory2:: CreateInstanceLic

[CreateInstance](#createinstance)와 유사 `CreateInstanceLic` 합니다. 단, 라이선스 키가 필요 합니다.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
진행 개체가 집계의 일부로 생성 되는 경우 *pUnkOuter* 은 알 수 없는 외부 여야 합니다. 그렇지 않으면 *pUnkOuter* 가 NULL 이어야 합니다.

*pUnkReserved*<br/>
진행 사용 되지 않습니다. Null이어야 합니다.

*riid*<br/>
진행 요청 된 인터페이스의 IID입니다. *PUnkOuter* 가 NULL이 아닌 경우 *riid* 는 여야 합니다 `IID_IUnknown` .

*bstrKey*<br/>
진행 이전에를 호출 하 여 가져온 런타임 라이선스 키 `RequestLicKey` 입니다. 개체를 만들려면이 키가 필요 합니다.

*ppvObject*<br/>
제한이 *Riid* 로 지정 된 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobject* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

[Requestlickey](#requestlickey)를 사용 하 여 라이선스 키를 가져올 수 있습니다. 허가 되지 않은 컴퓨터에서 개체를 만들려면를 호출 해야 `CreateInstanceLic` 합니다.

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a> CComClassFactory2:: GetLicInfo

클래스 팩터리의 라이선스 기능을 설명 하는 정보를 사용 하 여 [Licinfo](/windows/win32/api/ocidl/ns-ocidl-licinfo) 구조를 채웁니다.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>매개 변수

*pLicInfo*<br/>
제한이 구조체에 대 한 포인터 `LICINFO` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`fRuntimeKeyAvail`이 구조체의 멤버는 라이선스 키가 지정 된 경우 클래스 팩터리를 사용 하 여 허가 되지 않은 컴퓨터에서 개체를 만들 수 있는지 여부를 나타냅니다. *FLicVerified* 멤버는 전체 컴퓨터 라이선스가 있는지 여부를 나타냅니다.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a> CComClassFactory2:: LockServer

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

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a> CComClassFactory2:: RequestLicKey

`fRuntimeKeyAvail` [Licinfo](/windows/win32/api/ocidl/ns-ocidl-licinfo) 구조의 멤버가 TRUE 인 경우 라이선스 키를 만들고 반환 합니다.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>매개 변수

*dwReserved*<br/>
진행 사용 되지 않습니다. 0이어야 합니다.

*pbstrKey*<br/>
제한이 라이선스 키에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

[Createinstancelic](#createinstancelic) 를 호출 하 여 허가 되지 않은 컴퓨터에서 개체를 만들려면 라이선스 키가 필요 합니다. `fRuntimeKeyAvail`가 FALSE 이면 정식 라이선스 컴퓨터 에서만 개체를 만들 수 있습니다.

[Getlicinfo](#getlicinfo) 를 호출 하 여 값을 검색 `fRuntimeKeyAvail` 합니다.

## <a name="see-also"></a>참고 항목

[CComClassFactoryAutoThread 클래스](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton 클래스](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
