---
description: '자세히 알아보기: &lt; 메모리&gt;'
title: '&lt;memory&gt;'
ms.date: 08/04/2019
f1_keywords:
- <memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 05d5b6e87b23ea2a88e4ff5a8a11c2d6b054691f
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126522"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

개체를 할당하고 해제하는 데 도움이 되는 클래스, 연산자 및 몇 가지 템플릿을 정의합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<memory>

**네임스페이스:** std

## <a name="members"></a>멤버

### <a name="functions"></a>Functions

|Name|설명|
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|개체의 실제 주소를 가져옵니다.|
|[align](../standard-library/memory-functions.md#align)|제공된 정렬 및 시작 주소를 기준으로 지정된 크기 범위에 포인터를 반환합니다.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|지정된 할당자를 사용하여 지정된 형식에 대해 할당되고 생성되는 개체에 대한 `shared_ptr`을 만듭니다.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|`shared_ptr`로 const_cast를 수행합니다.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|지정된 주소에서 시작하고 표시된 블록 크기 내에 속하는 문자는 추적 가능한 포인터를 포함하지 않음을 가비지 수집기에 알립니다.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|지정된 주소가 할당된 스토리지에 대한 것이며 접근할 수 있음을 가비지 컬렉션에 알립니다.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|`operator new`를 사용하여 할당된 개체를 삭제합니다. `unique_ptr`에 사용하는 데 적합합니다.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|줄임 `destroy` 메서드.|
|[삭제](../standard-library/memory-functions.md#destroy)|줄임 `destroy` 메서드.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|줄임 `destroy` 메서드.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|`shared_ptr`로 dynamic_cast를 수행합니다.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|`shared_ptr`에서 Deleter 가져오기|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|모든 가비지 수집기에서 간주된 포인터 안전 형식을 반환합니다.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|지정된 수의 요소를 초과하지 않는 요소의 시퀀스를 위한 임시 스토리지를 할당합니다.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|기본 할당자를 사용하여 하나 이상의 인수에서 작성된 할당된 개체를 가리키는 `shared_ptr`를 만들고 반환합니다.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|0개 이상의 인수에서 생성된 할당된 개체를 가리키는 [unique_ptr](../standard-library/unique-ptr-class.md)을 만들고 반환합니다.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|`get_pointer_safety`에 대한 모든 가능한 반환 값의 열거형입니다.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|`get_temporary_buffer` 템플릿 함수를 사용하여 할당된 임시 메모리를 취소합니다.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|`shared_ptr`에 대한 정적 캐스팅입니다.|
|[스왑을](../standard-library/memory-functions.md#swap)|두 `shared_ptr` 또는 `weak_ptr` 개체를 바꿉니다.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|기본 주소 포인터와 블록 크기로 정의된 메모리 블록에 있는 문자는 이제 추적이 가능한 포인터를 포함할 수 있음을 가비지 수집기에 알립니다.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|지정된 메모리 위치에 접근할 수 없음을 `garbage_collector`에 알립니다.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|지정된 입력 범위에서 초기화되지 않은 대상 범위로 개체를 복사합니다.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|입력 반복기에서 지정된 수의 요소의 복사본을 만듭니다. 복사본은 정방향 반복기에 배치됩니다.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|줄임 `uninitialized_default_construct` 메서드.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|줄임 `uninitialized_construct` 메서드.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|지정된 값의 개체를 초기화되지 않은 대상 범위로 복사합니다.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|지정된 값의 개체를 초기화되지 않은 대상 범위의 지정된 수의 요소로 복사합니다.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|줄임 `uninitialized_move` 메서드.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|줄임 `uninitialized_move` 메서드.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|줄임 `uninitialized_value_construct` 메서드.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|줄임 `uninitialized_value_construct` 메서드.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](../standard-library/memory-operators.md#op_neq)|지정된 클래스의 할당자 개체가 다른지 테스트합니다.|
|[연산자 = =](../standard-library/memory-operators.md#op_eq_eq)|지정된 클래스의 할당자 개체가 같은지 테스트합니다.|
|[연산자>=](../standard-library/memory-operators.md#op_gt_eq)|하나의 할당자 개체에 대한 테스트는 지정된 클래스의 두 번째 할당자 개체보다 크거나 같습니다.|
|[연산자<](../standard-library/memory-operators.md#op_lt)|하나의 개체에 대한 테스트는 지정된 클래스의 두 번째 개체보다 적습니다.|
|[연산자\<=](../standard-library/memory-operators.md#op_gt_eq)|하나의 개체에 대한 테스트는 지정된 클래스의 두 번째 개체보다 적거나 같습니다.|
|[연산자>](../standard-library/memory-operators.md#op_gt)|하나의 개체에 대한 테스트는 지정된 클래스의 두 번째 개체보다 큽니다.|
|[연산자<<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` inserter.|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[allocator](../standard-library/allocator-class.md)|클래스 **템플릿은 형식 형식** 개체의 배열에 대해 저장소 할당 및 해제를 관리 하는 개체를 설명 합니다.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|할당자를 사용할 수 있는 컨테이너에 필요한 모든 정보를 확인하는 개체에 대해 설명합니다.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|클래스 템플릿은  <strong>\*</strong> 바깥쪽 auto_ptr 제거 될 때 요소가 가리키는 개체가 삭제 되도록 하는 형식 형식의 할당 된 개체에 대 한 포인터를 저장 하는 개체를 설명 합니다.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|불량 weak_ptr 예외를 보고합니다.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|`shared_ptr`을 생성할 수 있습니다.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|포인터 형식의 할당자를 설명 하기 위해 형식의 개체에 필요한 정보를 제공 `allocator_traits` `Ptr` 합니다.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|초기화되지 않은 메모리에 결과를 저장하는 알고리즘을 사용할 수 있도록 제공되는 어댑터 클래스입니다.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|동적으로 할당된 개체 주위에 참조 횟수가 계산되는 스마트 포인터를 래핑합니다.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|소유한 개체에 대한 포인터를 저장합니다. 다른 `unique_ptr`이 아닌 곳에서 포인터를 소유하고 있습니다. `unique_ptr`은 소유자가 소멸될 때 소멸됩니다.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|약하게 링크된 포인터를 래핑합니다.|

### <a name="structures"></a>구조체

|Name|설명|
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|및에 대해 특수화 된 오버 로드를 제공 `unique_ptr` `shared_ptr` 합니다.|
|[owner_less](../standard-library/memory-functions.md#owner_less)|공유된 포인터와 약한 포인트에 대한 소유권 기반의 혼합된 비교를 허용합니다.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>특수화

|Name|설명|
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|형식에 대 한 클래스 템플릿 할당자의 특수화 **`void`** 로,이 특수화 된 컨텍스트에서 맞는 멤버 형식만 정의 합니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
