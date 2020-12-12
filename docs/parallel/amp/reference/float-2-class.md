---
description: Float_2 클래스에 대해 자세히 알아보세요.
title: float_2 클래스
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
ms.openlocfilehash: a0d350c9742da6c11a5bf982a1638a1fc0921eb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325852"
---
# <a name="float_2-class"></a>float_2 클래스

두 float의 짧은 벡터를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class float_2;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[float_2 생성자](#ctor)|오버로드됨. 기본 생성자는 0으로 모든 요소를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|float_2:: get_x||
|float_2:: get_xy||
|float_2:: get_y||
|float_2:: get_yx||
|float_2:: ref_g||
|float_2:: ref_r||
|float_2:: ref_x||
|float_2:: ref_y||
|float_2:: set_x||
|float_2:: set_xy||
|float_2:: set_y||
|float_2:: set_yx||

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|float_2:: operator-||
|float_2:: operator--||
|float_2:: operator * =||
|float_2:: operator/=||
|float_2:: operator + +||
|float_2:: operator + =||
|float_2:: operator =||
|float_2:: operator-=||

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[크기 상수](#float_2__size)||

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|float_2:: g||
|float_2:: gr||
|float_2:: r||
|float_2:: rg||
|float_2:: x||
|float_2:: xy||
|float_2:: y||
|float_2:: yx||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`float_2`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="float_2"></a><a name="ctor"></a> float_2

기본 생성자는 0으로 모든 요소를 초기화 합니다.

```cpp
float_2() restrict(amp,
    cpu);

float_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

float_2(
    float _V) restrict(amp,
    cpu);

float_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>매개 변수

*_V0*<br/>
요소 0을 초기화할 값입니다.

*_V1*<br/>
요소 1을 초기화할 값입니다.

*_V*<br/>
초기화에 대 한 값입니다.

*_Other*<br/>
을 초기화 하는 데 사용 되는 개체입니다.

## <a name="size"></a><a name="float_2__size"></a> 크기가

```cpp
static const int size = 2;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
