---
description: '자세히 알아보기: IProvideClassInfo2Impl 클래스'
title: IProvideClassInfo2Impl 클래스
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 9c3422c98ebd857231f492efb77d51a0a49acb76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139259"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl 클래스

이 클래스는 [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) 및 [마샬러가 iprovideclassinfo2.getguid](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) 메서드의 기본 구현을 제공 합니다.

## <a name="syntax"></a>구문

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>매개 변수

*pcoclsid*<br/>
Coclass의 식별자에 대 한 포인터입니다.

*psrcid*<br/>
Coclass의 기본 나가는 서 수에 대 한 식별자에 대 한 포인터입니다.

*plibid*<br/>
인터페이스에 대 한 정보를 포함 하는 형식 라이브러리의 LIBID에 대 한 포인터입니다. 기본적으로 서버 수준 형식 라이브러리가 전달 됩니다.

*wMajor*<br/>
형식 라이브러리의 주 버전입니다. 기본값은 1입니다.

*wMinor*<br/>
형식 라이브러리의 부 버전입니다. 기본값은 0입니다.

*tihclass*<br/>
Coclass의 형식 정보를 관리 하는 데 사용 되는 클래스입니다. 기본값은 `CComTypeInfoHolder`입니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IProvideClassInfo2Impl:: GetClassInfo](#getclassinfo)|`ITypeInfo`Coclass의 형식 정보에 대 한 포인터를 검색 합니다.|
|[IProvideClassInfo2Impl:: GetGUID](#getguid)|개체의 나가는 개체에 대 한 GUID를 검색 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Coclass에 대 한 형식 정보를 관리 합니다.|

## <a name="remarks"></a>설명

마샬러가 [iprovideclassinfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) 인터페이스는 `GetGUID` 메서드를 추가하여 [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)를 확장합니다. 클라이언트는이 메서드를 사용 하 여 기본 이벤트 집합에 대 한 개체의 송신 인터페이스 IID를 검색할 수 있습니다. 클래스는 `IProvideClassInfo2Impl` 및 메서드의 기본 구현을 제공 `IProvideClassInfo` `IProvideClassInfo2` 합니다.

`IProvideClassInfo2Impl``CComTypeInfoHolder`coclass에 대 한 형식 정보를 관리 하는 형식의 정적 멤버를 포함 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a> IProvideClassInfo2Impl:: GetClassInfo

`ITypeInfo`Coclass의 형식 정보에 대 한 포인터를 검색 합니다.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>설명

Windows SDK [IProvideClassInfo:: GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) 를 참조 하세요.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a> IProvideClassInfo2Impl:: GetGUID

개체의 나가는 개체에 대 한 GUID를 검색 합니다.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>설명

Windows SDK에서 [마샬러가 iprovideclassinfo2.getguid:: GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) 를 참조 하세요.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a> IProvideClassInfo2Impl::IProvideClassInfo2Impl

생성자입니다.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>설명

`AddRef` [_Tih](#_tih) 멤버에 대 한를 호출 합니다. 이 소멸자는 `Release`을 호출합니다.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a> IProvideClassInfo2Impl:: _tih

이 정적 데이터 멤버는 기본적으로 인 *tihclass* 클래스 템플릿 매개 변수의 인스턴스입니다 `CComTypeInfoHolder` .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>설명

`_tih` coclass에 대 한 형식 정보를 관리 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
