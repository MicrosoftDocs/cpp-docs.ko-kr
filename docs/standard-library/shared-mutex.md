---
description: '자세히 알아보기: &lt; shared_mutex>'
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: 97446b3709dd71b49389fa63ac067f7cc9ccf820
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154066"
---
# <a name="ltshared_mutex"></a>&lt;shared_mutex>

&lt;Shared_mutex> 헤더는 여러 스레드에서 액세스할 수 있는 공유 데이터의 보호를 위한 동기화 기본 형식을 제공 합니다. 공유 mutex 클래스에서는 mutex 클래스가 제공하는 독점적 액세스 제어 기능을 사용할 수 있을 뿐 아니라, 비독점적 액세스를 위해 여러 스레드가 소유권을 공유할 수도 있습니다. 공유 뮤텍스를 사용하면 경쟁 조건을 발생시키지 않고 여러 스레드가 읽을 수 있는 동시에 스레드 하나가 독점적으로 쓸 수 있어야 하는리소스를 제어할 수 있습니다.

헤더 &lt; shared_mutex>는 클래스 `shared_mutex` 및 `shared_timed_mutex` , 클래스 템플릿 `shared_lock` 및 `swap` 공유 뮤텍스 지원을 위한 템플릿 함수를 정의 합니다.

|클래스|설명|
|-------------|-----------------|
|[shared_mutex 클래스](#class_shared_mutex)|에이전트 하나가 독점적으로 잠그거나 여러 에이전트가 비독점적으로 공유할 수 있는 공유 뮤텍스 형식입니다.|
|[shared_timed_mutex 클래스](#class_shared_timed_mutex)|에이전트 하나가 독점적으로 잠그거나 여러 에이전트가 비독점적으로 공유할 수 있는 시간이 지정된 공유 뮤텍스 형식입니다.|
|[shared_lock 클래스](#class_shared_lock)|시간이 지정 된 잠금 작업을 지원 하 고 여러 에이전트가 배타로 공유 하지 않도록 공유 뮤텍스를 래핑하는 클래스 템플릿입니다.|

|함수|설명|
|---------------|-----------------|
|[스왑을](#function_swap)|함수 매개 변수에서 참조하는 공유 뮤텍스 개체의 콘텐츠를 교환합니다.|

## <a name="syntax"></a>구문

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>설명

클래스 `shared_mutex`의 인스턴스는 범위 내 뮤텍스의 공유 소유권을 제어하는 형식인 *공유 뮤텍스 형식* 입니다. 공유 뮤텍스 형식은 뮤텍스 형식의 모든 요구 사항을 충족할 뿐 아니라 비독점적 공유 소유권 지원을 위한 구성원도 포함합니다.

공유 뮤텍스 형식은 추가 메서드 `lock_shared`, `unlock_shared` 및 `try_lock_shared`를 지원합니다.

- `lock_shared` 메서드는 스레드가 뮤텍스의 공유 소유권을 가져올 때까지 호출 스레드를 차단합니다.

- `unlock_shared` 메서드는 스레드를 호출하여 가져온 뮤텍스의 공유 소유권을 해제합니다.

- `try_lock_shared` 메서드는 차단 없이 뮤텍스에 대한 공유 소유권을 가져오려고 시도합니다. 반환 형식은로 변환할 수 **`bool`** 있으며, **`true`** 메서드가 소유권을 가져오면이 고, 그렇지 않으면입니다 **`false`** .

`shared_timed_mutex` 클래스는 공유 뮤텍스 형식과 시간이 지정된 뮤텍스 형식의 요구 사항을 모두 충족하는 *시간이 지정된 공유 뮤텍스 형식* 입니다.

시간이 지정된 공유 뮤텍스 형식은 추가 메서드 `try_lock_shared_for` 및 `try_lock_shared_until`을 지원합니다.

- `try_lock_shared_for` 메서드는 매개 변수에 의해 지정된 기간이 경과할 때까지 뮤텍스의 공유 소유권을 가져오려고 합니다. 기간이 양수가 아닌 경우 메서드는 `try_lock_shared`와 동일합니다. 공유 소유권을 가져오는 경우가 아니면 메서드는 지정된 기간 내에 결과를 반환하지 않습니다. 반환 값은 **`true`** 메서드가 소유권을 가져오는 경우이 고 그렇지 않은 경우입니다 **`false`** .

- `try_lock_shared_until` 메서드는 지정된 절대 시간이 경과할 때까지 뮤텍스의 공유 소유권을 가져오려고 합니다. 지정한 시간이 이미 지난 경우 메서드는 `try_lock_shared`와 동일합니다. 공유 소유권을 가져오는 경우가 아니면 메서드는 지정된 기간 이전에 결과를 반환하지 않습니다. 반환 값은 **`true`** 메서드가 소유권을 가져오는 경우이 고 그렇지 않은 경우입니다 **`false`** .

`shared_lock`클래스 템플릿은 공유 뮤텍스로의 제한 된 잠금 및 소유권 전송에 대 한 지원을 확장 합니다. 뮤텍스의 소유권은 생성 시나 생성 후에 가져와서 다른 `shared_lock` 개체로 전송할 수 있습니다. `shared_lock` 형식의 개체는 이동할 수는 있지만 복사할 수는 없습니다.

> [!WARNING]
> Visual Studio 2015부터 c + + 표준 라이브러리 동기화 형식은 Windows 동기화 기본 형식을 기반으로 하며, 더 이상 ConcRT를 사용 하지 않습니다 (대상 플랫폼이 Windows XP 인 경우 제외). Shared_mutex>에 정의 된 형식은 &lt; 모든 ConcRT 형식 또는 함수와 함께 사용 하면 안 됩니다.

## <a name="classes"></a>클래스

### <a name="shared_mutex-class"></a><a name="class_shared_mutex"></a> shared_mutex 클래스

`shared_mutex` 클래스는 공유 소유권 의미 체계를 사용한 비재귀적 뮤텍스를 구현합니다.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

### <a name="shared_timed_mutex-class"></a><a name="class_shared_timed_mutex"></a> shared_timed_mutex 클래스

`shared_timed_mutex` 클래스는 시간이 지정된 뮤텍스 형식의 요구 사항을 충족하는 공유 소유권 의미 체계를 사용하여 비재귀적 뮤텍스를 구현합니다.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

### <a name="shared_lock-class"></a><a name="class_shared_lock"></a> shared_lock 클래스

클래스 템플릿은 `shared_lock` 범위 내에서 공유 뮤텍스 개체의 공유 소유권을 제어 합니다. 템플릿 매개 변수는 공유 뮤텍스 형식이어야 합니다.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>함수

### <a name="swap"></a><a name="function_swap"></a> 스왑을

`shared_lock` 개체를 교환합니다.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

두 `shared_lock` 개체의 내용을 교환합니다. 실제로는 `x.swap(y)`과 동일합니다.

## <a name="requirements"></a>요구 사항

**헤더:** &lt;shared_mutex>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[&lt;뮤텍스>](../standard-library/mutex.md)
