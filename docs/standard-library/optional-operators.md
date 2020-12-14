---
description: '자세한 정보: &lt; 선택적 &gt; 연산자'
title: '&lt;선택적 &gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: 3c61f62ff87ab285dfeb5b26f1d22de86ef50fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201861"
---
# <a name="ltoptionalgt-operators"></a>&lt;선택적 &gt; 연산자

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체와 같은지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체와 같지 않은지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

### <a name="remarks"></a>설명

이 템플릿 함수는 `!(left == right)`를 반환합니다.

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체보다 작은지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 목록이 연산자 우변의 목록 보다 작거나 같지 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체보다 작거나 같은지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 목록이 연산자 우변의 목록 보다 작거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `!(right < left)`를 반환합니다.

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체보다 큰지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 목록이 연산자 우변의 목록 보다 크면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `right < left`를 반환합니다.

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

연산자의 좌변에 있는 `optional` 개체가 우변에 있는 `optional` 개체보다 크거나 같은지 테스트합니다.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>매개 변수

*비어*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

*오른쪽*\
, 또는 형식의 개체 `optional` 입니다 `nullopt_t` `T` .

### <a name="return-value"></a>반환 값

**`true`**`optional`연산자 좌 변의가 연산자 우변의 보다 크거나 같으면이 고, `optional` 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

템플릿 함수가 `!(left < right)`을 반환합니다.
