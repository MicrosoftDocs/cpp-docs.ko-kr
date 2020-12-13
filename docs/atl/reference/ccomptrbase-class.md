---
description: '자세히 알아보기: CComPtrBase 클래스'
title: CComPtrBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 34f197904775bc15366f412e629ef81b26dde74e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142391"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 클래스

이 클래스는 COM 기반 메모리 루틴을 사용 하는 스마트 포인터 클래스의 기반을 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
스마트 포인터에서 참조할 개체 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComPtrBase:: Advise](#advise)|이 메서드를 호출 하 여 `CComPtrBase` 의 연결 지점과 클라이언트의 싱크 간에 연결을 만듭니다.|
|[CComPtrBase:: Attach](#attach)|기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.|
|[CComPtrBase:: CoCreateInstance](#cocreateinstance)|지정 된 클래스 ID 또는 프로그램 ID와 연결 된 클래스의 개체를 만들려면이 메서드를 호출 합니다.|
|[CComPtrBase:: CopyTo](#copyto)|포인터를 다른 포인터 변수에 복사 하려면이 메서드를 호출 `CComPtrBase` 합니다.|
|[CComPtrBase::D etach](#detach)|포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.|
|[CComPtrBase:: IsEqualObject](#isequalobject)|지정 된이 `IUnknown` 개체와 연결 된 동일한 개체를 가리키는지 확인 하려면이 메서드를 호출 합니다 `CComPtrBase` .|
|[CComPtrBase:: QueryInterface](#queryinterface)|지정 된 인터페이스에 대 한 포인터를 반환 하려면이 메서드를 호출 합니다.|
|[CComPtrBase:: Release](#release)|인터페이스를 해제 하려면이 메서드를 호출 합니다.|
|[CComPtrBase:: SetSite](#setsite)|개체의 사이트를 `CComPtrBase` 부모 개체의로 설정 하려면이 메서드를 호출 `IUnknown` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CComPtrBase:: operator T *](#operator_t_star)|캐스트 연산자입니다.|
|[CComPtrBase:: operator!](#operator_not)|NOT 연산자입니다.|
|[CComPtrBase:: operator &](#operator_amp)|& 연산자|
|[CComPtrBase:: operator *](#operator_star)|\* 연산자|
|[CComPtrBase:: operator <](#ccomptrbase__operator lt)|보다 작음 연산자입니다.|
|[CComPtrBase:: operator = =](#operator_eq_eq)|같음 연산자입니다.|
|[CComPtrBase:: operator->](#operator_ptr)|멤버 포인터 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComPtrBase::p](#p)|포인터 데이터 멤버 변수입니다.|

## <a name="remarks"></a>설명

이 클래스는 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 및 [CCOMPTR](../../atl/reference/ccomptr-class.md)와 같은 COM 메모리 관리 루틴을 사용 하는 다른 스마트 포인터의 기반을 제공 합니다. 파생 클래스는 자체 생성자와 연산자를 추가 하지만에서 제공 하는 메서드를 사용 합니다 `CComPtrBase` .

## <a name="requirements"></a>요구 사항

**헤더:** comcli .h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a> CComPtrBase:: Advise

이 메서드를 호출 하 여 `CComPtrBase` 의 연결 지점과 클라이언트의 싱크 간에 연결을 만듭니다.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
클라이언트의에 대 한 포인터 `IUnknown` 입니다.

*iid*<br/>
연결 지점의 GUID입니다. 일반적으로이는 연결 지점에서 관리 하는 송신 인터페이스와 동일 합니다.

*pdw*<br/>
연결을 고유 하 게 식별 하는 쿠키에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

자세한 [내용은이 항목을](connection-point-global-functions.md#atladvise) 참조 하십시오.

## <a name="ccomptrbaseattach"></a><a name="attach"></a> CComPtrBase:: Attach

기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>매개 변수

*즉*<br/>
`CComPtrBase`개체는이 포인터의 소유권을 갖습니다.

### <a name="remarks"></a>설명

`Attach`기존 [Ccomptrbase::p](#p) 멤버 변수에서 [Ccomptrbase:: Release](#release) 를 호출 하 고, *p2* 를에 할당 `CComPtrBase::p` 합니다. 개체는 포인터에 대 한 `CComPtrBase` 소유권을 가질 때 포인터에 대해 자동으로를 호출 하 여 `Release` 개체의 참조 횟수가 0이 되 면 포인터와 할당 된 모든 데이터를 삭제 합니다.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a> CComPtrBase:: ~ CComPtrBase

소멸자입니다.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>설명

가 가리키는 인터페이스를 해제 `CComPtrBase` 합니다.

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a> CComPtrBase:: CoCreateInstance

지정 된 클래스 ID 또는 프로그램 ID와 연결 된 클래스의 개체를 만들려면이 메서드를 호출 합니다.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>매개 변수

*szProgID*<br/>
CLSID를 복구 하는 데 사용 되는 ProgID에 대 한 포인터입니다.

*pUnkOuter*<br/>
NULL 인 경우 개체가 집계의 일부로 생성 되지 않음을 나타냅니다. NULL이 아닌 경우는 집계 개체의 `IUnknown` 인터페이스 (제어)에 대 한 포인터입니다 `IUnknown` .

*dwClsContext*<br/>
새로 만든 개체를 관리 하는 코드가 실행 되는 컨텍스트입니다.

*rclsid*<br/>
개체를 만드는 데 사용 되는 데이터 및 코드와 연결 된 CLSID입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK를 반환 하거나, 오류 발생 시 REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING 또는 E_NOINTERFACE를 반환 합니다. 이러한 오류에 대 한 설명은 [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 및 [Clsidfromprogid](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) 를 참조 하세요.

### <a name="remarks"></a>설명

메서드의 첫 번째 폼이 호출 되 면 [Clsidfromprogid](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) 가 CLSID를 복구 하는 데 사용 됩니다. 그러면 두 폼이 모두 [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)를 호출 합니다.

디버그 빌드에서는 [Ccomptrbase::p](#p) 가 NULL이 아닌 경우 어설션 오류가 발생 합니다.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a> CComPtrBase:: CopyTo

포인터를 다른 포인터 변수에 복사 하려면이 메서드를 호출 `CComPtrBase` 합니다.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>매개 변수

*.Ppt*<br/>
포인터를 수신 하는 변수의 주소입니다 `CComPtrBase` .

### <a name="return-value"></a>반환 값

성공 시 S_OK을 반환 하 고 실패 시 E_POINTER 반환 합니다.

### <a name="remarks"></a>설명

`CComPtrBase` *PpT* 에 포인터를 복사 합니다. [Ccomptrbase::p](#p) 멤버 변수의 참조 횟수가 증가 합니다.

*PpT* 가 NULL 인 경우 오류 HRESULT가 반환 됩니다. 디버그 빌드에서는 *ppT* 가 NULL과 같은 경우 어설션 오류가 발생 합니다.

## <a name="ccomptrbasedetach"></a><a name="detach"></a> CComPtrBase::D etach

포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.

```
T* Detach() throw();
```

### <a name="return-value"></a>반환 값

포인터의 복사본을 반환 합니다.

### <a name="remarks"></a>설명

포인터의 소유권을 해제 하 고 [Ccomptrbase::p](#p) 데이터 멤버 변수를 NULL로 설정 하 고 포인터의 복사본을 반환 합니다.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a> CComPtrBase:: IsEqualObject

지정 된이 `IUnknown` 개체와 연결 된 동일한 개체를 가리키는지 확인 하려면이 메서드를 호출 합니다 `CComPtrBase` .

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>매개 변수

*pOther*<br/>
비교할 `IUnknown *`입니다.

### <a name="return-value"></a>반환 값

개체가 같으면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a> CComPtrBase:: operator!

NOT 연산자입니다.

```
bool operator!() const throw();
```

### <a name="return-value"></a>반환 값

`CComHeapPtr`포인터가 NULL과 같으면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a> CComPtrBase:: operator &amp;

& 연산자

```
T** operator&() throw();
```

### <a name="return-value"></a>반환 값

개체가 가리키는 개체의 주소를 반환 `CComPtrBase` 합니다.

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a> CComPtrBase:: operator \*

\* 연산자

```
T& operator*() const throw();
```

### <a name="return-value"></a>반환 값

[Ccomptrbase::p](#p);의 값을 반환 합니다. 즉, 개체에서 참조 하는 개체에 대 한 포인터입니다 `CComPtrBase` .

디버그 빌드에서는 [Ccomptrbase::p](#p) 가 NULL이 아닌 경우 어설션 오류가 발생 합니다.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a> CComPtrBase:: operator = =

같음 연산자입니다.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`CComPtrBase`와 *pT* 가 같은 개체를 가리키면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a> CComPtrBase:: operator-&gt;

멤버 포인터 연산자입니다.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>반환 값

[Ccomptrbase::p](#p) 데이터 멤버 변수의 값을 반환 합니다.

### <a name="remarks"></a>설명

이 연산자를 사용 하 여 개체가 가리키는 클래스에서 메서드를 호출 `CComPtrBase` 합니다. 디버그 빌드에서는 `CComPtrBase` 데이터 멤버가 NULL을 가리키는 경우 어설션 오류가 발생 합니다.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a> CComPtrBase:: operator &lt;

보다 작음 연산자입니다.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

현재 개체에서 관리 하는 포인터가 비교할 포인터 보다 작은 경우 true를 반환 합니다.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a> CComPtrBase:: operator T\*

캐스트 연산자입니다.

```
operator T*() const throw();
```

### <a name="remarks"></a>설명

클래스 템플릿에 정의 된 개체 데이터 형식에 대 한 포인터를 반환 합니다.

## <a name="ccomptrbasep"></a><a name="p"></a> CComPtrBase::p

포인터 데이터 멤버 변수입니다.

```
T* p;
```

### <a name="remarks"></a>설명

이 멤버 변수는 포인터 정보를 포함 합니다.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a> CComPtrBase:: QueryInterface

지정 된 인터페이스에 대 한 포인터를 반환 하려면이 메서드를 호출 합니다.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>매개 변수

*Q*<br/>
인터페이스 포인터가 필요한 개체 유형입니다.

*페이지*<br/>
요청 된 인터페이스 포인터를 받는 출력 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 E_NOINTERFACE을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))를 호출 합니다.

디버그 빌드에서는 *pp* 가 NULL과 같지 않을 경우 어설션 오류가 발생 합니다.

## <a name="ccomptrbaserelease"></a><a name="release"></a> CComPtrBase:: Release

인터페이스를 해제 하려면이 메서드를 호출 합니다.

```cpp
void Release() throw();
```

### <a name="remarks"></a>설명

인터페이스가 해제 되 고 [Ccomptrbase::p](#p) 가 NULL로 설정 됩니다.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a> CComPtrBase:: SetSite

개체의 사이트를 `CComPtrBase` 부모 개체의로 설정 하려면이 메서드를 호출 `IUnknown` 합니다.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>매개 변수

*punkParent*<br/>
부모의 인터페이스에 대 한 포인터입니다 `IUnknown` .

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [Atlsetchildsite](composite-control-global-functions.md#atlsetchildsite)를 호출 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
