---
description: '자세히 알아보기: IPersistStreamInitImpl 클래스'
title: IPersistStreamInitImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: f60483435be750c7031f2e7bf7f3f18cba36a023
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158155"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl 클래스

이 클래스는 `IUnknown` 를 구현 하 고 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스의 기본 구현을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPersistStreamInitImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IPersistStreamInitImpl:: GetClassID](#getclassid)|개체의 CLSID를 검색 합니다.|
|[IPersistStreamInitImpl:: GetSizeMax](#getsizemax)|개체의 데이터를 저장 하는 데 필요한 스트림의 크기를 검색 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IPersistStreamInitImpl:: InitNew](#initnew)|새로 만든 개체를 초기화 합니다.|
|[IPersistStreamInitImpl:: IsDirty](#isdirty)|개체의 데이터가 마지막으로 저장 된 후에 변경 되었는지 여부를 확인 합니다.|
|[IPersistStreamInitImpl:: Load](#load)|지정 된 스트림에서 개체의 속성을 로드 합니다.|
|[IPersistStreamInitImpl:: Save](#save)|개체의 속성을 지정 된 스트림에 저장 합니다.|

## <a name="remarks"></a>설명

[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스를 사용 하 여 클라이언트가 개체를 로드 하 고 영구 데이터를 단일 스트림으로 저장할 수 있습니다. 클래스는 `IPersistStreamInitImpl` 이 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a> IPersistStreamInitImpl:: GetClassID

개체의 CLSID를 검색 합니다.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Ipersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 를 참조 하세요.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a> IPersistStreamInitImpl:: GetSizeMax

개체의 데이터를 저장 하는 데 필요한 스트림의 크기를 검색 합니다.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) 를 참조 하세요.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a> IPersistStreamInitImpl:: InitNew

새로 만든 개체를 초기화 합니다.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>설명

Windows SDK에서 [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) 를 참조 하세요.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a> IPersistStreamInitImpl:: IsDirty

개체의 데이터가 마지막으로 저장 된 후에 변경 되었는지 여부를 확인 합니다.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>설명

Windows SDK에서 [IPersistStreamInit:: IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) 를 참조 하세요.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a> IPersistStreamInitImpl:: Load

지정 된 스트림에서 개체의 속성을 로드 합니다.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>설명

ATL은 개체의 속성 맵을 사용 하 여이 정보를 검색 합니다.

Windows SDK [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) 를 참조 하세요.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a> IPersistStreamInitImpl:: Save

개체의 속성을 지정 된 스트림에 저장 합니다.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>설명

ATL은 개체의 속성 맵을 사용 하 여이 정보를 저장 합니다.

Windows SDK [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[저장소 및 스트림](/windows/win32/Stg/storages-and-streams)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
