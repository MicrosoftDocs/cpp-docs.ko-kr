---
description: '자세한 정보: IThreadProxy 구조체'
title: IThreadProxy 구조체
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: e63a4d2bc29a1ae846e30d1b7e93c125def971b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334390"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 구조체

실행 스레드에 대한 추상화입니다. 직접 만든 스케줄러의 `SchedulerType` 정책 키에 따라 리소스 관리자는 일반 Win32 스레드 또는 UMS(사용자 모드 예약 가능) 스레드 중 하나에서 지원되는 스레드 프록시를 부여합니다. UMS 스레드는 Windows 7 이상 버전의 64비트 운영 체제에서 지원됩니다.

## <a name="syntax"></a>구문

```cpp
struct IThreadProxy;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IThreadProxy:: GetId](#getid)|스레드 프록시에 대 한 고유 식별자를 반환 합니다.|
|[IThreadProxy:: SwitchOut](#switchout)|내부 가상 프로세서 루트에서 컨텍스트의 연결을 끊습니다.|
|[IThreadProxy:: SwitchTo](#switchto)|현재 실행 중인 컨텍스트에서 다른 컨텍스트로의 협조적 컨텍스트 전환을 수행 합니다.|
|[IThreadProxy:: YieldToSystem](#yieldtosystem)|호출 스레드가 현재 프로세서에서 실행할 준비가 되어 있는 다른 스레드에 실행 명령을 내리도록 합니다. 운영 체제에서 실행할 다음 스레드를 선택 합니다.|

## <a name="remarks"></a>설명

스레드 프록시는 `IExecutionContext` 작업 디스패치 수단으로 인터페이스로 표시 되는 실행 컨텍스트에 연결 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IThreadProxy`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="ithreadproxygetid-method"></a><a name="getid"></a> IThreadProxy:: GetId 메서드

스레드 프록시에 대 한 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>반환 값

고유한 정수 식별자입니다.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a> IThreadProxy:: SwitchOut 메서드

내부 가상 프로세서 루트에서 컨텍스트의 연결을 끊습니다.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>매개 변수

*switchState*<br/>
스위치를 실행 하는 스레드 프록시의 상태를 나타냅니다. 매개 변수는 형식입니다 `SwitchingProxyState` .

### <a name="remarks"></a>설명

어떠한 이유로든 실행 중인 가상 프로세서 루트에서 컨텍스트 연결을 끊어야 할 경우 `SwitchOut`을 사용합니다. `switchState` 매개변수에 전달하는 값에 따라 그리고 가상 프로세서 루트에서 실행하는지 여부에 따라 이 호출은 해당 컨텍스트와 연결된 스레드 프록시를 즉시 반환하거나 차단합니다. 매개 변수를 `SwitchOut`로 설정하여 `Idle`을 호출하면 오류가 발생합니다. 이렇게 하면 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외가 발생 합니다.

