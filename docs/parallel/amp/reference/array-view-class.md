---
description: Array_view 클래스에 대해 자세히 알아보세요.
title: array_view 클래스
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: 170eb51a437fd56b9b9e74bb22e5b84d3478b4bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247880"
---
# <a name="array_view-class"></a>array_view 클래스

다른 컨테이너에 저장 된 데이터에 대 한 N 차원 뷰를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

### <a name="parameters"></a>매개 변수

*value_type*<br/>
개체에 있는 요소의 데이터 형식입니다 `array_view` .

*_Rank*<br/>
개체의 순위입니다 `array_view` .

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[array_view 생성자](#ctor)|`array_view` 클래스의 새 인스턴스를 초기화합니다. 에 대 한 기본 생성자가 없습니다 `array<T,N>` . 모든 생성자는 CPU 에서만 실행 되도록 제한 되며 Direct3D 대상에서는 실행할 수 없습니다.|
|[~ array_view 소멸자](#ctor)|개체를 소멸 시킵니다 `array_view` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[copy_to](#copy_to)|을 `array_view` 호출 하 여 개체의 내용을 지정 된 대상에 복사 합니다 `copy(*this, dest)` .|
|[data](#data)|의 원시 데이터에 대 한 포인터를 반환 합니다 `array_view` .|
|[discard_data](#discard_data)|이 뷰를 기반으로 하는 현재 데이터를 삭제 합니다.|
|[get_extent](#get_extent)|array_view 개체의 extent 개체를 반환합니다.|
|[get_ref](#get_ref)|인덱싱된 요소에 대 한 참조를 반환 합니다.|
|[get_source_accelerator_view](#get_source_accelerator_view)|의 데이터 소스가 있는 [accelerator_view](accelerator-view-class.md) 을 반환 합니다 `array_view` .|
|[고치십시오](#refresh)|`array_view`바인딩된 메모리가 인터페이스 외부에서 수정 되었음을 개체에 알립니다 `array_view` . 이 메서드에 대 한 호출은 캐시 된 모든 정보를 부실 하 게 렌더링 합니다.|
|[reinterpret_as](#reinterpret_as)|개체의 모든 요소를 포함 하는 1 차원 배열을 반환 `array_view` 합니다.|
|[여기서](#section)|`array_view`지정 된 원점에 있고, 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션을 반환 합니다.|
|[항목과](#synchronize)|개체에 대 한 수정 내용을 `array_view` 다시 원본 데이터에 동기화 합니다.|
|[synchronize_async](#synchronize_async)|개체에 대 한 모든 수정 내용을 `array_view` 다시 소스 데이터에 비동기적으로 동기화 합니다.|
|[synchronize_to](#synchronize_to)|개체에 대 한 모든 수정 내용을 `array_view` 지정 된 [accelerator_view](accelerator-view-class.md)동기화 합니다.|
|[synchronize_to_async](#synchronize_to_async)|개체에 대 한 모든 수정 내용을 `array_view` 지정 된 [accelerator_view](accelerator-view-class.md)비동기식으로 동기화 합니다.|
|[view_as](#view_as)|`array_view`이 개체의 데이터를 사용 하 여 다른 차수의 개체를 생성 `array_view` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 ()](#operator_call)|매개 변수에서 지정 하는 요소의 값을 반환 합니다.|
|[연산자\[\]](#operator_at)|매개 변수로 지정 된 요소를 반환 합니다.|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `array_view` 여기로 복사 합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[rank 상수](#rank)|개체의 순위를 저장 `array_view` 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[됨으로써](#extent)|`extent` 개체의 모양을 정의하는 `array_view` 개체를 가져옵니다.|
|[source_accelerator_view](#source_accelerator_view)|의 데이터 소스가 있는 [accelerator_view](accelerator-view-class.md) 를 가져옵니다. `array_view`|
|[value_type](#value_type)|`array_view`및 바인딩된 배열의 값 형식입니다.|

## <a name="remarks"></a>설명

`array_view`클래스는 개체의 [배열](array-class.md) 개체 또는 하위 섹션에 포함 된 데이터에 대 한 뷰를 나타냅니다 `array` .

`array_view`원본 데이터가 있는 개체 (로컬) 또는 다른 액셀러레이터 또는 일관성 도메인 (원격)에 액세스할 수 있습니다. 개체에 원격으로 액세스 하는 경우 필요에 따라 보기가 복사 되 고 캐시 됩니다. 자동 캐싱의 효과를 제외 하 고 개체 `array_view` 의 성능 프로필은 개체의 경우와 유사 `array` 합니다. 뷰를 통해 데이터에 액세스 하는 경우 약간의 성능 저하가 발생 합니다.

다음과 같은 세 가지 원격 사용 시나리오가 있습니다.

- 시스템 메모리 포인터에 대 한 뷰는 액셀러레이터 키에 대 한 [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) 호출을 통해 전달 되며 액셀러레이터 키에서 액세스 됩니다.

- 액셀러레이터 키에 있는 배열에 대 한 보기는 `parallel_for_each` 다른 액셀러레이터에 대 한 호출을 통해 전달 되며 거기에 액세스 됩니다.

- 액셀러레이터 키에 있는 배열에 대 한 보기는 CPU에서 액세스 됩니다.

이러한 시나리오 중 하나에서 참조 된 뷰는 런타임에 원격 위치로 복사 되 고, 개체에 대 한 호출로 수정 되 면 `array_view` 로컬 위치로 다시 복사 됩니다. 런타임은 변경 내용을 다시 복사 하는 프로세스를 최적화 하거나, 변경 된 요소만 복사 하거나, 변경 되지 않은 부분만 복사할 수 있습니다. `array_view`하나의 데이터 원본에서 개체를 겹치면 원격 위치에서 참조 무결성을 유지 하는 것을 보장할 수 없습니다.

동일한 데이터 원본에 대 한 모든 다중 스레드 액세스를 동기화 해야 합니다.

런타임에서는 개체의 데이터 캐싱에 대해 다음과 같은 사항을 보장 합니다 `array_view` .

- 개체에 대 한 모든 잘 동기화 된 액세스 `array` 와 `array_view` 프로그램 순서에서 개체에 대 한 개체는 순차적으로 발생 하는 관계를 따릅니다.

- `array_view`단일 개체에서 동일한 액셀러레이터에 있는 개체에 대 한 모든 잘 동기화 `array` 된 액세스는 개체를 통해 별칭이 지정 됩니다 `array` . 프로그램 순서를 따르는 하는 총 발생 이전 관계를 유도 합니다. 캐싱은 없습니다. `array_view`개체가 다른 액셀러레이터에서 실행 되는 경우 액세스 순서가 정의 되지 않아 경합 상태가 생성 됩니다.

`array_view`시스템 메모리에서 포인터를 사용 하 여 개체를 만드는 경우에는 포인터를 통해서만 뷰 개체를 변경 해야 합니다 `array_view` `array_view` . 또는 `refresh()` `array_view` 기본 네이티브 메모리가 개체를 통하지 않고 직접 변경 된 경우 시스템 포인터에 연결 된 개체 중 하나에서를 호출 해야 합니다 `array_view` .

두 작업 중 하나는 `array_view` 기본 네이티브 메모리가 변경 되었으며 액셀러레이터 키에 있는 복사본이 모두 오래 된 것을 개체에 알립니다. 이러한 지침을 따르는 경우 포인터 기반 뷰는 데이터 병렬 배열의 뷰에 제공 된 뷰와 동일 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="array_view"></a><a name="dtor"></a> ~ array_view

개체를 소멸 시킵니다 `array_view` .

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="array_view"></a><a name="ctor"></a> array_view

`array_view` 클래스의 새 인스턴스를 초기화합니다.

```cpp
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Arr_type*<br/>
데이터가 제공 되는 C 스타일 배열의 요소 형식입니다.

*_Container*<br/>
및 멤버를 지 원하는 선형 컨테이너를 지정 해야 하는 템플릿 인수입니다 `data()` `size()` .

*_E0*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E1*<br/>
이 섹션 범위에서 가장 중요 한 구성 요소입니다.

*_E2*<br/>
이 섹션 범위에서 가장 중요 하지 않은 구성 요소입니다.

*_Extent*<br/>
이의 각 차원에 대 한 범위 `array_view` 입니다.

*_Other*<br/>
`array_view<T,N>`새를 초기화할 형식의 개체입니다 `array_view` .

*_Size*<br/>
데이터가 제공 되는 C 스타일 배열의 크기입니다.

*_Src*<br/>
새 배열에 복사 되는 소스 데이터에 대 한 포인터입니다.

## <a name="copy_to"></a><a name="copy_to"></a> copy_to

을 `array_view` 호출 하 여 개체의 내용을 지정 된 대상 개체에 복사 합니다 `copy(*this, dest)` .

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>매개 변수

*_Dest*<br/>
복사할 개체입니다.

## <a name="data"></a><a name="data"></a> 데이터

의 원시 데이터에 대 한 포인터를 반환 합니다 `array_view` .

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>반환 값

`array_view`의 원시 데이터에 대한 포인터입니다.

## <a name="discard_data"></a><a name="discard_data"></a> discard_data

이 뷰를 기반으로 하는 현재 데이터를 삭제 합니다. 이 힌트는 뷰의 현재 콘텐츠를 액세스 하는 대상으로 복사 하는 것을 방지 하는 데 사용 되는 런타임에 대 한 최적화 힌트 `accelerator_view` 이며 기존 콘텐츠가 필요 하지 않은 경우 사용 하는 것이 좋습니다. Restrict (amp) 컨텍스트에서 사용 되는 경우이 메서드는 작동 하지 않습니다.

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a><a name="extent"></a> 됨으로써

`extent` 개체의 모양을 정의하는 `array_view` 개체를 가져옵니다.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a><a name="get_extent"></a> get_extent

개체의 [익스텐트](extent-class.md) 개체를 반환 합니다 `array_view` .

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>반환 값

`extent` 개체의 `array_view` 개체입니다.

## <a name="get_ref"></a><a name="get_ref"></a> get_ref

_Index로 인덱싱된 요소에 대 한 참조를 가져옵니다. CPU의 array_view에 액세스 하는 다른 인덱싱 연산자와는 달리이 메서드는이 array_view의 콘텐츠를 CPU에 암시적으로 동기화 하지 않습니다. 원격 위치에서 array_view에 액세스 하거나이 array_view 관련 된 복사 작업을 수행한 후이 메서드를 호출 하기 전에 사용자가 array_view를 CPU에 명시적으로 동기화 해야 합니다. 이렇게 하지 않으면 정의 되지 않은 동작이 발생 합니다.

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스입니다.

### <a name="return-value"></a>반환 값

_Index로 인덱싱된 요소에 대 한 참조

## <a name="get_source_accelerator_view"></a><a name="get_source_accelerator_view"></a> get_source_accelerator_view

Array_view의 데이터 소스가 있는 accelerator_view 반환 합니다. Array_view에 데이터 원본이 없는 경우이 API는 runtime_exception를 throw 합니다.

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>반환 값

## <a name="operator"></a><a name="operator_call"></a> 연산자 ()

매개 변수에서 지정 하는 요소의 값을 반환 합니다.

```cpp
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
요소의 위치입니다.

*_I0*<br/>
첫 번째 차원의 인덱스입니다.

*_I1*<br/>
두 번째 차원의 인덱스입니다.

*_I2*<br/>
세 번째 차원의 인덱스입니다.

*_I*<br/>
요소의 위치입니다.

### <a name="return-value"></a>반환 값

매개 변수에서 지정 하는 요소의 값입니다.

## <a name="operator"></a><a name="operator_at"></a> operator[]

매개 변수로 지정 된 요소를 반환 합니다.

```cpp
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스입니다.

*_I*<br/>
인덱스입니다.

### <a name="return-value"></a>반환 값

인덱스에 있는 요소의 값 또는 `array_view` 가장 중요 한 차원의 프로젝션입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 개체의 내용을 `array_view` 이 개체에 복사 합니다.

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`array_view`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `array_view` 입니다.

## <a name="rank"></a><a name="rank"></a> 배열

개체의 순위를 저장 `array_view` 합니다.

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a><a name="refresh"></a> 고치십시오

`array_view`바인딩된 메모리가 인터페이스 외부에서 수정 되었음을 개체에 알립니다 `array_view` . 이 메서드에 대 한 호출은 캐시 된 모든 정보를 부실 하 게 렌더링 합니다.

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a><a name="reinterpret_as"></a> reinterpret_as

옵션은 원본 array_view와 다른 값 형식을 가질 수 있는 1 차원 array_view를 통해 array_view를 다시 해석 합니다.

### <a name="syntax"></a>구문

```cpp
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Value_type2*<br/>
새 개체의 데이터 형식 `array_view` 입니다.

### <a name="return-value"></a>반환 값

이를 기반으로 하는 `array_view` 개체 또는 const `array_view` 개체로 `array_view` , 요소 형식이에서로 변환 되 `T` `_Value_type2` 고 순위가 *N* 에서 1로 감소 했습니다.

### <a name="remarks"></a>설명

경우에 따라 다차원 배열을 소스 배열과 다른 값 형식을 가질 수 있는 선형의 1 차원 배열로 보는 것이 편리 합니다. `array_view`이 메서드를 사용 하 여에서이를 수행할 수 있습니다.

**경고** 다른 값 형식을 사용 하 여 array_view 개체를 reinterpeting 안전 하지 않은 작업입니다. 이 기능은 주의 해 서 사용 해야 합니다.

예를 들면 다음과 같습니다.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a><a name="section"></a> 여기서

`array_view`지정 된 원점에 있고, 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션을 반환 합니다.

```cpp
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>반환 값

지정 된 `array_view` 원점에 있고 선택적으로 지정 된 범위를 갖는 개체의 하위 섹션입니다. 개체만 지정 된 경우 `index` 하위 섹션에는 개체의 요소 인덱스 보다 큰 인덱스가 있는 관련 익스텐트의 모든 요소가 포함 됩니다 `index` .

## <a name="source_accelerator_view"></a><a name="source_accelerator_view"></a> source_accelerator_view

이 array_view 연결 된 원본 accelerator_view를 가져옵니다.

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a><a name="synchronize"></a> 항목과

개체에 대 한 수정 내용을 `array_view` 다시 원본 데이터에 동기화 합니다.

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Access_type*<br/>
대상 [accelerator_view](accelerator-view-class.md)에 대 한 의도 된 [access_type](concurrency-namespace-enums-amp.md#access_type) 입니다. 이 매개 변수의 기본값은 `access_type_read` 입니다.

## <a name="synchronize_async"></a><a name="synchronize_async"></a> synchronize_async

개체에 대 한 모든 수정 내용을 `array_view` 다시 소스 데이터에 비동기적으로 동기화 합니다.

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Access_type*<br/>
대상 [accelerator_view](accelerator-view-class.md)에 대 한 의도 된 [access_type](concurrency-namespace-enums-amp.md#access_type) 입니다. 이 매개 변수의 기본값은 `access_type_read` 입니다.

### <a name="return-value"></a>반환 값

작업이 완료 될 때까지 대기 하는 미래입니다.

## <a name="synchronize_to"></a><a name="synchronize_to"></a> synchronize_to

이 array_view에 대 한 모든 수정 내용을 지정 된 accelerator_view와 동기화 합니다.

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Accl_view*<br/>
동기화 할 대상 accelerator_view입니다.

*_Access_type*<br/>
대상 accelerator_view에서 원하는 access_type입니다. 이 매개 변수의 기본값은 access_type_read입니다.

## <a name="synchronize_to_async"></a><a name="synchronize_to_async"></a> synchronize_to_async

이 array_view에 대 한 모든 수정 내용을 지정 된 accelerator_view에 비동기적으로 동기화 합니다.

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Accl_view*<br/>
동기화 할 대상 accelerator_view입니다.

*_Access_type*<br/>
대상 accelerator_view에서 원하는 access_type입니다. 이 매개 변수의 기본값은 access_type_read입니다.

### <a name="return-value"></a>반환 값

작업이 완료 될 때까지 대기 하는 미래입니다.

## <a name="value_type"></a><a name="value_type"></a> value_type

Array_view 및 바인딩된 배열의 값 형식입니다.

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a><a name="view_as"></a> view_as

이를 `array_view` 다른 순위의로 다시 해석 `array_view` 합니다.

```cpp
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_New_rank*<br/>
새 개체의 순위입니다 `array_view` .

*_View_extent*<br/>
변형 `extent` 입니다.

*value_type*<br/>
원래 [배열](array-class.md) 개체와 반환 된 개체 모두에 있는 요소의 데이터 형식입니다 `array_view` .

### <a name="return-value"></a>반환 값

`array_view`생성 되는 개체입니다.

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
