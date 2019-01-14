---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: 064afd4467a2aedebe3a9892fc80b14597c8552f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544081"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

노드 기반 컨테이너에 대해 메모리 블록을 할당 및 해제하는 데 도움이 되는 여러 템플릿을 정의합니다.

## <a name="syntax"></a>구문

```cpp
#include <allocators>
```

## <a name="remarks"></a>설명

\<allocators> 헤더는 노드 기반 컨테이너에 대한 메모리 관리 전략을 선택하는 데 사용할 수 있는 6개의 할당자 템플릿을 제공합니다. 이러한 템플릿과 함께 사용하도록, 메모리 관리 전략을 다양한 다중 스레딩 스키마(none 포함)에 맞게 조정할 수 있는 몇 가지 서로 다른 동기화 필터도 제공합니다. 메모리 관리 전략을 특정 애플리케이션의 알려진 메모리 사용 패턴 및 동기화 요구 사항과 일치시키면 종종 애플리케이션의 속도를 높이거나 전체 메모리 요구 사항을 줄일 수 있습니다.

할당자 템플릿은 추가 메모리 관리 전략을 제공하기 위해 사용자 지정하거나 대체할 수 있는 재사용 가능한 구성 요소로 구현됩니다.

C++ 표준 라이브러리(std::list, std::set, std::multiset, std::map and std::multimap)의 노드 기반 컨테이너는 개별 노드에 해당 요소를 저장합니다. 특정 컨테이너 형식에 대한 모든 노드는 크기가 같기 때문에 범용 메모리 관리자의 유연성이 필요하지 않습니다. 각 메모리 블록의 크기는 컴파일 시간에 알려지기 때문에 메모리 관리자는 훨씬 간단하고 빠를 수 있습니다.

노드 기반이 아닌 컨테이너(예: C++ 표준 라이브러리 컨테이너 std::vector std::deque 및 std::basic_string)와 함께 사용할 경우 할당자 템플릿은 올바르게 작동하지만, 기본 할당자에 비해 더 나은 성능을 제공하지는 않을 수 있습니다.

할당자는 지정된 형식의 개체 및 개체 배열에 대한 스토리지 할당 및 해제를 관리하는 개체를 설명하는 템플릿 클래스입니다. 할당자 개체는 C++ 표준 라이브러리의 여러 컨테이너 템플릿 클래스에서 사용됩니다.

할당자는 다음 형식의 모든 템플릿입니다.

```cpp
template<class Type>
class allocator;
```

여기서 템플릿 인수 `Type`은 할당자 인스턴스에 의해 관리되는 형식입니다. C++ 표준 라이브러리는 [\< memory>](../standard-library/memory.md)에 정의된 기본 할당자인 템플릿 클래스 [allocator](../standard-library/allocator-class.md)를 제공합니다. \<allocators> 헤더는 다음과 같은 할당자를 제공합니다.

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

다음 코드 예제와 같이, 컨테이너를 만들 때 할당자의 적절한 인스턴스화를 두 번째 형식 인수로 사용합니다.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0은 `allocator_chunklist` 및 기본 동기화 필터를 사용하여 노드를 할당합니다.

기본 필터 이외의 동기화 필터로 할당자 템플릿을 만들려면 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 매크로를 사용합니다.

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1은 `allocator_chunklist` 및 [sync_per_thread](../standard-library/sync-per-thread-class.md) 동기화 필터를 사용하여 노드를 할당합니다.

블록 할당자는 캐시 또는 필터입니다. 캐시는 std::size_t 형식의 인수 하나를 받는 템플릿 클래스입니다. 단일 크기의 메모리 블록을 할당 및 할당 취소하는 블록 할당자를 정의합니다. 연산자를 사용 하 여 메모리를 확보 해야 **새**, 연산자를 별도로 호출 해야 것 이지만 **새** 각 블록에 대 한 합니다. 예를 들어, 더 큰 블록에서 하위 할당을 수행하거나 후속 재할당을 위해 할당 취소된 블록을 캐시할 수 있습니다.

rebind를 컴파일할 수 없는 컴파일러에서는, 템플릿이 인스턴스화될 때 사용되는 std::size_t 인수의 값이 캐시의 멤버 함수인 allocate 및 deallocate에 전달되는 인수 _Sz의 값과 다를 수 있습니다.

\<allocators>는 다음 캐시 템플릿을 제공합니다.

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

필터는 템플릿 인수로서 전달되는 다른 블록 할당자를 사용하여 멤버 함수를 구현하는 블록 할당자입니다. 필터의 가장 일반적인 형태는 동기화 필터입니다. 동기화 필터는 다른 블록 할당자 인스턴스의 멤버 함수에 대한 액세스를 제어하기 위해 동기화 정책을 적용합니다. \<allocators>는 다음 동기화 필터를 제공합니다.

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators>는 또한 여러 개의 블록 할당자 인스턴스를 보유하고 컴파일 시간 대신 런타임에 할당 또는 할당 취소에 사용할 인스턴스를 결정하는 [rts_alloc](../standard-library/rts-alloc-class.md) 필터를 제공합니다. rebind를 컴파일할 수 없는 컴파일러에서 사용됩니다.

