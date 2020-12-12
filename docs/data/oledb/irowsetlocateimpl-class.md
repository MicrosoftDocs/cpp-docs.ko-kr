---
description: '자세히 알아보기: IRowsetLocateImpl 클래스'
title: IRowsetLocateImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: 5d723fbc1ff85ce2c5b50bb5eff53ba3771751fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287062"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 클래스

행 집합에서 임의 행을 인출 하는 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) 인터페이스를 구현 합니다.

## <a name="syntax"></a>구문

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRowsetLocateImpl` 입니다.

*RowsetInterface*<br/>
에서 파생 된 클래스 `IRowsetImpl` 입니다.

*RowClass*<br/>
의 저장소 단위 `HROW` 입니다.

*MapClass*<br/>
공급자가 보유 한 모든 행 핸들의 저장소 단위입니다.

*책갈피 Keytype*<br/>
긴 또는 문자열과 같은 책갈피의 유형입니다. 일반 책갈피의 길이는 2 바이트 이상 이어야 합니다. (싱글바이트 길이는 OLE DB [표준 책갈피](/previous-versions/windows/desktop/ms712954(v=vs.85)), 및에 대해 예약 되어 `DBBMK_FIRST` `DBBMK_LAST` `DBBMK_INVALID` 있습니다.)

*책갈피 유형*<br/>
책갈피-데이터 관계를 유지 관리 하기 위한 매핑 메커니즘입니다.

*책갈피 Mapclass*<br/>
책갈피에서 보유 한 모든 행 핸들의 저장소 단위입니다.

## <a name="requirements"></a>요구 사항

**헤더**: atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| Name | 설명 |
|-|-|
|[비교](#compare)|두 책갈피를 비교 합니다.|
|[GetRowsAt](#getrowsat)|책갈피의 오프셋으로 지정 된 행부터 시작 하 여 행을 인출 합니다.|
|[GetRowsByBookmark](#getrowsbybookmark)|지정 된 책갈피와 일치 하는 행을 페치합니다.|
|[해시](#hash)|지정 된 책갈피에 대 한 해시 값을 반환 합니다.|

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|[m_rgBookmarks](#rgbookmarks)|책갈피의 배열입니다.|

## <a name="remarks"></a>설명

`IRowsetLocateImpl` 은 [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) 인터페이스의 OLE DB 템플릿 구현입니다. `IRowsetLocate` 는 행 집합에서 임의 행을 인출 하는 데 사용 됩니다. 이 인터페이스를 구현 하지 않는 행 집합은 `sequential` 행 집합입니다. 행 `IRowsetLocate` 집합에가 있는 경우 열 0은 행의 책갈피입니다 .이 열을 읽으면 동일한 행으로 위치를 변경 하는 데 사용할 수 있는 책갈피 값이 표시 됩니다.

`IRowsetLocateImpl` 는 공급자에서 책갈피 지원을 구현 하는 데 사용 됩니다. 책갈피는 소비자가 행을 신속 하 게 반환 하 여 데이터에 고속으로 액세스할 수 있도록 하는 자리 표시자 (행 집합의 인덱스)입니다. 공급자가 행을 고유 하 게 식별할 수 있는 책갈피를 결정 합니다. 메서드를 사용 하 여 `IRowsetLocateImpl` 책갈피를 비교 하 고, 오프셋을 기준으로 행을 인출 하 고, 책갈피를 기준으로 행을 인출 하 고, 책갈피에 대 한 해시

행 집합에서 책갈피 OLE DB을 지원 하려면 행 집합이이 클래스에서 상속 하도록 합니다.

책갈피 지원을 구현 하는 방법에 대 한 자세한 내용은 *Visual C++ 프로그래머 가이드* 의 [책갈피에 대 한 공급자 지원](../../data/oledb/provider-support-for-bookmarks.md) 및 Platform SDK에서 *OLE DB 프로그래머 참조* 의 [책갈피](/previous-versions/windows/desktop/ms709728(v=vs.85)) 를 참조 하세요.

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a> IRowsetLocateImpl:: Compare

두 책갈피를 비교 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

책갈피 중 하나는 표준 OLE DB 정의 [표준 책갈피](/previous-versions/windows/desktop/ms712954(v=vs.85)) ( `DBBMK_FIRST` , `DBBMK_LAST` 또는) 일 수 있습니다 `DBBMK_INVALID` . 에서 반환 되는 값은 `pComparison` 두 책갈피 간의 관계를 나타냅니다.

- DBCOMPARE_LT ( `cbBookmark1` 이 (가 `cbBookmark2` ) 이전입니다.)

- DBCOMPARE_EQ ( `cbBookmark1` 은와 같음 `cbBookmark2` )

- DBCOMPARE_GT ( `cbBookmark1` 이후 `cbBookmark2` )

- DBCOMPARE_NE (책갈피가 동일 하 고 순서가 지정 되지 않음)

- DBCOMPARE_NOTCOMPARABLE (책갈피를 비교할 수 없습니다.)

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a> IRowsetLocateImpl:: GetRowsAt

책갈피의 오프셋으로 지정 된 행부터 시작 하 여 행을 인출 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

대신 커서 위치에서 인출 하려면 [IRowset:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85))를 사용 합니다.

`IRowsetLocateImpl::GetRowsAt` 커서 위치를 변경 하지 않습니다.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a> IRowsetLocateImpl:: GetRowsByBookmark

지정 된 책갈피와 일치 하는 하나 이상의 행을 페치합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85))에 대 한 *hchapter* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조* 에서 [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

책갈피는 사용자가 정의 하는 값 또는 [표준 책갈피](/previous-versions/windows/desktop/ms712954(v=vs.85)) OLE DB (또는) 일 수 있습니다 `DBBMK_FIRST` `DBBMK_LAST` . 커서 위치를 변경 하지 않습니다.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a> IRowsetLocateImpl:: Hash

지정 된 책갈피에 대 한 해시 값을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>매개 변수

*hReserved*<br/>
진행 [IRowsetLocate:: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85))에 대 한 *hchapter* 매개 변수에 해당 합니다.

다른 매개 변수는 *OLE DB 프로그래머 참조* 에서 [IRowsetLocate:: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) 를 참조 하세요.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a> IRowsetLocateImpl:: m_rgBookmarks

책갈피의 배열입니다.

### <a name="syntax"></a>구문

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate: IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85)) 
 [책갈피에 대 한 공급자 지원](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[책갈피](/previous-versions/windows/desktop/ms709728(v=vs.85))
