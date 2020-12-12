---
description: '자세히 알아보기: variant 클래스'
title: variant 클래스
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 0fc2887def147b458e63bc316f211e62a5eba879
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305106"
---
# <a name="variant-class"></a>variant 클래스

지정 된 시간의 모든 변형 인스턴스는 대체 유형 중 하나의 값을 보유 하거나 값을 보유 하지 않습니다.

## <a name="syntax"></a>구문

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[variant](#variant)|`variant` 형식의 개체를 생성합니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[emplace](#emplace)|새 포함 된 값을 만듭니다.|
|[index](#index)|포함 된 값의 인덱스를 반환 합니다.|
|[스왑을](#swap)||
|[valueless_by_exception](#emplace)|**`false`** 변형에 값이 포함 된 경우를 반환 합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 =](#op_eq)|Variant를 다른 variant의 복사본으로 바꿉니다.|

## <a name="emplace"></a><a name="emplace"></a> emplace

새 포함 된 값을 만듭니다.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a><a name="index"></a> 인덱싱할

포함 된 값의 인덱스를 반환 합니다.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> 변형은

`variant` 형식의 개체를 생성합니다. 소멸자도 포함 합니다.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>매개 변수

*항상*\
이 개체에 사용할 할당자 클래스입니다.

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

Variant를 다른 variant의 복사본으로 바꿉니다.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> 스왑을

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

**`false`** 변형에 값이 포함 된 경우를 반환 합니다.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
