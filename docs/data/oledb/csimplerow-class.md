---
description: '자세히 알아보기: CSimpleRow 클래스'
title: CSimpleRow 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: 7390a8d82e8996c81761065541eebbbccae510ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268420"
---
# <a name="csimplerow-class"></a>CSimpleRow 클래스

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md) 클래스에서 사용 되는 행 핸들의 기본 구현을 제공 합니다.

## <a name="syntax"></a>Syntax

```cpp
class CSimpleRow
```

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddRefRow](#addrefrow)|기존 행 핸들에 참조 횟수를 추가합니다.|
|[비교](#compare)|두 행을 비교 하 여 동일한 행 인스턴스를 참조 하는지 확인 합니다.|
|[CSimpleRow](#csimplerow)|생성자입니다.|
|[ReleaseRow](#releaserow)|행을 해제합니다.|

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|[m_dwRef](#dwref)|기존 행 핸들에 대 한 참조 수입니다.|
|[m_iRowset](#irowset)|커서를 나타내는 행 집합에 대 한 인덱스입니다.|

## <a name="remarks"></a>설명

행 핸들은 논리적으로 결과 행에 대 한 고유 태그입니다. `IRowsetImpl``CSimpleRow` [IRowsetImpl:: GetNextRows](./irowsetimpl-class.md#getnextrows)에서 요청 된 모든 행에 대해 새를 만듭니다. `CSimpleRow` 는의 기본 템플릿 인수 이므로를 행 핸들의 고유한 구현으로 바꿀 수도 있습니다 `IRowsetImpl` . 이 클래스를 바꾸기 위한 유일한 요구 사항은 대체 클래스가 **LONG** 형식의 단일 매개 변수를 허용 하는 생성자를 제공 하는 것입니다.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a> CSimpleRow:: AddRefRow

스레드로부터 안전한 방식으로 기존 행 핸들에 참조 횟수를 추가 합니다.

### <a name="syntax"></a>Syntax

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a> CSimpleRow:: Compare

두 행을 비교 하 여 동일한 행 인스턴스를 참조 하는지 확인 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>매개 변수

*pRow*<br/>
`CSimpleRow` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

HRESULT 값입니다. 일반적으로 두 행이 동일한 행 인스턴스인지, 아니면 두 행이 다른 지를 나타내는 S_FALSE S_OK. 가능한 다른 반환 값에 대 한 *OLE DB 프로그래머 참조* 에서 [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 를 참조 하세요.

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a> CSimpleRow:: CSimpleRow

생성자입니다.

### <a name="syntax"></a>구문

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>매개 변수

*iRowsetCur*<br/>
진행 현재 행 집합에 대 한 인덱스입니다.

### <a name="remarks"></a>설명

[M_iRowset](#irowset) 를 *iRowsetCur* 로 설정 합니다.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a> CSimpleRow:: ReleaseRow

스레드로부터 안전한 방식으로 행을 해제 합니다.

### <a name="syntax"></a>Syntax

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a> CSimpleRow:: m_dwRef

기존 행 핸들에 대 한 참조 수입니다.

### <a name="syntax"></a>Syntax

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a> CSimpleRow:: m_iRowset

커서를 나타내는 행 집합에 대 한 인덱스입니다.

### <a name="syntax"></a>구문

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl 클래스](../../data/oledb/irowsetimpl-class.md)
