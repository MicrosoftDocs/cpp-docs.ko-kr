---
description: '자세히 알아보기: IDBPropertiesImpl 클래스'
title: IDBPropertiesImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: e8384086de5b61422cd63e2dc3fbda0cfe040843
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317495"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 클래스

인터페이스에 대 한 구현을 제공 `IDBProperties` 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IDBPropertiesImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[GetProperties](#getproperties)|데이터 원본 개체에 현재 설정 된 데이터 원본, 데이터 원본 정보 및 초기화 속성 그룹의 속성 값 또는 현재 열거자에 설정 된 초기화 속성 그룹의 속성 값을 반환 합니다.|
|[GetPropertyInfo](#getpropertyinfo)|공급자가 지 원하는 모든 속성에 대 한 정보를 반환 합니다.|
|[SetProperties](#setproperties)|열거자에 대 한 데이터 원본 및 초기화 속성 그룹, 데이터 원본 개체 또는 초기화 속성 그룹의 속성을 설정 합니다.|

## <a name="remarks"></a>설명

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) 는 데이터 원본 개체에 대 한 필수 인터페이스 이며 열거자에 대 한 선택적 인터페이스입니다. 그러나 열거자가 [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))를 노출 하는 경우를 노출 해야 `IDBProperties` 합니다. `IDBPropertiesImpl``IDBProperties` [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map)에서 정의한 정적 함수를 사용 하 여를 구현 합니다.

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a> IDBPropertiesImpl:: GetProperties

데이터 원본 개체에 현재 설정 된 데이터 원본, 데이터 원본 정보 및 초기화 속성 그룹의 속성 값 또는 현재 열거자에 설정 된 초기화 속성 그룹의 속성 값을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) 를 참조 하세요.

일부 매개 변수는에서 설명 하는 다양 한 이름의 *프로그래머 참조* 매개 변수 OLE DB에 해당 합니다 `IDBProperties::GetProperties` .

|OLE DB 템플릿 매개 변수|*OLE DB 프로그래머 참조* 매개 변수|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>설명

공급자가 초기화 되 면이 메서드는 데이터 원본 개체에 현재 설정 된 DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT 속성 그룹의 속성 값을 반환 합니다. 공급자가 초기화 되지 않은 경우에는 DBPROPSET_DBINIT 그룹 속성만 반환 합니다.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a> IDBPropertiesImpl:: GetPropertyInfo

데이터 원본에서 지 원하는 속성 정보를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) 를 참조 하세요.

일부 매개 변수는에서 설명 하는 다양 한 이름의 *프로그래머 참조* 매개 변수 OLE DB에 해당 합니다 `IDBProperties::GetPropertyInfo` .

|OLE DB 템플릿 매개 변수|*OLE DB 프로그래머 참조* 매개 변수|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>설명

[IDBInitializeImpl:: m_pCUtlPropInfo](./idbinitializeimpl-class.md#pcutlpropinfo) 을 사용 하 여이 기능을 구현 합니다.

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a> IDBPropertiesImpl:: SetProperties

열거자에 대 한 데이터 원본 및 초기화 속성 그룹, 데이터 원본 개체 또는 초기화 속성 그룹의 속성을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

공급자가 초기화 되 면이 메서드는 데이터 원본 개체에 대 한 DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT 속성 그룹의 속성 값을 설정 합니다. 공급자가 초기화 되지 않은 경우에는 DBPROPSET_DBINIT 그룹 속성만 설정 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
