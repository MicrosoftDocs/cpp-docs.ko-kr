---
title: timed_mutex 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
dev_langs:
- C++
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: a4dc22ed8676c720dd8bde5c8f424915dfa8fe40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="timedmutex-class"></a>timed_mutex 클래스

*시간이 지정된 뮤텍스 형식*을 나타냅니다. 이러한 형식의 개체를 사용하면 프로그램 내에서 시간이 제한된 차단을 통해 상호 배제를 강제로 수행할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class timed_mutex;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|잠기지 않은 `timed_mutex` 개체를 생성합니다.|
|[timed_mutex::~timed_mutex 소멸자](#dtortimed_mutex_destructor)|`timed_mutex` 개체에서 사용하는 리소스를 모두 해제합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.|
|[try_lock](#try_lock)|차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.|
|[try_lock_for](#try_lock_for)|지정된 시간 간격으로 `mutex`의 소유권 가져오기를 시도합니다.|
|[try_lock_until](#try_lock_until)|지정된 시간까지 `mutex`의 소유권 가져오기를 시도합니다.|
|[unlock](#unlock)|`mutex`의 소유권을 해제합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<뮤텍스 >

**네임스페이스:** std

## <a name="lock"></a>  timed_mutex::lock

스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="timed_mutex"></a>  timed_mutex::timed_mutex 생성자

잠기지 않은 `timed_mutex` 개체를 생성합니다.

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>  timed_mutex::~timed_mutex 소멸자

`mutex` 개체에서 사용하는 리소스를 모두 해제합니다.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>설명

소멸자가 실행될 때 개체가 잠겨 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="try_lock"></a>  timed_mutex::try_lock

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
bool try_lock();
```

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="try_lock_for"></a>  timed_mutex::try_lock_for

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>매개 변수

`Rel_time` A [chrono::](../standard-library/duration-class.md) 메서드의 소유권을 가져오려고 시도 하는 최대 기간을 지정 하는 개체는 `mutex`합니다.

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="try_lock_until"></a>  timed_mutex::try_lock_until

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>매개 변수

`Abs_time` 지정 시간에는 메서드가 더 이상 소유권을 가져오려고 시도의 임계값을 지정 하는 `mutex`합니다.

### <a name="return-value"></a>반환 값

메서드가 성공적으로 `true`의 소유권을 가져오면 `mutex`이고, 그렇지 않으면 `false`입니다.

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="unlock"></a>  timed_mutex::unlock

`mutex`의 소유권을 해제합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

호출 스레드가 `mutex`를 소유하지 않은 경우, 이 동작은 정의되지 않습니다.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
