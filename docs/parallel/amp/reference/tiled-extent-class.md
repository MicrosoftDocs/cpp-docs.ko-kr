---
description: Tiled_extent 클래스에 대해 자세히 알아보세요.
title: tiled_extent 클래스
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: ca5b5c630152263ca49adf5c201ee0b892a192c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163875"
---
# <a name="tiled_extent-class"></a>tiled_extent 클래스

`tiled_extent`개체는 `extent` 익스텐트 공간을 1, 2 또는 3 차원 타일로 세분 하는 1 ~ 3 차원에 대 한 개체입니다.

## <a name="syntax"></a>구문

```cpp
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
```

### <a name="parameters"></a>매개 변수

*_Dim0*<br/>
가장 중요 한 차원의 길이입니다.

*_Dim1*<br/>
다음으로 중요 한 차원의 길이입니다.

*_Dim2*<br/>
최하위 차원의 길이입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[tiled_extent 생성자](#ctor)|`tiled_extent` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|`extent` `tiled_extent` 템플릿 인수, 및의 값을 캡처하는 개체를 반환 합니다 `_Dim0` `_Dim1` `_Dim2` .|
|[여백](#pad)|`tiled_extent`타일 크기에 따라 균등 하 게 나눌 수 있도록 익스텐트가 조정 된 새 개체를 반환 합니다.|
|[truncate](#truncate)|`tiled_extent`타일 크기에 따라 균등 하 게 나눌 수 있도록 범위를 조정 하 여 새 개체를 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `tiled_index` 여기로 복사 합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[tile_dim0 상수](#tile_dim0)|가장 중요 한 차원의 길이를 저장 합니다.|
|[tile_dim1 상수](#tile_dim1)|은 (는) 다음으로 중요 한 차원의 길이를 저장 합니다.|
|[tile_dim2 상수](#tile_dim2)|최하위 차원의 길이를 저장 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[tile_extent](#tile_extent)|`extent` `tiled_extent` 템플릿 인수, 및의 값을 캡처하는 개체를 `_Dim0` 가져옵니다 `_Dim1` `_Dim2` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`extent`

`tiled_extent`

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="tiled_extent-constructor"></a><a name="ctor"></a> tiled_extent 생성자

`tiled_extent` 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`extent`복사할 또는 `tiled_extent` 개체입니다.

## <a name="get_tile_extent"></a><a name="get_tile_extent"></a> get_tile_extent

`extent` `tiled_extent` 템플릿 인수, 및의 값을 캡처하는 개체를 반환 합니다 `_Dim0` `_Dim1` `_Dim2` .

### <a name="syntax"></a>구문

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Return Value

`extent`이 인스턴스의 크기를 캡처하는 개체 `tiled_extent` 입니다.

## <a name="pad"></a><a name="pad"></a> 패드

`tiled_extent`타일 크기에 따라 균등 하 게 나눌 수 있도록 익스텐트가 조정 된 새 개체를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Return Value

`tiled_extent`값을 기준으로 하는 새 개체입니다.

## <a name="truncate"></a><a name="truncate"></a> 자르기

`tiled_extent`타일 크기에 따라 균등 하 게 나눌 수 있도록 범위를 조정 하 여 새 개체를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Return Value

`tiled_extent`타일 크기에 따라 균등 하 게 나눌 수 있도록 범위를 조정 하 여 새 개체를 반환 합니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 개체의 내용을 `tiled_index` 여기로 복사 합니다.

### <a name="syntax"></a>구문

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`tiled_index`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 인스턴스에 대 한 참조 `tiled_index` 입니다.

## <a name="tile_dim0"></a><a name="tile_dim0"></a> tile_dim0

가장 중요 한 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"></a> tile_dim1

은 (는) 다음으로 중요 한 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"></a> tile_dim2

최하위 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

`extent` `tiled_extent` 템플릿 인수, 및의 값을 캡처하는 개체를 `_Dim0` 가져옵니다 `_Dim1` `_Dim2` .

### <a name="syntax"></a>구문

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
