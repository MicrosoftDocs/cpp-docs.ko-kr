---
description: '자세히 알아보기: IPerPropertyBrowsingImpl 클래스'
title: IPerPropertyBrowsingImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: eba17c0011343f50f586b13086dc76229f08ba3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139349"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 클래스

이 클래스는를 구현 `IUnknown` 하 고 클라이언트가 개체의 속성 페이지에 있는 정보에 액세스할 수 있도록 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPerPropertyBrowsingImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IPerPropertyBrowsingImpl:: GetDisplayString](#getdisplaystring)|지정 된 속성을 설명 하는 문자열을 검색 합니다.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|지정 된 속성에 사용할 수 있는 값에 해당 하는 문자열의 배열을 검색 합니다.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|지정 된 DISPID로 식별 되는 속성의 값을 포함 하는 VARIANT를 검색 합니다. DISPID는에서 검색 된 문자열 이름과 연결 됩니다 `GetPredefinedStrings` . ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|지정 된 속성과 연결 된 속성 페이지의 CLSID를 검색 합니다.|

## <a name="remarks"></a>설명

[Iperpropertybrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) 인터페이스를 사용 하면 클라이언트가 개체의 속성 페이지에 있는 정보에 액세스할 수 있습니다. 클래스는 `IPerPropertyBrowsingImpl` 이 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

> [!NOTE]
> Microsoft Access를 컨테이너 응용 프로그램으로 사용 하는 경우에서 클래스를 파생 해야 합니다 `IPerPropertyBrowsingImpl` . 그렇지 않은 경우 액세스는 컨트롤을 로드 하지 않습니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a> IPerPropertyBrowsingImpl:: GetDisplayString

지정 된 속성을 설명 하는 문자열을 검색 합니다.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Iperpropertybrowsing:: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) 을 참조 하십시오.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a> IPerPropertyBrowsingImpl::GetPredefinedStrings

항목을 포함 하지 않는 각 배열을 채웁니다.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>반환 값

[GetPredefinedValue](#getpredefinedvalue) 의 ATL 구현은 E_NOTIMPL 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [Iperpropertybrowsing:: GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) 를 참조 하세요.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a> IPerPropertyBrowsingImpl::GetPredefinedValue

지정 된 DISPID로 식별 되는 속성의 값을 포함 하는 VARIANT를 검색 합니다. DISPID는에서 검색 된 문자열 이름과 연결 됩니다 `GetPredefinedStrings` .

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

ATL의 [GetPredefinedStrings](#getpredefinedstrings) 구현은 해당 하는 문자열을 검색 하지 않습니다.

Windows SDK에서 [Iperpropertybrowsing:: GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) 를 참조 하세요.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a> IPerPropertyBrowsingImpl::MapPropertyToPage

지정 된 속성과 연결 된 속성 페이지의 CLSID를 검색 합니다.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>설명

ATL은 개체의 속성 맵을 사용 하 여이 정보를 가져옵니다.

Windows SDK에서 [Iperpropertybrowsing:: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[IPropertyPageImpl 클래스](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 클래스](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
