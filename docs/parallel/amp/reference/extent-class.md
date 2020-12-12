---
description: '자세한 정보: 익스텐트 클래스 (C++ AMP)'
title: extent 클래스(C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: fb355d0ab0676256df42a880722ebaac33eb3cb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325865"
---
# <a name="extent-class-c-amp"></a>extent 클래스(C++ AMP)

원점이 0 인 *n* 차원 공간의 경계를 지정 하는 *n* 정수 값의 벡터를 나타냅니다. 벡터의 값은 가장 중요 한 값부터 최하위 순서로 정렬 됩니다.

## <a name="syntax"></a>구문

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>매개 변수

*_Rank*<br/>
개체의 순위입니다 `extent` .

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[익스텐트 생성자](#ctor)|`extent` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[contains](#contains)|지정 된 개체에 `extent` 지정 된 순위가 있는지 확인 합니다.|
|[size](#size)|범위의 전체 선형 크기 (요소 단위)를 반환 합니다.|
|[놓기](#tile)|`tiled_extent`지정 된 차원에서 제공 하는 타일 익스텐트를 사용 하 여 개체를 생성 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자](#operator_min)|`extent` `index` 해당 요소에서 요소를 빼서 만들어진 새 개체를 반환 합니다 `extent` .|
|[연산자--](#operator_min_min)|개체의 각 요소를 감소 시킵니다 `extent` .|
|[연산자% =](#operator_mod_eq)|`extent`해당 요소를 숫자로 나눌 때 개체에 있는 각 요소의 모듈러스 (나머지)를 계산 합니다.|
|[연산자 * =](#operator_star_eq)|개체의 각 요소 `extent` 를 숫자로 곱합니다.|
|[operator/=](#operator_min_eq)|개체의 각 요소 `extent` 를 숫자로 나눕니다.|
|[익스텐트:: operator\[\]](#operator_at)|지정 된 인덱스에 있는 요소를 반환 합니다.|
|[연산자 +](#operator_add)|`extent`해당 및 요소를 추가 하 여 만들어진 새 개체를 반환 합니다 `index` `extent` .|
|[operator + +](#operator_add_add)|개체의 각 요소를 증가 시킵니다 `extent` .|
|[operator + =](#operator_add_eq)|개체의 각 요소에 지정 된 숫자를 추가 `extent` 합니다.|
|[연산자 =](#operator_eq)|다른 개체의 내용을 `extent` 여기로 복사 합니다.|
|[연산자-=](#operator_min_eq)|개체의 각 요소에서 지정한 수를 뺍니다 `extent` .|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[rank 상수](#rank_constant)|개체의 순위를 가져옵니다 `extent` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`extent`

## <a name="contains"></a><a name="contains"></a> 에서는

지정 된 [인덱스](index-class.md) 값이 ' 익스텐트 ' 개체에 포함 되어 있는지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
테스트할 `index` 값입니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 *인덱스* 값이 개체에 포함 되어 있으면 `extent` 이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="extent"></a><a name="ctor"></a> 됨으로써

' 익스텐트 ' 클래스의 새 인스턴스를 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Array*<br/>
`_Rank`새 개체를 만드는 데 사용 되는 정수 배열입니다 `extent` .

*_I*<br/>
범위의 길이입니다.

*_I0*<br/>
가장 중요 한 차원의 길이입니다.

*_I1*<br/>
다음으로 중요 한 차원의 길이입니다.

*_I2*<br/>
최하위 차원의 길이입니다.

*_Other*<br/>
`extent`새 개체의 기반이 되는 개체입니다 `extent` .

## <a name="remarks"></a>설명

기본 생성자는 차수가 3 인 개체를 초기화 합니다 `extent` .

배열을 사용 하 여 개체를 생성 하는 경우 `extent` 배열의 길이는 개체의 차수와 일치 해야 합니다 `extent` .

## <a name="operator"></a><a name="operator_mod_eq"></a> 연산자% =

' 범위 '에서 요소를 숫자로 나눌 때 각 요소의 모듈러스 (나머지)를 계산 합니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
모듈러스를 찾기 위한 숫자입니다.

### <a name="return-value"></a>반환 값

`extent` 개체

## <a name="operator"></a><a name="operator_star_eq"></a> 연산자 * =

' 익스텐트 ' 개체의 각 요소를 지정 된 수 만큼 곱합니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
곱할 숫자입니다.

### <a name="return-value"></a>반환 값

`extent` 개체

## <a name="operator"></a><a name="operator_add"></a> 연산자 +

`extent`해당 및 요소를 추가 하 여 만든 새 개체를 반환 합니다 `index` `extent` .

### <a name="syntax"></a>구문

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
`index`추가할 요소를 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

새로운 `extent` 개체입니다.

## <a name="operator"></a><a name="operator_add_add"></a> operator + +

' 익스텐트 ' 개체의 각 요소를 증가 시킵니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Return Value

전위 연산자의 경우 `extent` 개체 ( **`*this`** )입니다. 접미사 연산자의 경우 새 `extent` 개체입니다.

## <a name="operator"></a><a name="operator_add_eq"></a> operator + =

' 익스텐트 ' 개체의 각 요소에 지정한 수를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
더할 숫자, 인덱스 또는 범위입니다.

### <a name="return-value"></a>반환 값

결과 `extent` 개체입니다.

## <a name="operator-"></a><a name="operator_min"></a> 연산자

`extent` `index` 이 개체의 해당 요소에서 지정 된 개체의 각 요소를 빼서 새 개체를 만듭니다 `extent` .

### <a name="syntax"></a>구문

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
`index`뺄 요소를 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

새로운 `extent` 개체입니다.

## <a name="operator--"></a><a name="operator_min_min"></a> 연산자--

' 익스텐트 ' 개체의 각 요소를 감소 시킵니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Return Value

전위 연산자의 경우 `extent` 개체 ( **`*this`** )입니다. 접미사 연산자의 경우 새 `extent` 개체입니다.

## <a name="operator"></a><a name="operator_div_eq"></a> operator/=

' 익스텐트 ' 개체의 각 요소를 지정 된 수 만큼 나눕니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
나눌 숫자입니다.

### <a name="return-value"></a>반환 값

`extent` 개체

## <a name="operator-"></a><a name="operator_min_eq"></a> 연산자-=

' 익스텐트 ' 개체의 각 요소에서 지정한 수를 뺍니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
뺄 숫자입니다.

### <a name="return-value"></a>반환 값

결과 `extent` 개체입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

다른 ' 익스텐트 ' 개체의 내용을 여기로 복사 합니다.

### <a name="syntax"></a>구문

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`extent`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `extent` 입니다.

## <a name="extentoperator-"></a><a name="operator_at"></a> 익스텐트:: operator \[\]

지정 된 인덱스에 있는 요소를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
0에서 순위에서 1을 뺀 값 사이의 정수입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 요소입니다.

## <a name="rank"></a><a name="rank_constant"></a> 배열

' 익스텐트 ' 개체의 순위를 저장 합니다.

### <a name="syntax"></a>Syntax

```cpp
static const int rank = _Rank;
```

## <a name="size"></a><a name="size"></a> 크기가

`extent` 개체(요소의 단위에서)의 총 선형 크기 단위를 반환합니다.

### <a name="syntax"></a>Syntax

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a><a name="tile"></a> 놓기

지정 된 타일 크기를 사용 하 여 tiled_extent 개체를 생성 합니다.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>매개 변수

*_Dim0*<br/>
바둑판식으로 배열 된 범위의 가장 중요 한 구성 요소입니다.
*_Dim1*<br/>
바둑판식으로 배열 된 범위에서 다음으로 중요 한 구성 요소입니다.
*_Dim2*<br/>
바둑판식으로 배열 된 범위의 가장 중요 하지 않은 구성 요소입니다.

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
