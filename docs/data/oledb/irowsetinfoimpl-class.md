---
description: '자세히 알아보기: IRowsetInfoImpl 클래스'
title: IRowsetInfoImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: cc51a32b6bee62ef7343bf134b3f1bc4099b8562
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317365"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 클래스

[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) 인터페이스에 대 한 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetInfoImpl` 입니다.

*PropClass*<br/>
*T* 를 기본값으로 사용 하는 사용자 정의 가능한 속성 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** altdb .h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[GetProperties](#getproperties)|행 집합에서 지원하는 모든 속성의 현재 설정을 반환합니다.|
|[GetReferencedRowset](#getreferencedrowset)|책갈피가 적용 되는 행 집합에 대 한 인터페이스 포인터를 반환 합니다.|
|[GetSpecification](#getspecification)|이 행 집합을 만든 개체(명령 또는 세션)의 인터페이스 포인터를 반환합니다.|

## <a name="remarks"></a>설명

행 집합의 필수 인터페이스입니다. 이 클래스는 명령 클래스에 정의 된 [속성 집합 맵을](./macros-for-ole-db-provider-templates.md#begin_propset_map) 사용 하 여 행 집합 속성을 구현 합니다. 행 집합 클래스는 command 클래스의 속성 집합을 사용 하는 것 처럼 보이지만 명령 또는 세션 개체에 의해 생성 될 때 해당 행 집합은 런타임 속성의 자체 복사본과 함께 제공 됩니다.

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a> IRowsetInfoImpl:: GetProperties

그룹의 속성에 대 한 현재 설정을 반환 합니다 `DBPROPSET_ROWSET` .

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetInfo:: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) 를 참조 하세요.

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a> IRowsetInfoImpl:: GetReferencedRowset

책갈피가 적용 되는 행 집합에 대 한 인터페이스 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetInfo:: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) 을 참조 하세요. *Iordinal* 매개 변수는 책갈피 열 이어야 합니다.

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a> IRowsetInfoImpl:: GetSpecification

이 행 집합을 만든 개체(명령 또는 세션)의 인터페이스 포인터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetInfo:: getspecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) 을 참조 하세요.

### <a name="remarks"></a>설명

[Igetdatasourceimpl](../../data/oledb/igetdatasourceimpl-class.md) 포함 된이 메서드를 사용 하 여 데이터 원본 개체에서 속성을 검색 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
