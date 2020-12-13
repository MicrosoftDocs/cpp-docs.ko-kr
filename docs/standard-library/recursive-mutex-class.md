---
description: Recursive_mutex 클래스에 대해 자세히 알아보세요.
title: recursive_mutex 클래스
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: f8a9c9322407871984c83135eecd2e26ac475d2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337895"
---
# <a name="recursive_mutex-class"></a>recursive_mutex 클래스

*뮤텍스 형식을* 나타냅니다. [mutex](../standard-library/mutex-class-stl.md)와 달리 이미 잠겨 있는 개체에 대한 잠금 메서드 호출 동작은 적절하게 정의됩니다.

## <a name="syntax"></a>구문

```cpp
class recursive_mutex;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|`recursive_mutex` 개체를 생성합니다.|
|[~recursive_mutex 소멸자](#dtorrecursive_mutex_destructor)|`recursive_mutex` 개체에서 사용하는 리소스를 모두 해제합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|스레드가 뮤텍스의 소유권을 가져올 때까지 호출 스레드를 차단합니다.|
|[try_lock](#try_lock)|차단되지 않고 뮤텍스의 소유권을 가져오려고 시도합니다.|
|[잠금을](#unlock)|뮤텍스의 소유권을 해제합니다.|

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

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a> recursive_mutex

잠기지 않은 `recursive_mutex` 개체를 생성합니다.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

개체에서 사용하는 리소스를 모두 해제합니다.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>설명

소멸자가 실행될 때 개체가 잠겨 있는 경우, 이 동작은 정의되지 않습니다.

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

차단되지 않고 `mutex`의 소유권을 가져오려고 시도합니다.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** 메서드가 성공적으로의 소유권을 얻거나 `mutex` 호출 스레드가를 이미 소유 하 고 있는 경우에는 `mutex**; otherwise, **false` 입니다.

### <a name="remarks"></a>설명

호출 스레드가를 이미 소유 하 `mutex` 고 있으면 함수는를 즉시 반환 **`true`** 하며 이전 잠금은 적용 된 상태로 유지 됩니다.

## <a name="unlock"></a><a name="unlock"></a> 잠금을

뮤텍스의 소유권을 해제합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

이 메서드는 `recursive_mutex` 개체에 대해 [lock](#lock) 및 [try_lock](#try_lock)이 정상적으로 호출된 횟수만큼 호출된 후에만 `mutex`의 소유권을 해제합니다.

호출 스레드가 `mutex`를 소유하지 않은 경우, 이 동작은 정의되지 않습니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
