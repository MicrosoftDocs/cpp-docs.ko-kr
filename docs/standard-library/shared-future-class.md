---
description: Shared_future 클래스에 대해 자세히 알아보세요.
title: shared_future 클래스
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 169e9c7aa906a788975852ae6a3f90a1b46213c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154086"
---
# <a name="shared_future-class"></a>shared_future 클래스

*비동기 반환 개체* 를 설명 합니다. [future](../standard-library/future-class.md) 개체와는 달리 `shared_future` 개체의 경우 원하는 수만큼 *비동기 공급자* 에 연결할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>설명

*비어 있는*`shared_future` 개체에 대해서는 `valid`, `operator=` 및 소멸자 이외의 메서드는 호출하지 마세요.

`shared_future` 개체는 동기화되지 않습니다. 여러 스레드에서 같은 개체에 대해 메서드를 호출하면 결과를 예측할 수 없는 데이터 경쟁이 발생합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[shared_future](#shared_future)|`shared_future` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get](#get)|*연결된 비동기 상태* 에 저장된 결과를 검색합니다.|
|[유효](#valid)|개체가 비어 있지 않은지 여부를 지정합니다.|
|[대기한](#wait)|연결된 비동기 상태가 ready로 설정될 때까지 현재 스레드를 차단합니다.|
|[wait_for](#wait_for)|연결된 비동기 상태가 준비로 설정되거나 지정된 시간이 경과할 때까지 차단합니다.|
|[wait_until](#wait_until)|연결된 비동기 상태가 준비로 설정되거나 지정된 시점이 될 때까지 차단합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|새 연결된 비동기 상태를 할당합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<future>

**네임스페이스:** std

## <a name="shared_futureget"></a><a name="get"></a> shared_future:: get

*연결된 비동기 상태* 에 저장된 결과를 검색합니다.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>설명

결과가 예외이면 메서드는 예외를 다시 throw합니다. 그렇지 않으면 결과가 반환됩니다.

이 메서드는 결과를 검색하기 전에 연결된 비동기 상태가 준비로 설정될 때까지 현재 스레드를 차단합니다.

부분 특수화의 경우 `shared_future<Ty&>` 저장 된 값은 실제로는 반환 값으로 *비동기 공급자* 에 전달 된 개체에 대 한 참조입니다.

특수화에 대해 저장 된 값이 없으므로 `shared_future<void>` 메서드는을 반환 합니다 **`void`** .

## <a name="shared_futureoperator"></a><a name="op_eq"></a> shared_future:: operator =

지정 된 개체에서 *연결 된 비동기 상태* 를 전송 합니다.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`shared_future` 개체입니다.

### <a name="return-value"></a>반환 값

`*this`

### <a name="remarks"></a>설명

첫 번째 연산자의 경우 작업 후에는 더 이상 연결 된 비동기 *상태가 없습니다.*

두 번째 메서드에서는 연결 된 비동기 상태를 *적절* 하 게 유지 합니다.

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a> shared_future:: shared_future 생성자

`shared_future` 개체를 생성합니다.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
[future](../standard-library/future-class.md) 또는 `shared_future` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `shared_future` *연결 된 비동기 상태가* 없는 개체를 생성 합니다.

두 번째 및 세 번째 생성자는 `shared_future` 개체를 생성 하 고 *오른쪽* 에서 연결 된 비동기 상태를 전송 합니다. *오른쪽* 에는 더 이상 연결 된 비동기 상태가 없습니다.

네 번째 생성자는 `shared_future` *Right* 와 연결 된 비동기 상태를 포함 하는 개체를 생성 합니다.

## <a name="shared_futurevalid"></a><a name="valid"></a> shared_future:: valid

개체에 *연결 된 비동기 상태가* 있는지 여부를 지정 합니다.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>반환 값

**`true`** 개체가 연결 된 비동기 상태 이면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="shared_futurewait"></a><a name="wait"></a> shared_future:: wait

*연결 된 비동기 상태가* *ready* 가 될 때까지 현재 스레드를 차단 합니다.

```cpp
void wait() const;
```

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 준비입니다.

## <a name="shared_futurewait_for"></a><a name="wait_for"></a> shared_future:: wait_for

연결된 비동기 상태가 *ready* 로 설정되거나 지정된 시간이 경과할 때까지 차단합니다.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>매개 변수

*Rel_time*\
스레드가 차단되는 최대 시간 간격을 지정하는 [chrono::duration](../standard-library/duration-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

반환 이유를 나타내는 [future_status](../standard-library/future-enums.md#future_status)입니다.

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 *준비* 입니다.

## <a name="shared_futurewait_until"></a><a name="wait_until"></a> shared_future:: wait_until

연결된 비동기 상태가 *준비* 가 되거나 지정된 시점이 지날 때까지 현재 스레드를 차단합니다.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>매개 변수

*Abs_time*\
스레드 차단을 해제할 수 있는 시간을 지정하는 [chrono::time_point](../standard-library/time-point-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

반환 이유를 나타내는 [future_status](../standard-library/future-enums.md#future_status)입니다.

### <a name="remarks"></a>설명

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 준비입니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
