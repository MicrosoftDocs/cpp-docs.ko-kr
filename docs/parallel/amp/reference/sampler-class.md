---
description: '자세히 알아보기: 샘플러 클래스'
title: sampler 클래스
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 61292cccb9e28ca76dc4ecaa1aaca849d9219ffc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327614"
---
# <a name="sampler-class"></a>sampler 클래스

샘플러 클래스는 질감 샘플링에 사용할 샘플링 구성 정보를 집계 합니다.

## <a name="syntax"></a>구문

```cpp
class sampler;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[샘플러 생성자](#ctor)|오버로드됨. 샘플러 인스턴스를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|`address_mode`샘플러 개체와 연결 된를 반환 합니다.|
|[get_border_color](#get_border_color)|샘플러 개체와 연결 된 테두리 색을 반환 합니다.|
|[get_filter_mode](#get_filter_mode)|`filter_mode`샘플러 개체와 연결 된를 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|오버로드됨. 대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[address_mode](#address_mode)|개체의 주소 모드를 가져옵니다 `sampler` .|
|[border_color](#border_color)|개체의 테두리 색을 가져옵니다 `sampler` .|
|[filter_mode](#filter_mode)|개체의 필터 모드를 가져옵니다 `sampler` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`sampler`

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics. h

**네임 스페이스:** concurrency:: graphics

## <a name="sampler"></a><a name="ctor"></a> 샘플러

[샘플러 클래스](sampler-class.md)의 인스턴스를 생성 합니다.

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>매개 변수

*_Filter_mode*<br/>
샘플링에 사용 되는 필터 모드입니다.

*_Address_mode*<br/>
모든 차원에 대해 샘플링에 사용 되는 주소 지정 모드입니다.

*_Border_color*<br/>
주소 모드가 address_border 때 사용할 테두리 색입니다. 기본값은 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`입니다.

*_Other*<br/>
[5] `sampler` 새 인스턴스에 복사할 개체를 복사 하는 생성자 `sampler` 입니다.

[6] 생성자 이동 `sampler` 개체를 새 `sampler` 인스턴스로 이동 합니다.

## <a name="address_mode"></a><a name="address_mode"></a> address_mode

개체의 주소 모드를 가져옵니다 `sampler` .

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a><a name="border_color"></a> border_color

개체의 테두리 색을 가져옵니다 `sampler` .

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a><a name="filter_mode"></a> filter_mode

개체의 필터 모드를 가져옵니다 `sampler` .

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a><a name="get_address_mode"></a> get_address_mode

이에 대해 구성 된 필터 모드를 반환 `sampler` 합니다.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>반환 값

샘플러에 대해 구성 된 주소 모드입니다.

## <a name="get_border_color"></a><a name="get_border_color"></a> get_border_color

이에 대해 구성 된 테두리 색을 반환 합니다 `sampler` .

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>반환 값

테두리 색을 포함 하는 float_4입니다.

## <a name="get_filter_mode"></a><a name="get_filter_mode"></a> get_filter_mode

이에 대해 구성 된 필터 모드를 반환 `sampler` 합니다.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>반환 값

샘플러에 대해 구성 된 필터 모드입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

다른 샘플러 개체의 값을 기존 샘플러에 할당 합니다.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
[1] `sampler` 이에 복사할 개체에 대 한 복사 할당 연산자 `sampler` 입니다.

[2] `sampler` 이로 이동 하는 개체를 이동 `sampler` 합니다.

### <a name="return-value"></a>반환 값

이 샘플러 인스턴스에 대 한 참조입니다.

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
