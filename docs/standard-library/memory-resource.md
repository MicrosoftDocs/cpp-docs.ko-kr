---
description: '다음에 대 한 자세한 정보: &lt; memory_resource&gt;'
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: d575d94323552fd75fb6217ced7933e5050ee8b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183804"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource&gt;

컨테이너 클래스 템플릿 memory_resource 및 해당 지원 템플릿을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
#include <memory_resource>
```

## <a name="members"></a>멤버

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](../standard-library/memory-resource-operators.md#op_neq)|연산자의 좌 변에 있는 memory_resource 개체가 우변에 있는 memory_resource 개체와 같지 않은 지 테스트 합니다.|
|[연산자 = =](../standard-library/memory-resource-operators.md#op_eq_eq)|연산자의 좌 변에 있는 memory_resource 개체가 우변에 있는 memory_resource 개체와 같은지 테스트 합니다.|

### <a name="specialized-template-functions"></a>특별 템플릿 함수

|Name|설명|
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>클래스 및 구조체

|Name|설명|
|-|-|
|[memory_resource 클래스](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource 클래스](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options 구조체](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource 클래스](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource 클래스](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
