---
description: '자세히 알아보기: 질감 클래스'
title: texture 클래스
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: d8712f0d8ef3a66c921b63ae938f575e982d3d97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142755"
---
# <a name="texture-class"></a>texture 클래스

질감은 익스텐트 도메인의에 대 한 데이터 집계입니다 `accelerator_view` . 익스텐트 도메인의 각 요소에 대 한 변수의 컬렉션입니다. 각 변수는 c + + 기본 형식 ( **`unsigned int`** , **`int`** , **`float`** , **`double`** ), 스칼라 형식 ( `norm` 또는 `unorm` ) 또는 짧은 벡터 형식에 해당 하는 값을 포함 합니다.

## <a name="syntax"></a>구문

```cpp
template <typename value_type,  int _Rank>
class texture;
```

### <a name="parameters"></a>매개 변수

*value_type*<br/>
질감에 있는 요소의 형식입니다.

*_Rank*<br/>
질감의 순위입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`scalar_type`|스칼라 형식.|
|`value_type`|값 형식.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[질감 생성자](#ctor)|`texture` 클래스의 새 인스턴스를 초기화합니다.|
|[~ 텍스처 소멸자](#ctor)|개체를 소멸 시킵니다 `texture` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[copy_to](#copy_to)|`texture`전체 복사를 수행 하 여 개체를 대상에 복사 합니다.|
|[data](#data)|이 질감의 원시 데이터에 대 한 CPU 포인터를 반환 합니다.|
|[get](#get)|지정 된 인덱스에 있는 요소의 값을 반환 합니다.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|이 질감을 복사할 기본 대상인 [accelerator_view](accelerator-view-class.md) 반환 합니다.|
|[get_depth_pitch](#get_depth_pitch)|CPU의 3D 스테이징 텍스처에서 각 깊이 조각 사이의 바이트 수를 반환 합니다.|
|[get_row_pitch](#get_row_pitch)|CPU의 2D 또는 3D 스테이징 질감에서 각 행 사이의 바이트 수를 반환 합니다.|
|[set](#set)|지정 된 인덱스에 있는 요소의 값을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 ()](#operator_call)|매개 변수로 지정 된 요소 값을 반환 합니다.|
|[연산자\[\]](#operator_at)|지정 된 인덱스에 있는 요소를 반환 합니다.|
|[연산자 =](#operator_eq)|지정 된 [텍스처](texture-class.md) 개체를이 개체에 복사 합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[rank 상수](#rank)|개체의 순위를 가져옵니다 `texture` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|이 질감을 복사할 기본 대상인 [accelerator_view](accelerator-view-class.md) 가져옵니다.|
|[depth_pitch](#depth_pitch)|CPU의 3D 스테이징 텍스처에서 각 깊이 조각 사이의 바이트 수를 가져옵니다.|
|[row_pitch](#row_pitch)|CPU의 2D 또는 3D 스테이징 질감에서 각 행 사이의 바이트 수를 가져옵니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_Texture_base`

`texture`

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics. h

**네임 스페이스:** Concurrency:: graphics

## <a name="texture"></a><a name="dtor"></a> ~ 텍스처

개체를 소멸 시킵니다 `texture` .

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a><a name="associated_accelerator_view"></a> associated_accelerator_view

이 질감을 복사할 기본 대상인 [accelerator_view](accelerator-view-class.md) 가져옵니다.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a><a name="copy_to"></a> copy_to

`texture`전체 복사를 수행 하 여 개체를 대상에 복사 합니다.

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>매개 변수

*_Dest*<br/>
복사할 개체입니다.

*_Rank*<br/>
질감의 순위입니다.

*value_type*<br/>
질감에 있는 요소의 형식입니다.

## <a name="data"></a><a name="data"></a> 데이터

이 질감의 원시 데이터에 대 한 CPU 포인터를 반환 합니다.

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>반환 값

질감의 원시 데이터에 대 한 포인터입니다.

## <a name="depth_pitch"></a><a name="depth_pitch"></a> depth_pitch

CPU의 3D 스테이징 텍스처에서 각 깊이 조각 사이의 바이트 수를 가져옵니다.

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a><a name="get"></a> 가져오기

지정 된 인덱스에 있는 요소의 값을 반환 합니다.

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

지정된 인덱스에 있는 요소의 값입니다.

## <a name="get_associated_accelerator_view"></a><a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

이 질감을 복사할 기본 대상인 accelerator_view 반환 합니다.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>반환 값

이 질감을 복사할 기본 대상인 [accelerator_view](accelerator-view-class.md) 입니다.

## <a name="get_depth_pitch"></a><a name="get_depth_pitch"></a> get_depth_pitch

CPU의 3D 스테이징 텍스처에서 각 깊이 조각 사이의 바이트 수를 반환 합니다.

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>반환 값

CPU의 3D 스테이징 텍스처에서 각 깊이 조각 사이의 바이트 수입니다.

## <a name="get_row_pitch"></a><a name="get_row_pitch"></a> get_row_pitch

2 차원 스테이징 질감에서 각 행 사이의 바이트 수 또는 3 차원 스테이징 질감에서 깊이 조각의 각 행 사이의 바이트 수를 반환 합니다.

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>반환 값

2 차원 스테이징 질감에서 각 행 사이의 바이트 수 또는 3 차원 스테이징 질감에서 깊이 조각의 각 행 사이의 바이트 수입니다.

## <a name="operator"></a><a name="operator_call"></a> 연산자 ()

매개 변수로 지정 된 요소 값을 반환 합니다.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스입니다.

*_I0*<br/>
인덱스의 가장 중요 한 구성 요소입니다.

*_I1*<br/>
인덱스의 다음으로 중요 한 구성 요소입니다.

*_I2*<br/>
인덱스의 가장 중요 하지 않은 구성 요소입니다.

*_Rank*<br/>
인덱스의 순위입니다.

### <a name="return-value"></a>반환 값

매개 변수로 지정 된 요소 값입니다.

## <a name="operator"></a><a name="operator_at"></a> operator[]

지정 된 인덱스에 있는 요소를 반환 합니다.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
인덱스입니다.

*_I0*<br/>
인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 요소입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 [텍스처](texture-class.md) 개체를이 개체에 복사 합니다.

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`texture`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `texture` 입니다.

## <a name="rank"></a><a name="rank"></a> 배열

개체의 순위를 가져옵니다 `texture` .

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a><a name="row_pitch"></a> row_pitch

CPU의 2D 또는 3D 스테이징 질감에서 각 행 사이의 바이트 수를 가져옵니다.

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a><a name="set"></a> 설정

지정 된 인덱스에 있는 요소의 값을 설정 합니다.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
요소의 인덱스입니다.

*_Rank*<br/>
인덱스의 순위입니다.

*value*<br/>
요소의 새 값입니다.

## <a name="texture"></a><a name="ctor"></a> 질감

`texture` 클래스의 새 인스턴스를 초기화합니다.

```cpp
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>매개 변수

*_Acc_view*<br/>
질감의 위치를 지정 하는 [accelerator_view](accelerator-view-class.md) 입니다.

*_Av*<br/>
질감의 위치를 지정 하는 [accelerator_view](accelerator-view-class.md) 입니다.

*_Associated_av*<br/>
이 질감에 대 한 복사의 기본 대상을 지정 하는 accelerator_view입니다.

*_Bits_per_scalar_element*<br/>
질감의 기본 스칼라 형식에 있는 각 스칼라 요소 당 비트 수입니다. 일반적으로 지원 되는 값은 8, 16, 32 및 64입니다. 0을 지정 하면 비트 수는 기본 scalar_type와 동일 합니다. 64는 이중 기반 질감에만 유효 합니다.

*_Ext*<br/>
질감의 각 차원에 대 한 범위입니다.

*_E0*<br/>
질감의 가장 중요 한 구성 요소입니다.

*_E1*<br/>
질감의 다음으로 중요 한 구성 요소입니다.

*_E2*<br/>
질감의 범위에서 가장 중요 하지 않은 구성 요소입니다.

*_Input_iterator*<br/>
입력 반복기의 형식입니다.

*_Mipmap_levels*<br/>
기본 질감의 밉 맵 수준 수입니다. 0을 지정 하면 질감의 전체 범위는 지정 된 범위에 대 한 가능한 가장 작은 크기의 밉로 축소 됩니다.

*_Rank*<br/>
익스텐트의 순위입니다.

*_Source*<br/>
호스트 버퍼에 대 한 포인터입니다.

*_Src*<br/>
복사할 질감입니다.

*_Src_byte_size*<br/>
원본 버퍼의 바이트 수입니다.

*_Src_first*<br/>
소스 컨테이너에 대 한 시작 반복기입니다.

*_Src_last*<br/>
소스 컨테이너에 대 한 종료 반복기입니다.

*_Other*<br/>
기타 데이터 원본.

*_Rank*<br/>
섹션의 순위입니다.

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