`SwitchOut`은 리소스 관리자의 지시에 따라 또는 일시적으로 초과 구독된 가상 프로세서 루트를 요청했는데 그러한 요청이 처리되어 스케줄러의 가상 프로세서 루트 수를 줄이고자 할 때 유용합니다. 이 경우 매개 변수를로 설정 하 여에 대 한 호출을 수행 하기 전에 가상 프로세서 루트에서 [IVirtualProcessorRoot:: Remove](iexecutionresource-structure.md#remove) 메서드를 호출 해야 합니다 `SwitchOut` `switchState` `Blocking` . 이렇게 하면 스레드 프록시가 차단되고, 스케줄러의 다른 가상 프로세서 루트에서 실행할 수 있을 때 실행이 다시 시작됩니다. `SwitchTo`이 스레드 프록시의 실행 컨텍스트로 전환 하는 함수를 호출 하 여 차단 스레드 프록시를 다시 시작할 수 있습니다. 연결 된 컨텍스트를 사용 하 여 가상 프로세서 루트를 활성화 하 여 스레드 프록시를 다시 시작할 수도 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)를 참조 하세요.

또한 `SwitchOut`은 스레드 프록시를 차단하거나, 스레드 프록시가 실행 중인 가상 프로세서 루트와 스레드 프록시를 디스패칭하는 스케줄러에서 일시적으로 연결을 끊는 동안 나중에 활성화될 수 있도록 가상 프로세서를 다시 초기화하려 할 때도 사용할 수 있습니다. 스레드 프록시를 차단하려는 경우 `SwitchOut` 매개 변수를 `switchState`으로 설정하여 `Blocking`을 사용합니다. 위에서 언급했듯이 `SwitchTo` 또는 `IVirtualProcessorRoot::Activate`을 사용하여 나중에 다시 시작할 수 있습니다. 이 스레드 프록시가 실행 중인 가상 프로세서 루트 및 가상 프로세서가 연결된 스케줄러에서 일시적으로 스레드 프록시의 연결을 끊으려면 매개 변수를 `SwitchOut`으로 설정하여 `Nesting`을 사용합니다. 가상 프로세서 루트에서 실행 중일 때 `SwitchOut` 매개 변수를 `switchState`으로 설정하여 `Nesting`을 호출하면 루트가 다시 초기화되고 현재 스레드 프록시가 다른 루트를 필요로 하지 않고 계속 실행됩니다. 스레드 프록시는 이후 시점에서를 사용 하 여 [Ithreadproxy:: SwitchOut](#switchout) 메서드를 호출할 때까지 스케줄러에서 남겨진 것으로 간주 됩니다 `Blocking` . 매개 변수를 `SwitchOut`으로 설정하여 `Blocking`을 두 번째로 호출하는 목적은, 컨텍스트를 차단된 상태로 돌려서 `SwitchTo` 또는 컨텍스트 연결을 끊은 스케줄러의 `IVirtualProcessorRoot::Activate`에 의해 다시 시작될 수 있도록 하는 것입니다. 컨텍스트는 가상 프로세서 루트에서 실행되고 있지 않았기 때문에 다시 초기화가 수행되지 않습니다.

다시 초기화된 가상 프로세서 루트는 리소스 관리자가 스케줄러를 부여한 새로운 가상 프로세서 루트와 차이가 없습니다. 이는 `IVirtualProcessorRoot::Activate`를 사용하여 실행 컨텍스트로 가상 프로세서 루트를 활성화함으로써 실행하는 데 사용할 수 있습니다.

`SwitchOut``IThreadProxy`현재 실행 중인 스레드를 나타내는 인터페이스에서를 호출 해야 합니다. 그렇지 않으면 결과가 정의 되지 않습니다.

Visual Studio 2010과 함께 제공된 헤더 및 라이브러리에서 이 메서드는 매개 변수를 사용하지 않으며 가상 프로세서 루트를 다시 초기화하지 않습니다. 이전 동작을 유지하기 위해 `Blocking`의 기본 매개 변수 값이 제공됩니다.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a> IThreadProxy:: SwitchTo 메서드

현재 실행 중인 컨텍스트에서 다른 컨텍스트로의 협조적 컨텍스트 전환을 수행 합니다.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
협조적 전환에 대 한 실행 컨텍스트입니다.

*switchState*<br/>
스위치를 실행 하는 스레드 프록시의 상태를 나타냅니다. 매개 변수는 형식입니다 `SwitchingProxyState` .

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 첫 번째 실행 컨텍스트의 [IExecutionContext::D ispatch](iexecutioncontext-structure.md#dispatch) 메서드에서 한 실행 컨텍스트에서 다른 실행 컨텍스트로 전환 합니다. 메서드는 `pContext` 이미 연결 되어 있지 않은 경우 실행 컨텍스트를 스레드 프록시와 연결 합니다. 현재 스레드 프록시의 소유권은 인수에 대해 지정 하는 값에 따라 결정 됩니다 `switchState` .

`Idle`현재 실행 중인 스레드 프록시를 리소스 관리자로 반환 하려는 경우 값을 사용 합니다. `SwitchTo`매개 변수 `switchState` 를로 설정 하 여를 호출 하면 `Idle` 실행 컨텍스트가 `pContext` 기본 실행 리소스에서 실행 되기 시작 합니다. 이 스레드 프록시의 소유권은 리소스 관리자 전송 되며, `Dispatch` 전송을 완료 하기 위해가 반환 된 후 즉시 실행 컨텍스트의 메서드에서 반환 되어야 합니다 `SwitchTo` . 스레드 프록시의 디스패치를 수행 하는 실행 컨텍스트는 스레드 프록시와 분리 되며 스케줄러는 적합 한 것으로 표시 될 때이를 다시 사용 하거나 소멸 시킬 수 있습니다.

`Blocking`이 스레드 프록시가 차단 된 상태로 전환 되 게 하려면 값을 사용 합니다. `SwitchTo`매개 변수 `switchState` 를로 설정 하 여를 호출 하면 실행 컨텍스트가 실행을 시작 하 `Blocking` `pContext` 고, 다시 시작 될 때까지 현재 스레드 프록시가 차단 됩니다. 스레드 프록시가 상태일 때 스케줄러는 스레드 프록시의 소유권을 유지 `Blocking` 합니다. `SwitchTo`이 스레드 프록시의 실행 컨텍스트로 전환 하는 함수를 호출 하 여 차단 스레드 프록시를 다시 시작할 수 있습니다. 연결 된 컨텍스트를 사용 하 여 가상 프로세서 루트를 활성화 하 여 스레드 프록시를 다시 시작할 수도 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)를 참조 하세요.

`Nesting`이 스레드 프록시가 실행 중인 가상 프로세서 루트에서이 스레드 프록시를 일시적으로 분리 하 고,이 스레드 프록시가 작업을 디스패치할 스케줄러에서 일시적으로 분리 하려는 경우 값을 사용 합니다. `SwitchTo`매개 변수 `switchState` 를로 설정 하 여를 호출 하면 `Nesting` 실행 컨텍스트가 실행 되기 `pContext` 시작 하 고, 현재 스레드 프록시도 가상 프로세서 루트를 요구 하지 않고 계속 실행 됩니다. 스레드 프록시는 나중에 [Ithreadproxy:: SwitchOut](#switchout) 메서드를 호출할 때까지 스케줄러에서 남겨진 것으로 간주 됩니다. `IThreadProxy::SwitchOut`이 메서드는 가상 프로세서 루트를 다시 예약 하는 데 사용할 수 있을 때까지 스레드 프록시를 차단할 수 있습니다.

`SwitchTo``IThreadProxy`현재 실행 중인 스레드를 나타내는 인터페이스에서를 호출 해야 합니다. 그렇지 않으면 결과가 정의 되지 않습니다. `invalid_argument`매개 변수가로 설정 되 면 함수는을 throw 합니다 `pContext` `NULL` .

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a> IThreadProxy:: YieldToSystem 메서드

호출 스레드가 현재 프로세서에서 실행할 준비가 되어 있는 다른 스레드에 실행 명령을 내리도록 합니다. 운영 체제에서 실행할 다음 스레드를 선택 합니다.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>설명

일반 Windows 스레드에 의해 지원 되는 스레드 프록시에 의해 호출 되는 경우는 `YieldToSystem` windows 함수와 똑같이 동작 `SwitchToThread` 합니다. 그러나 UMS (사용자 모드 예약 가능) 스레드에서 호출 하는 경우이 `SwitchToThread` 함수는 운영 체제가 아닌 사용자 모드 스케줄러에 실행할 다음 스레드를 선택 하는 작업을 위임 합니다. 시스템에서 다른 준비 스레드로 전환 하는 데 필요한 효과를 얻으려면를 사용 `YieldToSystem` 합니다.

`YieldToSystem``IThreadProxy`현재 실행 중인 스레드를 나타내는 인터페이스에서를 호출 해야 합니다. 그렇지 않으면 결과가 정의 되지 않습니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[IExecutionContext 구조체](iexecutioncontext-structure.md)<br/>
[IScheduler 구조체](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 구조체](ivirtualprocessorroot-structure.md)
