---
description: '자세한 정보: mutex 클래스 (c + + 표준 라이브러리)'
title: mutex 클래스(C++ 표준 라이브러리)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 528fe0698fb7815be9b678d72055c54bad5ce2bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338283"
---
# <a name="mutex-class-c-standard-library"></a>mutex 클래스(C++ 표준 라이브러리)

*뮤텍스 형식을* 나타냅니다. 이 형식의 객체는 프로그램 내에서 상호 제외를 강제 수행하기 위해 사용될 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class mutex;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[뮤텍스의](#mutex)|`mutex` 개체를 생성합니다.|
|[mutex:: ~ mutex 소멸자](#dtormutex_destructor)|`mutex` 개체에서 사용하는 리소스를 모두 해제합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.|
|[native_handle](#native_handle)|뮤텍스 핸들을 나타내는 특정 구현 형식을 반환합니다.|
|[try_lock](#try_lock)|차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.|
|[잠금을](#unlock)|`mutex`의 소유권을 해제합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<mutex>

**네임스페이스:** std

## <a name="mutexlock"></a><a name="lock"></a> mutex:: lock

스레드가 `mutex`의 소유권을 가져올 때까지 호출 스레드를 차단합니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a> mutex:: mutex 생성자

잠기지 않은 `mutex` 개체를 생성합니다.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a> mutex:: ~ mutex 소멸자

`mutex` 개체에서 사용하는 리소스를 모두 해제합니다.

```cpp
~mutex();
```

### <a name="remarks"></a>설명

소멸자가 실행될 때 개체가 잠겨 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="mutexnative_handle"></a><a name="native_handle"></a> mutex:: native_handle

뮤텍스 핸들을 나타내는 특정 구현 형식을 반환합니다. 뮤텍스 핸들은 구현별 방식으로 사용할 수 있습니다.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>반환 값

`native_handle_type`은 `void *`로 캐스팅된 `Concurrency::critical_section *`으로 정의됩니다.

## <a name="mutextry_lock"></a><a name="try_lock"></a> mutex:: try_lock

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
bool try_lock();
```

### <a name="return-value"></a>반환 값

**`true`** 메서드가의 소유권을 가져오면 `mutex` 이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

호출 스레드가 이미 `mutex`를 소유하고 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="mutexunlock"></a><a name="unlock"></a> mutex:: unlock

`mutex`의 소유권을 해제합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

호출 스레드가 `mutex`를 소유하지 않은 경우, 이 동작은 정의되지 않습니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
