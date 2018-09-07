---
title: promise 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: a56e188e581ea5d9dcafaa222ab4367e0b4b33fe
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100302"
---
# <a name="promise-class"></a>promise 클래스

*비동기 공급자*를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[promise](#promise)|`promise` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get_future](#get_future)|이 promise와 연관된 [future](../standard-library/future-class.md)를 반환합니다.|
|[set_exception](#set_exception)|예외를 나타내기 위해 이 promise의 결과를 원자 단위로 설정합니다.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|예외를 나타내기 위해 이 promise의 결과를 원자 단위로 설정하고 현재 스레드에 있는 모든 스레드 지역 개체가 제거된 후에만 통지를 전달합니다.|
|[set_value](#set_value)|이 promise의 결과를 원자 단위로 설정하여 값을 나타냅니다.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|값을 나타내기 위해 이 promise의 결과를 원자 단위로 설정하고 현재 스레드에 있는 모든 스레드 지역 개체가 제거된 후에만 통지를 전달합니다.|
|[swap](#swap)|이 promise의 *연결된 비동기 상태*를 지정한 개체의 연결된 비동기 상태와 교환합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[promise::operator=](#op_eq)|이 promise 개체의 공유 상태에 대한 할당입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

*promise*<br/>

## <a name="requirements"></a>요구 사항

**헤더:** \<향후 >

**네임스페이스:** std

## <a name="get_future"></a>  promise::get_future

이 promise와 동일한 *연결된 비동기 상태*가 있는 [future](../standard-library/future-class.md) 개체를 반환합니다.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>설명

promise 개체가 비어 있는 경우 이 메서드는 [error_code](../standard-library/error-code-class.md)가 `no_state`인 [future_error](../standard-library/future-error-class.md)를 throw합니다.

이 메서드가 연결된 비동기 상태가 동일한 promise 개체를 위해 호출된 경우 `future_error`가 `error_code`인 `future_already_retrieved`를 thorw합니다.

## <a name="op_eq"></a>  promise::operator=

지정된 `promise` 개체에서 *연결된 비동기 상태*를 전송합니다.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

*기타*<br/>
`promise` 개체입니다.

### <a name="return-value"></a>반환 값

`*this`

### <a name="remarks"></a>설명

이 연산자 전송에서 연결된 된 비동기 상태 *다른*합니다. 전송 후 *다른* 됩니다 *빈*합니다.

## <a name="promise"></a>  promise::promise 생성자

`promise` 개체를 생성합니다.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

*Al*<br/>
메모리 할당자입니다. 자세한 내용은 [\<allocators>](../standard-library/allocators-header.md)를 참조하세요.

*기타*<br/>
`promise` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 *빈* `promise` 개체를 생성합니다.

두 번째 생성자는 빈 생성 `promise` 사용 하 여 개체 *Al* 메모리 할당에 대 한 합니다.

세 번째 생성자 구문을 `promise` 개체와 연결된 된 비동기 상태에서 전송 *다른*, 커지고 *다른* 빈 합니다.

## <a name="set_exception"></a>  promise::set_exception

이 `promise` 개체의 결과로 예외를 원자 단위로 저장하고 *연결된 비동기 상태*를 *ready*로 설정합니다.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>매개 변수

*전용*<br/>
이 메서드가 예외 결과로 저장한 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)입니다.

### <a name="remarks"></a>설명

`promise` 개체에 연결된 비동기 상태가 없는 경우 이 메서드는 오류 코드가 `no_state`인 [future_error](../standard-library/future-error-class.md)를 throw합니다.

`set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) 또는 [set_value_at_thread_exit](#set_value_at_thread_exit)가 동일한 연관 비동기 상태의 `promise` 개체에 대해 이미 호출된 경우 이 메서드는 오류 코드가 `promise_already_satisfied`인 `future_error`를 throw합니다.

이 메서드의 결과로 연결된 비동기 상태에서 차단된 모든 스레드의 차단은 해제됩니다.

## <a name="set_exception_at_thread_exit"></a>  promise::set_exception_at_thread_exit

이 `promise`의 결과를 원자 단위로 예외로 설정하여 현재 스레드의 스레드 로컬 개체가 모두 소멸된 후에만 통지를 전달합니다.

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>매개 변수

*전용*<br/>
이 메서드가 예외 결과로 저장한 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)입니다.

### <a name="remarks"></a>설명

promise 개체에 *연결된 비동기 상태*가 없는 경우 이 메서드는 오류 코드가 `no_state`인 [future_error](../standard-library/future-error-class.md)를 throw합니다.

[set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value) 또는 [set_value_at_thread_exit](#set_value_at_thread_exit)가 동일한 연관 비동기 상태의 `promise` 개체에 대해 호출된 경우 이 메서드는 오류 코드가 `promise_already_satisfied`인 `future_error`를 throw합니다.

[set_exception](#set_exception)과 달리 이 메서드는 현재 스레드에서 모든 스레드 로컬 개체가 제거될 때까지 연결된 비동기 상태를 ready로 설정하지 않습니다. 일반적으로 연관된 비동기 상태에서 차단된 스레드는 현재 스레드가 종료될 때까지 차단 해제되지 않습니다.

## <a name="set_value"></a>  promise::set_value

이 `promise` 개체의 결과로 값을 원자 단위로 저장하고 *연결된 비동기 상태*를 *ready*로 설정합니다.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>매개 변수

*val*<br/>
결과로 저장할 값입니다.

### <a name="remarks"></a>설명

`promise` 개체에 연결된 비동기 상태가 없는 경우 이 메서드는 오류 코드가 `no_state`인 [future_error](../standard-library/future-error-class.md)를 throw합니다.

[set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` 또는 [set_value_at_thread_exit](#set_value_at_thread_exit)가 동일한 연관 비동기 상태의 `promise` 개체에 대해 이미 호출된 경우 이 메서드는 오류 코드가 `promise_already_satisfied`인 `future_error`를 throw합니다.

이 메서드의 결과로 연결된 비동기 상태에서 차단된 모든 스레드의 차단은 해제됩니다.

첫 번째 메서드는 또한 때 throw 되는 모든 예외 throw *Val* 연결된 된 비동기 상태에 복사 됩니다. 이 경우 연결된 비동기 상태는 ready로 설정되지 않습니다.

두 번째 방법은 또한 때 throw 되는 모든 예외를 throw *Val* 연결 된 비동기 상태로 이동 됩니다. 이 경우 연결된 비동기 상태는 ready로 설정되지 않습니다.

부분 특수화에 대 한 `promise<Ty&>`에 저장된 된 값은 적용에 대 한 참조가 *Val*합니다.

특수화 `promise<void>`에 대해 저장된 값은 없습니다.

## <a name="set_value_at_thread_exit"></a>  promise::set_value_at_thread_exit

이 `promise` 개체의 결과로 값을 원자 단위로 저장합니다.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>매개 변수

*val*<br/>
결과로 저장할 값입니다.

### <a name="remarks"></a>설명

promise 개체에 *연결된 비동기 상태*가 없는 경우 이 메서드는 오류 코드가 `no_state`인 [future_error](../standard-library/future-error-class.md)를 throw합니다.

[set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) 또는 `set_value_at_thread_exit`가 동일한 연관 비동기 상태의 `promise` 개체에 대해 호출된 경우 이 메서드는 오류 코드가 `promise_already_satisfied`인 `future_error`를 throw합니다.

`set_value`와 달리 이 메서드는 현재 스레드에서 모든 스레드 로컬 개체가 제거될 때까지 연결된 비동기 상태를 ready로 설정하지 않습니다. 일반적으로 연관된 비동기 상태에서 차단된 스레드는 현재 스레드가 종료될 때까지 차단 해제되지 않습니다.

첫 번째 메서드는 또한 때 throw 되는 모든 예외 throw *Val* 연결된 된 비동기 상태에 복사 됩니다.

두 번째 방법은 또한 때 throw 되는 모든 예외를 throw *Val* 연결 된 비동기 상태로 이동 됩니다.

부분 특수화 `promise<Ty&>`에 저장 된 값에 대 한 참조는 사실상 *Val*합니다.

특수화 `promise<void>`에 대해 저장된 값은 없습니다.

## <a name="swap"></a>  promise::swap

이 promise 개체의 *연결된 비동기 상태*를 지정한 개체의 연결된 비동기 상태와 교환합니다.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

*기타*<br/>
`promise` 개체입니다.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
