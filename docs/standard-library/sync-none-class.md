---
description: Sync_none 클래스에 대해 자세히 알아보세요.
title: sync_none 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: 34c4f42962b1dc8b8dc58f07cd54384e049789a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183349"
---
# <a name="sync_none-class"></a>sync_none 클래스

동기화를 제공 하지 않는 [동기화 필터](../standard-library/allocators-header.md) 에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>매개 변수

`Cache`\
동기화 필터와 연결된 캐시 형식입니다. , 또는 일 수 있습니다 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) [`cache_freelist`](../standard-library/cache-freelist-class.md) [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[추가로](#allocate)|메모리 블록을 할당합니다.|
|[할당](#deallocate)|지정된 위치부터 시작하여 스토리지에서 지정된 개수의 개체를 해제합니다.|
|[equals](#equals)|두 캐시가 같은지 비교합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a> sync_none:: allocate

메모리 블록을 할당합니다.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>매개 변수

*수*\
할당할 배열의 요소 수입니다.

### <a name="remarks"></a>설명

구성원 함수는 `cache.allocate(count)`를 반환합니다. 여기서 `cache`는 캐시 개체입니다.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a> sync_none::d eallocate

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

구성원 함수는 `cache.deallocate(ptr, count)`를 호출합니다. 여기서 `cache`는 캐시 개체를 나타냅니다.

## <a name="sync_noneequals"></a><a name="equals"></a> sync_none:: equals

두 캐시가 같은지 비교합니다.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>매개 변수

*캐시*\
동기화 필터의 캐시 개체입니다.

*다른*\
같은지 비교할 캐시 개체입니다.

### <a name="return-value"></a>반환 값

멤버 함수는 항상 **`true`** 를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
