---
description: Norm_2 클래스에 대해 자세히 알아보세요.
title: norm_2 클래스
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
ms.openlocfilehash: 5b4b19d83672a88828d3cad8be7f22a2f54a431e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329982"
---
# <a name="norm_2-class"></a>norm_2 클래스

두 일반 숫자의 짧은 벡터를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class norm_2;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[norm_2 생성자](#ctor)|오버로드됨. 기본 생성자는 0으로 모든 요소를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|norm_2:: get_x||
|norm_2:: get_xy||
|norm_2:: get_y||
|norm_2:: get_yx||
|norm_2:: ref_g||
|norm_2:: ref_r||
|norm_2:: ref_x||
|norm_2:: ref_y||
|norm_2:: set_x||
|norm_2:: set_xy||
|norm_2:: set_y||
|norm_2:: set_yx||

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|norm_2:: operator-||
|norm_2:: operator--||
|norm_2:: operator * =||
|norm_2:: operator/=||
|norm_2:: operator + +||
|norm_2:: operator + =||
|norm_2:: operator =||
|norm_2:: operator-=||

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[크기 상수](#norm_2__size)||

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|norm_2:: g||
|norm_2:: gr||
|norm_2:: r||
|norm_2:: rg||
|norm_2:: x||
|norm_2:: xy||
|norm_2:: y||
|norm_2:: yx||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`norm_2`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="norm_2"></a><a name="ctor"></a> norm_2

기본 생성자는 0으로 모든 요소를 초기화 합니다.

```cpp
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
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

## <a name="size"></a><a name="norm_2__size"></a> 크기가

```cpp
static const int size = 2;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
