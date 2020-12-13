---
description: '자세히 알아보기: IPersistStorageImpl 클래스'
title: IPersistStorageImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: 1d3d996886b587c25988139eed62e409650b5d4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139336"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 클래스

이 클래스는 [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) 인터페이스를 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPersistStorageImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IPersistStorageImpl:: GetClassID](#getclassid)|개체의 CLSID를 검색 합니다.|
|[IPersistStorageImpl:: 수동 Soffstorage](#handsoffstorage)|모든 저장소 개체를 해제 하 고 HandsOff 모드를 시작 하도록 개체에 지시 합니다. ATL 구현은 S_OK 반환 합니다.|
|[IPersistStorageImpl:: InitNew](#initnew)|새 저장소를 초기화 합니다.|
|[IPersistStorageImpl:: IsDirty](#isdirty)|개체의 데이터가 마지막으로 저장 된 후에 변경 되었는지 여부를 확인 합니다.|
|[IPersistStorageImpl:: Load](#load)|지정 된 저장소에서 개체의 속성을 로드 합니다.|
|[IPersistStorageImpl:: Save](#save)|개체의 속성을 지정 된 저장소에 저장 합니다.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|저장소 개체에 쓰도록 표준 모드로 돌아갈 수 있음을 개체에 알립니다. ATL 구현은 S_OK 반환 합니다.|

## <a name="remarks"></a>설명

`IPersistStorageImpl`[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) 인터페이스를 구현 합니다 .이 인터페이스를 통해 클라이언트는 개체 로드를 요청 하 고 저장소를 사용 하 여 영구 데이터를 저장할 수 있습니다.

이 클래스를 구현 하려면 클래스에서 `T` 를 `IPersistStreamInit` 통해 사용할 수 있는 인터페이스의 구현을 만들어야 `QueryInterface` 합니다. 일반적으로이는 클래스가 `T` [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)에서 파생 되 고, COM 맵에에 대 한 항목을 제공 하 `IPersistStreamInit` 고, [속성 맵을](property-map-macros.md) 사용 하 여 클래스의 영구 데이터를 설명 [](com-map-macros.md)하는 것을 의미 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a> IPersistStorageImpl:: GetClassID

개체의 CLSID를 검색 합니다.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Ipersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 를 참조 하세요.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a> IPersistStorageImpl:: 수동 Soffstorage

모든 저장소 개체를 해제 하 고 HandsOff 모드를 시작 하도록 개체에 지시 합니다.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IPersistStorage:: 핸드 핸드 Ffstorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) 를 참조 하세요.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a> IPersistStorageImpl:: InitNew

새 저장소를 초기화 합니다.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>설명

ATL 구현은 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스에 위임 합니다.

Windows SDK [IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) 를 참조 하세요.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a> IPersistStorageImpl:: IsDirty

개체의 데이터가 마지막으로 저장 된 후에 변경 되었는지 여부를 확인 합니다.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>설명

ATL 구현은 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스에 위임 합니다.

Windows SDK에서 [IPersistStorage: IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) 를 참조 하세요.

## <a name="ipersiststorageimplload"></a><a name="load"></a> IPersistStorageImpl:: Load

지정 된 저장소에서 개체의 속성을 로드 합니다.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>설명

ATL 구현은 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스에 위임 합니다. `Load` "Contents" 라는 스트림을 사용 하 여 개체의 데이터를 검색 합니다. [Save](#save) 메서드는 원래이 스트림을 만듭니다.

[IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) in the Windows SDK를 참조 하세요.

## <a name="ipersiststorageimplsave"></a><a name="save"></a> IPersistStorageImpl:: Save

개체의 속성을 지정 된 저장소에 저장 합니다.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>설명

ATL 구현은 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스에 위임 합니다. `Save`를 처음 호출 하면 지정 된 저장소에 "Contents" 라는 스트림이 생성 됩니다. 이 스트림은 나중에에 대 `Save` 한 호출과 [로드](#load)호출에 사용 됩니다.

Windows SDK [IPersistStorage: 저장](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) 을 참조 하세요.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a> IPersistStorageImpl::SaveCompleted

저장소 개체에 쓰도록 표준 모드로 돌아갈 수 있음을 개체에 알립니다.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK [IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[저장소 및 스트림](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl 클래스](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl 클래스](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
