---
description: Recursive_timed_mutex 클래스에 대해 자세히 알아보세요.
title: recursive_timed_mutex 클래스
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 55722414e89f6ec91fd355208ffe5dcc491405be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337881"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex 클래스

*시간이 지정된 뮤텍스 형식* 을 나타냅니다. 이러한 형식의 개체를 사용하면 프로그램 내에서 시간이 제한된 차단을 사용하여 상호 배제를 강제로 수행할 수 있습니다. [timed_mutex](../standard-library/timed-mutex-class.md) 형식의 개체와 달리 `recursive_timed_mutex` 개체에 대한 잠금 메서드 호출의 효과는 적절하게 정의됩니다.

## <a name="syntax"></a>구문

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|잠기지 않은 `recursive_timed_mutex` 개체를 생성합니다.|
|[~ recursive_timed_mutex 소멸자](#dtorrecursive_timed_mutex_destructor)|`recursive_timed_mutex` 개체에서 사용하는 리소스를 모두 해제합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.|
|[try_lock](#try_lock)|차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.|
|[try_lock_for](#try_lock_for)|지정된 시간 간격으로 `mutex`의 소유권 가져오기를 시도합니다.|
|[try_lock_until](#try_lock_until)|지정된 시간까지 `mutex`의 소유권 가져오기를 시도합니다.|
|[잠금을](#unlock)|`mutex`의 소유권을 해제합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<mutex>

**네임스페이스:** std

## <a name="lock"></a><a name="lock"></a> 잠기지

스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

호출 스레드가 `mutex`를 이미 소유하고 있으면 메서드는 결과를 즉시 반환하며 이전 잠금은 적용된 상태로 유지됩니다.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a> recursive_timed_mutex 생성자

잠기지 않은 `recursive_timed_mutex` 개체를 생성합니다.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex 소멸자

`recursive_timed_mutex` 개체에서 사용하는 리소스를 모두 해제합니다.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>설명

소멸자가 실행될 때 개체가 잠겨 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** 메서드가 성공적으로의 소유권을 얻거나 `mutex` 호출 스레드가를 이미 소유 하 고 있으면 `mutex` 이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

호출 스레드가를 이미 소유 하 `mutex` 고 있으면 함수는를 즉시 반환 **`true`** 하며 이전 잠금은 적용 된 상태로 유지 됩니다.

## <a name="try_lock_for"></a><a name="try_lock_for"></a> try_lock_for

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>매개 변수

*Rel_time*\
메서드가 `mutex`의 소유권을 가져오려고 시도하는 최대 시간을 지정하는 [chrono::duration](../standard-library/duration-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 메서드가 성공적으로의 소유권을 얻거나 `mutex` 호출 스레드가를 이미 소유 하 고 있으면 `mutex` 이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

호출 스레드가를 이미 소유 하 고 있는 경우 `mutex` 메서드는를 즉시 반환 **`true`** 하며 이전 잠금은 적용 된 상태로 유지 됩니다.

## <a name="try_lock_until"></a><a name="try_lock_until"></a> try_lock_until

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>매개 변수

*Abs_time*\
임계값을 지정하는 특정 시점으로, 이 시간 경과 후에는 메서드가 더 이상 `mutex`의 소유권을 가져오려고 시도하지 않습니다.

### <a name="return-value"></a>반환 값

**`true`** 메서드가 성공적으로의 소유권을 얻거나 `mutex` 호출 스레드가를 이미 소유 하 고 있으면 `mutex` 이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

호출 스레드가를 이미 소유 하 고 있는 경우 `mutex` 메서드는를 즉시 반환 **`true`** 하며 이전 잠금은 적용 된 상태로 유지 됩니다.

## <a name="unlock"></a><a name="unlock"></a> 잠금을

`mutex`의 소유권을 해제합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

이 메서드는 `recursive_timed_mutex` 개체에 대해 [lock](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) 및 [try_lock_until](#try_lock_until)이 정상적으로 호출된 횟수만큼 호출된 후에만 `mutex`의 소유권을 해제합니다.

호출 스레드가 `mutex`를 소유하지 않은 경우, 이 동작은 정의되지 않습니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
