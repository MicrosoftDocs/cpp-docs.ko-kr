---
description: Rts_alloc 클래스에 대해 자세히 알아보세요.
title: rts_alloc 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: b2fe4bf3fe3f54e8fe1de3d89605280b2ba2b857
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148943"
---
# <a name="rts_alloc-class"></a>rts_alloc 클래스

Rts_alloc 클래스 템플릿에서는 캐시 인스턴스의 배열을 보유 하 고 컴파일 시간 대신 런타임에 할당 및 할당 취소에 사용할 인스턴스를 결정 하는 [필터](../standard-library/allocators-header.md) 에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>매개 변수

*캐시*\
배열에 포함된 캐시 인스턴스의 형식입니다. , 또는 일 수 있습니다 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) [`cache_freelist`](../standard-library/cache-freelist-class.md) [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

## <a name="remarks"></a>설명

이 클래스 템플릿은 여러 개의 블록 할당자 인스턴스를 보유 하 고 컴파일 시간 대신 런타임에 할당 또는 할당 취소에 사용할 인스턴스를 결정 합니다. rebind를 컴파일할 수 없는 컴파일러에서 사용됩니다.

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[추가로](#allocate)|메모리 블록을 할당합니다.|
|[할당](#deallocate)|지정된 위치부터 시작하여 스토리지에서 지정된 개수의 개체를 해제합니다.|
|[equals](#equals)|두 캐시가 같은지 비교합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a> rts_alloc:: allocate

메모리 블록을 할당합니다.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>매개 변수

*수*\
할당할 배열의 요소 수입니다.

### <a name="return-value"></a>반환 값

할당된 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

멤버 함수는를 반환 합니다 `caches[_IDX].allocate(count)` . 여기서 인덱스는 `_IDX` 요청 된 블록 크기 *수* 에 의해 결정 되거나, *개수가* 너무 크면를 반환 `operator new(count)` 합니다. `cache`를 반환합니다.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a> rts_alloc::d eallocate

지정된 위치부터 시작하여 스토리지에서 지정된 개수의 개체를 해제합니다.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>매개 변수

*ptr*\
스토리지에서 할당을 취소할 첫 번째 개체에 대한 포인터입니다.

*수*\
스토리지에서 할당을 취소할 개체의 수입니다.

### <a name="remarks"></a>설명

멤버 함수는를 호출 합니다 `caches[_IDX].deallocate(ptr, count)` . 여기서 인덱스는 `_IDX` 요청 된 블록 크기 *수* 에 의해 결정 되거나, *개수가* 너무 크면를 반환 `operator delete(ptr)` 합니다.

## <a name="rts_allocequals"></a><a name="equals"></a> rts_alloc:: equals

두 캐시가 같은지 비교합니다.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>매개 변수

*_Cache*\
필터와 연결된 캐시 개체입니다.

*_Other*\
같은지 비교할 캐시 개체입니다.

### <a name="remarks"></a>설명

**`true`** 의 결과 이면 `caches[0].equals(other.caches[0])` 이 고, 그렇지 않으면 **`false`** 입니다. `caches`는 캐시 개체의 배열을 나타냅니다.

## <a name="see-also"></a>참고 항목

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
