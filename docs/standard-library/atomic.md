---
title: '&lt;atomic&gt; | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
dev_langs:
- C++
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74dc0fde7ea066707bb6e93592420009b882ee21
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

원자 연산을 지원하는 형식을 위한 클래스 및 템플릿 클래스를 정의합니다.

## <a name="syntax"></a>구문

```cpp
#include <atomic>
```

## <a name="remarks"></a>설명

> [!NOTE]
> 사용 하 여 컴파일된 코드에서 **/clr**,이 헤더 ï ´ ù.

원자 연산에는 뮤텍스 잠금을 사용하지 않은 채 여러 스레드를 사용하여 개체를 올바르게 조작하는 데 도움이 되는 두 가지 주요 속성이 있습니다.

- 원자 연산은 나눌 수 없으므로, 다른 스레드의 동일한 개체에 대한 두 번째 원자 연산은 첫 번째 원자 연산 이전 또는 이후에만 개체의 상태를 가져올 수 있습니다.

- [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수를 기반으로 하는 원자 연산은 동일한 스레드에 있는 다른 원자 연산의 효과를 가시화하기 위해 순서 요구 사항을 설정합니다. 그 결과 순서 요구 사항을 위반하는 컴파일러 최적화는 금지됩니다.

일부 플랫폼에서는 `mutex` 잠금을 사용하지 않고서는 몇몇 형식의 원자 연산을 효율적으로 구현하지 못할 수 있습니다. 원자 형식의 어떤 원자 연산도 잠금을 사용하지 않는 경우 해당 원자 형식은 *잠금 해제*입니다.

**C++11**: `obj.is_lock_free()` 또는 `atomic_is_lock_free(x)`가 true인 경우 일부 신호 처리기에서 `obj` 개체에 대한 원자 연산을 수행할 수 없습니다.

[atomic_flag](../standard-library/atomic-flag-structure.md) 클래스는 `bool` 플래그가 포함된 최소 원자성 형식을 제공합니다. 해당 연산은 항상 잠금 해제입니다.

`atomic<T>` 템플릿 클래스는 `T` 인수 형식의 개체를 저장하고 저장된 값에 대한 원자성 액세스를 제공합니다. [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)를 사용하여 복사할 수 있고 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)를 사용하여 같음을 테스트할 수 있는 모든 형식을 사용하여 인스턴스화할 수 있습니다. 특히 이 클래스는 이러한 요구 사항을 충족하는 사용자 정의 형식과 함께, 그리고 많은 경우 부동 소수점 형식과 함께 사용할 수 있습니다.

템플릿에는 또한 정수 형식에 대한 특수화 집합 및 포인터에 대한 부분 특수화가 포함됩니다. 이러한 특수화는 기본 템플릿을 통해 사용할 수 없는 추가 작업을 제공합니다.

## <a name="pointer-specializations"></a>포인터 특수화

`atomic<T *>` 부분 특수화는 모든 포인터 형식에 적용되며, 포인터 산술 연산에 대한 메서드를 제공합니다.

## <a name="integral-specializations"></a>정수 계열 특수화

`atomic<integral>` 특수화는 모든 정수 형식에 적용되며, 기본 템플릿을 통해 사용할 수 없는 추가 작업을 제공합니다.

각 `atomic<integral>` 형식에는 컴파일 시간에 해당 형식에 대한 연산이 잠금 해제인지를 확인하기 위해 `if directive`에서 사용할 수 있는 해당 매크로가 있습니다. 매크로의 값이 0이면 해당 형식의 연산은 잠금 해제가 아닙니다. 값이 1이면 연산은 잠금 해제일 수 있으며, 런타임 확인이 필요합니다. 값이 2이면 연산은 잠금 해제입니다. 형식에 대한 연산이 잠금 해제인지를 런타임 시 확인하려면 `atomic_is_lock_free` 함수를 사용할 수 있습니다.

각 정수 형식에는 해당 정수 형식의 개체를 관리하는 명명된 해당 원자성 형식이 있습니다. 각 `atomic_integral` 형식에는 `atomic<T>`의 해당 인스턴스화와 동일한 멤버 함수 집합이 있으며, 이 형식은 비 멤버 원자성 함수 중 하나로 전달될 수 있습니다.

|`atomic_integral` 형식|정수 형식|`atomic_is_lock_free` 매크로|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|

Typedef 이름은 \<inttypes.h> 헤더에 정의된 일부 형식에 대한 원자성 템플릿의 특수화를 위해 존재합니다.

