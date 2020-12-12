---
description: '자세히 알아보기: array 클래스'
title: array 클래스
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: df74ab714fc2865cce71300e094b693664694b31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247893"
---
# <a name="array-class"></a>array 클래스

데이터를 액셀러레이터 키로 이동 하는 데 사용 되는 데이터 컨테이너를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>매개 변수

*value_type*<br/>
데이터의 요소 형식입니다.

*_Rank*<br/>
배열의 차수입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[array 생성자](#ctor)|`array` 클래스의 새 인스턴스를 초기화합니다.|
|[~ array 소멸자](#dtor)|개체를 소멸 시킵니다 `array` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[copy_to](#copy_to)|배열의 내용을 다른 배열에 복사 합니다.|
|[data](#data)|배열의 원시 데이터에 대 한 포인터를 반환 합니다.|
|[get_accelerator_view](#get_accelerator_view)|배열이 할당 된 위치를 나타내는 [accelerator_view](accelerator-view-class.md) 개체를 반환 합니다. 이 속성은 CPU 에서만 액세스할 수 있습니다.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|개체를 인스턴스화하기 위해 준비 생성자를 호출할 때 매개 변수로 전달 되는 두 번째 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다 `array` .|
|[get_cpu_access_type](#get_cpu_access_type)|배열의 [access_type](concurrency-namespace-enums-amp.md#access_type) 을 반환 합니다. 이 메서드는 CPU 에서만 액세스할 수 있습니다.|
|[get_extent](#get_extent)|배열의 [익스텐트](extent-class.md) 개체를 반환 합니다.|
|[reinterpret_as](#reinterpret_as)|개체의 모든 요소를 포함 하는 1 차원 배열을 반환 `array` 합니다.|
|[여기서](#section)|`array`지정 된 원점에 있고, 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션을 반환 합니다.|
|[view_as](#view_as)|개체에서 생성 된 [array_view](array-view-class.md) 개체를 반환 `array` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[operator std:: vector &lt; value_type&gt;](#operator_vec)|`copy(*this, vector)`를 사용 하 여 배열을 std::[vector](../../../standard-library/vector-class.md) 개체로 암시적으로 변환 합니다.|
|[연산자 ()](#operator_call)|매개 변수로 지정 된 요소 값을 반환 합니다.|
|[연산자\[\]](#operator_at)|지정 된 인덱스에 있는 요소를 반환 합니다.|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `array` 여기로 복사 합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[rank 상수](#rank)|배열의 차수를 저장합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|배열이 할당 된 위치를 나타내는 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다. 이 속성은 CPU 에서만 액세스할 수 있습니다.|
|[associated_accelerator_view](#associated_accelerator_view)|개체를 인스턴스화하기 위해 준비 생성자를 호출할 때 매개 변수로 전달 되는 두 번째 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다 `array` .|
|[cpu_access_type](#cpu_access_type)|CPU가 배열의 저장소에 액세스할 수 있는 방법을 나타내는 [access_type](concurrency-namespace-enums-amp.md#access_type) 를 가져옵니다.|
|[됨으로써](#extent)|배열의 셰이프를 정의 하는 범위를 가져옵니다.|

## <a name="remarks"></a>설명

형식은 `array<T,N>` 액셀러레이터 또는 CPU와 같은 특정 위치에 있는 조밀한 및 일반 (부정형이 아님) *N* 차원 배열을 나타냅니다. 배열에 있는 요소의 데이터 형식은 이며 `T` , 대상 액셀러레이터와 호환 되는 형식 이어야 합니다. 배열의 차수는 `N` 정적으로 결정 되 고 형식의 일부 이지만 배열의 범위는 런타임에 의해 결정 되며 클래스를 사용 하 여 표현 됩니다 `extent<N>` .

배열에는 `array` 차수가 1, 2, 3 인 개체에 대해 특수화 된 차원이 있지만 배열에는 여러 개의 차원이 있을 수 있습니다. 차원 인수를 생략 하는 경우 기본값은 1입니다.

배열 데이터는 메모리에 인접 하 게 배치 됩니다. 최하위 차원에서 1과 다른 요소는 메모리에서 인접해 있습니다.

배열은 다른 배열로 복사 될 때 전체 복사가 수행 되므로 논리적으로는 값 형식으로 간주 됩니다. 두 배열이 동일한 데이터를 가리키지 않습니다.

`array<T,N>`형식은 여러 시나리오에서 사용 됩니다.

- 액셀러레이터 키를 계산 하는 데 사용할 수 있는 데이터 컨테이너입니다.

- 호스트 CPU (다른 배열 간에 복사 하는 데 사용 될 수 있음)에 메모리를 보관 하는 데이터 컨테이너로 사용 됩니다.

- 호스트-장치 복사본에서 fast 중개자 역할을 하는 스테이징 개체입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`array`

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="array"></a><a name="dtor"></a> ~ 배열

개체를 소멸 시킵니다 `array` .

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a><a name="accelerator_view"></a> accelerator_view

배열이 할당 된 위치를 나타내는 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다. 이 속성은 CPU 에서만 액세스할 수 있습니다.

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="array"></a><a name="ctor"></a> 배열

[Array 클래스](array-class.md)의 새 인스턴스를 초기화 합니다. 에 대 한 기본 생성자가 없습니다 `array<T,N>` . 모든 생성자는 CPU 에서만 실행 됩니다. Direct3D 대상에서 실행할 수 없습니다.

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Associated_Av*<br/>
배열의 기본 대상 위치를 지정 하는 accelerator_view입니다.

*_Av*<br/>
배열의 위치를 지정 하는 [accelerator_view](accelerator-view-class.md) 개체입니다.

*_Cpu_access_type*<br/>
CPU의 배열에 대해 원하는 [access_type](concurrency-namespace-enums-amp.md#access_type)  입니다. 이 매개 변수의 기본값은 `access_type_auto` 런타임에 CPU 결정을 그대로 유지 하는 것입니다 `access_type` . `access_type`메서드를 사용 하 여 배열에 대 한 실제 CPU를 쿼리할 수 있습니다 `get_cpu_access_type` .

*_Extent*<br/>
배열의 각 차원에 대 한 범위입니다.

*_E0*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E1*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E2*<br/>
이 섹션 범위에서 가장 중요 하지 않은 구성 요소입니다.

*_InputIterator*<br/>
입력 반복기의 형식입니다.

*_Src*<br/>
복사할 개체입니다.

*_Src_first*<br/>
소스 컨테이너에 대 한 시작 반복기입니다.

*_Src_last*<br/>
소스 컨테이너에 대 한 종료 반복기입니다.

*_Other*<br/>
기타 데이터 원본.

*_Rank*<br/>
섹션의 순위입니다.

*value_type*<br/>
복사 되는 요소의 데이터 형식입니다.

## <a name="associated_accelerator_view"></a><a name="associated_accelerator_view"></a> associated_accelerator_view

개체를 인스턴스화하기 위해 준비 생성자를 호출할 때 매개 변수로 전달 되는 두 번째 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다 `array` .

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a><a name="copy_to"></a> copy_to

의 내용을 `array` 다른에 복사 `array` 합니다.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>매개 변수

*_Dest*<br/>
복사할 대상 [array_view](array-view-class.md) 개체입니다.

## <a name="cpu_access_type"></a><a name="cpu_access_type"></a> cpu_access_type

이 배열에 허용 되는 CPU access_type를 가져옵니다.

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a><a name="data"></a> 데이터

의 원시 데이터에 대 한 포인터를 반환 합니다 `array` .

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>반환 값

배열의 원시 데이터에 대 한 포인터입니다.

## <a name="extent"></a><a name="extent"></a> 됨으로써

의 모양을 정의 하는 [익스텐트](extent-class.md) 개체를 가져옵니다 `array` .

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a><a name="get_accelerator_view"></a> get_accelerator_view

개체가 할당 된 위치를 나타내는 [accelerator_view](accelerator-view-class.md) 개체를 반환 합니다 `array` . 이 속성은 CPU 에서만 액세스할 수 있습니다.

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>반환 값

`accelerator_view`개체가 할당 된 위치를 나타내는 개체입니다 `array` .

## <a name="get_associated_accelerator_view"></a><a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

개체를 인스턴스화하기 위해 준비 생성자를 호출할 때 매개 변수로 전달 되는 두 번째 [accelerator_view](accelerator-view-class.md) 개체를 가져옵니다 `array` .

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>반환 값

준비 생성자에 전달 되는 두 번째 [accelerator_view](accelerator-view-class.md) 개체입니다.

## <a name="get_cpu_access_type"></a><a name="get_cpu_access_type"></a> get_cpu_access_type

이 배열에 허용 되는 CPU access_type을 반환 합니다.

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>반환 값

## <a name="get_extent"></a><a name="get_extent"></a> get_extent

의 [익스텐트](extent-class.md) 개체를 반환 합니다 `array` .

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>반환 값

`extent`의 `array` 개체입니다.

## <a name="operator-stdvectorltvalue_typegt"></a><a name="operator_vec"></a> operator std:: vector &lt; value_type&gt;

`copy(*this, vector)`를 사용 하 여 배열을 std:: vector 개체로 암시적으로 변환 합니다.

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*value_type*<br/>
벡터 요소의 데이터 형식입니다.

### <a name="return-value"></a>반환 값

`vector<T>`배열에 포함 된 데이터의 복사본을 포함 하는 형식의 개체입니다.

## <a name="operator"></a><a name="operator_call"></a> 연산자 ()

매개 변수로 지정 된 요소 값을 반환 합니다.

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
요소의 위치입니다.

*_I0*<br/>
이 섹션의 원본에 대 한 가장 중요 한 구성 요소입니다.

*_I1*<br/>
이 섹션의 원본에 대 한 다음으로 중요 한 구성 요소입니다.

*_I2*<br/>
이 섹션의 원점에서 가장 중요 하지 않은 구성 요소입니다.

*_I*<br/>
요소의 위치입니다.

### <a name="return-value"></a>반환 값

매개 변수로 지정 된 요소 값입니다.

## <a name="operator"></a><a name="operator_at"></a> operator[]

지정 된 인덱스에 있는 요소를 반환 합니다.

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스입니다.

*_I*<br/>
인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 요소입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 개체의 내용을 복사 `array` 합니다.

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`array`복사할 개체입니다.

*_Src*<br/>
`array`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `array` 입니다.

## <a name="rank"></a><a name="rank"></a> 배열

의 순위를 저장 `array` 합니다.

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a><a name="reinterpret_as"></a> reinterpret_as

선택적으로 소스 배열과 다른 값 형식을 가질 수 있는 1 차원 array_view를 통해 배열을 다시 해석 합니다.

### <a name="syntax"></a>구문

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Value_type2*<br/>
반환 된 데이터의 데이터 형식입니다.

### <a name="return-value"></a>반환 값

요소 형식이 T에서 ElementType으로 다시 해석 하 고 순위가 N에서 1로 감소 하는 배열에 기반 하는 array_view 또는 const array_view 개체입니다.

### <a name="remarks"></a>설명

경우에 따라 다차원 배열을 소스 배열과는 다른 값 형식을 사용 하는 선형의 1 차원 배열로 보는 것이 편리 합니다. 이 메서드를 사용 하 여이를 달성할 수 있습니다.
**주의** 다른 값 형식을 사용 하 여 배열 개체를 reinterpeting 안전 하지 않은 작업입니다. 이 기능을 신중 하 게 사용 하는 것이 좋습니다.

다음 코드에 예가 나와 있습니다.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a><a name="section"></a> 여기서

`array`지정 된 원점에 있고, 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션을 반환 합니다.

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_E0*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E1*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E2*<br/>
이 섹션 범위에서 가장 중요 하지 않은 구성 요소입니다.

*_Ext*<br/>
섹션의 범위를 지정 하는 [익스텐트](extent-class.md) 개체입니다. 원점은 0입니다.

*_Idx*<br/>
원본 위치를 지정 하는 [index](index-class.md) 개체입니다. 하위 섹션은 범위의 나머지 부분입니다.

*_I0*<br/>
이 섹션의 원본에 대 한 가장 중요 한 구성 요소입니다.

*_I1*<br/>
이 섹션의 원본에 대 한 다음으로 중요 한 구성 요소입니다.

*_I2*<br/>
이 섹션의 원점에서 가장 중요 하지 않은 구성 요소입니다.

*_Rank*<br/>
섹션의 순위입니다.

*_Section_extent*<br/>
섹션의 범위를 지정 하는 [익스텐트](extent-class.md) 개체입니다.

*_Section_origin*<br/>
원본 위치를 지정 하는 [index](index-class.md) 개체입니다.

*value_type*<br/>
복사 되는 요소의 데이터 형식입니다.

### <a name="return-value"></a>반환 값

`array`지정 된 원점에 있고, 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션을 반환 합니다. 개체만 지정 된 경우 `index` 하위 섹션에는 개체의 요소 인덱스 보다 큰 인덱스를 포함 하는 연결 된 그리드의 모든 요소가 포함 됩니다 `index` .

## <a name="view_as"></a><a name="view_as"></a> view_as

이 배열을 다른 순위 [array_view](array-view-class.md) 으로 다시 해석 합니다.

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_New_rank*<br/>
`extent`매개 변수로 전달 되는 개체의 순위입니다.

*_View_extent*<br/>
새 [array_view](array-view-class.md) 개체를 생성 하는 데 사용 되는 범위입니다.

*value_type*<br/>
원래 개체와 반환 된 개체 모두에 있는 요소의 데이터 형식입니다 `array` `array_view` .

### <a name="return-value"></a>반환 값

구성 된 [array_view](array-view-class.md) 개체입니다.

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
