---
description: '자세히 알아보기: CBulkRowset 클래스'
title: CBulkRowset 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: 106a8ffb3d70a021adbdb03b426e53ca39285b02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198377"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 클래스

단일 호출로 여러 행 핸들을 검색 하 여 대량으로 데이터 작업을 수행 하기 위해 행을 페치 및 조작 합니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>매개 변수

*TAccessor*<br/>
접근자 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddRefRows](#addrefrows)|참조 횟수를 증가 시킵니다.|
|[CBulkRowset](#cbulkrowset)|생성자입니다.|
|[MoveFirst](#movefirst)|데이터의 첫 번째 행을 검색 하 고, 필요한 경우 새 대량 페치를 수행 합니다.|
|[MoveLast](#movelast)|마지막 행으로 이동 합니다.|
|[MoveNext](#movenext)|데이터의 다음 행을 검색 합니다.|
|[MovePrev](#moveprev)|이전 행으로 이동 합니다.|
|[MoveToBookmark](#movetobookmark)|책갈피로 표시 된 행 또는 해당 책갈피의 지정 된 오프셋에 있는 행을 인출 합니다.|
|[MoveToRatio](#movetoratio)|행 집합의 소수 위치에서 시작 하 여 행을 인출 합니다.|
|[ReleaseRows](#releaserows)|현재 행 ( `m_nCurrentRow` )을 0으로 설정 하 고 모든 행을 해제 합니다.|
|[SetRows](#setrows)|한 번의 호출로 검색할 행 핸들의 수를 설정 합니다.|

## <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법을 보여 줍니다 `CBulkRowset` .

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a> C대량 행 집합:: AddRefRows

[IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 를 호출 하 여 대량 행 집합에서 현재 검색 된 모든 행에 대 한 참조 횟수를 늘립니다.

### <a name="syntax"></a>구문

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a> C대량 행 집합:: C대량 행 집합

새 개체를 만들고 `CBulkRowset` 기본 행 수를 10으로 설정 합니다.

### <a name="syntax"></a>Syntax

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a> C대량 행 집합:: MoveFirst

데이터의 첫 번째 행을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a> C대량 행 집합:: MoveLast

마지막 행으로 이동 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a> C대량 행 집합:: MoveNext

데이터의 다음 행을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다. 행 집합의 끝에 도달 하면 DB_S_ENDOFROWSET 반환 됩니다.

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a> C대량 행 집합:: MovePrev

이전 행으로 이동 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a> C대량 행 집합:: MoveToBookmark

책갈피 또는 해당 책갈피에서 지정 된 오프셋 (*Lskip*)의 행으로 표시 된 행을 인출 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>매개 변수

*bookmark*<br/>
진행 데이터를 가져올 위치를 표시 하는 책갈피입니다.

*lSkip*<br/>
진행 책갈피에서 대상 행 까지의 행 개수입니다. *Lskip* 이 0 이면 인출 된 첫 번째 행이 책갈피가 설정 된 행입니다. *Lskip* 이 1 이면 인출 된 첫 번째 행이 책갈피가 설정 된 행 뒤의 행입니다. *Lskip* 이-1 이면 인출 된 첫 번째 행이 책갈피가 설정 된 행 앞의 행입니다.

### <a name="return-value"></a>반환 값

*OLE DB 프로그래머 참조* 에서 [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) 를 참조 하세요.

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a> C대량 행 집합:: MoveToRatio

행 집합의 소수 위치에서 시작 하 여 행을 인출 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>매개 변수

*nNumerator*<br/>
진행 데이터를 페치할 소수 자릿수를 결정 하는 데 사용 되는 분자입니다.

*nDenominator*<br/>
진행 데이터를 페치할 소수 자릿수를 결정 하는 데 사용 되는 분모입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

`MoveToRatio` 는 다음 수식에 따라 대략적으로 행을 인출 합니다.

`(nNumerator *  RowsetSize ) / nDenominator`

여기서 `RowsetSize` 는 행 단위로 측정 되는 행 집합의 크기입니다. 이 수식의 정확도는 특정 공급자에 따라 달라 집니다. 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) 를 참조 하세요.

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a> C대량 행 집합:: ReleaseRows

는 [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) 를 호출 하 여 대량 행 집합에서 현재 검색 된 모든 행에 대 한 참조 횟수를 감소 시킵니다.

### <a name="syntax"></a>구문

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a> C대량 행 집합:: SetRows

각 호출에 의해 검색 되는 행 핸들의 수를 설정 합니다.

### <a name="syntax"></a>구문

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>매개 변수

*nRows*<br/>
진행 행 집합의 새 크기 (행 수)입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하는 경우 행 집합이 열리기 전에 있어야 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
