---
description: Concurrent_vector 클래스에 대해 자세히 알아보세요.
title: concurrent_vector 클래스
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: c4149fc52d726cc5beea487c8ad24960c3698abd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189121"
---
# <a name="concurrent_vector-class"></a>concurrent_vector 클래스

`concurrent_vector` 클래스는 모든 요소에 대해 임의 액세스를 허용하는 시퀀스 컨테이너 클래스입니다. 동시성으로부터 안전한 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 사용할 수 있게 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다.

## <a name="syntax"></a>구문

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
벡터에 저장 되는 요소의 데이터 형식입니다.

*_Ax*<br/>
동시 벡터의 메모리 할당 및 할당 취소에 대 한 세부 정보를 캡슐화 하는 저장 된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이며 기본값은 `allocator<T>`입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`allocator_type`|동시 벡터의 할당자 클래스를 나타내는 형식입니다.|
|`const_iterator`|동시 벡터의 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|`const_pointer`|동시 벡터의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|`const_reference`|**`const`** 작업을 읽고 수행 하기 위해 동시 벡터에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다 **`const`** .|
|`const_reverse_iterator`|동시 벡터의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다 **`const`** .|
|`difference_type`|동시 벡터의 두 요소 사이에 부호 있는 거리를 제공 하는 형식입니다.|
|`iterator`|동시 벡터의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다. 반복기를 사용 하는 요소 수정은 동시성이 안전 하지 않습니다.|
|`pointer`|동시 벡터의 요소에 대 한 포인터를 제공 하는 형식입니다.|
|`reference`|동시 벡터에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다.|
|`reverse_iterator`|역방향 동시 벡터의 모든 요소를 읽을 수 있는 임의 액세스 반복기를 제공 하는 형식입니다. 반복기를 사용 하는 요소 수정은 동시성이 안전 하지 않습니다.|
|`size_type`|동시 벡터의 요소 수를 계산 하는 형식입니다.|
|`value_type`|동시 벡터에 저장 된 데이터 형식을 나타내는 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[concurrent_vector](#ctor)|오버로드됨. 동시 벡터를 생성 합니다.|
|[~ concurrent_vector 소멸자](#dtor)|모든 요소를 지우고이 동시 벡터를 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[assign](#assign)|오버로드됨. 동시 벡터의 요소를 지우고 `_N` 의 복사본 `_Item` 또는 반복기 범위 [,)로 지정 된 값에 할당 `_Begin` `_End` 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[at](#at)|오버로드됨. 동시 벡터의 지정 된 인덱스에 있는 요소에 대 한 액세스를 제공 합니다. 이 메서드는 읽기 작업에 대해 동시성이 보장 되며, 값이 `_Index` 동시 벡터의 크기 보다 작음을 확인 한 경우 벡터가 증가 하는 동안에도 벡터를 확장 합니다.|
|[뒤로](#back)|오버로드됨. 참조 또는 **`const`** 동시 벡터의 마지막 요소에 대 한 참조를 반환 합니다. 동시 벡터가 비어 있으면 반환 값은 정의 되지 않습니다. 이 메서드는 동시성이 보장 됩니다.|
|[시작](#begin)|오버로드됨. 또는 형식의 반복기를 `iterator` `const_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[수용](#capacity)|더 많은 메모리를 할당 하지 않고도 동시 벡터가 증가 될 수 있는 최대 크기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[cbegin](#cbegin)|형식의 반복기를 `const_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[cend](#cend)|형식의 반복기를 `const_iterator` 동시 벡터의 끝에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[clear](#clear)|동시 벡터의 모든 요소를 지웁니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[crbegin](#crbegin)|형식의 반복기를 `const_reverse_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[crend](#crend)|형식의 반복기를 `const_reverse_iterator` 동시 벡터의 끝에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[empty](#empty)|이 메서드가 호출 될 때 동시 벡터가 비어 있는지 테스트 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[end](#end)|오버로드됨. 형식이 `iterator` 나 `const_iterator` 동시 벡터의 끝 부분에 대 한 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[앞뒤](#front)|오버로드됨. 참조 또는 **`const`** 동시 벡터의 첫 번째 요소에 대 한 참조를 반환 합니다. 동시 벡터가 비어 있으면 반환 값은 정의 되지 않습니다. 이 메서드는 동시성이 보장 됩니다.|
|[get_allocator](#get_allocator)|동시 벡터를 생성 하는 데 사용 되는 할당자의 복사본을 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[grow_by](#grow_by)|오버로드됨. 이 동시 벡터가 요소로 증가 `_Delta` 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[grow_to_at_least](#grow_to_at_least)|는 요소가 하나 이상 있을 때까지이 동시 벡터를 늘립니다 `_N` . 이 메서드는 동시성이 보장 됩니다.|
|[max_size](#max_size)|동시 벡터가 유지할 수 있는 최대 요소 수를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[push_back](#push_back)|오버로드됨. 지정 된 항목을 동시 벡터의 끝에 추가 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[rbegin](#rbegin)|오버로드됨. 또는 형식의 반복기를 `reverse_iterator` `const_reverse_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[rend](#rend)|오버로드됨. 형식이 `reverse_iterator` 나 `const_reverse_iterator` 동시 벡터의 끝 부분에 대 한 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[두기](#reserve)|`_N`나중에 더 많은 메모리를 할당 하지 않고도 동시 벡터 크기를 늘릴 수 있는 충분 한 공간을 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[조정해](#resize)|오버로드됨. 동시 벡터의 크기를 요청 된 크기로 변경 하 고 필요에 따라 요소를 삭제 하거나 추가 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[shrink_to_fit](#shrink_to_fit)|조각화를 줄이고 메모리 사용을 최적화 하기 위해 동시 벡터의 내부 표현을 압축 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[size](#size)|동시 벡터의 요소 수를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.|
|[스왑을](#swap)|두 개의 동시 벡터의 내용을 바꿉니다. 이 메서드는 동시성이 보장 되지 않습니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자\[\]](#operator_at)|오버로드됨. 동시 벡터의 지정 된 인덱스에 있는 요소에 대 한 액세스를 제공 합니다. 이 메서드는 읽기 작업에 대해 동시성이 보장 되며, 값이 `_Index` 동시 벡터의 크기 보다 작음을 확인 한 경우 벡터를 확장 하는 데도 사용할 수 있습니다.|
|[연산자 =](#operator_eq)|오버로드됨. 다른 개체의 내용을 `concurrent_vector` 이 개체에 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|

## <a name="remarks"></a>설명

클래스에 대 한 자세한 내용은 `concurrent_vector` [병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>요구 사항

**헤더:** concurrent_vector. h

**네임 스페이스:** 동시성

## <a name="assign"></a><a name="assign"></a> 할당

동시 벡터의 요소를 지우고 `_N` 의 복사본 `_Item` 또는 반복기 범위 [,)로 지정 된 값에 할당 `_Begin` `_End` 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>매개 변수

*_InputIterator*<br/>
지정 된 반복기의 형식입니다.

*_N*<br/>
동시 벡터에 복사할 항목 수입니다.

*_Item*<br/>
동시 벡터를 채우는 데 사용 되는 값에 대 한 참조입니다.

*_Begin*<br/>
소스 범위의 첫 번째 요소에 대 한 반복기입니다.

*_End*<br/>
소스 범위에서 마지막 요소를 지난 요소에 대 한 반복기입니다.

### <a name="remarks"></a>설명

`assign` 는 동시성이 안전 하지 않습니다. 이 메서드를 호출할 때 다른 스레드가 동시 벡터에서 메서드를 호출 하 고 있지 않은지 확인 해야 합니다.

## <a name="at"></a><a name="at"></a> 속도

동시 벡터의 지정 된 인덱스에 있는 요소에 대 한 액세스를 제공 합니다. 이 메서드는 읽기 작업에 대해 동시성이 보장 되며, 값이 `_Index` 동시 벡터의 크기 보다 작음을 확인 한 경우 벡터가 증가 하는 동안에도 벡터를 확장 합니다.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
검색할 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 항목에 대 한 참조입니다.

### <a name="remarks"></a>설명

`at`비 참조를 반환 하는 함수의 버전은 **`const`** 다른 스레드에서 요소에 동시에 쓰는 데 사용할 수 없습니다. 동일한 데이터 요소에 대 한 동시 읽기 및 쓰기 작업을 동기화 하려면 다른 동기화 개체를 사용 해야 합니다.

이 메서드는 `out_of_range` `_Index` 가 동시 벡터의 크기 보다 크거나 같은 경우를 throw 하 고, `range_error` 인덱스가 벡터의 분할 된 부분에 대 한 것 이면를 throw 합니다. 벡터가 어떻게 손상 될 수 있는지에 대 한 자세한 내용은 [병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="back"></a><a name="back"></a> 뒤로

참조 또는 **`const`** 동시 벡터의 마지막 요소에 대 한 참조를 반환 합니다. 동시 벡터가 비어 있으면 반환 값은 정의 되지 않습니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>반환 값

**`const`** 동시 벡터의 마지막 요소에 대 한 참조 또는 참조입니다.

## <a name="begin"></a><a name="begin"></a> begin

또는 형식의 반복기를 `iterator` `const_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>반환 값

형식이 `iterator` 나 `const_iterator` 동시 벡터의 시작 부분에 대 한 반복기입니다.

## <a name="capacity"></a><a name="capacity"></a> 수용

더 많은 메모리를 할당 하지 않고도 동시 벡터가 증가 될 수 있는 최대 크기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>반환 값

동시 벡터가 더 많은 메모리를 할당하지 않고도 확장할 수 있는 최대 크기입니다.

### <a name="remarks"></a>설명

C + + 표준 라이브러리와 달리 `vector` `concurrent_vector` 개체는 더 많은 메모리를 할당 하는 경우 기존 요소를 이동 하지 않습니다.

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

형식의 반복기를 `const_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

`const_iterator`동시 벡터의 시작 부분에 대 한 형식의 반복기입니다.

## <a name="cend"></a><a name="cend"></a> cend

형식의 반복기를 `const_iterator` 동시 벡터의 끝에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

동시 벡터의 끝 부분에 대 한 형식의 반복기입니다 `const_iterator` .

## <a name="clear"></a><a name="clear"></a> 해제

동시 벡터의 모든 요소를 지웁니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

`clear` 는 동시성이 안전 하지 않습니다. 이 메서드를 호출할 때 다른 스레드가 동시 벡터에서 메서드를 호출 하 고 있지 않은지 확인 해야 합니다. `clear` 내부 배열을 해제 하지 않습니다. 내부 배열을 해제 하려면 다음에 함수를 `shrink_to_fit` 호출 `clear` 합니다.

## <a name="concurrent_vector"></a><a name="ctor"></a> concurrent_vector

동시 벡터를 생성 합니다.

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>매개 변수

*M*<br/>
원본 벡터의 할당자 형식입니다.

*_InputIterator*<br/>
입력 반복기의 형식입니다.

*_Al*<br/>
이 개체에 사용할 할당자 클래스입니다.

*_Vector*<br/>
요소를 복사해 오거나 이동해 올 소스 `concurrent_vector` 개체입니다.

*_N*<br/>
`concurrent_vector` 개체의 초기 용량입니다.

*_Item*<br/>
생성 된 개체의 요소 값입니다.

*_Begin*<br/>
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*_End*<br/>
복사할 요소의 범위를 벗어난 첫 번째 요소의 위치입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체를 저장 `_Al` 하 고 벡터를 초기화 합니다.

첫 번째 생성자는 빈 초기 벡터를 지정 하 고 할당자 형식을 명시적으로 지정 합니다. 사용할입니다.

두 번째 및 세 번째 생성자는 동시 벡터의 복사본을 지정 합니다 `_Vector` .

네 번째 생성자는 동시 벡터 `_Vector`의 이동을 지정합니다.

다섯 번째 생성자는 `_N` 클래스에 대 한 기본값의 요소에 대해 지정 된 수 ()의 반복을 지정 합니다 `T` .

여섯 번째 생성자는 값의 요소 반복 ()을 지정 합니다 `_N` `_Item` .

마지막 생성자는 반복기 범위 [,)에서 제공 하는 값을 지정 합니다 `_Begin` `_End` .

## <a name="concurrent_vector"></a><a name="dtor"></a> ~ concurrent_vector

모든 요소를 지우고이 동시 벡터를 소멸 시킵니다.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

형식의 반복기를 `const_reverse_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>반환 값

`const_reverse_iterator`동시 벡터의 시작 부분에 대 한 형식의 반복기입니다.

## <a name="crend"></a><a name="crend"></a> crend

형식의 반복기를 `const_reverse_iterator` 동시 벡터의 끝에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>반환 값

동시 벡터의 끝 부분에 대 한 형식의 반복기입니다 `const_reverse_iterator` .

## <a name="empty"></a><a name="empty"></a> 비우려면

이 메서드가 호출 될 때 동시 벡터가 비어 있는지 테스트 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 함수가 호출 된 순간에 벡터가 비어 있으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="end"></a><a name="end"></a> end

형식이 `iterator` 나 `const_iterator` 동시 벡터의 끝 부분에 대 한 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>반환 값

`iterator` `const_iterator` 동시 벡터의 끝 부분에 대 한 또는 형식의 반복기입니다.

## <a name="front"></a><a name="front"></a> 앞뒤

참조 또는 **`const`** 동시 벡터의 첫 번째 요소에 대 한 참조를 반환 합니다. 동시 벡터가 비어 있으면 반환 값은 정의 되지 않습니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>반환 값

**`const`** 동시 벡터의 첫 번째 요소에 대 한 참조 또는 참조입니다.

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

동시 벡터를 생성 하는 데 사용 되는 할당자의 복사본을 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

개체를 생성 하는 데 사용 되는 할당자의 복사본입니다 `concurrent_vector` .

## <a name="grow_by"></a><a name="grow_by"></a> grow_by

이 동시 벡터가 요소로 증가 `_Delta` 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>매개 변수

*_Delta*<br/>
개체에 추가할 요소의 수입니다.

*_Item*<br/>
새 요소를 초기화할 값입니다.

### <a name="return-value"></a>반환 값

첫 번째 항목에 추가 된 반복기입니다.

### <a name="remarks"></a>설명

`_Item`을 지정 하지 않으면 새 요소가 기본값으로 생성 됩니다.

## <a name="grow_to_at_least"></a><a name="grow_to_at_least"></a> grow_to_at_least

는 요소가 하나 이상 있을 때까지이 동시 벡터를 늘립니다 `_N` . 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>매개 변수

*_N*<br/>
개체의 새 최소 크기 `concurrent_vector` 입니다.

### <a name="return-value"></a>반환 값

추가 된 시퀀스의 시작을 가리키는 반복기 이거나, `_N` 추가 된 요소가 없는 경우 인덱스에 있는 요소입니다.

## <a name="max_size"></a><a name="max_size"></a> max_size

동시 벡터가 유지할 수 있는 최대 요소 수를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

개체가 보유할 수 있는 최대 요소 수 `concurrent_vector` 입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

다른 개체의 내용을 `concurrent_vector` 이 개체에 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>매개 변수

*M*<br/>
원본 벡터의 할당자 형식입니다.

*_Vector*<br/>
소스 `concurrent_vector` 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `concurrent_vector` 입니다.

## <a name="operator"></a><a name="operator_at"></a> operator[]

동시 벡터의 지정 된 인덱스에 있는 요소에 대 한 액세스를 제공 합니다. 이 메서드는 읽기 작업에 대해 동시성이 보장 되며, 값이 `_Index` 동시 벡터의 크기 보다 작음을 확인 한 경우 벡터를 확장 하는 데도 사용할 수 있습니다.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
검색할 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 항목에 대 한 참조입니다.

### <a name="remarks"></a>설명

`operator []`비 참조를 반환 하는 버전은 **`const`** 다른 스레드에서 요소에 동시에 쓰는 데 사용할 수 없습니다. 동일한 데이터 요소에 대 한 동시 읽기 및 쓰기 작업을 동기화 하려면 다른 동기화 개체를 사용 해야 합니다.

`_Index`가 동시 벡터의 유효한 인덱스 인지 확인 하기 위해 범위 검사를 수행 하지 않습니다.

## <a name="push_back"></a><a name="push_back"></a> push_back

지정 된 항목을 동시 벡터의 끝에 추가 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>매개 변수

*_Item*<br/>
추가할 값입니다.

### <a name="return-value"></a>반환 값

추가 된 항목에 대 한 반복기입니다.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

또는 형식의 반복기를 `reverse_iterator` `const_reverse_iterator` 동시 벡터의 시작 부분에 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>반환 값

형식이 `reverse_iterator` 나 `const_reverse_iterator` 동시 벡터의 시작 부분에 대 한 반복기입니다.

## <a name="rend"></a><a name="rend"></a> rend

형식이 `reverse_iterator` 나 `const_reverse_iterator` 동시 벡터의 끝 부분에 대 한 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>반환 값

`reverse_iterator` `const_reverse_iterator` 동시 벡터의 끝 부분에 대 한 또는 형식의 반복기입니다.

## <a name="reserve"></a><a name="reserve"></a> 두기

`_N`나중에 더 많은 메모리를 할당 하지 않고도 동시 벡터 크기를 늘릴 수 있는 충분 한 공간을 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>매개 변수

*_N*<br/>
공간을 예약 하는 요소 수입니다.

### <a name="remarks"></a>설명

`reserve` 는 동시성이 안전 하지 않습니다. 이 메서드를 호출할 때 다른 스레드가 동시 벡터에서 메서드를 호출 하 고 있지 않은지 확인 해야 합니다. 메서드가 반환 된 후의 동시 벡터 용량은 요청 된 예약 보다 클 수 있습니다.

## <a name="resize"></a><a name="resize"></a> 조정해

동시 벡터의 크기를 요청 된 크기로 변경 하 고 필요에 따라 요소를 삭제 하거나 추가 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>매개 변수

*_N*<br/>
동시 벡터의 새 크기입니다.

*짧은*<br/>
새 크기가 원래 크기보다 크면 새 요소의 값이 벡터에 추가됩니다. 값을 생략 하면 새 개체의 형식에 대 한 기본값이 할당 됩니다.

### <a name="remarks"></a>설명

컨테이너 크기가 요청 된 크기 보다 작은 경우 요청한 크기에 도달할 때까지 벡터에 요소가 추가 됩니다. 컨테이너의 크기가 요청 된 크기 보다 크면 컨테이너가 크기에 도달할 때까지 컨테이너 끝에 가장 가까운 요소가 삭제 됩니다 `_N` . 컨테이너의 현재 크기와 요청된 크기가 동일하면 아무런 작업도 실행되지 않습니다.

`resize` 는 동시성이 보장 되지 않습니다. 이 메서드를 호출할 때 다른 스레드가 동시 벡터에서 메서드를 호출 하 고 있지 않은지 확인 해야 합니다.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

조각화를 줄이고 메모리 사용을 최적화 하기 위해 동시 벡터의 내부 표현을 압축 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>설명

이 메서드는 내부적으로 메모리 이동 요소를 다시 할당 하 여 모든 반복기를 무효화 합니다. `shrink_to_fit` 는 동시성이 안전 하지 않습니다. 이 함수를 호출할 때 다른 스레드가 동시 벡터에서 메서드를 호출 하 고 있지 않은지 확인 해야 합니다.

## <a name="size"></a><a name="size"></a> 크기가

동시 벡터의 요소 수를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>반환 값

이 개체의 요소 수 `concurrent_vector` 입니다.

### <a name="remarks"></a>설명

반환 된 크기는 함수에 대 한 호출에 의해 추가 된 모든 요소를 포함 `push_back` 하거나이 메서드를 호출 하기 전에 완료 된 작업을 확장 하는 것을 보장 합니다. 그러나 할당 된 요소를 포함할 수 있으며, 증가 방법에 대 한 동시 호출을 통해 아직 생성 중입니다.

## <a name="swap"></a><a name="swap"></a> 스왑을

두 개의 동시 벡터의 내용을 바꿉니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>매개 변수

*_Vector*<br/>
내용을 바꿀 `concurrent_vector` 개체입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)
