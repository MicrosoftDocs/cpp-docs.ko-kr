---
title: concurrent_unordered_map 클래스
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: 04fdfb767645cb2db31a453a2378881a8b3e3a04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143161"
---
# <a name="concurrent_unordered_map-class"></a>concurrent_unordered_map 클래스

`concurrent_unordered_map` 클래스는 `std::pair<const K, _Element_type>` 형식의 다양한 길이 요소 시퀀스를 제어하는 동시성으로부터 안전한 컨테이너입니다. 시퀀스는 동시성으로부터 안전한 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 사용할 수 있는 방식으로 표시됩니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다.

## <a name="syntax"></a>구문

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

### <a name="parameters"></a>매개 변수

*K*<br/>
키 형식입니다.

*_Element_type*<br/>
매핑된 형식입니다.

*_Hasher*<br/>
해시 함수 개체 형식입니다. 이 인수는 선택 사항이며 기본값은 `std::hash<K>`입니다.

*key_equality*<br/>
같음 비교 함수 개체 형식입니다. 이 인수는 선택 사항이며 기본값은 `std::equal_to<K>`입니다.

*_Allocator_type*<br/>
순서가 지정 되지 않은 동시 맵에 대 한 메모리 할당 및 할당 취소에 대 한 세부 정보를 캡슐화 하는 저장 된 할당자 개체를 나타내는 형식입니다. 이 인수는 선택 사항이 며 기본값은 `std::allocator<std::pair<K``_Element_type>>`입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|name|설명|
|----------|-----------------|
|`allocator_type`|스토리지 관리를 위한 할당자의 형식입니다.|
|`const_iterator`|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|`const_local_iterator`|제어되는 시퀀스에 대한 상수 버킷 반복기의 형식입니다.|
|`const_pointer`|요소에 대한 상수 포인터의 형식입니다.|
|`const_reference`|요소에 대한 상수 참조의 형식입니다.|
|`difference_type`|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|`hasher`|해시 함수의 형식입니다.|
|`iterator`|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|`key_equal`|비교 함수의 형식입니다.|
|`key_type`|정렬 키의 형식입니다.|
|`local_iterator`|제어되는 시퀀스에 대한 버킷 반복기의 형식입니다.|
|`mapped_type`|각 키와 연결된 매핑된 값의 형식입니다.|
|`pointer`|요소에 대한 포인터의 형식입니다.|
|`reference`|요소에 대한 참조의 형식입니다.|
|`size_type`|두 요소 사이의 부호가 없는 거리의 형식입니다.|
|`value_type`|요소의 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|name|설명|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|오버로드됨. 순서가 지정 되지 않은 동시 맵을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|name|설명|
|----------|-----------------|
|[at](#at)|오버로드됨. 지정 된 키 값을 사용 하 여 `concurrent_unordered_map`에서 요소를 찾습니다. 이 메서드는 동시성이 보장 됩니다.|
|[hash_function](#hash_function)|저장된 해시 함수 개체를 가져옵니다.|
|[insert](#insert)|오버로드됨. `concurrent_unordered_map` 개체에 요소를 추가 합니다.|
|[key_eq](#key_eq)|저장 된 같음 비교 함수 개체를 가져옵니다.|
|[swap](#swap)|두 `concurrent_unordered_map` 개체의 내용을 바꿉니다. 이 메서드는 동시성이 보장 되지 않습니다.|
|[unsafe_erase](#unsafe_erase)|오버로드됨. `concurrent_unordered_map`에서 지정 된 위치에 있는 요소를 제거 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|

### <a name="public-operators"></a>Public 연산자

|name|설명|
|----------|-----------------|
|[operator\[\]](#operator_at)|오버로드됨. 지정된 키가 있는 요소를 찾거나 삽입합니다. 이 메서드는 동시성이 보장 됩니다.|
|[operator=](#operator_eq)|오버로드됨. 다른 `concurrent_unordered_map` 개체의 내용을이 개체에 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.|

## <a name="remarks"></a>설명

`concurrent_unordered_map` 클래스에 대 한 자세한 내용은 [병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>요구 사항

**헤더:** concurrent_unordered_map. h

**네임스페이스:** 동시성

## <a name="at"></a>속도

지정 된 키 값을 사용 하 여 `concurrent_unordered_map`에서 요소를 찾습니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
찾을 키 값입니다.

### <a name="return-value"></a>Return Value

찾은 요소의 데이터 값에 대한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값을 찾을 수 없는 경우 이 함수는 `out_of_range` 클래스의 개체를 throw합니다.

## <a name="begin"></a>시작

동시 컨테이너의 첫 번째 요소를 가리키는 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Return Value

동시 컨테이너의 첫 번째 요소에 대 한 반복기입니다.

## <a name="cbegin"></a>cbegin

동시 컨테이너의 첫 번째 요소를 가리키는 상수 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Return Value

동시 컨테이너의 첫 번째 요소에 대 한 상수 반복기입니다.

## <a name="cend"></a>cend

동시 컨테이너에서 마지막 요소 다음에 나오는 위치를 가리키는 상수 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Return Value

동시 컨테이너에서 마지막 요소 다음에 나오는 위치에 대 한 상수 반복기입니다.

## <a name="clear"></a>해제

동시 컨테이너의 모든 요소를 지웁니다. 이 함수는 동시성이 안전 하지 않습니다.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_unordered_map

순서가 지정 되지 않은 동시 맵을 생성 합니다.

```cpp
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>매개 변수

*_Iterator*<br/>
입력 반복기의 형식입니다.

*_Number_of_buckets*<br/>
순서가 지정되지 않은 이 맵에 대한 초기 버킷 수입니다.

*_Hasher*<br/>
순서가 지정되지 않은 이 맵에 대한 해시 함수입니다.

*key_equality*<br/>
순서가 지정되지 않은 이 맵에 대한 같음 비교 함수입니다.

*_Allocator*<br/>
순서가 지정되지 않은 이 맵에 대한 할당자입니다.

*_Begin*<br/>
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*_End*<br/>
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*_Umap*<br/>
요소를 복사해 오거나 이동해 올 소스 `concurrent_unordered_map` 개체입니다.

### <a name="remarks"></a>설명

모든 생성자는 할당자 개체 `_Allocator`를 저장하고 순서가 지정되지 않은 맵을 초기화합니다.

첫 번째 생성자는 비어 있는 초기 맵을 지정하고 사용할 버킷 수, 해시 함수, 같음 함수 및 할당자 형식을 명시적으로 지정합니다.

두 번째 생성자는 순서가 지정되지 않은 맵에 대한 할당자를 지정합니다.

세 번째 생성자는 반복기 범위 [`_Begin`, `_End`)에서 제공 하는 값을 지정 합니다.

네 번째 및 다섯 번째 생성자는 순서가 지정되지 않은 동시 맵 `_Umap`의 복사본을 지정합니다.

마지막 생성자는 순서가 지정되지 않은 동시 맵 `_Umap`의 이동을 지정합니다.

## <a name="count"></a>수

지정 된 키와 일치 하는 요소의 수를 셉니다. 이 함수는 동시성이 안전 합니다.

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
검색할 키입니다.

### <a name="return-value"></a>Return Value

키가 컨테이너에 표시 되는 횟수입니다.

## <a name="empty"></a> empty

요소가 있는지 여부를 테스트합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Return Value

동시 컨테이너가 비어 있으면 **true** 이 고, 그렇지 않으면 **false** 입니다.

### <a name="remarks"></a>설명

동시 삽입이 있을 때이 함수를 호출한 후에도 동시 컨테이너가 비어 있는지 여부는 반환 값을 읽기 전에 즉시 변경할 수 있습니다.

## <a name="end"></a>종단

동시 컨테이너에서 마지막 요소 다음에 나오는 위치를 가리키는 반복기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Return Value

동시 컨테이너에서 마지막 요소 다음에 나오는 위치에 대 한 반복기입니다.

## <a name="equal_range"></a> equal_range

지정 된 키와 일치 하는 범위를 찾습니다. 이 함수는 동시성이 안전 합니다.

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
검색할 키 값입니다.

### <a name="return-value"></a>Return Value

첫 번째 요소가 시작 부분에 대 한 반복기이 고 두 번째 요소는 범위의 끝 부분에 대 한 반복기 인 [쌍](../../../standard-library/pair-structure.md) 입니다.

### <a name="remarks"></a>설명

연속 삽입을 수행 하면 시작 반복기 뒤와 끝 반복기 앞에 추가 키를 삽입할 수 있습니다.

## <a name="find"></a>찾아낼

지정된 키와 일치하는 요소를 찾습니다. 이 함수는 동시성이 안전 합니다.

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
검색할 키 값입니다.

### <a name="return-value"></a>Return Value

제공 된 키와 일치 하는 첫 번째 요소의 위치를 가리키는 반복기 이거나, 이러한 요소가 없는 경우 `end()` 반복기입니다.

## <a name="get_allocator"></a> get_allocator

이 동시 컨테이너에 대해 저장 된 할당자 개체를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Return Value

이 동시 컨테이너에 대해 저장 된 할당자 개체입니다.

## <a name="hash_function"></a>hash_function

저장된 해시 함수 개체를 가져옵니다.

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>Return Value

저장된 해시 함수 개체입니다.

## <a name="insert"></a>넣거나

`concurrent_unordered_map` 개체에 요소를 추가 합니다.

```cpp
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>매개 변수

*_Iterator*<br/>
삽입에 사용되는 반복기 형식입니다.

*V*<br/>
맵에 삽입 된 값의 형식입니다.

*값*<br/>
삽입할 값입니다.

*_Where*<br/>
삽입 지점을 검색할 시작 위치입니다.

*first*<br/>
삽입할 범위의 시작 부분입니다.

*last*<br/>
삽입할 범위의 끝입니다.

### <a name="return-value"></a>Return Value

반복기 및 부울 값을 포함 하는 쌍입니다. 자세한 내용은 설명 섹션을 참조하세요.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 키가 `value`와 동일한 순서를 갖는 시퀀스에 X 요소가 있는지 여부를 확인 합니다. 그렇지 않은 경우 X 요소를 만들고 `value`를 사용 하 여 초기화 합니다. 그러면 함수는 X를 지정 하는 `where` 반복기를 확인 합니다. 삽입이 발생 한 경우 함수는 `std::pair(where, true)`을 반환 합니다. 그 외의 경우 `std::pair(where, false)`를 반환합니다.

두 번째 멤버 함수는 삽입 (`value`)을 반환 하며,이를 통해 제어 되는 시퀀스 내에서 삽입 지점을 검색 하는 시작 위치로 `_Where`를 사용 합니다.

세 번째 멤버 함수는 [`first`, `last`) 범위에서 요소 값의 시퀀스를 삽입 합니다.

마지막 두 멤버 함수는 처음 두 함수와 똑같이 동작하지만, `value`는 삽입된 값을 생성하는데 사용된다는 점이 다릅니다.

## <a name="key_eq"></a>key_eq

저장 된 같음 비교 함수 개체를 가져옵니다.

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>Return Value

저장 된 같음 비교 함수 개체입니다.

## <a name="load_factor"></a>load_factor

컨테이너의 현재 로드 비율을 계산 하 고 반환 합니다. 로드 비율은 컨테이너의 요소 수를 버킷 수로 나눈 값입니다.

```cpp
float load_factor() const;
```

### <a name="return-value"></a>Return Value

컨테이너의 로드 비율입니다.

## <a name="max_load_factor"></a>max_load_factor

컨테이너의 최대 로드 비율을 가져오거나 설정 합니다. 최대 로드 비율은 컨테이너가 내부 테이블을 확장 하기 전에 모든 버킷에 있는 요소 수보다 가장 많은 수입니다.

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>매개 변수

`_Newmax`

### <a name="return-value"></a>Return Value

첫 번째 멤버 함수는 저장된 최대 로드 비율을 반환합니다. 두 번째 멤버 함수는 값을 반환 하지 않지만 제공 된 로드 계수가 잘못 된 경우에는 [out_of_range](../../../standard-library/out-of-range-class.md) 예외를 throw 합니다.

## <a name="max_size"></a> max_size

할당자에 의해 결정 되는 동시 컨테이너의 최대 크기를 반환 합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Return Value

이 동시 컨테이너에 삽입할 수 있는 최대 요소 수입니다.

### <a name="remarks"></a>설명

이 상한 값은 실제로 컨테이너가 보유할 수 있는 값 보다 클 수 있습니다.

## <a name="operator_at"></a> operator[]

지정된 키가 있는 요소를 찾거나 삽입합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
키 값입니다.

찾거나 삽입 합니다.

### <a name="return-value"></a>Return Value

찾거나 삽입 된 요소의 데이터 값에 대 한 참조입니다.

### <a name="remarks"></a>설명

인수 키 값이 없으면 데이터 형식의 기본값과 함께 삽입됩니다.

`operator[]`를 사용 하 여 `m[key] = DataValue;`를 사용 하 `m` 지도에 요소를 삽입할 수 있습니다. 여기서 `DataValue`는 키 값이 `mapped_type` 인 요소의 `key`값입니다.

`operator[]`를 사용하여 요소를 삽입하는 경우 반환된 참조는 삽입이 기존 요소를 변경하는지 또는 새 요소를 생성하는지 여부를 나타내지 않습니다. 멤버 함수 `find` 및 [insert](#insert) 는 지정 된 키를 가진 요소가 삽입 전에 이미 있는지 여부를 확인 하는 데 사용할 수 있습니다.

## <a name="operator_eq"></a>연산자 =

다른 `concurrent_unordered_map` 개체의 내용을이 개체에 할당 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>매개 변수

*_Umap*<br/>
소스 `concurrent_unordered_map` 개체입니다.

### <a name="return-value"></a>Return Value

이 `concurrent_unordered_map` 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

동시 벡터의 기존 요소를 지운 후에 `operator=`는 `_Umap`의 내용을 동시 벡터로 복사하거나 이동합니다.

## <a name="rehash"></a>rehash

해시 테이블을 다시 빌드합니다.

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>매개 변수

*_Buckets*<br/>
원하는 버킷 수입니다.

### <a name="remarks"></a>설명

멤버 함수는 필요에 따라 버킷 수를 `_Buckets` 이상으로 변경하고 해시 테이블을 다시 빌드합니다. 버킷 수는 2의 거듭제곱 이어야 합니다. 2의 거듭제곱이 아닌 경우 다음으로 가장 큰 2의 제곱으로 반올림 됩니다.

버킷 수가 유효 하지 않은 경우 (0 이거나 최대 버킷 수보다 큰 경우) [out_of_range](../../../standard-library/out-of-range-class.md) 예외를 throw 합니다.

## <a name="size"></a>크기가

이 동시 컨테이너의 요소 수를 반환합니다. 이 메서드는 동시성이 보장 됩니다.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Return Value

컨테이너에 들어 있는 항목 수입니다.

### <a name="remarks"></a>설명

동시 삽입이 있을 경우 이 함수를 호출한 직후, 반환 값을 읽기도 전에 동시 컨테이너의 요소 수가 변경될 수 있습니다.

## <a name="swap"></a>스왑을

두 `concurrent_unordered_map` 개체의 내용을 바꿉니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>매개 변수

*_Umap*<br/>
스왑할 `concurrent_unordered_map` 개체입니다.

## <a name="unsafe_begin"></a>unsafe_begin

특정 버킷에 대 한이 컨테이너의 첫 번째 요소에 반복기를 반환 합니다.

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>매개 변수

*_Bucket*<br/>
버킷 인덱스입니다.

### <a name="return-value"></a>Return Value

버킷의 시작 부분을 가리키는 반복기입니다.

## <a name="unsafe_bucket"></a>unsafe_bucket

이 컨테이너에서 특정 키가 매핑되는 버킷 인덱스를 반환 합니다.

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>매개 변수

*KVal*<br/>
검색 되는 요소 키입니다.

### <a name="return-value"></a>Return Value

이 컨테이너의 키에 대 한 버킷 인덱스입니다.

## <a name="unsafe_bucket_count"></a>unsafe_bucket_count

이 컨테이너의 현재 버킷 수를 반환 합니다.

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Return Value

이 컨테이너의 현재 버킷 수입니다.

## <a name="unsafe_bucket_size"></a>unsafe_bucket_size

이 컨테이너의 특정 버킷에 있는 항목 수를 반환 합니다.

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>매개 변수

*_Bucket*<br/>
검색할 버킷입니다.

### <a name="return-value"></a>Return Value

이 컨테이너의 현재 버킷 수입니다.

## <a name="unsafe_cbegin"></a>unsafe_cbegin

특정 버킷에 대 한이 컨테이너의 첫 번째 요소에 반복기를 반환 합니다.

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>매개 변수

*_Bucket*<br/>
버킷 인덱스입니다.

### <a name="return-value"></a>Return Value

버킷의 시작 부분을 가리키는 반복기입니다.

## <a name="unsafe_cend"></a>unsafe_cend

특정 버킷에 있는 마지막 요소 다음의 위치에 대 한 반복기를 반환 합니다.

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>매개 변수

*_Bucket*<br/>
버킷 인덱스입니다.

### <a name="return-value"></a>Return Value

버킷의 시작 부분을 가리키는 반복기입니다.

## <a name="unsafe_end"></a>unsafe_end

특정 버킷에 대 한이 컨테이너의 마지막 요소에 반복기를 반환 합니다.

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>매개 변수

*_Bucket*<br/>
버킷 인덱스입니다.

### <a name="return-value"></a>Return Value

버킷 끝을 가리키는 반복기입니다.

## <a name="unsafe_erase"></a>unsafe_erase

`concurrent_unordered_map`에서 지정 된 위치에 있는 요소를 제거 합니다. 이 메서드는 동시성이 보장 되지 않습니다.

```cpp
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>매개 변수

*_Where*<br/>
지울 반복기 위치입니다.

*_Begin*<br/>
삭제할 요소의 범위에서 첫 번째 요소의 위치입니다.

*_End*<br/>
삭제할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*KVal*<br/>
지울 키 값입니다.

### <a name="return-value"></a>Return Value

처음 두 멤버 함수는 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, 이러한 요소가 없는 경우 `concurrent_unordered_map::end`()을 반환 합니다. 세 번째 멤버 함수는 제거 되는 요소의 수를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 `_Where`로 지정된 제어 시퀀스의 요소를 제거합니다. 두 번째 멤버 함수는 [`_Begin`, `_End`) 범위의 요소를 제거 합니다.

세 번째 멤버 함수는 `concurrent_unordered_map::equal_range`(KVal)로 구분 된 범위의 요소를 제거 합니다.

## <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

이 컨테이너의 최대 버킷 수를 반환 합니다.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Return Value

이 컨테이너의 최대 버킷 수입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임스페이스](concurrency-namespace.md)<br/>
[병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)
