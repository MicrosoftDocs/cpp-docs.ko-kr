---
title: '&lt;thread&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: bb0a0a12ec2882701447804f9c88d1776a196cb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375845"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 함수

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[스왑](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

현재 실행 스레드를 고유하게 식별합니다.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Return Value

현재 실행 스레드를 고유하게 식별하는 [thread::id](../standard-library/thread-class.md) 형식의 개체입니다.

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

호출 스레드를 차단합니다.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>매개 변수

*Rel_time*\
시간 간격을 지정하는 [duration](../standard-library/duration-class.md) 개체입니다.

### <a name="remarks"></a>설명

함수는 *호출*스레드를 Rel_time 지정한 시간 동안 차단합니다. 이 함수는 예외를 throw하지 않습니다.

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

최소한 지정된 시간까지 호출 스레드를 차단합니다.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>매개 변수

*Abs_time*\
특정 시점을 나타냅니다.

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="swap"></a><a name="swap"></a>스왑

두 **스레드** 개체의 상태를 바꿉습니다.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
왼쪽 **스레드** 개체입니다.

*오른쪽*\
올바른 **스레드** 개체입니다.

### <a name="remarks"></a>설명

함수는 `Left.swap(Right)`을 호출합니다.

## <a name="yield"></a><a name="yield"></a>항복

정상적인 경우라면 현재 스레드가 계속 실행되더라도 운영 체제에 다른 스레드를 실행할 것을 알립니다.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>참고 항목

[\<스레드>](../standard-library/thread.md)
