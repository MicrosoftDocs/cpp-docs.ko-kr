---
description: Texture_view 클래스에 대해 자세히 알아보세요.
title: texture_view 클래스
ms.date: 11/04/2016
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: e2c96f2fbddb5d2dc39a1e2e39fe5a0af656176a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321723"
---
# <a name="texture_view-class"></a>texture_view 클래스

질감에 대 한 읽기 권한 및 쓰기 권한을 제공 합니다. `texture_view` 는 값 형식이 **`int`** , **`unsigned int`** 또는 이며 **`float`** 기본 32 비트 bpse가 있는 질감을 읽는 데만 사용할 수 있습니다. 다른 질감 형식을 읽으려면를 사용 `texture_view<const value_type, _Rank>` 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>매개 변수

*value_type*<br/>
질감 집계에 있는 요소의 형식입니다.

*_Rank*<br/>
의 순위 `texture_view` 입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`|질감 집계에 있는 요소의 형식입니다.|
|`coordinates_type`|의 텍셀를 지정 하는 데 사용 되는 좌표 형식입니다 `texture_view` . 즉, `short_vector` 값 형식이 인 연결 된 질감과 순위가 같은입니다 **`float`** .|
|`gather_return_type`|수집 작업에 사용 되는 반환 형식입니다. 즉, 샘플링 된 `short_vector` 4 개의 텍셀 값에서 수집 된 4 개의 동종 색 구성 요소를 보유 하는 랭크 4입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[texture_view 생성자](#ctor)|오버로드됨. 인스턴스를 생성 `texture_view` 합니다.|
|[~ texture_view 소멸자](#ctor)|인스턴스를 소멸 시킵니다 `texture_view` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|오버로드됨. 지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 알파 (w) 구성 요소를 반환 합니다.|
|[gather_blue](#gather_blue)|오버로드됨. 지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 파란색 (z) 구성 요소를 반환 합니다.|
|[gather_green](#gather_green)|오버로드됨. 지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 녹색 (y) 구성 요소를 반환 합니다.|
|[gather_red](#gather_red)|오버로드됨. 지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 빨간색 (x) 구성 요소를 반환 합니다.|
|[get](#get)|오버로드됨. 인덱스를 기준으로 요소 값을 가져옵니다.|
|[샘플이](#sample)|오버로드됨. 지정 된 샘플링 구성을 사용 하 여 지정 된 좌표와 세부 수준에서 질감을 샘플링 합니다.|
|[set](#set)|인덱스를 기준으로 요소의 값을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 ()](#operator_call)|오버로드됨. 인덱스를 기준으로 요소 값을 가져옵니다.|
|[연산자\[\]](#operator_at)|오버로드됨. 인덱스를 기준으로 요소 값을 가져옵니다.|
|[연산자 =](#operator_eq)|오버로드됨. 대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[value_type](#value_type)|의 요소에 대 한 값 형식입니다 `texture_view` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_Texture_base`

`texture_view`

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics. h

**네임 스페이스:** concurrency:: graphics

## <a name="texture_view"></a><a name="dtor"></a> ~ texture_view

인스턴스를 소멸 시킵니다 `texture_view` .

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="texture_view"></a><a name="ctor"></a> texture_view

인스턴스를 생성 `texture_view` 합니다.

```cpp
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>매개 변수

*_Src*<br/>
[1, 2] `texture` 쓰기 가능한을 만드는 생성자입니다 `texture_view` .

[3, 4] 쓰기 불가능 한을 만드는 생성자입니다 `texture` `texture_view` .

*_Other*<br/>
[5] 소스를 쓸 수 있는 복사 생성자 `texture_view` 입니다.

[6, 7] 복사 생성자에 쓸 수 없는 소스 `texture_view` 입니다.

*_Mipmap_level*<br/>
이 쓰기 가능한 소스에 대 한 특정 밉 맵 수준 `texture` `texture_view` 입니다. 기본값은 최상위 수준 (가장 자세한) 밉 수준을 나타내는 0입니다.

*_Most_detailed_mip*<br/>
지정 된 개체를 기준으로 하는 최상위 수준 (가장 자세) 보기의 밉 수준 `texture_view` 입니다.

*_Mip_levels*<br/>
를 통해 액세스할 수 있는 밉 맵 수준 수입니다 `texture_view` .

## <a name="gather_red"></a><a name="gather_red"></a> gather_red

지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 빨간색 (x) 구성 요소를 반환 합니다.

```cpp
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Address_mode*<br/>
를 샘플링 하는 데 사용할 주소 모드 `texture_view` 입니다. 주소 모드는 모든 차원에 대해 동일 합니다.

*_Sampler*<br/>
를 샘플링 하는 데 사용할 샘플러 구성 `texture_view` 입니다.

*_Coord*<br/>
샘플을 가져올 좌표입니다. 소수 좌표 값은 샘플 텍셀 사이를 보간 하는 데 사용 됩니다.

### <a name="return-value"></a>반환 값

샘플링 된 텍셀 값 4 개의 빨강 (x) 구성 요소를 포함 하는 차수 4 short 벡터입니다.

## <a name="gather_green"></a><a name="gather_green"></a> gather_green

지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 녹색 (y) 구성 요소를 반환 합니다.

