---
description: Condition_variable_any 클래스에 대해 자세히 알아보세요.
title: condition_variable_any 클래스
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 853944a8eab0698fae6a12cace4ce9426ada8f3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324999"
---
# <a name="condition_variable_any-class"></a>condition_variable_any 클래스

`condition_variable_any` 클래스를 사용하여 모든 `mutex` 형식의 이벤트를 대기합니다.

## <a name="syntax"></a>구문

```cpp
class condition_variable_any;
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[condition_variable_any](#condition_variable_any)|`condition_variable_any` 개체를 생성합니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[notify_all](#notify_all)|`condition_variable_any` 개체를 대기 중인 모든 스레드를 차단 해제합니다.|
|[notify_one](#notify_one)|`condition_variable_any` 개체를 대기 중인 스레드 중 하나를 차단 해제합니다.|
|[대기한](#wait)|스레드를 차단합니다.|
|[wait_for](#wait_for)|스레드를 차단하고 스레드가 차단 해제되는 시간 간격을 설정합니다.|
|[wait_until](#wait_until)|스레드를 차단하고 스레드가 차단 해제되는 최대 시점을 설정합니다.|

## <a name="condition_variable_any"></a><a name="condition_variable_any"></a> condition_variable_any

`condition_variable_any` 개체를 생성합니다.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>설명

메모리가 부족한 경우 생성자에서 `not_enough_memory` 오류 코드가 있는 [system_error](../standard-library/system-error-class.md) 개체를 throw합니다. 몇 가지 다른 리소스를 사용할 수 없기 때문에 개체를 생성할 수 없는 경우 생성자에서 `resource_unavailable_try_again` 오류 코드가 있는 `system_error` 개체를 throw합니다.

## <a name="notify_all"></a><a name="notify_all"></a> notify_all

`condition_variable_any` 개체를 대기 중인 모든 스레드를 차단 해제합니다.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a><a name="notify_one"></a> notify_one

`condition_variable_any` 개체를 기다리는 스레드 중 하나를 차단 해제합니다.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a><a name="wait"></a> 대기한

스레드를 차단합니다.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>매개 변수

*Lck*\
모든 형식의 `mutex` 개체입니다.

*Pred*\
또는를 반환 하는 식입니다 **`true`** **`false`** .

### <a name="remarks"></a>설명

첫 번째 메서드는 `condition_variable_any` 개체에서 [notify_one](../standard-library/condition-variable-class.md#notify_one) 또는 [notify_all](../standard-library/condition-variable-class.md#notify_all)에 대한 호출을 통해 신호를 받을 때까지 차단합니다. 또한 의사적으로 대기 모드를 해제할 수도 있습니다.

두 번째 메서드는 실제로 다음 코드를 실행합니다.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a><a name="wait_for"></a> wait_for

스레드를 차단하고 스레드가 차단 해제되는 시간 간격을 설정합니다.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>매개 변수

*Lck*\
모든 형식의 `mutex` 개체입니다.

*Rel_time*\
스레드가 대기 모드를 해제하기 전까지의 시간을 지정하는 `chrono::duration` 개체입니다.

*Pred*\
또는를 반환 하는 식입니다 **`true`** **`false`** .

### <a name="return-value"></a>반환 값

첫 번째 메서드는 `cv_status::timeout` *Rel_time* 경과할 때 대기가 종료 될 경우를 반환 합니다. 그렇지 않은 경우 메서드는 `cv_status::no_timeout`를 반환합니다.

두 번째 메서드는 *Pred* 의 값을 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 메서드는 `condition_variable_any` 개체가 [notify_one](../standard-library/condition-variable-class.md#notify_one) 또는 [notify_all](../standard-library/condition-variable-class.md#notify_all)에 대 한 호출로 신호를 받거나 시간 간격 *Rel_time* 경과할 때까지 차단 됩니다. 또한 의사적으로 대기 모드를 해제할 수도 있습니다.

두 번째 메서드는 실제로 다음 코드를 실행합니다.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a><a name="wait_until"></a> wait_until

스레드를 차단하고 스레드가 차단 해제되는 최대 시점을 설정합니다.

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>매개 변수

*Lck*\
뮤텍스 개체입니다.

*Abs_time*\
[chrono::time_point](../standard-library/time-point-class.md) 개체입니다.

*Pred*\
또는를 반환 하는 식입니다 **`true`** **`false`** .

### <a name="return-value"></a>반환 값

형식을 반환 하는 메서드는 `cv_status` `cv_status::timeout` *Abs_time* 경과할 때 대기가 종료 될 경우를 반환 합니다. 그렇지 않으면 메서드는 `cv_status::no_timeout`을 반환합니다.

을 반환 하는 메서드는 **`bool`** *Pred* 의 값을 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 메서드는 `condition_variable` 개체가 [notify_one](../standard-library/condition-variable-class.md#notify_one) 또는 [notify_all](../standard-library/condition-variable-class.md#notify_all)에 대 한 호출로 신호를 받거나 *Abs_time* 때까지 차단 합니다. 또한 의사적으로 대기 모드를 해제할 수도 있습니다.

두 번째 메서드는 실제로 다음 코드를 실행합니다.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

세 번째와 네 번째 메서드는 `xtime` 형식의 개체에 대한 포인터를 사용하여 `chrono::time_point` 개체를 대체합니다. `xtime` 개체는 신호를 기다리는 최대 시간을 지정합니다.
