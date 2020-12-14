---
description: '자세한 정보: task 클래스 (동시성 런타임)'
title: 작업 클래스(동시성 런타임)
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: b16c7e8f7ae97b35731916d6834367c228ce867c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188380"
---
# <a name="task-class-concurrency-runtime"></a>작업 클래스(동시성 런타임)

PPL(병렬 패턴 라이브러리) `task` 클래스입니다. `task`개체는 동시성 런타임의 병렬 알고리즘에 의해 생성 된 다른 작업 및 병렬 작업과 동시에 비동기적으로 실행 될 수 있는 작업을 나타냅니다. 이러한 작업이 정상적으로 완료되면 `_ResultType` 형식의 결과가 생성됩니다. `task<void>` 형식의 작업에서는 결과가 생성되지 않습니다. 작업은 다른 작업과 관계없이 대기 및 취소할 수 있으며 연속 ( `then` ), join ( `when_all` ) 및 choice () 패턴을 사용 하 여 다른 작업으로 구성 될 수도 있습니다 `when_any` . 작업 개체가 새 변수에 할당 되는 경우의 동작은입니다 `std::shared_ptr` . 즉, 두 개체가 모두 동일한 기본 작업을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>매개 변수

*_ResultType*<br/>
태스크에서 생성 하는 결과의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`result_type`|이 클래스의 개체가 생성하는 결과의 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[임무](#ctor)|오버로드됨. `task` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get](#get)|오버로드됨. 이 작업으로 생성된 결과를 반환합니다. 작업이 종료 상태가 아닐 경우 `get`에 대한 호출은 작업이 끝날 때까지 대기합니다. 이 메서드는가 인 작업에 대해 호출 될 때 값을 반환 하지 않습니다 `result_type` **`void`** .|
|[is_apartment_aware](#is_apartment_aware)|작업이 Windows 런타임 `IAsyncInfo` 인터페이스의 래핑을 해제하는지 여부 또는 그러한 작업의 하위 작업인지 여부를 확인합니다.|
|[is_done](#is_done)|작업 완료 여부를 확인합니다.|
|[일정표](#scheduler)|이 작업에 대해 스케줄러를 반환합니다.|
|[다음](#then)|오버로드됨. 이 작업에 연속 작업을 추가합니다.|
|[대기한](#wait)|이 작업이 종료 상태에 도달할 때까지 기다립니다. `wait`은 작업 종속성을 모두 만족하며 백그라운드 작업자에 의해 이미 선택되지 않은 경우 작업을 인라인 실행할 수 있습니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자! =](#operator_neq)|오버로드됨. 두 `task` 개체가 서로 다른 내부 작업을 나타내는지 여부를 확인합니다.|
|[연산자 =](#operator_eq)|오버로드됨. 하나의 `task` 개체 콘텐츠를 다른 개체 콘텐츠로 바꿉니다.|
|[연산자 = =](#operator_eq_eq)|오버로드됨. 두 `task` 개체가 동일한 내부 작업을 나타내는지 여부를 확인합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`task`

## <a name="requirements"></a>요구 사항

**헤더:** ppltasks.h

**네임 스페이스:** 동시성

## <a name="get"></a><a name="get"></a> 가져오기

이 작업으로 생성된 결과를 반환합니다. 작업이 종료 상태가 아닐 경우 `get`에 대한 호출은 작업이 끝날 때까지 대기합니다. 이 메서드는가 인 작업에 대해 호출 될 때 값을 반환 하지 않습니다 `result_type` **`void`** .

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>반환 값

작업의 결과입니다.

### <a name="remarks"></a>설명

작업이 취소 되 면를 호출 하면 `get` [task_canceled](task-canceled-class.md) 예외가 throw 됩니다. 작업에서 다른 예외가 발생하거나 예외가 선행 작업에서 전파된 경우 `get`에 대한 호출은 해당 예외를 throw합니다.

> [!IMPORTANT]
> UWP (유니버설 Windows 플랫폼) 앱에서 [](#wait) `get` `wait` `get` 사용자 인터페이스 스레드에서 실행 되는 코드에서 concurrency:: task:: wait 또는 (호출)를 호출 하지 마세요. 그렇지 않으면이 메서드는 현재 스레드를 차단 하 고 앱이 응답 하지 않을 수 있으므로 [concurrency:: invalid_operation](invalid-operation-class.md) 을 throw 합니다. 그러나 `get` 결과를 즉시 사용할 수 있기 때문에 메서드를 호출 하 여 작업 기반 연속에서 선행 작업의 결과를 받을 수 있습니다.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a> is_apartment_aware

작업이 Windows 런타임 `IAsyncInfo` 인터페이스의 래핑을 해제하는지 여부 또는 그러한 작업의 하위 작업인지 여부를 확인합니다.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>반환 값

**`true`** 태스크가 인터페이스를의 래핑을 해제 `IAsyncInfo` 하거나 그러한 작업의 하위 항목인 경우이 고, **`false`** 그렇지 않으면입니다.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a> task:: is_done 메서드 (동시성 런타임)

작업 완료 여부를 확인합니다.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>반환 값

태스크가 완료 되었으면 True이 고, 그렇지 않으면 false입니다.

### <a name="remarks"></a>설명

작업을 완료 하거나 취소 하는 경우 (사용자 예외 유무에 관계 없이) 함수는 true를 반환 합니다.

## <a name="operator"></a><a name="operator_neq"></a> 연산자! =

두 `task` 개체가 서로 다른 내부 작업을 나타내는지 여부를 확인합니다.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
비교할 작업입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 서로 다른 기본 작업을 참조 하면이 고, **`false`** 그렇지 않으면입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

하나의 `task` 개체 콘텐츠를 다른 개체 콘텐츠로 바꿉니다.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
소스 `task` 개체입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

`task`가 스마트 포인터와 같이 작동할 경우, 복사 할당 후 이 `task` 개체는 `_Other`와 동일한 실제 작업을 나타냅니다.

## <a name="operator"></a><a name="operator_eq_eq"></a> 연산자 = =

두 `task` 개체가 동일한 내부 작업을 나타내는지 여부를 확인합니다.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
비교할 작업입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 동일한 기본 작업을 참조 하면이 고, **`false`** 그렇지 않으면입니다.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a> task:: scheduler 메서드 (동시성 런타임)

이 작업에 대해 스케줄러를 반환합니다.

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>반환 값

스케줄러에 대 한 포인터입니다.

## <a name="task"></a><a name="ctor"></a> 작업

`task` 개체를 생성합니다.

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
작업이 생성되는 매개 변수 형식입니다.

*_Param*<br/>
작업이 생성되는 매개 변수입니다. `task_completion_event<result_type>`Windows 런타임 앱에서 작업을 사용 하는 경우이는 람다, 함수 개체, 개체 또는 Windows:: Foundation:: IAsyncInfo 일 수 있습니다. 람다 또는 함수 개체는와 동일한 형식 이어야 합니다 `std::function<X(void)>` . 여기서 X는 `result_type` , `task<result_type>` 또는 Windows 런타임 apps의 Windows:: Foundation:: IAsyncInfo 형식의 변수일 수 있습니다.

*_TaskOptions*<br/>
작업 옵션에는 취소 토큰, 스케줄러 등이 포함됩니다.

*_Other*<br/>
소스 `task` 개체입니다.

### <a name="remarks"></a>설명

`task`에 대한 기본 생성자는 컨테이너 내에서 사용할 수 있는 작업을 허용하기 위해서만 존재합니다. 유효한 작업을 할당할 때까지 기본 생성 작업을 사용할 수 없습니다. 또는와 같은 메서드는 `get` `wait` `then` 기본 생성 작업에서 호출 될 때 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다.

`task_completion_event`에서 만든 작업은 작업 완료 이벤트가 설정되면 완료됩니다(연속 실행되도록 예약되어 있음).

취소 토큰을 사용하는 생성자의 버전은 이 토큰을 가져온 `cancellation_token_source`를 사용하여 취소할 수 있는 작업을 만듭니다. 취소 토큰 없이 만든 작업은 취소할 수 없습니다.

`Windows::Foundation::IAsyncInfo` 인터페이스에서 생성되었거나 `IAsyncInfo` 인터페이스를 반환하는 람다에서 생성된 작업은 포함된 Windows 런타임 비동기 작업 또는 동작이 완료될 때 종료 상태에 도달합니다. 마찬가지로을 반환 하는 람다에서 만든 작업은 `task<result_type>` 람다가 반환 될 때가 아닌 내부 작업이 터미널 상태에 도달 하면 해당 터미널 상태에 도달 합니다.

`task`는 스마트 포인터처럼 작동하고 값으로 안전하게 전달됩니다. 또한 잠글 필요 없이 여러 스레드에서 액세스할 수 있습니다.

Windows:: Foundation:: IAsyncInfo 인터페이스를 사용 하는 생성자 오버 로드 또는 이러한 인터페이스를 반환 하는 람다는 Windows 런타임 앱 에서만 사용할 수 있습니다.

자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

## <a name="then"></a><a name="then"></a> 다음

이 작업에 연속 작업을 추가합니다.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
이 작업으로 호출될 함수 개체의 형식입니다.

*_Func*<br/>
이 작업이 완료될 때 실행되는 연속 함수입니다. 이 연속 함수는 `result_type` 또는 `task<result_type>`을 입력 변수로 사용해야 하며, 여기서 `result_type`은 이 작업에서 생성하는 결과의 형식입니다.

*_TaskOptions*<br/>
작업 옵션에는 취소 토큰, 스케줄러 및 연속 컨텍스트가 포함됩니다. 기본적으로 앞의 세 가지 옵션은 선행 작업에서 상속됩니다.

*_CancellationToken*<br/>
연속 작업에 연결할 취소 토큰입니다. 취소 토큰 없이 만든 연속 작업은 선행 작업의 토큰을 상속합니다.

*_ContinuationContext*<br/>
연속이 실행되어야 하는 위치를 지정하는 변수입니다. 이 변수는 UWP 앱에서 사용 하는 경우에만 유용 합니다. 자세한 내용은 [task_continuation_context](task-continuation-context-class.md) 를 참조 하세요.

### <a name="return-value"></a>반환 값

새로 만든 연속 작업입니다. 반환된 작업의 결과 형식은 `_Func`가 반환하는 것에 따라 결정됩니다.

### <a name="remarks"></a>설명

`then`Windows:: Foundation:: IAsyncInfo 인터페이스를 반환 하는 람다 또는 함수를 사용 하는의 오버 로드는 Windows 런타임 앱 에서만 사용할 수 있습니다.

작업 연속을 사용 하 여 비동기 작업을 작성 하는 방법에 대 한 자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

## <a name="wait"></a><a name="wait"></a> 대기한

이 작업이 종료 상태에 도달할 때까지 기다립니다. `wait`은 작업 종속성을 모두 만족하며 백그라운드 작업자에 의해 이미 선택되지 않은 경우 작업을 인라인 실행할 수 있습니다.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>반환 값

`task_status` 또는 `completed`가 될 수 있는 `canceled` 값입니다. 작업 실행 중에 예외가 발생하거나 예외가 선행 작업에서 전파된 경우 `wait`은 해당 예외를 throw합니다.

### <a name="remarks"></a>설명

> [!IMPORTANT]
> UWP (유니버설 Windows 플랫폼) 앱에서 `wait` 사용자 인터페이스 스레드에서 실행 되는 코드를 호출 하지 마세요. 호출하는 경우 이 메서드가 현재 스레드를 차단하고 앱이 응답하지 않게 만들 수 있기 때문에 런타임에서 [concurrency::invalid_operation](invalid-operation-class.md) 을 throw합니다. 그러나 [concurrency::task::get](#get) 메서드를 호출하여 작업 기반 연속에서 선행 작업의 결과를 받을 수 있습니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
