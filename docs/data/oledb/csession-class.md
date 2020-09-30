---
title: CSession 클래스
ms.date: 11/04/2016
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: f507ed432e107f586d34bb6b08fa9d3f7dc509d8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507236"
---
# <a name="csession-class"></a>CSession 클래스

단일 데이터베이스 액세스 세션을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class CSession
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[중단이](#abort)|트랜잭션을 취소 (종료) 합니다.|
|[닫기](#close)|세션을 닫습니다.|
|[커밋](#commit)|트랜잭션을 커밋합니다.|
|[GetTransactionInfo](#gettransactioninfo)|트랜잭션에 대 한 정보를 반환 합니다.|
|[열기](#open)|데이터 원본 개체에 대 한 새 세션을 엽니다.|
|[StartTransaction](#starttransaction)|이 세션에 대 한 새 트랜잭션을 시작 합니다.|

## <a name="remarks"></a>설명

하나 이상의 세션을 각 공급자 연결 (데이터 원본)에 연결할 수 있으며,이는 [Cdatasource](../../data/oledb/cdatasource-class.md) 개체가 나타냅니다. 에 대해 새을 만들려면 `CSession` `CDataSource` [Csession:: Open](#open)을 호출 합니다. 데이터베이스 트랜잭션을 시작 하려면에서 `CSession` 메서드를 제공 합니다 `StartTransaction` . 트랜잭션을 시작한 후에는 메서드를 사용 하 여 트랜잭션을 커밋하거나 `Commit` 메서드를 사용 하 여 취소할 수 있습니다 `Abort` .

## <a name="csessionabort"></a><a name="abort"></a> CSession:: Abort

트랜잭션을 종료 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="csessionclose"></a><a name="close"></a> CSession:: Close

[Csession:: Open](#open)에서 연 세션을 닫습니다.

### <a name="syntax"></a>구문

```cpp
void Close() throw();
```

### <a name="remarks"></a>설명

포인터를 해제 `m_spOpenRowset` 합니다.

## <a name="csessioncommit"></a><a name="commit"></a> CSession:: Commit

트랜잭션을 커밋합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) 을 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

자세한 내용은 [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))를 참조 하세요.

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a> CSession:: GetTransactionInfo

트랜잭션에 대 한 정보를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ITransaction:: gettransactioninfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조*에서 [ITransaction:: gettransactioninfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) 를 참조 하세요.

## <a name="csessionopen"></a><a name="open"></a> CSession:: Open

데이터 원본 개체에 대 한 새 세션을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>매개 변수

*gid*<br/>
진행 세션을 열 데이터 원본입니다.

*pPropSet*<br/>
진행 설정할 속성 및 값을 포함 하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열에 대 한 포인터입니다. Windows SDK에서 *OLE DB 프로그래머 참조* 의 [속성 집합 및 속성 그룹](/previous-versions/windows/desktop/ms713696(v=vs.85)) 을 참조 하세요.

*ulPropSets*<br/>
진행 *PPropSet* 인수에 전달 된 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

로 전달 하기 전에 [Cdatasource:: open](./cdatasource-class.md#open) 을 사용 하 여 데이터 원본 개체를 열어야 합니다 `CSession::Open` .

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a> CSession:: StartTransaction

이 세션에 대 한 새 트랜잭션을 시작 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ITransactionLocal:: starttransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) 을 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조*에서 [ITransactionLocal:: starttransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
