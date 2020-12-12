---
description: '자세히 알아보기: IOpenRowsetImpl 클래스'
title: IOpenRowsetImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 4ec7f8ebdab132854172f7e5f4dff7387e46717f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317430"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 클래스

인터페이스에 대 한 구현을 제공 `IOpenRowset` 합니다.

## <a name="syntax"></a>구문

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>매개 변수

*SessionClass*<br/>
에서 파생 된 클래스 `IOpenRowsetImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[CreateRowset](#createrowset)|행 집합 개체를 만듭니다. 사용자가 직접 호출 하지 않습니다.|
|[OpenRowset](#openrowset)|단일 기본 테이블이 나 인덱스의 모든 행을 포함 하는 행 집합을 열고 반환 합니다. (ATLDB.H에 없습니다. 넣기|

## <a name="remarks"></a>설명

[Iopenrowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) 인터페이스는 session 개체에 대해 필수입니다. 단일 기본 테이블이 나 인덱스의 모든 행을 포함 하는 행 집합을 열고 반환 합니다.

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a> IOpenRowsetImpl:: CreateRowset

행 집합 개체를 만듭니다. 사용자가 직접 호출 하지 않습니다. *OLE DB 프로그래머 참조* 에서 [Iopenrowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 을 참조 하세요.

### <a name="syntax"></a>구문

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>매개 변수

*RowsetClass*<br/>
사용자의 행 집합 클래스를 나타내는 템플릿 클래스 멤버입니다. 일반적으로 마법사를 통해 생성 됩니다.

*pRowsetObj*<br/>
제한이 행 집합 개체에 대 한 포인터입니다. 일반적으로이 매개 변수는 사용 되지 않지만, COM 개체로 전달 하기 전에 행 집합에서 더 많은 작업을 수행 해야 하는 경우에 사용할 수 있습니다. *PRowsetObj* 의 수명은 *ppRowset* 에 의해 바인딩됩니다.

다른 매개 변수는 *OLE DB 프로그래머 참조* 에서 [Iopenrowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 을 참조 하세요.

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a> IOpenRowsetImpl:: OpenRowset

단일 기본 테이블이 나 인덱스의 모든 행을 포함 하는 행 집합을 열고 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [Iopenrowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 을 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 ATLDB.H에서 찾을 수 없습니다. 공급자를 만들 때 ATL 개체 마법사에 의해 만들어집니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
