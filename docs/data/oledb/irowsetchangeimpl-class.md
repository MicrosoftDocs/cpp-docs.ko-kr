---
description: '자세히 알아보기: IRowsetChangeImpl 클래스'
title: IRowsetChangeImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: 6536b589cdf936b653d87941fb717e96ff88422c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287231"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 클래스

OLE DB 사양에서 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 인터페이스의 OLE DB 템플릿 구현입니다.

## <a name="syntax"></a>구문

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetChangeImpl` 입니다.

*스토리지*<br/>
사용자 레코드입니다.

*BaseInterface*<br/>
인터페이스에 대 한 기본 클래스 (예:) `IRowsetChange` 입니다.

*RowClass*<br/>
행 핸들의 저장소 단위입니다.

*MapClass*<br/>
공급자가 보유 한 모든 행 핸들의 저장소 단위입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods-used-with-irowsetchange"></a>인터페이스 메서드 (IRowsetChange와 함께 사용 됨)

| Name | 설명 |
|-|-|
|[DeleteRows](#deleterows)|행 집합에서 행을 삭제 합니다.|
|[InsertRow](#insertrow)|행 집합에 행을 삽입 합니다.|
|[SetData](#setdata)|하나 이상의 열에 데이터 값을 설정 합니다.|

### <a name="implementation-method-callback"></a>구현 메서드 (콜백)

| Name | 설명 |
|-|-|
|[FlushData](#flushdata)|저장소에 데이터를 커밋하기 위해 공급자에 의해 재정의 됩니다.|

## <a name="remarks"></a>설명

이 인터페이스는 데이터 저장소에 대 한 즉시 쓰기 작업을 담당 합니다. "즉시"는 최종 사용자 (소비자를 사용 하는 사용자)가 변경 하는 경우 해당 변경 내용이 데이터 저장소에 즉시 전송 되 고 실행 취소할 수 없음을 의미 합니다.

`IRowsetChangeImpl``IRowsetChange`기존 행의 열 값을 업데이트 하 고, 행을 삭제 하 고, 새 행을 삽입할 수 있도록 하는 OLE DB 인터페이스를 구현 합니다.

OLE DB 템플릿 구현은 모든 기본 메서드 ( `SetData` , `InsertRow` 및)를 지원 합니다 `DeleteRows` .

> [!IMPORTANT]
> 공급자를 구현 하기 전에 다음 문서를 참조 하는 것이 좋습니다.

- [업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)

- *OLE DB 프로그래머 참조* 의 6 장

- 또한 `RUpdateRowset` [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플에서 클래스가 어떻게 사용 되는지 확인 합니다.

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a> IRowsetChangeImpl::D eleteRows

행 집합에서 행을 삭제 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetChange::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) 를 참조 하세요.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a> IRowsetChangeImpl:: InsertRow

행 집합의 새 행을 만들고 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetChange:: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) 를 참조 하세요.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a> IRowsetChangeImpl:: SetData

하나 이상의 열에 데이터 값을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 를 참조 하세요.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a> IRowsetChangeImpl:: FlushData

저장소에 데이터를 커밋하기 위해 공급자에 의해 재정의 됩니다.

### <a name="syntax"></a>구문

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>매개 변수

*hRowToFlush*<br/>
진행 데이터 행에 대 한 핸들입니다. 이 행의 형식은 클래스의 *Rowclass* 템플릿 인수에서 결정 됩니다 `IRowsetImpl` ( `CSimpleRow` 기본적으로).

*hAccessorToFlush*<br/>
진행 바인딩 정보 및 형식 정보를 포함 하는 접근자에 대 한 핸들 `PROVIDER_MAP` 입니다 ( [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)참조).

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
