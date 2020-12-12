---
description: '자세히 알아보기: 향후 클래스'
title: future 클래스
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: ca73a3d0273014c4f22e8e807c2bf7c3d6e43320
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324228"
---
# <a name="future-class"></a>future 클래스

*비동기 반환 개체* 를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>설명

각 표준 *비동기 공급자* 는 이 템플릿의 인스턴스화 형식이 포함된 개체를 반환합니다. 연결된 비동기 공급자에 액세스하려면 `future` 개체를 사용해야 합니다. 동일한 비동기 공급자와 연결된 여러 비동기 반환 개체가 필요할 경우 `future` 개체를 [shared_future](../standard-library/shared-future-class.md) 개체에 복사합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[생성](#future)|`future` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get](#get)|연결된 비동기 상태에 저장된 결과를 검색합니다.|
|[공유](#share)|개체를 `shared_future`로 변환합니다.|
|[유효](#valid)|개체가 비어 있지 않은지 여부를 지정합니다.|
|[대기한](#wait)|연결된 비동기 상태가 ready로 설정될 때까지 현재 스레드를 차단합니다.|
|[wait_for](#wait_for)|연결된 비동기 상태가 준비로 설정되거나 지정된 시간이 경과할 때까지 차단합니다.|
|[wait_until](#wait_until)|연결된 비동기 상태가 준비로 설정되거나 지정된 시점이 될 때까지 차단합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[future::operator=](#op_eq)|지정된 개체에서 연결된 비동기 상태를 전송합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<future>

**네임스페이스:** std

## <a name="futurefuture-constructor"></a><a name="future"></a> future:: future 생성자

`future` 개체를 생성합니다.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>매개 변수

*다른*\
`future` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 연결된 비동기 상태가 없는 `future` 개체를 구성합니다.

두 번째 생성자는 개체를 생성 `future` 하 고 *다른* 에서 연결 된 비동기 상태를 전송 합니다. *기타* 에는 더 이상 연결 된 비동기 상태가 없습니다.

## <a name="futureget"></a><a name="get"></a> future:: get

연결된 비동기 상태에 저장된 결과를 검색합니다.

```cpp
Ty get();
```

### <a name="return-value"></a>반환 값

결과가 예외이면 메서드는 예외를 다시 throw합니다. 그렇지 않으면 결과가 반환됩니다.

### <a name="remarks"></a>설명

이 메서드는 결과를 검색하기 전에 연결된 비동기 상태가 준비로 설정될 때까지 현재 스레드를 차단합니다.

부분 특수화 `future<Ty&>`의 경우 저장되는 값은 실제로는 반환 값으로 비동기 공급자에 전달된 개체에 대한 참조입니다.

특수화에 대해 저장 된 값이 없으므로 `future<void>` 메서드는을 반환 합니다 **`void`** .

다른 특수화에서 메서드는 저장된 값에서 반환 값을 이동합니다. 따라서 이 메서드를 한 번만 호출합니다.

## <a name="futureoperator"></a><a name="op_eq"></a> future:: operator =

지정된 개체에서 연결된 비동기 상태를 전송합니다.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`future` 개체입니다.

### <a name="return-value"></a>반환 값

`*this`

### <a name="remarks"></a>설명

전송 후에는 *오른쪽* 에 더 이상 연결 된 비동기 상태가 없습니다.

## <a name="futureshare"></a><a name="share"></a> future:: share

개체를 [shared_future](../standard-library/shared-future-class.md) 개체로 변환합니다.

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>반환 값

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a> future:: valid

개체에 연결된 비동기 상태가 있는지 여부를 지정합니다.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** 개체가 연결 된 비동기 상태 이면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="futurewait"></a><a name="wait"></a> 미래:: 대기

연결된 비동기 상태가 *준비* 로 설정될 때까지 현재 스레드를 차단합니다.

```cpp
void wait() const;
```

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 *준비* 입니다.

## <a name="futurewait_for"></a><a name="wait_for"></a> future:: wait_for

연결된 비동기 상태가 *준비* 로 설정되거나 지정된 시간 간격이 경과할 때까지 현재 스레드를 차단합니다.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>매개 변수

*Rel_time*\
스레드가 차단되는 최대 시간 간격을 지정하는 [chrono::duration](../standard-library/duration-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

반환 이유를 나타내는 [future_status](../standard-library/future-enums.md#future_status)입니다.

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 준비입니다.

## <a name="futurewait_until"></a><a name="wait_until"></a> future:: wait_until

연결된 비동기 상태가 *준비* 가 되거나 지정된 시점이 지날 때까지 현재 스레드를 차단합니다.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>매개 변수

*Abs_time*\
스레드 차단을 해제할 수 있는 시간을 지정하는 [chrono::time_point](../standard-library/time-point-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

반환 이유를 나타내는 [future_status](../standard-library/future-enums.md#future_status)입니다.

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 *준비* 입니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
