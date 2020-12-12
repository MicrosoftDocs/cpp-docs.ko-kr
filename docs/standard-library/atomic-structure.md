---
description: '자세한 정보: 원자성 구조'
title: atomic 구조체
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 9698e0e14129d8fa020bd1432912aea85498ff6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321696"
---
# <a name="atomic-structure"></a>atomic 구조체

*Ty* 형식의 저장 된 값에 대해 원자 연산을 수행 하는 개체에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>멤버

|멤버|설명|
|----------|-----------------|
|**생성자**||
|[원자적](#atomic)|atomic 개체를 생성합니다.|
|**연산자**||
|[atomic:: operator Ty](#op_ty)|저장된 값을 읽고 반환합니다. ([atomic:: load](#load))|
|[atomic:: operator =](#op_eq)|지정된 값을 사용하여 저장된 값을 바꿉니다. ([atomic:: store](#store))|
|[atomic:: operator + +](#op_inc)|저장된 값을 증가시킵니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.|
|[atomic:: operator + =](#op_add_eq)|지정된 값을 저장된 값에 더합니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.|
|[atomic:: operator--](#op_dec)|저장된 값을 감소시킵니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.|
|[atomic:: operator-=](#op_sub_eq)|지정된 값을 저장된 값에서 뺍니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.|
|[atomic:: operator&=](#op_and_eq)|지정 된 값과 저장 된 값에 대해 비트 and를 수행 합니다. 정수 계열 특수화에서만 사용됩니다.|
|[atomic:: operator&#124;=](#op_or_eq)|지정 된 값과 저장 된 값에 대해 비트 or을 수행 합니다. 정수 계열 특수화에서만 사용됩니다.|
|[atomic:: operator ^ =](#op_xor_eq)|지정 된 값과 저장 된 값에 배타적 비트 or 연산을 수행 합니다. 정수 계열 특수화에서만 사용됩니다.|
|**함수**||
|[compare_exchange_strong](#compare_exchange_strong)|에 대해 *atomic_compare_and_exchange* 작업을 수행 **`this`** 하 고 결과를 반환 합니다.|
|[compare_exchange_weak](#compare_exchange_weak)|에 대해 *weak_atomic_compare_and_exchange* 작업을 수행 **`this`** 하 고 결과를 반환 합니다.|
|[fetch_add](#fetch_add)|지정된 값을 저장된 값에 더합니다.|
|[fetch_and](#fetch_and)|지정 된 값과 저장 된 값에 대해 비트 and를 수행 합니다.|
|[fetch_or](#fetch_or)|지정 된 값과 저장 된 값에 대해 비트 or을 수행 합니다.|
|[fetch_sub](#fetch_sub)|지정된 값을 저장된 값에서 뺍니다.|
|[fetch_xor](#fetch_xor)|지정 된 값과 저장 된 값에 배타적 비트 or 연산을 수행 합니다.|
|[is_lock_free](#is_lock_free)|의 원자성 작업이 **`this`** *잠금 해제* 인지 여부를 지정 합니다. 원자 형식의 어떤 원자 연산도 잠금을 사용하지 않는 경우 해당 원자 형식을 *잠금 해제* 라고 합니다.|
|[로드](#load)|저장된 값을 읽고 반환합니다.|
|[스토어](#store)|지정된 값을 사용하여 저장된 값을 바꿉니다.|

## <a name="remarks"></a>설명

*Ty* 형식은 *일반적으로 복사할 수* 이어야 합니다. 즉, [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 를 사용 하 여 바이트를 복사 하면 원래 개체와 동일한 지 비교 하는 유효한 *Ty* 개체가 생성 되어야 합니다. [Compare_exchange_weak](#compare_exchange_weak) 및 [compare_exchange_strong](#compare_exchange_strong) 멤버 함수는 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 를 사용 하 여 두 개의 *Ty* 값이 같은지 여부를 확인 합니다. 이러한 함수는 *Ty* 정의를 사용 하지 않습니다 `operator==` . `atomic` `memcpy` *Ty* 형식의 값을 복사 하는 데 사용 하는 멤버 함수입니다.

부분 특수화 `atomic<Ty*>`는 모든 포인터 형식에 대해 존재합니다. 특수화를 사용하면 관리되는 포인터 값에 오프셋을 더하거나 값에서 오프셋을 뺄 수 있습니다. 산술 연산은 형식의 인수를 사용 하 `ptrdiff_t` 고, 일반 주소 산술과 일관 되도록 *Ty* 의 크기에 따라 해당 인수를 조정 합니다.

을 제외한 모든 정수 계열 형식에 대 한 특수화가 있습니다 **`bool`** . 각 특수화에서는 원자 산술 및 논리 연산을 위한 다양한 방법을 제공합니다.

:::row:::
   :::column:::
      `atomic<char>`\
      `atomic<signed char>`\
      `atomic<unsigned char>`\
      `atomic<char16_t>`\
      `atomic<char32_t>`\
      `atomic<wchar_t>`\
      `atomic<short>`
   :::column-end:::
   :::column:::
      `atomic<unsigned short>`\
      `atomic<int>`\
      `atomic<unsigned int>`\
      `atomic<long>`\
      `atomic<unsigned long>`\
      `atomic<long long>`\
      `atomic<unsigned long long>`
   :::column-end:::
:::row-end:::

정수 특수화는 해당 `atomic_integral` 형식에서 파생됩니다. 예를 들어 `atomic<unsigned int>`는 `atomic_uint`에서 파생됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<atomic>

**네임스페이스:** std

## <a name="atomicatomic"></a><a name="atomic"></a> atomic:: atomic

atomic 개체를 생성합니다.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
초기화 값입니다.

### <a name="remarks"></a>설명

원자성 개체를 복사 하거나 이동할 수 없습니다.

원자성의 인스턴스화 인 개체는 \<*Ty*> 집합체 초기화를 사용 하는 것이 아니라 *Ty* 형식의 인수를 사용 하는 생성자에 의해서만 초기화 될 수 있습니다. 그러나 atomic_integral 개체는 집합체 초기화를 사용 해야만 초기화할 수 있습니다.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="atomicoperator-ty"></a><a name="op_ty"></a> atomic:: operator *Ty*

Template에 지정 된 형식에 대 한 연산자 \<*Ty*> 입니다. 원자성. **\* 이** 에 저장 된 값을 검색 합니다.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>설명

이 연산자는 `memory_order_seq_cst` [memory_order](atomic-enums.md)을 적용 합니다.

## <a name="atomicoperator"></a><a name="op_eq"></a> atomic:: operator =

지정된 값을 저장합니다.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 개체입니다.

### <a name="return-value"></a>반환 값

*값* 을 반환 합니다.

## <a name="atomicoperator"></a><a name="op_inc"></a> atomic:: operator + +

저장된 값을 증가시킵니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>반환 값

처음 두 연산자는 증가 된 값을 반환 합니다. 마지막 두 연산자는 증가값 앞의 값을 반환 합니다. 연산자는 memory_order을 사용 합니다 `memory_order_seq_cst` [](atomic-enums.md).

## <a name="atomicoperator"></a><a name="op_add_eq"></a> atomic:: operator + =

지정된 값을 저장된 값에 더합니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
정수 계열 또는 포인터 값입니다.

### <a name="return-value"></a>반환 값

더하기의 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

이 연산자는 `memory_order_seq_cst` [memory_order](atomic-enums.md)을 사용 합니다.

## <a name="atomicoperator--"></a><a name="op_dec"></a> atomic:: operator--

저장된 값을 감소시킵니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>반환 값

처음 두 연산자는 감소 된 값을 반환 합니다. 마지막 두 연산자는 감소 전에 값을 반환 합니다. 연산자는 memory_order을 사용 합니다 `memory_order_seq_cst` [](atomic-enums.md).

## <a name="atomicoperator-"></a><a name="op_sub_eq"></a> atomic:: operator-=

지정된 값을 저장된 값에서 뺍니다. 정수 계열 및 포인터 특수화에서만 사용됩니다.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
정수 계열 또는 포인터 값입니다.

### <a name="return-value"></a>반환 값

뺄셈 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

이 연산자는 `memory_order_seq_cst` [memory_order](atomic-enums.md)을 사용 합니다.

## <a name="atomicoperator"></a><a name="op_and_eq"></a> atomic:: operator&=

지정 된 값과 **\* 이** 의 저장 된 값에 대해 비트 and를 수행 합니다. 정수 계열 특수화에서만 사용됩니다.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

### <a name="return-value"></a>반환 값

비트 and의 결과입니다.

### <a name="remarks"></a>설명

이 연산자는 memory_order의 제약 조건 내에서이의 저장 된 값을 비트 **\*** and *값* 및 **\* 이** 에 저장 된 현재 값으로 대체 하는 읽기-수정-쓰기 작업을 수행 `memory_order_seq_cst` [](atomic-enums.md)합니다.

## <a name="atomicoperator124"></a><a name="op_or_eq"></a> atomic:: operator&#124;=

지정 된 값과 **\* 이** 의 저장 된 값에 대해 비트 or을 수행 합니다. 정수 계열 특수화에서만 사용됩니다.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

### <a name="return-value"></a>반환 값

비트 or의 결과입니다.

### <a name="remarks"></a>설명

이 연산자는 memory_order 제약 조건 내에서이의 저장 된 값을 비트 or **\*** *값* 및 **\* 이** 에 저장 된 현재 값으로 대체 하는 읽기-수정-쓰기 작업을 수행 합니다 `memory_order_seq_cst` [](atomic-enums.md) .

## <a name="atomicoperator"></a><a name="op_xor_eq"></a> atomic:: operator ^ =

지정 된 값과 **\* 이** 의 저장 된 값에 대해 비트 배타적 or를 수행 합니다. 정수 계열 특수화에서만 사용됩니다.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

### <a name="return-value"></a>반환 값

배타적 비트 or의 결과입니다.

### <a name="remarks"></a>설명

이 연산자는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값을 비트 배타적 or *값* 또는 **\* 이** 에 저장 된 현재 값으로 바꿉니다 .이 값은 memory_order 제약 조건의 제약 조건에 포함 `memory_order_seq_cst` [](atomic-enums.md) 됩니다.

## <a name="atomiccompare_exchange_strong"></a><a name="compare_exchange_strong"></a> atomic:: compare_exchange_strong

**\* 이** 에 대해 원자성 비교 및 교환 작업을 수행 합니다.

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*.Exp*\
*Ty* 형식의 값입니다.

*Value*\
*Ty* 형식의 값입니다.

*Order1*\
첫 번째 `memory_order` 인수입니다.

*Order2*\
두 번째 `memory_order` 인수입니다.

### <a name="return-value"></a>반환 값

**`bool`** 값 비교의 결과를 나타내는입니다.

### <a name="remarks"></a>설명

원자 비교 및 교환 작업은 **\* 이** 에 저장 된 값을 *Exp* 와 비교 합니다. 값이 같으면 작업은 읽기-수정-쓰기 작업을 사용 하 고 *Order1* 로 지정 된 메모리 순서 제약 조건을 적용 하 여 **\* 이** 에 저장 된 값을 *값* 으로 바꿉니다. 값이 같지 않으면 작업에서 **\* 이** 에 저장 된 값을 사용 하 여 *Exp* 를 대체 하 고 *Order2* 로 지정 된 메모리 순서 제약 조건을 적용 합니다.

두 번째를 포함 하지 않는 오버 로드는 `memory_order` *Order1* 의 값을 기반으로 하는 암시적 *Order2* 를 사용 합니다. *Order1* 가 이면 `memory_order_acq_rel` *Order2* 는 `memory_order_acquire` 입니다. *Order1* 가 이면 `memory_order_release` *Order2* 는 `memory_order_relaxed` 입니다. 다른 모든 경우에는 *Order2* 가 *Order1* 와 같습니다.

두 개의 매개 변수를 사용 하는 오버 로드의 경우 `memory_order` *Order2* 의 값은 `memory_order_release` 또는이 아니어야 하며 `memory_order_acq_rel` *Order1* 값 보다 더 강력 하지 않아야 합니다.

## <a name="atomiccompare_exchange_weak"></a><a name="compare_exchange_weak"></a> atomic:: compare_exchange_weak

**\* 이** 에서 약한 원자 비교 및 교환 작업을 수행 합니다.

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*.Exp*\
*Ty* 형식의 값입니다.

*Value*\
*Ty* 형식의 값입니다.

*Order1*\
첫 번째 `memory_order` 인수입니다.

*Order2*\
두 번째 `memory_order` 인수입니다.

### <a name="return-value"></a>반환 값

**`bool`** 값 비교의 결과를 나타내는입니다.

### <a name="remarks"></a>설명

원자 비교 및 교환 작업은 **\* 이** 에 저장 된 값을 *Exp* 와 비교 합니다. 값이 같으면 작업은 읽기-수정-쓰기 작업을 사용 하 고 *Order1* 로 지정 된 메모리 순서 제약 조건을 적용 하 여 **\* 이** 에 저장 된 값을 *값* 으로 바꿉니다. 값이 같지 않으면 작업에서 **\* 이** 에 저장 된 값을 사용 하 여 *Exp* 를 대체 하 고 *Order2* 로 지정 된 메모리 순서 제약 조건을 적용 합니다.

약한 원자 비교 및 교환 작업은 비교된 값이 같은 경우 교환을 수행합니다. 값이 같지 않으면 작업에서 exchange를 수행 하는 것이 보장 되지 않습니다.

두 번째를 포함 하지 않는 오버 로드는 `memory_order` *Order1* 의 값을 기반으로 하는 암시적 *Order2* 를 사용 합니다. *Order1* 가 이면 `memory_order_acq_rel` *Order2* 는 `memory_order_acquire` 입니다. *Order1* 가 이면 `memory_order_release` *Order2* 는 `memory_order_relaxed` 입니다. 다른 모든 경우에는 *Order2* 가 *Order1* 와 같습니다.

두 개의 매개 변수를 사용 하는 오버 로드의 경우 `memory_order` *Order2* 의 값은 `memory_order_release` 또는이 아니어야 하며 `memory_order_acq_rel` *Order1* 값 보다 더 강력 하지 않아야 합니다.

## <a name="atomicexchange"></a><a name="exchange"></a> atomic:: exchange

지정 된 값을 사용 하 여 **\* 이** 의 저장 된 값을 바꿉니다.

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

교환 전에 **\* 이** 의 저장 된 값입니다.

### <a name="remarks"></a>설명

이 작업은 *값* 을 사용 하 여 **\* 이** 에 저장 된 값을 *Order* 에 지정 된 메모리 제약 조건 내에서 대체 하는 읽기-수정-쓰기 작업을 수행 합니다.

## <a name="atomicfetch_add"></a><a name="fetch_add"></a> atomic:: fetch_add

**\* 이** 에 저장 된 값을 페치 한 다음 지정 된 값을 저장 된 값에 추가 합니다.

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

추가 하기 전에 **\* 이** 에 저장 된 값을 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

`fetch_add`메서드는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값에 *값* 을 원자 단위로 추가 하 고 *Order* 에 지정 된 메모리 제약 조건을 적용 합니다.

## <a name="atomicfetch_and"></a><a name="fetch_and"></a> atomic:: fetch_and

값과 **\* 이** 에 저장 된 기존 값에 대해 비트 and를 수행 합니다.

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

비트 and의 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

`fetch_and`메서드는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값을 *순서 대로* 지정 된 메모리 제약 조건 내에서 비트 and *값* 및 **\* 이** 에 저장 된 현재 값으로 바꿉니다.

## <a name="atomicfetch_or"></a><a name="fetch_or"></a> atomic:: fetch_or

**\* 이** 에 저장 된 기존 값 및 값에 대해 비트 or을 수행 합니다.

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

비트 or의 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

`fetch_or`메서드는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값을 비트 or *값* 및이에 저장 된 현재 값으로 바꿉니다. **\* 이** 값은 *Order* 로 지정 된 메모리 제약 조건 내에 있습니다.

## <a name="atomicfetch_sub"></a><a name="fetch_sub"></a> atomic:: fetch_sub

지정된 값을 저장된 값에서 뺍니다.

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

뺄셈 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

`fetch_sub`메서드는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값에서 *Order* 로 지정 된 메모리 제약 조건 내에서 *값* 을 원자 단위로 뺍니다.

## <a name="atomicfetch_xor"></a><a name="fetch_xor"></a> atomic:: fetch_xor

**\* 이** 에 저장 된 값 및 기존 값에 대해 비트 배타적 or를 수행 합니다.

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 형식의 값입니다.

*주문을*\
`memory_order`

### <a name="return-value"></a>반환 값

배타적 비트 or의 결과를 포함 하는 *Ty* 개체입니다.

### <a name="remarks"></a>설명

`fetch_xor`메서드는 읽기-수정-쓰기 작업을 수행 하 여 **\* 이** 의 저장 된 값을 비트 배타적 or *값* 및 **\* 이** 에 저장 된 현재 값으로 바꾸고 *Order* 에 지정 된 메모리 제약 조건을 적용 합니다.

## <a name="atomicis_lock_free"></a><a name="is_lock_free"></a> atomic:: is_lock_free

**\* 이** 에 대 한 원자성 작업이 잠금 해제 인지 여부를 지정 합니다.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>반환 값

**\* 이** 에 대 한 원자성 작업이 잠금 해제 이면 true이 고, 그렇지 않으면 false입니다.

### <a name="remarks"></a>설명

원자 형식의 어떤 원자 연산도 잠금을 사용하지 않는 경우 해당 원자 형식을 잠금 해제라고 합니다.

## <a name="atomicload"></a><a name="load"></a> atomic:: load

지정 된 메모리 제약 조건 내에서 **\* 이** 의 저장 된 값을 검색 합니다.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>매개 변수

*주문을*\
`memory_order` *순서* 는 또는가 아니어야 합니다 `memory_order_release` `memory_order_acq_rel` .

### <a name="return-value"></a>반환 값

**\* 이** 에 저장 된 검색 된 값입니다.

## <a name="atomicstore"></a><a name="store"></a> atomic:: store

지정된 값을 저장합니다.

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>매개 변수

*Value*\
*Ty* 개체입니다.

*주문을*\
`memory_order`제약 조건입니다.

### <a name="remarks"></a>설명

이 멤버 함수는  **`*this`** *Order* 로 지정 된 메모리 제약 조건 내에서 값을 원자 단위로 저장 합니다.

## <a name="see-also"></a>참고 항목

[\<atomic>](../standard-library/atomic.md)\
[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
