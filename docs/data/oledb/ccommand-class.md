---
description: '자세히 알아보기: CCommand 클래스'
title: CCommand 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 150d543b666896964794503d185637680e6da8fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335511"
---
# <a name="ccommand-class"></a>CCommand 클래스

명령을 설정 하 고 실행 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>매개 변수

*TAccessor*<br/>
명령에서 사용할 접근자 클래스의 형식 (예: `CDynamicParameterAccessor` , `CDynamicStringAccessor` 또는 `CEnumeratorAccessor` )입니다. 기본값은 `CNoAccessor` 클래스가 매개 변수 또는 출력 열을 지원 하지 않도록 지정 하는입니다.

*TRowset*<br/>
`CArrayRowset`명령에서 사용 하려는 행 집합 클래스의 유형 (예: 또는 `CNoRowset` )입니다. 기본값은 `CRowset`입니다.

*TMultiple*<br/>
여러 결과를 반환할 수 있는 OLE DB 명령을 사용 하려면 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)를 지정 합니다. 그렇지 않으면 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)를 사용 합니다. 자세한 내용은 [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85))를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[닫기](#close)|현재 명령을 닫습니다.|
|[GetNextResult](#getnextresult)|여러 결과 집합을 사용 하는 경우 다음 결과를 페치합니다.|
|[열기](#open)|를 실행 하 고 선택적으로 명령을 바인딩합니다.|

### <a name="inherited-methods"></a>상속된 메서드

| Name | Description |
|-|-|
|[만들기](#create)|지정 된 세션에 대 한 새 명령을 만든 다음 명령 텍스트를 설정 합니다.|
|[CreateCommand](#createcommand)|새 명령을 만듭니다.|
|[GetParameterInfo](#getparameterinfo)|명령의 매개 변수, 이름 및 형식에 대 한 목록을 가져옵니다.|
|[준비](#prepare)|현재 명령의 유효성을 검사 하 고 최적화 합니다.|
|[ReleaseCommand](#releasecommand)|필요한 경우 매개 변수 접근자를 해제 한 다음 명령을 해제 합니다.|
|[SetParameterInfo](#setparameterinfo)|각 명령 매개 변수의 네이티브 형식을 지정 합니다.|
|[Unprepare](#unprepare)|현재 명령 실행 계획을 삭제 합니다.|

## <a name="remarks"></a>설명

매개 변수 기반 작업을 수행 하거나 명령을 실행 해야 하는 경우이 클래스를 사용 합니다. 단순히 단순 행 집합을 열어야 하는 경우에는 [CTable](../../data/oledb/ctable-class.md) 를 대신 사용 합니다.

사용 중인 접근자 클래스는 매개 변수 및 데이터를 바인딩하는 방법을 결정 합니다.

저장 OLE DB 프로시저는 Jet의 경우에는 저장 프로시저를 지원 하지 않으므로 해당 공급자는 저장 프로시저를 사용할 수 없습니다. 쿼리 문자열에는 상수만 사용할 수 있습니다.

## <a name="ccommandclose"></a><a name="close"></a> CCommand:: Close

명령과 연결 된 접근자 행 집합을 해제 합니다.

### <a name="syntax"></a>구문

```cpp
void Close();
```

### <a name="remarks"></a>설명

명령은 행 집합, 결과 집합 접근자 및 (선택 사항) 매개 변수 접근자를 사용 합니다. 테이블은 매개 변수를 지원 하지 않으며 매개 변수 접근자가 필요 하지 않습니다.

명령을 실행 하는 경우 `Close` 명령 후와 [ReleaseCommand](#releasecommand) 를 모두 호출 해야 합니다.

동일한 명령을 반복적으로 실행 하려면를 호출 하기 전에를 호출 하 여 각 결과 집합 접근자를 해제 해야 `Close` `Execute` 합니다. 시리즈의 끝에서를 호출 하 여 매개 변수 접근자를 해제 해야 합니다 `ReleaseCommand` . 또 다른 일반적인 시나리오는 출력 매개 변수가 있는 저장 프로시저를 호출 하는 것입니다. 많은 공급자 (예: SQL Server에 대 한 OLE DB 공급자)에서는 결과 집합 접근자를 닫을 때까지 출력 매개 변수 값에 액세스할 수 없습니다. `Close`를 호출 하 여 반환 된 행 집합 및 결과 집합 접근자를 닫을 수 있지만 매개 변수 접근자는 닫지 않으므로 출력 매개 변수 값을 검색할 수 있습니다.

### <a name="example"></a>예제

다음 예제에서는 동일한 명령을 반복해서 실행할 때 `Close` 및 `ReleaseCommand`을 호출할 수 있는 방법을 보여 줍니다.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a> CCommand:: GetNextResult

사용할 수 있는 경우 다음 결과 집합을 페치합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>매개 변수

*pulRowsAffected*<br/>
[in/out] 명령의 영향을 받는 행 수가 반환 되는 메모리에 대 한 포인터입니다.

*bBind*<br/>
진행 명령을 실행 한 후 자동으로 바인딩할 지 여부를 지정 합니다. 기본값은 이며 **`true`** ,이로 인해 명령이 자동으로 바인딩됩니다. *Bbind* 를로 설정 하면 **`false`** 수동으로 바인딩할 수 있도록 명령의 자동 바인딩이 방지 됩니다. (수동 바인딩은 OLAP 사용자에 게 특히 관심이 있습니다.)

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이전에 결과 집합을 인출 한 경우이 함수는 이전 결과 집합을 해제 하 고 열을 바인딩 해제 합니다. *Bbind* 가 인 경우 **`true`** 새 열을 바인딩합니다.

`CCommand`템플릿 매개 변수 *tmultiple* 을 설정 하 여 여러 결과를 지정한 경우에만이 함수를 호출 해야 합니다 = `CMultipleResults` .

## <a name="ccommandopen"></a><a name="open"></a> CCommand:: Open

를 실행 하 고 선택적으로 명령을 바인딩합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
진행 명령을 실행할 세션입니다.

*wszCommand*<br/>
진행 유니코드 문자열로 전달 되는 실행할 명령입니다. 를 사용 하는 경우 NULL 일 수 있습니다 `CAccessor` .이 경우 [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) 매크로에 전달 된 값에서 명령이 검색 됩니다. 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 를 참조 하세요.

*szCommand*<br/>
진행 이 매개 변수가 ANSI 명령 문자열을 사용 한다는 점을 제외 하 고 *wszCommand* 와 동일 합니다. 이 메서드의 네 번째 형태는 NULL 값을 사용할 수 있습니다. 자세한 내용은이 항목의 뒷부분에 나오는 "주의"를 참조 하십시오.

*pPropSet*<br/>
진행 설정할 속성 및 값을 포함 하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열에 대 한 포인터입니다. Windows SDK에서 *OLE DB 프로그래머 참조* 의 [속성 집합 및 속성 그룹](/previous-versions/windows/desktop/ms713696(v=vs.85)) 을 참조 하세요.

*영향을 받는 prows*<br/>
[in/out] 명령의 영향을 받는 행 수가 반환 되는 메모리에 대 한 포인터입니다. *\* 영향을 받는 PROWSAFFECTED* 가 NULL 이면 행 개수가 반환 되지 않습니다. 그렇지 않으면 `Open` 다음 조건에 따라 적용 되는 *\* prowsaffected* 을 설정 합니다.

|조건|결과|
|--------|----------|
|`cParamSets`의 요소가 `pParams` 1 보다 큽니다.|*\* 영향 받는 영향을 받는* 모든 매개 변수 집합의 영향을 받는 행의 총 수를 나타냅니다.|
|영향을 받는 행 수를 사용할 수 없습니다.|*\* 영향을 받는 prowsaffected* -1로 설정 됩니다.|
|이 명령은 행을 업데이트, 삭제 또는 삽입 하지 않습니다.|*\* 영향을 받는 prowsaffected* 정의 되지 않습니다.|

*guidCommand*<br/>
진행 명령 텍스트를 구문 분석 하는 데 사용할 공급자의 구문과 일반 규칙을 지정 하는 GUID입니다. 자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ICommandText:: Getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) 및 [ICommandText:: setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85)) 를 참조 하세요.

*bBind*<br/>
진행 명령을 실행 한 후 자동으로 바인딩할 지 여부를 지정 합니다. 기본값은 이며 **`true`** ,이로 인해 명령이 자동으로 바인딩됩니다. *Bbind* 를로 설정 하면 **`false`** 수동으로 바인딩할 수 있도록 명령의 자동 바인딩이 방지 됩니다. (수동 바인딩은 OLAP 사용자에 게 특히 관심이 있습니다.)

*ulPropSets*<br/>
진행 *PPropSet* 인수에 전달 된 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

의 처음 세 가지 형태는 세션을 사용 하 고, `Open` 명령을 만들고, 필요에 따라 매개 변수를 바인딩하는 명령을 실행 하는 것입니다.

의 첫 번째 형태는 `Open` 유니코드 명령 문자열을 사용 하며 기본값은 없습니다.

의 두 번째 형식은 `Open` ansi 명령 문자열을 사용 하 고 기본값은 사용 하지 않습니다 (기존 ANSI 응용 프로그램과의 호환성을 위해 제공 됨).

의 세 번째 형식은 `Open` 형식 때문에 명령 문자열이 null이 될 수 있도록 합니다 **`int`** . 기본값은 null입니다. `Open(session, NULL);` `Open(session);` NULL은 형식 이므로 또는를 호출 하기 위해 제공 됩니다 **`int`** . 이 버전에는 매개 변수가 NULL 임을 어설션하는 및가 필요 **`int`** 합니다.

`Open`명령을 이미 만들었고 단일 [준비](#prepare) 및 다중 실행을 수행 하려는 경우의 네 번째 형태를 사용 합니다.

> [!NOTE]
> `Open``Execute`는를 호출 하 여을 호출 `GetNextResult` 합니다.

## <a name="ccommandcreate"></a><a name="create"></a> CCommand:: Create

[CCommand:: CreateCommand](#createcommand) 를 호출 하 여 지정 된 세션에 대 한 명령을 만든 다음 [ICommandText:: setcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) 를 호출 하 여 명령 텍스트를 지정 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
진행 명령을 만들 세션입니다.

*wszCommand*<br/>
진행 명령 문자열의 유니코드 텍스트에 대 한 포인터입니다.

*szCommand*<br/>
진행 명령 문자열의 ANSI 텍스트에 대 한 포인터입니다.

*guidCommand*<br/>
진행 명령 텍스트를 구문 분석 하는 데 사용할 공급자의 구문과 일반 규칙을 지정 하는 GUID입니다. 언어에 대 한 설명은 *OLE DB 프로그래머 참조* 에서 [ICommandText:: getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

의 첫 번째 형태는 `Create` 유니코드 명령 문자열을 사용 합니다. 의 두 번째 형태는 `Create` ansi 명령 문자열 (기존 ansi 응용 프로그램과의 호환성을 위해 제공 됨)을 사용 합니다.

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a> CCommand:: CreateCommand

새 명령을 만듭니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
진행 `CSession` 새 명령과 연결 될 개체입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 세션 개체를 사용 하 여 명령을 만듭니다.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a> CCommand:: GetParameterInfo

명령의 매개 변수, 이름 및 형식에 대 한 목록을 가져옵니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="ccommandprepare"></a><a name="prepare"></a> CCommand::P repare

현재 명령의 유효성을 검사 하 고 최적화 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>매개 변수

*cExpectedRuns*<br/>
진행 명령을 실행 해야 하는 횟수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 OLE DB 메서드 [ICommandPrepare::P repare](/previous-versions/windows/desktop/ms718370(v=vs.85))를 래핑합니다.

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a> CCommand:: ReleaseCommand

매개 변수 접근자를 해제 한 다음 명령 자체를 해제 합니다.

### <a name="syntax"></a>구문

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>설명

`ReleaseCommand` 는와 함께 사용 됩니다 `Close` . 사용법 정보는 [닫기](#close) 를 참조 하세요.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a> CCommand:: SetParameterInfo

각 명령 매개 변수의 네이티브 형식을 지정 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="ccommandunprepare"></a><a name="unprepare"></a> CCommand:: Unprepare

현재 명령 실행 계획을 삭제 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Return Value

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 OLE DB 메서드 [ICommandPrepare:: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))를 래핑합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
