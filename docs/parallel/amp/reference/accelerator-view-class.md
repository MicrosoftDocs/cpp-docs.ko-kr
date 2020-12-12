---
description: Accelerator_view 클래스에 대해 자세히 알아보세요.
title: accelerator_view 클래스
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 2d17c856b988ffd759c73e2f4c039cbdf8b5d24f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254510"
---
# <a name="accelerator_view-class"></a>accelerator_view 클래스

데이터 병렬 가속기 C++ AMP의 가상 장치 추상화를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class accelerator_view;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[accelerator_view 생성자](#ctor)|`accelerator_view` 클래스의 새 인스턴스를 초기화합니다.|
|[~ accelerator_view 소멸자](#dtor)|개체를 소멸 시킵니다 `accelerator_view` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[create_marker](#create_marker)|지금까지이 개체에 전송 된 모든 명령의 완료를 추적 하는 미래를 반환 합니다 `accelerator_view` .|
|[플러시가](#flush)|개체에 대기 중인 모든 보류 중인 명령을 실행을 위해 액셀러레이터에 전송 합니다 `accelerator_view` .|
|[get_accelerator](#get_accelerator)|`accelerator` 개체의 `accelerator_view` 개체를 반환합니다.|
|[get_is_auto_selection](#get_is_auto_selection)|`accelerator_view`개체가 [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)에 전달 될 때 런타임에서 적절 한 액셀러레이터를 자동으로 선택 하는지 여부를 나타내는 부울 값을 반환 합니다.|
|[get_is_debug](#get_is_debug)|`accelerator_view`개체에 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있는지 여부를 나타내는 부울 값을 반환 합니다.|
|[get_queuing_mode](#get_queuing_mode)|개체의 큐 모드를 반환 `accelerator_view` 합니다.|
|[get_version](#get_version)|의 버전을 반환 합니다 `accelerator_view` .|
|[대기한](#wait)|개체에 전송 된 모든 명령이 완료 될 때까지 기다립니다 `accelerator_view` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자! =](#operator_neq)|이 `accelerator_view` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`false`** , 그렇지 않으면를 반환 **`true`** 합니다.|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `accelerator_view` 여기로 복사 합니다.|
|[연산자 = =](#operator_eq_eq)|이 `accelerator_view` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`true`** , 그렇지 않으면를 반환 **`false`** 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[accelerator](#accelerator)|`accelerator` 개체의 `accelerator_view` 개체를 가져옵니다.|
|[is_auto_selection](#is_auto_selection)|`accelerator_view`개체가 [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)에 전달 될 때 런타임에서 적절 한 액셀러레이터를 자동으로 선택 하는지 여부를 나타내는 부울 값을 가져옵니다.|
|[is_debug](#is_debug)|`accelerator_view`개체에 확장 오류 보고를 위해 디버그 계층이 활성화 되어 있는지 여부를 나타내는 부울 값을 가져옵니다.|
|[queuing_mode](#queuing_mode)|개체의 큐 모드를 가져옵니다 `accelerator_view` .|
|[version](#version)|엑셀러레이터의 버전을 가져옵니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`accelerator_view`

### <a name="remarks"></a>설명

`accelerator_view`개체는 액셀러레이터 키의 논리적 격리 된 뷰를 나타냅니다. 단일 물리적 계산 장치에는 여러 개의 논리적 격리 된 개체가 있을 수 있습니다 `accelerator_view` . 각 액셀러레이터에는 기본 `accelerator_view` 개체가 있습니다. 추가 `accelerator_view` 개체를 만들 수 있습니다.

여러 클라이언트 스레드 간에 물리적 장치를 공유할 수 있습니다. 클라이언트 스레드는 액셀러레이터의 동일한 개체를 협조적으로 사용할 수 있으며 `accelerator_view` , 각 클라이언트는 `accelerator_view` 다른 클라이언트 스레드와 격리 하기 위해 독립 개체를 통해 계산 장치와 통신할 수 있습니다.

개체에는 `accelerator_view` 두 가지 [queuing_mode 열거형](concurrency-namespace-enums-amp.md#queuing_mode) 상태 중 하나가 있을 수 있습니다. 큐 모드가 인 경우 `immediate` 및와 같은 명령이 `copy` `parallel_for_each` 호출자에 게 반환 되는 즉시 해당 액셀러레이터 장치로 전송 됩니다. 큐 모드가 인 경우 해당 `deferred` 명령은 개체에 해당 하는 명령 큐에 대기 됩니다 `accelerator_view` . 가 호출 될 때 까지는 명령이 실제로 장치로 전송 되지 않습니다 `flush()` .

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임스페이스:** 동시성

## <a name="accelerator"></a><a name="accelerator"></a> accelerator

Accelerator_view 개체에 대 한 액셀러레이터 개체를 가져옵니다.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a> accelerator_view

기존 개체를 복사 하 여 accelerator_view 클래스의 새 인스턴스를 초기화 `accelerator_view` 합니다.

### <a name="syntax"></a>구문

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
복사할 `accelerator_view` 개체입니다.

## <a name="create_marker"></a><a name="create_marker"></a> create_marker

지금까지이 개체에 전송 된 모든 명령의 완료를 추적 하는 미래를 반환 합니다 `accelerator_view` .

### <a name="syntax"></a>구문

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Return Value

지금까지이 개체에 전송 된 모든 명령의 완료를 추적 하는 미래입니다 `accelerator_view` .

## <a name="flush"></a>flush

accelerator_view 개체의 큐에 대기 중인 모든 보류 중인 명령은 실행을 위한 엑셀러레이터에 전송합니다.

### <a name="syntax"></a>구문

```cpp
void flush();
```

### <a name="return-value"></a>Return Value

**`void`** 을 반환 합니다.

## <a name="get_accelerator"></a><a name="get_accelerator"></a> get_accelerator

Accelerator_view 개체에 대 한 액셀러레이터 개체를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Return Value

Accelerator_view 개체에 대 한 액셀러레이터 키 개체입니다.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a> get_is_auto_selection

Accelerator_view [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)에 전달 될 때 런타임에서 적절 한 액셀러레이터를 자동으로 선택 하는지 여부를 나타내는 부울 값을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Return Value

**`true`** 런타임에 적절 한 액셀러레이터 키가 자동으로 선택 되 면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="get_is_debug"></a><a name="get_is_debug"></a> get_is_debug

accelerator_view 개체에 확장 오류 보고를 위해 DEBUG 레이어가 활성화되었는지 여부를 나타내는 부울 값을 반환합니다.

### <a name="syntax"></a>구문

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Return Value

`accelerator_view` 개체에 확장 오류 보고를 위해 DEBUG 레이어가 활성화되었는지 여부를 나타내는 부울 값입니다.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a> get_queuing_mode

accelerator_view 개체의 큐 모드를 반환합니다.

### <a name="syntax"></a>구문

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Return Value

`accelerator_view` 개체의 큐 모드입니다.

## <a name="get_version"></a><a name="get_version"></a> get_version

accelerator_view의 버전을 반환합니다.

### <a name="syntax"></a>구문

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Return Value

`accelerator_view`의 버전입니다.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a> is_auto_selection

Accelerator_view [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)에 전달 될 때 런타임에서 적절 한 액셀러레이터를 자동으로 선택 하는지 여부를 나타내는 부울 값을 가져옵니다.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a> is_debug

accelerator_view 개체에 확장 오류 보고를 위해 DEBUG 레이어가 활성화되었는지 여부를 나타내는 부울 값을 가져옵니다.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a> 연산자! =

이 accelerator_view 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`false`** , 그렇지 않으면를 반환 **`true`** 합니다.

### <a name="syntax"></a>구문

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
이것과 비교할 `accelerator_view` 개체입니다.

### <a name="return-value"></a>반환 값

**`false`** 두 개체가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`true`** 입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 accelerator_view 개체의 내용을이 개체에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
`accelerator_view`복사할 개체입니다.

### <a name="return-value"></a>반환 값

수정된 `accelerator_view` 개체에 대한 참조입니다.

## <a name="operator"></a><a name="operator_eq_eq"></a> 연산자 = =

이 accelerator_view 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`true`** , 그렇지 않으면를 반환 **`false`** 합니다.

### <a name="syntax"></a>구문

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
이것과 비교할 `accelerator_view` 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 두 개체가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="queuing_mode"></a><a name="queuing_mode"></a> queuing_mode

Accelerator_view 개체의 큐 모드를 가져옵니다.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>버전

accelerator_view의 버전을 가져옵니다.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

Accelerator_view 개체에 전송 된 모든 명령이 완료 될 때까지 기다립니다.

### <a name="syntax"></a>구문

```cpp
void wait();
```

### <a name="return-value"></a>Return Value

**`void`** 을 반환 합니다.

### <a name="remarks"></a>설명

[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) 이면 `immediate` 이 메서드는 차단 없이 즉시 반환 됩니다.

## <a name="accelerator_view"></a><a name="dtor"></a> ~ accelerator_view

Accelerator_view 개체를 소멸 시킵니다.

### <a name="syntax"></a>구문

```cpp
~accelerator_view();
```

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
