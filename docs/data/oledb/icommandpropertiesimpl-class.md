---
description: '자세히 알아보기: ICommandPropertiesImpl 클래스'
title: ICommandPropertiesImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: bf6a6f9a3ddd43a61671a85a791d63958f63c3e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317569"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 클래스

[ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) 인터페이스의 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
클래스는에서 파생 됩니다.

*PropClass*<br/>
속성 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[GetProperties](#getproperties)|행 집합에 대해 현재 요청 된 행 집합 속성 그룹의 속성 목록을 반환 합니다.|
|[SetProperties](#setproperties)|행 집합 속성 그룹의 속성을 설정 합니다.|

## <a name="remarks"></a>설명

명령에 필수입니다. 구현은 [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) 매크로에서 정의한 정적 함수를 통해 제공 됩니다.

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> ICommandPropertiesImpl:: GetProperties

명령의 속성 맵을 사용 하 여 요청 된 모든 속성 집합을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

[BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map)을 참조하세요.

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> ICommandPropertiesImpl:: SetProperties

Command 개체에 대 한 속성을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
