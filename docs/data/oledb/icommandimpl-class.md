---
title: ICommandImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: 2f2d3938d63e5e67fc501d52d269c06f6b144ac8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501833"
---
# <a name="icommandimpl-class"></a>ICommandImpl 클래스

[ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) 인터페이스에 대 한 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `ICommandImpl` 입니다.

*CommandBase*<br/>
명령 인터페이스입니다. 기본값은 `ICommand`입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[취소](#cancel)|현재 명령 실행을 취소 합니다.|
|[CancelExecution](#cancelexecution)|현재 명령 실행을 취소 합니다.|
|[CreateRowset](#createrowset)|행 집합 개체를 만듭니다.|
|[실행](#execute)|명령을 실행합니다.|
|[GetDBSession](#getdbsession)|명령을 만든 세션에 대 한 인터페이스 포인터를 반환 합니다.|
|[ICommandImpl](#icommandimpl)|생성자입니다.|

### <a name="data-members"></a>데이터 멤버

| 속성 | 설명 |
|-|-|
|[m_bCancel](#bcancel)|명령을 취소할지 여부를 나타냅니다.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|명령을 실행할 때 취소할 것인지 여부를 나타냅니다.|
|[m_bIsExecuting](#bisexecuting)|명령이 현재 실행 중인지 여부를 나타냅니다.|

## <a name="remarks"></a>설명

Command 개체의 필수 인터페이스입니다.

## <a name="icommandimplcancel"></a><a name="cancel"></a> ICommandImpl:: Cancel

현재 명령 실행을 취소 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>설명

*OLE DB 프로그래머 참조*에서 [ICommand:: Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) 을 참조 하세요.

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a> ICommandImpl:: CancelExecution

현재 명령 실행을 취소 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a> ICommandImpl:: CreateRowset

단일 행 집합을 만들기 위해 [Execute](#execute) 에 의해 호출 됩니다.

### <a name="syntax"></a>구문

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>매개 변수

*RowsetClass*<br/>
사용자의 행 집합 클래스를 나타내는 템플릿 클래스 멤버입니다. 일반적으로 마법사를 통해 생성 됩니다.

*pUnkOuter*<br/>
진행 `IUnknown` 행 집합이 집계의 일부로 생성 되는 경우 제어 인터페이스에 대 한 포인터이 고, 그렇지 않으면 null입니다.

*riid*<br/>
진행 의 *riid* 에 해당 `ICommand::Execute` 합니다.

*pParams*<br/>
[in/out] 의 *Pparams* 에 해당 `ICommand::Execute` 합니다.

*pcRowsAffected*<br/>
의 *pcRowsAffected* 에 해당 `ICommand::Execute` 합니다.

*ppRowset*<br/>
[in/out] 의 *ppRowset* 에 해당 `ICommand::Execute` 합니다.

*pRowsetObj*<br/>
제한이 행 집합 개체에 대 한 포인터입니다. 일반적으로이 매개 변수는 사용 되지 않지만, COM 개체로 전달 하기 전에 행 집합에서 더 많은 작업을 수행 해야 하는 경우에 사용할 수 있습니다. *PRowsetObj* 의 수명은 *ppRowset*에 의해 바인딩됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다. `ICommand::Execute`일반적인 값 목록은를 참조 하세요.

### <a name="remarks"></a>설명

둘 이상의 행 집합을 만들거나 다른 행 집합을 만들기 위한 고유한 조건을 제공 하려면 내에서에 대 한 다른 호출을 수행 `CreateRowset` `Execute` 합니다.

*OLE DB 프로그래머 참조* 에서 [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 를 참조 하세요.

## <a name="icommandimplexecute"></a><a name="execute"></a> ICommandImpl:: Execute

명령을 실행합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

요청 된 송신 인터페이스는이 함수가 만드는 행 집합 개체에서 가져온 인터페이스입니다.

`Execute`[CreateRowset](#createrowset)를 호출 합니다. 기본 구현을 재정의 하 여 두 개 이상의 행 집합을 만들거나 다른 행 집합을 만들기 위한 고유한 조건을 제공 합니다.

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a> ICommandImpl:: GetDBSession

명령을 만든 세션에 대 한 인터페이스 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ICommand:: getdbsession](/previous-versions/windows/desktop/ms719622(v=vs.85)) 을 참조 하세요.

### <a name="remarks"></a>설명

세션에서 속성을 검색 하는 데 유용 합니다.

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a> ICommandImpl:: ICommandImpl

생성자입니다.

### <a name="syntax"></a>구문

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a> ICommandImpl:: m_bCancel

명령이 취소 되었는지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>설명

`Execute`명령 클래스의 메서드에서이 변수를 검색 하 고 적절 하 게 취소할 수 있습니다.

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a> ICommandImpl:: m_bCancelWhenExecuting

실행할 때 명령을 취소할 수 있는지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>설명

기본값은 **`true`** (취소 가능)입니다.

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a> ICommandImpl:: m_bIsExecuting

명령이 현재 실행 중인지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>설명

`Execute`명령 클래스의 메서드는이 변수를로 설정할 수 있습니다 **`true`** .

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
