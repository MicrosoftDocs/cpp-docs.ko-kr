---
description: '자세히 알아보기: CAccessorRowset 클래스'
title: CAccessorRowset 클래스
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: c93580fa41967004947b075e82e00bdcb745ad4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307576"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 클래스

단일 클래스에서 행 집합 및 관련 접근자를 캡슐화 합니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>매개 변수

*TAccessor*<br/>
접근자 클래스입니다.

*TRowset*<br/>
행 집합 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|--|--|
| [바인딩하며](#bind) | 바인딩을 만듭니다 ( `bBind` **`false`** [CCommand:: Open](./ccommand-class.md#open)에서로 지정 된 경우에 사용 됨). |
| [CAccessorRowset](#caccessorrowset) | 생성자입니다. |
| [닫기](#close) | 행 집합 및 접근자를 닫습니다. |
| [FreeRecordMemory](#freerecordmemory) | 현재 레코드에서 해제 해야 하는 모든 열을 해제 합니다. |
| [GetColumnInfo](#getcolumninfo) | [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))를 구현 합니다. |

## <a name="remarks"></a>설명

클래스 `TAccessor` 는 접근자를 관리 합니다. 클래스 *trowset* 은 행 집합을 관리 합니다.

## <a name="caccessorrowsetbind"></a><a name="bind"></a> CAccessorRowset:: Bind

`bBind` **`false`** [CCommand:: Open](./ccommand-class.md#open)에서로 지정한 경우 바인딩을 만듭니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a> CAccessorRowset:: CAccessorRowset

초기화는 `CAccessorRowset` 개체입니다.

### <a name="syntax"></a>Syntax

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a> CAccessorRowset:: Close

모든 활성 접근자와 행 집합을 해제 합니다.

### <a name="syntax"></a>구문

```cpp
void Close();
```

### <a name="remarks"></a>설명

연결 된 모든 메모리를 해제 합니다.

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a> CAccessorRowset:: FreeRecordMemory

현재 레코드에서 해제 해야 하는 모든 열을 해제 합니다.

### <a name="syntax"></a>Syntax

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a> CAccessorRowset:: GetColumnInfo

열린 행 집합에서 열 정보를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

사용자는 반환 된 열 정보와 문자열 버퍼를 해제 해야 합니다. [Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 를 사용 하 고 바인딩을 재정의 해야 하는 경우이 메서드의 두 번째 버전을 사용 합니다.

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
