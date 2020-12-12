---
description: Sync_shared 클래스에 대해 자세히 알아보세요.
title: sync_shared 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 4093b85ce6f10552cba462074aee2a448cc5ce3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183284"
---
# <a name="sync_shared-class"></a>sync_shared 클래스

뮤텍스를 사용 하 여 모든 할당자에서 공유 하는 캐시 개체에 대 한 액세스를 제어 하는 [동기화 필터](../standard-library/allocators-header.md) 에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>매개 변수

*캐시*\
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

## <a name="sync_sharedallocate"></a><a name="allocate"></a> sync_shared:: allocate

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

구성원 함수는 뮤텍스를 잠그고, `cache.allocate(count)`를 호출하고, 뮤텍스 잠금을 해제한 다음 이전 호출의 결과를 `cache.allocate(count)`에 반환합니다. `cache`는 현재 캐시 개체를 나타냅니다.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a> sync_shared::d eallocate

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

이 구성원 함수는 뮤텍스를 잠그고, `cache.deallocate(ptr, count)`를 호출한 다음(여기서 `cache`는 캐시 개체를 나타냄) 뮤텍스 잠금을 해제합니다.

## <a name="sync_sharedequals"></a><a name="equals"></a> sync_shared:: equals

두 캐시가 같은지 비교합니다.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>매개 변수

*캐시*\
동기화 필터와 연결된 캐시 형식입니다.

*다른*\
같은지 비교할 캐시입니다.

### <a name="return-value"></a>반환 값

**`true`** 가 캐시 개체를 나타내는의 결과가 이면이 `cache.equals(Other.cache)` `cache` **`true`** 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