|원자성 형식|Typedef 이름|
|-----------------|------------------|
|`atomic_int8_t`|`atomic<int8_t>`|
|`atomic_uint8_t`|`atomic<uint8_t>`|
|`atomic_int16_t`|`atomic<int16_t>`|
|`atomic_uint16_t`|`atomic<uint16_t>`|
|`atomic_int32_t`|`atomic<int32_t>`|
|`atomic_uint32_t`|`atomic<uint32_t>`|
|`atomic_int64_t`|`atomic<int64_t>`|
|`atomic_uint64_t`|`atomic<uint64_t>`|
|`atomic_int_least8_t`|`atomic<int_least8_t>`|
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|
|`atomic_int_least16_t`|`atomic<int_least16_t>`|
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|
|`atomic_int_least32_t`|`atomic<int_least32_t>`|
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|
|`atomic_int_least64_t`|`atomic<int_least64_t>`|
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|
|`atomic_intptr_t`|`atomic<intptr_t>`|
|`atomic_uintptr_t`|`atomic<uintptr_t>`|
|`atomic_size_t`|`atomic<size_t>`|
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|
|`atomic_intmax_t`|`atomic<intmax_t>`|
|`atomic_uintmax_t`|`atomic<uintmax_t>`|

## <a name="structs"></a>구조체

|이름|설명|
|----------|-----------------|
|[atomic 구조체](../standard-library/atomic-structure.md)|저장된 값에 대해 원자 연산을 수행하는 개체를 설명합니다.|
|[atomic_flag 구조체](../standard-library/atomic-flag-structure.md)|`bool` 플래그를 원자 단위로 설정하고 지우는 개체를 설명합니다.|

## <a name="enums"></a>열거형

|이름|설명|
|----------|-----------------|
|[memory_order 열거형](../standard-library/atomic-enums.md#memory_order_enum)|메모리 위치에서 동기화 연산에 대한 기호 이름을 제공합니다. 이러한 연산은 하나의 스레드의 할당이 다른 스레드에 표시될 방법에 영향을 미칩니다.|

## <a name="functions"></a>함수

다음 목록에서 `_explicit`로 끝나지 않는 함수는, `memory_order_seq_cst`의 암시적 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수를 가지고 있다는 점을 제외하고, 해당 `_explicit`의 의미 체계를 가지고 있습니다.

|이름|설명|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|*원자 비교 및 교환* 작업을 수행합니다.|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|*원자 비교 및 교환* 작업을 수행합니다.|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|*약한 원자 비교 및 교환* 작업을 수행합니다.|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|*약한 원자 비교 및 교환* 작업을 수행합니다.|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|저장된 값을 대체합니다.|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|저장된 값을 대체합니다.|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|기존의 저장된 값에 지정된 값을 더합니다.|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|기존의 저장된 값에 지정된 값을 더합니다.|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|지정된 값 및 기존의 저장된 값에 대해 비트 `and`를 수행합니다.|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|지정된 값 및 기존의 저장된 값에 대해 비트 `and`를 수행합니다.|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|지정된 값 및 기존의 저장된 값에 대해 비트 `or`를 수행합니다.|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|지정된 값 및 기존의 저장된 값에 대해 비트 `or`를 수행합니다.|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|기존의 저장된 값에서 지정된 값을 뺍니다.|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|기존의 저장된 값에서 지정된 값을 뺍니다.|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|지정된 값 및 기존의 저장된 값에 대해 비트 `exclusive or`를 수행합니다.|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|지정된 값 및 기존의 저장된 값에 대해 비트 `exclusive or`를 수행합니다.|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|`atomic_flag` 개체의 플래그를 `false`로 설정합니다.|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|`atomic_flag` 개체의 플래그를 `false`로 설정합니다.|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|`atomic_flag` 개체의 플래그를 `true`로 설정합니다.|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|`atomic_flag` 개체의 플래그를 `true`로 설정합니다.|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|`atomic` 개체에서 저장된 값을 설정합니다.|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|지정된 개체에 대한 원자 연산이 잠금 해제인지를 지정합니다.|
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|값을 원자 단위로 검색합니다.|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|값을 원자 단위로 검색합니다.|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|동일한 스레드에서 실행되는 신호 처리기가 있는 호출 스레드에서 fence 간 메모리 순서 요구 사항을 설정하는 *fence* 역할을 수행합니다.|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|값을 원자 단위로 저장합니다.|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|값을 원자 단위로 저장합니다.|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|다른 fence와 관련하여 메모리 순서 요구 사항을 설정하는 *fence* 역할을 수행합니다.|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|가능한 종속성 체인을 중단합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
