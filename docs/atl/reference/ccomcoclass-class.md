---
description: '자세히 알아보기: CComCoClass 클래스'
title: CComCoClass 클래스
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 31895afa9100159e8ac1a9ef370f6548e2b2e3f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152258"
---
# <a name="ccomcoclass-class"></a>CComCoClass 클래스

이 클래스는 클래스의 인스턴스를 만들고 해당 속성을 가져오는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CComCoClass` 입니다.

*pclsid*<br/>
개체의 CLSID에 대 한 포인터입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComCoClass:: CreateInstance](#createinstance)|정적인 클래스의 인스턴스를 만들고 인터페이스를 쿼리 합니다.|
|[CComCoClass:: Error](#error)|정적인 클라이언트에 다양 한 오류 정보를 반환 합니다.|
|[CComCoClass:: GetObjectCLSID](#getobjectclsid)|정적인 개체의 클래스 식별자를 반환 합니다.|
|[CComCoClass:: GetObjectDescription](#getobjectdescription)|정적인 개체의 설명을 반환 하려면를 재정의 합니다.|

## <a name="remarks"></a>설명

`CComCoClass` 개체의 CLSID를 검색 하 고, 오류 정보를 설정 하 고, 클래스의 인스턴스를 만드는 메서드를 제공 합니다. 개체 맵에 등록 된 모든 클래스는에서 파생 되어야 합니다 `CComCoClass` .

`CComCoClass` 또한 개체에 대 한 기본 클래스 팩터리 및 집계 모델을 정의 합니다. `CComCoClass` 에서는 다음 두 매크로를 사용 합니다.

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) 클래스 팩터리를 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)로 선언 합니다.

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) 개체를 집계할 수 있음을 선언 합니다.

클래스 정의에서 다른 매크로를 지정 하 여 이러한 기본값 중 하나를 재정의할 수 있습니다. 예를 들어 대신 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 를 사용 하려면 `CComClassFactory` [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) 매크로를 지정 합니다.

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a> CComCoClass:: CreateInstance

이러한 함수를 사용 하 여 com `CreateInstance` API를 사용 하지 않고 com 개체의 인스턴스를 만들고 인터페이스 포인터를 검색 합니다.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>매개 변수

*Q*<br/>
*Pp* 를 통해 반환 되어야 하는 COM 인터페이스입니다.

*punkOuter*<br/>
진행 집계를 알 수 없는 외부 또는 제어 하는 외부입니다.

*페이지*<br/>
제한이 생성이 성공 하면 요청 된 인터페이스 포인터를 받는 포인터 변수의 주소입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다. 가능한 반환 값에 대 한 설명은 Windows SDK의 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 를 참조 하세요.

### <a name="remarks"></a>설명

일반적인 개체 생성을 위해이 함수의 첫 번째 오버 로드를 사용 합니다. 생성 되는 개체를 집계 해야 하는 경우 두 번째 오버 로드를 사용 합니다.

필요한 COM 개체를 구현 하는 ATL 클래스 (즉, [CComCoClass](../../atl/reference/ccomcoclass-class.md)의 첫 번째 템플릿 매개 변수로 사용 되는 클래스)는 호출 코드와 동일한 프로젝트에 있어야 합니다. COM 개체의 생성은이 ATL 클래스에 대해 등록 된 클래스 팩터리에 의해 수행 됩니다.

이러한 함수는 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) 매크로를 사용 하 여 외부에서 만들 수 없는 개체를 만드는 데 유용 합니다. 효율성의 이유로 COM API를 사용 하지 않으려는 경우에도 유용 합니다.

인터페이스 *Q* 에는 [__uuidof](../../cpp/uuidof-operator.md) 연산자를 사용 하 여 검색할 수 있는 IID와 연결 된 IID가 있어야 합니다.

### <a name="example"></a>예제

다음 예제에서 `CDocument` 는 `CComCoClass` 인터페이스를 구현 하는에서 파생 된 마법사 생성 ATL 클래스입니다 `IDocument` . 클래스가 OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 매크로를 사용 하 여 개체 맵에 등록 되므로 클라이언트는 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)를 사용 하 여 문서 인스턴스를 만들 수 없습니다. `CApplication` 는 자체 COM 인터페이스 중 하나에 메서드를 제공 하 여 문서 클래스의 인스턴스를 만드는 CoClass입니다. 아래 코드에서는 `CreateInstance` 기본 클래스에서 상속 된 멤버를 사용 하 여 문서 클래스의 인스턴스를 얼마나 쉽게 만들 수 있는 방법을 보여 줍니다 `CComCoClass` .

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a> CComCoClass:: Error

이 정적 함수는 인터페이스를 설정 `IErrorInfo` 하 여 클라이언트에 오류 정보를 제공 합니다.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>매개 변수

*lpszDesc*<br/>
진행 오류를 설명 하는 문자열입니다. 의 유니코드 버전은 `Error` *lpszDesc* 이 LPCOLESTR 형식이 되도록 지정 합니다. ANSI 버전은 lpcstr의 유형을 지정 합니다.

*iid*<br/>
진행 오류가 운영 체제에서 정의 되는 경우 오류 또는 GUID_NULL (기본값)를 정의 하는 인터페이스의 IID입니다.

*hRes*<br/>
진행 호출자에 게 반환할 HRESULT입니다. 기본값은 0입니다. *Hres* 에 대 한 자세한 내용은 설명을 참조 하세요.

*nID*<br/>
진행 오류 설명 문자열이 저장 되는 리소스 식별자입니다. 이 값은 0x0200과 0xFFFF 사이에 있어야 합니다. 디버그 빌드에서 *nID* 가 유효한 문자열을 인덱싱하지 않으면 **어설션이** 발생 합니다. 릴리스 빌드에서 오류 설명 문자열은 "알 수 없는 오류"로 설정 됩니다.

*dwHelpID*<br/>
진행 오류에 대 한 도움말 컨텍스트 식별자입니다.

*lpszHelpFile*<br/>
진행 오류를 설명 하는 도움말 파일의 경로 및 이름입니다.

*hInst*<br/>
진행 리소스에 대 한 핸들입니다. 기본적으로이 매개 변수는입니다 `_AtlModule::GetResourceInstance` `_AtlModule` . 여기서는 [catlmodule](../../atl/reference/catlmodule-class.md)의 전역 인스턴스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다. 자세한 내용은 설명을 참조하세요.

### <a name="remarks"></a>설명

를 호출 하려면 `Error` 개체가 인터페이스를 구현 해야 합니다 `ISupportErrorInfo Interface` .

*Hres* 매개 변수가 0이 아닌 경우는 `Error` *hres* 의 값을 반환 합니다. *Hres* 가 0 이면 처음 4 개 버전의가 `Error` DISP_E_EXCEPTION 반환 됩니다. 마지막 두 버전은 매크로 **MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)** 결과를 반환 합니다.

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a> CComCoClass:: GetObjectCLSID

개체의 CLSID를 검색 하는 일관 된 방법을 제공 합니다.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>반환 값

개체의 클래스 식별자입니다.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a> CComCoClass:: GetObjectDescription

이 정적 함수는 클래스 개체에 대 한 텍스트 설명을 검색 합니다.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>반환 값

클래스 개체의 설명입니다.

### <a name="remarks"></a>설명

기본 구현에서는 NULL을 반환 합니다. [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) 매크로를 사용 하 여이 메서드를 재정의할 수 있습니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription` 는에 의해 호출 됩니다 `IComponentRegistrar::GetComponents` . `IComponentRegistrar` 는 DLL에서 개별 구성 요소를 등록 및 등록 취소할 수 있도록 하는 자동화 인터페이스입니다. ATL 프로젝트 마법사를 사용 하 여 구성 요소 등록자 개체를 만들면 마법사가 자동으로 인터페이스를 구현 합니다 `IComponentRegistrar` . `IComponentRegistrar` 는 일반적으로 Microsoft 트랜잭션 서버에서 사용 됩니다.

ATL 프로젝트 마법사에 대 한 자세한 내용은 [Atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
