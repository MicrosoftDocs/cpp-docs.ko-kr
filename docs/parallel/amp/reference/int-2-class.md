---
description: Int_2 클래스에 대해 자세히 알아보세요.
title: int_2 클래스
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
ms.openlocfilehash: 7ee3f2726ce5c96a51a8246933c8d2d9d9eacc38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330034"
---
# <a name="int_2-class"></a>int_2 클래스

두 정수의 short 벡터를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class int_2;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[int_2 생성자](#ctor)|오버로드됨. 기본 생성자는 0으로 모든 요소를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|int_2:: get_x||
|int_2:: get_xy||
|int_2:: get_y||
|int_2:: get_yx||
|int_2:: ref_g||
|int_2:: ref_r||
|int_2:: ref_x||
|int_2:: ref_y||
|int_2:: set_x||
|int_2:: set_xy||
|int_2:: set_y||
|int_2:: set_yx||

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|int_2:: operator-||
|int_2:: operator--||
|int_2:: operator% =||
|int_2:: operator&=||
|int_2:: operator * =||
|int_2:: operator/=||
|int_2:: operator ^ =||
|int_2:: operator&#124;=||
|int_2:: operator ~||
|int_2:: operator + +||
|int_2:: operator + =||
|int_2:: operator<\<=||
|int_2:: operator =||
|int_2:: operator-=||
|int_2:: operator>>=||

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[크기 상수](#int_2__size)||

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|int_2:: g||
|int_2:: gr||
|int_2:: r||
|int_2:: rg||
|int_2:: x||
|int_2:: xy||
|int_2:: y||
|int_2:: yx||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`int_2`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="int_2"></a><a name="ctor"></a> int_2

기본 생성자는 0으로 모든 요소를 초기화 합니다.

```cpp
int_2() restrict(amp,
    cpu);

int_2(
    int _V0,
    int _V1) restrict(amp,
    cpu);

int_2(
    int _V) restrict(amp,
    cpu);

int_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
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

## <a name="size"></a><a name="int_2__size"></a> 크기가

```cpp
static const int size = 2;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
