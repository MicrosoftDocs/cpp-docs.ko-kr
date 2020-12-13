---
description: '자세한 정보: 인덱스 클래스'
title: index 클래스
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 46b49a7e0f65f06ad64ed32367cdfe6f6ca5ed1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330051"
---
# <a name="index-class"></a>index 클래스

*N* 차원 인덱스 벡터를 정의 합니다.

## <a name="syntax"></a>구문

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>매개 변수

*_Rank*<br/>
차수 또는 차원 수입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[인덱스 생성자](#index_ctor)|`index` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자--](#operator--)|개체의 각 요소를 감소 시킵니다 `index` .|
|[연산자% =](#operator_mod_eq)|`index`해당 요소를 숫자로 나눌 때 개체에 있는 각 요소의 모듈러스 (나머지)를 계산 합니다.|
|[연산자 * =](#operator_star_eq)|개체의 각 요소 `index` 를 숫자로 곱합니다.|
|[operator/=](#operator_div_eq)|개체의 각 요소 `index` 를 숫자로 나눕니다.|
|[index:: operator\[\]](#operator_at)|지정 된 인덱스에 있는 요소를 반환 합니다.|
|[operator + +](#operator_add_add)|개체의 각 요소를 증가 시킵니다 `index` .|
|[operator + =](#operator_add_eq)|개체의 각 요소에 지정 된 숫자를 추가 `index` 합니다.|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `index` 여기로 복사 합니다.|
|[연산자-=](#operator_-_eq)|개체의 각 요소에서 지정한 수를 뺍니다 `index` .|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[rank 상수](#rank)|개체의 순위를 저장 `index` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`index`

## <a name="remarks"></a>설명

구조체는 n `index` 차원 공간에서 고유 위치를 지정 하는 *n* 정수의 좌표 벡터 를 나타냅니다. 벡터의 값은 가장 중요 한 값부터 최하위 순서로 정렬 됩니다. [Operator =](#operator_eq)를 사용 하 여 구성 요소의 값을 검색할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="index-constructor"></a><a name="index_ctor"></a> 인덱스 생성자

Index 클래스의 새 인스턴스를 초기화 합니다.

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Array*<br/>
Rank 값을 포함 하는 1 차원 배열입니다.

*_I*<br/>
1 차원 인덱스의 인덱스 위치입니다.

*_I0*<br/>
가장 중요 한 차원의 길이입니다.

*_I1*<br/>
다음으로 중요 한 차원의 길이입니다.

*_I2*<br/>
최하위 차원의 길이입니다.

*_Other*<br/>
새 인덱스 개체의 기준이 되는 인덱스 개체입니다.

## <a name="operator--"></a><a name="operator--"></a> 연산자--

Index 개체의 각 요소를 감소 시킵니다.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>반환 값

전위 연산자의 경우 인덱스 개체 (* this)입니다. 접미사 연산자의 경우 새 인덱스 개체입니다.

## <a name="operator"></a><a name="operator_mod_eq"></a> 연산자% =

index 개체의 각 요소를 지정된 숫자로 나눌 때의 모듈러스(나머지)를 계산합니다.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
모듈러스(나머지)를 찾기 위해 나눌 숫자입니다.

## <a name="return-value"></a>반환 값

index 개체입니다.

## <a name="operator"></a><a name="operator_star_eq"></a> 연산자 * =

인덱스 개체의 각 요소에 지정 된 숫자를 곱합니다.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
곱할 숫자입니다.

## <a name="operator"></a><a name="operator_div_eq"></a> operator/=

인덱스 개체의 각 요소를 지정 된 수 만큼 나눕니다.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
나눌 숫자입니다.

## <a name="operator"></a><a name="operator_at"></a> 연산자\[\]

지정 된 위치에 있는 인덱스의 구성 요소를 반환 합니다.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Index*<br/>
0에서 순위에서 1을 뺀 값 사이의 정수입니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 요소입니다.

### <a name="remarks"></a>설명

다음 예에서는 인덱스의 구성 요소 값을 표시 합니다.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a> operator + +

Index 개체의 각 요소를 증가 시킵니다.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>반환 값

전위 연산자의 경우 인덱스 개체 (* this)입니다. 접미사 연산자의 경우 새 인덱스 개체입니다.

## <a name="operator"></a><a name="operator_add_eq"></a> operator + =

인덱스 개체의 각 요소에 지정한 수를 추가 합니다.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
더할 숫자입니다.

### <a name="return-value"></a>반환 값

index 개체입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 인덱스 개체의 내용을이 개체에 복사 합니다.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
복사할 인덱스 개체입니다.

### <a name="return-value"></a>반환 값

이 인덱스 개체에 대 한 참조입니다.

## <a name="operator-"></a><a name="operator_-_eq"></a> 연산자-=

Index 개체의 각 요소에서 지정한 수를 뺍니다.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>매개 변수

*_Rhs*<br/>
뺄 숫자입니다.

### <a name="return-value"></a>반환 값

index 개체입니다.

## <a name="rank"></a><a name="rank"></a> 배열

index 개체의 차수를 가져옵니다.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
