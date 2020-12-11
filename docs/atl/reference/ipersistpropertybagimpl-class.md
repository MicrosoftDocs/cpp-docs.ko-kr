---
description: '자세히 알아보기: IPersistPropertyBagImpl 클래스'
title: IPersistPropertyBagImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: 1e244c4349bd04a83d257280da3315f2c797003a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158168"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 클래스

이 클래스 `IUnknown` 는를 구현 하 고 개체에서 클라이언트 제공 속성 모음에 속성을 저장할 수 있도록 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPersistPropertyBagImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IPersistPropertyBagImpl:: GetClassID](#getclassid)|개체의 CLSID를 검색 합니다.|
|[IPersistPropertyBagImpl:: InitNew](#initnew)|새로 만든 개체를 초기화 합니다. ATL 구현은 S_OK 반환 합니다.|
|[IPersistPropertyBagImpl:: Load](#load)|클라이언트 제공 속성 모음에서 개체의 속성을 로드 합니다.|
|[IPersistPropertyBagImpl:: Save](#save)|클라이언트 제공 속성 모음에 개체의 속성을 저장 합니다.|

## <a name="remarks"></a>설명

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) 인터페이스를 사용 하면 개체가 클라이언트 제공 속성 모음에 속성을 저장할 수 있습니다. 클래스는 `IPersistPropertyBagImpl` 이 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

`IPersistPropertyBag`[IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) 및 [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\))와 함께 작동 합니다. 이러한 후자의 두 인터페이스는 클라이언트에 의해 구현 되어야 합니다. `IPropertyBag`클라이언트는를 통해 개체의 개별 속성을 저장 하 고 로드 합니다. 에서 `IErrorLog` 개체와 클라이언트는 모두 발생 한 오류를 보고할 수 있습니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a> IPersistPropertyBagImpl:: GetClassID

개체의 CLSID를 검색 합니다.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Ipersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 를 참조 하세요.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a> IPersistPropertyBagImpl:: InitNew

새로 만든 개체를 초기화 합니다.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) 를 참조 하세요.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a> IPersistPropertyBagImpl:: Load

클라이언트 제공 속성 모음에서 개체의 속성을 로드 합니다.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>설명

ATL은 개체의 속성 맵을 사용 하 여이 정보를 검색 합니다.

Windows SDK [IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) 를 참조 하세요.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a> IPersistPropertyBagImpl:: Save

클라이언트 제공 속성 모음에 개체의 속성을 저장 합니다.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>설명

ATL은 개체의 속성 맵을 사용 하 여이 정보를 저장 합니다. 기본적으로이 메서드는 *Fsaveallproperties* 의 값에 관계 없이 모든 속성을 저장 합니다.

Windows SDK [IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
