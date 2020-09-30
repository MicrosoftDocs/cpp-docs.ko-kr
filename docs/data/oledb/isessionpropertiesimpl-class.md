---
title: ISessionPropertiesImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: d664f32226498326ffb092f1d3248fbdbf614d50
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509762"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 클래스

[Isessionproperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) 인터페이스의 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `ISessionPropertiesImpl` 입니다.

*PropClass*<br/>
*T*를 기본값으로 사용 하는 사용자 정의 가능한 속성 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| 속성 | 설명 |
|-|-|
|[GetProperties](#getproperties)|세션에 현재 설정 된 세션 속성 그룹의 속성 목록을 반환 합니다.|
|[SetProperties](#setproperties)|Session 속성 그룹의 속성을 설정 합니다.|

## <a name="remarks"></a>설명

세션에 대 한 필수 인터페이스입니다. 이 클래스는 [속성 집합 맵에](./macros-for-ole-db-provider-templates.md#begin_propset_map)의해 정의 된 정적 함수를 호출 하 여 세션 속성을 구현 합니다. 속성 집합 맵은 session 클래스에서 지정 해야 합니다.

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a> IsessionGetProperties의 구현이::

`DBPROPSET_SESSION`현재 세션에 설정 되어 있는 속성 그룹의 속성 목록을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Isessionproperties:: GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) 를 참조 하세요.

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a> IsessionSetProperties의 구현이::

속성 그룹의 속성을 설정 `DBPROPSET_SESSION` 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [Isessionproperties:: SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
