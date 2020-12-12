---
description: Sync_per_container 클래스에 대해 자세히 알아보세요.
title: sync_per_container 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 83dc2f3d874fdc1910a3da4fdc34fb18c432cc25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183314"
---
# <a name="sync_per_container-class"></a>sync_per_container 클래스

각 할당자 개체에 대해 별도의 캐시 개체를 제공 하는 [동기화 필터](../standard-library/allocators-header.md) 에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>매개 변수

*캐시*\
동기화 필터와 연결된 캐시 형식입니다. , 또는 일 수 있습니다 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) [`cache_freelist`](../standard-library/cache-freelist-class.md) [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[equals](#equals)|두 캐시가 같은지 비교합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a> sync_per_container:: equals

두 캐시가 같은지 비교합니다.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>매개 변수

*캐시*\
동기화 필터의 캐시 개체입니다.

*다른*\
같은지 비교할 캐시 개체입니다.

### <a name="return-value"></a>반환 값

멤버 함수는 항상 **`false`** 를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[\<allocators>](../standard-library/allocators-header.md)
