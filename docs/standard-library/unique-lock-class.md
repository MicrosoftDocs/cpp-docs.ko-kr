---
title: unique_lock 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::unique_lock
dev_langs:
- C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9888b847c3e52cd8b6a034e95e35ca73933acd3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861833"
---
# <a name="uniquelock-class"></a>unique_lock 클래스

`mutex`의 잠금 및 잠금 해제를 관리하는 개체를 만들기 위해 인스턴스화할 수 있는 템플릿을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>설명

템플릿 인수 `Mutex`는 *뮤텍스 형식* 이름을 지정해야 합니다.

내부적으로는 `unique_lock`이 포인터 및 현재 스레드가 `mutex`를 소유하는지를 나타내는 `bool`을 연결된 `mutex` 개체에 저장합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|이름|설명|
|----------|-----------------|
|`mutex_type`|템플릿 인수 `Mutex`에 대한 동의어입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[unique_lock](#unique_lock)|`unique_lock` 개체를 생성합니다.|
|[~unique_lock 소멸자](#dtorunique_lock_destructor)|`unique_lock` 개체와 연결된 모든 리소스를 해제합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|스레드가 연결된 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.|
|[mutex](#mutex)|연결된 `mutex`에 대해 저장된 포인터를 검색합니다.|
|[owns_lock](#owns_lock)|호출 스레드가 연결된 `mutex`를 소유하는지를 지정합니다.|
|[release](#release)|연결된 `mutex` 개체에서 `unique_lock` 개체의 연결을 끊습니다.|
|[swap](#swap)|연결된 `mutex` 및 소유권 상태를 지정된 개체의 mutex 및 소유권 상태로 바꿉니다.|
|[try_lock](#try_lock)|차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.|
|[try_lock_for](#try_lock_for)|차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.|
|[try_lock_until](#try_lock_until)|차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.|
|[unlock](#unlock)|연결된 `mutex`의 소유권을 해제합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[operator bool](#op_bool)|연결된 `mutex`의 소유권이 호출 스레드에 있는지를 지정합니다.|
|[operator=](#op_eq)|저장된 `mutex` 포인터 및 연결된 소유권 상태를 지정한 개체에서 복사합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`unique_lock`

## <a name="requirements"></a>요구 사항

**헤더:** \<뮤텍스 >

**네임스페이스:** std

## <a name="lock"></a>  lock

스레드가 연결된 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

저장된 `mutex` 포인터가 `null`이면 이 메서드는 오류 코드가 `operation_not_permitted`인 [system_error](../standard-library/system-error-class.md)를 throw합니다.

호출 스레드가 연결된 `mutex`를 이미 소유하고 있으면 이 메서드는 오류 코드가 `resource_deadlock_would_occur`인 `system_error`를 throw합니다.

그렇지 않으면 이 메서드는 연결된 `mutex`에 대해 `lock`을 호출하고 내부 스레드 소유권 플래그를 `true`로 설정합니다.

## <a name="mutex"></a>  mutex

연결된 `mutex`에 대해 저장된 포인터를 검색합니다.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>  operator bool

연결된 뮤텍스의 소유권이 호출 스레드에 있는지를 지정합니다.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>반환 값

스레드가 뮤텍스를 소유하는 경우 `true`이고 그렇지 않으면 `false`입니다.

## <a name="op_eq"></a>  operator=

저장된 `mutex` 포인터 및 연결된 소유권 상태를 지정한 개체에서 복사합니다.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

`Other` A `unique_lock` 개체입니다.

### <a name="return-value"></a>반환 값

`*this`

### <a name="remarks"></a>설명

이 메서드가 `mutex`에 대해 `unlock`을 호출하기 전에 호출 스레드가 이전에 연결된 `mutex`를 소유하고 있었다면 새 값이 할당됩니다.

복사 후 이 메서드는 `Other`를 기본 생성 상태로 설정합니다.

## <a name="owns_lock"></a>  owns_lock

호출 스레드가 연결된 `mutex`를 소유하는지를 지정합니다.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>반환 값

스레드가 `mutex`를 소유하는 경우 `true`이고 그렇지 않으면 `false`입니다.

## <a name="release"></a>  release

연결된 `mutex` 개체에서 `unique_lock` 개체의 연결을 끊습니다.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>반환 값

저장된 `mutex` 포인터의 이전 값입니다.

### <a name="remarks"></a>설명

이 메서드는 저장된 `mutex` 포인터의 값을 0으로 설정하고 내부 `mutex` 소유권 플래그를 `false`로 설정합니다.

## <a name="swap"></a>  swap

연결된 `mutex` 및 소유권 상태를 지정된 개체의 mutex 및 소유권 상태로 바꿉니다.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

`Other` A `unique_lock` 개체입니다.

## <a name="try_lock"></a>  try_lock

차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

저장된 `mutex` 포인터가 `null`이면 이 메서드는 오류 코드가 `operation_not_permitted`인 [system_error](../standard-library/system-error-class.md)를 throw합니다.

호출 스레드가 `mutex`를 이미 소유하고 있으면 이 메서드는 오류 코드가 `resource_deadlock_would_occur`인 `system_error`를 throw합니다.

## <a name="try_lock_for"></a>  try_lock_for

차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>매개 변수

`Rel_time` A [chrono::](../standard-library/duration-class.md) 메서드의 소유권을 가져오려고 시도 하는 최대 기간을 지정 하는 개체는 `mutex`합니다.

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

저장된 `mutex` 포인터가 `null`이면 이 메서드는 오류 코드가 `operation_not_permitted`인 [system_error](../standard-library/system-error-class.md)를 throw합니다.

호출 스레드가 `mutex`를 이미 소유하고 있으면 이 메서드는 오류 코드가 `resource_deadlock_would_occur`인 `system_error`를 throw합니다.

## <a name="try_lock_until"></a>  try_lock_until

차단되지 않고 연결된 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>매개 변수

`Abs_time` 지정 시간에는 메서드가 더 이상 소유권을 가져오려고 시도의 임계값을 지정 하는 `mutex`합니다.

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

저장된 `mutex` 포인터가 `null`이면 이 메서드는 오류 코드가 `operation_not_permitted`인 [system_error](../standard-library/system-error-class.md)를 throw합니다.

호출 스레드가 `mutex`를 이미 소유하고 있으면 이 메서드는 오류 코드가 `resource_deadlock_would_occur`인 `system_error`를 throw합니다.

## <a name="unique_lock"></a>  unique_lock 생성자

`unique_lock` 개체를 생성합니다.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>매개 변수

`Mtx` 뮤텍스 형식 개체입니다.

`Rel_time` A [chrono::](../standard-library/duration-class.md) 메서드의 소유권을 가져오려고 시도 하는 최대 기간을 지정 하는 개체는 `mutex`합니다.

`Abs_time` 지정 시간에는 메서드가 더 이상 소유권을 가져오려고 시도의 임계값을 지정 하는 `mutex`합니다.

`Other` A `unique_lock` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 연결된 뮤텍스 포인터 값 0이 포함된 개체를 생성합니다.

두 번째 생성자는 연결된 뮤텍스 상태를 `Other`에서 이동합니다. 이동 후에는 `Other`가 뮤텍스와 더 이상 연결되지 않습니다.

나머지 생성자는 & `Mtx`를 저장된 `mutex` 포인터로 저장합니다. `mutex`의 소유권은 두 번째 인수(있는 경우)에 의해 결정됩니다.

|||
|-|-|
|`No argument`|연결된 `mutex` 개체에 대해 `lock` 메서드를 호출하여 소유권을 가져옵니다.|
|`Adopt`|이때 소유권이 있는 것으로 가정합니다. 생성자를 호출할 때 `Mtx`가 잠겨 있어야 합니다.|
|`Defer`|호출 스레드는 `mutex` 개체를 소유하지 않는다고 가정합니다. 생성자를 호출할 때는 `Mtx`가 잠겨 있지 않아야 합니다.|
|`Try`|연결된 `mutex` 개체에 대해 `try_lock`을 호출하여 소유권을 가져옵니다. 생성자는 아무 항목도 throw하지 않습니다.|
|`Rel_time`|`try_lock_for(Rel_time)`를 호출하여 소유권을 결정합니다.|
|`Abs_time`|`try_lock_until(Abs_time)`을 호출하여 소유권을 결정합니다.|

## <a name="dtorunique_lock_destructor"></a>  ~unique_lock 소멸자

`unique_lock` 개체와 연결된 모든 리소스를 해제합니다.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>설명

호출 스레드가 연결된 `mutex`를 소유하는 경우 소멸자는 `mutex` 개체에 대해 unlock을 호출하여 소유권을 해제합니다.

## <a name="unlock"></a>  unlock

연결된 `mutex`의 소유권을 해제합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

호출 스레드가 연결된 `mutex`를 소유하고 있지 않으면 이 메서드는 오류 코드가 `operation_not_permitted`인 [system_error](../standard-library/system-error-class.md)를 throw합니다.

그렇지 않으면 이 메서드는 연결된 `mutex`에 대해 `unlock`을 호출하고 내부 스레드 소유권 플래그를 `false`로 설정합니다.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
