---
description: '자세한 정보: AsyncBase 클래스'
title: AsyncBase 클래스
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 2e09e9ecb3a9b1ebf466989edd09cba747782028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175835"
---
# <a name="asyncbase-class"></a>AsyncBase 클래스

Windows 런타임 비동기 상태 컴퓨터를 구현합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>매개 변수

*TComplete*<br/>
비동기 작업이 완료 될 때 호출 되는 이벤트 처리기입니다.

*TProgress*<br/>
실행 중인 비동기 작업에서 작업의 현재 진행률을 보고할 때 호출 되는 이벤트 처리기입니다.

*resultType*<br/>
[Asyncresulttype](asyncresulttype-enumeration.md) 열거형 값 중 하나입니다. 기본적으로 `SingleResult`입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                               | 설명
---------------------------------- | -------------------------------------------------
[AsyncBase:: AsyncBase](#asyncbase) | `AsyncBase` 클래스의 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                         | 설명
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase:: Cancel](#cancel)                 | 비동기 작업을 취소 합니다.
[AsyncBase:: Close](#close)                   | 비동기 작업을 닫습니다.
[AsyncBase:: FireCompletion](#firecompletion) | 완료 이벤트 처리기를 호출 하거나 내부 진행률 대리자를 다시 설정 합니다.
[AsyncBase:: FireProgress](#fireprogress)     | 현재 진행률 이벤트 처리기를 호출 합니다.
[AsyncBase:: get_ErrorCode](#get-errorcode)   | 현재 비동기 작업에 대 한 오류 코드를 검색 합니다.
[AsyncBase:: get_Id](#get-id)                 | 비동기 작업의 핸들을 검색 합니다.
[AsyncBase:: get_Status](#get-status)         | 비동기 작업의 상태를 나타내는 값을 검색 합니다.
[AsyncBase:: GetOnComplete](#getoncomplete)   | 현재 완료 이벤트 처리기의 주소를 지정 된 변수에 복사 합니다.
[AsyncBase:: GetOnProgress](#getonprogress)   | 현재 진행률 이벤트 처리기의 주소를 지정 된 변수에 복사 합니다.
[AsyncBase::p ut_Id](#put-id)                 | 비동기 작업의 핸들을 설정 합니다.
[AsyncBase::P utOnComplete](#putoncomplete)   | 완료 이벤트 처리기의 주소를 지정 된 값으로 설정 합니다.
[AsyncBase::P utOnProgress](#putonprogress)   | 진행률 이벤트 처리기의 주소를 지정 된 값으로 설정 합니다.

### <a name="protected-methods"></a>Protected 메서드

Name                                                                         | 설명
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase:: CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | 현재 비동기 상태에서 대리자 속성을 수정할 수 있는지 여부를 테스트 합니다.
[AsyncBase:: CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | 비동기 작업의 결과를 현재 비동기 상태로 수집할 수 있는지 여부를 테스트 합니다.
[AsyncBase:: ContinueAsyncOperation](#continueasyncoperation)                 | 비동기 작업을 계속 처리 해야 하는지 아니면 중단 해야 하는지 결정 합니다.
[AsyncBase:: CurrentStatus](#currentstatus)                                   | 현재 비동기 작업의 상태를 검색 합니다.
[AsyncBase:: ErrorCode](#errorcode)                                           | 현재 비동기 작업에 대 한 오류 코드를 검색 합니다.
[AsyncBase:: OnCancel](#oncancel)                                             | 파생 클래스에서 재정의 되는 경우 비동기 작업을 취소 합니다.
[AsyncBase:: OnClose](#onclose)                                               | 파생 클래스에서 재정의 되는 경우 비동기 작업을 닫습니다.
[AsyncBase:: OnStart](#onstart)                                               | 파생 클래스에서 재정의 되는 경우 비동기 작업을 시작 합니다.
[AsyncBase:: Start](#start)                                                   | 비동기 작업을 시작 합니다.
[AsyncBase:: TryTransitionToCompleted](#trytransitiontocompleted)             | 현재 비동기 작업이 완료 되었는지 여부를 나타냅니다.
[AsyncBase:: TryTransitionToError](#trytransitiontoerror)                     | 지정 된 오류 코드가 내부 오류 상태를 수정할 수 있는지 여부를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>요구 사항

**헤더:** async. h

**네임스페이스:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a> AsyncBase:: AsyncBase

`AsyncBase` 클래스의 인스턴스를 초기화합니다.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a> AsyncBase:: Cancel

비동기 작업을 취소 합니다.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>반환 값

기본적으로는 항상 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

`Cancel()` 는의 기본 구현 `IAsyncInfo::Cancel` 이며 실제 작업은 수행 하지 않습니다. 실제로 비동기 작업을 취소 하려면 `OnCancel()` 순수 가상 메서드를 재정의 합니다.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a> AsyncBase:: CheckValidStateForDelegateCall

현재 비동기 상태에서 대리자 속성을 수정할 수 있는지 여부를 테스트 합니다.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>반환 값

대리자 속성을 수정할 수 있는지 여부를 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a> AsyncBase:: CheckValidStateForResultsCall

비동기 작업의 결과를 현재 비동기 상태로 수집할 수 있는지 여부를 테스트 합니다.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>반환 값

결과를 수집할 수 있는지 여부를 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbaseclose"></a><a name="close"></a> AsyncBase:: Close

비동기 작업을 닫습니다.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>반환 값

작업이 닫히거나 이미 닫혀 있으면를 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_STATE_CHANGE 합니다.

### <a name="remarks"></a>설명

`Close()` 는의 기본 구현 `IAsyncInfo::Close` 이며 실제 작업은 수행 하지 않습니다. 실제로 비동기 작업을 닫으려면 `OnClose()` 순수 가상 메서드를 재정의 합니다.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a> AsyncBase:: ContinueAsyncOperation

비동기 작업을 계속 처리 해야 하는지 아니면 중단 해야 하는지 결정 합니다.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>반환 값

**`true`** 비동기 작업의 현재 상태가 *시작* 됨 인 경우이는 작업을 계속 해야 함을 의미 합니다. 그렇지 않으면 **`false`** 작업이 중단 되어야 함을 의미 하는입니다.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a> AsyncBase:: CurrentStatus

현재 비동기 작업의 상태를 검색 합니다.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>매개 변수

*status*<br/>
이 작업이 현재 상태를 저장 하는 위치입니다.

### <a name="remarks"></a>설명

이 작업은 스레드로부터 안전 합니다.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a> AsyncBase:: ErrorCode

현재 비동기 작업에 대 한 오류 코드를 검색 합니다.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>매개 변수

*error*<br/>
이 작업이 현재 오류 코드를 저장 하는 위치입니다.

### <a name="remarks"></a>설명

이 작업은 스레드로부터 안전 합니다.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a> AsyncBase:: FireCompletion

완료 이벤트 처리기를 호출 하거나 내부 진행률 대리자를 다시 설정 합니다.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>설명

의 첫 번째 버전은 `FireCompletion()` 내부 진행 대리자 변수를 다시 설정 합니다. 비동기 작업이 완료 되 면 두 번째 버전은 완료 이벤트 처리기를 호출 합니다.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a> AsyncBase:: FireProgress

현재 진행률 이벤트 처리기를 호출 합니다.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>매개 변수

*인수가*<br/>
호출할 이벤트 처리기 메서드입니다.

### <a name="remarks"></a>설명

`ProgressTraits` 는 [ArgTraitsHelper 구조체](argtraitshelper-structure.md)에서 파생 됩니다.

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a> AsyncBase:: get_ErrorCode

현재 비동기 작업에 대 한 오류 코드를 검색 합니다.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>매개 변수

*errorCode*<br/>
현재 오류 코드가 저장 된 위치입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 현재 비동기 작업을 닫을지 여부를 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbaseget_id"></a><a name="get-id"></a> AsyncBase:: get_Id

비동기 작업의 핸들을 검색 합니다.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>매개 변수

*id*<br/>
핸들을 저장할 위치입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

### <a name="remarks"></a>설명

이 메서드는 `IAsyncInfo::get_Id`를 구현합니다.

## <a name="asyncbaseget_status"></a><a name="get-status"></a> AsyncBase:: get_Status

비동기 작업의 상태를 나타내는 값을 검색 합니다.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>매개 변수

*status*<br/>
상태를 저장할 위치입니다. 자세한 내용은 열거형을 참조 하세요 `Windows::Foundation::AsyncStatus` .

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

### <a name="remarks"></a>설명

이 메서드는 `IAsyncInfo::get_Status`를 구현합니다.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a> AsyncBase:: GetOnComplete

현재 완료 이벤트 처리기의 주소를 지정 된 변수에 복사 합니다.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>매개 변수

*completeHandler*<br/>
현재 완료 이벤트 처리기의 주소가 저장 되는 위치입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a> AsyncBase:: GetOnProgress

현재 진행률 이벤트 처리기의 주소를 지정 된 변수에 복사 합니다.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>매개 변수

*progressHandler*<br/>
현재 진행률 이벤트 처리기의 주소가 저장 되는 위치입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a> AsyncBase:: OnCancel

파생 클래스에서 재정의 되는 경우 비동기 작업을 취소 합니다.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a> AsyncBase:: OnClose

파생 클래스에서 재정의 되는 경우 비동기 작업을 닫습니다.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a> AsyncBase:: OnStart

파생 클래스에서 재정의 되는 경우 비동기 작업을 시작 합니다.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a> AsyncBase::p ut_Id

비동기 작업의 핸들을 설정 합니다.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>매개 변수

*id*<br/>
0이 아닌 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_INVALIDARG 또는 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a> AsyncBase::P utOnComplete

완료 이벤트 처리기의 주소를 지정 된 값으로 설정 합니다.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>매개 변수

*completeHandler*<br/>
완료 이벤트 처리기가 설정 된 주소입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a> AsyncBase::P utOnProgress

진행률 이벤트 처리기의 주소를 지정 된 값으로 설정 합니다.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>매개 변수

*progressHandler*<br/>
진행률 이벤트 처리기가 설정 된 주소입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.

## <a name="asyncbasestart"></a><a name="start"></a> AsyncBase:: Start

비동기 작업을 시작 합니다.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>반환 값

작업이 시작 되거나 이미 시작 된 경우 S_OK 합니다. 그렇지 않으면 E_ILLEGAL_STATE_CHANGE 합니다.

### <a name="remarks"></a>설명

`Start()` 는 호출자에 게 반환 되기 전에 비동기 작업 "hot start"가 표시 되기 때문에 외부적으로 표시 되지 않는 보호 된 메서드입니다.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a> AsyncBase:: TryTransitionToCompleted

현재 비동기 작업이 완료 되었는지 여부를 나타냅니다.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>반환 값

**`true`** 비동기 작업이 완료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a> AsyncBase:: TryTransitionToError

지정 된 오류 코드가 내부 오류 상태를 수정할 수 있는지 여부를 나타냅니다.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>매개 변수

*error*<br/>
오류 HRESULT입니다.

### <a name="return-value"></a>반환 값

**`true`** 내부 오류 상태가 변경 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 작업은 오류 상태가 이미 S_OK로 설정 된 경우에만 오류 상태를 수정 합니다. 오류 상태가 이미 오류, 취소 됨, 완료 됨 또는 닫힘 인 경우에는이 작업이 적용 되지 않습니다.