동기화 정책은 할당자 인스턴스가 다중 스레드의 동시 할당 및 할당 취소 요청을 처리하는 방법을 결정합니다. 가장 간단한 정책은 모든 요청을 기본 캐시 개체에 직접 전달하여 동기화 관리를 사용자에게 맡기는 것입니다. 좀 더 복잡한 정책은 뮤텍스를 사용하여 기본 캐시 개체에 대한 액세스를 직렬화하는 것일 수 있습니다.

컴파일러가 단일 스레드 및 다중 스레드 애플리케이션 컴파일을 모두 지원하는 경우 단일 스레드 애플리케이션에 대한 기본 동기화 필터는 `sync_none`이고, 다른 모든 경우에는 `sync_shared`입니다.

`cache_freelist` 캐시 템플릿은 free list에 저장할 최대 요소 수를 결정하는 최대 클래스 인수를 가져옵니다.

\<allocators>는 다음의 최대 클래스를 제공합니다.

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>매크로

|매크로|설명|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|할당자 템플릿 클래스를 생성합니다.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|`stdext::allocators::cache_chunklist<sizeof(Type)>`을 생성합니다.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|`stdext::allocators::cache_freelist<sizeof(Type), max>`를 생성합니다.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|`stdext::allocators::cache_suballoc<sizeof(Type)>`을 생성합니다.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|동기화 필터를 생성합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator!= (\<allocators>)](../standard-library/allocators-operators.md#op_neq)|지정된 클래스의 할당자 개체가 다른지 테스트합니다.|
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|지정된 클래스의 할당자 개체가 같은지 테스트합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|동기화 필터에서 사용자 정의 할당자를 만드는 데 필요한 기본 클래스 및 일반 함수를 정의합니다.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|[cache_chunklist](../standard-library/cache-chunklist-class.md) 유형의 캐시를 사용하여 개체에 대한 저장소 할당 및 해제를 관리하는 개체를 설명합니다.|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|[max_fixed_size](../standard-library/max-fixed-size-class.md)에 의해 관리되는 길이와 함께 [cache_freelist](../standard-library/cache-freelist-class.md) 형식의 캐시를 사용하여 `Type` 형식의 개체에 대한 저장소 할당 및 해제를 관리하는 개체를 설명합니다.|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|사용 하는 할당자를 구현 **delete 연산자** 메모리 할당을 취소 하려면 블록 및 **new 연산자** 메모리 블록을 할당 하려면.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|[cache_suballoc](../standard-library/cache-suballoc-class.md) 형식의 캐시를 사용하여 `Type` 형식의 개체에 대한 저장소 할당 및 해제를 관리하는 개체를 설명합니다.|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|[max_unbounded](../standard-library/max-unbounded-class.md)에 의해 관리되는 길이와 함께 [cache_freelist](../standard-library/cache-freelist-class.md) 형식의 캐시를 사용하여 `Type` 형식의 개체에 대한 저장소 할당 및 해제를 관리하는 개체를 설명합니다.|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|[max_variable_size](../standard-library/max-variable-size-class.md)에 의해 관리되는 길이와 함께 [cache_freelist](../standard-library/cache-freelist-class.md) 형식의 캐시를 사용하여 `Type` 형식의 개체에 대한 저장소 할당 및 해제를 관리하는 개체를 설명합니다.|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|단일 크기의 메모리 블록을 할당 및 할당 취소하는 블록 할당자를 정의합니다.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|단일 크기의 메모리 블록을 할당 및 할당 취소하는 블록 할당자를 정의합니다.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|단일 크기의 메모리 블록을 할당 및 할당 취소하는 블록 할당자를 정의합니다.|
|[freelist](../standard-library/freelist-class.md)|메모리 블록의 목록을 관리합니다.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|[freelist](../standard-library/freelist-class.md) 개체를 고정된 최대 길이로 제한하는 최대 클래스 개체를 설명합니다.|
|[max_none](../standard-library/max-none-class.md)|[freelist](../standard-library/freelist-class.md) 개체를 최대 영(0)의 길이로 제한하는 최대 클래스 개체를 설명합니다.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|[freelist](../standard-library/freelist-class.md) 개체의 최대 길이를 제한하지 않는 최대 클래스 개체를 설명합니다.|
|[max_variable_size](../standard-library/max-variable-size-class.md)|[freelist](../standard-library/freelist-class.md) 개체를 할당된 메모리 블록의 수와 대략 비례하는 최대 길이로 제한하는 최대 클래스 개체를 설명합니다.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|rts_alloc 템플릿 클래스는 캐시 인스턴스의 배열을 보유하고 컴파일 시간 대신 런타임에 할당 및 할당 취소에 사용할 인스턴스를 결정하는 [필터](../standard-library/allocators-header.md)를 설명합니다.|
|[sync_none](../standard-library/sync-none-class.md)|동기화를 제공하지 않는 동기화 필터를 설명합니다.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|각 할당자 개체에 대해 별도의 캐시 개체를 제공하는 동기화 필터를 설명합니다.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|각 스레드에 대해 별도의 캐시 개체를 제공하는 동기화 필터를 설명합니다.|
|[sync_shared](../standard-library/sync-shared-class.md)|뮤텍스를 사용하여 모든 할당자가 공유하는 캐시 개체에 대한 액세스를 제어하는 동기화 필터를 설명합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<allocators>

**네임스페이스:** stdext

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
