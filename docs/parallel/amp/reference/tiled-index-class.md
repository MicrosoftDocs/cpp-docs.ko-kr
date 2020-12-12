---
description: Tiled_index 클래스에 대해 자세히 알아보세요.
title: tiled_index 클래스
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 072735a9f98efc522c2f054d837d3c2f89e8958b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325826"
---
# <a name="tiled_index-class"></a>tiled_index 클래스

[Tiled_extent](tiled-extent-class.md) 개체에 대 한 인덱스를 제공 합니다. 이 클래스에는 로컬 타일 원본 및 전역 원본에 상대적인 요소에 액세스 하기 위한 속성이 있습니다. 바둑판식 공간에 대 한 자세한 내용은 [타일 사용](../../../parallel/amp/using-tiles.md)을 참조 하세요.

## <a name="syntax"></a>구문

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
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
|[tiled_index 생성자](#ctor)|`tile_index` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|[](extent-class.md) `tiled_index` 템플릿 인수, 및의 값을 갖는 익스텐트 개체를 반환 `_Dim0` 합니다 `_Dim1` `_Dim2` .|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[장벽 상수](#tiled_index__barrier)|현재 스레드의 타일에 장벽을 나타내는 [tile_barrier](tile-barrier-class.md) 개체를 저장 합니다.|
|[전역 상수](#tiled_index__global)|표 개체의 전역 인덱스를 나타내는 차수 1, 2 또는 3의 [index](index-class.md) 개체를 저장 합니다.|
|[local 상수](#tiled_index__local)|`index` [Tiled_extent](tiled-extent-class.md) 개체의 현재 타일의 상대 인덱스를 나타내는 차수 1, 2 또는 3의 개체를 저장 합니다.|
|[rank 상수](#tiled_index__rank)|개체의 순위를 저장 `tiled_index` 합니다.|
|[타일 상수](#tiled_index__tile)|`index`개체의 현재 타일의 좌표를 나타내는 차수 1, 2 또는 3의 개체를 저장 `tiled_extent` 합니다.|
|[tile_dim0 상수](#tiled_index__tile_dim0)|가장 중요 한 차원의 길이를 저장 합니다.|
|[tile_dim1 상수](#tiled_index__tile_dim1)|은 (는) 다음으로 중요 한 차원의 길이를 저장 합니다.|
|[tile_dim2 상수](#tiled_index__tile_dim2)|최하위 차원의 길이를 저장 합니다.|
|[tile_origin 상수](#tiled_index__tile_origin)|`index`개체에서 현재 타일의 원점의 전역 좌표를 나타내는 차수 1, 2 또는 3의 개체를 저장 `tiled_extent` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[tile_extent](#tile_extent)|[](extent-class.md) `tiled_index` 템플릿 인수 `tiled_index` 템플릿 인수 `_Dim0` , `_Dim1` 및의 값을 갖는 익스텐트 개체를 가져옵니다 `_Dim2` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="tiled_index-constructor"></a><a name="ctor"></a> tiled_index 생성자

`tiled_index` 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Global*<br/>
생성 된의 전역 [인덱스](index-class.md) 입니다 `tiled_index` .

*_Local*<br/>
생성 된의 로컬 [인덱스](index-class.md) 입니다. `tiled_index`

*_Tile*<br/>
생성 된의 타일 [인덱스](index-class.md) 입니다. `tiled_index`

*_Tile_origin*<br/>
생성 된의 타일 원점 [인덱스](index-class.md) 입니다. `tiled_index`

*_Barrier*<br/>
생성 된의 [tile_barrier](tile-barrier-class.md) 개체입니다 `tiled_index` .

*_Other*<br/>
`tile_index`생성 된에 복사할 개체 `tiled_index` 입니다.

### <a name="overloads"></a>오버로드

|Name|설명|
|-|-|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|`tile_index`전역 좌표의 타일 인덱스와 로컬 좌표에 있는 타일의 상대 위치에서 클래스의 새 인스턴스를 초기화 합니다. `_Global`및 `_Tile_origin` 매개 변수는 계산 됩니다.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|`tile_index`지정 된 개체를 복사 하 여 클래스의 새 인스턴스를 초기화 `tiled_index` 합니다.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a> get_tile_extent

[](extent-class.md) `tiled_index` 템플릿 인수, 및의 값을 갖는 익스텐트 개체를 반환 `_Dim0` 합니다 `_Dim1` `_Dim2` .

### <a name="syntax"></a>구문

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Return Value

`extent` 템플릿 인수 `tiled_index`, `_Dim0` 및 `_Dim1`의 값을 가진 `_Dim2` 개체입니다.

## <a name="barrier"></a><a name="tiled_index__barrier"></a> 장벽

현재 스레드의 타일에 장벽을 나타내는 [tile_barrier](tile-barrier-class.md) 개체를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a> 전역적

개체의 전역 인덱스를 나타내는 차수 1, 2 또는 3의 [index](index-class.md) 개체를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a> 로컬

[Tiled_extent](tiled-extent-class.md) 개체의 현재 타일의 상대 인덱스를 나타내는 차수 1, 2 또는 3의 [index](index-class.md) 개체를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a> 배열

개체의 순위를 저장 `tiled_index` 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a> 놓기

[Tiled_extent](tiled-extent-class.md) 개체의 현재 타일의 좌표를 나타내는 차수 1, 2 또는 3의 [index](index-class.md) 개체를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a> tile_dim0

가장 중요 한 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a> tile_dim1

은 (는) 다음으로 중요 한 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a> tile_dim2

최하위 차원의 길이를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a> tile_origin

[Tiled_extent](tiled-extent-class.md) 개체 내에서 현재 타일의 원본에 대 한 전역 좌표를 나타내는 차수 1, 2 또는 3의 [index](index-class.md) 개체를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

[](extent-class.md) `tiled_index` 템플릿 인수 `tiled_index` 템플릿 인수 `_Dim0` , `_Dim1` 및의 값을 갖는 익스텐트 개체를 가져옵니다 `_Dim2` .

### <a name="syntax"></a>구문

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
