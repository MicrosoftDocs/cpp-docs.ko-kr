---
title: IRowsetImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 27a07d10256147d3c3ed383744ba1ee5fdfd06a1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504076"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl 클래스

`IRowset` 인터페이스의 구현을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetImpl` 입니다.

*RowsetInterface*<br/>
에서 파생 된 클래스 `IRowsetImpl` 입니다.

*RowClass*<br/>
의 저장소 단위 `HROW` 입니다.

*MapClass*<br/>
공급자가 보유 한 모든 행 핸들의 저장소 단위입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddRefRows](#addrefrows)|기존 행 핸들에 참조 횟수를 추가합니다.|
|[CreateRow](#createrow)|새를 할당 하기 위해 [GetNextRows](#getnextrows) 에서 호출 `HROW` 됩니다. 사용자가 직접 호출 하지 않습니다.|
|[GetData](#getdata)|행 집합의 행 복사본에서 데이터를 검색합니다.|
|[GetDBStatus](#getdbstatus)|지정 된 필드의 상태를 반환 합니다.|
|[GetNextRows](#getnextrows)|이전 위치를 기억하여 행을 순서대로 페치합니다.|
|[IRowsetImpl](#irowsetimpl)|생성자입니다. 사용자가 직접 호출 하지 않습니다.|
|[RefRows](#refrows)|[Addrefrows](#addrefrows) 및 [ReleaseRows](#releaserows)에서 호출 됩니다. 사용자가 직접 호출 하지 않습니다.|
|[ReleaseRows](#releaserows)|행을 해제합니다.|
|[RestartPosition](#restartposition)|다음 인출 위치를 초기 위치로 위치를 다시 배치 합니다. 즉, 행 집합을 처음 만들 때의 위치입니다.|
|[SetDBStatus](#setdbstatus)|지정 된 필드의 상태 플래그를 설정 합니다.|

### <a name="data-members"></a>데이터 멤버

| 속성 | 설명 |
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|공급자가 뒤로 페치를 지원할지 여부를 나타냅니다.|
|[m_bCanScrollBack](#bcanscrollback)|공급자가 커서를 뒤로 스크롤할 수 있는지 여부를 나타냅니다.|
|[m_bReset](#breset)|공급자가 커서 위치를 다시 설정 했는지 여부를 나타냅니다. 이는 [GetNextRows](#getnextrows)에서 뒤로 스크롤 하거나 인출할 때 특별 한 의미가 있습니다.|
|[m_iRowset](#irowset)|커서를 나타내는 행 집합에 대 한 인덱스입니다.|
|[m_rgRowHandles](#rgrowhandles)|행 핸들의 목록입니다.|

## <a name="remarks"></a>설명

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) 는 기본 행 집합 인터페이스입니다.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a> IRowsetImpl:: AddRefRows

기존 행 핸들에 참조 횟수를 추가합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: addrefrows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 를 참조 하세요.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a> IRowsetImpl:: CreateRow

새를 할당 하기 위해 [GetNextRows](#getnextrows) 에서 호출 하는 도우미 메서드입니다 `HROW` .

### <a name="syntax"></a>구문

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>매개 변수

*lRowsOffset*<br/>
만들 행의 커서 위치입니다.

*cRowsObtained*<br/>
만든 행 수를 나타내는 참조를 사용자에 게 다시 전달 합니다.

*rgRows*<br/>
`HROW`새로 만든 행 핸들을 사용 하 여 호출자에 게 반환 되는의 배열입니다.

### <a name="remarks"></a>설명

행이 있으면이 메서드는 [Addrefrows](#addrefrows) 를 호출 하 고를 반환 합니다. 그렇지 않으면 RowClass 템플릿 변수의 새 인스턴스를 할당 하 고 [m_rgRowHandles](#rgrowhandles)에 추가 합니다.

## <a name="irowsetimplgetdata"></a><a name="getdata"></a> IRowsetImpl:: GetData

행 집합의 행 복사본에서 데이터를 검색합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) 를 참조 하세요.

일부 매개 변수는에서 설명 하는 다양 한 이름의 *프로그래머 참조* 매개 변수 OLE DB에 해당 합니다 `IRowset::GetData` .

|OLE DB 템플릿 매개 변수|*OLE DB 프로그래머 참조* 매개 변수|
|--------------------------------|------------------------------------------------|
|*Ststdata*|*pData*|

### <a name="remarks"></a>설명

또한 OLE DB 데이터 변환 DLL을 사용 하 여 데이터 변환을 처리 합니다.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a> IRowsetImpl:: GetDBStatus

지정 된 필드의 DBSTATUS 상태 플래그를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>매개 변수

*Customer.currentrow*<br/>
진행 현재 행입니다.

*columnNames*<br/>
진행 상태를 요청 하는 열입니다.

### <a name="return-value"></a>반환 값

열에 대 한 [Dbstatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) 플래그입니다.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a> IRowsetImpl:: GetNextRows

이전 위치를 기억하여 행을 순서대로 페치합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) 를 참조 하세요.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a> IRowsetImpl:: IRowsetImpl

생성자입니다.

### <a name="syntax"></a>구문

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>설명

일반적으로이 메서드를 직접 호출할 필요는 없습니다.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a> IRowsetImpl:: RefRows

기존 행 핸들의 참조 횟수를 증가 시키거나 해제 하기 위해 [Addrefrows](#addrefrows) 및 [ReleaseRows](#releaserows) 에서 호출 됩니다.

### <a name="syntax"></a>구문

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: addrefrows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a> IRowsetImpl:: ReleaseRows

행을 해제합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) 를 참조 하세요.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a> IRowsetImpl:: RestartPosition

다음 인출 위치를 초기 위치로 위치를 다시 배치 합니다. 즉, 행 집합을 처음 만들 때의 위치입니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [IRowset:: RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

행 집합 위치는가 호출 될 때까지 정의 되지 않습니다 `GetNextRow` . 을 호출 하 `RestartPosition` 고 뒤로 인출 또는 스크롤 하 여 rost에서 뒤로 이동할 수 있습니다.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a> IRowsetImpl:: SetDBStatus

지정 된 필드에 대 한 DBSTATUS 상태 플래그를 설정 합니다.

### <a name="syntax"></a>구문

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>매개 변수

*statusFlags*<br/>
열에 설정할 [Dbstatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) 플래그입니다.

*Customer.currentrow*<br/>
현재 행

*columnInfo*<br/>
상태를 설정할 열입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

공급자는이 함수를 재정의 하 여 DBSTATUS_S_ISNULL 및 DBSTATUS_S_DEFAULT에 대 한 특수 한 처리를 제공 합니다.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a> IRowsetImpl:: m_bCanFetchBack

공급자가 뒤로 페치를 지원할지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>설명

`DBPROP_CANFETCHBACKWARDS`그룹의 속성에 연결 `DBPROPSET_ROWSET` 됩니다. 공급자는를 지원 해야 합니다 `DBPROP_CANFETCHBACKWARDS` `m_bCanFetchBackwards` **`true`** .

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a> IRowsetImpl:: m_bCanScrollBack

공급자가 커서를 뒤로 스크롤할 수 있는지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>설명

`DBPROP_CANSCROLLBACKWARDS`그룹의 속성에 연결 `DBPROPSET_ROWSET` 됩니다. 공급자는를 지원 해야 합니다 `DBPROP_CANSCROLLBACKWARDS` `m_bCanFetchBackwards` **`true`** .

## <a name="irowsetimplm_breset"></a><a name="breset"></a> IRowsetImpl:: m_bReset

커서 위치가 행 집합에 정의 되어 있는지 여부를 확인 하는 데 사용 되는 비트 플래그입니다.

### <a name="syntax"></a>구문

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>설명

소비자가 음수 또는 CRows를 사용 하 여 [GetNextRows](#getnextrows) 를 호출 `lOffset` 하 *cRows* 고 `m_bReset` 가 true 이면 `GetNextRows` 행 집합의 끝으로 이동 합니다. `m_bReset`가 false 이면 소비자는 OLE DB 사양을 준수 하 여 오류 코드를 수신 합니다. `m_bReset`플래그는 **`true`** 행 집합을 처음 만들 때와 소비자가 [IRowsetImpl:: RestartPosition](#restartposition)를 호출 하는 경우로 설정 됩니다. 를 **`false`** 호출할 때로 설정 `GetNextRows` 됩니다.

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a> IRowsetImpl:: m_iRowset

커서를 나타내는 행 집합에 대 한 인덱스입니다.

### <a name="syntax"></a>구문

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a> IRowsetImpl:: m_rgRowHandles

에 대 한 응답으로 공급자에 현재 포함 된 행 핸들의 맵입니다 `GetNextRows` .

### <a name="syntax"></a>구문

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>설명

을 호출 하 여 행 핸들을 제거 `ReleaseRows` 합니다. *Mapclass*의 정의는 [IRowsetImpl 개요](../../data/oledb/irowsetimpl-class.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow 클래스](../../data/oledb/csimplerow-class.md)
