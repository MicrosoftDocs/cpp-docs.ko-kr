---
title: IRowsetUpdateImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 88ee9257655c96195339ded79f2dd4d3b7c7caf5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509779"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 클래스

[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) 인터페이스의 OLE DB 템플릿 구현입니다.

## <a name="syntax"></a>구문

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetUpdateImpl` 입니다.

*스토리지*<br/>
사용자 레코드입니다.

*UpdateArray*<br/>
행 집합을 업데이트 하기 위해 캐시 된 데이터를 포함 하는 배열입니다.

*RowClass*<br/>
의 저장소 단위 `HROW` 입니다.

*MapClass*<br/>
공급자가 보유 한 모든 행 핸들의 저장소 단위입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods-used-with-irowsetchange"></a>인터페이스 메서드 (IRowsetChange와 함께 사용 됨)

| 속성 | 설명 |
|-|-|
|[SetData](#setdata)|하나 이상의 열에 데이터 값을 설정 합니다.|

### <a name="interface-methods-used-with-irowsetupdate"></a>인터페이스 메서드 (IRowsetUpdate와 함께 사용 됨)

| 속성 | 설명 |
|-|-|
|[GetOriginalData](#getoriginaldata)|보류 중인 변경 내용을 무시 하 고 데이터 원본에서 가장 최근에 전송 되거나 데이터 원본에서 가져온 데이터를 가져옵니다.|
|[GetPendingRows](#getpendingrows)|보류 중인 변경 내용이 있는 행의 목록을 반환 합니다.|
|[GetRowStatus](#getrowstatus)|지정 된 행의 상태를 반환 합니다.|
|[실행 취소](#undo)|마지막 인출 또는 업데이트 이후 행의 변경 내용을 취소 합니다.|
|[Update](#update)|마지막 인출 또는 업데이트 이후 행의 변경 내용을 전송 합니다.|

### <a name="implementation-methods-callback"></a>구현 메서드 (콜백)

| 속성 | 설명 |
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|업데이트를 허용 하기 전에 보안, 무결성 등을 확인 하는 데 사용 됩니다.|

### <a name="data-members"></a>데이터 멤버

| 속성 | 설명 |
|-|-|
|[m_mapCachedData](#mapcacheddata)|지연 된 작업의 원래 데이터를 포함 합니다.|

## <a name="remarks"></a>설명

여기에 설명 된 모든 내용이 여기에 적용 되므로 먼저 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))설명서를 읽고 이해 해야 합니다. 데이터 설정에 대 한 *OLE DB 프로그래머 참조* 의 6 장도 읽어야 합니다.

`IRowsetUpdateImpl``IRowsetUpdate`소비자가 데이터 소스에 대 한 변경 내용 전송을 지연 하 `IRowsetChange` 고 전송 전에 변경 내용을 실행 취소할 수 있도록 하는 OLE DB 인터페이스를 구현 합니다.

> [!IMPORTANT]
> 공급자를 구현 하기 전에 다음 문서를 참조 하는 것이 좋습니다.

- [업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)

- *OLE DB 프로그래머 참조* 의 6 장

- 또한 `RUpdateRowset` 클래스가 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플에서 어떻게 사용 되는지 확인 합니다.

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a> IRowsetUpdateImpl:: SetData

하나 이상의 열에 데이터 값을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 [IRowsetChangeImpl:: SetData](./irowsetchangeimpl-class.md#setdata) 메서드를 재정의 하지만 작업의 즉시 또는 지연 된 처리를 허용 하기 위해 원본 데이터의 캐싱을 포함 합니다.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a> IRowsetUpdateImpl:: GetOriginalData

보류 중인 변경 내용을 무시 하 고 데이터 원본에서 가장 최근에 전송 되거나 데이터 원본에서 가져온 데이터를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: getoriginaldata](/previous-versions/windows/desktop/ms709947(v=vs.85)) 를 참조 하세요.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a> IRowsetUpdateImpl:: GetPendingRows

보류 중인 변경 내용이 있는 행의 목록을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85))의 *hchapter* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: getpendingrows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: getpendingrows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 를 참조 하세요.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a> IRowsetUpdateImpl:: GetRowStatus

지정 된 행의 상태를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85))의 *hchapter* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) 를 참조 하세요.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a> IRowsetUpdateImpl:: Undo

마지막 인출 또는 업데이트 이후 행의 변경 내용을 취소 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))의 *hchapter* 매개 변수에 해당 합니다.

*pcRowsUndone*<br/>
제한이 [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))의 *pcrows* 매개 변수에 해당 합니다.

*prgRowsUndone*<br/>
진행 [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))의 *prgrows* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) 를 참조 하세요.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a> IRowsetUpdateImpl:: Update

마지막 인출 또는 업데이트 이후 행의 변경 내용을 전송 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85))의 *hchapter* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조*에서 [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

[IRowsetChangeImpl:: FlushData](./irowsetchangeimpl-class.md#flushdata)를 호출 하 여 변경 내용을 전송 합니다. 소비자는 [CRowset:: Update](./crowset-class.md#update) 를 호출 하 여 변경 내용을 적용 해야 합니다. *OLE DB 프로그래머 참조*의 [행 상태](/previous-versions/windows/desktop/ms722752(v=vs.85)) 에 설명 된 대로 *prgRowstatus* 을 적절 한 값으로 설정 합니다.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a> IRowsetUpdateImpl:: IsUpdateAllowed

업데이트 전에 보안, 무결성 등을 확인 하려면이 메서드를 재정의 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>매개 변수

*status*<br/>
진행 행에 대 한 보류 중인 작업의 상태입니다.

*hRowUpdate*<br/>
진행 사용자가 업데이트 하려는 행의 핸들입니다.

*pRowStatus*<br/>
제한이 사용자에 게 반환 되는 상태입니다.

### <a name="remarks"></a>설명

업데이트를 허용 해야 하는 것으로 확인 되 면 S_OK을 반환 합니다. 그렇지 않으면 E_FAIL을 반환 합니다. 업데이트를 허용 하는 경우 `DBROWSTATUS` [IRowsetUpdateImpl:: update](#update) 의를 적절 한 [행 상태로](/previous-versions/windows/desktop/ms722752(v=vs.85))설정 해야 합니다.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a> IRowsetUpdateImpl:: m_mapCachedData

지연 된 작업의 원래 데이터를 포함 하는 맵입니다.

### <a name="syntax"></a>구문

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>매개 변수

*hRow*<br/>
데이터 행에 대 한 핸들입니다.

*pData*<br/>
캐시 될 데이터에 대 한 포인터입니다. 데이터는 *저장소* (사용자 레코드 클래스) 유형입니다. [IRowsetUpdateImpl 클래스](../../data/oledb/irowsetupdateimpl-class.md)의 *저장소* 템플릿 인수를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)
