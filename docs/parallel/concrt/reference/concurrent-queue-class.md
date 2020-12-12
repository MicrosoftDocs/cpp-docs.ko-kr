---
description: Concurrent_queue 클래스에 대해 자세히 알아보세요.
title: concurrent_queue 클래스
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: c7ac9686b03073016b509ce8e2bddaa664c3141f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250610"
---
# <a name="concurrent_queue-class"></a>concurrent_queue 클래스

`concurrent_queue` 클래스는 해당 요소에 대해 선입 선출 액세스를 허용하는 시퀀스 컨테이너 클래스입니다. `push` 및 `try_pop`과 같은 동시성으로부터 안전한 작업의 제한된 집합을 사용할 수 있게 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다.

## <a name="syntax"></a>구문

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
큐에 저장 되는 요소의 데이터 형식입니다.

*_Ax*<br/>
이 동시 큐의 메모리 할당 및 할당 취소에 대 한 세부 정보를 캡슐화 하는 저장 된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<T>`입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`allocator_type`|동시 큐의 할당자 클래스를 나타내는 형식입니다.|
|`const_iterator`|**`const`** 동시 큐의 요소에 대 한 스레드로부터 안전 하지 않은 반복기를 나타내는 형식입니다.|
|`const_reference`|**`const`** 작업을 읽고 수행 하기 위해 동시 큐에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|`difference_type`|동시 큐의 두 요소 사이에 부호 있는 거리를 제공 하는 형식입니다.|
|`iterator`|동시 큐의 요소에 대 한 스레드로부터 안전 하지 않은 반복기를 나타내는 형식입니다.|
|`reference`|동시 큐에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다.|
|`size_type`|동시 큐의 요소 수를 계산 하는 형식입니다.|
|`value_type`|동시 큐에 저장 된 데이터 형식을 나타내는 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[concurrent_queue](#ctor)|오버로드됨. 동시 큐를 생성 합니다.|
|[~ concurrent_queue 소멸자](#dtor)|동시 큐를 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[clear](#clear)|현재 큐에 있는 모든 요소를 삭제 하 여 동시 큐를 지웁니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[empty](#empty)|이 메서드가 호출 될 때 동시 큐가 비어 있는지 테스트 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[get_allocator](#get_allocator)|동시 큐를 생성 하는 데 사용 되는 할당자의 복사본을 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[push](#push)|오버로드됨. 동시 큐의 비상 끝에 있는 항목을 큐 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[try_pop](#try_pop)|큐에서 항목을 큐에서 제거 합니다 (사용 가능한 경우). 이 메서드는 동시성이 보장 됩니다.|
|[unsafe_begin](#unsafe_begin)|오버로드됨. 또는 형식의 반복기를 `iterator` `const_iterator` 동시 큐의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[unsafe_end](#unsafe_end)|오버로드됨. 또는 형식의 반복기를 `iterator` `const_iterator` 동시 큐의 끝에 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[unsafe_size](#unsafe_size)|큐에 있는 항목의 수를 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|

## <a name="remarks"></a>설명

자세한 내용은 [병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`concurrent_queue`

## <a name="requirements"></a>요구 사항

**헤더:** concurrent_queue. h

**네임 스페이스:** 동시성

## <a name="clear"></a><a name="clear"></a> 해제

현재 큐에 있는 모든 요소를 삭제 하 여 동시 큐를 지웁니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void clear();
```

## <a name="concurrent_queue"></a><a name="ctor"></a> concurrent_queue

동시 큐를 생성 합니다.

