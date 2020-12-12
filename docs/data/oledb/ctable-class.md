---
description: '다음에 대 한 자세한 정보: CTable 클래스'
title: CTable 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 62808080a68bbd5de00b39c43661e06617ba53f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317729"
---
# <a name="ctable-class"></a>CTable 클래스

단순 행 집합 (매개 변수 없음)에 직접 액세스 하는 방법을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
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
|-|-|
|[열기](#open)|테이블을 엽니다.|

## <a name="remarks"></a>설명

명령을 실행 하 여 행 집합에 액세스 하는 방법에 대 한 자세한 내용은 [CCommand](../../data/oledb/ccommand-class.md) 를 참조 하세요.

## <a name="ctableopen"></a><a name="open"></a> CTable:: Open

테이블을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
진행 테이블이 열려 있는 세션입니다.

*wszTableName*<br/>
진행 유니코드 문자열로 전달 되는 열 테이블의 이름입니다.

*szTableName*<br/>
진행 ANSI 문자열로 전달 되는 열 테이블의 이름입니다.

*dbid*<br/>
진행 `DBID` 열 테이블의입니다.

*pPropSet*<br/>
진행 설정할 속성 및 값을 포함 하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열에 대 한 포인터입니다. Windows SDK에서 *OLE DB 프로그래머 참조* 의 [속성 집합 및 속성 그룹](/previous-versions/windows/desktop/ms713696(v=vs.85)) 을 참조 하세요. NULL의 기본값은 속성을 지정 하지 않습니다.

*ulPropSets*<br/>
진행 *PPropSet* 인수에 전달 된 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [Iopenrowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
