---
description: '자세히 알아보기: IAccessorImpl 클래스'
title: IAccessorImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: e7b2c2ea7192ec0fdb8c943ce4062ada0b1f0504
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287413"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 클래스

[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) 인터페이스의 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
행 집합 또는 명령 개체 클래스입니다.

*BindType*<br/>
바인딩 정보에 대 한 저장소 단위입니다. 기본값은 `ATLBINDINGS` 구조체 (atldb.h 참조)입니다.

*BindingVector*<br/>
열 정보에 대 한 저장소 단위입니다. 기본값은 핵심 요소가 HACCESSOR 값이 고 value 요소가 구조체에 대 한 [포인터인 경우에](../../atl/reference/catlmap-class.md) 해당 합니다 `BindType` .

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[IAccessorImpl](#iaccessorimpl)|생성자입니다.|

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[AddRefAccessor](#addrefaccessor)|기존 접근자에 참조 횟수를 추가합니다.|
|[CreateAccessor](#createaccessor)|바인딩 집합에서 접근자를 만듭니다.|
|[GetBindings](#getbindings)|접근자에 있는 바인딩을 반환합니다.|
|[ReleaseAccessor](#releaseaccessor)|접근자를 해제합니다.|

## <a name="remarks"></a>설명

이는 행 집합 및 명령에 필수입니다. OLE DB에서는 공급자가 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 구조체의 배열에 대 한 태그란 haccessor를 구현 해야 합니다. 에서 제공 하는 HACCESSORs `IAccessorImpl` 는 구조체의 주소 `BindType` 입니다. 기본적으로 `BindType` 는 `ATLBINDINGS` 의 템플릿 정의로 정의 됩니다 `IAccessorImpl` . `BindType` 에서 `IAccessorImpl` 배열의 요소 수와 `DBBINDING` 참조 개수 및 접근자 플래그를 추적 하는 데 사용 하는 메커니즘을 제공 합니다.

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a> IAccessorImpl:: IAccessorImpl

생성자입니다.

### <a name="syntax"></a>Syntax

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a> IAccessorImpl:: AddRefAccessor

기존 접근자에 참조 횟수를 추가합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 의 [IAccessor:: addrefaccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) 를 참조 하세요.

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a> IAccessorImpl:: CreateAccessor

바인딩 집합에서 접근자를 만듭니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 의 [IAccessor:: createaccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) 를 참조 하세요.

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a> IAccessorImpl:: GetBindings

접근자에 있는 소비자의 기본 열 바인딩을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IAccessor:: getbindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) 를 참조 하세요.

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a> IAccessorImpl:: ReleaseAccessor

접근자를 해제합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 의 [IAccessor:: releaseaccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
