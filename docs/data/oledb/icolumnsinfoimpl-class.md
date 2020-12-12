---
description: '자세히 알아보기: IColumnsInfoImpl 클래스'
title: IColumnsInfoImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 9f6586f4d0315904ea16baf5aa1837bc43107602
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317625"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl 클래스

[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) 인터페이스의 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,
   public CDBIDOps
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IColumnsInfoImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetColumnInfo](#getcolumninfo)|대부분의 소비자에 필요한 열 메타데이터를 반환합니다.|
|[MapColumnIDs](#mapcolumnids)|지정된 열 ID로 식별되는 행 집합에 있는 열의 서수의 배열을 반환합니다.|

## <a name="remarks"></a>설명

행 집합 및 명령의 필수 인터페이스입니다. 공급자 구현의 동작을 수정 하려면 `IColumnsInfo` 공급자 열 맵을 수정 해야 합니다.

## <a name="icolumnsinfoimplgetcolumninfo"></a><a name="getcolumninfo"></a> IColumnsInfoImpl:: GetColumnInfo

대부분의 소비자에 필요한 열 메타데이터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 를 참조 하세요.

## <a name="icolumnsinfoimplmapcolumnids"></a><a name="mapcolumnids"></a> IColumnsInfoImpl:: MapColumnIDs

지정된 열 ID로 식별되는 행 집합에 있는 열의 서수의 배열을 반환합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IColumnsInfo:: mapcolumnids](/previous-versions/windows/desktop/ms714200(v=vs.85)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