```cpp
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Address_mode*<br/>
를 샘플링 하는 데 사용할 주소 모드 `texture_view` 입니다. 주소 모드는 모든 차원에 대해 동일 합니다.

*_Sampler*<br/>
를 샘플링 하는 데 사용할 샘플러 구성 `texture_view` 입니다.

*_Coord*<br/>
샘플을 가져올 좌표입니다. 소수 좌표 값은 샘플 텍셀 사이를 보간 하는 데 사용 됩니다.

### <a name="return-value"></a>반환 값

샘플링 된 4 개의 텍셀 값의 녹색 (y) 구성 요소를 포함 하는 차수 4 short 벡터입니다.

## <a name="gather_blue"></a><a name="gather_blue"></a> gather_blue

지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 파란색 (z) 구성 요소를 반환 합니다.

```cpp
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Address_mode*<br/>
를 샘플링 하는 데 사용할 주소 모드 `texture_view` 입니다. 주소 모드는 모든 차원에 대해 동일 합니다.

*_Sampler*<br/>
를 샘플링 하는 데 사용할 샘플러 구성 `texture_view` 입니다.

*_Coord*<br/>
샘플을 가져올 좌표입니다. 소수 좌표 값은 샘플 텍셀 사이를 보간 하는 데 사용 됩니다.

### <a name="return-value"></a>반환 값

샘플링 된 텍셀 값 4 개의 빨강 (x) 구성 요소를 포함 하는 차수 4 short 벡터입니다.

## <a name="gather_alpha"></a><a name="gather_alpha"></a> gather_alpha

지정 된 샘플링 구성을 사용 하 여 지정 된 좌표에 질감을 샘플링 하 고 4 개의 샘플링 된 텍셀의 알파 (w) 구성 요소를 반환 합니다.

```cpp
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Address_mode*<br/>
를 샘플링 하는 데 사용할 주소 모드 `texture_view` 입니다. 주소 모드는 모든 차원에 대해 동일 합니다.

*_Sampler*<br/>
를 샘플링 하는 데 사용할 샘플러 구성 `texture_view` 입니다.

*_Coord*<br/>
샘플을 가져올 좌표입니다. 소수 좌표 값은 샘플 텍셀 사이를 보간 하는 데 사용 됩니다.

### <a name="return-value"></a>반환 값

샘플링 된 텍셀 값 4 개의 알파 (w) 구성 요소를 포함 하는 차수 4 short 벡터입니다.

## <a name="get"></a><a name="get"></a> 가져오기

지정 된 인덱스에 있는 요소의 값을 가져옵니다.

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
가져올 요소의 인덱스입니다. 다차원 일 수도 있습니다.

*_Mip_level*<br/>
값을 가져와야 하는 밉 맵 수준입니다. 기본값 0은 가장 자세한 밉 맵 수준을 나타냅니다.

### <a name="return-value"></a>반환 값

요소의 값입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된와 동일한 질감의 뷰를 `texture_view` 이 인스턴스에 할당 합니다 `texture_view` .

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
[1, 2] 쓰기 가능한 개체를 복사 생성자로 복사 `texture_view` 합니다.

[3] 쓰기 불가능 한 개체를 복사 하는 생성자 `texture_view` 입니다.

### <a name="return-value"></a>반환 값

이 인스턴스에 대 한 참조 `texture_view` 입니다.

## <a name="operator"></a><a name="operator_at"></a> operator[]

인덱스를 기준으로 요소 값을 반환 합니다.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스가 다차원 일 수 있습니다.

*_I0*<br/>
1 차원 인덱스입니다.

### <a name="return-value"></a>반환 값

로 인덱싱된 요소 값 `_Index` 입니다.

## <a name="operator"></a><a name="operator_call"></a> 연산자 ()

인덱스를 기준으로 요소 값을 반환 합니다.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스가 다차원 일 수 있습니다.

*_I0*<br/>
인덱스의 가장 중요 한 구성 요소입니다.

*_I1*<br/>
인덱스의 다음으로 중요 한 구성 요소입니다.

*_I2*<br/>
인덱스의 가장 중요 하지 않은 구성 요소입니다.

### <a name="return-value"></a>반환 값

로 인덱싱된 요소 값 `_Index` 입니다.

## <a name="sample"></a><a name="sample"></a> 샘플이

지정 된 샘플링 구성을 사용 하 여 지정 된 좌표와 세부 수준에서 질감을 샘플링 합니다.

```cpp
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Filter_mode*<br/>
Texture_view를 샘플링 하는 데 사용 하는 필터 모드입니다. 필터 모드는 최소화, maximization 및 밉 맵 필터에 대해 동일 합니다.

*_Address_mode*<br/>
Texture_view를 샘플링 하는 데 사용할 주소 모드입니다. 주소 모드는 모든 차원에 대해 동일 합니다.

*_Sampler*<br/>
Texture_view를 샘플링 하는 데 사용할 샘플러 구성입니다.

*_Coord*<br/>
샘플을 가져올 좌표입니다. 소수 좌표 값은 텍셀 값 사이에 보간 하는 데 사용 됩니다.

*_Level_of_detail*<br/>
값은 샘플링할 밉 맵 수준을 지정 합니다. 소수 값은 두 개의 밉 맵 수준 간을 보간 하는 데 사용 됩니다. 기본 수준의 세부 정보는 0 이며 가장 자세한 밉 수준을 나타냅니다.

### <a name="return-value"></a>반환 값

보간된 샘플 값입니다.

## <a name="set"></a><a name="set"></a> 설정

지정 된 인덱스에 있는 요소의 값을 지정 된 값으로 설정 합니다.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
설정할 요소의 인덱스입니다. 다차원 일 수 있습니다.

*value*<br/>
요소를 설정할 값입니다.

## <a name="value_type"></a><a name="value_type"></a> value_type

Texture_view의 요소에 대 한 값 형식입니다.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
