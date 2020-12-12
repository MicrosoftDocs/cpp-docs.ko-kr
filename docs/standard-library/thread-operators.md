---
description: '자세한 정보: &lt; 스레드 &gt; 연산자'
title: '&lt;thread&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 3992dccf051622bcf854c1843f1bdeb15d227731
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207425"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 연산자

[연산자! =](#op_neq)\
[연산자&gt;](#op_gt)\
[연산자&gt;=](#op_gt_eq)\
[연산자&lt;](#op_lt)\
[연산자&lt;&lt;](#op_lt_lt)\
[연산자&lt;=](#op_lt_eq)\
[연산자 = =](#op_eq_eq)

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

하나의 `thread::id` 개체가 다른 개체보다 크거나 같은지를 확인합니다.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

`!(Left < Right)`

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

하나의 `thread::id` 개체가 다른 개체보다 큰지를 확인합니다.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

`Right < Left`

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

하나의 `thread::id` 개체가 다른 개체보다 작거나 같은지를 확인합니다.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

`!(Right < Left)`

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

하나의 `thread::id` 개체가 다른 개체보다 작은지를 확인합니다.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 전체 순서에서 *왼쪽* 이 *오른쪽* 앞에 오면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

연산자는 모든 `thread::id` 개체의 전체 순서를 정의합니다. 이러한 개체는 연관 컨테이너에서 키로 사용할 수 있습니다.

이 함수는 예외를 throw하지 않습니다.

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

두 `thread::id` 개체가 다른지 비교합니다.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

`!(Left == Right)`

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

두 `thread::id` 개체가 같은지 비교합니다.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>매개 변수

*비어*\
왼쪽 `thread::id` 개체입니다.

*오른쪽*\
오른쪽 `thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 두 개체가 동일한 실행 스레드를 나타내면이 고, 두 개체가 모두 실행 스레드를 나타내지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 함수는 예외를 throw하지 않습니다.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

`thread::id` 개체의 텍스트 표현을 스트림에 삽입합니다.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>매개 변수

*Ostr*\
[basic_ostream](../standard-library/basic-ostream-class.md) 개체입니다.

*A-id*\
`thread::id` 개체입니다.

### <a name="return-value"></a>반환 값

*Ostr*.

### <a name="remarks"></a>설명

이 함수는 *Ostr* 에 *Id* 를 삽입 합니다.

두 `thread::id` 개체가 비교 결과 같으면 해당 개체의 삽입된 텍스트 표현은 동일합니다.

## <a name="see-also"></a>참고 항목

[\<thread>](../standard-library/thread.md)
