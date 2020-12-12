---
description: Double_2 클래스에 대해 자세히 알아보세요.
title: double_2 클래스
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
ms.openlocfilehash: 104fef0c035487570a23360c312684ef176f69ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297131"
---
# <a name="double_2-class"></a>double_2 클래스

2 double의 짧은 벡터를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class double_2;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[double_2 생성자](#ctor)|오버로드됨. 기본 생성자는 0으로 모든 요소를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|double_2:: get_x||
|double_2:: get_xy||
|double_2:: get_y||
|double_2:: get_yx||
|double_2:: ref_g||
|double_2:: ref_r||
|double_2:: ref_x||
|double_2:: ref_y||
|double_2:: set_x||
|double_2:: set_xy||
|double_2:: set_y||
|double_2:: set_yx||

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|double_2:: operator-||
|double_2:: operator--||
|double_2:: operator * =||
|double_2:: operator/=||
|double_2:: operator + +||
|double_2:: operator + =||
|double_2:: operator =||
|double_2:: operator-=||

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|double_2::size 상수||

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|double_2:: g||
|double_2:: gr||
|double_2:: r||
|double_2:: rg||
|double_2:: x||
|double_2:: xy||
|double_2:: y||
|double_2:: yx||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`double_2`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="double_2"></a><a name="ctor"></a> double_2

기본 생성자는 0으로 모든 요소를 초기화 합니다.

```cpp
double_2() restrict(amp,
    cpu);

double_2(
    double _V0,
    double _V1) restrict(amp,
    cpu);

double_2(
    double _V) restrict(amp,
    cpu);

double_2(
    const double_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const norm_2& _Other) restrict(amp,
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

## <a name="size"></a><a name="double_2__size"></a> 크기가

```cpp
static const int size = 2;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