```cpp
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>매개 변수

*_InputIterator*<br/>
값 범위를 지정 하는 입력 반복기의 형식입니다.

*_Al*<br/>
이 개체에 사용할 할당자 클래스입니다.

*_OtherQ*<br/>
요소를 복사해 오거나 이동해 올 소스 `concurrent_queue` 개체입니다.

*_Begin*<br/>
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*_End*<br/>
복사할 요소의 범위를 벗어난 첫 번째 요소의 위치입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체를 저장 `_Al` 하 고 큐를 초기화 합니다.

첫 번째 생성자는 빈 초기 큐를 지정 하 고 사용할 할당자 형식을 명시적으로 지정 합니다.

두 번째 생성자는 동시 큐의 복사본을 지정 합니다 `_OtherQ` .

세 번째 생성자는 동시 큐 `_OtherQ`의 이동을 지정합니다.

네 번째 생성자는 반복기 범위 [,)에서 제공 하는 값을 지정 합니다 `_Begin` `_End` .

## <a name="concurrent_queue"></a><a name="dtor"></a> ~ concurrent_queue

동시 큐를 소멸 시킵니다.

```cpp
~concurrent_queue();
```

## <a name="empty"></a><a name="empty"></a> 비우려면

이 메서드가 호출 될 때 동시 큐가 비어 있는지 테스트 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 동시 큐가 검색 된 순간에 비어 있으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

이 메서드는, 및 메서드 호출에 대해 동시성이 보장 되지만 반환 되 `push` 는 `try_pop` `empty` 값은 호출 스레드에서 검사 된 시간에 따라 올바르지 않을 수 있습니다.

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

동시 큐를 생성 하는 데 사용 되는 할당자의 복사본을 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

동시 큐를 생성 하는 데 사용 되는 할당자의 복사본입니다.

## <a name="push"></a><a name="push"></a> 누르기

동시 큐의 비상 끝에 있는 항목을 큐 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>매개 변수

*_Src*<br/>
큐에 추가할 항목입니다.

### <a name="remarks"></a>설명

`push` 는, 및 메서드 호출에 대해 동시성이 보장 됩니다 `push` `try_pop` `empty` .

## <a name="try_pop"></a><a name="try_pop"></a> try_pop

큐에서 항목을 큐에서 제거 합니다 (사용 가능한 경우). 이 메서드는 동시성이 보장 됩니다.

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>매개 변수

*_Dest*<br/>
큐에서 제거 된 항목을 저장할 위치에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

**`true`** 항목이 성공적으로 큐에서 제거 되었으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

항목이 성공적으로 큐에서 제거 된 경우 매개 변수는 `_Dest` 큐에서 제거 된 값을 수신 하 고, 큐에 보관 된 원래 값이 제거 되 고,이 함수는를 반환 **`true`** 합니다. 큐에서 제거할 항목이 없는 경우이 함수는 **`false`** 를 차단 하지 않고 반환 하며 `_Dest` 매개 변수 내용이 정의 되지 않습니다.

`try_pop` 는, 및 메서드 호출에 대해 동시성이 보장 됩니다 `push` `try_pop` `empty` .

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a> unsafe_begin

또는 형식의 반복기를 `iterator` `const_iterator` 동시 큐의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 동시 큐 개체의 시작 부분에 있는 또는 형식의 반복기입니다.

### <a name="remarks"></a>설명

클래스에 대 한 반복기는 `concurrent_queue` 주로 디버깅을 위한 것 이며, 속도가 느리고 반복은 다른 큐 작업과 관련 하 여 동시성이 보장 되지 않습니다.

## <a name="unsafe_end"></a><a name="unsafe_end"></a> unsafe_end

또는 형식의 반복기를 `iterator` `const_iterator` 동시 큐의 끝에 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 동시 큐의 끝에 있는 형식의 반복기 또는입니다.

### <a name="remarks"></a>설명

클래스에 대 한 반복기는 `concurrent_queue` 주로 디버깅을 위한 것 이며, 속도가 느리고 반복은 다른 큐 작업과 관련 하 여 동시성이 보장 되지 않습니다.

## <a name="unsafe_size"></a><a name="unsafe_size"></a> unsafe_size

큐에 있는 항목의 수를 반환 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>반환 값

동시 큐의 크기입니다.

### <a name="remarks"></a>설명

`unsafe_size` 는 동시성이 안전 하지 않으며, 및 메서드를 호출 하 여 동시에 호출 된 경우 잘못 된 결과를 생성할 수 있습니다 `push` `try_pop` `empty` .

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
