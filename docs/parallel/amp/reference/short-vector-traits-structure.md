---
description: '다음에 대 한 자세한 정보: short_vector_traits 구조체'
title: short_vector_traits 구조체
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: dc211c8e66cbd31c57655afce22376909cf77530
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329890"
---
# <a name="short_vector_traits-structure"></a>short_vector_traits 구조체

short_vector_traits를 사용 하 여 짧은 벡터 형식 또는 스칼라 형식의 기본 벡터 길이와 스칼라 형식을 검색할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

### <a name="parameters"></a>매개 변수

`T`

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[short_vector_traits::short_vector_traits 생성자](#ctor)||

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[short_vector_traits::size 상수](#size)||

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`short_vector_traits`

## <a name="requirements"></a>요구 사항

**헤더:** amp_short_vectors. h

**네임 스페이스:** Concurrency:: graphics

## <a name="short_vector_traitsshort_vector_traits-constructor"></a><a name="ctor"></a> short_vector_traits:: short_vector_traits 생성자

```cpp
short_vector_traits();
```

## <a name="short_vector_traitssize-constant"></a><a name="size"></a> short_vector_traits:: size 상수

```cpp
static int const size = 1;
```

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
